---
date: 2025-11-18
---

I just watched another video of prime explaining that he doesn't understand why
clean code suggests having small functions, roughly less than 5 lines.

I am going to explain this as concisely as I can.  Although, there are a lot of
concepts that are at play.

Before I get started, let me say 2 things:

1. I don't know Uncle Bob's version of Clean Code&trade;, but that is
   irrelevant.  The point is developing robust, flexible, easy to maintain, and
   easy to understand software.
2. Small functions do not apply to the whole app.  It does apply to the vast
   majority of the app, although at higher levels of abstraction, procedures
   and orchestrating multiple components of the system require larger functions,
   but without doing any heavy lifting.

## Concepts at play

Here are a list of concepts that require some level of understanding to see the
bigger picture.

1. Levels of Abstraction
2. Encapsulation and Isolation (think: blackbox programming)
3. Coupling
4. Composition
5. Data vs. Behavior

## Prime's Reasoning

Prime is a fan of Locality of Behavior by the HTMX guy.

His take basically says that jumping from function to function to
understand or debug code, is painful and basically increases cognitive load.

This isn't wrong, _if_ you have to jump around.

This opinion is the result of procedural thinking.


## Encapsulation and Isolation

There are a few basic principles about classes and methods that a lot of people
never learned, which isn't their fault.

### Interfaces are more important than implementations.

How a function or method is implemented should be irrelevant.

A method signature is made-up of the method name, the inputs, and the output.

This _should_be_ all that matters.  If this isn't the case, than the author
likely had a procedural mindset and didn't understand the principles covered
here.

If you don't believe me, when I say that this is the only thing that matters,
let me as you a few questions.

When you use your language's stdlib, or you use some 3rd party package in your
app, how often do you read the source code?  You will go look up the API docs,
but what are these docs exposing to you?  Modules and method signatures.  Doc
generators _will_ link you to the source code, but how often have you actually
looked at it.  If you're curious that's one thing.  But when is the last time
you **had** to understand _how_ the function worked?  When's the last time you
had to debug, these libs?  Likely never.  What hashing algorithm does your
stdlib use for hashes/objects?  Most of us don't know and most of us will never
know. Why?  Because it does what's on the box, and it gives you all the tools
you will ever need to manage it.  (At its level of abstraction)

In other words, the inner state is encapsulated and it's hidden from the code
that consumes this class.

Ideally:

1. A class shouldn't know about the internals of another class.
2. A method shouldn't know about the internals of another method.
3. The inner state of a class should never be exposed or directly accessible.

It may take effort to start applying these principles, because after all, you
can read all of your apps code.  So if you can read how something works,
you will tailor your code to meet its specific needs (see: tight coupling).

### Composition - pt. 1

Composition comes in 2 forms:

1. Function composition
2. Data composition

Let's ignore function composition, although the same basic idea applies.

A general rule, although not absolute, is that if a class/method is interacting
with some object, than it is at a higher level of abstraction.  It oversees
and manages or controls that object.

### Levels of Abstraction

I've already mentioned it a few times, but what is a Level of Abstraction.

It's easy to think of it this way: human is high-level, machine is low-level.

A straight-forward example would be a car.  To drive your car you have a
key, steering wheel, pedals, and a few other user interface components.

These are the high-level components of a car.  When you interact with these
components, they turn around and interact with other components that most
drivers are unaware of and couldn't even identify.  Then those components
might interact with other components and so on.

There is a principle that suggests a method should only touch one level of
abstraction.  I would loosely extend this to the classes as well.

In the wild, procedures have a tendency to break this principle.

In fact, a procedure is a level of abstraction by itself, procedures live at
a high level of abstraction.  It shouldn't actually do any real work.  Instead,
it should delegate to lower-level components and they will do the work, or
further delegate to other components where eventually the dirty work happens.
Although, ideally the amount of delegation should be minimal/shallow.

Not always, but ideally, high level procedures should interact with high level
components.

But remember how I said that you should separate levels of abstraction?
I also suggest that you should keep the same level of abstraction together.
Meaning, if you have a high level procedure, don't break it apart.

These are the methods that will be more than 5 lines.  But they should
be easy reading like a recipe.  This way you know everything that
a procedure is doing and it's all in one place.

But, thanks to encapsulation, we can ignore the low-level, heavy lifting
that is required to make those steps happen.

### Separating Data from Behavior pt. 1

There are a few side-effects of procedural thinking that hinder developers
and the apps they work on.

One is primitive obsession and being reluctant to create new classes.

There is so much focus on what the code does, but not enough focus on data
structures.  In The Structure and Interpretation of Computer Programs,
data is described as passive, procedures are described as active.

Procedures are context aware, but data is context-free.

### Atomic Operations - coupling and composition

At this point, we've talked about levels of abstraction and how procedures
are generally high-level abstractions.  So let's look at low-level
abstractions.  They should look very similar to the modules defined by
the stdlib.  Their API defines a full set of atomic operations that
give you the ability to do anything you need to do with that class,
and they expose any data you would want to know.  They also rarely
impose logic and restrictions.  They describe what is possible.

What we are trying to accomplish is building a solid foundation that our
app is built on.

Once we define low/mid-level data structures and expose all its useful
data points/interactions via methods, then the rest of our app gets
all that functionality for free, through delegation.

This is where small methods and atomic operations matter.

It's ok to make methods that do more than one thing, but as mid-level
abstractions.

Once we introduce methods that do more than one thing, they become less
reusable.  The situations we can use them in start to drop off.

It's at higher levels of abstraction where we can compose these atomic
operations and impose restrictions.

However, if we do this at the lowest level, then if we need the atomic
operation, we either have to duplicate code, or refactor and split the function
anyway, then use delegation in the original method.

This also means that places in our code that actually do the work
are isolated to a single instance.  Keeping it free from logic and
restrictions helps ensure that our code can consume/use these methods
with confidence.

The same confidence that we have with our stdlib or 3rd party dependencies.


