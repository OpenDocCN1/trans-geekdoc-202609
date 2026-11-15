
## Appendix B: Configuring PHP

soap.wsdl_cache_ttl=86400

; Sets the size of the cache limit. (Max. number of WSDL files to cache)
soap.wsdl_cache_limit = 5

[sysvshm]
; A default size of the shared memory segment
;sysvshm.init_mem = 10000

[ldap]
; Sets the maximum number of open links or -1 for unlimited.
ldap.max_links = -1

[mcrypt]
; For more information about mcrypt settings see http://php.net/mcrypt-module-open

; Directory where to load mcrypt algorithms
; Default: Compiled in into libmcrypt (usually /usr/local/lib/libmcrypt)
;mcrypt.algorithms_dir=

; Directory where to load mcrypt modes
; Default: Compiled in into libmcrypt (usually /usr/local/lib/libmcrypt)
;mcrypt.modes_dir=

[dba]
;dba.default_handler=

; Local Variables:
; tab-width: 4
; End:

![](img/1ddec54918a4802eb9b4febec3d4e7f6_794_0.png)

## Alternatives to MySQL

In Chapters 12 through 14 you learned how to access MySQL databases from within your PHP applications. MySQL is often a great choice if you’re writing PHP scripts, because it’s freely available, cross-platform, and is installed by default on most PHP-supported Web servers.

However, MySQL isn’t for everyone, and in some scenarios it’s preferable to use an alternative database engine. This appendix takes a brief look at some of the more popular alternatives on the market. Most of these can work with the PDO extension that is described in Chapters 12 through 14, so if you do want to try a different database engine most of the content and examples in those chapters will still apply.

### SQLite

If you asked the average developer what is the most popular SQL database engine in use today, they’d probably think of MySQL, Oracle, or SQL Server. In fact the answer is probably SQLite (see `http://www.sqlite.org/mostdeployed.html` for the breakdown). The reason for this (apart from the fact that it’s very good) is that it’s an embedded database engine. This means that it’s bundled inside every copy of every application that uses it, from Firefox through to Skype and various mobile platforms including Symbian and iPhone. Contrast this with, say, MySQL, which consists of a separate server application, along with client libraries to talk to the server.

Another nice thing about SQLite is that its code is in the public domain, meaning that anyone can use and modify the code as they see fit.

These days SQLite is bundled with the PHP engine, which means you don’t have to install anything extra to start using it. It’s very fast, supports nearly every standard SQL command, and has some rather special tricks up its sleeve. It’s also relatively simple (because it doesn’t have a client-server architecture) and very reliable. In a nutshell, it’s well worth checking out.

Here are some other features of SQLite that make it stand out from the crowd:

