---
title: "Project Final Build: Design Revisions"
excerpt: "Design Revisions"
tags:
  - Project
  - "6.1040"
  - Final Build
  - AEMP
---

{% include toc %}

[**Vercel Deployment**](https://fridge-check.vercel.app/#/)  
[**Github Repo**](https://github.com/Pujabalaji/fridge-check)  

## Addition of “All Listings” page
In our user testing, the tester found it confusing that you can create listings but those aren’t visible to other users except when they are specifically trying to make a recipe that our app suggested and are missing ingredients. The tester commented that the concept of Listings could be more useful in our app if users had a way to see what food items are available to pick up and didn’t have to happen to be making a recipe that required those food items in order to see those listings. Therefore, we’ve added an All Listings page, where users can see all listings in communities they follow, and can see an explanation that they need to follow communities to view listings from those communities. 

## Change Delete button to Thrown Away
In Beta, a food item can be deleted. However, the option to ‘Delete’ removes the social guilt of wasting food. Thus, we revised the ‘Delete’ option to include both ‘Thrown Away’ and ‘Eaten’  options. This distinction creates more social incentive to eat and use food rather than throwing it away, helping our app be more effective in terms of reducing food waste.

## Added Stats page
The goal of the app is to reduce food waste. We’ve added a Stats page to help users realize how much FridgeCheck is helping them accomplish this goal. Without this page, there is no quantifiable and viewable measure of how much food they are wasting, and with this page, users can see the percentage of food they’re wasting (percentage of food items thrown away relative to the total number of food items added to their stockpile). Specifically when a user chooses the “Thrown Away” option the number of items they have thrown away increments, but if they mark a food as “Eaten” it remains unchanged.

## Confirm deletion with modal
There are several buttons on food items such as ‘Edit Quantity,’ deletion buttons (‘Delete’ for Beta and ‘Thrown Away’ and  ‘Eaten’ for Final Build), and ‘View Listing’. These buttons are very similar in style to each other and to other buttons on FridgeCheck. This means the user may accidentally delete the food when meaning to View Listing. Though these buttons have large areas and gaps between them to avoid this, we added a modal so users must confirm the deletion of the food, significantly reducing any burden that accidental deletions would cause the user. 

## Auto-follow your home community
Following a community indicates that a user is willing to pick up food items from a particular living location. When a user selects a home community, it is reasonable to assume students would typically want to follow the listings of their home community since that would be a convenient pickup location for them. We have added a synchronization where selecting a home community automatically makes that user follow that community, and this enables the user to immediately view listings rather than having to guess that they need to follow a community before listings appear. 

## Disable recipe suggestions if no ingredients in stockpile
If there are no ingredients in the stockpile, it makes sense that there should be no recipe suggestions based on a user’s stockpile. We disabled the option to suggest recipes that use ingredients in the user’s stockpile to avoid confusion and make it clear to users that we cannot suggest recipes using ingredients in their stockpile if they have nothing in their stockpile. The user can still search for recipes using the ‘Search Recipes by Name’ option because it makes sense that they might want to search for a recipe in general.

## Change prepared food checkbox into a required yes/no radio button
When adding a prepared food (Chipotle bowl) to their stockpile, our user tester missed the prepared food checkbox because it was small and hard to see. This is problematic because we don’t want users creating listings for their leftovers.  We’ve changed the indication of prepared food into a radio button with the options being either Yes or No, and we require the user to select either yes or no before the create food form can be submitted.

## Make the option for no units be called None instead of being blank
When trying to add eggs to the stockpile, our user tester was confused by whether they could leave the units blank or not. We’ve now set the default to be None, so the user can either select a unit or leave the dropdown set to None if they do not need units.

## Move “Want to make this recipe?” section to the recipe details page
Our user tester found it unnecessary to have the suggested food items to decrement the quantity or delete on the same page as the ingredient details, since the stockpile food items already show up under the “You have _ ingredients” section. The user mentioned that they would not know if they wanted to decrement until they determined they wanted to make the recipe by seeing the instructions. Therefore, we moved the suggested deletions to the Recipe Details page, because the user would click the recipe details for information on preparing that recipe if they were actually going to make it, and they could then easily remove the food items there as they make the recipe.

## Other small changes
We've made a few other small changes such as renaming labels to our app to make it more pleasant to use. We're including these as a bulleted list here because they aren't major design revisions:

- Add favicon
- Change “Contact info:” to “Email {{email}} to claim” for clarification on how to contact another user to claim listing
  - User tester did not realize they needed to email the listing creator in order to obtain the food
- Change “Create Food” name to “Add Food to Stockpile”
  - User tester found "Create Food" to be confusing wording
- Change “Suggested Recipes” to “Find Recipes”
  - User tester did not realize from the tab name that they could also search for recipes by name 
- The logo and app title are links to the home page
- Added a dropdown for pages and actions related to account
  - Make it easier to log out, also good placement for the stats page
- Changed Styling to have creation forms only appear when a button is clicked
- Changed frontend validation to only show errors when submit is pressed
  - Nicer user experience to not see red errors everywhere before you’ve had a change to fill everything out
