---
layout: single
title: "The Historical Context Test for Technical Debt"
date: 2020-04-25 10:00:00 -0700
categories: development
---

Technical debt is often a nebulous and hazy concept.
Almost every engineer would agree that the codebase they work on is full of technical debt, but those same engineers would often have trouble articulating what exact debts the codebase has or what workitems could pay it down.
Many complaints about technical debt aren't really about technical debt at all, but rather about high codebase complexity.

Technical debt is the result of past decisions causing present-day pain.
It is a mismatch between the solutions to past problems and the solutions to present-day problems.
If the codebase were to be rewritten from scratch today, the current codebase's technical debts would help identify the decisions that should be made differently with the benefit of hindsight.
Hindsight is critical when evaluating technical debt, since some engineering decisions once thought harmless can later turn out to be painful, while other decisions once thought risky can turn out to be of little consequence.
Technical debt requires both present-day pain and past-day hindsight.
Combining these concepts leads to a definition like the one below.

**Technical debt is anything that makes sense only if you know the historical context behind it.**

If a past engineering decision fails the "make sense" test, it's a sign that the past engineering decision is now a bad one.
If this past engineering decision can only be explained or justified by invoking the past (the "historical context test"), that's a sign that the decision looked reasonable at the time.
If a decision starts off looking reasonable but then goes on to cause problems down the road, it means that decision sacrificed the future in exchange for the present.
Just like with a financial debt, the present self reaps the benefits while the future self gets the bill.

For illustration, here are some non-sensitive examples of technical debt from the main codebase I work on nowadays, [Azure Batch](https://azure.microsoft.com/en-us/services/batch/).
New engineers dive into our codebase and tooling expecting everything to be nicely labelled as "Azure Batch", but instead they find a convoluted mess of names including "rd", "reddog", "WindowsAzure", "Azure Task", "WATask, "XTask", and "WABatch". 
These names fail the "make sense" test and leave our engineers confused, causing us present-day pain as they struggle to ramp up on the codebase.
The current situation is impossible to justify without invoking the past.
In this case, the historical context is that Azure has existed under many past times including "Red Dog" (old internal codename) and "Windows Azure", while the Batch service itself was previously called the Task service.

For another example, Azure Batch VM pools allow customers to choose a mix of "dedicated" (regular) VMs and "low-priority" VMs (VMs that are cheaper but with the caveat that they can be preempted from you at any time).
Dedicated and low-priority VMs may look like equal partners in our UIs and API schema, but they are not equal partners in our backend codebase.
In much of the service code, low-priority feels like a tack-on feature; our engineers get confused when they see our table columns are "NumVMs" and "LowPriorityNumVMs" instead of the expected "DedicatedNumVMs" and "LowPriorityNumVMs".
Only the past can explain the present; the explanation in this case is that Batch pools initially only supported dedicated VMs and that low-priority VM support was added a few years later in subsequent API releases.
It's important to note that requirement history is a major driver of technical debt and that many causes of technical debt cannot be foreseen in advance.
When Batch was first released, low-priority VMs didn't even exist yet as a concept in Azure.
At the same time, preemptively preparing the service for additional VM types would have been viewed as over-engineering.

Examples of these questions and historical explanations exist across all codebases.

Why does this module have no test coverage?
*When its scope was smaller, it was once simple enough to test manually.*

Why does this module have so much spaghetti code?
*The module's scope and responsibilities have changed a lot from when it was originally architected.*

What's all this dead code doing here?
*It's not dead; we need it to support a rarely-used endpoint on some really old API versions we haven't deprecated yet.*

Why don't we have proper partitioning?
*Our load used to be smaller than now and we didn't need it back then.*

Why is our logging and monitoring so bad?
*We were in a hurry to get our product out the door, so some internal tooling had to be neglected.*

It's important to note that technical debt is very rarely the result of outright stupidity.
Technical debt often arises from factors that were unknowable and unforeseeable at the time, the most common being future changes to requirements.
Engineers who are cutting corners (usually for time-related reasons) are usually aware that they are cutting corners.
At the end of the day, an engineer's job is to make satisfactory decisions in the face of a wide set of constraints.
Some decisions stay satisfactory into the future while others do not, but nearly all decisions are satisfactory at the time they are made.

When something in a codebase causes pain, the key test is to ask why the codebase is the way it is.
If the answer to "Why?" only needs to invoke the present, it's a sign that the pain point is not technical debt, but rather just complexity, requirements, or possibly bad engineering.
However, if "Why?" cannot be answered except by defensively invoking the past context in which the decision was made, this is the key sign that the problem is technical debt.
