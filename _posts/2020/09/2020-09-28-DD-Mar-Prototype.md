---
layout: post
title: Marches - I'm Pro Prototype
date: 2020-09-28 21:00:00
categories: [Dev Diary]
tags: [marcherLord]
last_modified_at: 20-09-28
---

## Greetings and Salutations
Good evening, dear...you know, since we've established that no one reads these, it may be more fun to address a specific no one rather than the general void.

Good evening, dear Gunfrith.  I had a pretty good first week on the project.  I got most of the way to a working prototype, which is pretty good considering the limited time I put towards it this week.  Let's dive right in.

## Prototyping
So Gunfy, if I may be so bold, you may be wondering what is up with my current fixation with prototypes?  Well for most people they are a great way to ensure that they are on the right track with their product.  For a game, it's great to see your core idea in action and hopefully let you save a bunch of effort pivoting to something related but different if it turns out it isn't.  The earlier in the process you discover that you need to interate, the more time and effort you save down the line.

For my own self, I have trouble finishing projects that I start just on my own behalf.  In addition to trying to blog about it here, I am also working on getting to this prototype as fast as possible to get a working thing before I lose steam on this guy and get distracted by a new project.  I am hoping this approach gets me to something playable by month's end.

## One small step for a sprite
What do I need to make this a playable prototype?  In truth, I have two targets in mind as sorts of milestones to work towards.  The second one is a janky version of my game that I will be able to ask people to playtest.  Before I hand it over to anyone, I plan to assert to them that it is a prototype with no time spent on music, minimal time on sound in general, minimal animations, severely pared down art assets, and possibly a menu screen.  Before I get to that, however, I plan to have an even jankier version with no sound, no animations, and just a couple blocks chasing one another around the screen.  This even less ambitious thing will be the first milestone.

Here's something to give you the flavor:
![The color scheme here is pretty awful, tbh...](/assets/DD_Mar_Week1.PNG)

This first round won't even have complicated combat mechanics.  My plan is to have the two armies (squares) navigate around the mountains (triangles) and always fight on contact.  The aggressor (red) always win unless they meet in an ambush zone (green hexagons), in which case the defender (blue) always wins.  Also to simplify, the player will start off only being the defender with an AI script moving the aggressor from town to town (orange circles) and only breaking off its path to chase down the defender if it sees him.  I still do have a couple kinks to iron out around pathfinding, but this is nearly done.

This week I made this rudimentary map and got the armies to move around on it.  Also, I followed [this really nice tutorial](https://www.youtube.com/watch?v=rQG9aUWarwE) to set up the field of view script which will be necessary to work out when the aggressor needs to head for the defender.  I've marked the mountains as obstacles that players can't see through, and I plan to only give the defender a slightly larger field of view than the aggressor, allowing them to scurry for an ambush point.  Naturally, defenders can't hide if they're being watched, so this whole setup should add an element of danger.  

## Where I want to be next week
The focus here will be the aforementioned kinks in pathfinding and then the actual battle logic, which again should be as simple as if on ambush spot then blue wins, else red wins.  From there, I'll want to focus on information flow to the player.  Specifically, if we are handicapping the player so much that they can't see around the next corner and will lose on contact with the enemy, we need to feed enough information to make this a little more balanced.

What I figure I can do here is to work out how long it should take for a runner to get from a sacked town to the player, and then after that delay we can notify the player that settlement _x_ was sacked _n_ days ago.  This will probably require some sort of UI to show the passage of days so that players have some sense for when, as well as a static representation of the last known location of the opponent and how long ago that was.  From there, that's probably enough to understand if what I'm thinking about will actually work.

I would like to hit this tiny MVP this week, so we'll see how far we get.  Ideally, I'd like to hit the full prototype before the end of October, but this week we'll settle for having this first mini version.

## Concluding remarks
Thanks for reading Gunfrith.  Your continued support means a lot to me.
