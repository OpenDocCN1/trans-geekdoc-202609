```
product_name
FROM my_table
ORDER BY product_name;
```

This query retrieves data from the columns product_id and product_name across all rows of the table, sorting by product_name. In the sections that follow, we will review illustrations of SQL commands in action, along with detailed explanations. Note that different relational database systems may use different extensions, and the syntax may differ slightly. Additionally, when using an API in Python, the API will have its own conventions. We will see this in the next section.

# Practical Matters

As a data scientist, it is extremely important to build skill in SQL since data manipulation is a large part of the job. Many companies include technical interviews where they expect to write correct SQL code to manage data. The way to get good at SQL is to practice on challenging code examples, breaking them down until they seem obvious. For students discouraged by a complex query, it can be helpful to take a step back and strategize on how to deconstruct it into subproblems. Then the subproblems can be pieced back together.

All SQL should be stored and versioned, as it is code. For example, the commands to build the tables and insert the data might be saved in files on GitHub. This allows stakeholders to understand what was done, and to replicate the work if needed.

Enough background info, now let's get to work! In the next section, we will use SQLite. We will walk through creating a database and interacting with it using Python. Specifically, we will write and execute SQL in Python to do these:

+   - Create a table
- Insert records into the table
- Query the data

# 7.3 Music Query: Single Table

In this section, we will learn and apply SQL on a single table of music artist data. We will begin by downloading and installing SQLite. Then we will launch