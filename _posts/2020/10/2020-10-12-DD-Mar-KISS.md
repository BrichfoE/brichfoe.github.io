---
layout: post
title: Marches - Keep It Simple, Stupid
date: 2020-10-12 13:00:00
categories: [Dev Diary]
tags: [marcherLord]
last_modified_at: 20-10-12
---

## Greetings and Salutations
Good morning, erstwhile Gunfrith.  How have you been?  Pity about those Viking raids.  I heard they made off with all the gold in the local church as well as torching your farm.  

Last week I aimed to finish the basic gameplay loop, and then move on to one of the following:
1. More terrain types than just mountains
2. Procedurally Generating the map
3. Implementing the rounds that will make up the secondary loop

I basically blew through the first part of getting the notifications of when the enemy has sacked a settlement on Monday.  I didn't get a huge amount of time to work on this week either, but I did make some good progress on the broader strokes.  Also, I did a lot of smaller things, and weirdly the most satisfying thing I did all week was making the army size scale to the army size.
![Big red block, tiny blue block](/assets/DD_Mar_Week3.PNG)

## Sticking to an MVP
In my last post I had a couple lofty ideas that I had not really thought through.  Working out the delay between when a settlement gets sacked and the defending army should hear about it is an interesting idea, particularly if you're playing as the aggressor and have an opportunity to prevent word from getting out.  However, I decided it is unnecessary complexity for my MVP.  Instead, I settled on just having a semi-transparent version of the aggressor army appearing on top of the settlement instantly.  This will do for now, and should be replaced with the settlement on fire or something when I actually have any art assets.

The other example was moving on to either broadening out the types of terrain or working on the procedural map generation.  The first of these is unnecessary for a prototype, and the latter is just a nice to have.  However, if I want to get a feel for how the game will progress, I really need to get started on the next steps.  All the things discussed so far are things I'll come back to, but as my previous boss used to remind me in nearly every technical design, it's usually best to adhere to KISS: Keep it simple, stupid.

The current state of the game is small little stealth thing action where you move around, get chased if you are spotted, and try to catch your enemy in a pass.  You don't know where they are if they aren't close enough or are around a corner, adding a small element of surprise and danger.  It isn't much, but it should be everything we need for the core of the game for the defender, the second to second gameplay.  This means, it is time for the secondary loop, the minute to minute gameplay to give the player a reason to play well in the primary loop.

## What that Secondary Loop looks like so far
The secondary loop then will be engaging in multiple rounds.  Each round will start with both armies spawning at opposite ends of the map and end with either the aggressor army being defeated or making it back to the border intact.  Between rounds I would like to have a screen where the player can spend resources to increase the strength or speed of your army to introduce a positive feedback loop to motivate players to take risks to stop the aggressor as early as possible.

I had to do a bunch of housekeeping to make the scene repeatable.  There were a bunch of assumptions in my code that the other army would always be there.  These had to get updated so I could tear down and re-create the scene at will.  That didn't take too long, and it will make writing unit tests easier, something I'll probably devote a post to at some point in the future.

The other thing was setting up the UI for the inter-round planning (forgive the blank space to the left, that will eventually be some stats on how the round went and what resources are available at the end of the turn, probably with a nice background image).
![Big red block, tiny blue block](/assets/DD_Mar_Week3b.PNG)
I put together a pretty basic UI where you could raise and lower the attributes of your army, which will take in an army and modify it.  However, currently there is nothing connecting this UI to the armies in the scene.  So essentially, I laid a good deal of groundwork this past week, leaving me well positioned to wire it all up next week.


## Building towards that Tertiary Loop
This coming week will be an extension on last week.  I'll write up some sort of logic to make the previous round feed into the menu, and then have the choices on that menu feed into the following round.

This will require me to actually add resources.  I have a basis for this in the loot that the Aggressor receives on sacking a settlement.  To date, this resource has only served to raise the morale of the aggressor and reduce its speed and strength.  Going forward, I'll want to sum up the remaining resources and make that available to the player to determine how many points they have to spend on improving their army.  Also, we'll want to have the success of the Aggressor feed into its morale and strength for the following round.

If that goes as quickly as I hope it will, I'll also try to work resources into the Aggressor AI's decision making so if it gets a good haul in the first couple settlements it will just turn back home rather than being a completionist the way it is today.

## Concluding remarks
Gunfrith, I hope to take up a collection to help you rebuild your farm.  I've begun advertising a GoFundMe page for you, and hopefully we can replace crops that were burnt when Magnus Haralson and his boys came through.  I will be in touch if we reach our funding goal.
