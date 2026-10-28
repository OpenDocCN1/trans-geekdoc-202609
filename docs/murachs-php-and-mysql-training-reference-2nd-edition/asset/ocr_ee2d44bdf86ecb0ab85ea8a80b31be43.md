# How to select data from multiple tables

Now that you know how to select data from a single table, you’re ready to learn how to select data from multiple tables. To do that, you code a join. A *join* lets you combine columns from two or more tables into a single result set. This topic shows how to use the most common type of join, an *inner join*.

MySQL also provides an outer join that you can use to retrieve all rows from the tables involved in the join, whether or not the join condition is TRUE. However, since outer joins aren’t used in the web applications described in this book, they aren’t presented in this chapter.

# How to code an inner join

Figure 18-9 presents the *explicit syntax* for coding an inner join. To use this syntax, you code the names of the two tables in the FROM clause along with the optional INNER keyword, the required JOIN keyword, and an ON phrase that specifies the *join condition*. The join condition indicates how the two tables should be compared. In most cases, they’re compared based on the relationship between the primary key of the first table and a foreign key of the second table.

The SELECT statement in this figure, for example, joins data from the customers and orders tables based on the customerID column in each table. Since this join condition uses the equals (=) operator, the value of the customerID column in a row in the customers table must match the customerID in a row in the orders table for that row to be included in the result set. In other words, only customers with one or more orders are included.

In this example, the customers table is joined with the orders table using a column that has the same name in both tables: customerID. Because of that, the columns must be qualified to indicate which table they come from. To do that, you can code a *qualified column name* by entering the table name and a period in front of the column name. Although this example uses qualified column names only in the join condition, you must qualify a column name anywhere it appears in the statement if the same name occurs in both tables. If you don’t, MySQL returns an error indicating that the column name is ambiguous. Of course, you can also qualify column names that aren’t ambiguous. However, we recommend you do that only if it clarifies your code.

MySQL also provides an *implicit syntax* that you can use to code inner joins. To do that, you can code a list of tables in the FROM clause and the join condition in the WHERE clause. However, there are several advantages to using the explicit syntax, so the implicit syntax is not presented in this book.