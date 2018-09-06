---
layout: post
title: The Future of Front-End Performance - Sia Karamalegos - Full-stack Fest 2018
date: 2018-09-06 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> Help! My app bundle is 5MB! My users are angry that my app is so slow! It’s easy to forget that performance matters when we are under pressure to deliver features quickly.
> We'll talk about bleeding-edge topics in front-end performance such as dual-bundles for modern browser transpiling.
> Come learn how to deliver better user experience with high-performing front-end apps using Webpack. This talk is library-agnostic (React, Angular, Vue, etc.)

Mirrors in elevators are to make people feel less close and to distract people with their image :)

Performance facts. Better performance means increas in conversion and orders.

Speed is now used as a ranking factor.

## Measurements and analisys

Pareto Princile.
80% of the effects come from 20% of the causes.
You should analyze and optimize your worst offenders.

Metrics that matter
- Speed index
- Time to interactive
- Jank responsiveness

Speed index is expressed in ms and it depends from the size of the viewport. Webpagetest.org to measure it.

Time to interactive. When the user sees things but clicks and nothing happens, it's not interactive :D

Jank or responsiveness: 50FPS vs 25 vs 12. 

In the network tab on devtools you can measure partial time of your app life. Synthetic testing on the Performance Tab to optimize responsiveness. 

Synthetic testing is how you can find your worst offenders.

## Real user monitoring

- Navigation Timing API
- Resource Timing API
- User Timing API for custom timings \*

\* You can put a manual flag of when a heading has rendered, or your framework was initialized, etc.

## Optimize for the device and network your users have.

We usually have much faster devices and connections. So simulate slower CPU and network. Webpagetest does it, configure it using your GA data. Not only in rular but only on shared wi-fi networks.

*Set performance budgets using webpack* --> _to investigate_

## Image optimization toolbox

* Use the right image type (png, jpg, gif, video)
* Use the right size in src and srcsets. Webpack loaders can autobuild srcsets --> _to investigate_
* Compress images using imageOptim or others. Webpack can do this too.

Javascript bytes !== JPEG bytes. They don't have to be parsed nor compiled, and they are downloaded asynchronously.

## Ship less code

* Less code = less load + less parse/compile
* Holy grail = prioritize only what's needed in view

## Client vs server vs progressive

First above the fold, then lazy load all the rest.

(she shows the time when html arrives, JS arrives, js parsed and eval'ed, view is painted)

Long story short: progressive rendering is better.

## Optimize Time to Interactive

- Analyze your loads and bundles
- Ship what's immediately needed
- Migrate to HTTP2
- Minify o speed up both download and parse/compile
- Compress with gzip or brotli
- Remove unused code - automatically with tree shaking, but still... 

Keep in mind that if you `import _ from 'lodash'` and you use only one function `_.isEmpty({})` it doesn't tree shake all the rest.

There are other micro libraries that you can use instead of lodash so that you get smaller bundles.

## Cost of unnecessary transpiling

You can save bytes by serving ES6 to browsers which support it.

If you use `<script type="module">` modern browser will use it, so no need to transpile it. You can serve JS to legacy browsers with `nomodule`.

## Optimizing responsiveness

- don't block the main thread!
- avoid mem leaks - garbage collector pause executrion
- avoid long running js - chink it with `requestAnimationFrame` or `requestIdleCallback`
- use up-to-date frameworks that prioritize user input (ike react fiber starging in React v.16)

## Perceived performance: Houston's baggage claim complaints

They made people walk around instead of waiting in the line. :)

The psychology of the wait is more important that the wait itself.

(Related topics: Optimistic UI, UI Skeleton)

Focus on what users are trying to get done and optimize for that.

---

Questions

Q: When should we stop bundling? 
A: Don't stop, it's also useful for organizing our code in different files, you should only bundle better for performance.

My questions

Q: How can we set performance budget using webpack?

> bit.ly/siaspeaks