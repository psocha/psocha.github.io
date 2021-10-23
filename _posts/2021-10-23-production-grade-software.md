---
layout: single
title: "What Does it Mean for Software to be Production-Grade?"
date: 2021-10-23 08:00:00 -0700
categories: workplace development
---

It's currently fall, which means that this year's cohort of (fully remote) summer interns has recently finished their internships.
I had a few interns in my org and participated in a 1:1 mentoring program with a few others.

Interns have gotten most of their prior software experience from completing school assignments and from building small projects on their own.
When interning at Microsoft, interns quickly realize that the [pace of development is slower than expected](/blog/code-change-frequency) and that all their decisions are much more thoroughly scrutinized.
At the end of their internships, interns often remark how writing software for the "real world" was a very different experience from their past programming work.

Both interns and their full-time mentors end up agreeing that going from writing code to writing production software is a big leap.
Anyone with industry experience has an intuitive sense of what the leap entails, but it's rare to hear anyone actually spell it out.
Having contributed both to production-grade and to non-production-grade software myself, here's a list of the main differentiators.
Whether you're making a website, a mobile app, or an invisible backend API, the same principles appear again and again.

**Production software must have readable code.**
Single-person software projects are notorious for having incomprehensible code that only the original author can understand.
Any impactful project is bound to have multiple contributors, so production-grade code needs to be compatible with a multi-developer model.
This means the file tree is logically organized, the code has sensible self-explanatory names, the formatting is friendly on the eyes, code comments are used appropriately, and each code change has a helpful commit message or equivalent documentation.

**Production software must be ready for error scenarios.**
Non-production-grade code can usually handle happy path scenarios but is less graceful in handling errors.
In contrast, production-grade software needs to accept that anything can fail and that errors are inevitable.
Production-grade software must be ready for its dependencies to return failure error codes or to throw exceptions.
Every dependency forces developers to confront new unhappy paths and to make decisions about what to do (usually some combination of aborting, retrying, or ignoring).
Failures are always disappointing for end users, but proper handling and communication makes them more tolerable.
It is virtually never okay to crash the program or to let it freeze forever.

**Production software must be debuggable.**
When something goes wrong, it must be possible for someone other than the code author to figure out what happened.
Programs must print logs and emit events that are neither too sparse nor too verbose; sub-categories like "error" and "status" logs should be applied correctly to notable events only.
In any production-grade environment, the program's log outputs are going to be huge; functionality for searching and querying quickly becomes essential.
The program needs to be debuggable for the end users too.
Users need to be able to tell apart user-at-fault errors from program-at-fault errors and they need to be given helpful instructions on how to recover.
Developers typically need to write troubleshooting guides for their users and different troubleshooting guides for themselves.

**Production software must be scalable.**
Production software must be ready to handle the "real world" with all its immense scale and complexity.
Design choices that are okay under a small load can become bottlenecks if the load is bigger.
At a minimum, software must avoid consuming all of the CPU, RAM, network bandwidth, and disk space of whatever computer is running it.
If a program's dependencies have performance problems, usage caps, or hard limitations, all of these constraints require workarounds at the program level.
End-to-end latencies must be kept low enough to be tolerable; common techniques for improving performance include caching, client-side processing, and asynchronous operations.
A single server and a single data store can quickly become a bottleneck once load starts growing; developers are usually forced to eventually split up their backend to allow horizontal scaling.
A one-in-a-million race condition that causes a crash is a tolerable problem at a small load, but at a higher load it will cause an overwhelming amount of user pain.

**Production software requires administrative capabilities.**
Developers spend much of their time working on the "meta" surrounding the system rather than on the system itself.
They need to have a way to view their application logs and metrics.
They need to have a way to view the program's data store and sometimes modify it.
Service operators need a way to perform common administrative and customer service tasks that involve changing the backend (eg quotas, approvals, feature rollouts, bans etc).
Many of these administration operations are sensitive and potentially damaging.
It's necessary to protect production touches behind a permission system, likely one with various layers for various types of jobs.
A service's internal administration portal can quickly become a major piece of software in its own right.

**Production software must be ready for chaotic users.**
Real-life software users are often very different from the idealized users that developers envision when writing software.
Real-life users usually don't know or care about the software's rules and limitations, so collectively they will push the limits.
All user input, especially anything free-form, absolutely needs to be inspected for validity.
Oddball users are going to come up with bizarre and unforeseen usage patterns that will stress the system at one of its bottlenecks.
Heavy users are going to overload your server with requests, so you need to have a system of throttles and usage caps to contain the damage.
Indecisive users are going to try editing or cancelling their operations while they are ongoing, so your transaction flows need to be ready for conflicting instructions.

**Production software must be secure.**
Users who provide data expect it to be stored responsibly and not be stolen or leaked.
Service administrators don't want to be impersonated by outsiders and users want to be protected from the actions of other users.
The problem of authentication is commonly solved with various cryptographic techniques (eg hashed passwords, certificates, API keys) that allow both users and the server to prove that they are who they say they are.
After the authentication layer, there needs to be an authorization layer, usually a multi-tiered access control system that assigns different permission requirements to different operations.
Making software more secure usually makes it less user-friendly, leaving developers stuck in the middle trying to strike a balance.

**Production software must be usable.**
In professional practice, user interfaces are usually designed by professional designers rather than by programmers because programmer-made UIs are usually terrible.
Rather than just dumping all the supported functions on the screen, UIs must be logically organized around common user stories.
The sizing, spacing, and positioning of UI elements must be visually balanced and give a sense of hierarchy.
UIs must be responsive and must give some kind of acknowledgment whenever a user performs an action.
If a user is being forced to wait due to backend limitations, the UI must still remain active and explain the status.
UIs need to stay graceful and presentable even under constrained conditions such as poor hardware and poor network connectivity.

**Production software should not break its existing users.**
In real-life scenarios, it is rarely okay to drop existing functionality because it's annoying to maintain or to throw away your data because you don't like your data store.
Production software needs to prioritize the functionality it has already released and which its users already depend on.
Production software must have thorough testing in place to ensure that regressions get caught before they're released.
Production software must have production health checks and alerts that can quickly detect whether production is unhealthy.
When a disruptive change such as a migration is unavoidable, developers spend lots of time thinking about how to make the experience as seamless as possible for existing users.
Developers yearn to stop needing to support outdated OS or platform versions, but the desire to deprecate must be balanced against the desire not to break a subset of the user base.

**Production software needs a deployment pipeline.**
Copy-pasting local build output files quickly becomes an unscalable strategy.
The build process needs to be automated and reproducible across various machines.
The build system must be able to manage any packages the program depends on as well as any dependencies of those dependencies.
Builds must be runnable in various environments (eg development, test, production) and each of these environments requires different config values.
Developers need to have tools to push builds to production and these tools must be able to report progress and failures.
Developers also need tools for common management tasks such as restarting server instances or adding new server capacity.

Computer science students mainly study foundational concepts like data structures and algorithms.
Software engineer interns often implicitly expect real-life programming work to be much of the same, only to realize that most software development happens higher on the stack.
Any real-life software solution is going to need many administrative layers above the core layer.
The core is usually stable and the outer layers are where the action is.

Any kid can run a lemonade stand business, but only a big team of skilled specialists can build a lemonade supply chain that can operate at a massive scale, handle all the chaos of the real world, and keep chugging along even when the managers are away.
Nobody can learn how to run a business entirely from the classroom and that's why internships are so useful.
