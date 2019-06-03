---
layout: single
title: "Lessons Learned from Rewriting a Microservice"
date: 2019-06-02 10:00:00 -0700
categories: development
---

The full service rewrite is the ultimate software engineering fantasy.
A rewrite offers a chance to wipe out all technical debt and redesign a system perfectly from the foundation.

Fantasy aside, the software engineering blogosphere mostly takes an overwhelmingly negative position against rewrites.
A quick web search will give you many bloggers who say that a full rewrite is always or almost always a bad idea.
These bloggers cite factors such as the [loss of accumulated knowledge](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/) or the [high likelihood that past mistakes will be repeated](https://daedtech.com/the-myth-of-the-software-rewrite/).
The hardliners concede that rewrites may occasionally make sense, but only if a very long list of conditions is met.

- Avenues for incremental improvement in the original service have been exhausted
- The future feature roadmap would be impossible or prohibitively expensive to implement on the original service
- The rewrite would be written in a better programming language than the original
- The rewrite would have a much more robust and elegant design architecture than the original
- The rewrite would be more testable, debuggable, and verifiable than the original
- The organization doing the rewrite is secure and stable enough to accept short-term setbacks for long-term gains
- The scope of the rewrite is limited and clearly-defined

At my day job, I was involved in a situation in which all of the above criteria were applicable.
I therefore ended up being part of a long-term project to rewrite a badly-aging component of our service.
Here are some things I learned from the experience.

**Rewrites follow Hofstadter's Law on a massive scale.**
All software engineers know Hofstadter's Law, which states that everything takes longer than expected, even after you've accounted for Hofstadter's Law.
If a minor bug that was supposed to take one day ends up taking two days, it's a huge delay in fractional terms but not in absolute terms.
However, when a multi-month rewrite project experiences multi-month delays, the stakes are much higher.
Short of building an entirely new service completely from scratch, rewrites are the largest and most complicated of all coding projects.
The size and complexity of an enterprise-grade microservice can be unfathomable to even the most senior engineers.
When a project's complexity is significantly underestimated, the required completion time will be significantly underestimated too.

**Code completion is just the beginning.**
A basic prototype is not a 90% completion checkpoint or even a 75% completion checkpoint - it's more like a 40% completion checkpoint.
Business logic represents only a small fraction of most production codebases.
Production software needs to be much more than just a program that gives expected outputs to expected inputs.
Production software must also have decent logging, monitoring, metric collection, configuration, scalability leeway, performance optimizations, input validation, error handling, security measures, self-recovery mechanisms, load management, and deployment infrastructure.
It is very common for engineers, [especially more junior ones](/blog/intermediate-developers), to underestimate both the scope and importance of these seemingly tangential concerns.
A sloppy prototype is easy to write quickly; most of the development time will be spent converting the prototype into a production-grade service.

**Beware the two-track life.**
The world does not just sit still while you do your rewrite.
The old codebase needs to be maintained until it is out of commission.
If new business features are added to the old service, you will need to ensure that the new service will have them too.
If a bug is found and fixed in the old codebase, you need to check if the new service is vulnerable to the same bug too.
Duplication of work adds to the cost of a service rewrite.
To save on the cost of duplicate work, you will often decide to implement some future planned features only on the new service and not on the old one.
However, this strategy ties the fate of the feature to the fate of the rewrite.
If a rewrite ends up delayed, so will the rollout of any features designed only for the new service.

**Timidity and caution will prevail.**
Since a rewrite is such a big investment, the biggest fear of engineers working on a rewrite is that the new service will be worse than the old one.
Despite all efforts, it is typical for newly-finished rewrites to do worse in integration and performance tests than the originals they're supposed to replace.
It is very demoralizing to get beaten by a legacy codebase that you've always regarded as horrible.
A rewrite team will err towards avoiding embarrassing themselves.
They will test the new service very thoroughly for a very long time before going out to production, making lots of minor improvements along the way.
They will likely avoid starting a production rollout until the new service is significantly better than the old one, even though it is optimal to start the rollout as soon as they have exceeded parity.
Any production bug, no matter how minor the bug is and no matter how bad the old service is, will be treated with a _"the rollout cannot continue until this is fixed"_ level of severity.
Only after a long stretch of time with no production problems will the team feel confident enough to crank the rollout all the way up to 100%.

**Are rewrites worthwhile?**
A rewrite project inevitably comes with challenges, delays, and frustrations.
Like nearly all non-trivial software projects, rewrites always end up slower, murkier, and muddier than expected.
Once a rewrite is finished, future development work on the new service will be quick, but this comes naturally when the engineers maintaining the service are the same ones who wrote it.
Increased speed and comfort in the future must be balanced against increased workloads in the present.
It's ultimately a question of short-term pain versus long-term gain, albeit one where the short-term pain is typically underestimated and the long-term gain is typically overestimated.

Are rewrites worthwhile?
It's a case-by-case question and one can never be certain about the conclusion.
The only way to be certain is to compare the rewrite timeline with a parallel timeline in which the rewrite never happened.
However, with good design and good management (which I'll discuss in a separate post), the likelihood of a successful rewrite can be greatly increased.
