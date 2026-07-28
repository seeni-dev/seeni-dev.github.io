---
layout: post
title: "How a Clean Codebase Becomes Unmaintainable"
---

This is my learned experience from working in Small-Mid Scale Software Companies.

Code should always have a pattern/style. We always strive towards it. But leave it out for a year without a big feature, it might become something unrecognizable to you. We don’t really talk about this in such small-scale organizations. But its existence has to be addressed.

In this short article, I will try to outline how the coding style increases and then degrades.

## Initial Crappy Code

When you start out a project, you write code to figure out the library and rough structure of the codebase. So this is always messy. You do this alone and no one else gonna guide you unless the senior is good with that tech stack. Most of us in small-Mid Software companies have faced this.

## Discovery of style template and 70% Structured Code

As things grow, you have found a style that works for your codebase. As you rush towards all the meetings, you leave things in an “out-of-style” convention in a hope that you can fix them later. And you do fix them silently when testing is going on. You even teach the juniors to adapt the coding style in your project and advocate using the same in other projects and in their career.

## Show Off

Once the product is released, your code is in a wonderful state and you feel proud about it. You should be. You are one of the engineers who really care about cleaner, simple, styled, and more importantly, readable and consistently-styled code. You use your codebase as a reference when reviewing the code of others.

## Slowly Degrading Style

There are mainly two ways, in which your coding style gets degraded.

As the project goes mainstream, you start getting feature requests with timelines like that of thin hair. So you end up hacking the code instead of engineering. [Hacking - Making it work and Engineering - Creating something new in a standardized way with a long-term view]. This is a major cause of style degradation.

As you go into handling many projects, you start to lose control of the packages or libraries that are being used in the organization. Even if you have control, you can’t really have control on the coding style of them since they are usually developed by another team. Juniors due to no fault of theirs try to integrate with whatever library/package provides without pushbacks. One day, you start reviewing the PRs.

When reviewing the PRs, Gargoyle sits in your carefully crafted garden.

You talk with Juniors to understand why. And then you find out your colleague made that library. If you have a relationship with the author, you can persuade them to change it. If you don’t, you got nothing.

Here, the drag begins.

## Eventuality

Eventually, your project will be a combination of N different coding styles with 2N unit-testing styles. There is no escape from it as you move away from the codebase and other engineers with different opinions add their changes.

You will end up doing “refactor” exercises where you invest a huge amount of time to fix up all the mess. This happens at least twice a year. There is no end to this cycle of madness when hotfixes are thrown at the codebase every month with a release target of 1 week.

This is true for most of the small-mid scale software companies where a single engineer is supposed to do the design, implement MVPs, and code review while engineering management assumes the engineer has infinite time.

But for others and FAANG level companies, I assume the situation would be highly different. Do let me know in the comments.

*Originally published on [HackerNoon](https://hackernoon.com/how-a-clean-codebase-becomes-unmaintainable).*
