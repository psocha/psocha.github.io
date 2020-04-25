---
layout: single
title: "The Engineer's Duty to be Invisible"
date: 2020-03-28 10:00:00 -0700
categories: development career
---

It is said that bad technology is distracting while great technology is invisible.
Anyone who works in software (or any business for that matter) has experienced being underappreciated when things are going well and getting their competence questioned when things are going wrong.
It is discouraging and soul-crushing when all the feedback you get is negative, but at the same time, it is a sign of progress and competence.
When all your feedback is negative, it means you may have reached the point where your service is taken for granted.

As I write this, the COVID-19 pandemic is sweeping the world and has disrupted the lives of billions of people.
The pandemic has shown us that services we considered to be infallible are not infallible after all.
We took it for granted that department stores would have toilet paper until panic-buyers all sought it at the same time and the supply chain couldn't react quickly enough.
We took it for granted that the healthcare system would be available for us until COVID-19 started pushing hospitals beyond their capacity.
We took it for granted that the school system would take care of our kids Monday through Friday until schools started closing down.
Using software terms, each of these services is guilty of an outage, a lapse in its uptime and availability.

The world of software is no stranger to outages and periods of degraded service.
Every software user has experienced things like lag, mysterious errors, periods of downtime, and weird corrupt states that are hard to get out of.
Software companies regularly make new releases that still have lots of kinks to iron out and which break functionality that was previously working.
Nothing can be fully trusted to be reliable.
Even software engineers accept this - whenever we write calls to external services, we wrap our calls in a try/catch block and make a retry loop to be ready for the inevitable errors.

Software engineers may think a bit of unreliability is okay, but the physical world disagrees.
Suppose I have a severe case of COVID-19 and I check in for emergency care at my local hospital.
I want to be able to state my situation to the hospital's receptionist and then have the hospital take charge of my care from that point onwards.
I don't want the receptionist to freeze up and go unresponsive, to be told that I had made an invalid request, to be told that the hospital is unexpectedly closed for an unclear period of time, or to be told, *"An unknown error has occurred. Please try again later."*

The pandemic helped remind me as a software engineer of what an "outage" looks like when it happens in the physical world.
When a service fails to fulfill its side of the contract, trust is lost.
Rather than think about a service purely based on the contract it fulfills and the functionality it provides, I now have to think about how it works and how it is implemented.
In the past I went to the grocery store at all times of day.
However, in response to the recent shortages, I now go in the early mornings because the new shipments arrive at night and the shelves tend to be fullest in the mornings.
This is a grocery store implementation detail I shouldn't need to care about.
However, since the grocery store has suffered a breach of contract and broken my trust, I now need to think about how to improve my odds of getting what I want.

In the end, uptime, availability, predictability, and reliability are the most important features of any service.
Good services are predictable rather than temperamental, mundane rather than quirky, and quiet rather than attention-seeking.
Good services create simplicity instead of complexity and clarity instead of confusion.
The best services are the ones you never need to worry about.
In short, the best services are invisible.

The world of software regularly fails to live by these principles.
Instead of being invisible, most software tries to be as flashy and as visible as it possibly can.
Modern software is always sending distracting notifications, bragging about its newest features, trying to get you to sign up for other services in the vendor's ecosystem, and reshuffling its user interface every few months.
In the meantime, most software is plagued by performance and reliability problems.
With few exceptions, most software has not ascended to the point where it is an invisible service that we can take for granted.

Going back to the brick-and-mortar world, let's consider some successful gadgets like the microwave oven, the refrigerator, and the dishwasher.
In all my years living in my current apartment, I have never experienced an issue with any of my household appliances.
All of them have perfect uptime and all of them always fulfill the contract I expect from them.
These technologies are so good that I don't need to think about how they actually work; I can think of them purely in terms of their function.
The contract they fulfill allows all their complexity to be abstracted away.
Unlike most modern software, home appliances make life simpler rather than more complicated.
My microwave has never forced me to make an account, failed to respond to my input, rejected my input as invalid, made me look at a loading spinner, sent me bright red notification pings, gone offline to install updates, redesigned its user interface for no reason, forced me to restart in order to fix a caching issue, sneakily added me to an email newsletter, or leaked my personal data to third parties.

Why can't our software be as good as our supply chains and our home appliances?
In theory, software should be more dependable than any technology that came before it.
Unlike institutions and supply chains, software is immune from the fallibility of human decisions and can act in a consistent and predictable manner.
Unlike physical gadgets like cars and microwave ovens, software is immune from physical wear-and-tear.
Unlike most physical items that are given away and become inaccessible, software can be monitored from afar and updated remotely if problems arise.

There are many reasons why software is more prone to high-visibility failures than most other services.
The main reason software development is so difficult is because it is so complex.
A user's contract with an online banking website is far more complex than a user's contract with a microwave oven.
Compared to simple contracts, complex contracts have more ways to fail and more ways in which to be misunderstood.

Complexity is inevitable but the cultural problems of the software industry are not.
From a software engineer's perspective, adding new features to software is impactful, visible, and pleasurable work.
On the other hand, we view bug fixes and firefighting as stressful, unsatisfying, invisible, and soul-sucking.
We view customer emergencies as a distraction from feature work and we often do the bare minimum to make the situation tolerable again.
This whole time, customers are pleading for fixes and improvements, but we rarely hear them because we're insulated from customers by managers and customer support.
In the meantime, our managers call for more features and more functionality; we are happy to oblige because writing our own new code is more fun than fixing other people's old code.

The COVID-19 pandemic has already had major effects on the world of software.
In the new stay-at-home world, major services such as Microsoft Teams, Slack, Messenger, WhatsApp, YouTube, and Netflix have all seen sudden increases in usage that would have been unimaginable even six months ago.
When usage goes up, pre-existing bugs, scalability problems, and performance issues suddenly become more apparent and more urgent.
In every overwhelmed service, regular feature development is being put on hold in favor of ensuring the service stays up.
In-progress and unreleased features that were once labelled as "urgent" by management are suddenly not urgent anymore.

A crisis forces people to re-evaluate what their priorities truly are.
Software companies habitually neglect reliability until suddenly the world is on fire and reliability turns out to be the only thing that truly matters.
The crisis has re-affirmed what has always been true but underappreciated.
Your most important customers are the ones you already have, not the ones you wish to win over.
Your most important features are the ones already in production, not the ones planned for the future.
Your customers' greatest source of frustration is unusability and unreliability, not the fact that some niche features are doing to get delayed.

Putting this mentality into long-term practice requires a shift in priorities.
We as engineers must place a higher value on our customers' problems than on our personal ambitions.
We must swallow our pride and accept that our customers don't care about our software nearly as much as we do.
We must start viewing ourselves as maintainers and operators first and foremost, rather than as creators who do some maintenance work on the side.
We must accept that our customers would rather have something quiet that works than something dazzling that doesn't work.
The end goal of an engineer should be to be invisible.

At Microsoft, senior executives are regularly reminding us that in the COVID-19 crisis, the medical response and the world economy are both relying on our software.
Uptime and reliability take precedence over all other priorities.
If we play the situation right, we can help make our software an invisible pillar of stability in an unstable world.
We all yearn for a world in which we can trust our software as much as we can trust our microwave oven - this crisis is a good time to help make this happen.
