Hirdesh Bhardwaj

# Query:

```
```sql
Select * from users inner join rec on users.uid=rec.uid;
```
```

# LEFT OUTER JOIN:

MYSQL LEFT OUTER JOIN returns all rows from the LEFT hand table specified in the ON condition and only those rows from the other table where the joined fields are equal.

![](bbox=[0.12, 0.42, 0.38, 0.57])

This would return all rows from the users table and only those rows from the rec table where the joined fields are equal.

# Query:

```
```sql
Select * from users left join rec on users.uid=rec.uid;
```
```

# RIGHT OUTER JOIN

MYSQL RIGHT OUTER JOIN returns all rows from the RIGHT hand table specified in the ON condition and only those rows from the other table where the joined fields are equal.

![](bbox=[0.12, 0.93, 0.38, 0.99])