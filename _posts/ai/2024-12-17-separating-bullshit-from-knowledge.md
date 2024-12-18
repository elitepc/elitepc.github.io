---
layout: post
title: Separating bullshit from knowledge in the context of people using LLMs
date: 2024-12-17 12:01 +0000
tags: snake oil bullshit agile models openai LLMs agents scripts rules tips
categories: ai
---

It's no big news that in the past 1 or 2 years many people seem very eager to adopt this new technology. 
LLMs are here to stay and revolutionize everything, so much so that some people want to use it for everything.

## My experience

My first contact with transformer-based architectures was in 2021 while researching techniques to identify patterns for a cybersecurity master thesis. Tried CNNs, RNNs and LSTMs and when I got to transformers, I was pretty impressed with the results. 
Although not that useful in my current context seeing that we could generate coherent text after a few training rounds was pretty nice.

A year later I started using LLMs, GPT-3, 2k token context for simple text features. Since then, we've expanded out usage of these tools to other areas of the product.

## The experiences that triggered this post

Although they are pretty impressive tools, they are still only tools. In this case, the only tool some people know how to work with. A few months ago I started seeing stuff like:

- People advocating to use it to retrieve personal information from other people, where wrong information was getting generated (insert surprise pikachu meme)
- Others advocating to use logic inside the prompts with "if else" statements instead of properly feeding the prompt with deterministic information
- Others just throwing, what I imagine to be confidential information into it expecting it to analyze data
- Others using it to end arguments "oh yeah? You think you know how to do this, lets see of chatgpt agrees" - "oh, it didn't, you must be wrong"
- Others saying that AI agents are infinitely better than scripts because they do what scripts can't, not even realizing that that's just an abstraction

More recently the craziness of trying to show that these systems can be created with 100% precisions and 100% recall in a small sample and making it the benchmark for engineering to implement and judge against.

We're talking about critical pieces of information or steps in infrastructure now dependent on the mood of an external model.

## What I've learned with this

What I'm getting with this experience is that the same experience I had at web summit, where non-technical people are making big assertions on tech topics, is leaking into the inside of companies.

I also learned that at an individual level, it looks like some people, for the first time in a while, feel more powerful. They can get the results without putting in the work (e.g. programming complex things without learning how to program).

From my observations social media is also affecting a lot of these decisions. Echo chambers of AI propagated by the people who benefit from the usage of AI directly or indirectly, mainly on linkedin leading everyone else to believe that that's the only true solution. A kind of misinformation that's on par with tiktok videos.


## Some personal rules of thumb

- Understand the goal, if you aim to provide accurate data, aim for at least some RAG system with accurate information, it all depends on your tolerance levels
- Understand who is asking for adoption. If it's the CEO, maybe sales or funding are more important than actual reliability, if it's product maybe the WOW factor is more important. Try to understand why they are asking for this type of technology in the first place and what would happen if you delivered something with the same kind of results but without the word AI in it
- Be on the lookout for anyone that promises 100% correctness based on technology that's not designed to be 100% accurate. Make it clear to everyone and document it that those numbers are most likely irrealistic if we don't want an infinite running project
- Make sure the people asking or implementing these systems understand the edge cases of the problem
- When getting advice on the topic, or even asked to implement it, try to assess where they fit into the Dunning–Kruger scale, just like a junior telling you to use MongoDB because it's webscale
- Management may push for more AI because there's a good incentive to do so, do more things, faster, with higher reliability, or so we've been sold on - similar to "I want the body without the gym", "I want the money without the work"
- Make sure that the ones defining the architecture will suffer the consequences (good or bad) of their decisions, otherwise there's no incentive of making it right
- If product requests specific performance targets that they have data to back it up, always measure against that data



With that said, I'm leaning more towards letting people learn on their own. Let people bang their heads on the wall, that's the way some people learn. I can offer advice and guidance, but I can't make anyone follow it. If we think of a circle model (7 habits of highly effective people) where the outer layer is a circle of concern, then an inner layer of a circle of influence and another one inside that one as a circle of control, the goal is to make the circle of concern as small as possible. If we're not that into politics, we may not even need to grow the circle of influence to the size of the company, even at a startup. 
