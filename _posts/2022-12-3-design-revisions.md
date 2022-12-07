---
title: "Project Beta: Design Revisions"
excerpt: "Design Revisions"
tags:
  - Project
  - "6.1040"
  - Beta
  - AEMP
---

{% include toc %}

[**Vercel Deployment**](https://fridge-check.vercel.app/#/)  
[**Github Repo**](https://github.com/Pujabalaji/fridge-check)  

## Adding Units to Food Concept

When we implemented the food concept we realized that the quantity parameter was not an accurate representation for the amount of food without including the unit. We also realized that to use the Spoonacular API it was necessary to pass in the specific units for the amount of food to yield the most accurate results. Therefore, we chose to add a unit field to the food concept.

## Distinguishing between leftovers and raw ingredients

One of the things we realized as we were implementing the listing concept is that users will likely not claim other individuals' leftovers. Thus, we update the food concept to note whether a food item is leftover from something the user cooked. If a food is a “prepared food” then we disable the create listing option.

## Recipe Display

We wanted to add more value to the user and display the foods that the user will use by making a specific recipe, so when displaying a recipe we separate the ingredients the user has and does not have. The listings are displayed below the corresponding food item to make it easy to find the ingredients the user is missing to make the recipe and contact other individuals to get those ingredients. 

## Adjusted quantity decrementation to suggestion

While implementing quantity decrementation and deleting foods if making the current recipe would use up all of an ingredient, we ran into several issues. First, the units inputted by the user when creating the food are not necessarily the same units used by the recipe. For example, butter can be measured in both sticks and tablespoons, so if a recipe calls for 4 tbsp and the user has 1 stick, that decrementation would not work, and the check for similar cases would be challenging and require lots of unit conversion cases. Instead, we’ve decided to display the food items in a recipe with the suggestion to manually delete ingredients using the delete button or adjust their quantities as needed.
