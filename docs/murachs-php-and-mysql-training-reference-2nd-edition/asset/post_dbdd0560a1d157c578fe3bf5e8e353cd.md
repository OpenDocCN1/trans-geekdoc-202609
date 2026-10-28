
## How to use an alias for a column

By default, MySQL gives a column in a result set the same name as the column in the base table. You can specify a different name, however, whenever necessary. When you do that, the new column name is known as a *column alias*. Figure 18-2 presents two techniques for creating column aliases.

The first technique is to code the column specification followed by the AS keyword and the column alias. This is the coding technique specified by the American National Standards Institute (ANSI, pronounced ‘ann-see’), and it’s illustrated by the first example in this figure.

The second technique is to code the column specification followed by a space and the column alias, as illustrated by the second example. However, it’s better to use the first technique since the AS keyword makes it easier to identify the alias for the column, which makes your SQL statement easier to read and maintain.

When you code an alias, you must enclose the alias in double quotes if the alias contains a space or is a keyword that’s reserved by MySQL. In this figure, the third example specifies an alias for the listPrice column that uses two words with a space between them.

When you specify an alias, the result set uses the exact capitalization that you specify. As a result, you should be sure to specify the capitalization that you want.

When you code a column that contains a calculated value, it’s a good practice to specify an alias for the calculated column. If you don’t, MySQL assigns the entire calculation as the name, which can be unwieldy. You’ll learn more about calculated values later in this chapter.

### Use the AS keyword to specify an alias

```sql
SELECT productID, productName AS name, listPrice AS price
FROM products
WHERE listPrice < 450
ORDER BY listPrice
```

| productID | name | price |
| ---: | --- | ---: |
| 5 | Washburn D10S | 299.00 |
| 6 | Rodriguez Caballero 11 | 415.00 |

### Omit the AS keyword

```sql
SELECT productID, productName name, listPrice price
FROM products
WHERE listPrice < 450
ORDER BY listPrice
```

| productID | name | price |
| ---: | --- | ---: |
| 5 | Washburn D10S | 299.00 |
| 6 | Rodriguez Caballero 11 | 415.00 |

### Use quotes to include spaces

```sql
SELECT productID AS "ID", productName AS "Product Name",
       listPrice AS "Price"
FROM products
WHERE listPrice < 450
ORDER BY listPrice
```

| ID | Product Name | Price |
| ---: | --- | ---: |
| 5 | Washburn D10S | 299.00 |
| 6 | Rodriguez Caballero 11 | 415.00 |

### Description

- By default, a column in the result set is given the same name as the column in the base table. If that’s not what you want, you can specify a *column alias* for the column.
- One way to name a column is to use the AS keyword as shown in the first example above. Although the AS keyword is optional, it enhances readability.
- When you enclose an alias in quotes, you can use spaces within the column name.

Figure 18-2  How to use an alias for a column

## How to select rows with a LIMIT clause

In the database for this chapter, each table has a small number of rows. As a result, you don’t need to limit the number of rows that your SELECT statements retrieve from this database. With a production database, however, it’s common for a table to have thousands or even millions of rows. Then, you don’t want to accidentally retrieve hundreds or thousands of rows.

One way to limit the number of rows that a SELECT statement retrieves is to code a LIMIT clause at the end of the statement as shown in figure 18-3. The easiest way to do that is to code the LIMIT keyword followed by the number of rows as shown in the first example. This retrieves the same rows as coding the LIMIT keyword followed by a row offset of 0, a comma, and the number of rows to retrieve as shown in the second example.

However, if you don’t want to begin retrieving rows starting at the first row, you can specify another offset. In this figure, for example, the third statement specifies an offset of 1 to begin retrieving rows at the second row. To begin retrieving rows at the third row, specify an offset of 2. To begin at the fourth row, specify an offset of 3. And so on.

By default, phpMyAdmin automatically adds a LIMIT clause to most SELECT statements so they only retrieve the first 30 rows of a table. This is usually what you want since it prevents you from accidentally retrieving thousands of rows from a database. However, if you want to use phpMyAdmin to view more than 30 rows, you can override this default setting by coding your own LIMIT clause.

### The syntax of the LIMIT clause

```
LIMIT [rowOffset, ] maxRows
```

### Retrieve the first three rows of the result set

```
SELECT productID, productName
FROM products
LIMIT 3
```

| productID | productName |
| ---: | --- |
| 1 | Fender Stratocaster |
| 2 | Gibson Les Paul |
| 3 | Gibson SG |

### Another way to retrieve the first three rows

```
SELECT productID, productName
FROM products
LIMIT 0, 3
```

| productID | productName |
| ---: | --- |
| 1 | Fender Stratocaster |
| 2 | Gibson Les Paul |
| 3 | Gibson SG |

### Retrieve three rows starting at the second row

```
SELECT productID, productName
FROM products
LIMIT 1, 3
```

| productID | productName |
| ---: | --- |
| 2 | Gibson Les Paul |
| 3 | Gibson SG |
| 1 | Yamaha FG700S |

### Description

- You can use the LIMIT clause to limit the number of rows that are included in the result set.

Figure 18-3 — How to select rows with a LIMIT clause

## How to select rows with a WHERE clause

Another way to limit the number of rows that a SELECT statement retrieves is to code a WHERE clause. When you do that, you often use the comparison operators shown in figure 18-4. If the result of the comparison is TRUE for a row, MySQL includes the row in the result set.

The examples in this figure show how to use some of the comparison operators. For instance, the first WHERE clause uses the equal operator (=) to retrieve only those rows with a categoryID column that has a value of 2. Since the category ID is a numeric literal, it doesn’t need to be enclosed in quotes, although it’s okay to enclose it in quotes. In contrast, a string literal like the one in the second WHERE clause must be enclosed in quotes.

The third WHERE clause uses the less than (<) operator to retrieve only those rows that have a list price that’s less than 499.99. Then, the fourth example uses the greater than or equal to (>=) operator to retrieve those rows that have a list price that’s greater than or equal to 499.99.

The fifth WHERE clause illustrates how you can use comparison operators other than the equal operator with string data. In this example, the less than (<) operator is used to compare the value of the productName column to a string literal that has the letter G in the first position. That causes the query to return all product names that begin with the letters A through F.

You can also use the comparison operators with date literals, as illustrated by the sixth and seventh clauses. The sixth clause retrieves rows that were added before January 31, 2014, and the seventh clause retrieves rows that were added on or after January 31, 2014. Like string literals, date literals must be enclosed in single quotes. MySQL also expects date literals to use this format: yyyy-mm-dd.

When you code a date literal, MySQL adds a default time of 00:00:00, which is the start of the day. As a result, if you’re working with a date/time value that includes a time component, you need to take this into account. If necessary, you can code a date literal that includes a time component. For example, you can code a time component for 4:30pm and 10 seconds like this:

```sql
'2014-10-30 16:30:10'
```

Note that the time component uses a 24 hour clock where 16 hours is 4pm.

The eighth WHERE clause shows how you can test for a not equal condition. To do that, you code a less than (<) sign followed by a greater than (>) sign. In this example, the WHERE clause only retrieves rows with a discount percent that’s not equal to 30.

Whenever possible, you should compare expressions that have similar data types. If you attempt to compare expressions that have different data types, MySQL may implicitly convert the data types for you. Although implicit conversions are often acceptable, they occasionally yield unexpected results.
