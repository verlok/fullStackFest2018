---
layout: post
title: Native JavaScript modules- import {Browsers, NodeJs}; export {production}; - Serg Hospodarets - Full-stack Fest 2018
date: 2018-09-06 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> All the modern browsers support native JavaScript modules, and it’s a perfect time to start using them, which will change the way we are bundling the JavaScript, and how the code is executed. We will understand the native modules features, performance details and lazy loading JS modules techniques.

Modularity is for code readability.

The old way to avoid globals were:

- using IIFE. Still not reusable.
- define using require.js. Still confusing.
- common JS. Still not async, not standard, not supported in browsers

Finally ES Modules, or JS modules, or ES6 modules, ESM.

- Module scopes
- Modules reuse
- Multiple named exports
- Deferred, but executed in order
- Both static and dynamic
- ES2015 standard
- Tooling Webpack, babel, rollup

Support in browsers?

- In 2015 they supported everything but not ESM.
- In 2017-2018 came to Firefox and Edge. Now supported in all the browsers. (but he hid Internet Explorer...)

[Table of modules systems comparison]
[Native ESM advantages]

As a result in dev cycle, saves time, benefits in debugging and build configs/browsers tools (webpack configuration not required).

## Scrypt type module

Use `type=module` to load them. 

- They are loaded and executed once (they're singletons) even if used more than once, and imported via different paths or methods.
- They are hoisted, they are executed before anything else.
- They allows CORS by default.
- They must have a valid JS MIME type. There's an easy fix on your app server to do this.
- They are not render blocking
- They are `use strict` by default (fix obvious problems like prevent uncontrolled globals, duplicate params, `this` out of scope, etc.)

## Module loading process

1. Construction - Find download, parseall the files into module records
2. Instantiation - Find boxes
3. Evaluation - ...

In the evaluation phase, circular dependencies are solved if modules are circular but not the code itself (see slides for example).

## ES Module path

- Must be a full url
- must start with `./`, `../`, `/`

## Dynamic import()

- The URL can be composed
- You can `await` for `import`

## Demo

Lazy load of bootstrap script on user actions.
(It's a video, see slides)

## Node

- On node js they are available under a flag from v. 8.5
- There's a complete polyfill, not fully compliant
- Requires .mjs extension for separation --> Its the flag to say "it's a es6 module"

## NPM package field

- `main` dist/bundled, 
- `browser` dist bundled-browser, 
- `module` index.js file

## import.meta

(didn't understand this)

## Other types

It's possible to use it for service workers with `new Worker("worker.js", {type: "module"});`

## Performance

- H2 is required because it parallelize resource requests, you now load thousands of files in parallel
- Chrome team are working in making it faster

## Demo

Loading lodash-es requires 640 files and executes in 300ms, Safari performs better at the moment.

## Link rel modulepreload

Performance trick

```html
<link rel="modulepreload" href="dependency.js">
<link rel="modulepreload" href="sub-dependency.js">
<script type="module" src="app.js">
```

Browser loads the dependencies, but it doesn't execute them until needed. 

## Nomodule for migration

```html
<script type="module" src=""></script> <!-- Skipped by old browser -->
<script nomodule src=""></script> <!-- Skipped by modern browser -->
```

## Proven usage

- lodash-es on node
- hospodarets.com on browsers

## Conclusion

- great support
- include them with `type=module`
- `nomodule` for migration
- h2 and `link modulepreload` for performance
- simplified configuration for debugging and publishing
- not fully ready for enterprice projects, perfect for mid-size apps

---

My questions

Q: What about internet explorer?

> @malyw