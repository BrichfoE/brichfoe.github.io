---
layout: post
title: Dev Diary - Rex Anglorum - Project Scope
date: 2020-08-14 09:00:00
categories: [Dev Diary]
tags: [rexAnglorum]
last_modified_at: 2020-08-14
---

## Greetings and Salutations
Good morning, dear mythical reader.  I finished week 1, which turned out to be a weak one amiright?  I would be ashamed of myself, but if current events have taught us anything, it is that the successful are not burdened with any sense of shame whatsoever.  Moving on to this week's topics.

	1. A bit more on what I forsee as my the MVP
	2. Defining how much I should be covering each week
	3. Specifically what I hope to cover for next week

## Scope of the thing in general
Last week I talked a bit about what I was aiming for as a final product.  However, if either of you that have stumbled on this blog happens to have ever tried your hand at game development, or in fact software development of any kind, you know that the intended scope of this project is enormous.  The simplest features can take hours or even days to code, and I have a pretty ambitious project outlined here.  My day job has taught me that while it is important to begin with the end in mind, it is equally important to limit your initial steps to something more reasonable.  The relevant concept for attacking this problem is the Minimum Viable Product (MVP), which is the smallest thing you can make that still accomplishes everything you actually require of it.

To use my game as a concrete example, I laid out my elevator pitch with multiple phases with increasing complexity as the size of the player's estate grows.  The MVP here will be that first phase, and skinny version of it to boot.  I want to build a prototype which has the core gameplay loop fully fleshed out and none of the extra features that are seem key to my intended full design.  This means no building influence in the region, no rival families, and possibly no regional event mechanics like marriage offers or repelling raids.  I want to restrict my focus to having a small farm where you can boss around your family, watch it grow over time, and try to keep them from hating you.

Hopefully, if I can accomplish this, it will let me see what is and is not working in these core components before I start building the bells and whistles on top of them.  If something isn't working, I will still have the option of pivoting my design without having to rewrite everything because I decided to shift the foundations a few feet to the left.

## Scope of each week as routine
I had set a remarkably easy goal for myself this past past week for a couple reasons.  One was that I wanted a quick win to get off on the right foot.  Another was that I had gotten so little done the week before due to a power outage in my area so I probably underestimated the amount of time I would be able to devote to working on the game.  As it turned out, I cleared my goal easily but wasn't really happy about it.  I basically got through the work queue stuff in the first day, which made me think I would accomplish most of what I had in mind for the first month of development in this first week.  However, the hour a day during this past week to work on this turned out to not add up to as much time as I had anticipated. This made for a dissappointing end of the week when the only thing I got working was the text window for picking which crops to go in a field.

![Looks like I should spend some time on not having the text be quite so fuzzy, eh?](/assets/DD_RA_Week1.PNG)

Part of the slow down was the amount of time I had to spend researching how best to do some very basic things.  Unity has excellent documentation on their website, but it gets a little demoralizing when you only have an hour to create a menu and you have to spend half of it reading through the proper way to set up the hierarchy needed to support one.  I suppose I should focus on the fact that time spent learning the tooling will help me work more efficiently later, but the ratio of time spent to progress made feels lopsided at the moment.

The other bummer this week was the relativly low difficulty of what I accomplished.  Part of the reason that I'm pursuing this hobby is to stretch myself in different directions, but everything I did this week felt pretty run of the mill.  In picking what to set as a goal for each week, I hope to have to have my reach slightly exceeding my grasp at each stage to spur growth, but not by so far that it becomes demoralizing at any point.  That said, padding the first few weeks with time to let me learn the tools is probably a good idea.

## Scope of this week in particular
Last week I got the work queue working how I wanted it so far, and you can now summon workers to you (though nothing happens when they get to you) and assign crops to fields which will grow.  I would like to double down on the field mechanics this week and get the full ploughing, planting, growing, and harvesting cycle going.  Ideally the field will notify the action queue when it is ready to go to the next step.  I also want to introduce an efficiency multiplier as a bonus objective this week.  As you overuse a field, it will go down until you plant some beans for nitrogen fixing and let it lie fallow to recharge.  The idea here is to force players to do crop rotation and eventually discourage growing in the middle of winter (Note: I do not plan to include seasons in the MVP for reasons stated above).

"But wait!" I hear you cry, dear imaginary reader.  "Didn't you just say you wanted to have a bit more of a challenge in your next goal?  That doesn't sound so hard if you already have the fields switching between crops and growning!"  It does sound easy, but right now I'm struggling to figure out where the code should live.  In Unity, you write C# scripts which you attach to a GameObject in your scene.  For a novice like me it is difficult to out which bits of code should live on which objects, particularly when two objects are interacting.  For example, when the player tells a farmer to go plant beans, it's not difficult to tell the farmer to go over to the field to start planting.  But who keeps track of how long it takes to plant the beans?  Is it the field or the farmer?  Probably the field, but then how does the farmer know when he can go do the next thing?  And what if the player interrupts the farmer for a chat?  How does the field know the farmer has been interrupted?

I have ideas for all these things right now, so this week I'm hoping to play around and see if I can't come up with a good model for this.  Ideally, this will be extendable to whatever kind of workstation I want to introduce, be it harvesting trees from a local forrest, shearing sheep, or even negotiating a dowry with a negibor.  We'll see how it goes.

## Concluding Remarks
That's it for this week.  I am hoping to get some more time spent on this over the weekend, so maybe I will even be able to move on to other types of workstations like the forrest.  I guess that would be the double bonus objective.  I am also considering also dropping some posts here about things I've been reading and watching recently now that I have the blog set up, but no promises there.