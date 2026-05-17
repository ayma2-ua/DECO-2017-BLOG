---
title: Turning the Avatar Concept into User Flows and Functional Requirements
date: 2026-04-24
author: Andrea Yaretzi
summary: How wireframes and user flow diagrams helped us define the main interactions, system behaviours and functional requirements of the prototype.
tags:
  - 4. Functionalities
  - Wireframes
  - User Flows
  - Scope
  - Design Decisions
---

## From concept to interaction

This week we focused on after choosing  creating the first wireframes for the application. Since we already agreed on the main concept (avatar progression as the core concept) and direction of the project, the next step was visualising how users would actually interact with the system, since at the moment the idea was still abstract (users would create missions, complete them and see their avatar improve). The wireframes and user flow diagrams helped us test whether this concept could become a clear interaction flow.

## Functional requirements identified

Before starting the wireframes themselves, we first decided which core functionalities the application would include. Since the main purpose of the project is helping users stay consistent with their self-development goals, we selected features that would support motivation, progression tracking and interaction in a simple but engaging way.

The functionalities are added in the Discussion, point "4.Functionalities".

## Key screens and why they matter

After deciding this, we also created a user flow diagram to understand how users would navigate through the application. Mapping the flow helped us see how each interaction connected to another, making it easier to identify the most important screens and actions users would need.

The first wireframe we created was the landing page. This page is the entry point of the app. From there, users can start the onboarding process through a “Get Started” button.

After that, we designed the sign up and sign in screens. These pages were kept intentionally minimal so users can access the app easily and quickly. Since the experience is meant to feel lightweight and motivational, we wanted the onboarding process to feel easy and accessible.

Another important wireframe was the avatar selection page. One of the main features of the app is the personalised avatar system, so users will be able to choose a character that represents them during their progression journey. Even at this early stage, we know that in the near future that we want avatars to feel expressive and visually tied to the gamified aspect of the project.

We also worked on the home feed structure where users can upload and view posts. This section is meant to encourage interaction and allow users to share progress, even though it is not the main purpose of this project. But we would still like to be able to add posts created from the accomplished achievments through the avatar, to keep motivation high.

The most important wireframe we created is the avatar progression page. This screen contains the user avatar together with multiple progression stats such as intelligence, strength, agility or productivity. These can vary depending on your goal. Alongside these stats, users can see their current tasks and goals, creating a more visual representation of their personal growth.

Connected to this screen, we also designed the “Add Challenge” interface. Here users can create tasks, assign descriptions, select specific weekdays and add progression points depending on the difficulty or importance of the challenge. We wanted this interaction to feel dynamic while still remaining easy to understand.

While working on these wireframes, we started noticing how the different components of the application related to each other. Even though we were still focused on the visual structure, this stage helped us begin thinking about the data and relationships that would later become part of the database design.

## What the flows revealed

As part of this stage, we also created user flow diagrams that maped how users would move through the different interactions of the app. The visualization was made easier after seeing these diagrams, and also to think about the decisions users would have to choose between and the responses of the system. For example, we mapped the login flow, avatar creation, adding a new mission, and sharing avatar progress. This made it easier to identify where validation, feedback messages, redirects and data storage would be needed.
Instead of only designing screens, we began thinking about what each screen needed to do, what data it required, and how the system should respond when something was completed, missing or invalid. Refer to discussion 4.Functional Requirements, to check out the different diagram flows made (login, avatar creaion, share your avatar status, mission completed and creation of new mission)

Overall, I believe creating the wireframes and user flow diagram has helped us to better visualize our abstract ideas and turn them into something much more tangible. 

## Scope decisions and trade-offs

One scope decision was to keep onboarding simple. We could have asked users to define all their goals, preferred stats and routine types during sign up, but this would make the first interaction longer. For the prototype, it made more sense to let users reach the avatar experience quickly and customise their progress later by adding missions.

Another trade-off was between personal tracking and community interaction. The community feed can support motivation, but too many social features could distract from the main avatar-mission loop. For this reason, the feed was treated as a supporting feature, while avatar progression and challenge creation became the core flow.

We also had to consider clarity. If users do not understand how completing a mission affects their avatar, the motivational value of the system is reduced. This means the interface needs clear feedback after important actions, especially when a mission is created, completed or missed.