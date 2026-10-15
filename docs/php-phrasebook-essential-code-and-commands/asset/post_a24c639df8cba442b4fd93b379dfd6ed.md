
```php
} else {
    echo 'Connection failed.';
}
?>
```

Sending SQL to Oracle (oci_execute.php; excerpt)

To send SQL to Oracle, two steps are required. First, a call to oci_parse() parses an SQL string and returns a resource that can then be executed using oci_execute(). The second parameter of oci_execute() is quite important. Several constants are allowed, but most of the time, OCI_DEFAULT is used. Despite the name, that's not the default value, but means "no auto-commit." On the other hand, OCI_COMMIT_ON_SUCCESS commits the pending transaction when no error has occurred. And this is, indeed, the default value.

Unfortunately, there is no such thing as oci_escape_string() to escape special characters for use in an SQL statement. Therefore, prepared statements are a must— but are also very easy to implement. For this, the SQL statement must contain placeholders that start with a colon:

```php
$sql = 'INSERT INTO quotes (quote, author, year)
    VALUES (:quote, :author, :year)';
```

Then, these placeholders have to be filled with values. For this, oci_bind_by_name() must be used:

```php
oci_bind_by_name($stmt, ':quote', $_POST['quote']);
```

The preceding code sends some form data to the database. No worries about special characters because oci_bind_by_name takes care of that.

## Sending SQL to Oracle

> When you are using OCI_DEFAULT as the commit mode, the changes must be written to the database using oci_commit($db); oci_rollback($db) performs a rollback.

> By the way, if you want to retrieve the autovalue of the most recent INSERT operation, you have to do it within a transaction and execute SELECT quotes_id.CURRVAL AS id FROM DUAL, where quotes_id is the name of the sequence you are using.

## Retrieving Results of a Query to Oracle

```php
oci_fetch_object($stmt)
```

You have several ways to access the return values of an SQL query, but the following functions are used most often in practice:

- oci_fetch_assoc() returns the current row in the resultset as an associative array.
- oci_fetch_object() returns the current row in the resultset as an object.
- oci_fetch_row() returns the current row in the resultset as a numeric array.
- oci_fetch_all() returns the complete resultset as an array of associative arrays. However, five parameters are required: the statement object from oci_parse(), the array that is used for the return data, the number of lines to skip, the maximum number of rows to be returned (-1 means infinite), and whether to return a numeric (OCI_NUM) or associative (OCI_ASSOC) array.

The listing in this phrase uses a while loop and oci_fetch_object() to retrieve all data in the table.

```php
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @oci_connect('scott', 'tiger', 'orcl'))
    {
        $stmt = oci_parse($db, 'SELECT * FROM quotes');
        oci_execute($stmt, OCI_COMMIT_ON_SUCCESS);
        while ($row = oci_fetch_object($stmt)) {
            printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
                htmlspecialchars($row->ID),
                htmlspecialchars($row->QUOTE),
                htmlspecialchars($row->AUTHOR),
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

*Retrieving Data from Oracle (oci_fetch.php; excerpt)*

> NOTE
> Oracle always returns column names in uppercase.
> Therefore, you have to use uppercase object properties or uppercase associative array keys when accessing the return values of an SQL query.

## Connecting to MSSQL

```php
@mssql_connect()
```

The Microsoft SQL engine comes in two flavors: the fully featured (and fully priced) Microsoft SQL Server (short: MSSQL) and the free edition, the Microsoft SQL Server Desktop Engine (short: MSDE), available for free at http://www.asp.net/msde/. Both versions are supported by PHP because they are compatible to each other. To make it work, you need the line `extension=php_mssql.dll` in your php.ini. Also, PHP needs access to the client libraries for MSSQL/MSDE, the file `ntwdbllib.dll`. In PHP 5, this file is in the PHP directory, so the PHP process just needs read access to it. In PHP 4, you might have to copy the file (that resides in the dll subdirectory) somewhere else, for example in the Windows system32 folder.

However, UNIX/Linux systems can also connect to MSSQL/MSDE installations in a heterogenous network, a combination that powers some high-traffic websites. For this to work, you have to download the FreeTDS library from http://www.freetds.org/ and install it after unpacking the distribution with this command:

```
./configure --prefix=/usr/local/tds --with-tdsver=4.2
make
sudo make install
```

Then, reconfigure PHP with the switch --with-sybase=/usr/local/freetds.

Finally, you can connect to the server using mssql_connect() and select the database to be used using mssql_select_db(), as the preceding listing shows.

```php
<?php
    if ($db = @mssql_connect('localhost', 'user',
        'password')) {
        mssql_select_db('phrasebook');
        echo 'Connected to the database.';
        mssql_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```

*Connecting to MSSDE/MSDE (mssql_connect.php)*

MSSQL/MSDE supports two modes to authenticate users: SQL authentication and Windows authentication. The latter one checks whether the current Windows user has sufficient rights to access the database. In a controlled environment, this might be a better idea than using username and password. However, you first have to find out which user is used. For instance, Microsoft IIS web server software uses the Internet guest account, that is, IUSR_<machinename>. Therefore, this user requires privileges in the database.

To use Windows authentication—sometimes also called trusted connection—you need the following php.ini directive:

```
mssql.secure_connection = On
```

## Sending SQL to MSSQL

### mssql_query()

The function mssql_query() sends an SQL statement to the MSSQL/MSDE installation. Again, the parameter order is a bit strange: first the SQL command, then the database handle. However, as you saw in the previous listing in the call to mssql_select_db(), this information can also be omitted—then, the last connection established is used automatically.

Another important point is escaping special characters. In MSSQL/MSDE, single quotes must not be escaped using a backslash, but double quotes are the way to go:

```
INSERT INTO quotes (quote, author, year) VALUES ('Ain''t Misbehavin''', 'Louis Armstrong', 1929)
```

To achieve this, addslashes() can be used—however, first, it has to be configured to behave so that MSSQL/MSDE-compatible strings are returned:

```
ini_set('magic_quotes_sybase', 'On');
$author = addslashes($_POST['author']);
```

```php
<?php
if ($db = @mssql_connect('localhost', 'user', 'password')) {
    require_once 'stripFormSlashes.inc.php';
    mssql_select_db('phrasebook', $db);
    ini_set('magic_quotes_sybase', 'On');
    mssql_query(sprintf(
        'INSERT INTO quotes (quote, author, year)
        VALUES (\'%s\', \'%s\', \'%s\')',
        addslashes($_POST['quote']),
        addslashes($_POST['author']),
        intval($_POST['year']), $db);
    echo 'Quote saved.';
    mssql_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*Sending SQL to MSSQL/MSDE (mssql_execute.php; excerpt)*

The listing at the beginning of this phrase sanitizes some form data and writes it to the (by now) well-known sample database.

## Retrieving Results of a Query to MSSQL

```php
$result = mssql_query();
mssql_fetch_assoc($result);
```

Finally, there is, of course, also a way to retrieve all data in the resultset. A while loop comes into play, using one of these functions:

- mssql_fetch_assoc() returns the current row in the resultset as an associative array
- mssql_fetch_object() returns the current row in the resultset as an object
- mssql_fetch_row() returns the current row in the resultset as a numeric array
