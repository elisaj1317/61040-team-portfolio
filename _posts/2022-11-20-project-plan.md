---
title: "Project Converge: Project Plan"
excerpt: "Project Plan"
tags:
  - Project
  - "6.1040"
  - Converge
  - AEMP
---

{% include toc %}

# Alpha

| **Task** | **Point Person** | **Deadline** |
| --- | --- | --- |
| Create Github | Puja | 11/19 |
| Create MongoDB for group | Monica | 11/19 |
| Create API account | Elisa | 11/19 |
| Map all MongoDB Routes | All | 11/20 (work together on 11/19) |
| Map additional API (Spoonacular) Routes | All | 11/20 (work together on 11/19) |
| Implement user concept | Ashley | 11/23 |
| Deploy Site | Monica | 11/23 |

# Beta Plan

| **Task** | **Point Person** | **Deadline** |
| --- | --- | --- |
| Implement creating a food item | Monica | 12/3 |
| Implement deleting a food item | Monica | 12/3 |
| Create "My Stockpile" page | Monica | 12/3 |
| Implement a listing concept | Ashley | 12/3 |
| Implement creating a listing, form on listings page for now | Ashley | 12/3 |
| Implement removing a listing | Ashley | 12/3 |
| Create "My Listings" page | Ashley | 12/3 |
| Implement Recipe api calls | Elisa | 12/3 |
| Create Recipe page | Elisa | 12/3 |
| Implement Community Concept | Puja | 12/3 |
| Create "My Communities" page | Puja | 12/3 |
| Code Review | All | 12/4 |
| Design Revision | All | 12/4 |
| Make sure site is properly deployed with updates | Puja | 12/4 |
| User Test | All | 12/6 |

# Final Build

| **Task** | **Point Person** | **Deadline** |
| --- | --- | --- |
| Implement editing food items | Monica | 12/11 |
| Implement editing listings | Ashley | 12/11 |
| Implement automatic decrementing | Elisa | 12/11 |
| Polish User concept | Puja | 12/12 |
| Polish Recipe Concept | Elisa | 12/12 |
| Polish Food Concept | Monica | 12/12 |
| Polish Listing Concept | Ashley | 12/12 |
| Polish Community Concept | Puja | 12/12 |
| Stylize Frontend | All | 12/12 |
| Make sure site is properly deployed with updates | Puja | 12/13 |

# Something went wrong...

The immediate response when we realize we may not reach a deadline is to support the point-person for the task. This involves further dividing up a task, if possible, so multiple people can share responsibility or transfer “ownership” of the task to another person.
 
If dorm communities lead to difficulties, maybe in finding listings for ingredients the user needs for the recipe, we can narrow down to the one overall community of MIT.
 
If something goes wrong, we may need to re-evaluate what can be done overall. For example, our Recipes concept includes two methods of recipe filtration, including searching for recipes from the API that includes the ingredients in a user’s fridge and searching for recipes the user has in mind by name. If progress is made on one, the other can be dropped or modified (specific modifications can include not integrating with Listings and instead having the user mention which ingredients they have in their fridge). Additionally, we currently plan on having a button for “Make this recipe” where if a user makes a suggested recipe, it automatically removes or decrements the quantity of those ingredients in the user’s stockpile. This may be a complicated synchronization and if we find that it’s too challenging, we can either not implement quantity decrementing or not implement automatic removal of items from the user’s stockpile. 