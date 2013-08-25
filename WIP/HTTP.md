# HTTP

This section may feel a little academic, as day-to-day you may not have to worry too much about how HTTP works, as things like Rails will hide much of it for you. 

However, given that HTTP underpins how browsers and web-servers communicate, and thus underpins how most of the internet works, and thus underpins _your job_, it'd probably be good to understand a little about how it works.

Also, it's useful to know what Rails is doing for you, so that if you get tripped up by something, or something breaks, you can unpick what's going on more quickly.

## Outline

### HTTP

HTTP stands for HyperText Transfer Protocol. It is a protocol by which computers can communicate with each other and request and receive hypertext (like HTML).

### Protocol

A protocol is a simple way of saying something like a "a finite, well defined language which computers can use to communicate with each other".

Let's understand protocols by way of analogy: robot coffee shops, of course. 

![coffee](http://media0.giphy.com/media/jaq7CPs6tjaIU/200.gif)

You want to build a chain of coffeeshops, staffed by artisan robot baristas. You also want your geeky friends to be able to build their own robot coffee buyers that can wheel down to the coffee shop and collect their favourite Guatemalan iced-latte from your shop.

#### How are you going to design your robots' brains so they can communicate with their customers, and undersstand and deliver orders?

**The naive way**: You could teach your robots to hear, parse, and understand any english phrase. It would take a lot of time and effort but you might be able to do it eventually. This would mean that they could understand:

> A'ight mate, can I get three triple-shot lattes?

> One cappucinno please.

> Do you sell cold brew?




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

