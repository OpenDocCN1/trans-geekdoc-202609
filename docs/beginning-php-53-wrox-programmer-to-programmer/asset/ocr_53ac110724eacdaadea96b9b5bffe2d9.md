# Part III: Using PHP Practice

There's a lot of repetition of the name accessLog members in this query. Fortunately, SQL lets
y create short table aliases by specifying an alias each table name in the FROM clause. You can
use those aliases to refer to the tables, rather than using the full table names each time:

```
mysql> SELECT DISTINCT al.memberId, m.firstName, m.lastName FROM accessLog
al, members m WHERE al.memberId = m.id;

| memberId | firstName | lastName |
|----------+-----------+----------|
| 1 | John | Sparks |
| 3 | Jo | Scrivener |
| 6 | Bill | Swan |

3 rows in set (0.00 sec)
```

You can also use the AS keyword to create aliases for the columns returned by your queries. Consider this
query that you looked at:

```
mysql> SELECT memberId, count( pageUrl ) FROM accessLog GROUP BY memberId;

| memberId | count( pageUrl ) |
|----------+--------------------|
| 1 | 1 |
| 3 | 2 |
| 6 | 1 |

3 rows in set (0.00 sec)
```

Notice that the second column in the result set is count( pageUrl ). Not only is this very
descriptive, but you'll find it awkward to refer to it in your PHP script. Therefore, it's a good idea to
rename it to something more meaningful:

```
mysql> SELECT memberId, count( pageUrl ) AS urlsView FROM accessLog GROUP
BY memberId;

| memberId | urlsView |
|----------|----------|
| 1 | 1 |
| 3 | 2 |
| 6 | 1 |

3 rows in set (0.00 sec)
```

# Other Useful MySQL Operators and Functions

MySQL contains a wealth of operators and functions that you can use to build more complex queries.
You've already used a few of these in this chapter. Here you will explore some other operators and
functions. Bear in mind that this is nowhere a complete list (you can find such a list in the MySQL
manual at http://dev.mysql.com/doc/).