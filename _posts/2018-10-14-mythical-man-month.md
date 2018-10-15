---
layout: single
title: "Book Review: 'The Mythical Man-Month' by Fred Brooks"
date: 2018-10-14 10:00:00 -0700
categories: books review
---

_The Mythical Man-Month_ was the software engineering book most frequently referenced by my university professors.
I recently had the chance to finally read it.

![Mythical Man-Month](/assets/images/MMM.jpg){:class="img-responsive"}

The book was written in 1975, a time of giant batch-processing computers, low-level programming languages, and mountains of physical paperwork.
The book's old age is sometimes apparent and sometimes not.
_The Mythical Man-Month_ has sections on how to resolve squabbles between programmers about who gets memory buffer space and who gets time to test their code on a "real" computer.
Improvements in technology have thankfully helped make these problems moot.
However, _MM-M_ also touches upon some timeless topics, such as the software industry's dysfunctional project management dynamics, constant schedule slippage, inexorable accumulation of technical debt, and hopeless battles against complexity.
Those sections of the book are every bit as relevant today as they were in the 1970s.

Here are the book's main takeaways.

### Adding people to a late project makes it later ###

This observation, also called "Brooks' Law", is the most commonly-cited idea from the book.
The basic idea is that each new team member adds overhead cost to the team.
Additional team members increase the number of communication channels that need to be open and the number of one-on-one personal relationships that need to be maintained.
When a new person joins, it is also necessary for senior team members to set aside time to bring the new person up to speed.

In programming, parallelism is generally good, but only if the coordination cost is low and lots of the work is parallelizable.
However, in software development the coordination costs are always high and parallelizability is often low.
Even in the happy case where adding staff improves a team's productivity in the long run, there is inevitably a decline in the short run.

### Software development requires autocratic leadership ###

Most software bugs are the result of mismatching assumptions between modules and misunderstandings of the project's specifications.
A robust system needs internal consistency and conceptual integrity, but these are hard goals when multiple people are adding their own ideas.
Brooks therefore proposes that the core design of a system should be done by as few architects as possible, preferably just one, and that the architects should later have full authority to ensure their vision is faithfully implemented.

Brooks makes an analogy to a surgical team.
The lead surgeon is the undisputed leader of the surgical team and has the final say on all technical matters.
When a team has a supreme leader, project scope does not get partitioned and conflicts can be resolved unilaterally.
Many minds end up working together to do the will of one.

In a programming environment, the architect should be a generalist supreme leader with a full view of the project.
The architect can be aided by other generalist "co-pilot" programmers who do much of the coding work.
Other team members, typically the more junior ones, should get more specialized roles, such as implementing individual modules, maintaining internal tooling, or preparing a testing framework.

I have often seen this team dynamic play out in practice at my past work placements, always developing organically rather than by management directive.
The architect's authority comes naturally because the architect is the person best capable of answering tricky questions or investigating unknown problems.
Specialization also tends to be inversely correlated with seniority, with senior programmers getting a fuller view of the system and junior programmers typically working on a narrower subset.
In my internships, I often ended up being "the tools guy" or "the test guy", two specialized roles that Brooks describes in the book.

### Fail quickly rather than slowly ###

The first iteration of a project is always bad.
Brooks recommends accepting this reality and working around it, rather than denying that it will happen.

If your design or specification has fatal flaws, you want to find them quickly.
It is best to uncover and adapt to problems during the design and prototype stages, when the sunk cost is still low.
If design flaws are not found until system integration testing or release, reworking the system at that point will be prohibitively expensive.

Brooks recommends aiming for a fully-compiling minimally-viable system as quickly as possible, even if this prototype has little functionality.
All changes past that point should be iterative additions.
The system should be able to compile and pass its tests at all times.

In the decades since _The Mythical Man-Month_ was written, iterative programming workflows have almost completely replaced the waterfall workflow that was common in the 1970s.
Software companies are also increasingly making use of "pre-release" releases to get early feedback on their systems.
I don't know whether Brooks' proposal was considered radical in its time, but his advice is almost universally followed today.

### Don't neglect your documentation ###

Incomplete and outdated documentation has been a problem in the past and remains a problem today.
Despite its benefits, documentation has a tendency of getting neglected in favor of more urgent priorities.

If information is not written down, it exists only in the minds of the team members, where it can easily disappear or get distorted.
Written documentation reduces conflict and misunderstandings by providing a single source of truth.
A historical paper trail can be useful when a team takes interest in a question from the past, such as why a certain design decision was made.

Even if it is not read, writing documentation is still a constructive exercise.
The act of writing has a way of exposing holes and ambiguities in a writer's thinking.
Software is extremely complex and people often overestimate their understanding until forced to describe it.

### Watch out for perverse incentives ###

Many causes of corporate incompetence stem directly from perverse incentives in the corporate system.
Programmers often avoid documenting their decisions so that they don't have to defend them, especially if they see these decisions as tentative.
Subordinates often give overly-positive status reports to their managers to make themselves look good and to avoid manager intrusion into their work.
Many talented technical people leave their talents behind and go into management roles mainly for the greater prestige.
These kinds of perverse incentives result in questionable engineering decisions, schedule slippage, and staffing problems, respectively.

Brooks believes these problems are ultimately cultural and not technical.
A corporate culture that is open, unthreatening, and flexible allows people to communicate honestly and thus avoids many of these social problems.

### Be skeptical of magical productivity solutions ###

Software development productivity has improved significantly over the decades.
However, Brooks was skeptical in 1975 that programmer productivity would continue to improve as quickly as it had in the past.
He strongly doubted that new engineering tools or management methodologies could produce massive productivity gains that were geometric rather than incremental.

Scarce low-quality hardware, clunky low-level languages, and immature tooling once frustrated programmers and wasted their time.
Now that writing, building, and testing software can be done so quickly, programmers are increasingly free to spend their time on higher-level tasks.
Programmers now spend much of their time thinking about or discussing requirements, specifications, designs, and implementations.

Technology has made it faster to write software, but it has not made it faster to decide what software to write.
Deciding what to write is now the main productivity bottleneck.
Since this problem is human rather than technical, it has proven to be resistant against attempts at simplifying or automating it.

### Conclusion ###

In the raw technical details, _The Mythical Man-Month_ shows its extreme age.
It is hard not to smile when the book mentions that memory is renting at about US$12/kilobyte/month, or when it says PL/I is currently the most modern of all available high-level programming languages.

_MM-M_ is best seen as a book about project management and the human side of the engineering profession.
Its observations about software teams have largely stayed true over the decades despite enormous technological changes.
Software project management has evolved a great deal since 1975, yet companies still struggle to release functional software on time and within budget.
Teamwork and organization remain timeless and unsolved problems.
