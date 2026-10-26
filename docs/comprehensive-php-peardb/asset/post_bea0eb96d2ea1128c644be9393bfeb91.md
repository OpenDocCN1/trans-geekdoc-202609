
|   |   | y |   |   |   |   |
|---|---|---|---|---|---|---|

All update queries finished successfully.

Executing query: `SELECT * from Employees\norder by last_name, first_name`

Number of rows in query result = 7

|   | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 2 | Cox | Jeffrey | 225 | 0 | 1 |
| 1 | 3 | McNulty | Kate | 214 | 2 | 3 |
| 2 | 51 | Murphy | Jim |   | 1 | 1 |
| 3 | 1 | Schwendiman | Joe | 2204 | 2 | 3 |
| 4 | 4 | Schwendiman | Ryan | 128 | 1 | 1 |
| 5 | 58 | Schwendiman | Scott | 234 | 1 | 1 |
| 6 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

Executing query: `SELECT * from Employees\nwhere ( mgr_id = 3 )`

Number of rows in query result = 0

Executing query: `SELECT * from Employees\nwhere ( dept_id = 2 )`

Number of rows in query result = 0

All delete queries finished successfully.

Executing query: `SELECT * from Employees\norder by last_name, first_name`

Number of rows in query result = 2

|   | id | last_name | first_name | phone_ext | mgr_id | dept_id |
|---|---|---|---|---|---|---|
| 0 | 1 | Schwendiman | Joe | 2204 | 2 | 3 |
| 1 | 59 | Schwendiman | Taylor | 323 | 1 | 1 |

Executing query: SELECT * from Employees
where ( mgr_id = 3 )

Number of rows in query result = 0

Executing query: SELECT * from Employees
where ( dept_id = 2 )

Number of rows in query result = 0

The output shown above has been slightly reformatted for readability, but provides the information needed.

## MySQL

MySQL is likely to be the most commonly-used database for PHP programmers. All versions of PHP 4 enable built-in support for MySQL databases. For either the Windows or unix-like platforms, MySQL support is typically on by default.

The DSN format for MySQL is illustrated in most of the examples in this book. The most common DSN format for a MySQL database is likely to be:

```
phptype://username:password@hostspec/database_name
```

The *hostspec* portion can contain just a hostname or IP address, or a *host:port* formatted host specification.

The general test script shown above worked without any problems for my MySQL installation (*MySQL 4.0.15-Max*).

### PostgreSQL

The support for PostgreSQL in PHP and PEAR::DB is excellent. The test example worked for PostgreSQL with only a minor change. The “DROP TABLE” command needs to be altered for a lower-case table name. Again, my inexperience with the database may be part of the problem. In any case, experienced PostgreSQL users will know the particulars of the database and avoid such bugs.

### Borland Interbase

Borland Interbase is supported by PHP in general, but I was unable to get the PEAR test to run successfully.

