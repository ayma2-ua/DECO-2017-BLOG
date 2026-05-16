---
title: "From Concept to Database: Designing an ERD and Transforming It into a Relational Database" 
date: 2026-05-15
author: Andrea Yaretzi
summary: 
tags:
  - Programming
---
This week main implementation and flow work of the app was finished. However this week, while reviewing the project, we identified security and validation issues that were not initially considered during the wireframing stage. One important issue appeared in the upload system. Even though the form restricted uploads through `accept="image/*"`, this validation only existed on the client side, meaning users could still bypass it and upload unsupported files directly to the server, leading to possible security issued in the future.

After reviewing this behaviour, we decided to change the upload handling process by implementing proper server-side validation directly inside the shared file storage helper. That way we didn't only relied on browser restrictions, the backend now validated file names, allowed extensions, MIME types and had a maximum upload sizes, all this before saving any file into the system.

During testing, we also discovered that some uploads sent by the testing agent used the generic MIME type `application/octet-stream`, so we where relying entirely on MIME validation, and that could incorrectly reject valid image uploads. To make the system more robust and independent from browser or client behaviour, we adapted the validation logic and decided to prioritise trusted file extensions while still validating MIME types whenever the client provided reliable information.

The upload system now blocks unsafe file names that could attempt path traversal, validates allowed file extensions, applies MIME validation when possible, enforces a maximum upload size of 5MB, and automatically removes partially uploaded files whenever an upload fails due to size or validation errors.

Another thing we checked in this wee was accessibility. While reviewing the interface, some validation messages were only visually displayed, meaning screen reader users might not be properly informed when an error occurred. To improve this, we updated the form error components by adding accessibility attributes such as `role="alert"` and `aria-live="polite"` so validation feedback can be announced correctly by assistive technologies.

We also identified a usability issue with the custom file upload component. To solve it, we added visible focus styles using `:focus-within`, allowing the custom “Add visual” button to display a clear focus indicator whenever the hidden input receives keyboard focus.

From a visual perspective this changes are almost not noticeable, but they significantly improved keyboard navigation and screen reader accessibility.

We also decided to apply what we learnt at class and integrated an external API to enhance the motivational aspect of the platform. We used DummyJSON Quotes API, which provides random motivational and self-improvement quotes that can be displayed dynamically inside the feed and dashboard sections of the application. We implemented it using the official API endpoint (no need for a key). Since the project is about getting good habits, we thought this API was perfect since it could help reinforce user engagement and better support the self-development theme of the platform.

While implementing this feature, we considered the reliability risks of depending on external services. Because APIs can fail or become temporarily unavailable, we added fallback error (try/catch) handling to ensure the application didn't have any issues even if it fail at the request (local quote if it failed).

We also decided to make these validation rules configurable depending on the route. For example, the community feed only accepts image uploads (`.png`, `.jpg`, `.jpeg`, `.gif`, `.webp`) because that is what matches best with the purpose of the platform, while the demo upload section keeps a broader but still controlled list of accepted file types such as text files, images and PDFs for testing purposes (in case in a future we decided to add more features).

Finally we reinforced the testing done. To make sure the validation worked correctly, we added integration tests covering both rejection and acceptance scenarios. For example, uploading a `.txt` file to the post feed now correctly returns a `400` error, while valid image uploads are accepted and processed normally. We also performed build and lint checks after implementing these changes, with all tests and assertions passing successfully.