# MySQL Quick Reference

Conditions (use % wildcard):

```
field = value
field > value
field < value
field >= value
field <= value
field != value
field BETWEEN value AND value2
field LIKE value
field NOT LIKE value
field IN (value1, value2, value3, etc)
field NOT IN (value1, value2, value3, etc)
```

# Selecting from Multiple Tables

You can retrieve information from two or more tables at once by using the following statements:

```
SELECT table1.field, table2.field FROM table1, table2 WHERE
table1.field = table2.field;
```

or

```
SELECT tablefield, table2field FROM table LEFT JOIN table 2;
```

# Sorting the Results

You can sort the results of the SELECT query by using the following clause at the end of the statement:

```
SELECT * FROM tableName WHERE field1=valuel ORDER BY field2 ASC|DESC
```

# Limiting the Results

If you would like to limit the results returned from our query, you can modify your SELECT statement like this:

```
SELECT * FROM tableName WHERE field1=valuel
ORDER BY field2 ASC
LIMIT offset, number_of_rows_to_be_returned
```

653