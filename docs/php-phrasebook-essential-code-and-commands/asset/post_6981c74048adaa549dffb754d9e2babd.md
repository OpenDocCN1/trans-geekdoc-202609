
## Sending SQL to MySQL

```php
mysql_real_escape_string($_POST['quote'], $db),
 mysql_real_escape_string($_POST['author'], $db),
 intval($_POST['year'])), $db);
 echo 'Quote saved.';
 mysql_close($db);
 } else {
 echo 'Connection failed.';
 }
 ?>
```

*Sending SQL to MySQL (mysql_query.php; excerpt)*

![](img/1e6d362f187af50011d2666ddaa68739_210_0.png)

**Figure 7.2** The HTML input form for Listings 7.3 and 7.4.

## Prepared Statements with MySQL

```php
$stmt = mysqli_prepare();
mysqli_stmt_execute($stmt);
```

The new MySQL extension offers a way to both avoid SQL injection and to speed up SQL statements: so-called prepared statements. Within them, you provide placeholders for any dynamic data you are using in the SQL code. You then assign values to those placeholders. The MySQL extension then takes care of all the rest, including escaping of special characters.

```php
<?php
if ($db = @mysqli_connect('localhost', 'user', 'password')) {
    require_once 'stripFormSlashes.inc.php';
    mysqli_select_db($db, 'phrasebook');
    $stmt = mysqli_prepare($db, 'INSERT INTO quotes (quote, author, year) VALUES (?, ?, ?)');
    $quote = mysqli_real_escape_string($db, $_POST['quote']);
    $author = mysqli_real_escape_string($db, $_POST['author']);
    $year = intval($_POST['year']);
    mysqli_stmt_bind_param($stmt, 'ssi', $quote, $author, $year);
    if (mysqli_stmt_execute($stmt)) {
        echo 'Quote saved. ';
    } else {
        echo 'Error writing quote.';
    }
    mysqli_close($db);
} else {
    echo 'Connection failed. ';
}
?>
```

So first, you prepare an SQL statement with `mysqli_prepare()`; as a placeholder character, you use a question mark:

```php
$stmt = mysqli_prepare($db, 'INSERT INTO quotes
    (quote, author, year) VALUES (?, ?, ?)');
```

Then, you bind values to each parameter. First, you provide the statement returned by `mysqli_prepare()`, then one-character codes for the values of all parameters (s for string, i for integer, d for double). Finally, you provide a list of values. Because these values are used by reference, you have to provide variables, not raw values.

```php
mysqli_stmt_bind_param($stmt, 'ssi', $quote,
    $author, $year);
```

Finally, `mysqli_stmt_execute()` executes the prepared statement.

### NOTE

The ext/mysqli extension supports some of the new features of recent MySQL versions, including transactions. For this, the following functions are available:

- `mysqli_autocommit($db, false)` deactivates autocommit
- `mysqli_rollback($db)` rolls back all pending transactions
- `mysqli_commit($db)` commits all pending transactions

> **TIP**
> When using auto_increment values, the functions `mysql_insert_id()` and `mysqli_insert_id()` return the value of the auto_increment field of the last INSERT SQL statement created.

## Retrieving Results of a Query to MySQL

```php
$result = mysqli_query(query);
mysql_fetch_object($result);
```

The return value of `mysql_query()` or `mysqli_query()` is a pointer to the actual resultset. It can be used to iterate through the complete list of entries returned by a SELECT statement. For this, these functions come in handy:

