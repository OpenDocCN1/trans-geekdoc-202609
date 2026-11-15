shows, there are many dangers if there are special characters such as apostrophes in the user input. Here is a brief illustrative example:

```
```php
$value = $_POST["value"] ?? "";
$sql = "INSERT INTO table (field) VALUES ('$value')";
```
```

What if the queried form value is Rasmus' invention, for example? Then $sql would have the following value:

```
```sql
INSERT INTO table (field) VALUES ('Rasmus invention')
```
```

This is syntactically incorrect and leads to an error; Chapter 32 shows even scarier attack possibilities.

It is therefore important to know about masking user input, similarly to how this is realized, for example, in the output of all data in many examples in this book with htmlspecialchars(). Unfortunately, there is no statement for SQL strings that works completely database-independently (addslashes() is not an option).

But there is an even better option, which is both somewhat faster and clearer. At all points in the SQL command where you insert data dynamically, use only placeholders—parameter names preceded by a colon, without apostrophes:

```
```php
$sql = "INSERT INTO table (field) VALUES (:fieldvalue)";
```
```

But what takes the place of the placeholders? You handle this in several steps:

+   1. Prepare the SQL command (with placeholders) for processing by the database using the prepare() method.
+   2. Use the bindParam() method to bind the method to the parameters (these values must be in the form of variables because these variables are bound as a reference).
+   3. Use the execute() method to finally execute the command.

This is a very practical (and usually also very high-performance) option, which is why we are showing another complete listing, this time with a so-called parameterized query.

```
```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage());
    exit();
}

$sql = "INSERT INTO my_table (field) VALUES (:fieldvalue);";
$command = $db->prepare($sql);
```
```