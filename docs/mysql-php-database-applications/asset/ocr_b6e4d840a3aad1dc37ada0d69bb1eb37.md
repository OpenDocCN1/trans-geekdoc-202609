# UCASE

This function returns the string str with all characters changed to upper case according to the current character-set mapping (the default is ISO-8859-1 Latin1):

```
UCASE(str) or UPPER(str)
RETURNS: string
```

# Date and Time Functions

MySQL offers many functions for calculating dates. Of all the MySQL functions available, these are the ones you will probably use most frequently.

The DATE_FORMAT function enables you to format dates to take the form of MySQL timestamps. In addition, several functions will enable you to get specific date information from a column with ease. For example, to find the day of the week of all the entries in a timestamp column, you could use the following code:

```
mysql> select dayname(created) from guestbook;
+---------------------+
| dayname(created) |
+---------------------+
| Sunday |
| Sunday |
| Wednesday |
| Sunday |
| Sunday |
| Wednesday |
| Wednesday |
| Wednesday |
+---------------------+
```

# DAYOFWEEK

This function returns the weekday index for date (1 for Sunday, 2 for Monday, and so on up to 7 for Saturday). These index values correspond to the ODBC standard. If an invalid date is supplied to the date functions, they return null.

```
DAYOFWEEK(date) (used in examples)
RETURNS: int
mysql> select dayofweek('2001-01-01');
+-------------------------+
| dayofweek('2001-01-01') |
```