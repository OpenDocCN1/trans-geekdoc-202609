# Connecting to Firebird

# ibase_connect()

The Firebird database is currently more an insider’s tip than a widely in use database, but is getting more users and may be an alternative to established RDBMS. The origins of this database lie in Borland’s InterBase product. Therefore, the extension is called ibase or interbase. So, Windows users need extension=php_interbase.dll in their php.ini, whereas “self-compilers” must configure PHP with the switch --with-interbase=/path/to/firebird. Then, Firebird supports two modes: a file mode comparable to SQLite and a server mode. For the sake of interoperability and for an easy deployment, this section uses the file mode.

```
<?php
    if ($db =
ibase_connect('localhost:/tmp/quotes.gdb', 'user',
    'password')) {
        echo 'Connected to the database.';
        ibase_close($db);
    } else {
        echo 'Connection failed.';
    }
?>
```

*Connecting to InterBase/Firebird (ibase_connect.php)*

This section also uses .gdb files that are compatible with both Firebird and Interbase; the new Firebird format has the extension .fdb. After this file is created, ibase_connect() connects to the file or database. For