---
layout: post
title: To push or not to push - Patrick Hamann - Full-stack Fest 2018
date: 2018-09-06 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> HTTP/2 server push gives us the ability to proactively send assets to a browser without waiting for them to be requested. Sounds great, right?! However, is this new mechanism really the silver bullet we thought it was? Using new research and real-world examples this talk will take a deep dive into server push and attempt to answer the question we're all asking: is it ready for production?.

About performance optimization. There are lots of resources that Browsers can't see upfront. Browsers are usually busy parsing and executing Javascript, there is time there we can use.

## Loading

What are the critical resources that your website need? Font? Logo? 
You need to ask yourself what is **essential** to display the **content** of the website.

- critical CSS
- fonts
- hero images
- initial route
- app bootstrap data

You need to optimize those resources and prioritize those requests.

A good loading strategy

- prioritizes above the fold
- prioritizes interactivity
- is easy to use
- is measurable

## Preload

What if we could tell browsers what to preload.
"you're gonna need those resources, please fetch them already".

The request for webfonts is made late in the pipeline of downloading and parsing HTML, JS, etc. (see flowchart in the slides)

(the CSSOM can be creates only when all the CSS files are downloaded, there could be a file later which says "display: none")

What are my hidden sub resoruses

- fonts
- application data
- etc.

Preload provides a **declarative** fetch primitive that initiates an **early fetch**.

You can decorate your HTTP responses with preload links.

That moves the font file requests earlier in the network waterfall. So users can read things earlier.

This improved by 50% (1.2 seconds) the text rendering in Shopify. Is that easy.

## Server push

To specify a `<link rel="preload">` in the html is too late. There's server think time, OK, but then there's the response download time and HTML parse time.

There is a PUSH_PROMISE telling the browser "hey, I'm going to send this resource to you so you don't need to request it".

## How can we push

```http
Link: rel=preload
```

(see slides)

There's a nopush attribute to say to the browser (don't push it, just preload it later)

What about server think time?
Link header indication is too late, anyway.

## Async push

A CDN surrogate server in front of your appserver like ngnix or apache or express (or akamai) can do it.

We can move our critical resources very early in the waterfall.

## What about the repeat view?

Am I sending all the resources down again?
The server has no knowledge of what the client has.
We don't want to overpush, to avoid slowing down the render next time.

**PRPL pattern**. > See slides

My server doesn't have idea of the state of the client's cache.

The "quick" protocol is going to solve this, but it'll be coming in years from now.

(chart of cache usage)

The push cache is the last it's going to be looing at. 
memory cache -> service worker -> http cache -> push cache

Push cache semantics is not standardizes. 
Jake Archibald's post on "push is harder than I thought"

There are also browser inconsistencies on Safari and Edge.

0.008% of the Fastly network is push initiated.

It we distroyed push, would anyone really notice?

So when should I push?

- you have long RTTs on serer processing
- you can use asyunc push
- you have a client rendered app shell
- you control the client cache

Other solutions?

## The future

Can we fix the problems with push?

If we could know what the client cache has, we could send only the missing assets.

CacheDigests for HTTP/2 -- a draft

Chrome and FF are extremely interested. But still seems to be complicated. 

## 103 hints

103 response indicates what the server is likely to send.
A HTTP status code to indicate hints.

With early hints server push would be much much simpler.

## Priority hints

We can specify the importance in the HTML for `link`, `img`, and `fetch`.

Get involved in the discussion in GitHub.

## Closing

H2 doesn't solve everything.
Performance if for humans, optimize for user experience first.

See resource loading check-list picture. :)

- identify your critical resources
- preload hidden subresources
- preconnect critical third parties
- avoid pushing with preload
- use async push with care
- decorate html with priority hints
- use early hints when available

---

> @patrickhamann