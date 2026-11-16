
Note that, by default, pg_fetch_array() will return a numerically and associatively-indexed array (PGSQL_BOTH). This will produce an array twice as large as it needs to be because each entry needs to be duplicated for each index type. Therefore, you should explicitly request either PGSQL_NUM or PGSQL_ASSOC when calling pg_fetch_array(), depending on the needs of your code.

## pg_freeresult()

```
int pg_freeresult(int result_id)
```

In the above examples, you may have noticed the use of pg_freeresult(). This function releases all memory associated with the given resultset. This would happen anyway when the script finishes executing, but if you are concerned about the memory usage for large resultsets in complex scripts, this function could give you a breather.

## An Online Library

Now that you are familiar with PHP's PostgreSQL interface, we will revisit the example application we started in the last chapter. If you skipped that chapter, you may want to go back and review that section.

In this chapter, we will concern ourselves only with porting the existing MySQL code to use PostgreSQL.

We'll begin by porting the login screen (login.php). Let's revisit the code as we left it in the last chapter. We'll just focus on the database interaction code:

```
// Connect to the database
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

mysql_select_db('Library', $conn) or die(mysql_error());

// Query the database
$sql = "SELECT username FROM Users WHERE username = '" .
    $username . "' and password = '" . $password . "'";
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

Now, we'll tackle the SQL query code. Because we didn't use any MySQL-specific constructs in our SQL statement, the only change we need to make is from mysql_query() to pg_exec():

```
// Query the database
$sql = "SELECT username FROM users WHERE username = '" .
    $username . "' and password = '" . $password . "'";
$result = pg_exec($conn, $sql);
```

The result-checking code is also a simple port. We just need to use pg_result() instead of mysql_result():

```
// Test the query result
$success = false;
if (trim(@pg_result($result, 0, 'username')) == $username) {
    $success = true;
}
```

PostgreSQL pads CHAR values to their full length with spaces (up to 32 characters, in this case). We add the trim() call to the above line to trim off those spaces.

Lastly, we need to change mysql_close() to pg_close():

```
// Close the connection to the database
pg_close($conn);
```

That completes our port of login.php from MySQL to PostgreSQL. We still need to add a user entry to our users table, though:

```
library=# INSERT INTO users VALUES ('jon', 'secret');
INSERT 101831 1
```

We'll move on to our port of the search.php script. Once again, we'll just focus on the database interaction code:

```
// Connect to the MySQL server
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

// Select the database
mysql_select_db('Library', $conn) or die(mysql_error());

// Query the database for the list of series
$sql = "SELECT series_ID, book_series FROM Series";
$result = mysql_query($sql, $conn);

// Print the <option> rows for the <select> widget
if ($result && (mysql_num_rows($result) > 0)) {
    while ($row = mysql_fetch_assoc($result)) {
        $option = sprintf('<option value="%d">%s</option>',
            $row['series_ID'], $row['book_series']);
        echo("$option\n");
    }
}
} else {
    echo("<option>No series are available</option>\n");
}
mysql_close($conn);
```

We already know how to port the `mysql_connect()`, `mysql_select_db()`, `mysql_query()`, and `mysql_close()` functions to their PostgreSQL equivalents.

Here, we'll just focus on the result processing code. In the first line we just need to replace the call to `mysql_num_rows()` with a call to `pg_numrows()`:

```
if ($result && (pg_numrows($result) > 0)) {
```

The next part is more interesting. There is no `pg_fetch_assoc()` function, so how do we port the call to `mysql_fetch_assoc()`? If we go back and examine the description of `pg_fetch_array()`, we'll see that it provides us with an associative array. We also need to use a row counter with the PostgreSQL functions.

The changed code looks like this:

```
$row_counter = 0;
while ($row = pg_fetch_array($result, $row_counter, PGSQL_ASSOC)) {
    $option = sprintf('<option value="%d">%s</option>',
        $row['series_ID'], $row['book_series']);
    echo("$option\n");
    $row_counter++;
}
```

The last script to port is results.php, which displays the user's search results. Once more, here is just the section of code that interacts with the database:

```
// Connect to the MySQL server
$conn = mysql_connect('localhost', 'jon', 'secret') or die(mysql_error());

// Select the database
mysql_select_db('Library', $conn) or die(mysql_error());

// Attempt to fetch the form variables
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];

// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
    "FROM Title, Details, Author, AuthorTitle, Series " .
    "WHERE Author.author_ID = AuthorTitle.auth_ID AND " .
    "AuthorTitle.ISBN = Title.ISBN AND Title.ISBN = Details.ISBN AND " .
    "Details.series_ID = Series.series_ID";

// Add the search terms to the query
if (!empty($series)) {
    $sql .= " AND Series.series_ID = $series";
}
if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND Details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND Author.auth_name LIKE '%$query%'" ;
    } elseif ($type == 'title') {
        $sql .= " AND Title.book_title LIKE '%$query%'";
    }
}

$result = mysql_query($sql, $conn);

// Print the <option> rows for the <select> widget
if ($result && (mysql_num_rows($result) > 0)) {
    while ($row = mysql_fetch_assoc($result)) {
?>
<tr>
<td><u><?php echo(htmlspecialchars($row['book_title'])); ?></u></td>
<td><?php echo(htmlspecialchars($row['auth_name'])); ?></td>
<td><?php echo(htmlspecialchars($row['price'])); ?></td>
</tr>
<?php
    }
} else {
    echo ("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}

mysql_close($conn);
```

You should already know how to port this code from MySQL to PostgreSQL based on your experience with the previous two scripts. Here's the PostgreSQL version of the above code:

```
// Connect to the PostgreSQL server
$conn = pg_connect('dbname=library user=jon password=secret')
    or die(pg_errormessage());

// Attempt to fetch the form variables
$query = addslashes($HTTP_GET_VARS['query']);
$series = $HTTP_GET_VARS['series'];
$type = $HTTP_GET_VARS['type'];

// Query the database for the list of series
$sql = "SELECT book_title, auth_name, price " .
    "FROM title, details, author, authorititle, series " .
    "WHERE author.auth_ID = authorititle.auth_ID AND " .
    "authorititle.ISBN = title.ISBN AND ISBN = details.ISBN AND " .
    "details.series_ID = series.series_ID";

// Add the search terms to the query
if (!empty($series)) {
    $sql .= " AND series.series_ID = $series";
}
if (!empty($query) && !empty($type)) {
    if ($type == 'isbn') {
        $sql .= " AND details.ISBN = '$query'";
    } elseif ($type == 'author') {
        $sql .= " AND author.auth_name LIKE '%$query%'";
    } elseif ($type == 'title') {
        $sql .= " AND title.book_title LIKE '%$query%'";
    }
}

$result = pg_exec($conn, $sql);

// Print the <option> rows for the <select> widget
if ($result && (pg_numrows($result) > 0)) {
    $row_counter = 0;
    while ($row = pg_fetch_array($result, $row_counter, PGSQL_ASSOC)) {
?>
<tr>
<td><u><?php echo(htmlspecialchars($row['book_title'])); ?></u></td>
<td><?php echo(htmlspecialchars($row['auth_name'])); ?></td>
<td><?php echo(htmlspecialchars($row['price'])); ?></td>
</tr>
<?php
        $row_counter++;
    }
} else {
    echo("<tr><td colspan=\"3\">No matches were found.</td></tr>\n");
}

pg_close($conn);
```

That's all there is to it.

### Database Abstraction

In the last chapter, we also built a simple database abstraction layer. Now that we know about two different databases (MySQL and PostgreSQL), you probably understand the need for such an abstraction layer. We have already discussed the database abstraction layer in the previous chapter, so if you haven't already read the corresponding section in the previous chapter, you may want to do so now. In this section, we will revisit the database abstraction layer and implement the PostgreSQL version.

We already learned how to port a PHP database application from one database to the next in the last section, so we won't go into those details again. Instead, we'll start with a DB.php file that has already been ported to PostgreSQL. The changes from the MySQL version are highlighted:

```php
class DB
{
    /* Connection parameters */
}
```
