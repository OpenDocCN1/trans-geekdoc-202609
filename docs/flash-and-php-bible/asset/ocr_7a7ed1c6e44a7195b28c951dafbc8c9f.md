A shortcut is used to exclude the column definitions. However, this is only possible when all values are being updated or you have assigned default values when you create the table.

```
INSERT INTO members ($name, $bio, $ip);
```

After an INSERT has completed, you can make a call to mysql_insert_id(), which will return the ID of the last successful insert.

```
$result = mysql_query("INSERT INTO members ( " .
  $name . ", " .
  $bio . ", " .
  $ip . ")");
```

```
$rowID = mysql_insert_id($result);
```

# DELETE

The DELETE statement is used to remove one or more rows from a table. Like the other statements, you can create a condition using WHERE, AND, OR, and so on.

```
DELETE FROM users WHERE id=3
```

You can also remove all rows in a database by omitting the condition:

```
DELETE FROM users
```

CAUTION The DELETE statement is a very powerful one that should be used with extreme caution.

# Conditions

Conditions in MySQL are used to limit the amount of data that is returned. For example, an SQL query such as the following would return all users in the database:

```
SELECT * FROM users
```

# WHERE

This would be okay if that’s what you want to occur. You probably only would want to return certain users or even one specific user. This would be done using the WHERE condition.

```
SELECT * FROM users WHERE id=3
```

# AND

The AND condition is used when you need to match more than one condition. An example would be you want to return a database of members that have been registered and have a valid account.

```
SELECT * FROM users WHERE active=1 AND registered="yes"
```

You can use any combination of the conditional statements, with the exception that there should only be one WHERE statement.