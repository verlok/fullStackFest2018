---
layout: post
title: State of the Art Web User Interfaces with State Machines - David Khourshid - Full-stack Fest 2018
date: 2018-09-06 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> This talk is intended for all developers, beginner to advanced, and provides gentle explanations to two otherwise confusing (but essential) computer science topics: finite state machines and statecharts. It will focus on using FSMs within any framework (or no framework at all), with an emphasis on statecharts - an extension of FSMs that simplifies even the most complex user interfaces, and is used to this day from traffic lights to avionics systems and NASA shuttle missions.

Keyframers, they create anymations with HTML CSS and JS

Developer user interfaces is hard. (shows funny animations)

The most neglected variable is time. Callbacks, promises, async await, observables. (funny slides with emojis :))

If you fetch data from a button, it can give you the response after a long time. So the user clicks again. So I smart developer I desable the button. So the experienced user uses devtools and enable the button again :)

So we start a request and set the loading animation. But if we want to cancel the request or something goes wrong... you have a lot of cases to manage for a single button.

Bottom up code is difficult to test, difficult to understand, will contain bugs (unavoidable fact), difficult to enhance, features make it worse (increasing the complexity).

**Intuition. UI components are NOT independent.**

(see animation in slides, very beautiful UI)

So how can we better model the behaviour of complex UIs?

## Finite state machines

First you have an initial state, then you have a finite number of states, and a finit number of events which trigger states. And a mapping of states transitions, and a finite number of final states.

Flowcharts like this are easy to understand from a developer and from a UI designer.

(shows states mapping in a JSON objet)

Example on Codepen. I can search for something, cancel the request, click on an image. It shows the current state on a layer.

Another example with animations, no matter how many times I click the submit button, it doesn't break the UI.

## Using state machines for integration testing

Depth first search algorithm for finding all simple paths
- Represents all possible user flows
Etc.

## Using state machines for analytics

In the transition we can push the current state, next state and message using telemetry.

It can make clear that there might be a better path (pass from state A to state C)

## Software bugs are made visually clear

No need to restart the machine :)

## Does this scale?

No. But is still a good idea. :)

Statecharts introduced a notion of 

- actions --> on entry, on exit, transition
- guards --> conditional transitions
- hierarchy --> nested states!!
- orthogonality --> parallel states
- history --> remembered states

Case: bold, italics underline. The combination of this 3 makes 8 possible states. But we can simplify drawing only the transition between bold on/off, italic on/off, etc. and it's much simple to read.

## State charts with xState

There's a `transition` function which is like your reducer function in Redux. This naturally gives you the actions.

## Advantaces of using statecharts

- visualized modeling
- precise diagrams
- automatic code generation
- accomodation of late-breaking requirement changes

## Disadvantages

- Learning curve
- Modeling requires planning ahead (boxes and arrows before start coding, I know you want to jump right to your coding)

## Complexity trade-offs

Complexity in the design fase, but not in the maintenance.

I have a [statechart visualization tool](https://bit.ly/xstate-viz).
(he shows a demo)

It was used by workshop.me tech training.

## xstate v4

He's releasing new version, featuring:

- External state (like redux)
- Delayed transitions and events
- Interpreter --> integrate with react or redux
- SCXML conversion, which is a standard you can use in C#, Java, Python and more
- Final states
- New visualization

```
npm install xstate@next
```

(Resources slide)

## Demo - TicTacToeMahine.js

It has an initial state, a list of events that can chenge the state, a condition which has to be valid, etc. 

He shows the demo and the tests. Filters the number of moves to \<=5, searches winningPaths. It generates tests and show them in the browser


> Your code can do more.


---

My questions

Q: 

> @davidkpiano