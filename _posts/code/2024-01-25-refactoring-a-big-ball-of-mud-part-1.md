---
layout: post
title: Refactoring a big ball of mud - Part 1
date: 2024-01-25 12:01 +0000
tags: refactoring tech debt codebase engineering cleaning buy-in communication risk
categories: code
---

Coming from a PHP background, I'm no stranger to big refactorings, very old tech debt, replacing solutions made by people that see programming as a hobby and not an engineering discipline.

This time it's a bit different, the codebase is 9 years old, made mostly by people that knew what they were doing, however, the problems they were solving changed very rapidly overtime and this was just the result of adding solutions on top of solutions without considering the big picture.

This was not a fault of engineers, and I'd actually say that this was the best approach, the company needed to survive and in order to do that they needed to ship different things fast in an unsustainable way hoping that the time would come where they could refactor. With a pivot in the business mid-way, this became even more of an issue.

Shortly after I was hired, we had one of the main engineers leaving the company, and then the rest, one by one also left. In a span of about 5 months I was the oldest Backend Engineer in the company.

Here are some tips that helped me refactor this big ball of mud.

## 1. Don't panic

The first step is understanding that if things are running, you don't have to understand every part of the system to make changes.

You don't have to make a plan for a big refactor. A high-level plan is enough, no need for too much detail.

## 2. Understand the big picture

* What are the core business domains?
* How do people use internal tools?
* What are the main flows?
* Are there unused services?

## 3. Start with the easiest things to get the ball rolling

Like cleaning up the house, it's easier to clean if the clutter is gone. Start by removing these unused services.

Don't go too deep into the rabbit hole, don't try to go too deep into the code right away, otherwise it's an infinite task of removing unused code.

## 4. Deploy frequently

Make sure you don't accumulate changes for too long, otherwise you'll have a hard time getting feedback

## 5. Define the goal and milestones

In my case we had multiple goals and milestones:

* Resolve the three-legged problem, multiple services accessing the same databases
* Remove redundant systems
* Remove old unmaintained vms
* Remove no longer used features and big business requirements
* Regain ownership of the code
* Elevate the codebase to new standards, allowing for continuous delivery

## 6. Communicate

Make sure you understand why you need each milestone. If you can't explain it properly or can't find a reason other than "it's old", it's probably not worth doing it. For example in this case:

### 6.1. Resolve the three-legged problem

We had multiple services that were last touched before I joined the company, making changes to databases that I now needed to change because they affected current expected tasks.
If I did a breaking change in the schema, these services would probably break, and to me, these were unknown systems. Not unknowable because we can always learn new stuff, but if a change in a current task requires me to understand 10 different systems and 6 different storage systems, it's probably not worth it.

Making each service responsible for its own data would allow us to make changes without worrying about breaking other systems. Effectively unlocking the product team to suggest changes to every part of the system without turning a "change the color of a button" story into a 3 months' task.

### 6.2. Remove redundant systems

We had at least 3 different systems trying to insert the same data in the database depending on some events. We had multiple internal tools to manage the product.
There's no need to hinder the performance of colleagues by making them use different systems in a single flow if not even engineering wants it that way.

This would reduce the amount of projects to maintain, no more discussions on what should live where, no more discussions on what should be the source of truth.

### 6.3. Remove old unmaintained vms

Unmaintained vms are a security risk and a product reliability risk. If we don't know what's running there, we don't know what's going to break if we change something else.
In our case, we had these vms to powering internal tools with local databases and some services that were dependencies of main product services.

Making sure we moved this to a better environment would reduce day-to-day risks and improve developer experience.

### 6.4. Remove no longer used features and big business requirements

The codebase, if not cleaned up will have a history of all business decisions that were made. We went through a pricing model change, which means that a lot of business requirements no longer make sense.

This is a quick way to reduce the amount of code that needs to be maintained and the amount of code that needs to be understood in later steps.

### 6.5. Regain ownership of the code

If something breaks you want someone to take care of it. If no-one feels responsible for it, you may have firefighters, but you won't have people thinking about it in the long term.

Reduce the risk of code rot by making sure that someone is responsible for each part of the codebase.

### 6.6. Elevate the codebase to new standards, allowing for continuous delivery

If you already apply continuous delivery practices in your day-to-day, elevating the whole codebase to this standard will probably allow you to move faster and with less risk.

If this is not done you'll always have parts of your codebase that you're afraid to touch, hindering the scope of product decisions.


## 7. Get buy-in

**IMPORTANT: Before going further make sure you have enough influence proportional to the changes you want to make. There are few things more annoying than having a new colleague wanting to redo everything because they don't understand it and without proving themselves first.**

Get buy-in from everyone that you need. Manager, Product, the rest of Engineering. Use whatever is available to you to make this happen.
Confluence docs, notion docs, loom videos, Jira tickets, whatever works for you and your team.

Remember that different people will have different concerns and visibility. Here's what worked for me:

* Manager: Confluence docs and Jira tickets
  * Make it clear that there was no ownership
  * Good practices could not be done across the board due to these problems
  * If something broke, the time to recovery could be too long
  * Make it clear that observability was not good enough
* Product: Confluence and notion docs
  * Make it clear that there are parts of the system that, if touched, the time for impact would be too long
  * Make it clear that the product can break at any time in some areas
  * Make it clear that the users' perception could be affected by this
  * Make it clear that, when defining new requirements, product has to think and be able to respond to all old business requirements
* Managing Directors, CRO, etc: Loom videos, 1on1s - Be in-sync with your manager, he does most of the heavy lifting here
  * Make it clear that this impacts product development speed
  * Make it clear that this is a business risk
  * Make it clear that company goals could be affected by this
* Engineering: Confluence docs
  * Make it clear that this will help us with dev experience

## 8. Make it happen - General tips

* Identify and ask for help from whoever you need. In my case, Data, Platform, Frontend
* Use old docs to help you out. Even if they're outdated, they'll give you a good starting point of how people thought at that point
* Make sure that before an internal system is decommissioned no-one uses it (audit logs can help)
* Implement observability, you must be able to understand what breaks where and when, specially when transferring between systems
* Aim for fewer systems, less code, less complexity
* Make sure everyone that you need help from understands the big picture or at least how their role fits in the big picture

(To be continued)
