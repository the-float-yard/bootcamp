# Ruby, Rails, Ruby on Rails, what's the deal?

![crazy](http://media2.giphy.com/media/C1ODiCUL8VO9O/original.gif)

Let's get something straight, _Ruby_ is a programming language; _Ruby on Rails_ (or just _Rails_) is a framework, written in ruby, to help you build web applications more easily.

This implies a few things:

* All of _Rails_ is written in _Ruby_.
* We could, if we wished, rewrite all of Rails ourselves, in Ruby.
* We don't have to use Rails to build web applications in Ruby, but it (mostly) makes our lives easier.
* _If we want to become good Rails developers, we also have to be good Ruby developers._

That last point is important, and that's what we are going to work on first. Rails lets us build things quickly (which is awesome), but following a rails tutorial and getting a blog built in rails, won't necessarily teach us very much about Rails, or ruby for that matter.

Now, you might think, "well if Rails is written in Ruby, can't I just build lots of rails apps, and I'll get better at ruby?". Unfortunately it doesn't tend to work like that, because:

* Rails makes significant changes to ruby under the hood, which means it's hard to know when you are working with _just ruby_ or _rails modified ruby_.
* Rails gives you a lot of structure - it provides all the classes for you to "fill in" (ActiveModel::Base for example), and the directory structure etc that you need. We should learn how to build some of this structure ourselves.
* Rails does a lot of magic. This _magic_ is generally a win, but if you don't understand ruby very well, that magic can be pretty confusing, and hard to comprehend when things don't work as you expected.
* Rails is not perfect. Sometimes the _rails way_ isn't the best way of solving a problem, but if you don't know how to write ruby otherwise, you'll be kind of stuck.
* We don't always want to build big web applications. Sometimes we want a tiny little web application, where something like [Sinatra](http://www.sinatrarb.com/) is a more appropriate, lighter weight, tool for building web applications. Other times we just want to write scripts, or other apps, in ruby to make our lives easier, for fun, or to just get our job done.

## Rails modified Ruby

Above, I said that rails "modifies" ruby. What do I mean by this? Let's take a quick diversion.

As an example, open up a irb console (`$ irb`) and type `Date.yesterday`:

```
› irb
>> require 'date'
=> true

>> Date.yesterday
NoMethodError: undefined method `yesterday' for Date:Class
        from (irb):2
                from /Users/Roberts/.rvm/rubies/ruby-1.9.3-p125-perf/bin/irb:16:in `<main>'
```

Okay, so there is no method `yesterday` on `Date`.

Now, open up a `rails console`, which is just `irb` but in the context of rails. (You'll need to find a rails project and do it from within there:

```
› rails console
>> Date.yesterday
=> Thu, 22 Aug 2013
```

Woah? Where did that method come from? Rails added it to ruby for us. It adds a bunch of other methods too: [http://api.rubyonrails.org/classes/Date.html](http://api.rubyonrails.org/classes/Date.html). Rails can do this, because Ruby is so flexible. We can add methods to existing classes easily. We could write `Date.yesterday` ourselves if we wanted:


```
› irb
>> require 'date'
=> true

>> class Date           #reopen the date class
>>   def self.yesterday #add yesterday method to the date class
>>     Date.today - 1   #subtract on day from the date
>>     end
>>   end
=> nil

>> Date.yesterday
=> #<Date: 2013-08-22 ((2456527j,0s,0n),+0s,2299161j)>
```

Huzzah, it worked. The output isn't quite as pretty (rails also modifies how dates print out in the console, but you should get the idea.

Okay, let's learn some ruby.

# Lesson 1 - Ruby Koans

Okay. Without further ado. Let's do lesson 1!

The lovely guys at Neo (the scottish contingent of which are a floor below you _right now_) have written some [ruby koans](http://rubykoans.com/) to teach you the basics of ruby. From their website:

> The Koans walk you along the path to enlightenment in order to learn Ruby. The goal is to learn the Ruby language, syntax, structure, and some common functions and libraries. We also teach you culture. Testing is not just something we pay lip service to, but something we live. It is essential in your quest to learn and do great things in the language.

__On Testing__: Testing is _a big deal_ in the ruby community. Hopefully, testing, and in particular test-driving, our software should help us write better, more maintainable code, more quickly. Testing is hard though, and will take some time to get good at. Don't worry, just keep trying, it gets easier. The ruby koans are all written as tests, so as well as learning about ruby, hopefully you will learn something about testing too.


## Lesson plan: 

1. Go to [http://rubykoans.com](http://rubykoans.com) and follow their instructions for getting started.
2. Work through the exercises. For the basic introductory stuff, you should work on your own computers (but feel free to ask each other for help, and me if you get really really stuck (try and battle through it on your own for a while first though)).
3. When you get to a `_project` lesson, I would like you to pair program. Come ask me what I mean by that when you've both got to your first one.

### Notes:

* If you have questions/wonder how something works, write it down, google it, think about it, ask each other. Don't just blast through the lessons, the point is to learn, not finish quickly. I will very gladly discuss these things with you afterwards, so make sure you write down your thoughts and we can go through them over lunch or something.


[← Intro](README.md) | [Lesson 2 →](2-Git-Immersion.md)
