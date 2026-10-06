# Appendix C: Alternatives to MySQL

Here are some other features of SQLite that make it stand out from the crowd:

+   - It's dynamically typed: The field can hold different data types from one record to the next. This tends to mesh well with PHP's loose typing, and you a lot of flexibility. (However, it can make it harder to maintain database integrity, and it's not compatible with other SQL database systems.)

+   - A database is stored in a single, cross-platform database file: This makes it easy to back up your SQLite databases, as well as port them to different operating systems.

+   - It's easy to configure: There's no separate application to install, start, or configure, and you don't need to create queries or assign permissions to databases before you use them.

+   - You can call PHP functions from an SQL query: This is one of the more impressive SQLite features, made possible by the fact that the SQLite engine is embedded within PHP. (See the example later in this section.)

Generally speaking, if you need a lightweight database for your web application, SQLite is well worth it. However, if you need an "industrial" strength database for complex queries, large amounts of data, or high-traffic Web sites, you probably need to look elsewhere.

> For a detailed discussion of when (and not) to use SQLite see: http://www.sqlite.org/whentouse.html

At the time of writing, the current version of SQLite is 3. Your PHP scripts can talk to SQLite 3 through the SQLite extension (see http://www.php.net/manual/en/book.sqlite3.php) via PDO (see http://www.php.net/manual/en/ref.pdo-sqlite3.php).

Here's a simple example that shows how to use PDO to create an SQLite database and table, populate the table with records, and retrieve the record (calling the PHP str_word_count() function from inside the SQLite at the same time):

```
<php
$dsn = "sqlite:home/matt/proverbs.sqlite3";

// Create a connection to the database
// (database file is automatically created)
try {
    $conn = new PDO($dsn);
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERR_MODE_EXCEPTION);
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}

// Create a new SQLite function based on the PHP str_word_count() function
$conn->sqliteCreateFunction("wordCount", "str_word_count", 1);
```

758