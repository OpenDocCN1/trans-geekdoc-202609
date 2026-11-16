```
function error()
{
    return (mysql_error());
}
```

This function calls the mysql_error() function and returns the resulting error message. The mysql_error() function returns a string describing the last error that occurred inside the PHP MySQL extension.

We can now extend our test program to including functions that open and close connections to the database and report error messages on failure:

```
<?php
require_once("DB.php");

$db = new DB('localhost', 'jon', 'secret', 'Library');

if (! $db->open()) {
    die($db->error());
}

if (! $db->close()) {
    die($db->error());
}
?>
```

Now that we can open and close database connections, we can add some real functionality to our database abstraction class.

The query() function allows us to pass SQL statements to the database server. In this implementation, we simply call mysql_query() with the given SQL statement. The result of the query is stored in the $this->result instance variable.

Different types of queries return different results. For example, SELECT queries return a resultset while DELETE queries simply indicate the success of their operation. They have one thing in common, however: they all return false on failure. Because we want our abstract query() function to return true on success and false on failure, we test for a false return value from mysql_query(). If we don't receive a false value, we can assume the query was successful, and our function will return true. Otherwise, our function returns false:

```
function query($sql)
{
    $this->result = @mysql_query($sql, $this->conn);
    return($this->result != false);
}
```

Now that our database abstraction class supports queries, we can start working with results:

```
function affectedRows()
{
    return(@mysql_affected_rows($this->conn));
```