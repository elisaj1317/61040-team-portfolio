---
title: "Project Converge: Conceptual Design and Synchronizations"
excerpt: "Conceptual Design and Syncronizations"
tags:
  - Project
  - "6.1040"
  - Converge
  - AEMP
---

<style>
  p {
    margin-bottom: 0.25em !important;
  }
  p + ul {
    margin-top: -0.25em !important;
  }

  p + h2, p + h1 {
    margin-top: 1em !important;
  }

</style>

{% include toc %}

# Conceptual Design

## Food

**Name** : Food [Item]

**Purpose** : Track consumable objects in an entity's fridge or pantry

**Operational principle** : If an entity inputs a food item with an expiration date, then that food is displayed in order of expiration date (earliest at the top) in one of three sections: "Expiring within the next 7 days", "Expired", or "Rest of my stockpile".

**State** :

- stockpile: Item -\> set Food // stores all foods by owner, there exists one for every owner
- name: Food -\> one name // food's unique identifier
- quantity: Food -\> one number // number of food in owner's possession
- expiration: Food -\> lone Date // date of expiration on food
- wner: Food -\> one Item // entity who has possession of food

**Actions** :

- Entity u adds a food with name x, quantity y, and expiration date z
  - Create a listing v
  - Set u as owner of v
  - Set v's name as x
  - Set v's quantity as y
  - Set v's expiration date as z
  - Add v to u's stockpile
- Entity u removes a food v where u is owner of v
  - Remove u as owner as v
  - Remove v from u's stockpile
- Entity u decreases quantity to x of food v where u is owner of v
  - Decrease quantity of food v to x



## Community

**Name** : Community [Item]

**Purpose** : Find available food that an entity is willing to travel to

**Operational Principle** : If an entity follows a community, then when they are missing items needed to make a recipe, they can see food items available from people in that community

- Note: the person who wants the food does the walking
- Note: Due to the time constraint, there will be preset communities limited to the MIT community

**State** :

- name: Community -\> one name // community's unique identifier
- members: Community -\> set Item // entities who have joined the community (each entity can only be a member to one community)
- followers: Community -\> set Item // entities who are willing to walk to this community to claim food

**Actions** :

- Entity u follows community with name v
  - Add u to community v's followers
- Entity u unfollows community with name v
  - Remove u from community v's followers

## User

**Name** : User

**Purpose** : Establish a user's identity to allow them to input food items and engage with content on FridgeCheck

**Operational Principle** : If an entity creates an account with a username and password and they provide the same username and password when signing in, then they will gain access to the profile and actions they take are associated with that account. If they provide the same username and a different password, then they will not gain access to the profile.

**State** :

- username: User -\> one username //user's unique identifier
- password: User -\> one password //user's password for authentication
- community: User -\> one Community //the community where the user resides
- contact: User -\> one content // information for contacting the user
- diet: User -\> set diet // user's dietary restrictions (vegan, etc.)
- allergies: User-\> set allergies // user's allergies (peanuts, gluten, lactose etc.)

**Actions** :

- User registers with username u, password p, community c, contact i, diet d, and allergies a where there is no user signed in
  - User created with username u, password p, community c, contact i, diet d, and allergies a if there does not already exist a user with username u
  - User is added to community c's members
- User edits their contact information to contact c where there is a user signed in
  - Contact is updated to c
- User edits their allergies to a where there is a user signed in
  - Contact is allergies to a
- User edits their diet to d where there is a user signed in
  - Contact is diet to d
- User edits their community to c where there is a user signed in
  - User is removed from original communities members
  - Community is updated to c
  - User is add to c's members
- User deletes their account where there is a user already signed in
  - User with information of signed in user is deleted
  - Current user is signed out
- User signs in with username u and password p where there is no user signed in
  - If there exists a User with username u and password p, currentUser is set to that user
- User signs out where there is a user signed in
  - Current user is signed out

## Recipe

**Name** : Recipe

