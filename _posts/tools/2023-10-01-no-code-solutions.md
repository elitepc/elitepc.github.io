---
layout: post
title: No-code solutions - the art of programing in production
date: 2023-10-01 11:01 +0000
tags: tools integrations no-code programming software engineering product maintenance processes prototyping
categories: tools
---

For years, the dream of creating software without delving into the intricacies of programming has tantalized many. Even in my younger days, tools like Dreamweaver and Microsoft FrontPage allowed me to craft complex websites without mastering code. Back then, it felt like a superpower – I could bring my ideas to life without wrestling with lines of text.

However, as I honed my programming skills, I found myself shunning these tools, driven partly by ego. Writing code became a badge of honor; using auto-generating tools seemed beneath a "real" developer. 

With that said, as my understanding deepened, I realized the true challenge lay not just in building software but in maintaining it over time. Nicholas Gallagher's statement, "Can you maintain this without losing your minds?" resonated profoundly.

In recent years, I explored platforms like OutSystems, Unreal Blueprints, Retool, Make.com, and Zapier. When used judiciously, these tools proved invaluable, accelerating the product development process. Yet, they come with caveats.

## Challenges of No-code Platforms

The allure of rapid development in no code platforms is undeniable. However, comparing this ease with traditional programming reveals its shortcomings. Consider the process of implementing a code change versus a change in a no-code platform:

### Code Change in a Repository:

1. Write the code.
1. Write a commit.
1. Let CI ensure code functionality and styling.
1. Undergo code review (optional).
1. Deploy to a production-like environment.
1. Run smoke tests.
1. Deploy.
   
### Change in a No-Code Application:

1. Make the change.
1. Deploy.

This streamlined process significantly expedites moving from concept to production. Yet, as the application grows in complexity, pitfalls emerge. No-code platforms can't escape issues like unintelligible code consequences, rudimentary version control, and challenging code reviews.

## Drawbacks and Considerations

No-code platforms, despite their advantages, pose several challenges:

- Complexity Conundrum: As sections of the program grow intricate, understanding the implications of changes becomes daunting – akin to deciphering lengthy functions.
- Tool Selection Ambiguity: Non-engineering teams might not always choose the optimal tool, akin to an intern making unreviewed production changes.
- Code Reusability Struggles: Reusing code in these platforms is challenging, reminiscent of building microservices for every new application requirement.
- Integration Hassles: Integration within CI pipelines becomes complex, akin to testing a blackbox with external influences affecting results.
- Versioning Woes: Reliable code versioning is absent, leading to haphazard change tracking.
- Code Review Nightmares: Code reviews become labyrinthine, akin to comparing intricate game differences block by block.

## Navigating the Terrain: Tips and Solutions

While confronting these challenges, strategies emerge for different use cases:

### 1. General Usage:

- Consider Consequences: Evaluate the impact of potential breakdowns; bolster robustness or avoid these tools if disruptions are costly.
- Implement Oversight: Introduce a process reviewer to prevent direct publishing to production.
- Simplicity Triumphs: Keep scenarios as straightforward as possible; complexity hampers adaptability.
- Error Management: Direct errors to an error platform, preventing inbox inundation.
- Prune Unused Scenarios: Archive scenarios no longer in use to maintain clarity.

### 2. Internal Processes:

- User Familiarity: For small groups, ensure users comprehend and contribute to changes.
- Database Integrity: Restrict direct changes in production databases; replace them with integrations with in-house apps.
- Data Source Limitation: Limit accessible data sources to prevent misuse.
- Mindful Integrations: Avoid spamming by integrating tools like Slack judiciously; beware of infinite loops and so on.

### 3. Prototyping for Demos:

- Clear Communication: Emphasize that prototypes aren't production-ready; they're placeholders for future, robust versions.
- User Testing: Have someone apart from the "developer" test the prototype before presentation.
- Iterative Approach: Replace prototypes with simpler, sturdy versions as ideas solidify.

### 4. Integrations:

- Unified Interface: Create a singular interface connecting to the no-code platform.
- Code Complexity Management: Retain intricate logic in your code, sending simplified data to the no-code platform.
- Custom Integrations: Keep integrations simple, especially for tools like CRMs, to ease maintenance.

### 5. Adding Functionality:

Be Cautious: Only experiment with non-critical features destined for replacement; If this debt is not paid it often leads to employee frustration and turnover.


## TL;DR:
- Maintainability is hard when you don't know the consequences of your actions
- Use the best tool for the job, not the only one you know
- Do not let product teams override an engineering decision
- There's no good solution to keep them as stable as traditional programming
