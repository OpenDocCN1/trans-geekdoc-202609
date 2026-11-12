**unbuffered query**, on the other hand, lets MySQL hold onto the results until you request them, one row at a time (e.g. with mysqli_fetch_array). Not only does this allow your script to continue running while MySQL performs the query, it also saves PHP from having to store all of the rows in memory at once.

PHP lets you perform unbuffered queries with mysqli_unbuffered_query:

```
$queryResource = mysqli_unbuffered_query($sql, $dbConn);
```

Of course, all good things come at a price—with unbuffered queries you can no longer use the mysqli_num_rows function to count the number of rows. Obviously, as PHP doesn't keep a copy of the complete result set, it is unable to count the rows it contains! You also must fetch all rows in the result set from MySQL before you can make another query.

Although other functions exist for getting rows and cells from query results, like mysqli_fetch_object and mysqli_result, you can achieve more or less the same things with just mysqli_fetch_array, and the consistency may help keep your code simple.

# Fetching with Classes

Now that you're happy with the basics of fetching data from MySQL, it's time to build some more on the MySQL class from the last solution.

First, let's add a method to run queries from the class:

```
File: Database/MySQL.php (in SPLIB) (excerpt)

/**
 * Returns an instance of MySQLResult to fetch rows with
 * @param $sql string the database query to run
 * @return MySQLResult
 * @access public
 */
function &query($sql)
{
    if (!($queryResource = mysqli_query($sql, $this->dbConn)) {
        trigger_error('Query failed: ' . mysqli_error($this->dbConn)
            . ' SQL: ' . $sql);
    }

    return new MySQLResult($this, $queryResource);
}
```