# 20.2 Database Access with SQLite

For SQLite, the necessary steps are explained one after the other: Establish connection, send queries, and analyze return value(s). Special features such as transactions also are not left unmentioned.

Good (and at the same time, bad) news first: Internally, all data in an SQLite database are handled as strings. SQLite therefore performs type conversions more or less automatically. However, this makes handling a little easier.

> **Note: Functions or Methods?**
> 
> In PHP, there are two ways of accessing databases for most database types. Either you use functions, as was already the case in PHP 4, and pass a database handle as the first parameter, which you receive when the connection is established, or you use the OOP syntax.
> 
> This was also the case with SQLite—up to and including PHP 5.2. Since version 5.3 and the aforementioned change to SQLite3, there is only the OOP-based programming interface.

# 20.2.1 Connection Setup

Establishing a connection to a SQLite database is relatively simple. You do not need any complicated connection parameters, just a file name: that of the database file, of course.

As a second parameter, you can (optionally) specify the mode or modes for opening the database. Three values are possible (and can be combined with a bitwise operator):

+   * SQLITE3_OPEN_READONLY
+     Open for read-only access
+   
+   * SQLITE3_OPEN_READWRITE
+     Open for read and write access (default behavior)
+   
+   * SQLITE3_OPEN_CREATE
+     Create database file if it does not yet exist (also standard behavior)

The third parameter contains an optional encryption key for the database. The object to whose constructor you must pass all this is called SQLite3(). You close the connection again with the close() method of the instance.

```
<?php
try {
    $db = new SQLite3("file.db");
    echo "Connection successful.";
    $db->close();
} catch (Exception $ex) {
```