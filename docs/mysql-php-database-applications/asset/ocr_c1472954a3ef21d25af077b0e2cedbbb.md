This function is used in the following example to prepend a wildcard character onto the column in the WHERE clause of a query:

```
select 1 from blocked_domains
WHERE '$REMOTE_HOST' like concat('%.domain)
and release_dt is null
```

# LENGTH

This function returns the length of the string str. If a numeric value is used as the argument, it's converted to a string first. Note that for CHAR_LENGTH() multi-byte characters are counted only once.

```
LENGTH(mixed)
```

or

```
CHAR_LENGTH(mixed)
```

RETURNS: int

```
mysql> select length('mysql functions');
+-----------------------------+
| length('mysql functions') |
+-----------------------------+
|                           15 |
+-----------------------------+
1 row in set (0.00 sec)
```

# LOCATE

This function returns the position of the first occurrence of substring substr in string str. Returns 0 if substr is not in str.

```
LOCATE(substr,str [,pos])
```

or

```
POSITION(substr IN str)
```

RETURNS: int

The optional third argument enables you to specify an offset at which to start the search:

```
mysql> select locate('s', 'mysql functions') as example1,
-> locate('s', 'mysql functions',4) as example2;
+---+---------+
```