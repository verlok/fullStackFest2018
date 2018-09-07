---
layout: post
title: A Real World PWA - Zack Argyle - Full-stack Fest 2018
date: 2018-09-07 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> There is a lot of hype around PWAs, especially from Google is who is leading its evolution. But all of the demos are small self-contained examples that don’t include the intricacies of large, real-world applications.
> Where does server rendering fit in with the app shell model? What are the pitfalls of service worker caching?
> As the tech-lead for Pinterest’s mobile web rewrite, Zack learned first-hand the pros and cons of current progressive web app strategies. These are lessons that all web engineers should be aware as the world embraces the progressive web.

The story, the 3 Rs, the metrics

## The story

Dark lights, speaks spanish, talks about the interstitial page asking to download the app. I'm not alone (shows tweets about pinterest UX, like "you suck")

Why are we doing this that everyone hates?

> Metrics do not measure entiment

AB tests the change of a button can be tested. But a layer that sends you to the app store? Some could click it, but some else next time wouldn't go to the pinterest page.

## 3 Rs

Not anymore "A site that utilizes 'progressive enhancements', meaning that modern browsers will et a bettere experience than older browser."

Now: "a site that uses ..." (see slides)

Why cant ce call it a "modern web app"? Or other funny ways... (see slides)

- Reduce
- Reuse
- Review

Reduce: make everything smaller. Don't send too much JS. Shoot for <200 kb of JS for initial page load. Twitter is now sending 5 megs (?).

**Check webpack common chungs using "webpack bundle anayzer"**

They used the analisys and tried to move javascript around and they arrived to less then 200 kb. 109 in the entry, 71 vendor, 8 route, 2 async.

## Your HTML is too big

> We need to talk about Redux and SSR. Just was second large site sending more than 100k zipped HTML payload. (alex russell)

They also send few HTML and 5k of inline CSS. They re-hidrate the information on the client. **Avoid to send down JSON data in the HTML.**

App Shell | SSR

(The shell is the skeleton.)

SSR can show content faster, but takes a lot to become interactive.

App Shell + hydration make interactive fast, but you need to wait for the API to go back, so it's a delay for the meaningful paint.

But in PWA you can cache routes (server side is not cache-able -- _not really, you can cache HTML response_) 

For SEO? 
We use AMP instead of SSR. Any traffic coming from search engines, we give them an AMP page. (_does Google accept this trick?_)

## Service Workers

- are network proxies, so everything it would go through the network goes to the service worker first.
- are awesome because they're supported by major browsers (on Safari they still suck, they have problems)
- you can use them to preemptively download routes that are likely to be used

## Review

Avoid ambush by JS (very funny cat gif, lol)

> Whatever tools you choose, a budget is essential. Without one, even the most advanced, "lightweight"...

If you have the data about the performance, you can analyze and fix problems.

## The metrics

TTFP 4.2 -> 1.8 s
TTI 23s -> 5.6s
JS bundle 620kb -> 150kb
CSS bundle 150kb -> 6kb

Custom metrics like pins seen, pins saved, etc. +100% to +400% to +800% signups

Great talk! Funny and serious at the same time.


---

My questions

Q: SW on Safari?
A: It was a big achievement but they don't have a whole reason in investing in mobile web, since their money come from apps. 
QQ: But what are the bugs?


> @zachargyle