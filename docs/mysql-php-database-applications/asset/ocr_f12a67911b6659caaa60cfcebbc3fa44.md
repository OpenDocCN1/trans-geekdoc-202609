# # NOT LIKE

A NOT LIKE pattern match uses the same syntax and escaping as like.

```
expr NOT LIKE pattern
RETURNS: int
```

As you could probably have predicted, NOT LIKE returns true if the pattern and the expression do not match:

```
mysql> select 'jay greenspan' NOT LIKE 'jay%'
+----------------------------------+
| 'jay greenspan' NOT LIKE 'jay%' |
+----------------------------------+
|                                    |
|                                    1 |
+----------------------------------+
```

# # REGEXP

This function performs a pattern match of a string expression (expr) against a regular expression (pat). See Appendix G for a discussion of regular expressions. But be aware that MySQL does not support regular expressions to the extent you find in PHP.

```
expr REGEXP pat
RETURNS: int
```

REGEXP returns 1 (true) if the pattern is found or 0 (false) if not:

```
mysql> select name from guestbook WHERE name regexp '^j.*g*';
+--------------+
| name         |
+--------------+
| Jay Greenspan |
| Jay Green    |
+--------------+
2 rows in set (0.00 sec)
```

# # NOT REGEXP

This function works identically to REGEXP, except that patterns that fail to match the expression test true and those that do match test false.