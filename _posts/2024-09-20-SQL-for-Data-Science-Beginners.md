---
layout: post
title:  "Learning SQL"
author: Kolby Taylor
description: Teaches the basics of SQL, a programming language used to gather and organize data.   
image: "/assets/images/sql_background.avif"

``


---

## An Underrated Tool
When I first started working with data, I was overwhelmed by the sheer amount of information at my fingertips, but I had no idea how to extract meaningful insights. That’s when I discovered SQL, and everything changed. Now, I can manipulate vast amounts of data with just a few lines of code.
All data scientists aspire to build complex models and uncover powerful analytical insights. However, without clean, well-structured data, these goals are impossible to achieve. SQL is the most used tool for cleaning and organizing data.
According to a study conducted by RTInsights, almost 70% of data scientists use SQL regularly, and it is often one of the first skills required in data science job postings. However, despite its importance, SQL remains undertaught in universities across the country. Today, I will provide a brief introduction to this powerful language and explain a few ways it can be utilized.
 
## Getting Started with SQL
Before you dive in, you’ll need to set up an environment where you can practice. One of the most popular ways to do this is by installing a database management system like MySQL or PostgreSQL. MySQL is a fantastic option for beginners due to its user-friendly interface and helpful guides. If you're looking for something a bit more robust, PostgreSQL offers advanced features and excellent compliance with SQL standards, making it a great choice for tackling more complex queries.
But what if you’re not quite ready to dive into installation? No problem! You can also explore SQL through online platforms like SQLFiddle or db-fiddle. These web-based tools let you run SQL queries in your browser without any setup hassle. They’re perfect for quickly testing out your SQL skills or experimenting with new queries. Whether you prefer to install software or use an online platform, getting started with SQL is easier than ever.
 
## Basic SQL Queries
When you're getting started with SQL, having an understanding of basic queries is crucial. The foundation of these queries lies in a few key components: SELECT, FROM, WHERE, and ORDER BY. Here's an example query that pulls client information from a database:

``` sql
SELECT
  company_name,
  annual_revenue,
  number_of_employees
FROM client_data.client_information
WHERE annual_revenue >= 1000000 AND number_of_employees >= 10
ORDER BY annual_revenue DESC
```

SELECT
The SELECT statement is the backbone of any SQL query, allowing you to retrieve specific data from a database. This statement lets you specify which columns you want to view from a given table. In our query, we selected some information about each company, including its name, annual revenue, and the number of employees.

FROM
The FROM statement allows you to specify which table you are pulling the columns from. Tables within folders are specified by a period separating the two. In our query, you can see that the client_information table is inside the client_data folder.

WHERE
To filter your data based on certain conditions, you can use the WHERE clause. This is especially useful when you only want to see specific entries that meet certain criteria. In our example query, we only wanted to see our bigger clients, which is why we made sure we only kept rows with at least $1 Million in revenue and 10 employees. This helps you focus on specific groups of data, making it easier to analyze information that meets your requirements. To use more than one filter, you can simply use AND or OR.

ORDER BY
Finally, the ORDER BY clause allows you to sort your query results based on one or more columns. For example, if you want to see a list of employees sorted by their salary in descending order, this clause would help you achieve that. Sorting your results can be incredibly useful for identifying trends. In our example, we sorted by annual revenue from highest to lowest. The type of sorting that will occur depends on the data type of the column. If it is categorical, it will sort it alphabetically. Numbers are sorted from lowest to highest. Dates are ordered from oldest to newest. If you want to reverse the sorting order, you can use DESC.
 
## Aggregating and Joining Data with SQL
When writing SQL queries, often you will want to do more complex operations, like grouping together data, or combining data from multiple tables. 

Imagine you have a table that shows all the test grades of different students. You want to be able to see how each student performs overall, not just their individual tests. Here's an example of how you can do this:

``` sql
SELECT
  student,
  COUNT(*),
  AVG(test_score),
  MIN(test_score),
  MAX(test_score)
FROM test_scores
```

Uh oh! Looks like there is some attendance data you need, but it's in another table. No worries, you can just join the two tables together:

``` sql
SELECT
  ts.student,
  COUNT(ts.test_score),
  AVG(ts.test_score),
  MIN(ts.test_score),
  MAX(ts.test_score),
  SUM(ad.attendance)
FROM test_scores ts
LEFT JOIN attendance_data ad ON ad.student = ts.student
GROUP BY student
```

# COUNT, SUM, AVG, MIN, MAX
These functions are pretty self explanatory, they complete a mathematical operation on the specified column. In our query, we calculated the following information for each student:
1. The number of tests taken (COUNT)
2. The average test score (AVG)
3. The lowest test score (MIN)
4. The highest test score (MAX)
5. The number of days attended (SUM)

# GROUP BY
The GROUP BY clause is essential for aggregating data. In our sample query, we grouped our data by student. This allowed us to perform the calculations for every student.

# JOIN
JOINs are the way SQL combines data from multiple tables. There are multiple types of joins, including left, right, inner, and full. The one I've seen used most often is the left join. It keeps all the data from the table in your FROM statement, and adds all of the rows from the new table that match up. To specify which column should be getting matched, you can use ON. 

One thing to always remember is to alias your tables. Did you notice how before every column name in the query, there were two letters? When you specify tables in FROM statements or JOINs, you can add a short name. Doing so allows use to specify which table you want to select the column from. This is very important when there are columns in each table with the same name.
 
## Wrapping Things Up
In this tutorial, we’ve covered the key components of SQL, from fundamental queries to practical applications in reporting and data cleaning. With a solid grasp of these concepts, you can effectively analyze data, generate insightful reports, and ensure data quality.
As you continue to develop your SQL skills, consider exploring more advanced topics such as window functions and CTEs! These areas can enhance your data manipulation capabilities and make you more proficient in handling complex datasets.

Now it’s your turn to apply what you've learned. Experiment with your own queries and datasets to deepen your understanding! The more you practice, the more confident you'll become in your SQL abilities.
