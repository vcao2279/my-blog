---
title: Week 2 in Labs8
date: '2018-11-16'
---

Our MVP for this week is to connect frontend to backend, implement Auth0 for signup/login, and implement Stripe API.
This week is particularly more challenging because we lost a day due to Veteran day, the change in project specs,
and the steep learning curve of the APIs

## Team Progress

Even though we couldn't manage achieve all the goals we wanted, i think we did well. Personally for me, I spent the
majority of my time helping my team with implementing the APIs. A lot more researching and reading documentations than
writing code. We got Auth0 and Stripe working on frontend, but we're stuck with sending the auth token to the backend.
It's important because everything in the backend depends on the auth id. Without it we cannot create other data.

![Contribution Graph](https://i.imgur.com/03eAmCI.jpg)

## Task Pulled

### Front End

- Ticket 1

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/22)
  - [Trello](https://trello.com/c/vOL3Sst6/5-navigation)

- Ticket 2

  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/30)
  - [Trello](https://trello.com/c/si0GCW22/50-search-and-preview-in-create-page)

- Ticket 3
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/34)
  - [Trello](https://trello.com/c/xMD6lklA/60-improving-script-to-scrape-recipes-and-save-to-db)

### Back End

- Ticket 1
  - [Github](https://github.com/Lambda-School-Labs/Labs8-Cookbook/pull/27)
  - [Trello](https://trello.com/c/SOV74CZA/55-stripe-integration)

### Analysis

The most challenge task for me this week was the backend task of implementing Stripe, which i worked with Katie.
At first it seemed easy, because the UI was created by Stripe Api, but it was very complicated when we have to
connect it to graphql server. Stripe works in react through a package called react-stripe-checkout. This package
provides a StripeCheckOut component. We can provide properties of our checkout interface that will display in
the front end interface like app name, app email, charge amount, currency, as well a stripe secret key that our
Stripe account provides.

```
<StripeCheckout
    stripeKey='pk_test_FyA4hajfxfEQ4jCcEaeQtTIL'
    name='Cookbook Subscription'
    zipcode={false}
    amount={1000}
    currency='USD'
    email='cookbook_project@yahoo.com'
    token = {res => this.onToken(res, createSubscription)}
/>
```

Now when our customer choose to pay, they will see a checkout window created by Stripe.

![Stripe checkout](https://i.imgur.com/ECO4Rdp.jpg)

Now in the StripeCheckOut component above, there's also a property called `token`. When the customer hit
the pay button, our client will send these information to Stripe server. Stripe server will send back a
token with payment information. At this point however, the charge isn't completed. This token is for us
to perform a 1 time charge to the customer credit card. This is why the token property is a function called
`onToken`. `onToken` receives a response from Stripe (the token Stripe sends back), and responsible for
passing this token to a mutation in graphql backend server called `createSubscription`.

```
onToken = (res, createSubscription) => {
    createSubscription({
      variables: {
        token: res.id
      }
    }).catch(error =>{
      console.log(error.message);
    })
  }
```

When `createSubscription` is called, it will execuate the charge, send it to Stripe again for confirmation,
and receives back from Stripe a charge id ( you can think of it as receipt number). `createSubscription` will
also create a subscription in our database for the record, with customer id, subscription created date, and the
charge id. At this point since the payment is completed, we can see the transaction in our Stripe account.

![Completed transaction](https://i.imgur.com/zIQlB0n.jpg)

And only then, the entire process is completed. This diagram sums up the whole process pretty well for me,
and it felt pretty good getting this API to work.

![Stripe process](https://i.imgur.com/MJf1cQO.jpg)

### Reflection

This week felt chaotic. We had many new things to implement, each with a steep learning curve. It was challenging
to complete everything in 3 days. Personally I spent a lot of time after-hour to read as many documentation as I
can with the hope that i can help my team get everything done. And I can see why the staff advised against
this. I feel pretty burned out trying to cover all the problems that we have. I'm gonna slow down a little bit, and
try to focus on my tasks more, and help whenever my teammates need me.

### Whiteboard Interview

[Video](https://youtu.be/6G_CvxANCS0)

### MVP Links for this week

- [Auth0 signup/login](https://lambda-cookbook.netlify.com)
- [Stripe checkout](https://lambda-cookbook.netlify.com/home/settings)
