---
title: Week 4 in Labs8
date: '2018-12-07'
---

This is the last week of our project. We're supposed to complete all functionalities and stylings for our project.

## Team Progress

The functionalities are completed for the most part. We just need to fix bugs here and there, and adding minor feature
to make the app better. The styling is proven to be difficult this week. As we use external packages for calendar, and
they come with their own styling file, it's very hard to customize them, but we're getting there. We still need to
get started on the README file, and add comments for our code, then we're ready for the Capstone Defense on Monday.

![Contribution Graph](https://i.imgur.com/0xUEDdN.jpg)

## Task Pulled

### Front End

- Ticket 1

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/62)
  - [Trello](https://trello.com/c/BhDGOWCf/89-create-page-new-features)

- Ticket 2
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/70)
  - [Trello](https://trello.com/c/40O9Jt66/96-grocery-list-page-stripe-date-validating)

### Back End

- Ticket 1

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/74)
  - [Trello](https://trello.com/c/bL7igsHW/66-remove-signup-page-and-complete-settings-page)

- Ticket 2

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/80)
  - [Trello](https://trello.com/c/5M6tIlyv/105-multiples-features-and-bug-fixes)

### Analysis

The majority of my work this week was fixing app-breaking bugs and implement some difficult features.
A major problem for me during this week was all the asynchronous mutations and queries function
that we're using. Since most of our data is pulled directly from prisma database, anytime we perform
a mutation to create, delete, or update recipes and events, the components don't know that the data
have changed, hence it doesn't re-render. We couldn't understand why after we create recipe, the website
redirects to our recipes page, but the newly created recipe doesn't show up until we manually refreshes
the page.
I discovered that since create-recipe mutation is asynchronous, when the redirection happens,
the mutation hasn't been completed yet, therefore the new recipe will be missing from the recipes page.
After reading apollo documentation, I found out that Apollo provide a functionality called refetchingqueries.
Basically what it does is after the mutation is complete, immediately refetch the query that used on the next
page to pull data. This way the query isn't executed until after the mutation is completed.

![refetchquery](https://i.imgur.com/HdMcj61.jpg)

That solved the problem for displaying recipe after redirection. But it still doesn't show the scheduled meals
on the recipe card which displays the scheduled meals for that recipe.

![no-event](https://i.imgur.com/nZm9OWS.jpg)

The reason was simple once i understood it.
When user hit save recipe, there are 2 mutations happen, first one is to create recipe, then use the id of
the newly created recipe to create schedule meals for it. However since these are asynchronous functions,
there are no guarantess that the recipe is created before the create event mutation is run, hence it will
return no events. The fix is just add another fetch recipe query to refetchQueries, and it's good to go.

![double-fetch](https://i.imgur.com/oYcF8SF.jpg)

![with-event](https://i.imgur.com/1YcIcvI.jpg)

It truly feels great everytime i found an "aha" moment in graphql.

### Reflection

This week was challenging with all the bug fixes and styling. We had to rely on our strength in each area, in
order to maximize our efficiency. I think our team synergy is really great, and i hope we can get it all done
by monday.

### Whiteboard Interview

[Video](https://youtu.be/mxGyZGkiloc)

### MVP Links for this week

- [App Link](https://lambda-cookbook.netlify.com)
