---
layout: post
title: "My Experience with Scala"
---

I am gonna talk about Scala in a hope that it motivates you to learn/adopt scala in your next project. I am not gonna go over the stuff that is available on the docs page of Scala like performance, functional but ideas around developer experience and productivity.

Disclaimer: Some of the goods mentioned here will never be realized by you if you never went through docs/blogs on scala or your senior engineers were bad programmers and they didn’t wanna change things.

## Concurrent Programming

Scala has the easiest tools to implement Concurrent Programming.

Experienced programmers and “genius” programmers can implement concurrent programming in any language and/or claim so.

But when junior engineers are concerned, there is no better place than Scala.

The simplest version is Wrap it around Future {}. How simplest is that?

## Immutability

When I started with Scala, I thought immutability is not that much of a big deal. I thought “I am not a library/system developer and I am not writing any code with shared variables/resources”.

But only after months, I realized that immutability leads to fewer bugs.

It’s like Math. Everything is defined. Once defined, you can’t change it. if you do, it won’t work.

```scala
val a = Seq(1,2,3)
val b = a.map(t=>t*t)
register(a)
process(b)
```

In this block, if you are concerned with `process` function, you only need to check the value of `b`. You never need to check what happened to `a`.

But in other programming languages, by default, you have to check if a.map is changing values in place or not and/or if the register is changing them. (With correct tools, this problem would never come up in other languages but scala forcing this by default is a very good idea).

This saves us from bugs and tonne of time that was spent in debugging.

## Unit testing with Mocking

If you are a beginner, you will end up writing unit tests, and that too using mocking. This is true for most languages but feels natural when you write it in Scala due to the Immutability and discouragement of global variables.

How would you write code if the usage of global variables is discouraged? only one way: Pass it via the constructor or function. If you do that, mocking becomes much easier to set up. You don’t have to worry about other test cases messing up your logic.

## Adequate Functional programming tools

Functional programming has many benefits (look it up). But most of us never need those highly complicated concepts because most of our code deals with business logic. Scala's standard library has just that.

Scala, by default, comes wraps most things in basic functional paradigms. Option, Either, Try, and even Future. Everything behaves in a consistent way improving developer productivity.

## Coding Style Will Improve

Because of all the above advantages, it is only natural that your coding style will improve. Moreover, your coding style in other languages will improve because of the ideas you picked up in Scala. For me, it did with PHP. I became a better developer than before My code and my junior’s code (whom I trained with my ideas) always looked cleaner than others and colleagues would say the same about my code(A little bit of bragging there 😁).

So, If you are learning scala or wondering if you should use it for a new project in your organization, I suggest that you do. As always, see if scala and scala’s ecosystem suits you. But from developers’ experience and productivity, it is one of the best languages one could work with.

*Originally published on [HackerNoon](https://hackernoon.com/my-experience-with-scala).*
