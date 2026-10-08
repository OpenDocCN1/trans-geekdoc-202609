
('0-672-31769-9', 'Thomas Schenk',
'Caldera OpenLinux System Administration Unleashed', 49.99);

```sql
INSERT INTO Orders VALUES
(NULL, 3, 69.98, '2007-04-02'),
(NULL, 1, 49.99, '2007-04-15'),
(NULL, 2, 74.98, '2007-04-19'),
(NULL, 3, 24.99, '2007-05-01');
```

```sql
INSERT INTO OrderItems VALUES
(1, '0-672-31697-8', 2),
(2, '0-672-31769-9', 1),
(3, '0-672-31769-9', 1),
(3, '0-672-31509-2', 1),
(4, '0-672-31745-1', 3);
```

```sql
INSERT INTO Book_Reviews VALUES
('0-672-31697-8', 'The Morgan is clearly written and goes well beyond
most of the basic Java books out there.');
```

You can run this script from the command by piping it through MySQL as follows:

```bash
mysql -h host -u bookorama -p books < /path/to/book_insert.sql
```

# Retrieving Data from the Database

The workhorse of SQL is the SELECT statement. It's used to retrieve data from a database by selecting rows that match criteria from a table. There are lot of options and different ways to use the SELECT statement.

The basic form of a SELECT is

```sql
SELECT [options] items
[INTO file_details]
FROM [tables]
[PARTITION partitions]
[WHERE conditions ]
[ GROUP BY group_type ]
[ HAVING where_definition ]
[ORDER BY order_type ]
[LIMIT limit_criteria ]
[PROCEDURE proc_name(arguments)]
[INTO destination]
[options]
```

In the following sections, we describe each of the clauses of the statement. First, though, let's look at a query without any of the optional clauses, one selects some items from a particular table. Typically, these items are columns from the table. (They can also be the results of any MySQL expressions. We discuss some of the more useful ones in a later section.) This query lists the contents of the Name and City columns from the Customers table:

```sql
SELECT Name, City
FROM Customers;
```

This query has the following output, assuming that you've entered the sample data from Listing 10.1:

| Name | City |
|---|---|
| Julie Smith | Airport West |
| Alan Wong | Box Hill |
| Michelle Arthur | Yarrraville |

3 rows in set (0.00 sec)

As you can see, this table contains the items selected—Name and City—from the table specific-Customers. This data is shown for all the rows in the Customers table.

You can specify as many columns as you like from a table by listing them after the SELECT keyword. You can also specify some other items. One useful item is the wildcard operator, which matches all the columns in the specified table or tables. For example, to retrieve all columns and all rows from the Order_Items table, you would use

```sql
SELECT *
FROM Order_Items;
```

which gives the following output:

| ObjectID | ISBN | Quantity |
|---|---|---|
| 1 | 0-672-31697-8 | 2 |
| 2 | 0-672-31769-9 | 1 |
| 3 | 0-672-31509-2 | 1 |
| 3 | 0-672-31769-9 | 1 |
| 4 | 0-672-31745-1 | 1 |

5 rows in set (0.00 sec)

# Retrieving Data with Specific Criteria

To access some of the rows in a table, you need to specify some selection criteria. You can do this with a WHERE clause. For example,

```sql
SELECT *
FROM Orders
WHERE CustomerID = 3;
```

selects all the columns from the Orders table, but only the rows with a CustomerID of 3. Here's the output:

| OrderID | CustomerID | Amount | Date |
|------|---|---|---|
| 1 | 3 | 69.98 | 2007-04-02 |
| 4 | 3 | 24.99 | 2007-05-01 |

2 rows in set (0.02 sec)

The WHERE clause specifies the criteria used to select rows. In this case, we selected rows with a CustomerID of 3. The single equal sign is used to test equality; note that this is different from PHP, and you can easily become confused when you're using them.

In addition, MySQL supports a full set of operators and regular expressions. The ones you will most commonly use WHERE clauses are listed in Table 10.1. Note that this list is not complete; if you need something else, check the MySQL manual.

# Table 10.1 Useful Comparison Operators for WHERE Clauses

