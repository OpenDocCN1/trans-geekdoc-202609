# ROUND

This function returns the argument X, rounded to an integer, rounded to the specified number of decimal places (or zero places by default):

```
Round ROUND(X [,D])
RETURNS: int or float
```

ROUND returns the argument X rounded to a number with D decimals. If D is 0, or does not exist, the result will have no decimal point or fractional part.

```
mysql> select round(8.53), round(8.47), round(8.534,2);
+--------------+--------------+----------------+
| round(8.53)  | round(8.47)  | round(8.534,2) |
+--------------+--------------+----------------+
| 9            | 8            | 8.53           |
+--------------+--------------+----------------+
1 row in set (0.33 sec)
```

# TRUNCATE

TRUNCATE returns the number X truncated to D decimals. If D is 0, the result will have no decimal point or fractional part.

```
TRUNCATE(X,D)
RETURNS: decimal
```

```
mysql> select truncate(8.53,0), truncate(8.43,0), truncate(8.534,2);
+------------------+------------------+------------------+
| truncate(8.53,0) | truncate(8.43,0) | truncate(8.534,2) |
+------------------+------------------+------------------+
| 8                | 8                | 8.53             |
+------------------+------------------+------------------+
1 row in set (0.05 sec)
```

# EXP

This function returns the value of e (the base of natural logarithms) raised to the power of X:

```
EXP(X)
RETURNS: float
```