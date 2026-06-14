---
title: "A3 Reflection" 
date: 2026-06-10
author: Andrea Yaretzi
summary: A final reflection on the performance, accessibility, user experience and functional requirements of the completed prototype
tags:
  - Evaluation
  - Performance
  - Accessibility
  - User Testing
  - Reflection
  - Functional Requirements
---

After many weeks moving from initial ideas to wireframes, database design and implementation, we arrived to the final stage of this project, so we started to do the evaluation of what we had actually built. On this final post we have to evaluate if the decisions we took worked in real life, what the application does reliably, if there are any struggles, and what we would change if development continued.

The application was evaluated in the local environment required for this project and can be run through npm run dev. It was not publicly hosted since it was not part of the project requirements. This means that areas such as production hosting conditions, large numbers of simultaneous users, HTTPS configuration and external network latency where not evaluated.

# Evaluation of performance and technical behaviour

To evaluate performance, we used Lighthouse. The results were:

Category	Score
Performance 	76
Accessibility	95
Best Practices	100
SEO	            90

The performance score was 76. We had many results that showed a positive result: First Contentful Paint and Speed Index were both 1.5 seconds, Total Blocking Time was 0 milliseconds and Cumulative Layout Shift was 0. So our page content was reasonably quickly, did not block the main thread for a noticeable amount of time, and remained visually stable while loading.

However, the Largest Contentful Paint was 3.2 seconds, which was slightly slower than the three-second maximum performance target recommended in the brief. The main cause was the avatar images. The image was approximately 678 KB and had dimensions of 1254 by 1254 pixels, even though we displayed it at around 176 by 176 pixels. This means the browser downloaded much more image data than was actually required.

So here we encountered our first hurdle, which showed a direct relationship between a visual design decision and technical performance. Adding more avatar options improved personalization, but the new images were not sufficiently compressed so they took too much time and downloaded too much data. With more time, an improvement would be to convert these images to WebP or AVIF, resize them to match their displayed dimensions and use responsive image sources where needed.

Lighthouse also identified missing cache lifetimes, render-blocking CSS and unused CSS rules. The stylesheet is still relatively small, and even so, some rules are shared across pages but are not required during the first render. A future improvement would be to minify the CSS, remove unused rules and separate critical styles from less important page-specific styles.


We also checked automated integration and model testing on this evaluation. The final test suite passed 158 out of 158 assertions, and the linting process was completed without errors. The tests did not only confirm existing behaviour; they helped us discover real implementation problems.

For example, a test for creating a text-only post initially returned a 500 Internal Server Error at the beginning. The post controller assumed that every request contained an uploaded file and attempted to parse multipart data even when the post contained only text. After identifying the error, we changed the controller so it first checks whether the request is multipart. After that the system can now create both text-only posts and posts containing images.

Testing also revealed weaknesses in the upload system. The form used accept="image/*", but this only guided the browser and did not give a warning or error when another file type was uploaded. For this we added server-side validation for safe file names, extensions, MIME types and a maximum size of 5 MB. The system now also removes partial files if an upload fails. Integration tests confirmed that the feed rejects a .txt upload with a 400 response while accepting valid images.


The external quotes API was also implemented with a local fallback. If DummyJSON is temporarily unavailable or returns an invalid response, the feed displays a predefined quote instead of failing. That way reliability is not affected of the main application.

# Evaluation of user experience and accessibility

We asked two classmates to test the application. The first participant was initially unsure what the platform was, since we didn't give her a detailed explanation before she started. We did this to try and avoid hiding possible unknown interface problems, so this confusion was useful evidence rather than simply a testing mistake. It let us know that the landing page did not explain well enough the purpose of the page. A new user should be able to understand that they create missions, complete them and improve their avatar without depending on a verbal explanation from us. So with this information, in a future version we should change our introductory sentence for another one that is more clear or a short visual example showing the connection between a real-life task and the avatar stat it improves.

The same participant asked for avatar options she could personalise. At that point, the application only used Pebble as the available avatar. We responded to this by adding more characters that users can select (at the moment we have 3). She also said that she liked the general visual style of the platform, suggesting that the colours and playful design matched the gamified style we where looking for.

