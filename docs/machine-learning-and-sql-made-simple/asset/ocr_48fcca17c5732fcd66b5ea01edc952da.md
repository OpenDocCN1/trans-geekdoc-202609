# Section 5: NULL Values

In SQL, NULL represents missing or unknown data. When dealing with NULL values, special operators are used:

+   - IS NULL: Matches NULL values.
- IS NOT NULL: Matches non-NULL values.

Example:

```
```sql
SELECT * FROM employees
WHERE department IS NULL;
```
```

In this example, we retrieve all records from the "employees" table where the "department" column contains NULL values.