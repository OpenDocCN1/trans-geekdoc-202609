```
```php
if ($row = mysql_fetch_array($this->query, MYSQL_ASSOC)) {
	return $row;
} else if ( $this->size() > 0 ) {
	mysql_data_seek($this->query, 0);
	return false;
} else {
	return false;
}
}
/**
 * Checks for MySQL errors
 * @return boolean
 * @access public
 *
*/
function isError()
{
	return $this->mysql->isError();
}
```
```

Now, hold your breath just a little longer until you’ve seen what using these classes is like:

```
```php
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harry'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Connect to MySQL
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

$sql = "SELECT * FROM articles ORDER BY title";

// Perform a query getting back a MySQLResult object
$result = $db->query($sql);

// Iterate through the results
while ($row = $result->fetch()) {
	echo 'Title: ' . $row['title'] . '<br />';
	echo 'Author: ' . $row['author'] . '<br />';
}
```
```