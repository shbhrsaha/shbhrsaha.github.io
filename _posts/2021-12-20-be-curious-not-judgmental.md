---
layout: post
title: Be curious, not judgmental
published: true
---

## The trigger

This video went viral a few years ago:

<iframe width="400" height="252" src="https://www.youtube.com/embed/1BB6wj6RyKo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

tl;dr is that to factory reset a smart light bulb, you need to turn it on for eight seconds at a time, five times. (There's a more complex variation of the procedure for older firmware.)

Twitterati were quick to knock the tedious procedure:

{% include image.html url="/static/be-curious-not-judgmental/tweet1.png" caption="" %}

{% include image.html url="/static/be-curious-not-judgmental/tweet2.png" caption="" %}

## The problem

It's tempting to offer ostensibly simpler alternatives:
- _Add a tiny factory reset button!_
- _Shorten the sequence length!_
- _Shorten the time intervals to two seconds!_

The reality, though, is that without understanding all constraints of the problem, we can't really tell what the best solution would be-- perhaps what's depicted in the video, perhaps something else.

Heck, I don't know what all the constraints are, but I can propose a few for consideration: size, cost, manufacturing complexity, thermal safety, accidental triggering...

Why not add a factory reset button? Well, where would we put it? We can't put it in on the glass, so now we consider the metal part of the bulb. We can't put it there, though, because it might trigger accidentally when people screw in the bulb. 

Even if we did manage to sneak a button onto the bulb, how would people press it? Unscrew the light bulb, fair enough. But now we don't have power to run the factory reset process. Should we add a capacitor or a battery? If the latter, how do we keep it protected from the bulb's heat?

So, we ditch the button and settle for a timed sequence. Why not shorten the sequence length? Be careful-- if it's too short, people might trigger it accidentally during day-to-day use.

Why not shorten the time intervals to two seconds? If they're too short, people might execute it incorrectly when they _do_ want to factory reset.

## The takeaway

I'm not saying the procedure depicted in the video _is_ the best solution. I'm saying that we don't know enough about the constraints to say there's a better solution.

Product development is a challenging exercise in constraint optimization and managing tradeoffs. There's a common misconception that requirements should be made by product managers or designers in isolation-- that good design is the result of someone walking alone into a room, thinking really hard, and walking out with a product requirements document.

The reality is that product managers, designers, engineers, and other stakeholders need to collaborate to optimize myriad constraints originating from their respective disciplines to derive the best solution-- however they define "best" to be.

It's a messy process. There's [more to the design of everyday things](https://xkcd.com/1741/) than meets the eye.

By being curious, not judgmental, we can start to understand these peculiar things around us. Only by understanding, we might even find a way to make them better.