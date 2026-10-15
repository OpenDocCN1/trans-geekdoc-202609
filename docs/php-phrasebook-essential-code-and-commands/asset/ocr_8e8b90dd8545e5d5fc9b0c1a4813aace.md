# Sending SQL to SQLite

# sqlite_exec()

The PHP function sqlite_exec() sends an SQL statement to the database. As the first parameter, the database handle—returned by sqlite_open()—is used; the second parameter is the SQL string. To avoid SQL injection, the PHP function sqlite_escape_string() escapes dangerous characters in dynamic data. The preceding code implements this for the sample table quotes that has also been used in the MySQL phrases.

```
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error))
{
require_once 'stripFormSlashes.inc.php';
sqlite_exec($db, sprintf(
'INSERT INTO quotes (quote, author, year)
VALUES (\'%s\', \'%s\', \'%s\')',
sqlite_escape_string($_POST['quote']),
sqlite_escape_string($_POST['author']),
intval($_POST['year'])));
echo 'Quote saved.';
sqlite_close($db);
} else {
echo 'Connection failed: ' . htmlspecialchars
($error);
}
?>
```

Sending SQL to SQLite (sqlite_exec.php; excerpt)