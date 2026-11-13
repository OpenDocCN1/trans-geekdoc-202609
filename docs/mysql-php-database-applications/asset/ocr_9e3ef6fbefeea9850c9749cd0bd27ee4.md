# Cast Operators

You will encounter only one cast operator in MySQL.

# BINARY

```
BINARY
RETURNS: string
```

The BINARY operator casts the string following it to a binary string. Using it is an easy way to force a column comparison to be case-sensitive even if the column isn't defined as BINARY or BLOB.

```
mysql> select binary('Foo') = 'foo', binary('Foo') = 'Foo';
+-----------------------------+-----------------------------+
| binary('Foo') = 'foo' | binary('Foo') = 'Foo' |
+-----------------------------+-----------------------------+
|                           0 |                           1 |
+-----------------------------+-----------------------------+
1 row in set (0.06 sec)
```

# Control Flow Functions

Two functions allow for varying results depending on conditions.

# IFNULL

```
IFNULL(expr1,expr2) (used in examples)
RETURNS: type of expr1 or expr2
```

If expr1 is not NULL, IFNULL() returns expr1; otherwise, it returns expr2. IFNULL() returns either a numeric or a string value depending on the context in which it is used.

```
mysql> select ifnull(1/0, 'exp 1 is null');
+-----------------------------+
| ifnull(1/0, 'exp 1 is null') |
+-----------------------------+
| exp 1 is null               |
+-----------------------------+
1 row in set (0.00 sec)
```

```
mysql> select ifnull(1/1, 'exp 1 is not null');
+--------------------------------------+
```