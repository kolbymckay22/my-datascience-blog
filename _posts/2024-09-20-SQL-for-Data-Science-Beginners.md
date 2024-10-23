---
layout: post
title:  "Teaching Ryan Howard SQL"
author: Kolby Taylor
description: Teaches the basics of SQL, a programming language used to gather and organize data.   
image: "/assets/images/ryan_howard.jpeg"


---

## An Underrated Tool
When I first started working with data, I was overwhelmed by the sheer amount of information at my fingertips, but I had no idea how to extract meaningful insights. That’s when I discovered SQL, and everything changed. Now, I can manipulate vast amounts of data with just a few lines of code.

According to a study conducted by RTInsights, almost 70% of data scientists use SQL regularly ([RTInsights](https://www.rtinsights.com/almost-70-of-data-scientists-use-sql-regularly/)), and it is often one of the first skills required in data science job postings. However, despite its importance, SQL remains undertaught in universities across the country. Today, I will provide a brief introduction to this powerful language and explain a few ways it can be utilized.
 
 
## Dunder Mifflin's Top Clients
Imagine working as an intern at a small paper supply company. Your boss, Michael, asks to build him a report about the company's clients. Your task is simple, give him a list of the companies ten biggest clients and he'll be happy. Luckily, he doesn't expect too much. He's not much of an overachiever.


<div style="text-align: center;">
  <img src="https://static1.cbrimages.com/wordpress/wp-content/uploads/2021/05/Michael-Asks-Ryan-For-Music-Advise.jpg" alt="You and Your Boss" />
</div>

You might be nervous. This is your first project at the company! Plus, the only way to get the data is by writing queries. Don't worry, today I'll provide a step by step example of how you can gather the data you need using SQL. Your new-found querying skills are sure to blow your boss away... not that you need to. It's actually a little creepy how much he does... 

<div style="text-align: center;">
  <img src="https://i.pinimg.com/736x/78/5d/28/785d2874b373ca70dac84968c6f83195.jpg" alt="Creep?" />
</div>

Either way, you have big aspirations at this company, and so you want to do a good job. Lucky for you, I've got a step by step guide for how you can provide the perfect report!

## Step 1: SELECT Your Columns
The first thing you need to do is select the columns you want in your final dataset. If you want all of the columns in the table you're querying from, you can simply use *, like this:

``` sql
SELECT
  *
```

For your report, we want to get a little more specific. Let's make sure that we have the company name and their annual revenue.
``` sql
SELECT
  client_name, annual_revenue
```

## Step 2: Specify Your Table
The next step is to specify which table you need to query from. You can do this using a FROM statement. Let's pull our columns from the client_data table.

``` sql
SELECT
  client_name,
  annual_revenue
FROM client_data
```
## Step 3: Rank Your Companies
Too rank your companies from largest to smallest, we can use the ORDER BY clause. Using this tool, you can make sure that your data is ordered any way that you would like. With the order by clause, you can specify whether you want your rows to be ordered in ascending or descending order, using ASC or DESC. Here's ORDER BY works with different types of columns:

| Type   | ASC                           | DESC                           |
|:--------|:-------------------------------|:--------------------------------|
| Number | Smallest -> Biggest           | Biggest -> Smallest            |
| String | Alphabetically A -> Z         | Alphabetically Z -> A          |
| Date   | Chronologically Oldest -> Newest | Chronologically Newest -> Oldest |




Since we want to rank our clients from biggest to smallest, our query needs to look like this.

``` sql
SELECT
  client_name,
  annual_revenue
FROM client_data
ORDER BY annual_revenue DESC
```


## Step 4: Only Keeping 10 Biggest Clients
There are lots of ways to only keep the ten biggest clients. The easiest way is to use LIMIT. LIMIT allows you to keep your rows down to a certain number. This can be very useful when you're pulling from a very large dataset and only need a few rows.

``` sql
SELECT
  client_name,
  annual_revenue
FROM client_data
ORDER BY annual_revenue DESC
LIMIT 10
```

Great work! Michael seems to be happy with your work. He even grew some facial hair to match yours.

<div style="text-align: center;">
  <img src="https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2F0kgez3l0knn11.jpg" alt="Matching Goatees" />
</div>

Yikes. Maybe you should take it easy on your SQL writing skills. 

## Wrapping Things Up
Great job learning SQL! Now, you're ready to start working with more complicated queries. For now, focus on the basics, but soon, you can start grouping columns, joining tables togehter, and writing CTEs. Your new found talent in SQL will not go to waste. As a data scientist, you will find that it is one of your most useful skills.

Thanks for reading! Leave a comment if you have any questions or suggestions. Happy querying!

