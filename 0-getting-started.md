# Getting Started

## Prerequisites

![Computers](http://media2.giphy.com/media/HjvvlK5jJRGq4/original.gif)

* A computer (ideally osx/\*nix)
* A text editor you are comfortable with. Use [Sublime Text 2](http://www.sublimetext.com/2) if you aren't sure what to use.
* Somewhere to answer questions/take notes/write down questions for me that you can refer back to easily and won't lose. A notebook works if your handwriting is better than mine. Otherwise evernote/google docs/a text file checked into git also works.

That's about it. Everything else we can figure out as we go along.

## Setup

### Text editor setup

The main bit of text editor setup is to get setup for using two-spaced, soft tabs. This means:

* When you hit tab, your text editor indents an appropriate number of spaces, instead of inserting a hard-tab `\t` character.
* That appropriate number of spaces is 2.

People argue all the time about what is _the best_ in this regard, but at the end of the day what's best is what everyone else does. It really doesn't matter _what_ as long as it's consistent. The ruby community almost exclusively uses two-spaced soft tabs. The JavaScript community is a little more varied, but two-spaced, soft is certainly not unpopular. And all of Float is two-spaced soft tabs.

#### Sublime Text

If you are using sublime text, you want to set the following options:

```
{
  "tab_size": 2,
  "translate_tabs_to_spaces": true
}
```

On OSX you do that by going "Sublime Text 2" > "Preferences" > "Settings - Default" and changing the above options. I am not sure of the exact menu option in \*nix but it'll be similar.

#### VIM

If you are using VIM you can probably figure this out by yourself.

[← Intro](README.md) | [Lesson 1 →](1-Ruby-Koans.md)
