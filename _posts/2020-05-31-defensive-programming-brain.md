---
layout: single
title: "Defensive Programming for the Brain"
date: 2020-05-31 10:00:00 -0700
categories: career personal
---

As software engineers, we put lots of effort into defending our services from getting overwhelmed.
We apply partitioning and load balancing to protect individual servers from too many requests.
We throttle excessive requests, validate and reject malformed requests, and return timeout errors for requests that prove too much work.
We do expensive tasks inside of asynchronous or background operations rather than create a blocking operation on the spot.
We put quotas and limits on our services to put caps on how much utilization we can expect.
Lastly, we monitor our service load in real time, sounding the alarm when our servers struggle from high CPU usage, low memory, high latencies, frequent crashes, or frequent request failures.

When we take such defensive measures, our goals are to avoid lag and to avoid unplanned downtime of the service.
We implicitly accept that our programs are fragile and delicate things that must be protected from the outside world.
Even though computers have amazing calculating power and extraordinary memories, we accept that they'll probably do something stupid and self-destructive if we ask too much from them.

If we're worried about our servers, we should be extra-worried about ourselves.
Unlike computers, our brains are not hard-working, not meticulous, and not indistractable.
Our calculating speeds and our long-term memories are much worse than those of computers, meaning that our thresholds for being overwhelmed are much lower.
At the same time, our brains are unpredictable and temperamental, making them hard to monitor and allowing a wide variety of error states.

A software engineer's work subjects the brain to a torrent of information it is not always well-adapted to handle.
It is blind and neglectful for us to work on preventing computers from getting overwhelmed without applying similar defenses to ourselves.
Fortunately, many of the principles we apply in defending our servers can readily be applied to defending our brains.

**Don't seek extra stimulation.**
If you overwork your muscles, they scream out in pain and call for relief.
The overworked brain is different; it seems to have a habit of trying to maintain its current level of arousal, viewing reductions as boredom.
This is why during the lunchtime lineup to the office microwave oven, almost everyone will be on their smartphones; after the morning's stimulation, standing and doing nothing feels intolerable.
What the brain actually needs at this time of day is a break, a period of reduced input where it can clear out its clutter and perform a soft reset.
Your servers don't spent their quiet time sniffing around for more inputs and neither should you.
Like a computer restart, a soft reset of the brain inexplicably fixes many things.
When you're unsure whether or not you should get up and take a break, take it.
During your breaks, deprive your brain of input rather than give it the cheap dopamine hits it will likely want.

**Keep unwanted input out of mind.**
In software, the higher up on the stack you can stop an unwanted request, the better.
High-level measures like firewalls or throttling limits protect the core code more thoroughly than lower-level measures like programmatic validation.
Rather than get an unwelcome input and consciously shrug it off, the best approach is to never find out about the input altogether.
For office email, this means auto-archiving virtually every message not personally directed at you and liberally using the "Ignore" function on rambling Reply-All email chains.
For the office web browser, this means having extensions to block ads, recommendation panes and other potential rabbit holes.
For all devices, this means cutting out all push notifications except the truly urgent ones.

**Optimize for few "runtime" decisions.**
The existence of "decision fatigue" is one of the main ways our brains differ from computers.
Decisions are why a YouTube session feels like a "break" while playing a game of chess feels like "work", even though YouTube is a torrent of input bits into your brain while a chess game is merely a trickle.
Decisions cost willpower; every runtime decision you make saps at your willpower reserve until you are depleted [(book on this subject)](/book-summaries/willpower).
A depleted person is an ineffective wreck who falls for distractions, makes impulsive decisions, and procrastinates on anything that requires effort.
Having a stable background and home life is essential for long-term productivity.
As a university student with final exams, I was fanatical about keeping fixed routines for things like sleep, meal breaks, and exercise; I was doubling-down on normalcy during a time when normalcy often gets eroded and replaced with chaos.
To reduce cognitive load in my life, I have many borderline-eccentric habits such as maintaining identical weekly meal plans and taking the bus to work instead of driving.
It's best to think of the brain's executive center as a CPU that is extremely powerful but also has very low capacity and deteriorates over time.
The optimal strategy is to put life's routine matters on autopilot so that only the most interesting matters need conscious decision-making.

**Don't optimize for throughput.**
There's a certain feeling that when you're in the workplace on company time, you should make the most of every minute and make every moment productive in some way.
Our software does not operate on this principle.
During periods of low load, our software does not brood about its productivity level or guilt-trip itself about time-wasting.
However, engineers regularly do these things; the most common manifestation of the throughput fallacy is kicking off a build or test run, then trying to fill the time with an email check, then getting distracted and going down an email rabbit hole, then forgetting about the initial task after the build has finished.
At the macro level, the throughput fallacy causes short-sighted habits such as engineers neglecting their breaktimes, working during lunch, or failing to take sufficient vacation time.
We don't judge our software for its utilization efficiency as long as it meets expected uptime expectations and delivers business impact; we should judge ourselves the same way.

**Minimize context-switching and thrashing.**
Professional software does not pointlessly unload and reload partitions without due cause; we recognize that such operations are expensive and time-consuming.
Just as we avoid asking our computers to do too much multitasking and context-switching, we should avoid doing the same ourselves.
The brain's lack of multitasking and context-switching abilities has gotten lots of public attention in recent years and rightfully so.
The management strategy I have tried for this is to decide on the concrete purpose of my computer session before I sit down, then catch myself when I find myself wanting to switch to another task without finishing the first.
I've also made myself mindful of the moments when I start having more than about five browser tabs; when it happens, I purge out everything except the immediate task.
This kind of self-monitoring requires a substantial amount of self-awareness and cognitive overhead, but almost everything is cheaper than repeated context-switching.

**Do your thinking in advance.**
A major key both for productivity and for peace of mind is to be ready and prepared.
Google does not go into a panicked and sloppy scramble when it receives search requests because it spends lots of background async resources on cataloguing and organizing the web's information; its responses are immediate and relatively inexpensive.
Students don't go into a panicked and sloppy scramble when they start their exams (at least good students don't) because they spent some study time thinking about the subject beforehand; they work from memory rather than learn the entire course on the spot.
Both people and computers can think at much greater depth when time constraints and urgency aren't creating undue pressure.
No computer algorithm or person can be fully prepared for every decision that comes their way.
However, basic tasks like preemptively getting organized and deciding on core guiding principles have lots of upside at very little cost.
Doing your thinking and learning in the background rather than on the spot is good both for effectiveness and for happiness.

**Give non-urgent matters non-urgent treatment.**
High-end production software generally avoids performing non-urgent tasks immediately if they can be done at a leisurely pace in the background.
On the other hand, people have a tendency to overestimate the urgency of most matters and to give urgent treatment to matters that don't deserve it.
Many short and fleeting tasks get handled unnecessarily quickly out of fear that they will end up forgotten if not immediately attended to.
My current habit is if I get knocked out of the flow by an IM or by a self-distracting urge to check something, I jot it down immediately on my paper todo list (avoiding the possibility of forgetting), stand up from my desk to wander around a bit (resetting my brain state), then decide after sitting back down if the interruption deserves an immediate response (avoiding mis-prioritization).

The nice thing about defensive programming is that it is good both for productivity and for overall perceived well-being.
Like any habits, defensive measures cost some willpower upfront to set up, but afterwards becomes automatic.
