---
date: 2025-11-23
---

Just watched a prime video where he says he doesn't understand Clean
Code&trade;'s insistance on small methods.

There are many concepts that contribute to the idea that small methods are a
good thing.  If I narrow it down, I would say there at least 3 concepts that
are prerequsites to understanding why small methods is a practical suggestion.

In no particular order:

- Levels of Abstraction
    - Classes/Methods shouldn't mix levels of abstraction
- Procedural Thinking (and why you should avoid it)
    - A common mindset to avoid
- Encapsulation, specifically Isolation aka Information Hiding
    - Classes shouldn't expose, or give direct access to, internal state
    (instance variables)
    - Interacting with and manipulating state happens via methods


# Levels of Abstraction

![]({{ site.image_url }}/spacial_model.02.png)

Here we have a simple model of a rails app or maybe any MVC web app. It's
probably won't match a lot of rails apps, but ideally, they would be organized
like this.

It's not exhaustive, but it serves its purpose.

When I think about the components in an app, this represents how I organize
things spatially in my mind.  But it also roughly matches the execution path,
which flows top-down.

The components are also positioned in a way to matches their level of
abstraction.

Level of Abstraction is a spectrum from Human to Machine.  Human at the top,
Machine at the bottom.

It's also relative.  There are no absolute classifications for where code
fits in the spectrum.

When DDD suggests ubiquitous language and modeling the code after the language
that the business uses, we're talking about High-level abstractions, or
high-level concepts.

When data is being directly manipulated, that is low-level.

When you drive a car, you're using high-level components.  Steering wheel,
pedals, etc.  The low-level components are things like spark plugs,
transmission, alternator, etc.

If your app has background jobs.  The job is at one level of abstraction.  The
code that manages the queue and actually runs jobs, then monitors the status of
jobs.  That code is at a higher level of abstraction.  It's overseeing and
managing jobs.

So, when we talk about small functions, it's not an absolute rule.  Like any
principle in software, approaching it like it's dogma is a mistake.  What's
important here though, is small functions matter at lower levels of
abstraction.

Procedures, aka service objects, which coordinate and orchestrate different
components, are high-level.  Procedures don't follow the same rules and values
that typical classes follow.

It's not just mixing levels of abstraction.  Procedures, shouldn't be
fragmented.  Ideally the whole procedure is defined in a single class.
But, it shouldn't do any real work, it should delegate to classes that
handle that stuff.  This will keep noise away and make reading/following the
procedure easier.

# Procedural Thinking

A lot of developers think procedurally.
That software and code is about describing a sequence of steps.

This is not what OOP or FP is about.

Software has always been about data structures and algorithms.

A well defined data structure is a work of art.

<!-- A lot of people are hesitant to name and introduce new concepts into an app. -->


# Encapsulation

- Encapsulation, specifically Isolation aka Information Hiding
    - Classes shouldn't expose, or give direct access to, internal state
    (instance variables)
    - Interacting with and manipulating state happens via methods
    - Interface over implementation

Encapsulation is super important.

One of the arguments against small functions is that jumping from function to
function sucks.  It does, people aren't wrong.

However, if you have good encapsulation, you can have small methods and not
need to jump around.

Let me explain.

Regardless of what language you use to build software, it has a standard
library.

For common things that aren't in the standard library, there are well-known
libraries that fill in the gaps.

When you need more info, you go to the api docs, right?

What do the api docs show you?

Interfaces aka method signatures.  A lot of times, they will also show you the
code for any methods, but how often have you actually looked at the code?

For most people, the answer is never, unless they were curious.