| Operator | Name (If Applicable) | Example | Description |
|---|---|---|---|
| = | Equality | customerid = 3 | Tests whether two values are equal |
| > | Greater than | amount > 60.00 | Tests whether one value is greater than another |
| < | Less than | amount < 60.00 | Tests whether one value is less than another |
| >= | Greater than or equal to | amount >= 60.00 | Tests whether one value is greater than equal to another |
| <= | Less than or equal to | amount <= 60.00 | Tests whether one value is less than equal to another |
| != or <> | Not equal | quantity != 0 | Tests whether two values are not equal |
| IS NOT NULL | n/a | address is not null | Tests whether a field actually contains a value |
| IS NULL | n/a | address is null | Tests whether a field does not contain a value |
| BETWEEN | n/a | amount between 0 and 60 | Tests whether a value is greater than equal to a minimum value and less than a maximum value |
| IN | n/a | city in ("Carlton", "Moe") | Tests whether a value is in a particular set |
| NOT IN | n/a | city not in ("Carlton", "Moe") | Tests whether a value is not in a set |
| LIKE | Pattern match | name like ("Fred %") | Checks whether a value matches using simple matching |
| NOT LIKE | Pattern match | name not like ("Fred %") | Checks whether a value doesn't match a pattern |
| REGEXP | Regular expression | name regex | Checks whether a value matches a regular expression |

The REGEXP keyword is used for regular expression matching. MySQL uses POSIX regular expressions. Instead of using REGEXP, you can use LIKE, which is a synonym. The syntax for regular expressions is a little different from the PCRE used in PHP (PHP used to support POSIX-style regular expressions, but they have been deprecated). You can test multiple criteria using the simple operators and the pattern matching syntax and combine them into complex criteria with AND and OR. For example:

```sql
SELECT *
FROM Orders
WHERE CustomerID = 3 OR CustomerID = 4;
```

# Retrieving Data from Multiple Tables

Often, to answer a question from the database, you need to use more data than one table. For example, if you wanted to know which customers ordered, you would need to look at the Customers table and the Orders table. If you also wanted to know what they ordered, you would also need to look at the Order_Items table.

These items are in separate tables because they relate to real-world objects. This is one of the principles of good database design that we described in Chapter 8, "Designing Your Database."

To put this information together in SQL, you must perform an operation called a join. This simply joins two or more tables to follow the relationships between the data. For example, if you want to see the orders that customer Julie Smith has placed, you will need to look at the Customers table to find Julie's CustomerID and then at the Orders table for orders with CustomerID.

Although joins are conceptually simple, they are one of the most subtle and complex parts of SQL. Several different types of joins are implemented in MySQL, and each is used for a different purpose.

# Simple Two-Table Joins

Let's begin by looking at some SQL for the query about Julie Smith we just discussed:

```sql
SELECT Orders.OrderID, Orders.Amount, Orders.Date
FROM Customers, Orders
WHERE Customers.Name = 'Julie Smith' and Customers.CustomerID = Orders.CustomerID;
```

The output of this query is:

| OrderID | Amount | Date |
|---|---|---|
| 2 | 49.99 | 2007-04-15 |

1 row in set (0.02 sec)

There are a few things to notice here. First, because information from two tables is needed to answer your query, you must list both tables.

By listing two tables, you also specify a type of join, possibly without knowing it. The comma between the names of the tables is equivalent to typing INNER JOIN or CROSS JOIN. This is a type of join also referred as a full join, or the Cartesian product of the tables. It means, “take the tables, and make one big table. The big table should have a row for each possible combination of rows from each of the tables, whether that makes sense or not.” In other words, you will get every row from the customers table matched up with every row from the Orders table, regardless of whether a particular customer placed a particular order.

Brute-force doesn't make a lot of sense in most cases. Often what you want to see the rows that really do match—that is, the orders by a particular customer matched up with that customer.

You achieve this result by placing a join condition in the WHERE clause. This special type of conditional statement explains which attributes show the relationship between the two tables. In this case, the join condition is

```sql
Customers.CustomerID = Orders.CustomerID
```

which tells MySQL to pull rows in the result only if the CustomerID from the Customers table matches the CustomerID from the Orders table.
