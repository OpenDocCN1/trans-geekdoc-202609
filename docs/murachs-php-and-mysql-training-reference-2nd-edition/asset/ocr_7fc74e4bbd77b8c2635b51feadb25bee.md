# The syntax for a SELECT statement that gets all columns

```
SELECT *
FROM table-1
[WHERE selection-criteria]
[ORDER BY column-1 [ASC|DESC] [, column-2 [ASC|DESC] ...]]
```

# A SELECT statement that gets all columns

```
SELECT * FROM products
WHERE categoryID = 2
```

| productID | categoryID | productCode | productName       | listPrice |
|---:|---:|---|---|---:|
| 7 | 2 | precision | Fender Precision | 799.99 |
| 8 | 2 | hofner | Hofner Icon | 499.99 |

# The syntax for a SELECT statement that gets selected columns

```
SELECT column-1 [, column-2] ...
FROM table-1
[WHERE selection-criteria]
[ORDER BY column-1 [ASC|DESC] [, column-2 [ASC|DESC] ...]]
```

# A SELECT statement that gets selected columns and rows

```
SELECT productName, listPrice
FROM products
WHERE listPrice < 500
ORDER BY listPrice ASC
```

| productName | listPrice |
|---|---:|
| Washburn D10S | 299.00 |
| Rodriguez Caballero 11 | 415.00 |
| Yamaha FG700S | 489.99 |
| Hofner Icon | 499.99 |

# Description

+   - A SELECT statement is a SQL statement that returns a *result set* (or *result table*) that consists of the specified rows and columns.
+   - To specify the columns, you use the SELECT clause.
+   - To specify the table that the data should be retrieved from, you use the FROM clause.
+   - To specify rows, you use the WHERE clause.
+   - To specify how the result set should be sorted, you use the ORDER BY clause.

Figure 3-4 — How to select data from a single table