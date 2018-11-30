---
title: Week 3 in Labs8
date: '2018-11-30'
---

Our goal for this week is to complete all MVP core functionalities. For our app those are scraping recipes, saving
recipes' information, instructions, ingredients, and scheduled day into database. Then we need to display these
information in respective pages like recipes page, calendar pages, grocery list page.

## Team Progress

We fell short this week due to a variety of problems. First the helper website we relied on had some problem, so we
couldn't run scraper to extract recipes. Then Auth0 doesn't work well with social media login, if we login using
facebook or google account, then the callback doesn't redirect us to our main content.Third is the problem of creating
complex nested mutation and queries. After user extract the recipe, when they click save, 4 different mutations need to
happens at the same time: saving recipe, instructions, ingredients, and the schedule for recipe. Instruction, ingredients
and schedule all connect to recipe, and recipe connects to user, we needed to perform a nested mutation. It was super hard.
We'll keep working on fixing these problems today.

![Contribution Graph](https://i.imgur.com/2kJacmf.jpg)

## Task Pulled

### Front End

- Ticket 1

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/45)
  - [Trello](https://trello.com/c/QloJWuJo/76-complete-scraper)

- Ticket 2
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/40)
  - [Trello](https://trello.com/c/FNN2qAuA/70-auth0-apollo-graphql-routes-and-redirection)

### Back End

- Ticket 1

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/53)
  - [Trello](https://trello.com/c/qyRkqSCG/81-create-event-mutation)

- Ticket 2

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/55)
  - [Trello](https://trello.com/c/f6Yzh6WK/79-add-instructions-and-ingredients-mutations-to-create-page)

### Analysis

This week i did a lot documentation reading to be able to troubleshoot a lot of the problems we had. I
particularly enjoyed reading about graphql mutation and query, and learn how to do nested mutation.
In graphql, each mutation or query is imported into react as Mutation or Query components, and these
components pass down data or mutation function using render props.

![Query Example](https://i.imgur.com/HdMcj61.jpg)

When we nest them, these render props get extremely complicated. In this example, we need to use the
User query component above to extract information of the logged in user. Then use that user id to retrieve
all recipes belong to this user. With render props the code looks really complicated, and prone to errors.

![Nested Query](https://i.imgur.com/JIFS3tl.jpg)

Then I discovered a different syntax that Apolly provides, and this was a ground breaking discovery because
we were stuck with nested mutation for almost 2 days, and this really simplified the way we pass data from
1 mutation to another. In this example, after we scrape the recipe, we need to save recipe into database,
then use that recipe id to save instructions, ingredients, and scheduled meals for this recipe. Usually we
would have to 3 double nested mutation like the nested query above. But by using Apollo `graphql()` syntax,
we could expose these mutation to our component, then use them where we see fit without writing Mutation components.

![Expose Mutations](https://i.imgur.com/2ukgSg7.jpg)

In the example above, I use `graphql` syntax to expose 4 mutations to Create components props: createRecipe, createEvent,
createInstruction, and createIngredients, without having write 4 render props components. Then i can call these functions
anywhere in Create, and in any order, from this.props.

![Call Nested Mutation](https://i.imgur.com/TVZtbXz.jpg)

Now i can first call createRecipe function to create that user just scraped, and extract recipe from the returned data. Now
i use that id to construct the instructions, ingredients, and scheduled meal for this recipe by calling createInstruction,
createIngredients, or createEvent next. It provides much better readability and can be debugged easier.

### Reflection

I think for me this week has been the most challenging so far. It shows that tackling 3 new technologies within
a few week is very hard. A lot of time when each of us stuck on something, others would have to read the documentation
of that tech in order to be able to help. Within 3 weeks i've read documentation of Auth0, Apollo, Graphql, Graphql-Yoga,
and Prisma. While it was hard, i had many aha moments when i figured out how all of these connect and improve each other.
What i've learned might just be scratches on the surface, but it gives me the confidence that I can manage to do it under
pressure.

### Whiteboard Interview

[Video](https://www.youtube.com/watch?v=z9WZTxXW_d0)

### MVP Links for this week

- [App Link](https://lambda-cookbook.netlify.com)
