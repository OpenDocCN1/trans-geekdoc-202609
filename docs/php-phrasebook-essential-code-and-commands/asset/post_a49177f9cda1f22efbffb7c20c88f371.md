
> TIP
> If a table contains an identity column (data type INTEGER PRIMARY KEY when using SQLite), calling `sqlite_last_insert_rowid()` after sending an SQL statement returns the value this column has for the new entry in the database.

## Retrieving Results of a Query to SQLite

```
$result = sqlite_query($db, 'SELECT * FROM quotes');
sqlite_fetch_array($result);
```

The function `sqlite_exec()` from the previous phrase is very quick performing; however, it is not possible to access return values from the SQL statement sent with it. For this, `sqlite_query()` must be used. This function returns a handle of the resultset of the query. The following functions can then be used to iterate over the resultset:

- `sqlite_fetch_array()` returns the current row in the resultset as an associative array (field names become keys) and moves farther to the next row.
- `sqlite_fetch_object()` returns the current row in the resultset as an object (field names become properties) and moves farther to the next row.
- `sqlite_fetch_all()` returns the complete resultset as an array of associative arrays.

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
  if ($db = @sqlite_open('quotes.db', 0666, $error))
  {
    $result = sqlite_query($db, 'SELECT * FROM
      quotes');
    while ($row = sqlite_fetch_array($result)) {
      printf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
        htmlspecialchars($row['id']),
        htmlspecialchars($row['quote']),
        htmlspecialchars($row['author']),
        htmlspecialchars($row['year'])
      );
    }
    sqlite_close($db);
  } else {
    printf('<tr><td colspan="4">Connection failed:
      %s</td></tr>',
      htmlspecialchars($error));
  }
