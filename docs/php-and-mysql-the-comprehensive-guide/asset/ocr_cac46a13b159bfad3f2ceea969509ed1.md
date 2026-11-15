> > **Note**
> > As of the time of publication, laminas-db was only compatible with PHP versions 8.0 to 8.2, so we could not reproduce the following steps with PHP 8.3.

Back to the actual implementation. The adapter is used to do the following things:

+   1. Create a SQLite database in memory.
+   2. Create a table.
+   3. Fill the table with six random numbers.
+   4. Read out these six random numbers.
+   5. Delete the table.

The prerequisite for this is that the pdo_sqlite extension is activated in php.ini (more on this in Chapter 18). The following listing contains the complete code, added directly to the model file from the previous example.

```
<?php
namespace Application\Model;

class HelloWorld {
public $numbers;

function __construct() {
$numbers = [];

$db = new \\Laminas\\Db\\Adapter\\Adapter(
[
"driver" => "Pdo_Sqlite",
"database" => ":memory:",
]
);

$db->query(
'CREATE table numbers (number INTEGER)',
\\Laminas\\Db\\Adapter\\Adapter::QUERY_MODE_EXECUTE);

for ($i = 0; $i < 6; $i++) {
$db->query(
'INSERT INTO numbers (number) VALUES (?)',
[rand(1, 49)]);
}

$stmt = $db->query('SELECT * FROM numbers');
$rows = $stmt->execute();
```