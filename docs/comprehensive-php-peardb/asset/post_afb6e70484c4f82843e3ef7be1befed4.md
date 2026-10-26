
Extensions are likely to be supported in future PEAR::DB releases.

- 3. PEAR::DB provides a consistent interface to error handling through the DB_Error class (a subclass of the PEAR_Error class).

As a software developer, it is nearly impossible to overstate the benefits of standardizing and reusing software components over multiple development projects. If there were no other reason to use PEAR::DB, it would still be worthwhile to every PHP developer just from a reuse perspective alone. There are more reasons to use PEAR::DB, though, and all of these will be explored through the remainder of this document.

The following example should be enough reason for any PHP developer to get excited about PEAR::DB. The code in Code Listing 5 below is an exact duplicate of Code Listing 4, but with the DSN changed on line 4. This simple change in the code has dramatic effects on the run-time behavior of the script. Instead of using MySQL, this script uses ODBC to connect to a Microsoft Access database to retrieve the necessary data.

```php
<?php
require_once( 'DB.php' );
$oDB = DB::connect( 'odbc://book_test', true );
if ( !DB::isError( $oDB ) )
{
    $oDB->setFetchMode( DB_FETCHMODE_ASSOC );
    $query = "SELECT Employees.last_name as emp_last_name, Employees.first_name as emp_first_name, Employees.phone_ext as emp_phone_ext, Departments.name as dept_name, Employees_1.last_name as mgr_last_name, Employees_1.first_name as mgr_first_name, Employees_1.phone_ext as mgr_phone_ext FROM (Departments INNER JOIN Employees ON Departments.id = Employees.dept_id) LEFT JOIN Employees AS Employees_1 ON Employees.mgr_id = Employees_1.id";
}
```

```php
$oRows = $oDB->query( $query );
if ( !DB::isError( $oRows ) )
{
    print( '<table>' );
    while ( $oRow = $oRows->fetchRow() )
    {
        print '<tr>';
        foreach ( $oRow as $col_value ) {
            print "<td>$col_value</td>";
        }
        print '</tr>';
    }
    print( '</table>' );
}
else
{
    print( 'Query failed:' );
    print( $oDB->getMessage() );
    print( '<br>' );
}
}
else
{
    print( 'Unable to connect to database server: ' );
    print( $oDB->getMessage() );
    print( '<br>' );
}
?>
```

## Code Listing 5: PEAR::DB Database Access (Take Two)

The only external requirements to using the examples in Code Listing 4 and Code Listing 5 are that the databases must exist. The Microsoft Access database must have an ODBC DSN (specifically, a system DSN named book_test) set up to point to it as well.

## Summary

No matter the size, scope or requirements of your PHP database application, PEAR::DB is applicable. It provides a consistent, easy-to-read interface to the major database back ends. It standardizes error handling and overall it simplifies the maintenance of PHP applications.

## PEAR::DB In Depth

This section is the detailed reference section intended to provide the in-depth coverage of PEAR::DB and its classes.

### Introduction

Before detailing the classes themselves, it is important to gain a high-level perspective of some of the concepts of using PEAR::DB. These concepts include the Data Source Name (DSN) and generally the methods need to connect to databases and retrieve or modify data. Another high-level concept covered in this section is sequences.

### DSN

To connect to a database using PEAR::DB, you must first create a valid Data Source Name (DSN). For Windows users, it is important to distinguish between a PEAR::DB DSN and an ODBC DSN. An ODBC DSN may be used with a PEAR::DB DSN, but for most database types, the PEAR::DB DSN has nothing at all to do with an ODBC DSN. For details about using an ODBC database with PEAR::DB, see the ODBC section in the detailed examples starting on page 134.

A PEAR::DB DSN is formatted after the fashion of a Universal Resource Identifier. The format, in its fullest form is shown below in Code Listing 6.

```text
phptype(dbsyntax)://username:password@protocol+host
spec/database
```

#### Code Listing 6: Full DSN Format

Most variations are allowed, such as those shown below in Code Listing 7.

