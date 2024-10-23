---
layout: post
title:  "Learning SQL"
author: Kolby Taylor
description: Teaches the basics of SQL, a programming language used to gather and organize data.   
image: "/assets/images/sql_background.avif"


---

## An Underrated Tool
When I first started working with data, I was overwhelmed by the sheer amount of information at my fingertips, but I had no idea how to extract meaningful insights. That’s when I discovered SQL, and everything changed. Now, I can manipulate vast amounts of data with just a few lines of code.
All data scientists aspire to build complex models and uncover powerful analytical insights. However, without clean, well-structured data, these goals are impossible to achieve. SQL is the most used tool out there for cleaning and organizing data, and all aspiring data scientists should learn it.
According to a study conducted by RTInsights, almost 70% of data scientists use SQL regularly ([RTInsights](https://www.rtinsights.com/almost-70-of-data-scientists-use-sql-regularly/)), and it is often one of the first skills required in data science job postings. However, despite its importance, SQL remains undertaught in universities across the country. Today, I will provide a brief introduction to this powerful language and explain a few ways it can be utilized.
 
 
## Building A Query
Imagine working as an intern at a small paper supply company. Your boss, Michael, asks to build him a report about the company's clients. Your task is simple, give him a list of the companies ten biggest clients and he'll be happy. Don't worry, he doesn't too expect too much.


`!["You and Your Boss"]"/assets/images/michael_and_ryan.jpeg"`

Don't worry, your boss loves you. It's actually a little creepy, it seems like he's al

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
The FROM statement allows you to specify which table you are pulling the columns from. When the table you need is located inside a folder, you have to specify that in your FROM statement. Normally, folders and files are separated by a backslash, like this:

``` sql
FROM client_data/client_information
```

However, in SQL, this is incorrect. Instead, they should be separated with a period, like this:
``` sql
FROM client_data.client_information
```

WHERE
To filter your data based on certain conditions, you can use the WHERE clause. This is especially useful when you only want to see specific entries that meet certain criteria. In our example query, we only wanted to see our bigger clients, which is why we made sure we only kept rows with at least $1 Million in revenue and 10 employees. This helps you focus on specific groups of data, making it easier to analyze information that meets your requirements. To use more than one filter, you can simply use AND or OR.

ORDER BY
Finally, the ORDER BY clause allows you to sort your query results based on one or more columns. For example, if you want to see a list of employees sorted by their salary in descending order, this clause would help you achieve that. Sorting your results can be incredibly useful for identifying trends. In our example, we sorted by annual revenue from highest to lowest. The type of sorting that will occur depends on the data type of the column. If it is categorical, it will sort it alphabetically. Numbers are sorted from lowest to highest. Dates are ordered from oldest to newest. If you want to reverse the sorting order, you can use DESC.



## Wrapping Things Up
In this tutorial, we’ve covered the key components of SQL, from fundamental queries to practical applications in reporting and data cleaning. With a solid grasp of these concepts, you can effectively analyze data, generate insightful reports, and ensure data quality.
As you continue to develop your SQL skills, consider exploring more advanced topics such as window functions and CTEs! These areas can enhance your data manipulation capabilities and make you more proficient in handling complex datasets.

Now it’s your turn to apply what you've learned. Experiment with your own queries and datasets to deepen your understanding! The more you practice, the more confident you'll become in your SQL abilities.
