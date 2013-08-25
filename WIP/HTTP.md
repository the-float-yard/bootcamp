# HTTP

This section may feel a little academic, as day-to-day you may not have to worry too much about how HTTP works, as things like Rails will hide much of it for you. 

However, given that HTTP underpins how browsers and web-servers communicate, and thus underpins how most of the internet works, and thus underpins _your job_, it'd probably be good to understand a little about how it works.

Also, it's useful to know what Rails is doing for you, so that if you get tripped up by something, or something breaks, you can unpick what's going on more quickly.

## Outline

### HTTP

HTTP stands for HyperText Transfer Protocol. It is a protocol by which computers can communicate with each other and request and receive hypertext (like HTML).

### Protocols

A protocol is a simple way of saying something like a "a finite, well defined language which computers can use to communicate with each other".

Let's understand protocols by way of analogy: robot coffee shops, of course. 

![coffee](http://media0.giphy.com/media/jaq7CPs6tjaIU/200.gif)

You want to build a chain of coffeeshops, staffed by artisan robot baristas. You also want your geeky friends to be able to build their own robot coffee buyers that can wheel down to the coffee shop and collect their favourite Guatemalan iced-latte from your shop.

#### How are you going to design your robots' brains so they can communicate with their customers, and undersstand and deliver orders?

**The naive way**: You could teach your robots to hear, parse, and understand any english phrase. This would mean that they could understand:

> Do you sell cold brew?

and

> One cappucinno please.

and even

> A'ight mate, can I get three triple-shot lattes?

Hopefully you can already see the issue with this: English is kind of sucky as a communication language. It is ambiguous, difficult to parse and it's generally hard to build computers that understand it well (see: Siri).

It also imposes unreasonable demands on your coffee shop's robot customers as they would also have to be able to understand english to understand what your robot baristas were saying.

**A better way: a protocol** If we think about it for a while. We might realise that it is somewhat unnecessary to enlist the entirety of the english language, just to order coffee. The following types of exchanges would probably cover 99% of the required conversation in that scenario:

> Customer: I would like 1 cold-brew and I would like 2 lattes.

> Barista: Okay _or_ Sorry we don't have cold-brew.

---

> Customer: Do you sell lattes?

> Barista: Yes we sell lattes _or_ No we don't sell lattes.

---

> Customer: Do you accept credit cards?

> Barista: Yes we accept cards _or_ No we don't accept cards.

---

> Barista: That will be £6.25.

> Customer: Here is £10 cash _or_ Here is my credit card.

---


> Barista: Here is your change _or_ here is your credit card.


We could reduce these exchanges down to a few rules.

First we define a strict set of things that can appear in a message

**Parts of a message:**
* <n> integer number
* <amount> an amount in £s
* <coffee-type> valid type of coffee
* <payment-type> valid payment type ("cash"/"credit card")
* <barista-verb> actions baristas can take: ("accept"/"sell")
* <barista-noun> either <coffee-type> or <payment-type>
* <affirmation> either "yes" or "no"

Then we define some modifiers to modify the above.

**Modifiers:**
* [optional] - bracketed items are optional
* \* - asterisked items can be repeated any number of times

Then we can define some customer phrases that use the parts and modifiers above.

**Customer phrases:**
* ASK\_FOR\_COFFEE: I would like <n> <coffee-type> [and ASK\_FOR\_COFFEE]\*
* REQUEST: Do you <barista-verb> <barista-noun>?
* OFFER: Here is my [<amount>] <payment-type>.

And do the same for the barista.

**Barista phrases:**
* RESPOND: <affirmation> we <barista-verb> <barista-noun>.
* REQUEST\_CASH: That will be <amount>.
* RETURN\_PAYMENT: Here is your [change] [credit-card].

We may also define valid communication sequences. I.e. a BARISTA::RESPOND may only follow a CUSTOMER::REQUEST.

What we have defined above is a basic protocol. Our simple set of rules, can completely describe an artisan coffee transaction. A limited, finite set of rules, considerably reduces the complication in designing and building either a barista or customer that can interoperate. Not only does this make our job a lot easier, but if we have a nice protocol it's more likely to be used - so our coffee chain is more likely to be successful.

### The HTTP Protocol

The protocol for HTTP is somewhat similar to our coffee barista protocol. But it is somewhat more detailed as it is (actually complete) and has some more features. Instead of allowing customers and baristas to exchange money for coffee, it allows web servers and user-agents (browsers) to exchange HTML.

The official spec for HTTP version 1.1 is RFC2616 (catchy title huh?) and can be found [here](http://pretty-rfc.herokuapp.com/RFC2616).

## Reading: 

### Introduction

Read the introduction to the HTTP spec: [Chapter 1](http://pretty-rfc.herokuapp.com/RFC2616#introduction)

### HTTP Message

Read: [Chapter 3: HTTP Message](http://pretty-rfc.herokuapp.com/RFC2616#httpmessage)q

1. Explain the difference between the HEADER and the BODY?
2. How does this relate to `<head>` and `<body>`?
3. Using curl, request the headers for http://floatapp.com and explain what each of them mean.


### Method Definitions

Read: [Chapter 9: Method Definitions](http://pretty-rfc.herokuapp.com/RFC2616#method.definitions)

1. Explain "safe methods"
2. Are GET requests guaranteed to be safe?
3. Explain idempotence
4. Why is idempotence important
5. If we wish to create a new resource on the server, should we use PUT or POST? Why?

### Status Codes

Read: [Chapter 10: Status Codes](http://pretty-rfc.herokuapp.com/RFC2616#status.codes)

* If we were building a web application, what status code would you return if a logged out user requested a page that could only be accessed by logged in users?

* What status code would we return if there was an internal error in our application? Maybe our database has crashed and our webserver cannot get the data the user has requested?


### Caching

Read and watch: [Google's HTTP caching intro](https://developers.google.com/speed/articles/caching) (it's much more informative than the HTTP spec)

* Briefly explain what HTTP caching is, and its benefits.
* What would be an appropriate cache-expiration duration for the google logo on the google homepage? Why?
* _Now that you have answered the question above_ use the chrome developer tools to determine how long google actually cache the logo for. ([hint](http://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome)).
* What would be an appropriate cache-expiration duration for the list of tweets on your (logged-in) twitter timeline? Why?
* If we set the float logo on the floatapp.com to have a cache-expiration duration of 100 years, that means that anyone who has viewed the floatapp.com homepage will have the float logo served from the browser's cache for the next 100 years (as long as they don't empty the cache manually). If we updated our brand and changed the logo, how could we ensure people saw the new logo in their browser, rather than the cached one?

