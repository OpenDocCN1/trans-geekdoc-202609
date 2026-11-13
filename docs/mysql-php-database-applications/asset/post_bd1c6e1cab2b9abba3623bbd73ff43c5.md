

```
mysql> select period_add(200006,7);
+----------------------------+
| period_add(200006,7)       |
+----------------------------+
| 200101                     |
+----------------------------+
1 row in set (0.00 sec)
```

## PERIOD_DIFF

This function returns the number of months between periods P1 and P2. P1 and P2
should be in the format YYMM or YYYYMM.

```
PERIOD_DIFF(P1,P2)
RETURNS: int
```

Note that the period arguments P1 and P2 are not date values.

```
mysql> select period_diff(200106,200001);
+----------------------------+
| period_diff(200106,200001) |
+----------------------------+
| 17                         |
+----------------------------+
1 row in set (0.00 sec)
```

## DATE_ADD

These functions perform date arithmetic.

```
DATE_ADD(date,INTERVAL expr type)

or

DATE_SUB(date,INTERVAL expr type)

or

ADDDATE(date,INTERVAL expr type)

or

SUBDATE(date,INTERVAL) (used in examples)
RETURNS: date
```

ADDDATE() and SUBDATE() are identical to DATE_ADD() and DATE_SUB(), respectively. In all versions of MySQL since version 3.23 you can use + and - symbols, respectively, instead of DATE_ADD() and DATE_SUB(). (See the following example.) date is a DATETIME or DATE value specifying the starting date. expr is an expression specifying the interval value to be added or subtracted from the starting date. expr is a string; it may start with a - for negative intervals. type is a keyword indicating how the expression should be interpreted.

Table J-1 shows how the type and expr arguments are related.

| Type | Meaning | Expected expr Format Value |
| :--- | :--- | :--- |
| SECOND | Seconds | SS |
| MINUTE | Minutes | MM |
| MINUTE_SECOND | Minutes and seconds | MM:SS |
| HOUR | Hours | HH |
| HOUR_SECOND | Hours, minutes, seconds | HH:MM:SS |
| HOUR_MINUTE | Hours and minutes | HH:MM |
| DAY | Days | DAYS |
| DAY_SECOND | Days, hours, minutes, seconds | DAYS HH:MM:SS |
| DAY_MINUTE | Days, hours, minutes | DAYS HH:MM |
| DAY_HOUR | Days and hours | DAYS HH |
| MONTH | Months | MONTHS |
| YEAR | Years | YEARS |
| YEAR_MONTH | Years and months | YEARS-MONTHS |

MySQL allows any punctuation delimiter in the expr format. The ones shown in the table are the suggested delimiters. If the date argument is a DATE value and your calculations involve only YEAR, MONTH, and DAY parts (that is, no time parts), the result is a DATE value. Otherwise, the result is a DATETIME value.

```
mysql> select '2001-01-01 13:00:00' + interval 10 minute
+-------------------------------------------+
| '2001-01-01 13:00:00' + interval 10 minute |
+-------------------------------------------+
| 2001-01-01 13:10:00                       |
+-------------------------------------------+
1 row in set (0.39 sec)
```

```
mysql> select '2000-01-01 00:00:00' - interval 1 second;
+--------------------------------------------+
| '2000-01-01 00:00:00' - interval 1 second  |
+--------------------------------------------+
| 1999-12-31 23:59:59                        |
+--------------------------------------------+
1 row in set (0.00 sec)
```

```
mysql> select date_add('2000-01-01 00:00:00', interval '1:1:1' hour_second);
+-----------------------------------------------------------+
| date_add('2000-01-01 00:00:00', interval '1:1:1' hour_second) |
+-----------------------------------------------------------+
| 2000-01-01 01:01:01                                     |
+-----------------------------------------------------------+
1 row in set (0.00 sec)
```

```
mysql> select date_sub('2000-01-01 00:00:00', interval '1' month);
+-------------------------------------------------+
| date_sub('2000-01-01 00:00:00', interval '1' month) |
+-------------------------------------------------+
| 1999-12-01 00:00:00                             |
+-------------------------------------------------+
1 row in set (0.00 sec)
```

If you specify an interval value that is too short (one that does not include all the
interval parts that would be expected from the type keyword), MySQL assumes you
have left out the leftmost parts of the interval value. For example, if you specify a
type of DAY_SECOND, the value of expr is expected to have days, hours, minutes,
and seconds parts. If you specify a value like 1:10, MySQL assumes that the days
and hours parts are missing and that the value represents minutes and seconds.

## TO_DAYS

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

## FROM_DAYS

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

## DATE_FORMAT

This function formats the date value according to the format string:

```
DATE_FORMAT(date,format) (used in examples)
RETURNS: string
```

The specifiers in Table J-2 can be used in the format string.

### TABLE J-2 DATE_FORMAT SPECIFIERS

| Specifier | Meaning |
|---|---|
| %M | Month name (January through December) |
| %W | Weekday name (Sunday through Saturday) |
| %D | Day of the month with English ordinal suffix (1st, 2nd, 3rd, and so on) |
| %Y | Year, numeric, four digits |
| %y | Year, numeric, two digits |
| %a | Abbreviated weekday name (Sun...Sat) |
| %d | Day of the month, two numeric digits (01..31) |
| %e | Day of the month, numeric (1..31) |
| %m | Month, two numeric digits (01..12) |
| %c | Month, numeric (1...12) |
| %b | Abbreviated month name (Jan...Dec) |
| %j | Day of year (001..366) |
| %H | Hour (00..23) |
| %k | Hour (0...23) |
| %h | Hour (01...12) |
| %I | Hour (01...12) |
| %i | Minutes, numeric (00...59) |
| %r | Time, 12-hour (hh:mm:ss [AP]M) |
| %T | Time, 24-hour (hh:mm:ss) |
| %S | Seconds (00...59) |
| %s | Seconds (00...59) |
| %p | AM or PM |
| %w | Day of the week (0=Sunday...6=Saturday) |
| %U | Week (00..53), where Sunday is the first day of the week |

### TABLE J-2 DATE_FORMAT SPECIFIERS (Continued)

| Specifier | Meaning |
| --- | --- |
| %u | Week (0..53), where Monday is the first day of the week |
| %V | Week (1..53), where Sunday is the first day of the week; used with %X |
| %v | Week (1..53), where Monday is the first day of the week; used with %x |
| %X | Year for the week, where Sunday is the first day of the week; numeric, four digits, used with %V |
| %x | Year for the week, where Monday is the first day of the week; numeric, four digits, used with %v |
| %% | A literal % |

All other characters are just copied to the result without interpretation:

```
mysql> select date_format('2001-01-01', '%W %M %d, %Y');
+-----------------------------------------+
| date_format('2001-01-01', '%W %M %d, %Y') |
+-----------------------------------------+
| Monday January 01, 2001 |
+-----------------------------------------+
1 row in set (0.00 sec)
```

```
mysql> select date_format('2001-01-01 15:30:20',
->'%W %M %d, %Y %I:%i:%S %p');
+--------------------------------------------------+
| date_format('2001-01-01 15:30:20', '%W %M %d, %Y %I:%i:%S %p') |
+--------------------------------------------------+
| Monday January 01, 2001 03:30:20 PM |
+--------------------------------------------------+
1 row in set (0.00 sec)
```

For MySQL 3.23 and later versions, the % character is required before format-specifier characters. In earlier versions of MySQL, % was optional.

## TIME_FORMAT

This function is used like the DATE_FORMAT() function just discussed, but the format string can contain only those format specifiers that handle hours, minutes, and

