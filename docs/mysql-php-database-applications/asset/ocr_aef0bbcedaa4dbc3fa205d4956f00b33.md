# Appendix J

# MySQL Function Reference

MYSQL HAS MANY FUNCTIONS, and only some of these were used in the course of this book. You should, however, have a good idea of what other MySQL functions are available, as you might find they come in handy at times. To see the complete MySQL function reference check out MySQL AB's documentation at http:// www.mysql.com/documentation/mysql/bychapter/manual_Reference.html.

# String Comparison Functions

This set of functions should not be confused with PHP's string handling functions. Normally, if any expression in a string comparison is case-sensitive, the comparison is performed in a case-sensitive way.

# LIKE

This function conducts a pattern match using basic SQL wildcard characters:

```
expr LIKE pattern
RETURNS: int
```

With like you can use the following two wildcard characters in the pattern: %, which matches any number of characters, even zero characters, and _ , which matches exactly one character. To test for literal instances of a wildcard character, precede the character with the escape character, usually a backslash (\).

In MySQL you can specify a different escape character, but this is rarely useful. This function returns 1 (true) if the pattern is found or 0 (false) if not:

```
mysql> select 'jay greenspan' like 'jay%';
+-------------------------------------+
| 'jay greenspan' like 'jay%' |
+-------------------------------------+
| 1 |
+-------------------------------------+
1 row in set (0.00 sec)
```