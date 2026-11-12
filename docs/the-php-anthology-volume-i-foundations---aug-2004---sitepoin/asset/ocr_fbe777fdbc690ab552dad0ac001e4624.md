```
$sql = "SELECT * FROM articles ORDER BY title";
```

It's handy to keep it in a separate variable, as when we get into writing more complex queries and something goes wrong, we can double-check our query with this one-liner:

```
echo $sql;
```

+   2. Next, tell MySQL to perform the query:

```
$queryResource = mysql_query($sql, $dbConn);
```

This can be confusing at first. When you tell MySQL to perform a query, it doesn’t immediately give you back the results. Instead, it holds the results in memory until you tell it what to do next. PHP keeps track of the results with a **resource identifier**, which is what you get back from the `mysql_query` function. In the code above, we’ve stored the identifier in `$queryResource`.

+   3. Finally, use `mysql_fetch_array` to fetch one row at a time from the set of results:

```
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC))
```

This places each row of the results in turn in the variable `$row`. Each of these rows will be represented by an array. By using the additional argument `MYSQL_ASSOC` with `mysql_fetch_array`, we’ve told the function to give us an array in which the keys correspond to column names in the table. If you omit the `MYSQL_ASSOC` argument, each column will appear twice in the array: once with a numerical index (i.e. `$row[0]`, `$row[1]`, etc.), and once with a string index (i.e. `$row['title']`, `$row['author']`, etc.). While this doesn’t usually cause a problem, specifying the type of array value you want will speed things up slightly.

Using a while loop, as shown above, is a common way to process each row of the result set in turn. The loop effectively says, “Keep fetching rows from MySQL until I can’t get any more”, with the body of the loop processing the rows as they’re fetched.

# Forego Buffering on Large Queries

![](bbox=[0.116, 0.799, 0.186, 0.822])

For large queries (that is, queries that produce large result sets), you can improve performance dramatically by telling PHP not to **buffer** the results of the query. When a query _is_ buffered, the entire result set is retrieved from MySQL and stored in memory before your script is allowed to proceed. An