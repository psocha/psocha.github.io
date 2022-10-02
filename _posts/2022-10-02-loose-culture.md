---
layout: single
title: "Why is the Culture of Software Engineering So Loose?"
date: 2022-10-02 10:00:00 -0700
categories: career
---

A few months ago I finished reading the book [Rule Makers, Rule Breakers](/book-summaries/rule-makers-rule-breakers).
The book's central idea is that there exists a spectrum of tight cultures and loose cultures; tight cultures are strict and by-the-book, whereas loose cultures are permissive and trusting.
It's a universal idea that just about everyone can relate to.

In my software engineering career spanning six different employers, I have observed that software companies are on the loose end of the tight-loose spectrum.
_Rule Makers, Rule Breakers_ even names tech startups as a textbook example of a loose workplace.
Everyone is on a first-name basis with everyone else.
Dress codes are virtually non-existent.
Work hours are often not well-defined and not tracked.
It's common to join meetings 1-3 minutes past the official start time.
Deadlines and promised delivery dates regularly get delayed with impunity.
Bosses spend most of the time creating clarity and giving guidance rather than barking orders or making threats.
Documentation, standard procedures, and paper trails are usually incomplete and sloppy.
The chain of command in theory and the chain of soft influence in practice are often quite different.
Direct personal blame and personal criticism are extremely rare.
Employees are incentivized with carrots rather than with sticks.
Employees knowingly and intentionally break the industry's so-called "best practices" all the time.
Compared to other industries, the software industry was less heavy-handed about getting workers to return to the office as the COVID-19 pandemic started to wane.
Software companies like to portray themselves as scrappy underdogs trying to disrupt old and established ways of doing things.

Moving from the tight culture of public school to the looser culture of software engineering was a culture shock for me and forced me to unlearn many of my [public school habits](/blog/public-school-habits).
An [old blog post](/blog/duty-to-be-invisible) of mine criticizing the industry's casual approach to software quality can be interpreted as a criticism of the industry's looseness.
In a more recent blog post, I described an internal [quality initiative](/blog/quality-initiative) that tightened my team's culture a little bit with positive results.
Lots of debates that appear to be about other topics are really about tightness and looseness.

We know the software industry is culturally loose; the question is why.
Looking at the industry from the outside, you could easily predict that the nature of the business would force software companies to adopt a tight culture instead.
Software engineering is precise work with low margins of error and low tolerance for sloppiness.
Software development is a team activity in which groups of people need to coordinate closely, especially when dealing with the implicit contracts between different modules.
Team lapses such as outages, app-breaking bugs, or security breaches can be costly from both a revenue and a reputation perspective.
Requirement discussions, design discussions, and code reviews offer lots of opportunities for tough interpersonal conflicts that someone may eventually need to resolve by force.
The day-to-day work is computer-based and solitary, making it easy for engineers to slack off or defy orders if they are not monitored.
Let's look at each of these background factors in turn.

### Low Margins of Error ###

Computers are exact and literal-minded; the contract between programmers and computers is very much a tight culture.
As a software engineer, you can break any codebase by replacing a single keystroke somewhere with another.
However, you're probably not going to get away with it.

Out of the theoretical set of all possible code changes to a codebase, nearly all of them are invalid and would immediately be rejected by a compiler.
Out of the subset that's valid, an even smaller subset would also pass the project's test suite.
Out of that subset, an even smaller subset would also pass manual code review by a codebase owner.
With so many safeguards in place, the likelihood of introducing a breaking change is significantly reduced.
Computers have low margin of error, but this same low margin of error can be used to help spot the mistakes of programmers.

Software engineers have the ability to catch mistakes early before they have impact in the real world.
Compared to other engineering domains, software engineers have an easier time proving that what they are proposing is beneficial, or at least not harmful.
Thanks to this ability to validate, software engineers have an easier time giving each other the benefit of the doubt, a key element of a loose culture.

### Close Interpersonal Coordination ###

Cultures tend to be tight when groups of people need to work in lockstep and it's risky to let everyone wander off and do their own thing.
In software engineering, most of the toughest problems happen at the integration phase when trying to get different modules to play well together.
If a client and a server have differing expectations of one another, serious bugs can result.
Given this reality, shouldn't the software industry have a culture of engineers being forced to very clearly spell out their API contracts and expectations?

The typical modern software project is built on top of a confusing pile of packages and makes network calls to a wide variety of API endpoints.
Most of a software project's dependencies are owned and operated by faraway strangers in other organizations or in the open-source community.
Given such a dispersed setup, engineers have little room to influence each other's contractual decisions and need to accept whatever they're given.

API writers say, _"This is our API surface. Deal with it."_
API callers say, _"This is our bizarre usage pattern. Deal with it."_

The service I work on in my day job has a JSON Swagger spec whose line count is somewhere in the low five figures; nobody besides our compiler has ever read the whole thing.
Engineers complain about a lack of documentation all the time, but when documentation is available, only small subsets of it are ever of any interest; much of the rest is inferred through intuition.
When a module's behavior in practice differs from its behavior in documentation, the results observed in practice are readily accepted as the reality.
Engineers know that external calls are unreliable; no matter what the documentation or the code owners promise, they will still write some safety measures such as retry loops, try-catch blocks, and error fallback logic.

