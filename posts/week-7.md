---
title: Choosing the Core Concept, Self-Development Through Avatar Progression
date: 2026-04-17
author: Andrea Yaretzi
summary: Reflection on why we moved away from our first ideas and committed to a self-development platform based on avatar progression.
tags:
  - 2. Concept Commitment
  - 3. Group Discovery
  - Functional Requirements
  - Design Decisions
---
## Moving away from our first ideas

Me and my teammate got toghether this week to put ideas toghether. We had really different topics and ideas, so after doing a idea shower, we saw there we where not agreeing on any implementation on any of both topics, so we decided to "break" those two ideas, and choose a new one. 

## Why self-development became stronger

We ended up finding a common topic we both where interested in, which was, self-development. While the other two topics were still interesting, self-development seemed to fit the BlaBla brief better because it creates repeated interaction, user participation and community support.

We also gave the project a clearer user need. Many people are interested in improving their habits, such as exercising, studying, reading or becoming more productive, but the difficult part is often maintaining consistency rather than starting.

This made the problem suitable for a community-based web application. Users would not only need a place to record goals, but also a system that makes progress feel visible and rewarding. A platform based only on posts or advice would not be enough, because the main problem is not lack of information, but lack of sustained motivation.

## Core feature: avatar progression

So the core feature we thought about after doing some research was a **personalized avatar that shows your performance and goals**. These was chosen after seeing in forums that people usually struggle more with consistency rather than starting their self-improvement journey. We also tried to see what an useful approach could be so that people wouldn't quit after starting, and we disvocered that a good way for people to mantain focus is creating an interactive experience for them, transform their goals in something more "tangible", something that they can keep track easily, not so much of an abstract thing, like some goals usually are, since results can't be seen until much later along the way.

Even though we did decide on this feature, we still have to find our scope, since there are some trade-offs that can be considered. An example would be that making the feature interactive will help engagement, but that could also affect performance if not done correctly. Also symplifying the progression stats can make it more accesible, but it risks ending up being oversimplified for all the characteristics a personal growth goals have.

## Initial functional priorities

After choosing this concept, we started separating the features that were essential from the ones that would only support the experience.

| Priority -> Requirement -> Reason
| Core -> Users must be able to create or select a personal avatar -> The avatar is the main representation of the user’s progress. 
| Core -> Users must be able to create goals, tasks or missions -> The system needs real-life actions to connect to avatar progression. 
| Core -> Users must be able to complete or miss missions -> This creates the feedback loop that updates stats, levels or health.
| Core -> The system must update avatar stats based on user actions -> Progress needs to be visible and connected to behaviour. 
| Supporting -> Users should be able to share achievements with the community -> Sharing can increase motivation and accountability, but the app should still work without it. 
| Optional -> Comments, reactions and extra community features -> These could improve interaction, but they also add moderation and implementation complexity. 

## Trade-offs and scope decisions

As discussed befor, but not in detail, an important trade-off was between making the avatar system engaging and keeping it simple enough for users to understand. A very complex RPG-style system could include many stats, formulas and rewards, but this probably would confuse users and go out of the scope for this app project. For this reason, we decided that the avatar should focus on clear stats and visible progress rather than complex game mechanics.

There is also a possible risk in making missed tasks reduce health or points. This could motivate some users, but it could also discourage others. For the prototype, this means feedback should be designed carefully so that the system feels supportive rather than punitive.

Another trade-off was between personal progress and community interaction. Community features can support motivation, but if the project focuses too much on the posts, comments and or reactions, the mission of the avatar could become less relevant, so we will treat the avatar and mission system as the core, while community sharing will become a supporting feature.


## Design methods used

The design toolkit methods used where: 
- Mind mapping to explore different initial ideas and connections.
- Reframing to shift our focus from cybersecurity and drones to self-development, since it showed a more engaging and relevant problem space. 
- User profiles and empathy mapping, so we could identify the key challenges such as lack of motivation and inconsistency. 
- Scenario-based thinking to visualise how users would interact with the avatar system, so we could map how real-life actions translate into in-app feedback.

## Reflection

By the end of this week, the project became clearer. The main requirement was no longer simply to create a community for self-development, but to design a feedback loop where users can create missions, complete actions and see their avatar progress.

This changed how we understood the application. The community aspect will still be valuable. However our main focus won't be there, but in the avatar-mission.