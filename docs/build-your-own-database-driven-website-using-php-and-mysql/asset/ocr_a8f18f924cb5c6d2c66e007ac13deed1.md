to those results separately. This type of query is useful if you want to obtain the result of a SELECT query, store it in a temporary table, and then perform a second SELECT query on it. To some extent, this may be used to make up for MySQL's lack of support for sub-selects, which allow you to perform the same type of operation in a single query.

# DELETE

```
DELETE [LOW_PRIORITY] FROM tbl_name [WHERE where_clause] [LIMIT rows]
```

This query deletes all rows from the specified table, unless the optional (but desirable!) WHERE or LIMIT clauses are specified. The WHERE clause works the same way as its twin in the SELECT query described on page 187. The LIMIT clause simply lets you specify the maximum number of rows to be deleted.

The LOW_PRIORITY option causes the query to wait until there are no clients reading from the table to perform the operation.

# DESCRIBE

```
{DESCRIBE | DESC} tbl_name [col_name | wild]
```

Supplies information about the columns, a specific column (col_name), or any columns that match a pattern containing wildcards '%' and '_' (wild), that make up the specified table. The information returned includes the column name, its type, whether it accepts NULL as a value, whether the column had an index, the default value for the column, and any extra features it has (e.g. auto_increment).

# DROP DATABASE

```
DROP DATABASE [IF EXISTS] db_name
```

This is a dangerous command. It will immediately delete a database along with all of its tables. This query will fail if the database does not exist (unless IF EXISTS is specified), or if you don't have the required privileges.