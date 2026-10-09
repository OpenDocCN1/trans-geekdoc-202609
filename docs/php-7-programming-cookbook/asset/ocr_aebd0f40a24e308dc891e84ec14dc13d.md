+   8.  Set the fetch mode to PDO::FETCH_OBJ to return results as a stdClass instance. Here you will note that the while() loop takes advantage of the fetch mode, PDO::FETCH_OBJ. Notice that the printf() statement refers to object properties, in contrast with the preceding example, which references array elements:

```
while ($row = $stmt->fetch(PDO::FETCH_OBJ)) {
    printf('%4d | %20s | %5s', PHP_EOL,
           $row->id, $row->name, $row->level);
}
```

+   9.  If you want to create an instance of a specific class while processing a query, set the fetch mode to PDO::FETCH_CLASS. You must also have the class definition available, and PDO::query() should set the class name. As you can see in the following code snippet, we have defined a class called Customer, with public properties $id, $name, and $level. Properties need to be public for the fetch injection to work properly:

```
class Customer
{
    public $id;
    public $name;
    public $level;
}

$stmt = $pdo->query($sql, PDO::FETCH_CLASS, 'Customer');
```

+   10. When fetching objects, a simpler alternative to the technique shown in step 5 is to use PDOStatement::fetchObject():

```
while ($row = $stmt->fetchObject('Customer')) {
    printf('%4d | %20s | %5s', PHP_EOL,
           $row->id, $row->name, $row->level);
}
```

+   11. You could also use PDO::FETCH_INTO, which is essentially the same as PDO::FETCH_CLASS, but you need an active object instance instead of a class reference. Each iteration through the loop re-populates the same object instance with the current information set. This example assumes the same class Customer as in step 5, with the same database parameters and PDO connections as defined in step 1:

```
$cust = new Customer();
while ($stmt->fetch(PDO::FETCH_INTO)) {
    printf('%4d | %20s | %5s', PHP_EOL,
           $cust->id, $cust->name, $cust->level);
}
```