```text
2  phptype://username:password@protocol+hostspec:110//usr/db_file.db
3  phptype://username:password@hostspec/database_name
4  phptype://username:password@hostspec
5  phptype://username@hostspec
6  phptype://hostspec/database
7  phptype://hostspec
8  phptype(dbsyntax)
9  phptype
```

#### Code Listing 7: Variations of DSN Format

Currently, the following databases shown in Table 1 below are supported by PEAR::DB.

| Database | phptype | Database Information Web Site |
|---|---|---|
| MySQL | mysql | http://www.mysql.com/ |
| PostgreSQL | pgsql | http://www.postgresql.org/ |
| Borland InterBase | ibase | http://www.borland.com/ |
| Mini SQL | msql | http://www.hughes.com.au/products/msql |
| Microsoft SQL Server | mssql | http://www.microsoft.com/ |
| Oracle 7/8/8i | oci8 | http://www.oracle.com/ |
| ODBC (Open Database Connectivity) | odbc |  |
| SyBase | sybase | http://www.sybase.com/home |
| Informix | ifx | http://www.informix.com/ |
| FrontBase | fbsql | http://www.frontbase.com |

| Database | Driver | URL |
|---|---|---|
| SQLite | sqlite | http://www.sqlite.org/ |
| dBase | dbase |  |

Table 1: PEAR::DB Supported Databases

Some examples of DSNs have already been shown in Code Listing 4 and Code Listing 5. Since the use of a DSN is so fundamental to using PEAR::DB, more examples will be given. Additionally in the detailed database-specific examples provided later, specific examples of a DSN for each supported database type will be provided.

### Connect

Establishing a connection to any supported database is most easily accomplished using **DB::connect()**. There are two parameters: the connect DSN and a mixed value containing either a Boolean value or an array of values – this will be discussed further in this section. The return value of a call to **DB::connect()** is either a valid instance of a database class or an error or warning object. To check for errors and warnings, use the **DB::isError()** and **DB::isWarning()** class methods. To disconnect from the database, use the **disconnect()** method of the database object that is returned.

The second parameter to **DB::connect()** is important to understand, because it controls database specific options. Each database class type contains a **setOption()** method that is used to set various database specific optional values. The parent class of all the database classes, DB_common, defines the options shown in Table 2 by default.

| Option Name | Default Value | Brief Description |
|---|---|---|
| persistent | false | Whether or not to establish a persistent connection to the database. |
| optimize | performance | Values currently used are ‘performance’ and ‘portability’. Each database uses this option in a slightly different way. |
| debug | 0 | Numeric value representing the level of debug information to generate. |
| seqname_format | %s_seq | Describes the format of the names used for sequences. |
| autofree | false | If set to true, this flag causes PEAR::DB to free all fetched data retrieved using fetchRow() or fetchInto(). |

Table 2: Default Options for Database Classes

For each option specified in the call to **DB::connect()**, the **setOption()** method is called once. If you do not specify any options, the default values are used. More details about the options can be found in the detailed coverage of each database starting on page 134. The *seqname_format* option will be discussed in the section on sequences.

It is also possible to pass a Boolean value instead of an array of values as the second parameter to **DB::connect()**. When a Boolean value is passed, it represents the value of the *persistent* option which indicates whether or not a persistent connection to the database should be established.

The sample code shown below in Code Listing 8 illustrates several examples of connections to a MySQL database server. No significant output is generated; this example is for illustration only.

```php
<?php
require_once( 'DB.php' );

// make a non-persistent connection to a MySQL
// database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( !DB::isError( $oDB ) )
{
    print( 'test 1 success<br>' );
    $oDB->disconnect();
}

// make a persistent connection to a MySQL
// database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( !DB::isError( $oDB ) )
{
    print( 'test 2 success<br>' );
    $oDB->disconnect();
}

// make a persistent connection to a MySQL
// database -- alternate method
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
array( 'persistent' => true ) );
if ( !DB::isError( $oDB ) )
{
    print( 'test 3 success<br>' );
    $oDB->disconnect();
}
?>
```
