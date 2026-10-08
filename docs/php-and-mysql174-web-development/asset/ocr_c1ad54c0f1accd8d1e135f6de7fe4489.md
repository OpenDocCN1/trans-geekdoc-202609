As you declare the tables you are going to use, you add an AS clause to declare the alias for that table. You can also use aliases for columns; we return to this approach when we look at aggregate functions shortly.

You need to use table aliases when you want to join a table to itself. This task sounds more difficult and esoteric than it is. It is useful, for example, if you want to find rows in the same table that have values in common. When you want to find customers who live in the same city—perhaps to set up a reading group—can you give the same table (Customers) two different aliases:

```
SELECT C1.Name, C2.City
FROM Customers AS C1, Customers AS C2
WHERE C1.City = C2.City
AND C1.Name != C2.Name;
```

What you are basically doing is pretending the table Customers is two different tables, C1 and C2, and performing a join on the City column. Notice that you also need the second condition, C1.Name != C2.Name; this is to avoid each customer coming up with a match to herself.

# Summary of Joins

The different types of joins we have described are summarized in Table 10.2. There are a few others, but these are the main ones you will use.

| Table 10.2 Join Types in MySQL |
| Name | Description |
|---|--|
| Cartesian product | All combinations of all the rows in all the tables in the join. Used by specifying a comma between table names, and not specifying a WHERE clause. |
| Full join | Same as preceding. |
| Cross join | Same as above. Can also be used by specifying the CROSS JOIN keywords between the names of the tables joined. |
| Inner join | Semantically equivalent to the comma. Can also specified using the INNER JOIN keywords. Without a WHERE clause, equivalent to a full join. Usually, you specify a WHERE condition as well to make this a true inner join. |
| Equi-join | Uses a conditional expression with = to match rows from the different tables in the join. In SQL, this is a join with a WHERE clause. |
| Left join | Tries to match rows across tables and fills in nonmatching rows with NULLS. Use in SQL with the LEFT JOIN keywords. Used for finding missing values. You can equivalently use RIGHT JOIN. |