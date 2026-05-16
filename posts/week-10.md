---
title: "From Concept to Database: Designing an ERD and Transforming It into a Relational Database" 
date: 2026-05-08
author: Andrea Yaretzi
summary: 
tags:
  - Programming
---
This week we focused on transforming our previous design work into the real application, start coding. Until now, most of the project had been based on research, wireframes, user flows, ERD diagrams and database planning. During this stage, we started turning those ideas into working features, including authentication, posts, uploads, avatar progression, personal tasks, admin permissions and testing.

Instead of only thinking about how the app should work, we implemented the logic behind the interactions. The app now uses mojo.js as the web framework, SQLite for the database, templates for the views, models for the data structure and controllers to manage user actions.

One of the things we started off at was the authentication system. Users can register and log in using their username or email and password. We also kept a demo profile option so the app can be tested more easily. This helped us move through the different flows faster during development without having to manually create a new user each time.

This demo profiles where created as admin users. Admin permissions allow you to edit and delete anyone's post. For regular user, they can create posts, edit their own posts and delete only their own posts, and same goes for the tasks. This way the system now checked not only if someone is logged in, but also if they are allowed to perform a specific action.

Another important improvement was the feed. Users can now create posts with text, images, or both. During testing, we discovered that the system initially assumed every post included a file upload. Because of this, text-only posts could fail. We fixed this by updating the backend so it checks whether the request actually contains multipart data before trying to process uploaded files. This made the post creation flow more reliable.

After creating all this flow work it was time to test it. While at it, we discovered an issue in the post creation flow. The system initially assumed that every post submission included a file upload, which caused the `/posts` controller to fail when a user attempted to create a text-only posts. Since the request was not multipart, the backend still attempted to parse uploaded files, resulting in a 500 error from the server.

To solve this, we updated the controller logic to handle better the posts without neeiding an attached files. The system now checks whether the request contains multipart data before attempting file processing, allowing users to create both text-only and media posts reliably.

Different issues like the one shown above where found thanks to the usability and flow tests we did. This helped us validate all our work.

This also reinforced the importance of defensive programming and validating assumptions about user input during backend development.

After implementing new features and tests, we also performed linting and code quality checks to ensure the new changes followed consistent coding standards and did not introduce avoidable issues. This helped maintain a cleaner and more maintainable codebase while development became more complex.