Note: Uses [spoonacular API](https://spoonacular.com/food-api)

**Purpose** : Use user's stored items to suggest snacks or meals, and provide information on which ingredients are in their fridge and which they do not currently have

**Operational Principle** : If the user knows of or searches for meals/snacks they want to make, multiple sets of instructions are displayed for possible food items.

**State** :

- name: Recipe -\> one name // name of recipe
- ingredients: Recipe -\> set Food // set of Food need to make the recipe
- instructions: Recipe -\> one content // the directions for making the recipe
- diet: Recipe -\> one dietary restriction // the dietary restriction of the recipe (vegan, vegetarian, etc.)

**Actions** :

- User searches for recipe with set of Foods y
  - Gets recipes from spoonacular api that use ingredients y
- User searches for recipe with name n
  - Get Set of recipes r from spoonacular api that contain n in the name


## Listing

**Name** : Listing [Item]

**Purpose** : Sell or give away food to people in your communities

- Note: Listings are removed automatically upon expiration

**Operational Principle** : If the user creates a listing with a price, then other users can get the item for the given price. If the user creates a listing with no price, then other users can get the item for free.

**State** :

- item: Listing -\> one Item // Item being posted for exchange/sale
- price: Listing -\> lone price // Price for item being posted
- listings: User -\> set Listing // All listings by a user

**Actions** :

- User creates a listing for item u with optional price p
  - If u has an expiration date that has not passed, then a listing is created with item u and price p (if given)
  - The listing is added to user's set of listings
- User deletes a listing u
  - The listing u is removed from the user's set of listings
- User edits a listing u with new price p
  - The price associated with listing u is changed to p
- User searches for listings for item x
  - Gets listings whose item is listed as x

# Tradeoffs

## Creating Communities

Originally, we wanted users to be able to create communities to allow them more flexibility in where they list their foods. However, this flexibility adds complexity that is not core to our app. The purpose of communities is to "find available food that the user is willing to travel to." Thus, we would need to define distance. How do we allow users to define their location in a consistent way? How do we measure the location between two users? Due to the time constraint, we decided to limit communities to communities on MIT's campus. This will allow us to focus on novel features that are core to our app instead of calculating distance.

## Food Exchange

Originally we wanted to allow consumers access to all of the listings within their communities. This brought up many questions about the purpose of our website. Do we want people to just exchange food between each other? Do we want to guarantee that the food being exchanged will be used promptly? We decided the focus of the website was to search for recipes based on food you currently have and/or a specific recipe you want to make and only requesting items for things that are not currently in your stockpile. This would achieve our goal of minimizing food waste since it ensures that the user claiming a food item intends to use it in the near future. Thus our main objective of the food exchange was as a supplement to the recipes feature, as such we decided the community listings to be internal and users only have access to specific community listings when they search for a recipe that requires certain ingredients that they do not have in the stockpile.

## Search based on Custom Recipe

We debated over the idea of allowing custom recipes in our app, meaning users could add recipes that they regularly like to make and indicate the quantity of each ingredient needed. Then, users could click on that recipe to see what ingredients they're missing and who they can contact to procure those ingredients. We've decided against this because we think that allowing a user to create a custom recipe would add complexity to the user experience since we are already allowing the user to search through a database of a wide variety of recipes. We also want to have the user search based on the ingredients they have, which if the user had a custom recipe they would already know they could make it and that would defeat the purpose of the recipe search function. If a user wants to make a custom recipe they can simply remove the items they used from their stockpile and add any leftovers they have from making the recipe.

# Synchronizations

- If user u searches for recipe r and ingredients i are not in their stockpile, but are in their community listings, then the set listings l will be displayed
- If Food f is listed and expires, then listing l of Food f will be removed
- If Food f is listed and removed, then listing l of Food f will be removed
- If a user decides to "make" a recipe the ingredients the user has in their stockpile that are in the recipe will automatically have their quantity decremented or be removed