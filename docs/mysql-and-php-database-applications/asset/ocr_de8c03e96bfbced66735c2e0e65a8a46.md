# Appendix I: MySQL Function Reference

# SECOND

This function returns the second for time, in the range 0 to 59.

```
SECOND(time)
RETURNS: int
```

# PERIOD_ADD

This function adds N months to P (in the format YYMM or YYYYMM) and returns a value in the format YYYYMM.

```
PERIOD_ADD(P,N)
RETURNS: int
```

Note that the period argument P is not a date value.

```
mysql> select period_add('200006','7');
+\| period_add('200006','7') |
+\| |
+| 200101 |
+\| |
+\|
1 row in set (0.00)
```

# PERIOD_DIFF

This function returns the number of months between periods P1 and P2. should be in the format YYMM or YYYYMM.

```
PERIOD_DIFF(P1,P2)
RETURNS: int
```

Note that the period arguments P1 and P2 are not date values.

```
mysql> select period_diff('200106','200001');
+\| period_diff('200106','200001') |
+\| |
+| 17 |
+\| |
+\|
1 row in set (0.00)
```