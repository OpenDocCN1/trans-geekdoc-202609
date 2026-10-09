# Interacting with a Database

+   12. If you do not specify an error mode, the default PDO error mode is PDO::ERRMODE_SILENT. You can set the error mode using the PDO::ATTR_ERRMODE key, and either the PDO::ERRMODE_WARNING or the PDO::ERRMODE_EXCEPTION value. The error mode can be specified as the fourth argument to the PDO constructor in the form of an associative array. Alternatively, you can use PDO::setAttribute() on an existing instance.

+   13. Let us assume you have the following DSN and SQL (before you start thinking that this is a new form of SQL, please be assured: this SQL statement will not work!):

```php
$params = [
    'host' => 'localhost',
    'user' => 'test',
    'pwd'  => 'password',
    'db'     => 'php7cookbook'
];
$dsn = sprintf('mysql:host=%s;dbname=%s', $params['host'],
    $params['db']);
$sql = 'THIS SQL STATEMENT WILL NOT WORK';
```

+   14. If you then formulate your PDO connection using the default error mode, the only clue that something is wrong is that instead of producing a PDOStatement instance, the PDO::query() will return a boolean FALSE:

```php
$pdo1 = new PDO($dsn, $params['user'], $params['pwd']);
$stmt = $pdo1->query($sql);
$row = ($stmt) ? $stmt->fetch(PDO::FETCH_ASSOC) : 'No Good';
```

+   15. The next example shows setting the error mode to WARNING using the constructor approach:

```php
$pdo2 = new PDO(
    $dsn,
    $params['user'],
    $params['pwd'],
    [PDO::ATTR_ERRMODE => PDO::ERRMODE_WARNING]
);
```

+   16. If you need full separation of the prepare and execute phases, use PDO::prepare() and PDOStatement::execute() instead. The statement is then sent to the database server to be pre-compiled. You can then execute the statement as many times as is warranted, most likely in a loop.

+   17. The first argument to PDO::prepare() can be an SQL statement with placeholders in place of actual values. An array of values can then be supplied to PDOStatement::execute(). PDO automatically provides database quoting, which helps safeguard against SQL Injection.