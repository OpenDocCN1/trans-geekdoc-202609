
### POW(X,Y) or POWER(X,Y)

This function returns the value of X raised to the power of Y.

```
RETURNS: float
```

### SQRT

This returns the non-negative square root of X.

```
SQRT(X)
```

```
RETURNS: float
```

### PI

This returns an approximation of Pi.

```
Pi()
```

```
RETURNS: float
```

### COS

COS returns the cosine of X, where X is given in radians.

```
COS(X)
```

```
RETURNS: float
```

### SIN

SIN returns the sine of X, where X is given in radians.

```
SIN(X)
```

```
RETURNS: float
```

### TAN

This returns the tangent of X, where X is given in radians.

```
TAN(X)
```

```
RETURNS: float
```

### ACOS

This function returns the arc cosine of X—that is, the value whose cosine is X. It returns NULL if X is not in the range -1 to 1.

```
ACOS(X)
RETURNS: float
```

### ASIN

This returns the arc sine of X—that is, the value whose sine is X. Returns NULL if X is not in the range -1 to 1.

```
ASIN(X)
RETURNS: float
```

### ATAN

ATAN returns the arc tangent of X—that is, the value whose tangent is X.

```
ATAN(X)
RETURNS: float
```

### ATAN2

ATAN2 returns the arc tangent of the two variables X and Y. The process is similar to calculating the arc tangent of Y/X, except that the signs of both arguments are used to determine the quadrant of the result.

```
ATAN2(X,Y)
RETURNS: float
```

### COT

This function returns the cotangent of X.

```
COT(X)
RETURNS: float
```

### RAND

This function returns a random floating-point value in the range 0 to 1.0.

```
RAND()
or
RAND(N)
RETURNS: float
```

If an integer argument N is specified, it is used as the seed value. You can't use a column with RAND() values in an `order by` clause because order by would evaluate the column multiple times. In MySQL 3.23, you can, however, do: select * from table_name order by rand(). This is useful to get a random sample. Note that a RAND() in a WHERE clause will be re-evaluated every time the WHERE is executed.

### LEAST

With two or more arguments, this function returns the smallest (minimum-valued) argument.

```
LEAST(X,Y,...)
RETURNS: type of X
```

mysql> select least(2,7,9,1);

| least(2,7,9,1) |
|---|
| 1 |

1 row in set (0.00 sec)

### GREATEST

GREATEST returns the largest (maximum-valued) argument. In MySQL versions prior to 3.22.5, you can use MAX() instead of GREATEST.

```
GREATEST(X,Y,...)
RETURNS: type of X
```

mysql> select greatest(2,7,9,1);

| greatest(2,7,9,1) |
|---|
| 9 |

1 row in set (0.00 sec)

### DEGREES

This returns the argument X, converted from radians to degrees.

```
DEGREES(X)
RETURNS: float
```

### RADIANS

This returns the argument X, converted from degrees to radians.

```
RADIANS(X)
RETURNS: float
```

## String Functions

MySQL's string functions return NULL if the length of the result would be greater than the max_allowed_packet server parameter. This parameter can be set by starting MySQL with a command like this:

```
safe_mysqld -O max_allowed_packet=16M
```

For functions that operate on string positions, the first position is numbered 1.

### ASCII

Returns the ASCII code value of the leftmost character of the string str. Returns 0 if str is the empty string. Returns NULL if str is NULL.

```
ASCII(str)
RETURNS: int
```

mysql> select ascii('\n');

| ascii('\n') |
|---|
| 10 |

1 row in set (0.00 sec)

### ORD

If the leftmost character of the string str is a multi-byte character, this function returns the code of multi-byte character by returning the ASCII code value of the character in the format of: ((first byte ASCII code)*256+(second byte ASCII code))[*256+third byte ASCII code...]. If the leftmost character is not a multi-byte character, ORD returns the same value as the similar ASCII() function.

```
ORD(str)
RETURNS: int
```

### CONV

This function converts numbers between different number bases.

```
CONV(N,from_base,to_base)
RETURNS: string
```

