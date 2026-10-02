Example:

```
```sql
SELECT * FROM customers
LIMIT 10;
```
```

In this example, we retrieve the first 10 records from the "customers" table.

# Section 6: Combining Conditions with AND and OR

You can combine multiple conditions in the WHERE clause using logical operators like AND and OR. This allows for more complex filtering criteria. Here's an example:

```
```sql
SELECT * FROM customers
WHERE city = 'New York' AND age > 30;
```
```