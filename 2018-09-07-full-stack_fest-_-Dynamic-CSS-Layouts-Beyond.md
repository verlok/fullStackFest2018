---
layout: post
title: Dynamic CSS, Layouts & Beyond - Miriam Suzanne - Full-stack Fest 2018
date: 2018-09-07 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> Miriam is an author, performer, musician, designer, and web developer — with 15 years experience as a project manager, user-experience designer, and front-end architect. She is a co-founder of OddBird, creator of Susy and other popular open source tools, author of SitePoint’s Jump Start Sass, and staff-writer for CSS Tricks.

# History

1993: HTML
1997: `<font>` and `<table>`
2000: CSS (principle of Least Power, we should use programming languages as weak as possible to solve our problems)

("CSS IS AWESOME" overflowing is a feature)

2000: a Dao of Web Design - John Allsopp - the control of the layout is a limitation of the printed page, the web is flexible

2007-2010: Major Grid - Framewoks. Blueprint, OOCSS, 960 grid system

With framewoks we could go all the repeated hacks go away. 
Natalie's Downe talk in London's barcamp 5 (they're on slideshare)

Responsive before responsive, but with Ugly Math, like `width: 23.72343%` to build a grid system.

2009: Compass and Sass, a lot of math inside the code
So Susy Grid System created to make code readable again. (don't use it!) To name things. Code is communication. :)

2011: calc() from Firefox 4. I can do `calc(100% - 200px)`.

2011: Responsive Web Design (Ethan Marcott)

Don't be fooled, Declarative Syntax doesn't mean Static Results. All the issues we need to handler are Dynamic.

Flow: inline (with float)

Responsive design was about Fluid grids, flexible images, etc.

2012: Flexbox, still works in a single direction (main-axis) and then wraps if we want to.

2014: CSS variables (firefox 31+) - Shows some variable examples, AKA "custom properties"
> they are like vendor prefix without the vendor name :)

Similar to SASS, we're still naming things, storing data somewere. But there's a big diff: SASS variables scope, so they follow the cascade and the file name. CSS props doesn't scope, and you can change them in a media Query (_or in JS_), etc. 

They inherit everywere, if you don't want to you can do `:root{--myVar: initial}` (<-- wrong, see slides)

Safe inine styles: `<button style="var(--color: green)">` --- wut?

For lower specificity --- wut?

Defaults & missing Longhand - to change a single value e.g. in shadows

Combine with `calc()` to do more

She re-created Susy with CSS vars and she demoed it and showed the code. Still you still don't want to use this :)
The problem with Susy is that it tries to solve every layout's problem, you have your onw.

Use Radial Values to Theme (like the HUE value)

Use Clamped --- wut? -- it's a way to change the text's color depending on the background color

Issues with CSS vars. They can't be used inside url(), it would've been useful.

## 2017: Jet Packs (?) and CSS Grid.

Firefox 52+
Nothing like it - At All.

The spec is complex, getting started is not.

Fe define it on container ,we can define grid template and gutters. 
Optional Element Control. `Auto` returns to the flow.

- % => relative to parent width
- vw => viewport
- fr => to the remaining space (once that everything has been calculated, the space that remains)

We can also define layouts with "ASCII art" :) then use it named.

Fluid and fixed values working together. Fixed, Fraction, minmax, etc.

The layouts are really 2 dimensional. 

(she went crazy with demos here :D very good job)

https://gridbyexample.com by Rachel Andrew --> examples, templates, etc.











---

My questions

Q: 

> @mirisuzanne