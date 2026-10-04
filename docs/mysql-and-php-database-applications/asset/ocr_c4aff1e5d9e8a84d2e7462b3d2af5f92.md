# TRUNCATE

TRUNCATE returns the number X, truncated to D decimals. If D is 0, the result will have no maine decimal point or fractional part.

```
TRUNCATE(X,D)
RETURNS: decimal
```

Example:

```
mysql> select truncate(8.53,0), truncate(8.43,0), truncate(8.534,2);
+----------------+----------------+----------------+
| truncate(8.53,0) | truncate(8.43,0) | truncate(8.534,2) |
+----------------+----------------+----------------+
|                 8                |                 8                |                8.53             |
+----------------+----------------+----------------+
1 row in set (0.05 sec)
```

# EXP

This function returns the value of e (the base of natural logarithms) raised to the power of X.

```
EXP(X)
RETURNS: float
```

# LOG

This function returns the natural logarithm of X. If you want the log of a number X to some arbitrary base B, use the formula LOG(X)/LOG(B).

```
LOG(X)
RETURNS: float
```

# LOG10

LOG10 returns the base-10 logarithm of X.

```
LOG10(X)
RETURNS: float
```