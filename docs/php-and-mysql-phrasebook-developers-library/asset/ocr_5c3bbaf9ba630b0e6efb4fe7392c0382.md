The PHP function sqlite_exec() sends a SQL statement to the database using ext/sqlite. As the first parameter, the database handle—returned by sqlite_open()—is used; the second parameter is the SQL string. To avoid SQL injection, the PHP function sqlite_escape_string() escapes dangerous characters in dynamic data. The preceding code implements this for the sample table quotes that have also been used in the MySQL phrases in Chapter 8.

Users of ext/sqlite3 need to execute the exec() method of the SQLite3 class:

```
<?php
try {
    $db = new SQLite3('quotes.db');
    $db->exec(sprintf(
        'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
        $db->escape_string($_POST['quote']),
        $db->escape_string($_POST['author']),
        intval($_POST['year'])));
    echo 'Quote saved.';
    $db->close();
} catch ($ex) {
    echo 'An error has occurred.';
}
?>
```

Sending SQL to SQLite3 (sqlite3_exec.php; excerpt)

TIP: If a table contains an identity column (data type INTEGER PRIMARY KEY when using SQLite), calling the sqlite_last_insert_rowid() function (for ext/sqlite) or the lastInsertRowID() method (for ext/sqlite3) after sending a SQL statement returns the value this column has for the new entry in the database.