In short, tight collaboration and tight contracts are not the norm in the software industry.
For better and for worse, this means that most software engineering work is solitary and that most acts of collaboration are done silently and unknowingly between strangers.

### Costly Mistakes ###

Cultures tend to be tight in contexts where mistakes are costly.
When one mistake can ruin you, there is a strong incentive to dot the i's and cross the t's, to be risk-averse, to second-guess the intentions of others, to prepare for scenarios that may never happen, and to leave as little to chance as possible.

In software engineering, the worst things that can happen on the job are server-side outages, security breaches, and the inadvertent release of bugs that make the software unusable.
The software industry has been shifting away from one-time ready-aim-fire release models to more flexible service-based models where they can freely make updates to code after it's already in production.
Now that it's easier than ever to fix defects in production software, the stakes have fallen, and the culture surrounding software quality has been free to loosen.
One exception to this trend is probably security and the fear of breaches; my impression from the field is that security is being taken more seriously nowadays and the culture there is tightening.

Last but not least, customers have come to have low expectations for consumer software.
When Microsoft Windows starts acting all erratic and temperamental, we just restart it.
When websites don't load properly, we just refresh the tab.
When our phone apps display their loading spinners for too long, we shrug and try again another time.
People complain about software brownouts and bugs all the time, but it's almost never enough to motivate them to defect to a competitor's offering.
Most of these degradations are forgotten almost as soon as they are resolved.
Software companies are largely in the business of selling functionality rather than quality.
Since software companies can get away with quality lapses most other businesses cannot, quality can take a backseat to other priorities and the culture surrounding software quality can loosen.

### Intractable Conflicts ###

In contexts where there can never be any ambiguity about who is in charge and whose word takes precedence over others, tight hierarchies tend to form in response.
Do conflicts between software engineers fit this label?

The most common arenas for interpersonal technical conflicts between software engineers are code reviews and design document reviews; these typically take the form of the author-owner posting something and reviewers writing comments on it.
In the vast majority of cases, the author agrees with the reviewer and makes a change in response.
If the author disagrees with the reviewer, the two of them can usually settle things on their own by discussing the technical merits of the proposed options.
If there is still disagreement, authors have lots ways to cop out, including saying they'll put a problem out of scope for now and revisit it later, pointing out that their proposal can easily be reversed if needed, or pointing out that the issue is too low-stakes to be worth the trouble.
Very few software engineering conflicts require an appeal to authority or the involvement of a tie-breaking mediator.

Software engineering often seems to get by without chains of command or formal authority figures.
The open-source community has created remarkable projects despite dealing with a hodgepodge of stakeholders and despite having leadership figures that are mostly informal.

### Ease of Defecting ###

When I got my first software internship, I got a computer all to myself with full admin permissions and none of the deny-listing or snooping software typical of public school computers.
People rarely checked in to see how I was doing and whether I was slacking off.
I could use the computer for non-work purposes or take long breaks and nobody would notice.
My 18-year-old brain was boggled by the amount of trust that was placed in me.

Why do software companies so readily trust their software engineers when this trust can be so easily broken?
Perhaps a better question is this: what would it look like if engineers weren't trusted and were instead treated like lazy and rebellious public school kids?
You can record everyone's computer activity for auditing purposes, but the audit paper trail would quickly become overwhelming.
You can prohibit all sorts of things, but this will create a stifling and creativity-suppressing culture.
You can wrap everything up in bureaucracy and approvals processes, but that will slow everyone down.
You can try micromanaging and second-guessing the decisions of your engineers, but even a mild second-guessing habit will take over most of your workdays.

The number of decisions software engineers make every minute of every workday is enormous.
It might not feel overwhelming on a normal day, but decision overload is especially apparent when you're [onboarding new engineers](/blog/onboarding-new-engineers) and you find yourself having to make a subset of their day-to-day decisions on top of your own.
Making lots of decisions is fundamentally an engineer's job.
Engineers need to be trusted because there isn't much of an alternative.

Due to the high stakes involved, finding trustworthy people is critical.
Software engineering may have a loose culture, but the culture surrounding software engineering recruiting is very tight.
Big Tech has a mostly-well-deserved reputation as a monoculture of millennial White and Asian men with upper-middle-class upbringings and degrees from top-50 schools.
When mistakes are so costly, extreme risk aversion is the norm, and engineers pick candidates similar to themselves.
When my university-age self was writing side projects and preparing for esoteric coding interview questions, it was often less about developing as an engineer and more about making myself a palatable candidate who can pass off as an insider to the tech industry's subculture.
The tech industry is willing to trust you, but only after you have scaled a sometimes-arbitrary wall.

## Conclusion ##

The tightness of a culture tends to be proportional to the amount of threats it faces.
Most of the domains that Big Tech works in face few threats nowadays, especially given the rise of continuous integration and continuous deployment.
Software engineering mistakes have become easier to avoid, easier to detect, easier to discuss, and easier to reverse.

Thanks in part to the work of past software engineers who worked in tighter cultures than those seen today, today's risks and today's stakes are lower than those of the past.
The looseness of the modern software industry is a side effect of some hard-won technical victories.
