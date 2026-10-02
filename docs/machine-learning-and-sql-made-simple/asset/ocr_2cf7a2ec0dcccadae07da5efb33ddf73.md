```
```sql
SELECT * FROM customers
ORDER BY last_name ASC, first_name ASC;
```
```

In this example, we retrieve all records from the "customers" table and sort them in ascending order based on the "last_name" column. For records with the same "last_name," we sort them in ascending order based on the "first_name" column.

# Section 5: Limiting Results with LIMIT

The LIMIT clause allows you to restrict the number of rows returned in the result set. This is useful when dealing with large datasets or when you only need a specific number of records. Here's the syntax:

```
```sql
SELECT column1, column2, ...
FROM table_name
LIMIT count;
```
```