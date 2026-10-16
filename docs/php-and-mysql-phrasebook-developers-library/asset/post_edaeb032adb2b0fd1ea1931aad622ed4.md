
```php
htmlspecialchars($row->YEAR)
);
}
oci_close($db);
} else {
echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

Retrieving Data from Oracle (oci_fetch.php; excerpt)

You have several ways to access the return values of a SQL query, but the following functions are used most often in practice:

- oci_fetch_assoc() returns the current row in the resultset as an associative array.
- oci_fetch_object() returns the current row in the resultset as an object.
- oci_fetch_row() returns the current row in the resultset as a numeric array.
- oci_fetch_all() returns the complete resultset as an array of associative arrays. However, five parameters are required: the statement object from oci_parse(), the array that is used for the return data, the number of lines to skip, the maximum number of rows to be returned (-1 means infinite), and whether to return a numeric (OCI_NUM) or associative (OCI_ASSOC) array.

The listing in this phrase uses a while loop and oci_fetch_object() to retrieve all data in the table.

## CHAPTER 9 Working with Other Databases

NOTE: Oracle always returns column names in upper-case. Therefore, you have to use uppercase object properties or uppercase associative array keys when accessing the return values of a SQL query.

```php
<?php
$config = array('UID' => 'user', 'PWD' =>
'password',
'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('localhost\SQLExpress',
$config)) {
	echo 'Connected to the database.';
	sqlsrv_close($db);
} else {
	echo 'Connection failed.';
}
?>
```

The Microsoft SQL engine comes in two flavors: the fully featured (and fully priced) Microsoft SQL Server (short: MSSQL) and the free edition, the Microsoft SQL Server Express Edition, available for free at www.microsoft.com/sqlserver/en/us/editions/express.aspx. Both versions are supported by PHP because they are compatible with each other.

PHP ships with an extension for MSSQL, ext/mssql. However it is quite old and not actively maintained any more. Instead, Microsoft provides a new (Windows-only) extension, ext/sqlsrv, which is the recommended one to use.

To make it work, you need to add the extension using extension=<filename>.dll in your php.ini. Also, you need the extension itself. Depending on which version of PHP you are using, you need a specific version. The PHP manual page http://php.net/sqlsrv.installation points you to the correct download page. If possible, you should use at least version 3 of the extension, which uses the Microsoft SQL Server 2012 Native Client libraries; version 2 requires the Microsoft SQL Server 2008 R2 Native Client libraries. Microsoft describes the up-to-date system requirements at http://msdn.microsoft.com/en-us/library/cc296170.aspx.

To connect to MSSQL, call mssql_connect() and provide the name of the server ((local) serves as shortcut for localhost); if you are using a named instance of Microsoft SQL Server (for example, SQLEXPRESS, which is installed with the MSSQL Express Edition by default), you append it to the server name, separated by a backslash: (local)\SQLEXPRESS. As the second argument, you can provide an array with connection information. The following array keys are supported by the extension:

- Database—Name of the database
- PWD—Password
- UID—Username

If you want to authenticate against the database with the current user (sometimes also called trusted connection), just omit the UID and PWD configuration settings.

### Sending SQL to MSSQL

```php
<?php
$config = array('UID' => 'user', 'PWD' =>
'password', 'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('localhost\SQLEXPRESS')) {
ini_set('magic_quotes_sybase', 'On');
sqlsrv_query($db, sprintf(
"INSERT INTO quotes (quote, author, year) VALUES (\'%s\', \'%s\', \'%s\')",
addslashes($_POST["quote"]),
addslashes($_POST["author"]),
intval($_POST["year"])));
echo 'Quote saved.';
sqlsrv_close($db);
} else {
echo 'Connection failed.';
}
?>
```

Sending SQL to MSSQL (sqlsrv.execute.php; excerpt)

The function sqlsrv_query() sends a SQL statement to the MSSQL installation. The parameter order is similar to the one from ext/mysql: first the database handle, then the SQL command.

Another important point is escaping special characters. In MSSQL, single quotes must not be escaped using a backslash, but double quotes are the way to go:

INSERT INTO quotes (quote, author, year) VALUES ('Ain\'t Misbehavin\'', 'Louis Armstrong', 1929)

To achieve this, you can use addslashes(). However, first, you must configure it to behave so that MSSQL/MSDE-compatible strings are returned:

```php
ini_set('magic_quotes_sybase', 'On');
$author = addslashes($_POST['author']);
```

One word of warning, though: The magic_quotes_sybase setting has been deprecated in PHP 5.3 and removed in PHP 5.4. If you are using user information in SQL statements, you should use prepared statements instead (two phrases onward). The listing at the beginning of this phrase sanitizes some form data and writes it to the (by now) well-known sample database.

### Retrieving Results of a Query to MSSQL

```php
$result = sqlsrv_query();
sqlsrv_fetch_object($result);
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
$config = array('UID' => 'user', 'PWD' => 'password', 'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('(local)\SQLEXPRESS', $config)) {
    $result = sqlsrv_query($db, 'SELECT * FROM quotes');
    while ($obj = sqlsrv_fetch_object($result)) {
        printf(
```

```php
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s
</td></tr>',
htmlspecialchars($row->id),
htmlspecialchars($row->quote),
htmlspecialchars($row->author),
htmlspecialchars($row->year)
);
sqlsrv_close($db);
} else {
echo '<tr><td colspan="4">Connection
failed.</td></tr>';
}
?>
</table>
```

*Retrieving Data from MSSQL (sqlsrv_fetch.php; excerpt)*

Finally, there is, of course, a way to retrieve all data in the resultset. A while loop comes into play, using one of these functions:

- sqlsrv_fetch_array() returns the current row in the resultset as an associative array and/or a numerically indexed array; by default, it returns both.
- sqlsrv_fetch_object() returns the current row in the resultset as an object.

### Using Prepared Statements with MSSQL

```php
$stmt = sqlsrv_query();
sqlsrv_execute($stmt);
```

```php
<?php

$config = array('UID' => 'user', 'PWD' => 'phrasebook', 'Database' => 'phrasebook');
if ($db = @sqlsrv_connect('(local)\SQLEXPRESS', $config)) {
    $year_as_int = intval($_POST['year']);
    $data = array(&$_POST['quote'], &$_POST['author'], &$year_as_int);
    $stmt = sqlsrv_query(
        $db,
        'INSERT INTO quotes (quote, author, year)
VALUES (?, ?, ?)',
        $data);
    sqlsrv_execute($stmt);
    echo 'Quote saved.';
    sqlsrv_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

Retrieving Data from MSSQL with Prepared Statements
(sqlsrv_prepare.php; excerpt)

Because there is no designated escaping functions in ext/sqlsrv, prepared statements are the only viable way to use user-supplied data in SQL statements and to avoid SQL injection. As usual, two steps must be taken. First, you create a statement object (the function to be used here is sqlsrv_prepare() with placeholders, and then you execute this statement. While preparing the statement, you also have to provide the data for the placeholders.

The ext/sqlsrv extensions expects a question mark (?) for each placeholder. The values for those placeholders are provided in an array, in the exact order as the placeholders in the SQL statement. These values can be passed by reference.

### Using MSSQL without Windows

```php
$db = @mssql_connect();
$result = mssql_query();
mssql_fetch_assoc($result);
```

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
if ($db = @mssql_connect('localhost', 'user', 'password')) {
    mssql_select_db('phrasebook', $db);
    $result = mssql_query('SELECT * FROM quotes', $db);
    while ($row = mssql_fetch_assoc($result)) {
        print(
            '<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            htmlspecialchars($row['id']),
            htmlspecialchars($row['quote']),
            htmlspecialchars($row['author']),
            htmlspecialchars($row['year'])
        );
    }
    mssql_close($db);
} else {
    echo '<tr><td colspan="4">Connection failed.</td></tr>';
}
?>
</table>
```

*Retrieving Data from MSSQL with ext/mssql (mssql_fetch.php; excerpt)*
