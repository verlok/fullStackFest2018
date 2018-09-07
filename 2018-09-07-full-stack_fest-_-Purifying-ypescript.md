---
layout: post
title: Purifying Typescript - Timothy Clifford - Full-stack Fest 2018
date: 2018-09-07 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> You’ve seen the articles littered all over the internet, urging you to let go of your impure, object oriented ways and join the functional programming revolution. At the same time, there are a growing number of options for writing type-safe JavaScript. In this talk, Tim will cover one of these options – TypeScript – and explore how to leverage functional programming techniques to write safer, more concise and understandable code.

We do a lot of functional programming but never tried to functional programming. How to apply them?

Agenda: 

- functional programming overview
- typescript
- functional with TS
- summary
- where to next


All the patterns used in OO are functions!

# 1. Functinal Programming:

- building software by composing pure functions, avoiding shared state, mutable data and side effects
- enable or enforce the principlesof functional programming. 
- the stricter the language, the more functional.

## Origins

Calculus. Lambdas. John McCarthy. List programming language. Closure language is inspired to it.

## Reasons

Total made up numbers :)

## Concepts

- First class function
- Pure functions, all the side effects are inside the functions, not touching the outside world
- ?
- Recursion
- Currying
- Pattern matching

## Benefits

- Plain code, easy to be controlled
- Ideal for working with complex systems
- Easier to test

# 2. Type script

- Compile time error checking
- Safer refactoring
- Doc through types
- Types are optionals - type inference FTW
- JS superset

It has benefits, but removes some of the JS flexibility.

# 3. Functional TS

Demos in Code

- Types (errors when writing code)
- Recursion vs nesting (calls `filter` and `map`)
- Immutability - read only customer, we can't change its values or add elements to its arrays
- Function composition (not readable code vs R.pipe(addSalary, subtractFees, subtractBills)) -- (R is rambda)
- Currying - `R.curry(updateBankBalance)`
- Pattern Matching - uses `tsmonad`, monad is wrapping uncertain values in containers and can specify something that may or may not be there. It's similar to promises. -- `maybe(balance).caseOf({just, nothing})

There's TL lint, you could use it for ensuring things like: the vars are read only, that you're using `const` instead of `var`, etc.

# 4. Summary

## Terminology

"Monads, monoids, functors, category theory?" They might be scaring, but you just start trying. It will make sense sooner or later.

## Types

Safety is nice, but it's not free.

## Pure functions

Easy to write, hard to combine. The more difficult part is composing them, and this changes the mindset from imperative to a more decorative way.


## Side effects

Staying pure is difficult in a mutating word.

Isolate side effects putting your core business logic inside functional, impure in outer layer.

## Higher kinded types

Where is my generic generic? 

## Functional evolution

You'll get better with the time.

# Reference

- Functional programming libraries:
- Immutable
- Algebraic
- Functional programming
- Futures

Functinal -> JS

- Elm
- Purescript
- Reason
- Idris
- ScalaJS
- Clojurescript
- Fable
- GHCJS

Slides 
https://goo.gl/hv54JG

---

> @timothyclifford