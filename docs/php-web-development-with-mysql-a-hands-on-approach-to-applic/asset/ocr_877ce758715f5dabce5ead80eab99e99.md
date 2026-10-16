Let's look at Listing 26.27 for reading a single row based on the ID.

# Listing 26.27.

```
```php
public function readById($id)
{
    $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);

    // Read the record given by the id
    $sql = "SELECT * FROM student WHERE id=:id";

    try
    {
        $query = $db->prepare($sql);
        $query->bindParam(":id", $id, PDO::PARAM_INT);
        $query->execute();

        // Fetch result into instance of a Student object
        $result = $query->fetchObject("Student");
    }
    catch(Exception $ex)
    {
        echo "{$ex->getMessage()}<br/>";
    }

    return $result;
}
```
```

Everything in this method should be straight forward except for line 15:

```
$result = $query->fetchObject("Student");
```

> *Another way to specify our class is Student::class—without quotes. PHP uses the ::class constant to reference the fully-qualified name of a class which includes its namespace.*
> 
> `$result = $query->fetchObject(Student::class);`

In our readAll() method, we used the fetchAll() method which returned an array of Student objects. We could have done the same thing on line 15, but we would return a single object inside an array with one element. It's more convenient to return a single object since we know we're only looking for a single row. Therefore, we need to use the fetchObject() method, which takes a string with the name of the class we want to use that contains properties with all the fields in the student table, which in our case is Student.

If an ID that does not exist in the student table is passed in, readById() returns false.