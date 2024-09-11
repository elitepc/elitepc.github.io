---
layout: post
title: No estimates - A year later
date: 2024-09-11 18:01 +0000
tags: no estimates time management product story points scrum agile lean burnout startup Allen Holub
categories: process
---

At Building Radar (small startup) we've subscribed to #noestimates for over a year now. I'd say we've been pretty successful so far.

## How it worked before

Before we already used to just divide tasks into 2 categories. 1 SP = 2 days or less, 2 SP = 5 days. This was already cutting a lot of time
out of estimations and refinement sessions, however it had its downsides. We always kept tasks shorter or equal to 1 week of work. We still try to do this today. We believe in short iterations and course correcting instead of very careful planning spanned across months.

We used to work in sprints, meaning that if we had 5 available developers for 2 weeks, 20 SP or more were expected. (it's worth noting that we tried just decreasing the amount of SP expected per sprint, similar to counting with 70% of development time, but still it didn't work well for us)

We also had another constraint of BE and FE people being entirely separated as skill sets, which makes hard to "share" story points.

## Why we changed this

- if a task is 1 SP, and it has been more than 2 days, it would raise red flags. And although there was no real repercussion, seeing that we work with a very motivated team, that led to developers always pushing themselves over the limit, leading to extreme exhaustion
- if a task is 15 minutes, then what can we do with the rest of the time? we shouldn't plan more than 20 SP per sprint (we usually just pulled another one)
- the story points don't account for other time hogs, usual ceremonies, unexpected meetings, unexpected investigations, tasks needing more collaboration than expected
- indecisions on what would happen with a task that was both BE and FE and would take 3 days each? 1 task for 2 SP? 2 tasks for 2 SP, but we kind of knew that it wouldn't fully fill in the 4 total SP? How do we account for integration time of the 2 tasks if one of them gets cut out off the sprint?
- time spent trying to estimate better was a pointless exercise. We'd beat ourselves down in retros for estimating badly. In retrospect, basically saying that we didn't know how much time it would take to do something we didn't know the exact scope of. Doesn't sound very logical, but the feelings were real
- the decision was always looming, it's Thursday afternoon, this is not near completion, should I sacrifice personal time? Tests? Code quality? Edge cases? Sprint goals? Meetings? Colleagues asking for help? Other responsibilities?
- PR reviews would extend the time for delivery and were another source of invisible work, especially PR reviews from a previous sprint
- imagine there's a 1 SP gap, so we search for a task that's pointed as 1 SP, even if it's item #20 on the backlog and probably should have never been picked up

Summing it up:

We didn't know how much something would take unless we started investigating, estimating sometimes would take the same amount of just doing the work.
We prioritized meaningless tasks just because there was capacity in the "sprint". There was a lot of invisible work, that we'd deliver on and then felt bad for not delivering on time on sprint promises.

## How it is right now

We go into refinement sessions, let the product team know that we could split up tasks in smaller iterations or not, point everything with 1 point. 
The top of the backlog is always what gets picked up, no one cares if it was just reshuffled as long as the next item is refined. 
We understand that scope changes and setbacks happen, and we're more open to extending tasks that need more time instead of compromising on everything else. 

## Tricks to get it working in an healthy manner

- Make sure everyone is onboard, otherwise requests for time estimates still come
- Make sure the product team can manage expectations in a way that says "for 2 months we'll be working on this topic + 3 other topics" instead of specifying the exact tasks
- You can still analyze velocity, just try to keep tasks as small as possible (MVP, always) and point them as 1 SP
- Feel free to leave some work prepared for future work that you know is coming. Future thinking is future garbage, but migrating databases 10x per week also sucks
- Be on the lookout for blockers. A task taking too long is still a red flag, check if you can unblock your teammates
- Make sure invisible work is kept to a minimum. Being by creating more subtasks, communicating on stand-ups or whatever works for you, just make sure people don't think you're not working, otherwise there's a mismatch in perception and reality and tensions can be created where they aren't needed
- Make sure you have a healthy backlog, it's easy to fall into the trap of refining 10 tickets that are 30 minutes each and no one noticed and in no time the backlog can run dry

Mandatory watch from Allen Holub [[https://www.youtube.com/watch?v=QVBlnCTu9Ms](https://www.youtube.com/watch?v=QVBlnCTu9Ms)]
