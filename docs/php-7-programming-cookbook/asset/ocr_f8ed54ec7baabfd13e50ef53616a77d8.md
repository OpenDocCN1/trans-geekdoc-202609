Enter the following code:

```
$obj = new stdClass();
$obj->test = 'TEST';
echo $obj->test;
echo PHP_EOL;

include (__DIR__ . './../Application/Database/Connection.php');
$connection = new Application\Database\Connection(
    include __DIR__ . DB_CONFIG_FILE);

$sql = 'SELECT * FROM iso_country_codes';
$stmt = $connection->pdo->query($sql);
$row = $stmt->fetch(PDO::FETCH_OBJ);
var_dump($row);
```

Here is the output:

![](bbox=[0.24, 0.42, 0.75, 0.62])

# See also...

For more information on refinements in PHP 7.1 on the keyword $this, please see https://wiki.php.net/rfc/this_var.

# Extending classes

One of the primary reasons developers use OOP is because of its ability to re-use existing code, yet, at the same time, add or override functionality. In PHP, the keyword extends is used to establish a parent/child relationship between classes.