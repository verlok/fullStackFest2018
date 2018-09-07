---
layout: post
title: Killing the checkout or: How I learned to stop worrying and love Payment Request - Krystian Czesak - Full-stack Fest 2018
date: 2018-09-07 09:00:00 +01:00
categories:
- conferences
tags: [full-stack fest, notes]
---

These are my notes from Full-stack fest 2018 Barcelona conference.

> What if payments were natively supported in the browser? This is the goal of W3C’s Web Payments Working Group first deliverable: the Payment Request API.
> Now implemented in most major browsers and with the Payment Handler API on its way, you’ll never think of payments on the web the same way. We want that by the end of this presentation, you not only know how to accept payments on the web through the Payment Request API, but would be able to code your very own payment method through the Payment Handler API.
> Let’s spread the knowledge around Payment Request and Payment Handlers, killing the checkout as we know it, forever.

History: 
402 payment request, reserved for future use. Not used currently.

- No native solution to initiate transfer money on the web
- Same solutions were attempted
  - W3C ecommerce interest group (micropayments, like for apps). solution in 2000 was very verbose 
  - Ecommerce Modeling Language (ecml) - never really caught
- Closest solutions today
  - 3rd party payment libraries

State of the checkout

- Not changed for a while
- Same process in different websites
- Same problems solved over and over
- Few redeeming features help reduce friction

As a result

- 69% carts are abandonate
- 27% abandoned because complicated
- 14 fields to fill on average

So Web Payments

(shows a video of the payment layer on Chrome mobile)

- Total
- Address
- Payment details
- CVV code
- Thank you page

It's now supported in Edge, Chrome, FF nightly, ...

## What is a payment request

- a checkout experience by js api
- directly in the browser
- can show multiple payment methods
- It's NOT a paymente processor
- Unbranded experience --- :(

## Code overview

```js
new paymentRequest()
details = {
    displayItems: [
        {
            label: "shipping"
            ...
        }
    ]
}
```

Wha is method data?

- What they can pay with

```js
const methodData = [
    {
        data: ...,
        suportedMethods: "basic-card",
    },
    {
        data: ...,
        supportedMethods: "https://mollie.com/ideal/pay"
    }
] as PaymentMethodData[];
```

- Then with `paymentRequest`

```js
paymentRequest.addEventListener(...);
paymentRequest.addEventListener(...);
```

Showing the sheet

```js
const paymentResponse = await paymentRequest.show;
let order;

if (paumentResponse.methodName === "basic-card){
    order = processCreditCard(paymentResponse.details as IBasicCardDetails);
}

await paymentResponse.complete(order.status);

complete(order);
```

## Payment Handler API

???

## Browser's payment methods

Chrome: basic-card, Google Pay, interledger
Safari: Apple pay only
...

## International Payment Methods

- bank transfers / ACH
- boleto bancario
- ...


## Payment Handler demo

- Install the payment method in your browser
- Find it in payment methods in the "checkout" layer
- Surface payment...

## What's needed

- payment-manifest.json
- manifest.json
- service-worker.js

- Install page `GET /`
- Identifier URL `GET /pay`
- Checkout `GET /checkoyt`

(See slides for details of what to put inside each file)

The install page is made though a service worker

Then `await registration.paymentManager`...

## Sum

Payment handler API

- Allows to surface our payment method
- Standardizes payment method comms
- Allows for register 3rd party payment methods

## Caveats

Payment affecting

- discount codes
- tender transations
- few payment methods
- payment handler API adptions

Checkout affecting

- Accept T&C
- KYC info
- Delivery dates
- Gift message
- Subscribe to newsletter

Keep those in mind. It's a paradigm shift.




---

My questions

Q: we work with the Fashion industry and our customers are very picky about art direction and graphics. How customizable are the new "checkout phase" using the payment API? Can we at least change the color of the background, text and buttons? 
A: not very customizable. Having a standardized interface can help build trust, then.

Others:

Q: Why does a user have to install a payment handler himself? If the `/pay` URL has been added to the payment request config, doesn't it have all the information it needs?
Q: How does the api works on desktop?
Q: Are the payment configs shared/synced between mobile/desktop? (i.e Chrome)



> @krystosterone