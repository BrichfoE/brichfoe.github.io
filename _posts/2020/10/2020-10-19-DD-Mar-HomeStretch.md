---
layout: post
title: Marches - The Home Stretch
date: 2020-10-19 13:00:00
categories: [Dev Diary]
tags: [marcherLord]
last_modified_at: 20-10-19
---

## Greetings and Salutations
Good evening, fair Gunfrith.  We should talk about your upcoming nuptials.  I know it's been hard since your family perished, but your engagement to Judith seems a bit too soon to be deemed polite.  Please let me know a good time to chat about this.

Last week I aimed to polish off the secondary gameplay loop, having rounds progress from one to the other.  Based on how this went, this promises to be a pretty short entry.

## Sometimes life happens
One danger of trying to make progress in one's hobbies is that you are putting deadlines on things you do in your free time.  This means that when you run short on free time, you are likely to miss said deadlines.

This week I spent a good deal of time dealing with housing things and my day job, leaving less time and energy to devote to my project here.  It's not a great feeling to admit this, but I failed to make the time I wanted for this.  Luckily, I have another week to try to grind on this to get the prototype where I want it before my self-imposed October 26th deadline.

## What did I actually do this week?
Rounds actually work now.  Defeating the aggressor results in victory and the inter-round screen.  Defeat results in the game speeding up as you helplessly watch the aggressor visit every settlement in the area before heading home.  In between rounds you can choose to increase your army strength, and these updates get carried over into the next round.

I also got most of the way through adding the resources into the mix.  Now there is a randomly assigned value assigned to every settlement at the beginning of each round.  The aggressor collects a sizable percentage of this when they sack a settlement.  The defender gets a more modest percentage in tax revenue between rounds.  This means an early victory for the defender would ensure a sizeable haul before the next round, while allowing the aggressor to take every settlement would not be too devastating.

## Polishing week
What does that leave?  For one thing, the AI side of choosing how to spend points.  On top of that, it lacks any sort of polish, really.  There's been no work to balance how the feedback loop of the previous round feeds into the next.  After testing what happens when you end a round in victory or defeat, I may need to weak how the added resources would impact each side.  I think chiefly we need to just play with it.

An idea I am toying with would be to have a defeat not be a complete loss in either case.  Maybe the loser gets its strength diminished but gets a head start so they can make more than one attempt.  This might also help add another chance at redemption and prevent a loss from being too crushing.

The stretch goal this week will be to have some level randomization going, but this will be extra credit.

## Concluding remarks
Gunfrith, I meant what I said.  Give me a call sometime.  I would have words.
