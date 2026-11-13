
**Passwords** Neither the PHP warning nor the message from `mysql_error` contains the password used when the reason for failure is an invalid logon attempt.

## Summary

In this lesson you have learned how to use PHP's interface to the MySQL database system. In the next lesson you will learn how PHP can communicate with different database back ends by using a database abstraction layer.

## Lesson 20. Database Abstraction

In this lesson you will learn how to access different databases from PHP, using a single interface. Database abstraction is a very powerful technique; it allows you to write scripts for a nonspecific database back end, which you can then easily port simply by changing the connection parameters.

## The PEAR DB Class

Many different database abstraction layers are available for PHP, but the one you will learn how to use in this lesson is the PEAR DB class. In Lesson 25, "Using PEAR," you will find out more about PEAR, the PHP Extension and Application Repository, and some other useful classes it contains.

The DB class implements database abstraction, using PHP's database extensions, and it currently supports the extensions shown in Table 20.1.

### Table 20.1. PHP Database Extensions supported by the PEAR DB Class

| Extension | Database |
|---|---|
| dbase | dBase (.dbf) |
| fbsql | FrontBase |
| ibase | Firebird/Interbase |
| ifx | Informix |
| msql | Mini SQL |
| mssql | Microsoft SQL Server |
| mysql | MySQL |
| mysqli | MySQL 4.1 and higher |
| oci8 | Oracle versions 7, 8, and 9 |
| odbc | ODBC |
| pgsql | PostgreSQL |
| sqlite | SQLite |
| Sybase | Sybase |

> **DB Class Documentation** The online documentation for the PEAR DB class can be found at http://pear.php.net/package/DB.

## Installing the DB Class

To check whether the DB class is installed on your web server, you can run the following command to display a list of installed packages:

```
$ pear list
```

If you need to install the DB class, you run the following command:

```
$ pear install DB
```

Note that you need to be an admin to install a PEAR class, so if you are using a shared web hosting service, you might need to contact your system administrator.

Because the underlying PHP extensions are used, no additional database drivers are needed to communicate with each type of database from the DB class.

> **Further Reading** To learn about the MySQL database, read *Sams Teach Yourself MySQL in 24 Hours* by Julie Meloni. Or, for a quick SQL language guide, refer to *Sams Teach Yourself SQL in 10 Minutes* by Ben Forta.

## Data Source Names

To connect to a database through the DB class, you need to construct a valid data source name (DSN), which is a single string that contains all the parameters required to connect and is formed in a similar manner to a URL that you might use to access a protected web page or FTP server.

The following DSN can be used to connect to a MySQL database running on localhost:

```
mysql://chris:mypassword@localhost/mydb
```

The components of this DSN are the database back-end type (mysql), username (chris), password (mypassword), host (localhost), and database name (mydb).

The full syntax definition for a DSN is as follows, and the components that it can be constructed from are given in Table 20.2.

```
phptype(dbsyntax)://username:password@protocol+hostspec/
database?option=value
```

### Table 20.2. Components of a DSN

| Component | Description |
|---|---|
| phptype | Database back-end protocol to use (for example, mysql, oci8) |
| dbsyntax | Optional parameters related to SQL syntax; for ODBC, should contain the database type (for example, access, mssql) |
| username | Username for database login |
| password | Password for database login |
| protocol | Connection protocol (for example, tcp, unix) |
| hostspec | Host specification, either hostname or hostname:port |
| database | Database name |
| option | Additional connection options; multiple options are separated by & |

As shown in the first example of connecting to MySQL, not every component of the DSN is required. The exact syntax depends on what information your database back end needs.

For instance, a connection to SQLite which requires no username, password, or hostspec would look like the following:

```
sqlite:///path/to/dbfile
```

On the other hand, a connection to a PostgreSQL server that is not running on a standard port number would require something more complex like this:

```
pgsql://username:password@tcp(hostname:port)/dbname
```

Database Types The database type values for the phptype argument are the values shown in the first column of Table 20.1.

## Using the DB Class

To begin using the DB class in scripts, you simply include it by using the following statement:

```
include "DB.php";
```

To make a connection to a database, you call the connect method on the DB class, giving your DSN as the argument:

```
$db = DB::connect($dsn);
```

The $db return value is an object on which the DB class methods can be invoked to perform different types of database operation.

> **Database Objects** Note that you cannot create a new instance of a DB object by using the `new` keyword. You must call `DB::connect` to begin a new database session.

If the database connection fails, the return value is a DB_Error object, which you can analyze by using the `isError` and `getMessage` methods. The following code shows a database connection attempt with error checking:

```
$db = DB::connect($dsn);
if (DB::isError($db)) {
    echo "Connection error: " . $db->getMessage();
    exit;
}
```

The function `isError` returns `True` only if the argument passed is a `DB_Error` object, which indicates a problem of some kind with the database connection. You can then call the `getMessage` method on the `DB_Error` object to retrieve the actual error message from the database server.

> **Connection Errors** `$db` is assigned an object value of some kind, whether or not the connection is successful. Its value will never be `NULL` or `FALSE`.

## Performing a Query

To execute a SQL query through the DB class, you use the query method. The return value depends on the type of query being executed, but in the event of any error, a DB_Error object is returned, and the error can be detected and diagnosed in the same way as can connection errors.

The following example executes the query stored in $sql with error checking:

```php
$res = $db->query($sql);
if (DB::isError($res)) {
    echo "Query error " . $res->getMessage();
    exit;
}
```

If the query submitted is an INSERT, UPDATE, or DELETE statement, the return value is the constant DB_OK. You can find out the number of rows affected by the statement by calling the affectedRows method on the database object itself, as shown in the following example:

```php
$sql = "UPDATE mytable SET col2 = 'newvalue' WHERE coll > 5";
$res = $db->query($sql);
echo $db->affectedRows() . " row(s) were affected";
```

## Retrieving Selected Data

If you issue a SELECT statement, the return value from the query is a DB_Result object, which can then be used to access records from the result data set.

To view the number of rows and columns in the data set, you use the numRows and numCols methods, respectively, as in this example:

```php
$sql = "SELECT * FROM mytable";
$res = $db->query($sql);
echo "Query found " . $res->numRows . " row(s) ".
    "and " . $res->numCols . " column(s)";
```

You can use the fetchRow method on a DB_Result object to return a row of data at a time in an array structure. The result pointer is then increased so that each subsequent call to fetchRow returns the next row of data, in order. The following code shows how you can fetch all the rows returned by a query by using fetchRow in a loop:

```php
$sql = "SELECT coll, col2 FROM mytable";
$res = $db->query($sql);
while ($row = $res->fetchRow()) {
    echo "coll = " . $row[0] . ", ";
    echo "col2 = " . $row[1] . "<br>";
}
```
