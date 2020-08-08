---
layout: post
title: Dev Diary - Rex Anglorum - An Introduction
date: 2020-08-07 09:00:00
categories: [Dev Diary]
tags: [rexAnglorum]
last_modified_at: 2020-08-07
---

## Greetings and Salutations
Good morning, dear hypothetical reader.  Today I am going to try to accomplish a couple things.

	1. Describe exactly why I am writing
	2. Describe somewhat what I am building
	3. Describe maybe what I will accomplish before next week
	
## Point the first, why do?
It's really pretty straightforward.  I was watching Kurosawa's last movie the other day, *Maadadayo*, and at one point the main character quoted the old axiom "He who chases two hares catches neither."  This seemed particularly applicable to me as I have accumulated about a dozen projects during our pandemic induced isolation, each more ambitious than the last.  Usually each project gets somewhere between 2 and 5 hours of work put into it before I'm onto the next one.  With this in mind, a more accurate axiom may be "He who thinks about catching 30 hares watches a lot of Hulu."

In this state of permanent unproductivity, I stumbled across Ben "Yahtzee" Crowshaw's dev diary series in which he, a video game reviewer with Escapist magazine, created a new game every month for a year.  I was inspired by his ability to see so many small projects to completion as well as his ability to keep limiting his scope to something achievable. Most of my shelter at home projects have been things as complicated as learning how natural language processing works and then use that to create a machine learning algorithm that will learn how to read critically and flag dubious assertions in people's social media feeds.  I still think there's a valuable project there, but probably not something I can crank out by working on it on an occasional weekend.

So, the idea here is to pick this one item, a game, and work on it until I'm satisfied with the product.  That will at least mean a working prototype, possibly enough of a game to ask for money for it.  That will all depend on how far I take it before I call it quits.  In the meantime, I will be putting out weekly blog posts to document the progress I've made and hold myself accountable, because these will be awfully awkward updates if there is no progress to give as an update.

## Point the second, what do?
The game here is an idea I've been chewing on for a long time, but I never really knew what format I'd want to use until basically this week.  The working title is Rex Anglorum, King of the English in Latin, and the idea would be to give us a historical management sim which represented how difficult it was to run a feudal anything.  If you play something like Total War, you get an unrealistic amount of control over your kingdom because you are managing towns and armies.  In real life, you had to manage people, which were rarely so cooperative and unquestioning.

So, you the player get to start off as an old pater/mater familis in an Anglo Saxon farm sometime around the Christianization of the Anglo-Saxons.  You are immobile, but your children and their spouses come to you to receive direction, and you are happy to tell them what to plant in which fields and when to harvest and what types of crafts they should begin to learn to sell at the occasional market.  Eventually, you die and your child becomes the pater/mater familis.  The player stays with that family, building their fortunes over generations.  Whenever sufficient influence is built over the family's neighbors, the game moves from the farm to a village.  Your head of the household is now head of a manor and hold sway over its accompanying village.  The same rules apply, with the player building influence over generations until they are the most influential family in the province, the region, and finally the country.  The idea here is lifted from Spore which has these separate gameplay loops, each feeding into the next with distinct challenges and objectives, but maintaining a consistent through line.

## Point the third, what next?
So far, I have done enough planning and mockups to call my infantile design document done and created the project.  I am using Unity as it allows me to use C# for scripting, a language I am fairly familiar with from my day job.  I have created a primitive level, and put in some work around creating the worker queue.  This is where we will store the actions that the player wants the workers to perform.  So far, I have finished the queue itself and the logic that will allow the workers to pick up the next item off the queue.  Also, the scripting that moves the workers from point to point is complete.

![If you can even call this progress...](/assets/DD_RA_Intro.PNG)

Next steps are to build out the player controls.  Ideally, the player will be able to interact with this workflow queue in two ways.  One is to click on a field, and decide what should be planted there without determining who will do it.  Second will be calling out to a family member and inserting a new task in their queue for just that worker.  This week I hope to get both of these working, even if it is just hard coding in the desired action when the user clicks a field or a worker.  If time permits, I will also move on to creating the text window the player will use to choose from the available options (plant wheat or beans? {the answer is always beans}).

## Conclusion
If you made it this far, you are either very lost or are possibly a robot scanning for a comment section to post that you found a way to make tons of money working from home.  Either way, thank you for reading!  Even the milliseconds your robot eyes spent scanning this page have filled me with immeasurable joy!  Come back next week for more of whatever this has been.

