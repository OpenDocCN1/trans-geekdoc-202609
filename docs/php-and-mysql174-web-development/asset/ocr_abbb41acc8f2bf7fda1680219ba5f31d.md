# Correlated Subqueries

There is a special type of subqueries known as correlated subqueries. In these, you can use items
from the outer query to the inner query. For example,

```
SELECT ISBN, Title
FROM Books
WHERE EXISTS
(SELECT * FROM Order_Items WHERE Order_Items.ISBN = Books.ISBN);
```

This query illustrates the use of correlated subqueries and the use of the last special
subquery operator, EXISTS. It retrieves any books that have never been ordered. Note that the
inner query includes only the Order_Items table in the FROM list but refers to Books.ISBN.
in other words, the inner query refers to data in the outer query. This is the definition of a
correlated subquery: You are looking for inner rows that match (or in this case don't match) the
outer rows.

The EXISTS operator returns true if there are any matching rows in the subquery. Conversely,
NOT EXISTS returns true if there are no matching rows in the subquery.

# Row Subqueries

All the subqueries so far have returned a single value, although in many cases this value is true
or false (as with the preceding example using EXISTS). Row subqueries return an entire row,
which can be compared to rows in the outer query. This approach is generally used
to look for rows in one table also in another table. There is no good example of
in this books database, but a generalized example of the syntax could be something like
following:

```
SELECT c1, c2, c3
FROM t1
WHERE (c1, c2, c3) IN (SELECT c1, c2, c3 FROM t2);
```

# Using a Subquery as a Temporary Table

You can use a subquery in the FROM clause of an outer query. This approach effectively allows
to query the output of the subquery, treating it as a temporary table.

In its simplest form, this is something like

```
SELECT *
(SELECT CustomerID, Name FROM Customers WHERE City = 'Box Hill')
AS box_hill_customers;
```

Note that we put the subquery in the FROM clause here. Immediately after the subquery’s
closing parenthesis, you must give the results of the subquery an alias. You can then treat it as any
other table in the outer query.