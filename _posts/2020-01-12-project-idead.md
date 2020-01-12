---
layout: post
title: "Some project ideas"
date: 2020-01-12 20:32
categories: jekyll update
---

Many programmers find it difficult to focus on projects when they don't have direct incentives. This is demonstrated ofton on the excelled [Embedded.fm](https://embedded.fm/) podcast, where a common question is

    Would you rather complete one project, or start a dozen?

A large percentage of the guests say that they would rather start a dozen, or even if they would rather not, they admit that this is what happens.

Software is an exciting thing and it can seem like someone else is always working on something cooler than you, and that makes you want to use that cool new thing!
And maybe it's open source and free, so why shouldn't you?

However, many genuinely great or useful things come not from suddenly changing tack and trying out a new toy, but from insight and effort in a specific domain.

With that in mind, and with the background outlined in [my previous post](https://timguite.github.io/jekyll/update/2020/01/04/learning-other-languages.html) about how I am trying to learn many different programming languages, I have decided to write down here some of the ideas I would like to focus on and develop further.

# Data.Maybe in Python

[Data.Maybe](https://hackage.haskell.org/package/base-4.12.0.0/docs/Data-Maybe.html) is a commonly used package in Haskell.
It allows the result of expressions to be encapsulated as `Just x` or `Nothing` and provides a number of functions to access those values.
This is used for describing the output of functions within Haskell's type system.

Python does not have a strong type system like Haskell.
However, I recently found out avout the [singledispatch](https://docs.python.org/3/library/functools.html#functools.singledispatch) decorator, which allows function overloading based on type!

To find out more and develop my understading of Python, Haskell and types, I think it would be really cool to implement an approximation of Data.Maybe in Python.

I have already made a good start [here](https://github.com/TimGuite/python_maybe).

# Simulate undergraduate mechanical engineering

Once I had grown up a bit at university, I started taking the time to actually try out and test some of the things I was learning.
I found, as I always have, that this was a great help in understanding what I was learning.
A good example was implementing Fourier Transform in Python directly rather than just using the first package that appeard on Google!

I have been thinking recently about how much of my engineering degree I have probably forgotten by now!
And I thought a great way of reminding myself and triggering some further understanding would be to simulate some of the situations which were presented to us in a theoretical manner.

Ideas include:

- calculating centre of mass, second moment of area, shear and compression forces on static objects
- basic electrical circuitry
  - minimizing resistor circuits
  - how current and voltage change with time in RC circuits
- mechanics
  - how does a pendulum behave?
  - how does an inverted pendulum behave
- controls (extended!)
  - how could one control an inverted pendulum?
  - how would the control parameters change depending on the physical attributes of the pendulum?

# pysimpleapp Qt implementation

[pysimpleapp](https://pysimpleapp.readthedocs.io/en/latest/) is a good example of a project I started and have somewhat neglected.
It is an application framework which I thought about and created, and I think it would be useful for others who either need an application framework or want to understand what they do.

It is very much designed to be a white box project, where everything can be seen and is available.

I would like to add support for the [PyQt](https://riverbankcomputing.com/software/pyqt/intro) graphical framework so that it can be more useful to more people.

This would also prompt me to improve other parts of the framework, and to create more examples!

# Circuit layout for night lights

A few months ago, I laid out a few dozen leds and resistors, some transistors and an Arduino knock off, and soldered together what I think is quite a nice night light for my girlfriend.

It should be relatively simple to move this on to a PCB using free online tools and then actually get this built.
If I could then develop a nice enclosure for it, this might be something which could be taken forward as a Kickstarter type project!

# Wish me luck!

I'll probably need it!
