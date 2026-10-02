```
```sql
SELECT * FROM products
WHERE category = 'Electronics' AND price < 1000;
```
```

In this example, we retrieve all records from the "products" table where the "category" column is 'Electronics' and the "price" column is less than 1000.

# Section 3: Wildcard Operators

Wildcard operators are used to match patterns within text or string values. They are particularly useful when you want to search for values that partially match a given pattern. The commonly used wildcard operators are:

+   - %: Matches any sequence of characters (zero or more).
- _: Matches any single character.

Example:

```
```sql
SELECT * FROM customers
```
```