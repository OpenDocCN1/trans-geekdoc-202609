
# Part III: Using PHP in Practice

You can even sort by more than one column by separating the column names with:

```mysql
mysql> SELECT favoriteGenre, firstName, lastName FROM members ORDER BY
favoriteGenre, firstName;
+------------------------------------------------+
| favoriteGenre | firstName | lastName |
+------------------------------------------------+
| crime | Jane | Field |
| crime | John | Sparks |
| horror | Marty | Pareene |
| thriller | Mary | Newton |
| romance | Jo | Scrivener |
| scifi | Nick | Blakeley |
| nonFiction | Bill | Swan |
+------------------------------------------------+
7 rows in set (0.00 sec)
```

You can read this ORDER BY clause as: "Sort the results by favoriteGenre, then by firstName." Notice how the results are ordered by genre, but where the genre is "crime", the results are sorted by firstName "Jane" "John".

By default, MySQL sorts columns in ascending order. If you want to sort in descending order, add the keyword DESC after a field name. To avoid ambiguity, you can also add ASC after a field name to explicitly sort in order:

```mysql
mysql> SELECT favoriteGenre, firstName, lastName FROM members ORDER BY
favoriteGenre DESC, firstName ASC;
+------------------------------------------------+
| favoriteGenre | firstName | lastName |
+------------------------------------------------+
| nonFiction | Bill | Swan |
| scifi | Nick | Blakeley |
| romance | Jo | Scrivener |
| thriller | Mary | Newton |
| horror | Marty | Pareene |
| crime | Jane | Field |
| crime | John | Sparks |
+------------------------------------------------+
7 rows in set (0.00 sec)
```

Remember that ORDER works faster on a column that has an index, because indexes are already sorted in order.

# Using Pattern Matching for Flexible Queries

So far, all the WHERE clauses you've looked at have been fairly precise:

```mysql
SELECT * from fruit WHERE name = 'banana';
SELECT * from fruit WHERE id >= 2;
```

# Chapter 13: Retrieving Data from MySQL with PHP

Although this approach is good if you know the exact column values you're after, it's useful to be a bit less specific in your queries. For example, say you wanted to get a list of club members who travel among their interests. Each otherInterests field in the members table is free-form, consisting of a plain-English list of topics. How can you find out otherInterests fields contain the word "travel"?

The answer is to use the LIKE operator. This operator allows you to specify a string in the form of a pattern to search for, rather than an exact string:

```mysql
SELECT ... WHERE fieldName LIKE pattern;
```

Within the pattern string, you can include the following wildcard characters in addition to regular characters:

- % matches any number of characters (including no characters at all)
- _ matches exactly one character

So to retrieve a list of members that list travel as one of their interests, you could use:

```mysql
mysql> SELECT username, firstName, lastName, otherInterests FROM members
WHERE otherInterests LIKE '%travel%';
+----------------------------------------------------------------+
| username | firstName | lastName | otherInterests |
+----------+-----------+------------+--------------------------------+
| mary | Mary | Newton | Writing, hunting and travel |
| janefield | Field | Thai cookery, gardening, traveling | |
+----------+-----------+------------+--------------------------------+
2 rows in set (0.00 sec)
```

Notice MySQL has picked up both the word "travel" and the word "traveling". Both strings match the pattern "%travel%" (zero or more characters, followed by the word "travel", followed by zero or more characters).

By the way, there is no requirement to include the column that you're comparing — otherInterests in this case — this is only done so that you can see that members' interests include travel. The following SQL is equally valid:

```mysql
mysql> SELECT firstName FROM members WHERE firstName LIKE 'Mar_y';
```

You can use the (underscore) wildcard character to match a single character — for example:

```mysql
mysql> SELECT firstName, lastName FROM members WHERE firstName LIKE 'Mar_y';
+-----------+-----------+
| firstName | lastName |
+-----------+------------+
| Marty | Pareene |
+-----------+-----------+
1 row in set (0.03 sec)
```

