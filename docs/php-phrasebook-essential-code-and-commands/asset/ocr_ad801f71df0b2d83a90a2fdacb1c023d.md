# Connecting Via PDO

To make this as portable and easy to deploy as possible, the following phrases use the SQLite driver; however, other drivers and database systems are just as good. Note that this driver uses SQLite 3 and not SQLite 2 as bundled with PHP 5 (that’s why the binary distribution of the driver weighs in at over 200KB). Whatever system you choose, download and install the driver and load it after PDO in your php.ini.

Because PDO only works with PHP 5 and later versions, you can use an object-oriented approach. All you need is a suitable data source name (DSN), a user, and a password (and possibly other options). The preceding code connects to/creates an SQLite file.

# Sending SQL Via PDO

```
$stmt = $db->prepare($sql);
$stmt->execute();
```

To send SQL via PDO, a statement must be executed using the query() method. As always, you need a way to escape special characters. This can, once again, be done using prepared statements. First, an SQL query can be parsed using a method called prepare(), whereas placeholders start with a colon. Then, the bindParam() method binds a value to a placeholder name. Finally, the execute() method sends the statement to the database.

```
<?php
try {
    $db = new PDO('sqlite:PDOquotes.db');
    require_once 'stripFormSlashes.inc.php';
    $sql = 'INSERT INTO quotes (quote, author, year)
```