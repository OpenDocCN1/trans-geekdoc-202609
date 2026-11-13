```
| example1 | example2 |
+------------+------------+
| 3 | 15 |
+------------+------------+
1 row in set (0.00 sec)
```

# INSTR

This function returns the position of the first occurrence of substring substr in string str. It is the same as LOCATE(), except that the arguments are swapped and no argument that indicates position is allowed.

```
INSTR(str,substr)
RETURNS: int
```

# LPAD

This function returns the string str, left-padded with the string padstr until str is len characters long.

```
LPAD(str,len,padstr)
RETURNS: string
```

```
mysql> select lpad('foo', 15, 'k');
+-----------------------------+
| lpad('foo', 15, 'k')      |
+-----------------------------+
| kkkkkkkkkkkkfoo           |
+-----------------------------+
1 row in set (0.00 sec)
```

# RPAD

This function returns the string str, right-padded with the string padstr until str is len characters long.

```
RPAD(str,len,padstr)
RETURNS: string
```

# LEFT

This function returns the leftmost len characters from the string str:

```
LEFT(str,len)
RETURNS: string
```