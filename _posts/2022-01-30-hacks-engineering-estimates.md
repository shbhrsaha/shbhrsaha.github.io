---
layout: post
title: Hacks for engineering estimates
links:
    - Hacker News: https://news.ycombinator.com/item?id=31317037
---

Engineers often have to ask each other for "estimates"-- rough projections for how long projects will take. While some teams do rigorous estimation rituals to varying degrees of success, many situations simply require answering based on gut feel.

Even though answers are often based on gut feel, how you ask for and interpret the estimates still matter. Here are a few behavioral hacks I've observed that often made the difference between a bad estimate conversation and a great one.

## Separate estimate vs. target vs. commitment vs. plan

Consider whether an estimate is really what you're looking for. Estimates are not the same as targets, commitments, or plans.

In [*Software Estimation: Demystifying the Black Art*](https://www.amazon.com/Software-Estimation-Demystifying-Developer-Practices/dp/0735605351), Steve McConnell disambiguates them accordingly:

- **Estimate**: *"prediction of how long a project will take or how much it will cost"*
- **Target**: *"statement of a desirable business objective"*
- **Commitment**: *"promise to deliver defined functionality at a specific level of quality by a certain date"*
- **Plan**: steps for how to *"seek a particular result"*

Conversations between stakeholders often set off on the wrong foot by confusing these four terms. Notably, McConnell warns *"you can negotiate the commitment, but don’t negotiate the estimate"*.

A few of the hacks below can be applied to both estimates and commitments.

## Identify the extremes

It's important to identify the latest/earliest that a project might complete, but teams often find it difficult to reason about this-- especially when asked to give an answer on-the-spot.

In [MFM Mini - A Guide to Asking Better Questions](https://open.spotify.com/episode/4r4wDlLv5l09M6WCS92UzB?si=h8d4ID1RQvG0vke8zQG-SA), Shaan Puri shared a great line of questioning from Twitch CPO Dan Clancy.

> (For Worst Case) *"I know we don't know the exact timeline [...] When would you be surprised that we didn't have this done?"*
>
>(For Best Case) *"Best case scenario, what are you thinking?"*

These questions are useful because their informality encourages people to share how they candidly feel.

## Note the precision

When listening to an estimate/commitment, note the "precision" with which the answer is expressed-- whether it's in days, weeks, months, quarters, or years.

Then, to set expectations for yourself, add one unit of the expressed precision to the provided estimate. A project estimated to complete *"sometime in Q2"* is just as likely to finish in Q3.

Of course, the real delay in the project can end up being indefinitely long, but the answer's precision gives you a probabilistic glimpse into *at least how long* the delay might be.

## Ask for confidence levels over time

It's common for people to share confidence levels (high, medium, low) alongside their engineering estimates/commitments. It's not as common to continuously update those confidence levels as a project progresses

Updating confidence levels over time is valuable to prompt conversation about risks as they're discovered.

This is especially useful for cross-team conversations, where partners may be hesitant to communicate potential delays until closer to the anticipated completion date. Imagine hearing the following weekly updates:

> (Week 6) *"It'll take four more weeks, we have high confidence"*
> 
> (Week 7) *"It'll still take three more weeks, but we're medium confidence now"*

Understanding what changed confidence from high to medium will tell you more about the potential outcome than the estimate itself.

## Conclusion

Engineering estimates rarely predict real-world outcomes with 100% accuracy; the reality is that most projects experience delays. Paying attention to how we ask for and interpret estimates, though, can help set expectations appropriately.
