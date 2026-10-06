# Chapter 13: Retrieving Data from MySQL with PHP

Much like PHP, MySQL features various comparison operators that you can use to compare column values and other expressions in your queries. Here are some common ones:

| Comparison Operator | Description |
|---|---|
| = | equal to |
| <> | NULL-safe version of equal to |
| != = or < | not equal to |
| < | less than |
| > | greater than |
| <= | less than or equal to |
| >= | greater than or equal to |

Using a comparison operator results in a value of 1 (TRUE), 0 (FALSE), or NULL.

Most of these operators are self-explanatory. <> is useful if you think either of the values you're comparing might be NULL. Remember that NULL values propagate throughout an expression, so if any value in an expression is NULL, the result will also be NULL. This isn't very helpful when you're trying to compare two values. For example:

```
mysql> select 1 = 2;
+-------+
| 1 = 2 |
+-------+
|   0   |
+-------+
1 row in set (0.00 sec)

mysql> select 2 = 2;
+------+
| 2 = 2 |
+------+
|  1   |
+------+
1 row in set (0.00 sec)

mysql> select 1 = NULL;
+----------+
| 1 = NULL |
+----------+
|  NULL |
+----------+
1 row in set (0.00 sec)
```

383