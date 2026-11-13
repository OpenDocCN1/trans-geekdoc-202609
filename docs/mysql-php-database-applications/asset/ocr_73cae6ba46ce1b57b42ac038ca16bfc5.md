# MOD

Modulo is like the % operator in C. It returns the remainder of N divided by M:

```
MOD(N,M) or N % M
RETURNS: int
```

```
mysql> select mod(10,3), mod(10,4);
+-------------+-------------+
| mod(10,3) | mod(10,4) |
+-------------+-------------+
| 1 | 2 |
+-------------+-------------+
1 row in set (0.05 sec)
```

# FLOOR

This function returns the largest integer value not greater than X:

```
FLOOR(X)
RETURNS: int
```

```
mysql> select floor(8.5);
+-------------+
| floor(8.5) |
+-------------+
| 8 |
+-------------+
1 row in set (0.00 sec)
```

# CEILING

This function returns the smallest integer value not less than X:

```
CEILING(X)
RETURNS: int
```

```
mysql> select ceiling(8.5);
+---------------+
| ceiling(8.5) |
+---------------+
| 9 |
+---------------+
1 row in set (0.00 sec)
```