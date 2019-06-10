---
layout: single
title: "Thing A Week - Week One"
tags:
  - thing a week
  - week one
---

Welcome to Week One of Thing a Week! We're kicking things off with a competition for all of my spreadsheets to decide which will become a Thing.

I'm a huge fan of building and managing spreadsheets. I have one for pretty much everything in my weekly routine, and right now, I've been spending a lot of time managing these:

- Meal Planner
- Personal Budget
- Weekly Planning
- Order Calorie Counter

Pretty basic stuff, and that's why I think these would be great to get my feet wet. So, let's do a basic Pros / Cons for each of these and see if we can decide!

### Meal Planner

Basic meal planner with a cell for each meal and each day of the week. Since I'm in love with counting calories, it also has a slot for that.

##### Pros

- Pretty simple
- Lots of interesting possibilities using different APIs
- Useful for pretty much everyone that has to manage his own or his household meals

##### Cons

- Well... It's pretty simple, maybe even a little underwhelming?

### Personal Budget

I don't like budgeting for long periods, so I use a single daily / weekly budget that keeps track of how much I have and how much I can spend in every day and week.

##### Pros

- Very useful. Budgeting and tracking expenses is probably the one single thing that has the biggest impact to anyone's finances.

##### Cons

- Hard to get right. Budgeting is very personal since there are so many different income sources and possible expenses.

### Goals Planner

I like the idea of having max. 3 goals for each day of the week, and i write them down here (alongside my chores).

##### Pros

- Very simple! Basically a Todo List, except it doesn't let you add too many things.

##### Cons

- People already use a wide array of tools to manage tasks, and having an admittedly not very flexible tool might put a lot of people off.

### Order Calorie Counter

I like knowing how many calories there are in my food whenever I order, and I use this sheet to keep track of that.

##### Pros

 - Very useful, and I don't think there are any practical alternatives out there.

##### Cons

 - It takes a lot of work to find the restaurant menu and estimating how many calories the food has. We would need a tool to simplify this proccess as much as possible.
 - Much more complex than all others. Most food order services don't even have an API, so we would need to reverse engineer that before even getting started.

---

As you can see, the order of complexity is 

Order Calorie Counter > Personal Budget > Meal Planner > Goals Planner

Since we're just getting started, I'll just pick one from the middle in the complexity scale: **Personal Budget**.

Let's take a look at the requirements!

### Personal Budget Requirements

- Enter income
  - The user inputs how much he earns (weekly, monthly, daily).
  - The user can also add one time payments, and how much he has in savings
- Enter expenses
  - The system has places to add itemized expenses and savings, such as utilities, bills, expenses, savings and credit card payments
  - The system easily allows users to insert data from previous days
- Summary
  - From the data, the system shows a nice summary of expenses, income and budget values. It tells you what your flexible spending is, and how much you can afford to spend daily, weekly and monthly and still save money to meet the budget goals.
  - Also, it has a daily tracker to give a more down to earth picture of where the money is being spent.
- Work offline
  - The data must be always available for the user device
- Sync
  - If the user wishes to, he can create an account and sync his data to any other connected device
- Import Expenses through Copy/Paste or CSV
  - Lets users import CSV files from other software into his expenses
- Export all to Sheet
  - Simple CSV function to export all of the user data to a CSV file so he can use it with other software

--- 

Seems just about enough work for a week! Now, let's discuss our tools!

- Prototyping: I'll be using Adobe XD for the interface design.

- Front-End:
  - React + Redux + Styled Components: I don't think I even need to explain this choice, right?
  - Bootstrap + Sass: Bootstrap 4 is amazing, but we'll need to customize it heavily. Thankfully, that's very easy with Sass!
  - Workbox: Since we'll be doing a lot of offline, background sync stuff behind the scenes, Google's Workbox will make our life much easier.

- Back-End:
  - Node: I love Node, Node loves me back.
  - PostgreSQL: Honestly, I'm not sure there's a better database system out there nowadays. I'm not a huge fan of NoSQL for highly structured data such as our users expenses, so we're going with good, old-fashioned SQL.

---

Time to get our hands dirty with the interface design! See you in the next post!