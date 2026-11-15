By using the null-safe operator <=>, you ensure that any NULL value isn't propagated through to the result:

```
mysql> select 1 <=> 2;
+-----------+
| 1 <=> 2   |
+-----------+
|         0 |
+-----------+
1 row in set (0.00 sec)
```

```
mysql> select 1 <=> NULL;
+-------------+
| 1 <=> NULL  |
+-------------+
|           0 |
+-------------+
1 row in set (0.00 sec)
```

```
mysql> select NULL <=> NULL;
+-----------------+
| NULL <=> NULL   |
+-----------------+
|               1 |
+-----------------+
1 row in set (0.00 sec)
```

You can also use the Boolean operators AND, OR, and NOT to build more complex expressions. For example:

```
mysql> SELECT * FROM accessLog WHERE lastAccess > '2008-11-04' AND lastAccess < '2008-11-09';
+-----------+------------+-----------+---------------------+
| memberId  | pageUrl    | numVisits | lastAccess          |
+-----------+------------+-----------+---------------------+
|         3 | books.php  |         2 | 2008-11-08 19:47:34 |
|         3 | contact.php|         1 | 2008-11-08 14:52:12 |
+-----------+------------+-----------+---------------------+
```

MySQL's functions can be broken down into many categories. For example, there are many date and time functions, such as now(), that retrieves the current date and time (useful when comparing dates and times against the current moment). You can also use curdate() to retrieve just the date portion of now(), and curtime() to get just the time portion:

```
mysql> SELECT now(), curdate(), curtime();
+---------------------+------------+----------+
| now()               | curdate()  | curtime() |
+---------------------+------------+----------+
| 2008-11-09 12:17:08 | 2008-11-09 | 12:17:08 |
+---------------------+------------+----------+
1 row in set (0.08 sec)
```