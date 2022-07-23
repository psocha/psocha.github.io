---
layout: single
title: "The Quality Initiative and What Came of It"
date: 2022-07-23 10:00:00 -0700
categories: career
---

A few months ago, my immediate team started a new program, one very different from anything that existed in my past teams and past employers.
The program was called the "Quality Initiative" and was billed as a way to finally get some frustrating and long-neglected technical problems under control.

The Quality Initiative's main rule was that each week, every participating developer on the team needed to merge one "quality-related" code change.
At the start of each week, the team would have a short meeting in which everyone would present their change from the previous week, discuss their techniques, talk about potential follow-ups, and get thanks for solving problems.
There was no minimum bar on how big or ambitious the week's quality code change needed to be, but it was important to get something - anything - merged to the development branch.
Weekly exemptions were made for on-call shifts and vacation time.

A "quality" change was defined as anything that helped with readability, testability, test coverage, or the inner development loop.
Regular feature development and bug fixes were explicitly disqualified from being quality workitems, even if they had the side effect of increasing our code quality.
Whereas features and bug fixes were things we did in the name of our customers, quality changes were things we did in the name of our codebase.

I was initially a bit wary of the program, much as I usually am of most top-down impositions.
I was especially concerned about how people were going to find worthwhile problems and inspiration, especially newer developers who don't yet know the codebase very well.
Nevertheless, when the program began, I gave it my best shot; my first quality code change was a styling-related cleanup of a messy test file that I was pretty familiar with.

Here are some examples of code changes that developers on my team have done as part of the Quality Initiative:
* Reformat untidy code to conform to the style guide
* Move classes and files around to make the file tree more logical
* Add test coverage to areas of the code that previously didn't have it
* Fix flaky or permanently-failing tests
* Improve performance of slow tests
* Improve performance of end-to-end build and test pipelines
* Automate end-to-end tests that could previously only be run through a complicated manual process
* Refactor classes to a dependency-inversion pattern to make them testable
* Make test logs more readable and useful
* Port tests from a legacy framework to a better framework
* Refactor code to reduce duplication
* Delete dead code

Now that the program has been running for a few months and many dozen improvements have been merged in total, here are some of my observations about the program's effects.

**The codebase became less frustrating.**
Developers are well-known for complaining about their codebases and dismissing them as irredeemable.
Developers like to say that their codebase has lots of [technical debt](/blog/technical-debt), but often struggle to articulate exactly what the problems are.
The Quality Initiative forced us to tackle these kinds of questions head-on.
Upon closer inspection, lots of frustrating code is frustrating because of relatively simple things like untidiness, bad formatting, and illogical organization.
A simple refresh is often all that it takes to turn rage-inducing code into tolerable code.

**The pre-checkin process was streamlined.**
With every developer now expected to merge ~50 additional code changes every year, the pull request merge gate naturally came under higher scrutiny.
Before the quality initiative, our merge gate suffered from slow automated flows, high test flake rates, and delays in getting code reviews.
This would normally be a diffusion-of-responsibility sort of situation in which everyone wants the problems to be solved but nobody wants to be the one who puts in the work to solve them.
However, since developers didn't want to have their Quality Initiative changes blocked too long at the pre-checkin stage, improving the checkin pipeline became a rational self-serving thing to do.
Lots of early Quality Initiative changes targeted our pre-checkin automated flows; we fixed flaky tests, found ways to speed up other tests, removed unnecessary cruft from our build, and increased the parallelization in our pipeline.
People who worked in this area received a lot of gratitude from their peers.

**Low-productivity days became more salvageable.**
One of my initial concerns about the Quality Initiative was that it would inevitably take time away from other things or that it would be yet another high-urgency low-importance chore that gets in the way of deep focus work.
However, when I looked more closely at the times when I typically worked on QI workitems, I noticed that I often worked on them during the awkward lulls or lazy low-inspiration periods of my workdays.
Quality changes are a good fit for those awkward 30-60 minute open time slots that are too long for shallow work but too short for very deep work, as well as for lazy late afternoons when you don't want to start something big.
Rather than steal top-quality focus time, the Quality Initiative helped turn low-quality time slots into decent-quality time slots.

**Developer breadth has improved.**
Lots of developers express a wish to expand their technical breadth to other areas beyond their core specialization, but are unsure how to get started.
The Quality Initiative offered a valid excuse for exploring the codebase and digging around in less-familiar code.
I've had the chance to merge a few QI changes in components that I otherwise rarely touch; I have found these experiences to be good learning experiences and a refreshing break from routine.

**Inspiration proved to be a solvable problem.**
Inspiration was one of my initial concerns about the viability of the initiative, but this concern turned out to be overblown.
In a big codebase, anyone who goes around looking for problems is eventually going to find some.
Thanks to the practice of having meetings to share our changes, people get to see the sorts of things that other people work on and get to hear about potential future follow-up workitems that could be done in the same areas.
When I'm doing my non-QI work and I run into something that frustrates me, I jot it down in my notes; this list quickly became a pretty long one.
Even when inspiration is completely lacking, there are plenty of simple universal algorithms you can follow to find potential QI workitems (eg find the codebase's slowest test, find the codebase's flakiest test, find the codebase's most bloated file etc).

**A better balance was reached between short-term and long-term priorities.**
The balance between near-term and long-term priorities tends to flow in a cyclical manner.
There are periods where the team is preoccupied with shipping new features and less-urgent priorities are neglected.
Technical debt and growing pains start to accumulate; developers find themselves wanting fewer features and more time to work on scalability, maintainability, internal tooling, technical debt, and other non-customer-facing problems.
Developer teams often whiplash between periods where they think too short-term and periods where they think too long-term.
Neither position in the cycle is sustainable on its own; all software teams must do a mix of high-urgency and low-urgency tasks and a mix of short-term and long-term initiatives.
The Quality Initiative helped wall off a block in which the team may work on low-urgency, internal-facing, and long-term issues.
As far as technical debt management is concerned, the Quality Initiative is the closest thing I have seen to a sustainable routine.

**Team morale has improved.**
We're all merging pull requests more frequently than we used to, which is always a nice feeling; it's especially nice for senior-band developers like me who would otherwise find themselves doing less coding over time.
It's satisfying to see longstanding frustrations getting resolved, no matter whether it was by you or by someone else.
A big part of developer satisfaction involves not despising the codebase you work on; the Quality Initiative has prompted lots of improvements in this area.
Technical debt is no longer something insurmountable that was added long ago before you joined the team, but something manageable that is actively being reduced.
If something is frustrating you, you now have management's blessing to try solving it and a well-defined window in which to do so.
More than anything else, the Quality Initiative strengthened a sense of being in control.

Finding ways to organize software teams and organize their work is a timeless problem.
The Quality Initiative entered my life at a time when it felt like I had already seen every possible top-down management intervention.
The Quality Initiative brought lots of improvements to our codebase and developer culture while demanding relatively little in return.
It brought lots of quick and easy wins to a team like mine that was skeptical that quick and easy wins were still possible.
