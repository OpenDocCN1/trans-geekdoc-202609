
[content]

# REGEXP

This function performs a match of a string expression (expr) against a regular expression (pat). See Appendix C for a discussion of regular expressions. But be aware that MySQL does not support regular expressions to the extent you will find in PHP.

```
expr REGEXP pat
```

or

```
expr RLIKE pat
RETURNS: int
```

REGEXP returns 1 (true) if the pattern is found or 0 (false) if not.

```
mysql> select name from guestbook where name regexp '^aj.*g*':
+----------------+
| name           |
+----------------+
| Jay Greenspan  |
| Jay Green      |
+----------------+
2 rows in set (0.00 sec)
```

mysql>

# STRCMP

STRCMP(expr1,expr2) (used in examples)
RETURNS: int

0 if the strings are the same, -1 if the first argument is smaller than the second, and 1 if the second argument is smaller than the first.

```
mysql> select strcmp('foo', 'bar');
+--------------------+
| strcmp('foo', 'bar') |
+--------------------+
|                    1 |
+--------------------+
1 row in set (0.11 sec)
```

```
mysql> select strcmp('bar', 'bar');
+----------------------+
| strcmp('bar', 'bar') |
+----------------------+
|                    0 |
+----------------------+
1 row in set (0.00 sec)

mysql> select strcmp('bar', 'foo');
+----------------------+
| strcmp('bar', 'foo') |
+----------------------+
|                   -1 |
+----------------------+
1 row in set (0.00 sec)

mysql>
```

# Appendix I: MySQL Function Reference

## Cast Operators

There is only one cast operator you will encounter in MySQL.

## Binary

BINARY
RETURNS: 1

The BINARY operator casts the string following it to a binary string. This is an easy way to force a column comparison to be case-sensitive even if the column isn't defined as BINARY or BLOB. BINARY was introduced in MySQL 3.23.0.

```
mysql> select binary('Foo') = 'foo', binary('Foo') = 'Foo';
+--------------------------------------+
| binary('Foo') = 'foo' | binary('Foo') = 'Foo' |
+--------------------------------------+
|                                      1 |
+--------------------------------------+
1 row in set (0.06 sec)
```

## Control Flow Functions

There are two functions that allow for varying results depending on conditions.

## IFNULL

IFNULL(expr1,expr2) (used in examples)
RETURNS: type of expr1

If expr1 is not NULL, IFNULL() returns expr1; otherwise, it returns expr2. IFNULL() returns a numeric or string value depending on the context in which it is used.

```
mysql> select ifnull(1/0, 'exp 1 is null');
+--------------------------------------+
| ifnull(1/0, 'exp 1 is null') |
|                                      |
|                exp 1 is null         |
+--------------------------------------+
1 row in set (0.00 sec)
```

```
mysql> select ifnull(1/1, 'exp 1 is not null');
+--------------------------------------+
| ifnull(1/1, 'exp 1 is not null') |
|                                      1.00 |
+--------------------------------------+
1 row in set (0.00 sec)
```

## IF

IF(expr1,expr2,expr3) (used in examples)

If expr1 is TRUE (expr1 <> 0 and expr1 <> NULL) then IF() returns expr2; otherwise, it returns expr3. IF() returns a numeric or string value depending on the context in which it is used. expr1 is evaluated as an integer value, which means that if you are testing floating-point or string values, you should do so using a comparison operation.

```
mysql> select if(name like 'jay%', 'Yes', 'No') as 'Jay Names'
--> from querybook;
+--------------------------------------+
| Jay Names              |
+--------------------------------------+
| Yes                     |
| Yes                     |
| Yes                     |
| No                      |
| No                      |
```

## Mathematical Functions

All mathematical functions return NULL in case of error.

### ABS

This function returns the absolute value of X.

```
ABS(X)
RETURNS: type of X
```

### SIGN

This function returns the sign of the argument as -1, 0, or 1, depending on whether X is negative, 0, or positive.

```
SIGN(X)
RETURNS: int
mysql> select sign(10), sign(-10), sign(0);
+--------------------------------------+
| sign(10) | sign(-10) | sign(0) |
+--------------------------------------+
|      1     |     -1     |      0  |
+--------------------------------------+
1 row in set (0.00 sec)
```

### MOD

Modulo is like the % operator in C. It returns the remainder of N divided by M.

```
MOD(N,M) or N % M
RETURNS: int
mysql> select mod(10,3), mod(10,4);
+------------------------+
| mod(10,3) | mod(10,4) |
+------------------------+
|      1      |      2      |
+------------------------+
1 row in set (0.05 sec)
```

### FLOOR

This function returns the largest integer value not greater than X.

```
FLOOR(X) RETURNS: int
mysql> select floor(8.5);
+-----------+
| floor(8.5) | |
+-----------+
|     8      |
+-----------+
1 row in set (0.00 sec)
```

### CEILING

This function returns the smallest integer value not less than X.

```
FUNCTION: CEILING(X)
RETURNS: int
mysql> select ceiling(8.5);
+-----------+
| ceiling(8.5) | |
+-----------+
|     9      |
+-----------+
1 row in set (0.00 sec)
```

### Round

This function returns the argument X, rounded to an integer.

```
Round ROUND(X [.D])
RETURNS: mixed
```

Returns the argument X, rounded to a number with D decimals. If D is 0, or not specified, the result is rounded to the nearest integer.

### TRUNCATE

TRUNCATE returns the number X truncated to D decimals. If D is not specified, the result is truncated to an integer.

```
TRUNCATE(X,D)
RETURNS: float
```

### EXP

This function returns the value of e (the base of natural logarithms) raised to the power of X.

```
EXP(X)
RETURNS: float
```

### LOG

This function returns the natural logarithm of X. If you want the log of a number X to some arbitrary base B, use the formula LOG(X)/LOG(B).

```
LOG(X [,base]) )
RETURNS: float
```

### LOG10

LOG10 returns the base-10 logarithm of X.

```
LOG10(X)
RETURNS: float
```

### POW(X,Y) or POWER(X,Y)

This function returns the value of X raised to the power of Y.

```
POW(X,Y)
RETURNS: float
```

### SQRT

This returns the non-negative square root of X.

```
SQRT(X)
RETURNS: float
```

### PI

This returns an approximation of Pi.

```
PI()
RETURNS: float
```

### COS

COS returns the cosine of X, where X is given in radians.

```
COS(X)
RETURNS: float
```

### SIN

This returns the sine of X, where X is given in radians.

```
SIN(X)
RETURNS: float
```

### TAN

This returns the tangent of X, where X is given in radians.

```
TAN(X)
RETURNS: float
```

### ACOS

This function returns the arc cosine of X—that is, the value whose cosine is X. Returns NULL if X is not in the range -1 to 1.

ACOS(X)
float

### ASIN

This returns the arc sine of X—that is, the value whose sine is X. Returns NULL if X is not in the range -1 to 1.

ASIN(X)
RETURNS: float

### ATAN

ATAN returns the arc tangent of X—that is, the value whose tangent is X.

ATAN(X)
RETURNS: float

### ATAN2

ATAN2 returns the arc tangent of the two variables X and Y. The process is similar to calculating the arc tangent of Y/X, except the signs of both arguments are used to determine the quadrant of the result.

ATAN2(X,Y)
RETURNS: float

### COT

This function returns the cotangent of X.

COT(X)
RETURNS: float

### RAND

This function returns a random floating-point value in the range 0 to 1.0.

RAND()

or
RAND(N)
RETURNS: float