- `mysql_fetch_assoc()` and `mysqli_fetch_assoc()` return the current row in the resultset as an associative array (field names become keys) and move farther to the next row.
- `mysql_fetch_object()` and `mysqli_fetch_object()` return the current row in the resultset as an object (field names become properties) and move farther to the next row.
- `mysql_fetch_row()` and `mysqli_fetch_row()` return the current row in the resultset as a numeric array and move farther to the next row.

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @mysqli_connect('localhost', 'user', 'password')) {
        mysqli_select_db($db, 'phrasebook');
        $result = mysqli_query($db, 'SELECT * FROM quotes');
        while ($row = mysqli_fetch_object($result)) {
            printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
                htmlspecialchars($row->id),
                htmlspecialchars($row->quote),
                htmlspecialchars($row->author),
                htmlspecialchars($row->year)
            );
        }
        mysqli_close($db);
    } else {
        echo '<tr><td colspan="4">Connection failed.</td></tr>';
    }
?>
</table>
```

*Retrieving Data from MySQL (mysqli_fetch.php; excerpt)*

There are other functions, as well; however, these three are the ones that are used more often. The following code uses `mysql_fetch_assoc()`, whereas the preceding listing prints out the contents of the database table with `mysqli_fetch_object()`. The main idea is to use a while loop—all `mysql_fetch_*`/`mysqli_fetch_*` functions return false when no data is left in the resultset.

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @mysql_connect('localhost', 'user',
        'password')) {
    mysql_select_db('phrasebook', $db);
    $result = mysql_query('SELECT * FROM quotes',
        $db);
    while ($row = mysql_fetch_assoc($result)) {
        printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    mysql_close($db);
} else {
    echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

*Retrieving Data from MySQL (mysql_fetch.php; excerpt)*

Figure 7.3 shows the contents of the database after some (political) quotes have been filled in. Sorry, I am from abroad—I took the first ones I found.

![](img/1e6d362f187af50011d2666ddaa68739_216_0.png)

**Figure 7.3** The contents of the database.

## Connecting to SQLite

```php
@sqlite_open('quotes.db', 0666, $error)
```

Starting with PHP 5, SQLite is bundled with the scripting language. This is a lightweight, file-based database. That allows very fast reading (in many cases, even faster than when using a “real” database), but writing can sometimes take longer than with other systems because file locking is an issue. However, PHP 4 users can also use SQLite as there is a PECL (PHP Extension Community Library) module available at http://pecl.php.net/.

```php
<?php
if ($db = @sqlite_open('quotes.db', 0666, $error))
{
echo 'Connected to the database.';
sqlite_close($db);
} else {
echo 'Connection failed: ' . htmlspecialchars
    ($error);
}
?>
```

*Connecting to SQLite (sqlite_open.php)*

If you use PHP 5, SQLite support is already included; when using PHP 4, use `pear install SQLite` or, when Windows is the operating system of your choice, load the current SQLite binary extension at http://snaps.php.net/win32/PECL_STABLE/php_sqlite.dll, copy it to PHP’s extension folder, and then load it using `extension=php_sqlite.dll` in your `php.ini`.

Then, you can connect to a SQLite data source using `sqlite_open()`. As the first parameter, you provide the name of the database file (it gets created if it doesn’t exist yet). For this to work, the PHP process needs read and write privileges to the file. The second parameter is the file open mode (0666 is recommended); however, as of this writing, this parameter is ignored. The third parameter is a variable that contains any error messages (such as insufficient rights).

### NOTE

Just like ext/mysqli, the SQLite extension under PHP 5 can also be accessed using an object-oriented programming (OOP) approach:

```php
<?php
$db = new SQLiteDatabase('quotes.db');
echo 'Connected to the database.';
$db->close();
?>
```

For the sake of backward compatibility, this chapter uses the functional approach for the subsequent phrases.

## Sending SQL to SQLite

### sqlite_exec()

The PHP function `sqlite_exec()` sends an SQL statement to the database. As the first parameter, the database handle—returned by `sqlite_open()`—is used; the second parameter is the SQL string. To avoid SQL injection, the PHP function `sqlite_escape_string()` escapes dangerous characters in dynamic data. The following code implements this for the sample table quotes that has also been used in the MySQL phrases.

```php
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

*Sending SQL to SQLite (sqlite_exec.php; excerpt)*
