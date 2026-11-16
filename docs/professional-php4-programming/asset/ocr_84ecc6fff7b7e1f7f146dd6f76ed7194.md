# pg_fetch_object()

object pg_fetch_object(int result, int row [, int result_type])

pg_fetch_object() is used to access the data in a SELECT statement's resultset. It returns a single record of data in the form of an object whose properties correspond to the record's fields. If there are no records left in the resultset, pg_fetch_object() will return false. This function is usually used in a loop.

In the code below, we place pg_fetch_object() in a while loop to process each record in the set. Each call of pg_fetch_object() automatically moves to the next record in the resultset. At the end of the set, pg_fetch_object()'s resulting false will cause the loop to end:

```
<?php
//Fetch_Object.php
$conn = pg_connect("dbname=library user=postgres") or
    die(pg_errormessage());
$sql = "SELECT ISBN, book_title FROM title";
$result = pg_exec($conn, $sql);
$row_counter = 0;
while ($row = @pg_fetch_object($result, $row_counter)) {
    echo("ISBN: " . htmlspecialchars($row->ISBN) .
        ", Title: " . htmlspecialchars($row->book_title) . "<br>");
    $row_counter++;
}
pg_freeresult($result);
pg_close($conn);
?>
```

Note the use of the @ operator to suppress errors from the call to pg_fetch_object(). In the above code, pg_fetch_object() will generate a warning like "Unable to jump to row 2 on PostgreSQL result index 2" when it runs out of rows. We already test for that condition and hence suppressing the warning will do no harm.

The individual fields are accessed as properties of the returned object. We use htmlspecialchars() to ensure that odd characters in the data (such as < or &) cannot wreak havoc in the browser.

# pg_fetch_row()

array pg_fetch_row(int result, int row)

pg_fetch_row() is very similar to pg_fetch_object(), except for what it returns. Instead of returning an object, it returns a numerically indexed array containing the field values:

```
<?php
//Fetch_Row.php
$conn = pg_connect("dbname=library user=postgres") or
    die(pg_errormessage());
$sql = "SELECT ISBN, book_title FROM title";
$result = pg_exec($conn, $sql);
$row_counter = 0;
```