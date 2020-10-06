---
layout: post
title: Marches - It's Alive!
date: 2020-10-05 21:00:00
categories: [Dev Diary]
tags: [marcherLord]
last_modified_at: 20-10-05
---

## Greetings and Salutations
Good evening, dear Gunfrith.  How's the wife and kids?  Pestilent and numerous?  Well some things never change.

Last week I basically had two goals.
1. Make battles happen
2. Hide the opposing player, giving movement updates when they hit the cities.

I managed to leave out that having AI logic to actually move the dudes around was a prerequisite for both of these.  It wasn't too difficult, but I had never really done anything more complicated than "spawn enemies that go directly towards the player and shoot at random intervals" before.  The newness of it made it so much the more satisfying when it started working, but I had a busy personal weekend, so I did not get to making part two happen.

## I've created a monster
Referring to the logic which controls enemy objects in games as "Artificial Intelligence" always seemed kind of misleading to me.  Generally, when people think of AI, they think of programs that learn and improve.  I personally think of machine learning programs that learn to identify if a picture is or is not a cat without humans updating the code as they get trained.  

I suppose if you think about it broadly enough, game enemies have a set of logic that they follow to react dynamically to different circumstances.  In my case, the enemy will stomp from settlement to settlement pillaging, and if it sees another army while it is in 'raid' mode, it will enter 'chase' mode and go after that army.  If it loses sight of that army, it will enter 'search' mode and go to the last known location of that army, switching back into 'chase' if it sees it.  It's very rudimentary, but again the dynamically reacting to its environment gives it the appearance of intelligence.

The right side below is the game view, but you can see the red army's field of view here as the white circle in the Unity scene inspector on the left.  The green lines are for pathing, working out where they need to step to get from point A to point B, so you can see the red army losing sight of the blue one when it stops updating its destination.  Basically, I accidentally made a stealth game.
<div style="width:100%;height:0;padding-bottom:51%;position:relative;"><iframe src="https://giphy.com/embed/lRAFZU9NDmbpPHpBeS" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/lRAFZU9NDmbpPHpBeS"></a>Thrilling chase scene complimnets of Giphy</p>

I had to work through a couple minor bugs to keep the red army from freezing between stages, but after I got through those it was a surreal experience.  It started chasing me, and with the way the battles work now, catching me meant instant death.  All of the sudden, it felt alive and it was after me, and there were stakes for getting caught.  Just like that, it felt like my stupid 20 or so lines of code had animated this thing and it hated me.  It was marvelous.

## Where I want to be next week
This week is a little tricky.  The first part is what I said I'd be doing last week with working on how to properly feed information to the player about the enemy's whereabouts.  You can look at [last week's post](/DD-Mar-Prototype/) for a description of that.

The harder part to opine on now is figuring out next steps for the full prototype.  I expect I'll decide that the procedurally generated maps will be the next thing as the lowest effort and highest value add.  That, or I might start working out how to have multiple rounds in the same map.  Or, I might go with mixing up the terrain for added difficulty.  

As I say, the first step will be working out what parts I need for the full prototype, then prioritizing them, then picking up the first one off the stack.  I'll let you know how it goes.

## Concluding remarks
Gunfrith, your loyalty to reading these does you great credit.  Someday we'll try to collect all of these together and translate them into Old English so you can take it back and share it with your whole village.