First, the **getTables()** method is not supported in the PEAR::DB implementation for Interbase, so the code had to be reworked. There is a sample script (available with the source code at **http://www.intechra.net/**) called _code_listing_67.php_ that removes the lines related to the **getTables()** method.

After getting the script to run past the initial **getTables()** failure, I encountered a consistent error in a select SQL statement:

```
Running PEAR::DB test for database Borland
Interbase

Employees table successfully dropped.

Employees table successfully created.
```

7 All data inserted successfully.
9 Executing query: SELECT * from Employees order by
last_name, first_name
10

11 Number of rows in query result = Object
13

14 Executing query: SELECT * from Employees where (
mgr_id = 3 )
15

16 PHP has encountered an Access Violation at 77F83AED

The error on line 16 occurred in every test run. After getting the error, it was necessary to stop and restart IIS.

Without jumping to any conclusions, I have to assume that my configuration is not correct for using PHP with Interbase. Assuming a correctly-running PHP + Interbase configuration, I also have to assume that the PEAR::DB test above will work correctly, save for the missing implementation for getTables().

## Mini SQL

Apparently I’m not intelligent enough to get Mini SQL to work correctly. I was entirely unable to use a Windows PHP installation to connect to a remote Linux-based Mini SQL server. I followed every step on the http://www.php.net/msql page, but to no avail. I was able to eventually establish a connection from PHP when I switched to using PHP + Mini SQL on Linux. However, the test code failed to run at various different places (each run seemed to fail at a different spot).

Many of the links on the Mini SQL home page are broken (especially related to Windows support), so I am left to make some assumptions about the general state of the project.

My suggestion to a PHP developer looking for a small database backend is to check out SQLite. I had no problems setting it up and there were no problems with the PEAR::DB test code.

## Microsoft SQL Server

Microsoft SQL Server is extremely simple to set up in a Windows-based PHP install. For testing, I simply installed the latest PHP binaries available from the PHP web site. After configuring PHP at the most basic level to begin testing, it is necessary to load the MS SQL extension by editing the *php.ini* file.

Simply remove the semicolon comment character preceding the line *extension=php_mssql.dll* in the configuration file and it works.

Configuration of non-Windows PHP for use with a MS SQL database is slightly more complicated, but still possible. See **http://www.php.net/mssql** for setup instructions.

Once running, PHP works great with MS SQL server and the PEAR::DB implementation is very complete. The test script works perfectly for MS SQL server as tested against MS SQL Server 2000 (version 8.00.760 SP3).

## Oracle 7/8/8i

`php_fsql.dll` and configure PHP via the `php.ini` file to use FrontBase. The general PEAR::DB test script ran without any trouble the first time it was tried.

Considering that I have had no previous experience with FrontBase, this is very encouraging. If you are considering using FrontBase with your PHP application, there are a development licenses available so you can test your application before making the financial commitment to deploy.

### SQLite

SQLite is an interesting database engine that will be shipping (according to recent online sources) with PHP by default starting in version 5 of PHP. SQLite is a file-based database engine that is (as its name implies) very lightweight. The DSN specification is something like:

```
sqlite:///c:/temp/PEAR/sqlite_employees.dat
```

The above DSN works on Windows, but it can be simply adapted for use on other operating systems by simply updating the path format appropriately.

Installing SQLite on a Windows-based PHP is a snap. Simply download the `php_sqlite.dll` file available from **http://www.php.net/sqlite** and then download the actual SQLite engine DLL (`sqlite.dll`) from the SQLite web site at **http://www.sqlite.org/**. Place the `sqlite.dll` file in the search path of Windows (such as the `system32` directory), then copy `php_sqlite.dll` to your PHP extensions directory. Then enable SQLite by adding `extension=php_sqlite.dll` to your `php.ini` file.

The test script runs without any errors or warnings.
There is, however, a single notice generated:

```
Notice: Undefined index: mode in C:\\temp\\PEAR\\php-4.3.4-Win32\\pear\\DB\\sqlite.php on line 185
```

This warning is based on the fact that for some reason, the SQLite database object expects the parsed DSN to have a member called *mode* which does not exist. Perhaps this will be added in a future version of PEAR::DB. In any case, this notice will not be displayed if you are running in a typically configured environment. However, if you are running SQLite on a unix-like operating system, the *mode* value specifies the file mode (e.g. 0644) which you may wish to specify. If you do, you will need to edit the DB_sqlite implementation or use an array-based DSN and provide the *mode* key directly.

The SQLite support in PEAR::DB is surprisingly complete for such a new database (from the PHP perspective). Using SQLite may be preferred in restricted hosting environments or in situations where a full database backend is not required. The overhead of SQLite is very small and the SQL language support is very complete.

## dBase

dBase support in PEAR::DB is extremely limited. The example code will not work with dbase because so little of the interface is truly supported. After looking a bit on the PHP web site, even dBase itself is not fully supported:

There is no support for indexes or memo fields. There is no support for locking, too. Two concurrent
