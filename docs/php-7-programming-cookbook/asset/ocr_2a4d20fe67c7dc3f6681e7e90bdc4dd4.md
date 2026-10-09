```
$params['pwd'],
                [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION]);
$sql = "INSERT INTO customer ("
     . implode(",", $fields)
     . ") VALUES (?,?,?,?,?)";
$stmt = $pdo->prepare($sql);
foreach ($data as $row) $stmt->execute($row);
} catch (PDOException $e) {
    echo $e->getMessage();
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

To test the use of a prepared statement with named parameters, modify the SQL statement to add a WHERE clause that checks for customers with a balance less than a certain amount, and a level equal to either BEG, INT, or ADV (that is, beginning, intermediate, or advanced). Instead of using `PDO::query()`, use `PDO::prepare()`. Before fetching results, you must then perform `PDOStatement::execute()`, supplying the values for balance and level:

```
$sql = 'SELECT * FROM customer '
         . 'WHERE balance < :val AND level = :level '
         . 'ORDER BY id LIMIT 20';
$stmt = $pdo->prepare($sql);
$stmt->execute(['val' => 100, 'level' => 'BEG']);
```

Here is the resulting output:

![](bbox=[0.33, 0.55, 0.68, 0.71])

Instead of providing parameters when calling `PDOStatement::execute()`, you could alternatively bind parameters. This allows you to assign variables to placeholders. At the time of execution, the current value of the variable is used.