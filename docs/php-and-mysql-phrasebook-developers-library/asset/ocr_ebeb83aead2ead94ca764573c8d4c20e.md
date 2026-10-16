Windows users have to use (or compile) php_sqlite.dll, copy it to PHP's extension folder, and then load it using extension=php_sqlite.dll in their php.ini for ext/sqlite or extension=php_sqlite3.dll for ext/sqlite3.

When using ext/sqlite, you can connect to a SQLite data source using sqlite_open(). As the first parameter, you provide the name of the database file; it gets created if it doesn't exist yet. For this to work, the PHP process needs read and write privileges to the file. The second parameter is the file open mode (0666 is recommended); however, as of this writing, this parameter is ignored. The third parameter is a variable that contains any error messages (such as insufficient rights).

NOTE: Just like ext/mysql i, the SQLite extension under PHP 5 can also be accessed using an object-oriented programming (OOP) approach:

```
<?php
$db = new SQLiteDatabase('quotes.db');
echo 'Connected to the database.';
$db->close();
?>
```

For the sake of backward compatibility, this chapter uses the functional approach for the subsequent phrases.

The ext/sqlite3 extension uses a mandatory OOP application programming interface (API). Here, the open() method of the SQLite3 class would open a database file. Because you need to instantiate that class anyway, a quicker approach is to provide the filename in the class constructor, which in turn would open the