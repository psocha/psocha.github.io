---
layout: single
title: Projects
permalink: /projects/
author_profile: true
---

## Go Game Clock ##
_Stack: Android, Java_

![Go Game Clock](/assets/images/gogameclock.png){:class="img-responsive"}

A niche clock app for keeping track of time controls in the board game Go.

The app supports complicated "byoyomi" time controls that are common in Go but which other clock apps (typically tailored to chess) do not support.

Currently with over 3300 total installations and a 4.5-star rating on Google Play.

[![Go Game Clock on Google Play](/assets/images/google-play-icon.png)](https://play.google.com/store/apps/details?id=com.psocha.goclock)

## Homework Tracker ##
_Stack: JavaScript, HTML, CSS_

![Homework Tracker](/assets/images/homeworktracker.png){:class="img-responsive"}

A Google Chrome extension for tracking homework items and due dates.

The extension is written in vanilla JavaScript with no jQuery or other big libraries.
This lean design allows it to be faster, more responsive, and less memory-intensive than similar list-management apps on the Chrome Web Store.

Currently with about 15000 weekly users.

[![Homework Tracker on Chrome Web Store](/assets/images/chrome-web-store.png)](https://chrome.google.com/webstore/detail/homework-tracker/nblmegnbohbagljeheaniomchelnhhka)

## Chess Engine ##
_Stack: C++_

![Chess Engine](/assets/images/chessengine.png){:class="img-responsive"}

A computer engine for the game of chess. 
This engine does not have a graphical interface, but instead uses the text-based UCI protocol, allowing it to be installed and run on almost any chess GUI program.

The engine's AI uses a min-max tree search with alpha-beta pruning.
To evaluate positions, it applies basic strategies like material-counting and piece-square tables.

The engine currently plays at the level of a human beginner, though it is able to beat standard open-source engines like Stockfish on the lowest difficulty settings. More improvements are in the works.

Source code is available at my [GitHub](https://github.com/psocha/ChessEngine).

## External Projects with Major Contributions ##

### [Manifold](https://manifold-lang.github.io) ###
_Stack: Java_

Manifold is an open-source hardware description language developed at the University of Waterloo. 
It is designed to be high-level, easy-to-use, domain-agnostic, and similar to modern functional programming languages.

As part of my fourth-year design project at the University of Waterloo, I worked with some fellow undergraduate and graduate students to extend Manifold.
We focused on giving Manifold the ability to describe and analyze microfluidic circuits, a young domain poorly supported by existing software tools.
We ended up making a prototype that can handle very simple circuits.

We also wrote a [research paper](/assets/documents/manifold-paper.pdf) on our work which was accepted for the 2017 IEEE Canadian Conference on Electrical and Computer Engineering.
We presented our paper at CCECE 2017 in Windsor, ON in May 2017.

## External Projects with Minor Contributions ##

[Global Visionaries](http://globalvisionaries.org/): a Wordpress site made in a group as part of the 2016 [Seattle GiveCamp](http://www.seattlegivecamp.org/) charitable hackathon.

[Unloop](https://www.un-loop.org/): Improvements to online course materials for a node.js web development curriculum, done as part of a 2018 Microsoft Hack for Good hackathon.
