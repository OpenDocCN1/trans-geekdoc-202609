
below for the **DB_common** class. Also, some limitations and usage information is provided in the discussion of the **autoExecute()** method on page 66.

## Introductory Summary

This ends the introductory information to PEAR::DB. The above high-level overview outlines the major concepts in PEAR::DB. The following sections detail the PEAR::DB classes and their methods and properties.

## Class DB

The main **DB** class is really just a container class consisting of some static methods and utility functions that are general to PEAR::DB. The static methods listed in Table 3 are defined in the **DB** class.

| Method | Description |
|---|---|
| `factory()` | Creates a new database connection object of a specific type. Does not actually establish a connection. |
| `connect()` | Creates a new database connection object and establishes a connection to the database server. |
| `apiVersion()` | Returns the DB API version. |
| `isError()` | Checks if the passed parameter is an error object. |
| `isConnection()` | Checks if the passed parameter is a DB connection type. |
| `isWarning()` | Checks if the passed parameter is a warning object. |
| `isManip()` | Checks if the passed SQL statement is a data manipulation query or a data definition query. |
| `errorMessage()` | Returns a textual error message for a numeric DB error code or DB_Error object. |
| `parseDSN()` | Returns a fully parsed DSN from a DSN string. This method is unlikely to be used directly and may normally be considered a private method. |
| `assertExtension()` | Loads a particular PHP extension dynamically as needed. This method is unlikely to be used directly and may normally be considered a private method. |

Table 3: DB Class Methods

### DB::factory

`mixed factory( string $type )`

Creates a new DB connection object, but does not connect to the database server. The *type* parameter is a string value containing just the type of database object to create. Valid values are shown in the *phptype* column of Table 1 on page 19.

Returns either the newly created DB object or a **DB_Error** object.

Typically this method is not used as the **connect()** method performs both DB object creation and connection. However, there may be instances where creating a DB object without a connection is preferable.

Note that if you choose to use the **factory()** method to obtain a DB object, then use the object’s **connect()** method, you will need to set the options of the DB object manually. Also, you will need to call **parseDSN()** directly as the instantiated DB object expects a parsed DSN, not a DSN string. An example of this is shown in Code Listing 13.

```php
<?php
require_once( 'DB.php' );

// create an unconnected MySQL DB object
$oDB = DB::factory( 'mysql' );
if ( DB::isError( $oDB ) )
{
    print( 'Unable to create MySQL DB object<br>' );
    exit;
}

$oDB->setOption( 'optimize', 'portability' );

$result = $oDB->connect( DB::parseDSN(
'mysql://bt_user:bt_user:bt_password@207.44.182.3/book_test'
) );
if ( DB_OK == $result )
{
    // do DB work, then disconnect
    //$oDB->disconnect();
}
else
{
    // $result is a DB_Error object
    print( 'Unable to connect to MySQL' . $result->getMessage() . '<br>' );
    exit;
}
?>
```

### Code Listing 13: DB::factory

In Code Listing 13, the object is created on line 5. Only the database type is specified by the call to **factory()**. The result is checked for validity, then an option is set on line 12. On line 14, the actual connection to the database server is made. Note that the DSN string passed to the **parseDSN()** method contains the database type. This is necessary for the parsing to succeed (see Code Listing 7 on page 18 for a listing of valid DSN string formats). Be sure that the database type used in the **factory()** method matches the database type specified in the DSN used to make the actual connection.

Again, it is recommended to use the **connect()** method in almost all cases.

### DB::connect

`mixed connect( mixed $dsn, mixed $options = false )`

This is the preferred method for creating a new database object and simultaneously connecting to a database server.

The *dsn* parameter is either a DSN string, or a parsed DSN (returned from **DB::parseDSN**). The *options* parameter may be either a Boolean value or an array. When *options* is an array, it must be an associative array whose name/value pairs can be passed to the DB object's **setOption()** method. The default options currently used are shown in Table 2 on page 20. When *options* is a Boolean value, it is interpreted

| Element | Default | Description |
|---|---|---|
| dbsyntax | false | Database used with regards to SQL syntax etc. |
| username | false | User name for login |
| password | false | Password for login |
| protocol | false | Communication protocol to use (tcp, unix etc.) |
| hostspec | false | Host specification (hostname[:port]) |
| port | false | Port on which to connect |
| socket | false | Socket on which to connect |
| database | false | Database to use on the DBMS server |

Table 4: DSN Array Elements

Each back-end database server may use the DSN elements differently. For examples of valid DSNs for each database server, see the sections below that detail specifically the database servers.

### DB::assertExtension

`boolean assertExtension( string $name )`

Loads a PHP extension based on the name parameter passed in. For the purposes of PEAR::DB, the extensions are the database extensions (e.g. mysql, oci8, etc.).

Returns true if the extension is loaded.

```php
<?php
require_once( 'DB.php' );
$aExtensions = array( 'mysql', 'pgsql', 'ibase',
'msql', 'mssql', 'oci8', 'odbc', 'sybase', 'ifx',
'fbsql', 'sqlite', 'dbase' );
foreach( $aExtensions as $aExt )
{
    if ( DB::assertExtension( $aExt ) )
        print( $aExt . ' extension loaded<br>' );
    else
        print( $aExt . ' extension not loaded<br>' );
}
?>
```

### Code Listing 15: DB::assertExtension Example

The example code shown in Code Listing 15 illustrates how to check for each of the supported PEAR::DB database servers. The output for my Windows-based installation is shown in Output 5.

```
1 mysql extension loaded
2 pgsql extension not loaded
3 ibase extension not loaded
4 msql extension not loaded
5 mssql extension not loaded
6 oci8 extension not loaded
7 odbc extension loaded
8 sybase extension not loaded
9 ifx extension not loaded
10 fbsql extension not loaded
11 sqlite extension not loaded
12 dbase extension not loaded
```

Output 5: DB::assertExtension Example Output

## Class DB Summary

Only two members of the DB class are commonly used in an average development project, **connect** and **isError**. The other methods are helpful in certain circumstances, but will be rarely used. Typically the DB class methods will be used statically; there is no need to create an object of type **DB**.

## Class DB_common

Class **DB_common** is the parent class of all of the database-server specific classes. The purpose of **DB_common** is to provide a common interface definition for all the concrete implementation classes. **DB_common** can be thought of, in a way, as an abstract base class since many of the methods defined in **DB_common** do nothing but return an error.

The methods described in this section are the common methods available to all database server classes.

| Method | Description |
|---|---|
| `toString()` | String conversion. This method provides a string representation of the DB_common object. |
| `quoteString()` | Quotes a string so it can be safely used within string delimiters in a query (preserved for compatibility issues, `quote()` is preferred). |
| `quote()` | Preferred method for quoting a string for safe use within queries. |
| `provides()` | Tell whether a DB implementation or its backend extension supports a given feature. |
| `errorCode()` | Map native error codes to portable PEAR::DB codes. |
| `errorMessage()` | Map a DB error code to a textual message. This is actually just a wrapper |
