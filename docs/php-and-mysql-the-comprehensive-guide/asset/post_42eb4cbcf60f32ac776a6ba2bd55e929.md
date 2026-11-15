
| Parameters | Description | Default Value |
|---|---|---|
| mysqli.default_host | Standard server | ZERO |
| mysqli.default_port | Standard port | 3306 |
| mysqli.default_pw | Default password | ZERO |
| mysqli.default_socket | Default socket name | ZERO |
| mysqli.default_user | Default user name | ZERO |
| mysqli.max_links | Maximum number of connections | "-1" (unlimited) |
| mysqli.max_persistent | Maximum number of persistent connections | "-1" (unlimited) |

Table 19.2 Some Configuration Parameters in "php.ini"

If mysqlnd is used as the client library (which is the default), then further settings can be made in the [mysqlnd] section, including those in Table 19.3.

| Parameters | Description | Default Value |
|---|---|---|
| mysqlnd.collect_memory_statistics | Determines whether statistical information on memory consumption should be collected | 0 |
| mysqli.collect_statistics | Determines whether general statistical information should be collected | 1 |
| mysqlnd.net_cmd_buffer_size | Buffer size in bytes when sending commands to MySQL | 4096 |
| mysqlnd.net_read_buffer_size | Buffer size in bytes when reading returns from MySQL | 32768 |

Table 19.3 Some "mysqlnd" Configuration Parameters in "php.ini"

## Chapter 20

## SQLite

> If a file-based database will do, then SQLite is a surprisingly performant option— especially when reading data (not so much when writing, which is obvious).

Let's start with a historical reminder: One of the most noticeable new features of PHP 5 was support for the SQLite database. When it became public knowledge that PHP 5 would offer this new feature, the first voices claiming that MySQL was dead or would be shunned by PHP were heard.¹ That this is of course not the case.

To make a long story short: SQLite is not a replacement for MySQL but an alternative in certain cases. PHP is known to support a large number of databases; there are so many that we can’t even introduce them all in this book. SQLite is another one, but one that has caused quite a stir in the community.

SQLite is actually a C library, available at www.sqlite.org, and is now integrated into PHP. The greatest strength of SQLite is that it is a file-based database. There is therefore no need for a daemon running in the background; you simply work with the file system. This simplifies handling and also the deployment of an application.

SQLite’s greatest strength is also its greatest weakness: When reading from a file, the system is really performant, usually even faster than established databases² such as MySQL or Microsoft SQL Server. When writing, however, the entire database file—that is, the complete database—is locked, which is of course significantly slower than its competitors. SQLite is a great choice, for example, for a news portal with a large number of read operations and only a few write operations. If the user behavior of a highly frequented site is analyzed and stored in a database (tracking), there may be better alternatives than SQLite.

### 20.1 Preparations

The installation of SQLite is simple. The library is already integrated in PHP, and a call to phpinfo() displays information about the library (see Figure 20.1). If you want to get rid of it, you need to compile PHP with the --without-sqlite3 option.

1 Among other things, there was the one Microsoft employee who called and said that it was illegal to use MySQL with PHP because of the GPL. Sure.
2 See the (old, obsolete, but still worth reading) study on the SQLite website at www.sqlite.org/speed.html.

![](img/ae7820c36e8f24c1623d26668b28e80e_598_0.png)

Figure 20.1 A Look at "phpinfo()" Confirms the Successful Installation

You can already see from the name of the command line button that it uses version 3 of SQLite—SQLite3 for short. To be more precise: this version of the database has been supported since PHP 5.3. This has implications for Windows users. They must load the php_sqlite3.dll extension in php.ini:

```
extension=sqlite3
```

The php_sqlite.dll DLL was previously used but is no longer available for current PHP versions in the official distribution.

Nothing more is necessary. No server process needs to be started; you only need read and write permissions for the database file(s) you want to use. You also need these rights for the directory in which the files are located as SQLite can also create temporary files.

### Note

If you store sensitive data in the databases, you should follow three guiding rules:

- 1. If possible, place the database file in a directory that cannot be accessed by a user via HTTP, but only by you via PHP script. This prevents downloading. Alternatively, you can configure the web server so that files with certain extensions (such as .db) cannot be downloaded.
- 2. If this is not possible, at least think of an imaginative name for the database—for example xlbrmf.db. A database.db, file.db, or creditcarddetails.db file is quickly found by data thieves who are good at guessing names. However, we implore you: Also follow one of the recommendations from the first point.
- 3. Intercept PHP error messages. These can also contain the name of the database file.

### 20.2 Database Access with SQLite

For SQLite, the necessary steps are explained one after the other: Establish connection, send queries, and analyze return value(s). Special features such as transactions also are not left unmentioned.

Good (and at the same time, bad) news first: Internally, all data in an SQLite database are handled as strings. SQLite therefore performs type conversions more or less automatically. However, this makes handling a little easier.

> **Note: Functions or Methods?**
> 
> In PHP, there are two ways of accessing databases for most database types. Either you use functions, as was already the case in PHP 4, and pass a database handle as the first parameter, which you receive when the connection is established, or you use the OOP syntax.
> 
> This was also the case with SQLite—up to and including PHP 5.2. Since version 5.3 and the aforementioned change to SQLite3, there is only the OOP-based programming interface.

### 20.2.1 Connection Setup

Establishing a connection to a SQLite database is relatively simple. You do not need any complicated connection parameters, just a file name: that of the database file, of course.

As a second parameter, you can (optionally) specify the mode or modes for opening the database. Three values are possible (and can be combined with a bitwise operator):

- SQLITE3_OPEN_READONLY
  Open for read-only access

- SQLITE3_OPEN_READWRITE
  Open for read and write access (default behavior)

- SQLITE3_OPEN_CREATE
  Create database file if it does not yet exist (also standard behavior)

The third parameter contains an optional encryption key for the database. The object to whose constructor you must pass all this is called SQLite3(). You close the connection again with the close() method of the instance.

```
<?php
try {
    $db = new SQLite3("file.db");
    echo "Connection successful.";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

Listing 20.1 Connection Setup with SQLite ("sqlite-connect.php")

> **Tip**
> 
> Instead of a file name, you can also specify `:memory:`, in which case the database is created in memory. Unfortunately, it will then disappear again after the end of the script. This is usually only useful for temporary tables (to save intermediate results) or for test purposes.

### 20.2.2 Queries

There are two ways to send a query to the SQLite database:

- exec() for queries without a return value
- query() for queries with return value

If you like it simple and convenient, you may want to use `query()` because this also works for queries that do not return a value (the return of the function then contains no relevant data). However, for queries without a return value (such as `CREATE TABLE` or `INSERT`) it is better to use `exec()` for queries without a return. This also happens in Listing 20.2: Simply pass the SQL command as a parameter.

The following listing creates a test table (familiar from the previous chapter) and fills it with some data.

```
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "CREATE TABLE my_table (
    id INTEGER PRIMARY KEY,
    field VARCHAR(1000)
    )";
    if ($db->exec($sql)) {
    echo "Table created.<br />";
    } else {
    echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('Value1')";
    if ($db->exec($sql)) {
    echo "Data entered.<br />";
    } else {
```