It returns a string representation of the number N, converted from base from_base to base to_base. It returns NULL if any argument is NULL. The argument N is interpreted as an integer, but may be specified as an integer or a string. The minimum base is 2 and the maximum base is 36. If to_base is a negative number, N is regarded as a signed number. Otherwise, N is treated as unsigned. CONV works with 64-bit precision.

mysql> select conv(3,10,2);

| conv(3,10,2) |
|---|
| 11 |

### BIN

This function returns a string representation of the binary value of N, where N is a long (BIGINT) number. It is equivalent to CONV(N,10,2). Returns NULL if N is NULL.

```
BIN(N)
RETURNS: string
```

### OCT

This function returns a string representation of the octal value of N, where N is a long (BIGINT) number. It is equivalent to CONV(N,10,8). It returns NULL if N is NULL.

```
OCT(N)
RETURNS: string
```

### HEX

This function returns a string representation of the hexadecimal value of N, where N is a long (BIGINT) number. This is equivalent to CONV(N,10,16). Returns NULL if N is NULL.

```
HEX(N)
RETURNS: string
```

### CHAR

This function interprets the arguments as integers and returns a string consisting of the ASCII code values of those integers. NULL values are skipped.

```
CHAR(N,...)
RETURNS: string
```

### CONCAT

This function returns the string that results from the concatenation of the arguments. It returns NULL if any argument is NULL. CONCAT may have more than two arguments. A numeric argument is converted to the equivalent string form.

```
CONCAT(str1,str2,...) (used in examples)
RETURNS: string
```

This function is used in the following example to prepend a wildcard character onto the column in the where clause of a query.

```
select 1 from blocked_domains
  where '$REMOTE_HOST' like concat('%',domain)
  and release_dt is null
```

### LENGTH

This function returns the length of the string str. Note that for CHAR_LENGTH(), multi-byte characters are only counted once.

```
LENGTH(str)
```

or

```
CHAR_LENGTH(str)
RETURNS: int
```

mysql> select length('mysql functions');

| length('mysql functions') |
|---|
| 15 |

1 row in set (0.00 sec)

### LOCATE

This function returns the position of the first occurrence of substring substr in string str. Returns 0 if substr is not in str. The optional third argument allows you to specify a starting position for the search.

```
LOCATE(substr,str [,pos])
```

or

```
POSITION(substr IN str)
RETURNS: int
```

The optional third argument specifies an offset to start the search.

mysql> select locate('s', 'mysql functions') as example1,
    -> locate('s', 'mysql functions',4) as example2;

| example1 | example2 |
|---|---|
| 3 | 15 |

1 row in set (0.00 sec)

### INSTR

This function returns the position of the first occurrence of substring `substr` in string `str`. It is the same as `LOCATE()`, except that the arguments are swapped and no argument that indicates position is allowed.

```
INSTR(str,substr)
RETURNS: int
```

### LPAD

This function returns the string `str`, left-padded with the string `padstr` until `str` is `len` characters long.

```
LPAD(str,len,padstr)
RETURNS: string
```

mysql> select lpad('foo', 15, 'k');

| lpad('foo', 15, 'k') |
|---|
| kkkkkkkkkkkkfoo |

1 row in set (0.00 sec)

### RPAD

This function returns the string `str`, right-padded with the string `padstr` until `str` is `len` characters long.

```
RPAD(str,len,padstr)
RETURNS: string
```

### LEFT

This function returns the leftmost len characters from the string str.

```
LEFT(str,len)
RETURNS: string
```

### RIGHT

This function returns the rightmost len characters from the string str.

```
RIGHT(str,len)
RETURNS: string
```

### SUBSTRING

This function returns a substring len characters long from string str, starting at position pos, and continuing for len number of characters. The variant form that uses FROM is ANSI SQL92 syntax.

```
SUBSTRING(str,pos[,len])
```

or

```
SUBSTRING(str FROM pos FOR len)
```

or

```
MID(str,pos,len) (used in examples)
RETURNS: string
```

mysql> select mid('mysqlfunctions',6,8);

| mid('mysqlfunctions',6,8) |
|---|
| function |

1 row in set (0.00 sec)

### SUBSTRING_INDEX

This function returns the substring from string str after count occurrences of the delimiter delim. If count is positive, everything to the left of the final delimiter
