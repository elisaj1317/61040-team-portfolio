---
title: "Project Final Build: Advice for Future Students"
excerpt: "Our advice for future 6.1040 students"
tags:
  - Project
  - "6.1040"
  - Final Build
  - AEMP
---

{% include toc %}

## Advice for future 6.1040 students
Dear Future Software Studio Students,

The opportunity to build a new, authentic app as a team is super exciting! Here is some advice we have after creating [FridgeCheck](fridge-check.vercel.app).

If you are going to use a front-end framework/library, such as React, Bootstrap, or Ember, choose one ahead of time so you do not need to restyle all of your components later. This group decision will also enable each team member to contribute to the front-end as they code their concept(s).

We found it helpful to discuss the routes as a team prior to parting ways to work on our separate concepts, this made the integration easier later on since we all knew how to obtain information related to other concepts. 

After the typical delegation of tasks between necessary concepts, be sure to set aside enough time to manage synchronizations. Concepts are independent, but there are synchronizations that are necessary to ensure full and pleasant functionality in your app. We recommend reconvening after everyone has (mostly) finished their tasks to discuss and complete synchronizations or anticipate synchronizations before coding concepts and include them in your initial project schedule for after the initial implementation of each concept is completed. 

Debugging can be tricky, and there are many alternate (and usually more effective) approaches than printing to your console through a ```console.log``` command. One valuable debugging tool is the extension Vue Devtools. Vue Devtools allows you to highlight parts on your Vue-based web page and check the back-end components that make up that part. You can view and edit the relevant code through the extension. This helps quickly narrow down the root of the problem.

When debugging, we typically start with the backend since the front-end relies on routes provided in the router. Instead of building the whole pipeline, including an HTML form, we would suggest using [Postman](https://www.postman.com/). Simply log your route to the console and use that route in Postman. This verifies that the backend works before proceeding, and it is particularly helpful if your project utilizes multiple APIs. 


Sincerely,
Team AEMP