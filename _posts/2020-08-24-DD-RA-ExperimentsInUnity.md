---
layout: # post
title: Experiments in Unity
date: 2020-08-24 23:30:00
categories: [Dev Diary]
tags: [rexAnglorum]
last_modified_at: 2020-08-24
---

## Greetings and Salutations
Good morning, dear imaginary reader.  I had finished what I had set out for myself by Friday, but decided instead to switch up the schedule to post on Mondays.  I was able to stretch a bit more in the direction I had in mind, and I foresee myself wanting to have the weekend at the end of my sprint to close out the week's goals.  This was an issue for week 2 as I spent the weekend actually working on this very blog rather than the game, so it was a poorly planned week.  

Regardless, here we are posting on Mondays.  Today I want to talk a little bit about how I don't know what I'm doing.

	1. The benefits of trying things you're not qualified for
	2. Trying things out this week
	3. What cool new things I want to try next week

## Learning Through Experimentation
I am currently working as software developer at a finance company.  Six years ago, I had just left a job teaching English as a second language at a for-profit school, probably the least fulfilling work I have ever done.  I had no knowledge about finance or even basic economics, and I had absolutely no idea how a computer worked.  However, I had a friend who worked at a startup and his work seemed interesting, and I spent the next six years trying different things, transitioning from a receptionist, to an administrative assistant (effectively a secretary), to a data input monkey, to a product manager, to a developer.  At each stage I was able to pick small projects that fit the job description I was trying to assume.  

I had no idea how what I was doing for any of these stages, and I relied heavily on the experience and the patience of those around me.  These projects were not uniformly successful.  Thanks to the projects that my mentors helped me pick, these many failures were minor failures.  They were things that could have gone better or took longer than they should have, but ultimately the scope was small enough and the urgency was low enough that I was able to do new things, and learn from the people around me and my own mistakes.

I cannot overstate the impact of this not only on what I am capable of, but my own appetite for trying new things.  Last week I talked about picking small goals for quick wins each week to build confidence in the success of the project.  Similarly, doing things that seemed impossible a year ago keeps you optimistic about the future.

## Last Week's Experiment
This past week, I tried to work out how best to manage the work.  Warning that this section is going to involve a bit of code.

I picked unity because all this C# stuff is pretty normal for me these days.  The things that aren't normal for me are using the Unity code libraries, as I alluded to last week.  So it was pretty normal for me to create a fun little model to keep track of the various types of actions, be they planting, building, ploughing, foraging, etc.  That looks a little like this (plus some constructors I've trimmed for space).

```
 public class WorkerAction
    {
        public Guid ActionId;
        public ActionType ActionType;
        public IWorkstation TargetWorkstationController;
        public GameObject TargetObject;
        public float CompletionPercentage;
        public GameObject ActingWorker;
        public DateTime? CompletionTime;
    }
```

So great, we can make actions.  Why would we do this?  Well, having them as their own objects lets us create as many as we like which I can store in a central queue.  The best way I've found to do that so far is in a static class with a queue.  This way it'll always be accessible for whatever needs it.  That can be found here, with both a current action queue and a dictionary we can use to look up specific action details in the future if we ever decide do show that kind of info later on.  May scrap this or change the data structure, but this'll do for now.

```
public static class PublicActionQueue
{
    public static Queue<WorkerAction> ActionQueue = new Queue<WorkerAction>();
    public static Dictionary<System.Guid, WorkerAction> ActionHistory = new Dictionary<System.Guid, WorkerAction>();
}
```

So great, we can create these actions and add them to a universally accessible queue.  How do our worker bees actually know what to do?  Well from the few tutorials I've seen the usual format seems to be to create scripts called xController which manage the behavior of x.  This was an adjustment for me who's been working on MVC web applications (the C also stands for controller in that acronym), but it kind of makes sense.  To have this thing make sense to Unity, you then have it inherit from the MonoBehavior class as shown below, and you can attach it to your actual game objects.  That means once you write this script, you can just drag it on top of the worker in the Unity editor and it'll run whatever code you find inside.

In the WorkerController, I made an action queue specific to that worker as well as just a current active action.  This lets me interrupt workers to summon them over to our boss for a conversation without losing whatever it was they were just working on because they can pop it onto the queue and replace "run to the boss for a chat" as the current action, picking the last action once they've completed that.  Actually writing this, I may swap out the queue here for a stack seeing as I'm now envisioning actions as last in first out (LIFO) if the only way to do this is to replace the current action with a more important one.  Again, data structure subject to review as they see more use.

```
public class WorkerController : MonoBehaviour, IPointerDownHandler
{
    public Queue<WorkerAction> WorkerActionQueue;
    public WorkerAction CurrentAction;

    private List<Resource> _inventory;
}
```

So that's great, we have workers who can access the public queue, grab out any kind of action and work through whatever needs to be done there.  However, it gets a bit trickier when we need the actual places that the work gets done to hold their own status.  For example, a field of barley needs to be ploughed fully, then the barley can be planted, then it has to grow on its own without intervention from the worker, then it needs to be harvested.  That means that we need to have each farm have its own controller.  Not only that, each place we can do work may need to have its own controller as the logic for forests should be different than the logic for fields as one requires much more supervision than the other, even if workers should interact with them in a similar fashion.

My solution was to use a C# interface.  Interfaces are essentially contracts of what an object does.  I can create my own custom contract with all the methods I would need a worker to use to interact with each workstation, force each workstation to implement this contract, and then generically have the worker use the Interface methods to do whatever action the worker is attempting at that moment.  [More on interfaces if you enjoy reading dry reference material.](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/interface)

```
public class FarmController : MonoBehaviour, IWorkstation, IPointerDownHandler
{
    public WorkstationType CurrentContext;

    public decimal ProductionPercent;
    public decimal ActionPercent;
    public bool RequiresPrep;
    private decimal _efficency;
    private bool _harvestReady;

    public Resource _currentResourceStockpile;
}
```

So my IWorkstation interface has methods that expose the relevant fields on my Farm.  The below lets me access any of the custom interface methods to expose these properties, and because I put the IWorkstation property on the WorkerAction I should be able to use these across the board without thinking too hard about them.

```
var actionCompletion = currentAction.TargetWorkstationController.GetActionPercent();
```

Unity has some built in functionality which you would think would handle things like this.  However, the below does not let me directly access the custom properties I put on the FarmController.

```
var controller = currentAction.TargetObject.GetComponent<FarmController>().ActionPercent;
```

All in all, I'm not super happy with it.  I feel this is exactly how interfaces are supposed to be used, but I suspect there's something already in the Unity library that would solve the same problem with less overhead.  If you know why this is a bad idea, email me at elliott.brichford@gmail.com and let me know why and I'll run a retraction here.

The takeaway though was that I was trying to do something which Unity does not obviously support as most of its libraries are dedicated to the graphics rendering and physics processing.  I got to know the engine a little better and did more reading than I would have otherwise.

## Experimenting This Week
Well now that that's all said, what's for this week?  This week I'd like to build off of the custom properties I have already made and work on building out the workers themselves.  Specifically, I would like to get the foundations laid for some of the core mechanics around people management.  I want to give the worker personal preferences about what kind of work they need to do, how much time they should be allowed between tasks.  Also this will probably naturally require some work in the command conversation screens.

Additionally, this will likely be a strange sprint.  I will be on vacation insofar as that is possible in 2020, so I will probably not post next Monday, but possibly the day after Labor Day.

## Concluding Remarks
This one ended up being _very_ code heavy.  Apologies for the non-technical for speaking in Greek, and apologies for the too-technical who think my solution is crap.