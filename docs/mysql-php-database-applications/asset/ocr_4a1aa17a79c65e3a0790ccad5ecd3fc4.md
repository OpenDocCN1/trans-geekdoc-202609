# TO_DAYS

Given a date date, this function returns a daynumber (the number of days since year 0):

```
TO_DAYS(date) (used in examples)
RETURNS: int
```

```
mysql> select to_days('2003-01-01');
+------------------------+
| to_days('2003-01-01')  |
+------------------------+
|                   731581 |
+------------------------+
```

TO_DAYS() is not intended for use with values that precede the advent of the Gregorian calendar (1582). Note that it is not the same as the PHP mktime() function, which gets the date relative to January 1, 1970. See the entry for the MySQL UNIX_TIMESTAMP function, later in this appendix, if you need that information.

# FROM_DAYS

Given a daynumber N, this function returns a DATE calculated from year 0:

```
FROM_DAYS(N) (used in examples)
RETURNS: date
```

```
mysql> select from_days('731581');
+------------------------+
| from_days('731581')    |
+------------------------+
| 2003-01-01             |
+------------------------+
```

FROM_DAYS() is not intended for use with values that precede the advent of the Gregorian calendar (1582).

# DATE_FORMAT

This function formats the date value according to the format string:

```
DATE_FORMAT(date,format) (used in examples)
RETURNS: string
```