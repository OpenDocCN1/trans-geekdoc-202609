+   - [ ] Use joins to extract data from multiple tables
+   - [ ] Use various MySQL functions to further enhance the power of your queries

Along the way, you'll hone your skills using the MySQL command-line tool. Once you've finished reading these sections, you'll be well on your way to creating complex data-driven PHP applications.

# Limiting the Number of Rows Returned

You've already seen in the last chapter how to use a WHERE clause to limit the results of a query based on field values:

```
mysql> SELECT * from fruit WHERE name = 'banana';
+----+--------+-------+
| id | name   | color |
+----+--------+-------+
|  1 | banana | yellow|
+----+--------+-------+
1 row in set (0.08 sec)
```

As well as (or instead of) using a WHERE clause, you can set an upper limit on the number of returned rows by using the LIMIT keyword. For example, the following query returns the IDs and usernames for just the first four members in the members table:

```
mysql> SELECT id, username FROM members LIMIT 4;
+----+----------+
| id | username |
+----+----------+
|  1 | sparky   |
|  2 | mary     |
|  3 | jojo     |
|  4 | marty    |
+----+----------+
4 rows in set (0.00 sec)
```

The LIMIT clause always comes at the end of the query.

By default, LIMIT counts from the first row of the results. However, by including two numbers after the LIMIT keyword, separated by a comma, you can specify both the row from which to start returning results, as well as the number of results to return:

```
mysql> SELECT id, username FROM members LIMIT 1, 2;
+----+----------+
| id | username |
+----+----------+
|  2 | mary     |
|  3 | jojo     |
+----+----------+
2 rows in set (0.00 sec)
```

Notice that the start row counts from zero, so 1 is actually the second row (mary).