---
layout: single
title: "The Most Useful Courses I Took at Waterloo"
date: 2018-12-16 10:00:00 -0700
categories: education
---

It has been over a year and a half since I wrote the last final exam of my software engineering degree at the University of Waterloo.
Now that I am in the workforce, I am in a position to look back on my course history and evaluate it with the benefit of hindsight.

Looking back, the most useful courses were the ones that taught a timeless and technology-independent concept.
The courses on this list are the ones that imprinted an idea into my mind and changed the way I thought about engineering.

### 1. Operating Systems - SE 350 ###
_Programming is bookkeeping._

An operating system's main duties involve keeping track of system memory and scheduling processes to run on its cores.
Operating systems are low on the system stack, lower than most application developers ever go.
Despite the different levels of abstraction that OSs and applications deal with, the similarities in programming stand out more than the differences.
The particulars may vary, but virtually all programs need to maintain an internal data state and they need to use this data state to make decisions when prompted.
The basic client-server model exists everywhere; the only difference between stack layers is the abstractness of the problems that the programs deal with.

### 2. User Interfaces - CS 349 ###
_Be intuitive, not impressive._

The ultimate promise of software is to reduce cognitive load for human end-users.
When programmers make overwhelming or unintuitve user interfaces that frustrate their users, this promise is broken.
Saying _"If the users find the interface confusing, it's because they're dumb"_ is a lazy rebuttal.
Novice and expert computer users will broadly agree on what interfaces are good and what interfaces are bad.
Interfaces may look like a fuzzy art, but they can be judged by objective criteria just like almost everything else in software.
The goal is always the same: aim to minimize cognitive load.
The cognitive load principle applies not only to writing UIs for end-users to use, but also when writing code for other programmers to read.

### 3. Algorithms - CS 341 ###
_Complexity rules the day._

The optimal algorithm for a problem is an intrinsic property of the problem itself.
It can be proven that some problems don't have algorithms faster than a certain time complexity.
It can even be proven in some cases that a problem is not solvable at all, the Halting Problem being the textbook example.
If solutions are properties of problems, then finding good algorithmic solutions is a matter of discovery rather than a matter of engineering.
Past a certain point, a problem's complexity cannot be bypassed and there are no further shortcuts.

### 4. Data Structures - CS 240 ###
_The only thing more expensive than order is disorder._

Some data arrangements are objectively superior to others.
If your list is a jumbled random mess then you will have linear-time searching, but if you put in the effort to keep your list sorted then you will improve to logarithmic-time searching.
Structure and order require overhead to set up and effort to maintain, but depending on the use case, such work often pays off.

### 5. Computer Networks - ECE 358 ###
_Protocols make the world go round._

Massive distributed projects like the internet are possibly only because computers around the world all speak the same language.
Without protocols, all messages are just incomprehensible streams of bits with no decoding instructions.
Protocols like IP, TCP, and HTTP use a consistent structure with consistently-placed metadata, allowing recipients to decipher them.
Each of the common protocols above also has solutions to inevitable problems such as missing, corrupt, or out-of-order messages.
Programmers frequently add new protocols above HTTP, REST APIs being perhaps the most typical example.
The standard lower-level protocols demonstrate the robust elegance that all programmers should aspire to.

### 6. Cooperative and Adaptive Algorithms - ECE 457A ###
_Intractably-large problems are still solvable._

Many mathematical problems have overwhelmingly-large search spaces that computers will never be powerful enough to explore in full, the traveling salesman problem being the textbook example.
Just because some problems are mathematically intractable doesn't mean that all hope is lost.
For example, human brains are incapable of evaluating millions of chess positions per second, yet this doesn't prevent good human chess players from existing anyway.
Human brains deal with decision overload by first drastically cutting down the number of choices using simple heuristics.
They then explore promising options in detail while dismissing bad ideas quickly, always staying responsive to feedback along the way.
Computer algorithms can be made to run in a similar adaptive fashion., strategically avoiding the unproductive parts of the search tree.
A non-brute-force AI won't give you perfect and optimal answers every time, but "good enough" is often all you need.

### 7. Concurrency - CS 343 ###
_Avoiding conflicts is easier than solving them._

Race conditions are the worst kind of software bug.
They manifest themselves unpredictably and can corrupt your program's state in bizarre ways.
The end consequences of a concurrency bug can happen far away from the true root cause, making the buggy code section hard to pin down.
Worse yet, concurrency bugs often appear non-deterministically, making them hard to reproduce and making it hard to conclusively prove that your code is bug-free.
Anyone who falls into concurrency hell because of a missing safeguard will vow never to let it happen again.
The only way to win against chaos is with due diligence and a defensive mindset.
Preventing corruption is much easier than trying to fix corruption once it happens.

### 8. Distributed Systems - ECE 454 ###
_Work as a team, but don't trust your teammates._

Distributed systems open a world of promise, with new possibilities for parallel processing and reliability-through-redundancy.
Distributed systems also open a world of new problems, including communication, coordination, consistency, and an increase in the number of possible points of failure.
Distribution is a double-edged sword.
The benefits cannot exist without the drawbacks.

### 9. Foundations of Sequential Programs - CS 241 ###
_Information can be preserved even after a radical transformation._

When high-level language code is compiled, it undergoes many levels of transformation.
By the time a program is executed, it is in the form of a long sequence of extremely basic commands that do nothing except write numbers into registers, read numbers from registers, perform basic arithmetic on numbers inside registers, and jump the program's control point to other places on the command list.
A compiler's input and output are so different that they appear to have nothing in common, yet they ultimately represent the same program.
Against all intuition, there is some equivalent information stored inside both formats that wasn't lost in translation.
Computers are capable of doing all their work in binary because all information can survive being reduced to such a simple format.

### 10. Applied Cryptography - CO 487 ###
_Secrecy, authenticity, and data integrity are similar problems._

Certificates aren't merely those pesky things that cause outages in your service when they auto-expire.
They have a critical security purpose and there is a lot of fascinating math underlying them.
Cryptography is built upon mathematical operations that are easy to perform but prohibitively expensive to reverse or to forge.
The math is interesting in its own right, but it also comes with a surprisingly diverse set of practical applications, not all of them in security.