?>
</table>
```

*Retrieving Data from SQLite (sqlite_fetch.php; excerpt)*

The preceding listing shows how to access all data within the resultset using sqlite_fetch_array(). A while loop calls this function as long as it returns something other than false (which means that there is no data left).

> TIP
> 
> Using sqlite_fetch_all() reads the whole resultset into memory at once. So, if you do not have much data, this is the best-performing method. If you have more data, an iterative approach using sqlite_fetch_array() and sqlite_fetch_object() might be better.

## Connecting to PostgreSQL

### @pg_connect()

PostgreSQL has a growing fanbase. Some even say this is because the new version 8.0 finally comes in a native Windows version. However, most productive systems that use PostgreSQL are hosted on Linux or UNIX, nevertheless.

After installing the database, web-based administration software such as phpPgAdmin (http://sourceforge.net/projects/phppgadmin) or other tools such as the graphical user interface (GUI) application pgAdmin (http://www.pgadmin.org/) can be used to administer the database. Alternatively, the command-line tool can be used. To allow PHP to access the PostgreSQL installation, Windows users must load the extension with the entry extension=php_pgsql.dll in php.ini; UNIX/Linux users configure PHP with the switch --with-pgsql=/path/to/pgsql.

Then, pg_connect() connects to the data source. You have to provide a connection string that contains all important data, including host, port, name of the database, and user credentials.

## Sending SQL to PostgreSQL

```
 intval($_POST['year']));
    echo 'Quote saved.';
    pg_close($db);
} else {
    echo 'Connection failed.';
}
?>
```

*Sending SQL to PostgreSQL (pg_query.php; excerpt)*

> NOTE
> Retrieving the value in the identity column after the last INSERT statement is a bit tricky. The PostgreSQL term for such a data type is SERIAL, which automatically creates a sequence. To get the sequence’s value, you can use pg_last_oid() to retrieve the oid (object id) of this value. Then, execute a SELECT id FROM quotes WHERE oid=<oid>, when <oid> is the oid you just retrieved. This finally returns the desired value.

## Updating Data in PostgreSQL

### pg_insert()

Another way to insert or update data in PostgreSQL comes in the form of the functions pg_insert() and pg_update(). The first parameter must be the database handle, the second parameter is the table to be inserted into/updated, and the third parameter contains some data in the form of an associative array (column names are the keys). In the event of an UPDATE SQL statement, the update condition must also be submitted as an array in the fourth parameter of the function. The preceding code shows how to insert data.

```
<?php
if ($db = @pg_connect('host=localhost port=5432
dbname=phrasebook user=postgres
password=abc123')) {
require_once 'stripFormSlashes.inc.php';
$data = array(
'quote' => pg_escape_string($_POST['quote']),
'author' => pg_escape_string($_POST
['author']),
'year' => intval($_POST['year'])
);
pg_insert($db, 'quotes', $data);
echo 'Quote saved.';
pg_close($db);
} else {
echo 'Connection failed.';
}
?>
```

*Sending SQL to PostgreSQL (pg_insert.php; excerpt)*

## Retrieving Results of a Query to PostgreSQL

```
$result = pg_query();
pg_fetch_row($result);
```

The return value of a call to pg_query() is a pointer to a resultset that can be used with these functions:

- pg_fetch_assoc() returns the current row in the resultset as an associative array
- pg_fetch_object() returns the current row in the resultset as an object
- pg_fetch_row() returns the current row in the resultset as a numeric array

- pg_fetch_all() returns the complete resultset as an array of associative arrays

```
<table>
<tr><th>#</th><th>Quote</th><th>Author</th><th>Year</th></tr>
<?php
    if ($db = @pg_connect('host=localhost port=5432
    dbname=phrasebook user=postgres
    password=abc123')) {
    $result = pg_query($db, 'SELECT * FROM quotes');
    while ($row = pg_fetch_row($result)) {
        vprintf(
'<tr><td>%s</td><td>%s</td><td>%s</td><td>%s</td></tr>',
            $row
        );
    }
    pg_close($db);
    } else {
    echo '<tr><td colspan="4">Connection
failed.</td></tr>';
    }
?>
</table>
```

*Retrieving Data from PostgreSQL (pg_fetch.php; excerpt)*

The code uses pg_fetch_row() to read out all data from the quotes table.

Alternatively, pg_select() works similarly to pg_insert() and pg_update(). Just provide a database handle, a table name, and maybe a WHERE clause in the form of an array, and you get the complete resultset as an array of (associative) arrays.

```
$data = pg_select($db, 'quotes');
```

## Connecting to Oracle

### @oci_connect()

Two PHP extensions are available for Oracle, but only one is actively maintained and also works with more recent versions of the RDBMS. To install it, configure PHP with the switch --with-oci8. The environment variable ORACLE_HOME must be set so that PHP can find the client libraries. Windows users need the php.ini directive extension=php_oci8.dll. In addition, PHP requires read access to the client libraries. Then, oci_connect() tries to establish a connection to the server. The order of the parameters is a bit strange: first username and password, then the name of the service (that has been configured using the configuration assistant or is part of the tnsnames.ora file). The return value is a handle to the connection and is required by further operations in the database.

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
 echo 'Connected to the database.';
 oci_close($db);
} else {
 echo 'Connection failed.';
}
?>
```

Connecting to Oracle (oci_connect.php)

> WARNING
> 
> In PHP 4, oci_connect() did not exist yet, so for this version, oci_logon() has to be used. However, this is considered deprecated in PHP 5. Therefore, all Oracle phrases in this chapter use the PHP 5 syntax; however, files with the extension .php4 are included in the download repository that work on older PHP versions.

## Sending SQL to Oracle

### oci_execute()

This section again uses the quotes table, which also includes an identity column; however, this is a bit more complicated to implement with Oracle. Refer to the script quotes.oracle.sql in the download archive for more information.

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
require_once 'stripFormSlashes.inc.php';
$sql = 'INSERT INTO quotes (quote, author, year)
    VALUES (:quote, :author, :year)';
$stmt = oci_parse($db, $sql);
oci_bind_by_name($stmt, ':quote',
    $_POST['quote']);
oci_bind_by_name($stmt, ':author',
    $_POST['author']);
oci_bind_by_name($stmt, ':year',
    intval($_POST['year']));
oci_execute($stmt, OCI_COMMIT_ON_SUCCESS);
echo 'Quote saved.';
oci_close($db);
}
```