Notice this query doesn't bring back Mary Newton's record because the underscore matches exactly one character, and there are no characters between the "r" and "y" of "Mary".

# Part III: Using PHP in Practice

You can reverse the sense of the comparison using NOT LIKE instead of LIKE. The following example displays a list of members who don't include travel in their interests:

```mysql
mysql SELECT username, firstName, lastName, otherInterests FROM members
WHERE otherInterests NOT LIKE '%travel%';
+-----------+-------------+------------+--------------------------------+
| username | firstName | lastName | otherInterests |
| sparky  | John      | Sparks     | Football, fishing and gardening |
| jojo    | Jo        | Parareen   | Genealogy, writing, painting |
| marty   | Marty     | Scrivener  | Guitar playing, rock music, clubbing |
| nickb   | Nick      | Blakeley  | Watching movies, cooking, socializing |
| bigbill | Bill      | Swan       | Tennis, judo, music |
+-----------+-------------+------------+--------------------------------+
5 rows in set (0.05 sec)
```

# Summarizing Data

Just as PHP has a large number of built-in functions, MySQL also gives you many functions to assist with your queries. In this section you will look at MySQL's aggregate functions. Rather than returning the actual data contained in a table, these functions let you summarize a table's data in different ways:

- count() — Returns the number of rows selected by the query
- sum() — Returns the total of all the values of a given field selected by the query
- min() — Returns the minimum value of all the values of a given field selected by the query
- max() — Returns the maximum value of all the values of a given field selected by the query
- avg() — Returns the average of all the values of a given field selected by the query

You can use count() in two different ways:

- count( fieldname ) — Returns the number of rows selected by the query where fieldname is NOT NULL
- count(*) — Returns the number of rows selected by the query, regardless of whether the rows contain any NULL values

Here are a couple of count() examples. The first example counts all the rows in the members table:

```mysql
mysql> SELECT COUNT(*) FROM members;
+-----------+
| COUNT(*) |
+-----------+
| 7        |
+-----------+
1 row in set (0.02 sec)
```

# Chapter 13: Retrieving Data from MySQL with PHP

This example, on the other hand, counts only the number of women in the members table:

```mysql
mysql> SELECT COUNT(*) FROM members WHERE gender = 'f';
+-----------+
| COUNT(*) |
+-----------+
|      3    |
+-----------+
1 row in set (0.00 sec)
```

Notice that in both cases the MySQL tool reports that there is only one row in the result set. Although the first example selects seven rows from the members table, the count() aggregate function takes those rows and returns a single value (7). The final result set contains only one row. Similarly, the second count() query reduces the three-row result to a value of 3.

The remaining aggregate functions work just as you'd expect. For example, this query returns the total number of visits to the club web site across all members:

```mysql
mysql> SELECT SUM( numVisits) FROM accessLog;
+-----------------------+
| SUM(numVisits) |
+-----------------------+
|          9      |
+-----------------------+
1 row in set (0.00 sec)
```

You can use functions like min() and max() on dates. This query returns the date that the first member joined the club:

```mysql
mysql> SELECT MIN( joinDate ) FROM members;
+----------------------+
| MIN(joinDate)|
+----------------------+
| 2006-03-03 |
+----------------------+
1 row in set (0.02 sec)
```

# Eliminating Duplicate Results

Occasionally a query returns more data than you actually need, even using WHERE AND LIMIT clauses. Say your accessLog table contains the following data:

```mysql
mysql> SELECT * FROM accessLog;
+--------------------------------------+
| memberId | pageUrl    | numVisits | lastAccess |
+----------|-------------|------------|------------+
| 1 | diary.php   | 2 | 2008-11-03 14:12:38 |
| 3 | books.php   | 2 | 2008-11-08 19:47:34 |
| 3 | contact.php | 1 | 2008-11-08 14:52:12 |
| 6 | books.php   | 4 | 2008-11-09 11:32:44 |
+------------------------------------------------------+
