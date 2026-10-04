
If an integer argument N is specified, it is used as the seed value. You can't use a column with RAND() values in an 'order' by clause order would evaluate the column multiple times. In MySQL 3.23, you can, however, do: select * from table_name order rand(). This is useful to get a random sample. Note that RAND() in a WHERE clause will be re-evaluated every time the WHERE clause is executed.

## LEAST

With two or more arguments, this function returns the smallest (minimum-valued) argument.

```
LEAST(X,Y,....)
RETURNS: type of X
mys> select least(2,7,9,1)
+----------------+
| least(2,7,9,1) |
+----------------+
|                1 |
+----------------+
1 row in set (0.00 sec)
```

## GREATEST

GREATEST returns the largest (maximum-valued) argument. In MySQL versions prior to 3.22.5, you can use MAX() instead of GREATEST.

```
GREATEST(X,Y,....)
RETURNS: type of X
mys> select greatest(2,7,9,1)
+----------------+
| greatest(2,7,9,1) |
+----------------+
|                9 |
+----------------+
1 row in set (0.00 sec)
```

## DEGREES

This returns the argument X, converted from radians to degrees.

```
DEGREES(X)
RETURNS: float
```

## RADIANS

This returns the argument X, converted from degrees to radians.

## String Functions

MySQL's string functions return NULL if the length of the result would be greater than the max_allowed_packet server parameter. This parameter can be set by starting MySQL with a command like this:

```
safe_mysqld -O max_allowed_packet=16M
```

For functions that operate on string positions, the first position is numbered 1.

## ASCII

Returns the ASCII code value of the leftmost character of the string str. Returns 0 if str is the empty string. Returns NULL if str is NULL.

```
ASCII(str)
RETURNS: int
mysql> select ascii('\n');
+----------------+
| ascii('\n') |
+----------------+
|      10       |
+----------------+
1 row set in (0.00 sec)
```

## ORD

If the leftmost character of the string str is a multi-byte character, this function returns the code of multi-byte character by returning the ASCII code of the character in the format of: ((first byte ASCII code)*256+(second ASCII code)*25+third byte ASCII code...). If the leftmost character is not a multi-byte character, ORD returns the same value as the similar ASCII() function.

```
ORD(str)
RETURNS: int
```

## CONV

This function converts numbers between different number bases.

```
CONV(N,from_base,to_base)
RETURNS: string
```

It returns a string representation of the number N, converted from base from_base to to_base. It returns NULL if any argument is NULL. The argument N is interpreted as an integer, may be specified as an integer or a string. The mini-base is 2 and the maximum base is 36. If to_base is a negative number, N is regarded as a signed number. Otherwise, N is treated as unsigned. CONV works with 64-bit precision.

```
mysql> select conv(3,10,2);
+-------------+
| conv(3,10,2) |
+-------------+
| 11          |
```

## BIN

This function returns a string representation of the binary value of N, where N is a long (BIGINT) number. It is equivalent to CONV(N,10,2). Returns NULL if N is NULL.

BIN(N)
RETURNS: string

## OCT

This function returns a string representation of the octal value of N, where N is a long (BIGINT) number. It is equivalent to CONV(N,10,8). Returns NULL if N is NULL.

OCT(N)
RETURNS: string

## HEX

This function returns a string representation of the hexadecimal value of N, where N is a long (BIGINT) number. It is equivalent to CONV(N,10,16). Returns NULL if N is NULL.

HEX(N)
RETURNS: string

## CHAR

This function interprets the arguments as integers and returns a string consisting of the ASCII code values of those integers. NULL values are skipped.

## Appendix I: MySQL Function Reference

CHAR(N....)
RETURNS: string

## CONCAT

This function returns the string that results from the concatenation of the arguments. It returns NULL if any argument is NULL. CONCAT may have more than two arguments. A numeric argument is converted to the equivalent string form.

CONCAT(str1,str2,...) (used in examples)
RETURNS: string

This function is used in the following example to prepend wildcard character
to the column in the where clause of a query.

```
select 1 from blocked_domains
where '$REMOTE_HOST' like concat('%',domain)
and release_dt is null
```

## LENGTH

This function returns the length of the string str. Note that for CHAR_LENGTH(), multi-byte characters are only counted once.

LENGTH(str)

or

CHAR_LENGTH(str)
RETURNS: int
mysql select length('mysql functions');

+--------------------------------------+
| length('mysql functions') |
+--------------------------------------+
| 16 |
+--------------------------------------+

## LOCATE

This function returns the position of the first occurrence of substring in str. Returns 0 if substring is not found.

```
LOCATE(substr,str[,pos])
RETURNS: int
```

## INSTR

This function returns the position of the first occurrence of substring in str. It is the same as LOCATE(), except that arguments are swapped and no pos argument is allowed to specify the search.

## LPAD

This function returns the string str, left-padded with the string padstr until len characters long.

```
LPAD(str,len,padstr)
RETURNS: string
```

## RPAD

This function returns the string str, right-padded with the string padstr until len characters long.

```
RPAD(str,len,padstr)
RETURNS: string
```

## LEFT

This function returns the leftmost len characters from str.

```
LEFT(str,len)
RETURNS: string
```

## RIGHT

This function returns the rightmost len characters from str.

```
RIGHT(str,len)
RETURNS: string
```

## SUBSTRING

This function returns a substring len characters from str, starting at pos, and continuing for len number of characters. The variant form that uses FROM is ANSI SQL92 syntax.

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

## SUBSTRING_INDEX

This function returns the substring from str after count occurrences of the delimiter. If count is positive, everything to the left of the final delimiter (counting from the left) is returned. If count is negative, everything to the right of the final delimiter (counting from the right) is returned.

```
SUBSTRING_INDEX(str,delim,count) (used in examples)
RETURNS: string
```

## LTRIM

This function returns the string str with leading spaces removed.

```
LTRIM(str)
RETURNS: string
```

## RTRIM

This function returns the string str with trailing space characters removed.

```
RTRIM(str)
RETURNS: string
```

## TRIM

This function returns the string str with all remstr prefixes and/or suffixes removed. If none of the specifies BOTH, LEADING, or TRAILING are given, BOTH is assumed. If remstr is not specified, spaces are removed.

```
TRIM([[BOTH | LEADING | TRAILING][remstr] FROM) str) (used in examples)
RETURNS: string
```
