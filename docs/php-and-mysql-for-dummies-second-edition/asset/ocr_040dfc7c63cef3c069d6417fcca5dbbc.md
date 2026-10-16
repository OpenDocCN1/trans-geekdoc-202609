To interact with the database, put your SQL query into a variable and send it to the MySQL server by using the function mysql_query, as in the following example:

```
$query = "SELECT * FROM Pet";
$result = mysql_query($query)
    or    die ("Couldn't execute query.");
```

The query is executed on the currently selected database for the last connection that you opened. If you need to — if you have more than one connection open, for instance — you can send the query to a specific database server like this:

```
$result = mysql_query($query,$connection)
    or    die ("Couldn't execute query.");
```

The variable $result holds information on the result of executing the query. The information depends on whether or not the query gets information from the database:

+   - **For queries that don't get any data:** The variable $result contains information on whether the query executed successfully or not. If it's successful, $result is set to TRUE; if it's not successful, $result is set to FALSE. Some queries that don't return data are INSERT and UPDATE.
+   - **For queries that return data:** The variable $result contains a result identifier that identifies where the returned data is located and not the returned data itself. Some queries that do return data are SELECT and SHOW.

![](bbox=[0.11, 0.6, 0.2, 0.73])

The use of single and double quotes can be a little confusing when assigning the query string to $query. You are actually using quotes on two levels: the quotes needed to assign the string to $query and the quotes that are part of the SQL language query itself. The following rules will help you avoid any problems with quotes:

+   - Use double quotes at the beginning and end of the string.
+   - Use single quotes before and after variable names.
+   - Use single quotes before and after any literal values.

The following are examples of assigning query strings:

```
$query = "SELECT firstName FROM Member";
$query = "SELECT firstName FROM Member WHERE lastName='Smith'";
$query = "UPDATE Member SET lastName='$last_name'";
```

![](bbox=[0.11, 0.85, 0.2, 0.95])

The query string itself does not include a semicolon (;), so don't put a semicolon inside the final quote. The only semicolon is at the very end; this is the PHP semicolon that ends the statement.