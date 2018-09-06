---
layout: post
title: Building a Modern Memex - Andrew Louis - Full-stack Fest 2018
date: 2018-09-06 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> The Memex was proposed in 1945 as the ultimate organizational tool. The desk-sized device would store a user’s personal library and allow for information to be searched, organized, connected together with hyperlinks, and shared.
> Without a device like this, its creator suggested, our species would drown in information overload and come to a premature end.
> Tragically, zero of these devices were ever produced, but 72 years later, Andrew has built a Memex in JavaScript. He's built importers for dozens of different sources of personal data and data consumptions and put it all behind a graph-based API.
> He’ll be going over the history of the Memex and demoing his own version by showing what type of queries, organizing tools, and visualization are available.

History in tech (funny slides about var, let and jQuery).

1930s: Vannevar Bush was an engineer whomade analogue computers to solve calculus. He became a manager then.
During the war he was responsible for the tech research. WW2 was explosion in information. Whole rooms of paper and information was generted.

> We are being buried under our own product.

"As we may think" book. He called the MemE. A device to extend your memory. It had a camera, a voice recorder, microfilms for memory, etc.

> The human brain makes association. Memex will do this mechanically.

Different documents would be connected by trails. 

The number of memexes produced was: `0`.

Good idea, though. 

I'm an information pack rat. I keep journals, kindergarden reports, cinema tickets, chats, paper maps and trails.

The solution: Talk to a therapist. No. Build a Memex. :D

Gathering data: 
- reading and browsing from browser history, ebook reader, twitter, RSS
- Digital consuptions like photos viewed, videos watched, bmusic post
- Location history from phone
- Messaging and social interactions
- Journaling, personal photos, notes

Data details
- Data from 1995 ttoday
- 6M activities
- 5M 
- 17M relationship

Live demo time!
Finger crossed!

--> Provider: twitter, verb: liked -- can change to gitub

At the side there's a graph, linking to other things he liked.

--> Verb: listened, represents: song, reators: aretha frankin

Shows the results, and the graph

--> involved: (javascript) before: 2002-06-03

Remove node modules :)

-->  provider: bash, verb commanded, involved gifsicle

--> verb. read

Shows whatever was read

It also can highlight the quotes that he saved


--> verb: browsed involved(wikipedia) occured_during: verb: read

Shows what he searched for

--> Verb travelled, instrument walking, duration >10, near: bondi beach

Shows the map from mapbox, too

--> Verb: travelled; instrument: automobile; duration 10; occured_with: (Max)
--> Added verb: listened, represent: episode, etc.
--> Or added verb: photographed, involved(fuel)

It works, cool :D


--> Verb: ate; unit: burrit; near: toronto

Shows a log of burrito he ate.
Also scrolling back in time, it can show a heat map instead of single points

**AWESOME DEMO!!! Big claps.**

---

The nitty gritty

Fancy graph database

- postgres
- that's it
- one nodes table, one relationships table
- database handles graph traversals

Querying: (see slides)

API
- a single endpoont for qeruing
- a single endpoint for importing data (write only with deduping system)

Desktop app:

- interface
- importers
--> API --> Postgres

API was made in Rails

Interface with EmberJS. 
Electron for importer


## Why ember?

Lots of stability, easy to work on it, nothing is going to break completely. 
The community evolves but for me is good so I can focus on app development and not rewriting everything.

## Where's this project going?

> You are just a number

I can create a number of charts combining any strange data, like heart rate on bicicle and perceived temperature.

> "My memex as a weird art project"

It did an experiment training chatbots.

> "My memex as long-running experiment"

A whole bunch of behaviour could emerge.

And open source soon!

https://hyfen.net/memex --> sign in for newsletter 

## Back to the story of the first memex

It was weird project.

- For its form factor (computers were big)
- For the problem it solved (it solved a problem for individuals,)
- Technologies it used (microfilms, he was stuck with tech he could make work)
- For how it was published. It was in the Atlantic magazine, surrounded by a poem and the mail, a deodorant commercial, etc.
- Because he was one of his side projects, an "image of potentiality"

Every people liked it for different reasons.

Doug engerlbert created modern computing, .... (lost him here) -- The modern web and computing are a descendant of Bush's Memex

Side projects: make them weird, make them experimental! You have a lot of power.

Using my onw weird side project.

- places ive visited in berlin
- things i've liked on instagram
- times I mentioned this or that guy

That's it! End. **Big claps!**

---

My questions

Q: 

> @hyfen