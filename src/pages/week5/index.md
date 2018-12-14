---
title: Week 5 in Labs8
date: '2018-12-14'
---

This is it! The final week of our capstone. We completed almost everything that need to be done. It's been a long and
challenging 5 weeks. And i'm really proud of the final product we got in the end.

## Team Progress

During this week we improved some of the core functionalities, as well as UI in all pages. The hardest part probably to 
complete the UI for the best possible UX experience. Other than that the implementation wasn't too bad.

![Contribution Graph](https://i.gyazo.com/6b96378626c4738f492d73fea8a8c35d.png)

## Task Pulled

### Front End

- Ticket 1
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/91)
  - [Trello](https://trello.com/c/1cKutUUH/125-add-error-component-and-404-page)

- Ticket 2
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/95)
  - [Trello](https://trello.com/c/UG9YJOA1/127-more-polishing)

- Ticket 3
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/102)
  - [Trello](https://trello.com/c/cmsUsTmW/133-redo-settings-page)

### Back End

- Ticket 1

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/83)
  - [Trello](https://trello.com/c/N3DvJTun/114-bug-fixes-and-more-features)

  
### Analysis

The majority of work this week was on the front end. Our back end was stable and didn't need any changes.
One of the major improvement i did was to allow users to schedule multiple events at the same time when they
schedule using modal. Before they would have to do it multiple times for each recipe, but now they can do it
just once.

![demonstration1](https://i.gyazo.com/6abb0664e0daf3d3387d29e894d55994.png)

I also use toastify package to add a popup modal everytime the user delete/update anything successfully, as 
well as telling them if what they're doing is not right

![demonstration2](https://i.gyazo.com/a54c98ec1c4c285697b632e73971232b.png)

The major UI improvement i did was for the settings page, to make it consistent to the rest of the theme. It took
more work than i expected. But it looks quite nice in the end.

![settings page](https://i.gyazo.com/b0126af5d6260299862c424609e28d6f.png)


### Team Reflection

For this project we used the following tech stack: React, Apollo for front-end, and Graphql, Prisma for back-end.
We wanted to use this tech stack to test our learning ability, and we're proud that we could complete our project
in the given 5 weeks. React is the most popular framework with the biggest list of supporting packages. Plus we 
felt like we would be overwhelmed with learning if we were to choose something else like Vue, or Angular. Apollo 
is the bridge to connect React and Graphql back-end. Apollo comes with cache and store so it replaces the need to 
use Redux. We chose GraphQL as our back-end server because of it's simplicity to pull data compared to REST API. 
It eliminates the need to have multiple end-point, and we can pull exactly the data we need, nothing more, nothing 
less. Prisma is the connection between GraphQL and our database postgreSQL. Prisma pre-generate basic resolvers based
on how we define our data models.

Our app Cookbook is a web application that allows users to add recipes from any website into their collection of recipes. 
Allows them to easily search and filter through recipes and view all of the information for any recipe. They can plan 
meals by scheduling recipes for any amount of days and also generate a shoping list for grocery of the ingredients 
you'll need for a customized date range.

### README file

[readme](hhttps://github.com/Lambda-School-Labs/Labs8-Cookbook/blob/master/README.md)

### MVP Links for this week

- [App Link](https://lambda-cookbook.netlify.com)
