---
layout: single
title: "Avoiding Getting Frazzled as a Software Engineer"
date: 2019-11-03 10:00:00 -0700
categories: career personal
---

Software engineering can often make your brain hurt, especially if [your brain is wired to over-process everything it receives](\blog\highly-sensitive-programmer).
Information overload is perfectly understandable; codebases are complicated and software teams have lots of communication overhead.
Some of the complexity is a mandatory part of the job but some of it exists only because of our own mismanagement.

Nearly every software engineer would confess to wasting too much time on time-sucks like email and chat.
Nearly every software engineer complains about excessive distractions and a lack of focus time.
We complain about information overload yet we compulsively check our emails at the slightest sign of idleness and spend much of our downtime browsing our phones.
Instead of calming our overstimulated brains down during our breaktimes, we double down on our overstimulation and keep revving our brains further up.
We briefly feel productive but our results turn up disappointing and we feel exhausted afterwards.
It turns out we had spent our time sorting through self-inflicted clutter in our heads instead of actually getting things done.
We know these habits are bad for us and yet we don't stop.

The brain is wired to value and to seek out novel information.
This habit is helpful only when the obtained information proves to be useful.
Most of the information in the daily barrage of emails, chats, and documents is transient crud.
It is relevant for only a few people and it will likely be completely forgotten by tomorrow.
The brain doesn't care about the unimportance of this information.
It will continue diving deeper down an unproductive rabbit hole in the hope of finding something useful.
It is easier than ever to fall for the over-preparation trap, gathering knowledge that will never be used and preparing for situations that will never happen.

As programmers, we often fall for the fallacy of thinking that the human mind is like a computer.
Unlike a computer, the brain is not some infallible command center capable of processing a torrent of inputs, organizing huge amounts of data, and applying due diligence to every task it is asked to do.
The brain has limited cache space, low bandwidth, high flakiness, flawed prioritization, and low data retention.
To be happy and productive as engineers, we must play to our brain's strengths while leaving the frazzling work to the computers.

Here is a list of strategies I've successfully applied to reduce load on my brain at my day job.

**Turn off most notifications.**
Every app thinks that it's the most important app on your device and that it's the central hub for all your computer activity.
By default, nearly every app grants itself the right to bombard you with banners, push notifications, blinky lights, and other distracting gimmicks whenever something happens.
Notifications are still distractions whether or not you indulge them, so it's best to disable anything you can get away with.
In my case, I disable all email notifications and all IM notifications except for direct messages and direct mentions.

**Aggressively hide emails.**
As developers, when we need to spend several hours a week putting out production fires, we get outraged and we demand time for fixes and improvements.
Thanks to a prioritization bug in our brains, we do not get equally outraged at the idea of wasting several hours a week reading through emails.
In every job I've had, I subscribed to a bunch of mailing lists on my first day, ranging from useful team groups to noisy automated notification dumps.
I split off some of the chatty groups into their own folders but I rarely consciously revisited why my email policies were arranged the way they were.
For something used as often as email, your policies should be intentional and regularly revisited.
Any groups that are rarely relevant should be auto-archived and hidden from view unless you actively search for them.
Our brains have deep fears of missing out on information that might be important, so we hoard emails to an irrational degree.
Hoarding is not harmless because every email you read forces your brain to do an expensive context switch.
The central goal of an email management policy should be to minimize the number of emails you actually read.

**Maintain a paper task list.**
One common way to get frazzled is to have your task list grow faster than you're able to work it down.
Emails, alerts, incident tickets, code reviews, and other tasks come at irregular and unpredictable intervals, meaning that your to-do list is prone to sudden spurts of growth.
Much of your mental bandwidth then has to be devoted to mentally managing your task list rather than actually focusing on the tasks at hand.
If you jot down every task as you receive it, you can temporarily set the new tasks aside without worrying about whether you'll forget them if you don't do them immediately.
This is best done with a paper notebook because it takes very little setup time (no need to boot up your laptop and open your notes app) and because a paper notebook is easy to take anywhere.

**Check email last, not first.**
Email is the most common source of distractions and new tasks.
If email is the first thing you check every time you sit down at your desk, you will immediately be put into a reactionary mindset, likely forgetting the task you originally intended to do.
Email is best checked at the end of your sitting session, right before you stand up to take a break.
This way, you can jot down any followup tasks in your notebook, get up for your break, let your brain assign priorities in the background while you're away, and finally return back to your desk with a clear sense of what you'll work on next.