- It's dynamically typed: The same field can hold different data types from one record to the next. This tends to mesh well with PHP's loose typing, and gives you a lot of flexibility. (However, it can make it harder to maintain database integrity, and it's not compatible with other SQL database systems.)
- A database is stored in a single, cross-platform database file: This makes it easy to back up your SQLite databases, as well as port them to different operating systems.
- It's easy to configure: There's no separate application to install, start, or configure, and you don't need to create users or assign permissions to databases before you can use them.
- You can call PHP functions from inside an SQL query: This is one of the more impressive SQLite features, made possible by the fact that the SQLite engine is embedded within PHP. (See the example later in this section.)

Generally speaking, if you need a fast, lightweight database engine for your Web application, SQLite is well worth a look. However, if you need an “industrial” strength database for very complex queries, very large amounts of data, or high-traffic Web sites, you probably need to look elsewhere.

> For a detailed discussion of when (and when not) to use SQLite see http://www.sqlite.org/whentouse.html

At the time of writing, the most recent version of SQLite is Version 3. Your PHP scripts can talk to SQLite 3 through the SQLite3 extension (see http://www.php.net/manual/en/book.sqlite3.php) or via PDO (see http://www.php.net/manual/en/ref.pdo-sqlite.php).

Here's a simple example that shows how to use PDO to create an SQLite database and table, populate the table with a record, and retrieve the record (calling the PHP str_word_count() function from inside the SQL at the same time):

```
<?php
$dsn = "sqlite:/home/matt/proverbs.sqlite3";
// Create a connection to the database
// (database file is automatically created)
try {
    $conn = new PDO( $dsn );
    $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
    echo "Connection failed: " . $e->getMessage();
}
// Create a new SQLite function based on the PHP str_word_count() function
$conn->sqliteCreateFunction( "wordCount", "str_word_count", 1 );
```

```
// Create the proverbs table
// (columns of type INTEGER PRIMARY KEY serve as auto-increment columns)
$sql = "DROP TABLE IF EXISTS proverbs";
$conn->exec( $sql );
$sql = "CREATE TABLE proverbs ( id INTEGER PRIMARY KEY, proverbText )";
$conn->exec( $sql );

// Add a proverb
$sql = "INSERT INTO proverbs ( proverbText ) VALUES ( :proverbText )";
$st = $conn->prepare( $sql );
$st->bindValue( ":proverbText", "A bird in the hand is worth two in the bush" );
$st->execute();

// Retrieve the proverb and its word count, and display the results
$sql = "SELECT id, proverbText, wordCount( proverbText ) AS numWords FROM proverbs";
$st = $conn->query( $sql );
$proverb = $st->fetch();
echo "ID: " . $proverb["id"] . "<br />";
echo "Proverb: " . $proverb["proverbText"] . "<br />";
echo "Word count: " . $proverb["numWords"]. "<br />";

?>
```

This script displays the following:

```
ID: 1
Proverb: A bird in the hand is worth two in the bush
Word count: 11
```

### PostgreSQL

PostgreSQL (http://www.postgresql.org/) is a free, open-source, standards-compliant database engine. PHP lets you talk to a PostgreSQL database through a native extension (http://www.php.net/manual/en/book.pgsql.php) that works much like its MySQL equivalent, or through PDO (http://www.php.net/manual/en/ref.pdo-pgsql.php)

Of all the database engines supported by PHP, PostgreSQL is probably the closest competitor to MySQL. Both are open-source and free; both offer roughly the same level of power and scalability; and both have a strong following among Web developers.

In fact this closeness often results in “religious wars” as fans of both systems argue over which is better. Historically, MySQL has been perceived as being easier to use and faster, whereas PostgreSQL has had a reputation for being more feature-rich, powerful, and reliable (an open-source alternative to Oracle, if you like).

## Appendix C: Alternatives to MySQL

These days, however, there’s much less to choose between the two systems, as MySQL becomes more feature-rich and stable while PostgreSQL gets easier to work with. At the time of writing, the main criticism of MySQL is possibly that it’s not strict enough at preventing data loss (such as letting you insert an invalid `DATETIME` value and silently converting it to zero), whereas PostgreSQL lacks built-in replication (though it can be added as a plugin) and isn’t installed on as many Web hosting accounts as MySQL. However, by the time you read this, the gap between the two will no doubt have narrowed further.

The truth is that, as a Web developer it probably doesn’t matter greatly which of the two systems you choose initially. If you use PDO to connect to the database, and you’re not using some of the more esoteric features of either engine, you’ll usually find it fairly straightforward to port your application from MySQL to PostgreSQL, or vice-versa.

You can find a thorough discussion of the relative merits of MySQL and PostgreSQL at http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL.

Here’s the get_fruit.php script from Chapter 12 rewritten to use PostgreSQL instead of MySQL. As you can see, the changes required were minimal:

```
<!DOCTYPE html PUBLIC "--//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fruit</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Fruit</h1>
<?php
$dsn = "pgsql:host=localhost;dbname=mydatabase";
$username = "postgres";
$password = "mypass";
try {
$conn = new PDO( $dsn, $username, $password );
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
echo "Connection failed: " . $e->getMessage();
}

$sql = "SELECT * FROM fruit";
echo "<ul>";
try {
$rows = $conn->query( $sql );
foreach ( $rows as $row ) {
echo "<li>A " . $row["name"] . " is " . $row["color"] . "</li>";
}
}
```
