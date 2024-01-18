---
layout: post
title: The X-Y Problem when interacting with a product team
date: 2024-01-18 12:01 +0000
tags: problem solving communication product engineering team collaboration
categories: process
---

## The X-Y Problem

The X-Y Problem is a communication problem where you have a problem X, and you think you know the solution Y, but you don't. 
You ask for help with Y, and people try to help you with Y, but you're still stuck with X. This is better explained here: https://xyproblem.info/

## How this applies to interactions between engineering and product teams

When product comes with an idea/problem, it's common that they already have a solution in mind. So we start discussing the solution, and we start thinking about how to implement it.

We may know this part of the problem, but we don't know the whole problem. We don't know the whole context, the constraints, the trade-offs, the impact, the alternatives, etc. So we may assume that the product team made this diligence before bringing the solution forward.

## How to avoid this

When product comes with a solution, don't assume that they did the diligence. Ask questions to broaden the understanding of the problem. Ask questions like:

* What did users say to lead to this solution?
* How do you see this solution growing in the future?
* What related features were requested?
* What are the constraints of this solution? Could it handle 10x the current load? Is PII involved?
* How extensible is this solution? How easy would it be to add a new feature?
* Do we expect any data migration in case we need to make this more robust?


## What to do if the solution is not a long-term solution?

* Write down the problem and the proposed solution
* Explore other alternative solutions during the development phase
* If you find a better solution, discuss it with the product team
* If you can't find a better solution within the constraints think of solutions without those constraints
* In case you find a better solution by removing the development cost constraint add it as a technical debt item for a later stage
* If the solution works for long enough (depending on the feature itself), don't forget to clean up these technical debt items later on, most of these forgotten items are probably not going to be developed or needed anymore

