---
layout: single
title: "Best Practices for Rewriting a Microservice"
date: 2019-08-17 10:00:00 -0700
categories: development
---

In a [previous post](/blog/rewrite-microservice), I wrote about how component rewrites are long and costly undertakings that are only justifiable under specific circumstances.
However, if you do end up considering this path, here are some tips from my personal experience on how to run such a large project.

# The "We can still back out" stage #

**Set your priorities.**
Developers love to say that the legacy codebases they work on are bad.
However, if you press them on the topic and ask them to articulate exactly why the codebase is bad, they will often have trouble responding.
Does the codebase truly have some fundamental and irredeemable design flaws that impede future maintenance and development, or is it merely complicated and hard to read?
If complexity is the problem then a rewrite is not the answer; you will face all the same complexities that the original authors did.
However, if the problem is with scalability, maintainability, reliability, performance, or testability, then these priorities are valid.

**Beware of selfish incentives.**
Developers like to advocate for rewrites because rewrites make for pleasant work.
Developers working on rewrites are inherently exempt from many unpleasant chores that other developers must deal with.
There is no need to dig through incomprehensible legacy code because you're the one writing the code.
There is no need to debug production fires because the in-progress service has no production users.
There is little sense of urgency because your legacy component can continue operating in production as long as you need it to.
There is a sense of personal accomplishment that comes with replacing a legacy codebase with something shiny, whereas maintaining old code is emotionally unsatisfying work.
Rewrites are an over-prescribed remedy because the programmers proposing them are often thinking of their own interests rather than the interests of their users.
Once again, it is important to make sure that a rewrite is being done for the right reasons.

**Handle the immediate fires.**
Production does not sit still while you do a rewrite of your service.
If your old and buggy legacy service is causing customer pain, saying "We'll fix that bug in the rewrite" is not a satisfying answer.
Business pressure will force you to fix the painful bugs in your legacy service.
If you apply enough fixes and get your service to a reasonably stable state, you may find that the legacy service isn't as hopelessly buggy as you thought.

# The Preparation Stage #

**Don't skimp on design.**
There's a common proverb, "Weeks of programming can save you hours of planning".
This remains true for rewrite projects, except with much longer timeframes and much larger stakes.
If you are committing to a project as big as a rewrite, it makes no sense to rush through the design.
Nobody wants to write a codebase so bad that it will need to be rewritten again one day.
You should approach the planning stage as if you will only ever have one chance to get it done right.

**Pick a trusted architect.**
Because of the stakes involved in a rewrite, it is important that an experienced developer is leading the design effort.
The consequences of careless design can be enormous.
A single scalability chokepoint or a single overextended module with too many responsibilities will create pain for developers for years to come.
It takes considerable accumulated wisdom to recognize design flaws in advance, which is why it is essential that an experienced engineer is leading the project.

**Assign clear membership.**
During a rewrite, it is important to specify which developers are part of the project and which ones are not.
Rewrites are best done by small and compact teams that aren't weighed down by communication and administration overhead.
When outsiders offer unsolicited advice or start questioning the project long after development has started, it slows the project down without benefiting anybody.
The right time to ask tough questions is during the design and planning stage; once the plans are all finalized, it is usually prudent to stay the course.
Developers working on a rewrite need to make lots of implementation decisions; the project cannot proceed smoothly if outside approval is needed for every little detail.

# The Implementation Stage #

**Set aside the grunt work.**
Rewrites inherently involve lots of new code, only a fraction of which is actually interesting.
It makes sense for the lead architect to write out the broad outlines of the codebase and to write the core business logic.
However, it is a waste of an architect's bandwidth to focus on boilerplate code, integrations, low-level utilities, or other basic pieces that all production codebases require.
Filling in the gaps is a good job for the more junior developers on the team.
Indeed, this is how my current day job at Microsoft originally started.

**Give political cover.**
Rewrites are large and complicated projects prone to delays and frustrations.
During a rewrite, particularly towards the end as the code-complete service is getting prepared for a production rollout, many weeks or months can pass with seemingly no visible progress.
Managers and developers not involved with the project may start viewing the rewrite team with skepticism and exasperation.
For this reason, it is essential that rewrite projects are led by someone who is widely-liked and widely-trusted.
It is also essential that the lead developers have the backing of management.
The last thing anyone wants is for the whole project to suddenly start getting questioned at the late stages.

**Pass the torch.**
During and after a rewrite, the lead architect is likely to be the project's sole anchor, the only person capable of answering any question or debugging any problem.
It is unsustainable for a codebase to have only one expert, so a process of knowledge transfer will need to happen sooner or later.
When problems are uncovered or when incremental features need to be implemented, it is tempting to assign the lead architect to do this work.
However, it is better long-term for the team if other developers get the chance to get hands-on experience with the new codebase.