The second participant was given a bit more of context of the application. She was able to create posts and tasks without assistance. This showed that the main interaction flows were understandable once the purpose of the platform was known. However, she wanted the avatar to feel more interactive. Her suggestions was including items that could only be unclocked with points gained by completing the tasks, adding animations and making progression produce more visible rewards. At the moment, progression is visible through points, stats and levels, but the avatar itself is static. The system works functionally, although the emotional reward could be stronger for what we saw on this user test experiences.

She also suggested two-step authentication. This would be valuable in a production service, but at the moment we where only deploying locally. So, this feedback was concluded as a possible long-term security improvement.


We also considered accessibility. We used the WCAG Accessibility and Testing guide as our evaluation framework. Following its recommendation to combine automated and manual testing, we used Lighthouse, navigated the main interactions using only the keyboard, tested forms and navigation with Windows Narrator, and manually reviewed focus indicators, labels and colour contrast. We also applied the POUR principles to consider whether the prototype was perceivable, operable, understandable and robust.

The main interaction flows could be completed without a mouse, the tab order followed the visual structure of the interface, and Narrator communicated the controls and form labels correctly. However, Lighthouse identified insufficient contrast on the primary button, showing that the prototype still requires a small visual adjustment before we can confidently claim full WCAG AA compliance.

During development, we also improved error messages using role="alert" and aria-live="polite", so when a login or registration error appeared, a screen reader could announced it instead of relying only on visual text. We also improved the custom file selector. Although the real file input is visually hidden, the visible “Add visual” control now shows a focus indicator through :focus-within when it receives keyboard focus.

Lighthouse gave accessibility a score of 95, so we can be sure that buttons and form controls had accessible names, inputs had labels, the page included a language attribute, headings followed a logical order, and a main landmark and focusable skip link were present. What we saw was insufficient was the contrast on the primary button. This should be corrected by adjusting the background colour and retesting the contrast against WCAG AA requirements.

The application does not depend on audio to communicate important information, so users with hearing difficulties can access the same tasks, stats, posts and feedback visually.

# Critical reflection and improvement planning

One of the main lessons that we take from this project was that working functionality is not the same as a complete user experience. For me, I am more used to only seeing the technical challenges behing a webpage. The application shows my technical knowledge of this in many parts; it can store users and avatars, and is also possible to create tasks, stats, posts, comments and upload images. However, I had to learn to also focus on user testing, where I saw that all this elements mean nothing, if you can't communicate it clearly.

On another note, the strongest part of our project is the connection between tasks and avatar progression. It creates a clear feedback loop and gives the community a more specific purpose than simply sharing self-development posts. It helps users to stay motivated. 

Talking about the technical structure, it also became more strong thanks to the model separation, the integration testing and server-side validation.

At the same time, some problems came from assumptions made during implementation. We assumed that users would immediately understand the avatar concept, or that posts would would always include images and that browser upload restrictions were enough. Thanks to all the testing, we where able to spot this incomplete parts, and work torwards its improvement.

For the improvements that would need attention sooner, I would prioritise compressing the avatar images, clarifying the onboarding and making avatar rewards more visible through simple unlockable items or animations. I would also complete the missed-mission behaviour, but in a supportive way. Instead of heavily punishing users, the system could mark a task as missed and encourage them, so they don't just quit, but get themselves back up again and try again.

# Retrospective assessment of functional requirements

Looking back, the original core requirements were mostly realistic and we were able to implement them successfully. Users can select an avatar, create routines and missions, complete tasks, gain points and update their avatar stats and level. The dashboard also displays the avatar, level, main stats, tasks and weekly progress.

The supporting community features were also completed. Users can create text or image posts, share achievements and comment on other posts. We also added a motivational quote API with fallback handling and a countdown timer showing when daily tasks reset.

The main unfinished requirement was what we called 'missed missions'. Tasks are not automatically marked as missed at any point in time, so the avatar does not lose energy or stats after inactivity, and no specific feedback is shown. Reactions and an activity streak were also left out.

In conclusion, the missed-mission requirement was less clear than it should have been, because it involved decisions about time zones, reset logic and how negative feedback could affect motivation.

Overall, and in my personal opinion, I believe our prototype achieved the main avatar-mission loop, that was supported by the evaluation, that also, showed us what the next improvements should be. I believe our focus should be more clarity, more feedback and better performance, rather than just start adding unrelated features.