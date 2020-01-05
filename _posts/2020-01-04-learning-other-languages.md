---
layout: post
title: "Learning Other Languages"
date: 2020-01-04 12:00
categories: jekyll update
---

No, I'm not talking about Japanese. ごめんなさい。
I'm talking about [programming languages](https://en.wikipedia.org/wiki/List_of_programming_languages).
These allow us to work with computers to achieve our goals.
Like spoken languages, there are lots of them!
And they all have their own quirks.

If you're not a programmer, the first thing you would probably notice is that they look different from one another.
Some have semi-colons and curly braces, others have angle brackets and forward slashes, and some don't appear to have any of these.
This is called "syntax" and while it can be a barrier to learning new languages, I think for a lot of programmers this is the quickest part to learn.
The harder part is understanding _how to say things_ in your new language.

My job is starting to revolve around software.
I'm quite enjoying that but as I haven't had much formal training in software, it is easy to feel like you're missing some information that would help.
Especially as every so often someone will show you how to solve a problem in such a way that makes you think _why didn't I think of that!?_

In the last few months, I have started learning a number of new languages at work and on my own.
Some of these I already knew, some I had heard of but never really seen, and some were completely new to me.
Hopefully in the future I will have more time to discuss my adventures further, but for now I will introduce the languages I have been looking at, and resources which I have found really useful for helping me learn and really think about my programming.

# The Languages

## C++

Now _this_ is a programming language.
C++ works in so many different situtations that it would almost be easier to think about situations where it wouldn't be useful.

Want to build a freely available game engine which will allow people to create everything from platform games for phones to open world virtual realities? C++ does [that](<https://en.wikipedia.org/wiki/Unity_(game_engine)>).

Want to program a microprocessor to monitor vibration levels on a pump and send a signal when it is about to break, while conserving energy so it can run on a battery for months or years at a time? C++ does [that](bit.ly/timmscdiss).

C++ allows you to think about problems in the abstract, and then solve them with specific tools.
It gives you a lot of power and control over how you want the computer to work for you, which means you can also break things if you are not careful!

I would very much recommend watching [this interview](https://www.youtube.com/watch?v=uTxRF5ag27A) with Bjarne Stroustrup, the creator of C++. He does a fantastic job of explaining how things ended up the way they are!

## Haskell

Haskell is a _functional language_.
If, like myself a few months ago, you do not know what a functional language is, don't worry about it too much.
I watched a lot of lectures and read a lot of blog posts which seemed to lack a good definition for it.
To make things worse, many modern languages use aspects of functional langauges mixed in with other philosophies.

My attempt to summarize:

```
Functional languages treat everything as a series of operations on data
```

Basically this means your code should start to look like a maths function - `f(x) -> y` - which can be composed - `f(g(x)) === f . g`.

At the start, this can seem like a slightly fancy and difficult way of doing things you've always been able to do.
However, Haskell asks you to look at the world its way, and doing this has introduced me to a number of programming concepts:

- how a strong type system can be helpful for solving problems, not just avoiding errors
- where recursion is truly useful
- the benefits of treating data as immutable
- higher order functions
- folds - left and right!
- functors
- monads

These concepts have already been useful for me in my work and as I continue on this path I think they will serve me very well!

To start with Haskell, use [Learn You A Haskell](http://learnyouahaskell.com/introduction) and to go further, I have been using [Real World Haskell](http://book.realworldhaskell.org/read/).

## Java

Java is one of the [world's most popular languages](https://www.tiobe.com/tiobe-index/).
From what I knew of it beforehand, it was not necessarily the most loved, but because it is used in so many places you can hardly just choose to ignore it.

I haven't learnt a lot of Java yet, but I can already understand some of why people like it and people don't.
It seems I have started at a good time, as Java has welcomed in new concepts, such as those from the world of functional programming, which help you write better code.

One thing I will say about Java is that for a complete newcomer it can be a bit bewildering.
For instance, if you want to learn Java, which one do you want to learn? [Java SE? Java EE? Jave Embedded?](https://www.oracle.com/java/technologies/)
Then there are popular frameworks such as [Spring Boot](https://spring.io/projects/spring-boot) which sit on top of Java but are presented in some places **as** Java.
I found the whole thing quite confusing!

Having said that, I will reserve further judgement until later. There are probably more tutorials for Java than any other language so look for tutorials for the basics first! [This one](https://www.w3schools.com/JAVA/default.asp) is quite simple.

## Rust

Rust is apparently what happened when people who loved C++ decided to make a new language which used all of the best parts of modern language.
It was [developed by Mozilla](https://www.infoq.com/news/2012/08/Interview-Rust/https://www.infoq.com/news/2012/08/Interview-Rust/) with an intent to slowly replace the C++ code which causes bugs in Firefox with a new language in which certain types of bugs would be impossible.

Rust mixes some of the ideas from Haskell with the kind of direct control C++ provides.
Effective parallel computing is a core goal of the language.
Mozilla's work on [Web Assembly](https://webassembly.org/) means that Rust can be used for computation in web applications.
[Embedded devices](https://www.rust-lang.org/what/embedded) are also a target for Rust.

The wide range of applications, along with the fact that[ developers seem to love it](https://insights.stackoverflow.com/survey/2019#key-results), makes it a very interesting language to learn!

### Languages for the future

- Scala - interoperable with Java while keeping a functional perspective
- Elm - functional approach to UI for web applications

# Useful Resources

It can be hard to learn new languages.
Some tutorials are too easy, some answers on Stack Overflow are incomprehensible.
Many people say the best way to learn a language is to need to do something, to solve some problem.
But it's hard to come up with problems all the time!
And sometimes when you need something done, you actually want it done!
So it makes more sense to do it in a language you feel comfortable in.

Where can you get better challenges from?

## Exercism

[Exercism](https://exercism.io/) is a website with lots of challenges in many different languages.
It provides a number of tests for each problem which you have to pass with the code that you write.
The challenges range in difficulty and subject.
One problem, finding the _nth_ prime number, has a maths focus, while creating a binary search tree is a basic computer science problem.

Additionally, for some languages, volunteers will mentor you through a core set of problems.
This means you can get feedback on your code from experts in the language **for free**.
This is a huge help and really gives you confidence to carry on and learn more!

Once you have solved your challenge, you can see how other people on the website solved it.
As there are a wide range of people on the site, some use basic operations and others might use features of the language you have never seen before.
There is always something to take from this.

## Project Euler

[Project Euler](https://projecteuler.net/) explicitly has a mathematical tilt, but it has a **lot** of problems to solve!
You can use any language, so the real work is up front, thinking about how to solve problems.
This could be a bit intimidating if maths doesn't seem like your thing, but I think it is worth trying!
Lots of problems you will come across when programming are just different forms of these problems; thinking about them now will give you a better chance later!

# How do you learn?

If you've got any better ideas, let me know!
I'm always looking for ways to get better and new things to try.
We get better faster by helping each other!
