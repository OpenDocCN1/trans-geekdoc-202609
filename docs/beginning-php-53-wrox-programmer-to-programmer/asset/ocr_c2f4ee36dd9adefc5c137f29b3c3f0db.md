# Chapter 13: Retrieving Data from MySQL with PHP

The PDOStatement::bindValue method takes three arguments: the name of the placeholder to bind, the value instead of the placeholder, and the data type of the value (PDO::PARAM_INT, integer, in this case). By specifying the data type, PDO can ensure the correct type of data is passed to MySQL. In addition, PDO automatically escapes any quote marks and other special characters in the data. (Failure to escape special characters is a common cause of SQL injection vulnerabilities.)

Some common data types that you can use:

+   - PDO::PARAM_BOOL — A Boolean data type
- PDO::PARAM_NULL — The NULL data type
- PDO::PARAM_STR — A string type. (This is the default if you don't specify a type)
- PDO::PARAM_LOB — A LOB data type, such as BLOB or LONGBLOB

Now that the statement has been prepared and the filled with actual values, it's time to run the query:

```
$st->execute();
```

The next block of code loops through the result set returned by the query. For each row returned, it creates a associative Member object to hold the row's data, and stores the object in an array:

```
$members = array();
foreach ($st->fetchAll() as $row) {
    $members[] = new Member($row);
}
```

PDOStatement::fetchAll() is one of many ways that you can retrieve the result set returned from a query. fetchAll() grabs the result set in one go, and returns it as an array of arrays, where each associative array holds a row of data. Though is fine for relatively small result sets—less than 100 rows—be careful of using fetchAll() with large result sets, because the entire result is loaded into your script's memory in one.

However, in case fetchAll is not ideal the script loops through the rows of array, passing each $row associative array into the Member class. Remember that the constructor is actually in the DataObject class, and it expects an associative array of field names and values, which is exactly what each array returned by fetchAll() contains. The constructor then uses this associative array to populate the Member object with the data.

Once the array Member objects have been created, the method runs another query. Remember the SQL_CALC_ROWS keyword in the original query? To extract the calculated number of rows, you need to run a second query immediately after the first:

```
$st = $conn->query("SELECT COUNT(*) AS TotalRows*");
$row = $st->fetch();
```

The query calls the MySQL found_rows function to get calculated total, and returns the result as an alias, totalRows. Notice that this is a regular query that uses PDO::query(), rather than a prepared statement as used by the first query. You don't need to use placeholders because the query doesn't need to contain any passed-in values; here there is no need to go into the trouble of creating a prepared statement.