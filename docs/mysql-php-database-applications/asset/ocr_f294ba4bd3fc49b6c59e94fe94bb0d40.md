```
+----------------------------------+
1 row in set (0.00 sec)

mysql> select NULLIF('jay', 'jack');
+-----------------------+
| NULLIF('jay', 'jack') |
+-----------------------+
| jay                   |
+-----------------------+
1 row in set (0.00 sec)
```

# Mathematical Functions

You can see the most current list of MySQL's math functions at http://www.mysql.com/doc/M/a/Mathematical_functions.html. All mathematical functions return NULL in case of an error.

# ABS

This function returns the absolute value of X:

```
ABS(X)
RETURNS: type of X
```

```
mysql> select abs(22), abs(-22);
+----------+-----------+
| abs(22)  | abs(-22)  |
+----------+-----------+
| 22       | 22        |
+----------+-----------+
```

# SIGN

This function returns the sign of the argument as -1, 0, or 1, depending on whether X is negative, 0, or positive:

```
SIGN(X)RETURNS: intmysql> select sign(10), sign(-10), sign(0);
```

```
+----------+-----------+----------+
| sign(10) | sign(-10) | sign(0)  |
+----------+-----------+----------+
| 1        | -1        | 0        |
+----------+-----------+----------+
1 row in set (0.00 sec)
```