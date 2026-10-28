# # How to select data from multiple tables

Figure 3-5 shows how to use the SELECT statement to retrieve data from two tables. This is commonly known as a *join*. The result of any join is a single table.

An *inner join* is the most common type of join. When you use one, the data from the rows in the two tables are included in the result set only if their related columns match. In this figure, for example, the SELECT statement joins the data from the rows in the products and categories tables only if the value of the categoryID column in the products table is equal to the categoryID column in the categories table. In other words, if there isn’t any data in the products table for a category, that category won’t be added to the result set.

To code an inner join, you use the JOIN clause to specify the second table and the ON clause to specify the columns to be used for the join. If a column in one table has the same name as a column in the other table, you can code the table name, a dot, and the column name to specify the column that you want to use. This is illustrated by the ON clause in this figure.

Although this figure only shows how to join data from two tables, you can extend this syntax to join data from additional tables. For example, let’s say you want to create a result set that includes data from three tables named categories, products, and orderitems. In that case, you can code the FROM clause of the SELECT statement like this:

```
FROM categories
    INNER JOIN products
        ON categories.categoryID = products.categoryID
    INNER JOIN orderitems
        ON products.productID = orderitems.productID
```

Then, you can include any of the columns from the three tables in the column list of the SELECT statement.

Another type of join is an *outer join*. With this type of join, all of the rows in one of the tables are included in the result set whether or not there are matching rows in the other table. This can be useful when you need to see all the records in a table regardless of whether they have a match in the other table. This kind of query can also be helpful in identifying missing data.

In a *left outer join*, all of the rows in the first table (the one on the left) are included in the result set. In a *right outer join*, all of the rows in the second table are included.

To illustrate, suppose that a SELECT statement uses a left outer join to join the rows in a categories table with the rows in a products table. In that case, all of the rows in the categories table would be included in the result set... even if some of the rows in the categories table don’t have any matching rows in the products table.