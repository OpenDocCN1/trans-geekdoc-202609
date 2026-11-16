Note that, by default, pg_fetch_array() will return a numerically and associatively-indexed array (PGSQL_BOTH). This will produce an array twice as large as it needs to be because each entry needs to be duplicated for each index type. Therefore, you should explicitly request either PGSQL_NUM or PGSQL_ASSOC when calling pg_fetch_array(), depending on the needs of your code.

# pg_freeresult()

```
int pg_freeresult(int result_id)
```

In the above examples, you may have noticed the use of pg_freeresult(). This function releases all memory associated with the given resultset. This would happen anyway when the script finishes executing, but if you are concerned about the memory usage for large resultsets in complex scripts, this function could give you a breather.

# An Online Library

Now that you are familiar with PHP's PostgreSQL interface, we will revisit the example application we started in the last chapter. If you skipped that chapter, you may want to go back and review that section.

In this chapter, we will concern ourselves only with porting the existing MySQL code to use PostgreSQL.

We'll begin by porting the log in screen (login.php). Let's revisit the code as we left it in the last chapter. We'll just focus on the database interaction code:

```
// Connect to the database
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

mysql_select_db('Library', $conn) or die(mysql_error());

// Query the database
$sql = "SELECT username FROM Users WHERE username = '' .
$username . '' and password = '' . $password . '';
$result = mysql_query($sql, $conn);

// Test the query result
$success = false;
if (@mysql_result($result, 0, 0) == $username) {
    $success = true;
}

mysql_close($conn);
```

We'll begin by changing the database connection code to connect to our PostgreSQL database instead of the MySQL database. That reduces us to the following two lines:

```
// Connect to the database
$conn = pg_connect('dbname=library user=jon password=secret')
or die(pg_errormessage());
```