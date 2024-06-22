---
layout: post
title: Prompt Engineering Concerns
date: 2024-06-22 12:01 +0000
tags: prompt engineering product management owner programming snake oil bullshit agile models openai LLMs
categories: ai
---

At this stage it's hard to understand how to best work around prompt engineering. But first lets start with a definition.

## What is prompt engineering?

Prompt engineering is the process of improving results from a model by changing the prompts used to query it, mainly in the context of large language models.

## What I've seen so far

For context, I've been integrating with GPT for almost 2 years now, focused in fast releases and prod monitoring. 
I've also experimented with a lot of smaller models, different providers and so on, but not really for production use.

In my experience, when building features that integrate with LLMs a very bad prompt can totally kill the feature. 

However, from an "ok" prompt to a "good" prompt, the difference in results can be insignificant. In a specific feature I was working on, the process of having 4 prompts and choosing the best one with experts in the loop yielded a 6% improvement in quality.

What I've learned from that experience and from other similar feature implementations also is that the process of 
prompt engineering is very time-consuming coming to a point where it's no longer worth the effort very quickly.

But that's only the case for big efficient models. Definitely not the case of 7B models for example.

## Community opinions on prompt engineering in general

What I've noticed is that the software engineering community is very reluctant to accept the term "prompt engineering" as a valid engineering practice.

As soon as you mention "prompt engineering" it's as if you're immediately labeled as a "non-engineer" or "non-scientist", definitely not a "real" engineer nor with any background in AI.

List of things I've heard engineers say about prompt engineering:

- There's no science behind it
- I wouldn't call myself an IDE engineer, why should I call myself a prompt engineer?
- It's a misappropriation of the term "engineering"
- It's too specific to be a role
- That's just something you learn on the side
- The models should understand the prompts, not the other way around
- Anyone who uses the term "prompt engineering" has no clue how LLMs work
- It's all snake oil


On the other hand, in the Product Management community what I hear most is:

- Democratization of AI through prompt engineering
- Prompt engineering is really helpful to get meaningful user value out of the features
- PMs can iterate on prompts much faster than engineers can iterate on models


So from this what I can gather is that software engineers tend to discard the idea, while product managers tend to embrace it.

## My take on prompt engineering

Although the name makes it sound more important than it actually is, there's actually a practice that needs to be done when working with LLMs.
Weather we call it prompt engineering or not, it doesn't really matter.

It's very clear that most engineers haven't had the chance to integrate LLMs in their current products, hence never had to deal with prompt engineering.

It's also very clear that most product managers have the tendency to think that a new "fad" is going to solve all their problems.

I'm more in the middle. If you can work with big models, maybe spending more than a day on prompt engineering for most use cases is probably overkill.
For smaller models, it's probably worth the effort, but tha really has to justify the cost.

The approach I'd recommend would be based in agile. Start with a "good enough" prompt. Release it. Gather feedback. Iterate if needed.
