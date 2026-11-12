When we call the extract method, we provide a path under which it should extract the archive—in this case, the subdirectory extract from the location where this script is executed. Nice and easy.

Archive_Tar is particularly interesting in that it allows strings to be added to the archive as files. Consider the following example:

```
```php
<?php
// Include MySQL class
require_once 'Database/MySQL.php';

// Include PEAR::Archive_Tar
require_once 'Archive/Tar.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate MySQL connection
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// Instantiate Archive_Tar
$tar = new Archive_Tar('demo/articles.tar.gz', 'gz');

$sql = "SELECT * FROM articles";

$result = $db->query($sql);

while ($row = $result->fetch()) {
  // Add a string as a file
  $tar->addString('articles/' . $row['article_id'] . '.txt',
    $row['body']);
}
echo 'Article archive created';
?>
```
```

Here, we've queried a database using the MySQL class we created in Chapter 3, and used the addString method to add to the archive as files some of the data we fetched. The first argument represents the path and filename under which the string should be stored; the second is the string itself.

That should give you a general idea of when Archive_Tar can be useful to you. For a more extensive tutorial, see the recommended reading below.