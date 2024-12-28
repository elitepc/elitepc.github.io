---
layout: post
title: P/PC Balance in software engineering
date: 2024-12-17 12:01 +0000
tags: books balance habits software engineering
categories: process
---

When re-reading the book 7 Habits of Highly Effective People describing this Production (P) vs Production Capability (PC) balance it made me think of if in the context of Software Engineering.

## The principle

This principle comes from the fable of the goose and the golden egg. A farmer after seeing that a goose would produce golden eggs every day decided to kill it to get them all at once.

Although this is a fictional story we can understand that the end result was not more Production (P) because the Production Capability (PC) was killed.

## How this applies to software engineering

As software engineers we have to constantly balance correctness, reliability, delivery time, security and many more variables.

In specific on thing that we need to look out for is "does this action makes subsequent changes easier or harder"?

### Types of changes and their consequences

Making subsequent changes easier or harder depends a lot on the current, predicted and future contexts, but we can go through some scenarios:

- We have a monolith and need to test a new concept in the api:
  - We add a lambda function in AWS to take care of that
    - PC impact: expected to be moved to a more solid system later (tech debt)
    - PC impact: hard to discover that that code exists if there's no easy discoverability, which can slow down future developments (unexpected changes as that code could have low discoverability) 
    - P impact: very fast deliver of value, error-prone
  - We add proper code to the monolith
    - PC impact: tested, predictable implementation easy to make changes to understanding the consequences of it in other places of the app
    - PC impact: small increase in CI running times
    - P impact: slower deliver of value, not much error-prone
- We want to process a csv:
  - We can process it with a LLM
    - PC impact: non-deterministic behavior will be hard to debug and may be impossible to get right (infinite time spent bug fixing)
    - PC impact: hard to build on top of if the output is not as predictable as developers assume it to be
    - P impact: very fast deliver of value, error-prone
  - We can process it with a library and some code or other services that do that
    - PC impact: deterministic reliable code
    - P impact: slower deliver of value, not much error-prone

### How to make the trade-off
  
What's best in each scenario totally depends on the company, stage, resources, customers, and so on there's no single truth. However here are some rules of thumb I can think of from experience:

- Decide if this implementation seems to be core to the business/product
  - If this is core the tolerance for sacrificing PC in order for immediate P should be very low
  - If this isn't core, PC may not be very important yet
- Be attentive to who is trying to apply pressure for each approach
- Make sure the ones choosing to sacrifice PC will suffer the consequences of the decision (e.g. product pressuring this would need a follow-up task created to clean it up; an engineer leaving the company soon should have less impact on the decision then the ones staying)
- Make sure it's known that the sacrifice in PC is being made
- Make sure to translate PC into P in the future. Taking more P now, means spending more later to get the same P, or having less P later -> translate this into business terms for higher management if needed
- Try to isolate PC trade-offs, as in don't make the whole project dependent on a hack, make the hack on the side if needed, so it only compromises the new part and not the whole system 
- Don't compromise on things you're certain would bring the project to a halt, if you care about the company, you can let people shoot themselves a bit on the foot if they really want to (giving the benefit of the doubt) but do not let them shoot themselves in the heart


As a footnote, make sure you really understand the stage of the company you're in. A startup is not expected to invest fully in PC as it may not have enough P to exist for too long. Just make sure the decision is conscious.
