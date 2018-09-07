---
layout: post
title: The Web Authentication API - Imagine a World Without Passwords - Suby Raman - Full-stack Fest 2018
date: 2018-09-07 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> Passwords are a problem. We reuse them. We forget them. Worst of all, they’re easy to steal.
> The Web Authentication API is now available, providing a Javascript API to integrate with strong authenticators like biometric readers, making a password-free future more possible. Let’s learn how!
> In this talk Suby will discuss the history and weaknesses of passwords. He'll give an overview of the Web Authentication spec and the problems it attempts to solve. He'll give code samples describing the basic implementation on the server and client. He’ll describe the user-experience and engineering challenges faced by my team in integrating the Web Authentication API into our product. He will conclude with thoughts on the prospects of Web Authentication, and why he feels it could have a significant impact on the way we web developers think about security.

Passwords are lame. We need to replace them with something better. And they should protect all of your data, medical information, etc.

> There's no cloud, it's just someone else's computer.

Go back in time, the Romans used passwords to trust military in the armi. In the 60's Fernando Cornatò invented computer passwords. 

In the 80's providers used passwords to make you access the internet.

## Problem 1: they are shared secrets.

 My cat wants to register on my website, i store it in my DB, then Darth Vader comes and he can: 

- accesses to the DB
- read the password while it's in transit

Now Darth can fully impersonate my cat.

## Problem 2: they are hard to create and remember.

 Most of us uses simple password like 123456, password, etc. 
Darth can access a dictionary of common passwords to go.

## Problem 3: they're easily stolen

Fishing. You fake google login page, but it's not google, it's https://www.portal-login-online.com 

It happened during the Clinton campaign.

## Problem 4: Passwords are reused

I recommend to d oa password manager tool.

## Problem 5: they are hard to secure

Even if they are md5, the dictionary of common passwords serves here too.

---

> It's become kind of a nightmare

They represent one of the greatest user-experience cnallenges of our time.

How can Web Auth solve it?

Public Key criptography, it's developed by Google, Mozilla, etc.

Cat / Darth examle. 

Cat has a private and a public key. The public can be sent to the server and stored to the DB. The combination of the two allows us to authenticate.

Even if Darth catches the key in transit or in the DB, it's useless.

Private key could be the authenticator, like Touch ID, Windows Hello, etc.

It's strong, scoped and 

Scoped meaning that even if it's a phishing attent, it will be detected.

Attested meaning that we can crypto prove that a keypair comes from a secure hardware.

## Registration

Server requests the user to create a new keypair, and the public is sent to the server to be kept. 

```js
await navigator.credentials.create({ publicKey: {...} });  
```

Shows the code for the public key: `challenge`, `rp`, `user` and `pubKeyCredParams` fields of the plain object.

Shows a video of doing this in the browser console

Data retrieved from credential creation: 

`clientDataJson`: we get an object with the `challenge`, the `origin` and `type` fields.

`attestationObect`: shows it in the console decoding it using `CBOR.decode(credential.response.attestationObject);`


_(too technical too fast here, must check the video of the presentation again :))_


And you're done with the registration!

We solved the facts

- it's not anymore a shared secret,
- not hard to remember, 
- not easily stolen 
- not re-usable, 
- easy to secure.

The website requests an assertion from the user's authenticator (hello, touch id, etc.)

It then requires assertion using 

```js
assertion = await navigator.credentials. get({publicKey})
```

Server verifies the assertion then.

```js
... 
if (valid) return "Hooray!"
```

What if I lose a device? Do I have to re-register to every website? 
Maybe. It's not a solved problem.

> Security is not a single technology
> It's a constant process and discipline

Ciao.

---

My questions

> How can we make sure that authenticators like Apple, Microsoft etc. don't share our biometric data to a central server?

We need to trust manifacturers. Good. We're giving all the power to an enterprise. I think I might prefer passwords :smile:

> @subyraman