---
title: Week 1 in Labs8
date: '2018-11-09'
---

This week is the first week of Labs8. Our project is called Cookbook. Cookbook
let user save a recipe from the internet, and schedule the recipe for a
particular day during the week. The app will automatically generate a shopping
list for the whole week. User can also open a recipe and follow the cooking
instructions.

## Team Progress

We did a lot of work in the first week, and got the MVP done. My handle is Vcao2279.
![Contribution Graph](https://imgur.com/cifR4f2.jpg)

## Task Pulled

### Front End

- Ticket 1
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/17)
  - [Trello](https://trello.com/c/9ObJyfx4/37-deploy-front-end-to-netlify)

### Back End

- Ticket 1: Initialize GraphQL Server
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/7)
  - [Trello](https://trello.com/c/L8Jhvo8H/10-graphql-initial-setup)
- Ticket 2: Deploy Prisma DB
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/14)
  - [Trello](https://trello.com/c/xQmrGqhh/36-deploy-prisma-db-to-heroku)
- Ticket 3: Create GraphQL datamodels and authentication logic
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/12)
  - [Trello](https://trello.com/c/VdMUMZXh/26-graphql-data-relationships-and-authentication-logic)

### Analysis

The most challenge task for me this week was ticket 3, creating graphQL datamodels.
We use Prisma as an ORM for our database, which is a posgreSQL. Prisma translate
all SQL queries into graphQL syntax, which allows us to perform all CRUD operations
without writing complex SQL. In order to do this, Prisma generates a schema
based on the datamodels that we define in the database, and we call this Database Schema.
For example, a User table with userid, name, email, password would be defined like this:
![Prisma Schema](https://imgur.com/U8CXdh1.jpg)

Using this database schema, we'll generate a graphQL server schema, called Application Schema.
And with this, we can create Mutation and Query resolvers, which is what graphQL uses to
perform CRUD operation. For examples, with if we wanted to query the user table above, the query
resolver would look like this:
![Query resolver](https://imgur.com/xlpNei6.jpg)

Now that the graphQL server is able to read the data from user table. We can test this GraphQL
playground.
![User Query](https://imgur.com/TeTJorO.jpg)
Here we can select a particular user and return the information we need, in this case id, first name,
last name, and email.

The datamodel of graphQL is totally different than SQL tables. It's challenging to wrap my head this
at the beginning. At the same time, it's also nice to see how precise the syntax is. Datamodels are
tightly connected in graphQL schema, and this allows me to query exactly what I want using very short
query, compared to SQL where I have to write complex query.

### Reflection

Working in a team is hard! I'm more of an individual type of developer. I like
to have an attack plan for a project, and stick with it. The first challenge I
had was to compromise. Each of us had his/her idea on how to tackle this lab project.
And we had to figure out how to divide our tasks in a logical way. The good thing was
that none of us was really pushing their idea on other members in the team. We all
compromised and figured out what we liked to do, then divided our tasks accordingly.
I think this is the main reason that we worked together pretty well during this first week.
And if we can keep this up I think we can do well in making each week MVP.

### Deployment Links

- [Frontend Deployment on Netlify](https://lambda-cookbook.netlify.com)
- [Backend Deployment on Heroku](https://lambda-cookbook.herokuapp.com/)
- User Signup
  ![User Signup](https://imgur.com/L53yDrl.jpg)
- User Login
  ![User Login](https://imgur.com/XtZVdNi.jpg)
