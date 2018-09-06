---
layout: post
title: Building peer-to-peer apps with the Beaker Browser - Tara Vancil - Full-stack fest 2018
date: 2018-09-06 09:00:00 +01:00
categories:
- conferences
tags: [full-stack-fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> Beaker is a browser for exploring and building the peer-to-peer Web. With Beaker, you can build and host websites directly from your computer — no server required! But what’s the Web without apps? Is it really possible to build an app without managing a server or a database? This talk will explore the world of peer-to-peer apps, and take a look at how they use Beaker’s APIs to manage user data, create profiles, and connect users.

When I discovered HTML5, CSS3 and JS it was a very awesome momet for me, I could crate styff, it was like a humanity wide language.

The web is open, free, decentralized (no gatekeepers), shared (it belongs to all humanity, and we maintain and improve it).

I <3 the web. I know it's imperfect, and that's OK. But it's so young, it was created in 1990, 28 years ago. How will we shape it for the next 30 years? What capability will it have?

# Complains

## Servers suck

Geocities was made to make websites, used by millions, but it got shut down.

Now we deal with heroku and aws, but I prefer not to deal with it, I prefer to design stuff.

Maybe there's room for improvement.

## Apps aren't customizable

Instagram doesn't have a chronological feed.
Twitter is frustrating because of a dozen reasons. 
I don't have a way to actually shape how they work.
Our online experiences are defined by corporations. I'm not sure I want this for the next 30 years.

## It's too hard to connect

Too hard to make apps that connect users.
With Slack for example, I need to send a message to a corporation, then they send the message to another person.
Why can't we send a message directly?

(recap. servers suck, not customizable, too hard to connect)

# Beaker browser

So: beakerbrowser.com
Made with @pfrazee and @mafintosh

Why don't we just make a browser and use peer to peer to distribute websites.

A client-server protocol like HTTP is request to server, response to client.
Peer to peer is not like taht, it requests it to the whole network, other browsers host the files. It reduces the network cost.

datprotocol.com, datproject.org

How might a p2p protocol change what sucks?

- servers suck less?
- apps be customizable?
- easier to connect?

## Beaker browser demo

The website has a `dat://` url.
I download the site from others visiting the website.

You can choose to seed the websites forever or for a shorter period of time.

You can create a website from beaker and host it directly from the browser.

She shows how to do it. You can create a website easily, change the source directly from its editor. Or you can use your favorite text editor, and it live reloads.

No server involved here.

## Connect with users

Would it be easier?

Apps is made to store data, ... (see slides)
We do it by do post requests with AJAX.
On the P2P web and Beaker, we use `var website = new DatArchive('dat://blablabla.com')` to store data with `website.writeData(JSON.stringify({foo: bar}))`

She demoes `writeFile` and `readFile` in the browser console.

Ok what about in actual app. 

Fritter! `dat://fritter.hashbase.io`

It's like twitter, the posts are json files, profiles too.

To connect to other users you can watch when something changes. Like another user's profile.

---

My questions

Q: How do you register a domain on dat://?

Q: How much time takes to `writefile` to propagate the write to the whole p2p network?

Q: What about using blockchain technlogy to authenticate the data on the P2P network?

> @taravancil