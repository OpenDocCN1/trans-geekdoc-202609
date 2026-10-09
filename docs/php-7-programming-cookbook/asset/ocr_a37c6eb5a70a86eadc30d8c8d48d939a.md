![](bbox=[0.26, 0.14, 0.74, 0.36])

Finally, to test the factory() method shown previously, save the code into the Application\Database\Connection class in a Connection.php file in the Application\Database folder. You can then try this:

```
include __DIR__ . '/../Application/Database/Connection.php';
use Application\Database\Connection;
$connection = Connection::factory(
    'mysql', 'php\'cookbook\'', 'localhost', 'test', 'password'
);
$stmt = $connection->query('SELECT name FROM iso_country_codes');
while ($country = $stmt->fetch(PDO::FETCH_COLUMN))
    echo $country . ' ';

```

You will see a list of countries pulled from the sample database:

![](bbox=[0.24, 0.59, 0.74, 0.86])