**Don't mix chore work with focus work.**
In my task notebook, I maintain two columns.
The "chores" column contains small, fast-paced tasks that don't require extended focus, such as responding to an inquiry, writing an email, doing a minor code review, checking automated reports, responding to incident alerts, and making small low-risk code changes.
The "focus" column contains work that requires a slower and deeper frame of mind, such as coding complex tasks, writing design documents, or doing deep dives into unfamiliar code.
By my experience, if I start off with tasks from the chore column, I will enter a fast and shallow state of mind that will make it harder to switch later to focus work.
It is easy to move from a deep mind to a shallow mind, but hard to do the opposite without taking an extended break.
Once chore work takes over, your brain will be in chore mode for the rest of your work session.
Chore work cannot peacefully coexist with focus work; if you value your focus time, make focus work the first thing you do and save the chores for later.

**Grayscale.**
Computer apps make liberal use of unnaturally bright colors (especially red) to get your lizard brain's threat center all fired up.
One way to reduce presentations to their raw data is by setting your screen to grayscale, turning everything black and white.
I've regularly used grayscale on my phone for over a year with positive results.
Try browsing a distracting app like Facebook on a grayscale phone; it's so drab and boring you'll wonder how that app was ever able to pull you in.
I wasn't able to successfully replicate this experiment on my computer desktop, mainly because of the heavy reliance many apps have on colors.
Even when it's only my phone, it still drastically reduced my time-wasting and that counts as a success for me.

**Don't fill your idle time.**
Checking email or chat is often an unconscious compulsive habit rather than an intentional choice.
For me, I find myself frequently doing it right after kicking off a build or a test run.
If the prospect of being idle for even a minute sounds crazy to you, it's a sign that you are frazzled and need to give your brain a break.
Trying to fill every minute of the day with something productive leads to exhausting context switching and multitasking.
If the gap is small, don't bother trying to fill it.

## How to avoid being a burden on your coworkers' minds ##

Just like you, your coworkers have a tendency to overseek information and to let information overload distract them from doing focus work.
With this in mind, here are some ways be thoughtful and avoid frazzling your coworkers.

**Shrink your email recipient lists.**
As a general rule, people overestimate the importance of their tasks, overestimate the size of the group that must be kept in the loop for a given issue, and overestimate the issues for which they should personally be in the loop.
It is easy to add someone to a thread when needed but it is hard for uninvolved people to detach themselves when everyone keeps mashing the Reply-All button.
If you're unsure whether you need to follow a given conversation or unsure whether to include a particular person in the CC line, err on the side of not doing it.

**Keep tense discussions in person.**
Negative emails frazzle people in ways that negative face-to-face correspondence would not.
Without any body language cues, even a well-meaning message can come across as terse, contemptuous, or sarcastic, especially to a frazzled reader.
Threatening-looking emails send their readers down unproductive rabbit holes where they over-analyze how they had apparently made you angry and over-prepare their responses.
To minimize frazzling people, handle difficult conversations in person rather than in writing.
This way, you can let your good intentions make themselves self-evident in your speech and body language.

**Keep emails succinct.**
People are not in focus mode while they are reading emails; more likely than not, they are frazzled or simply bored.
To make sure your message is read, keep it short, use simple formats like bulletted lists, avoid walls of text, and bolden or highlight any passages that are especially important.

**Designate a sacrificial lamb.**
Because of the difficulty of interleaving chores with focus work, if you get a lot of chore work, you might as well go all-in on chore work and give up on focus work.
Instead of having many team members each partially burdened with chore work, you can have a more productive team by isolating the chore work among a smaller subset of people.
On my team, we have a weekly "distraction" rotation distinct from our wider org's daily livesite on-call rotation.
Each week, we have one person handle all our livesite investigations, release management, correspondence with outside teams, and other distracting unpredictable tasks.
This arrangement frees up the rest of the team to do focus work in peace.
In return, we accept that our designated sacrificial lamb will probably not get any focus work done during their rotation.

## Conclusion ##

As interns and college hires, we typically came to the workforce with solid technical chops but with little wisdom on how to handle office life.
Much of our early growth came not from learning more technical skills, but from learning how to apply existing skills and learning how to be productive.
We usually didn't fear information overload at first, though inevitably we would end up experiencing it directly.
For our happiness and for the happiness of our employers, we must accept that the brain is a fragile thing that requires gentle treatment.
