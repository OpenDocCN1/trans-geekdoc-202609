# How to use named parameters

```
```php
$query = 'SELECT * FROM products
          WHERE categoryID = :category_id
          AND listPrice > :price';
$statement = $db->prepare($query);
$statement->bindValue(':category_id', $category_id);
$statement->bindValue(':price', $price);
$statement->execute();
$products = $statement->fetchAll();
$statement->closeCursor();
```
```

# How to use question mark parameters

```
```php
$query = 'SELECT * FROM products
          WHERE categoryID = ?
          AND listPrice > ?';
$statement = $db->prepare($query);
$statement->bindValue(1, $category_id);
$statement->bindValue(2, $price);
$statement->execute();
$products = $statement->fetchAll();
$statement->closeCursor();
```
```

# How to modify data

```
```php
// Sample data
$category_id = 2;
$code = 'hofner';
$name = 'Hofner Icon';
$price = '499.99';

// Prepare and execute the statement
$query = 'INSERT INTO products
              (categoryID, productCode, productName, listPrice)
          VALUES
              (:category_id, :code, :name, :price)';
$statement = $db->prepare($query);
$statement->bindValue(':category_id', $category_id);
$statement->bindValue(':code', $code);
$statement->bindValue(':name', $name);
$statement->bindValue(':price', $price);
$success = $statement->execute();
$row_count = $statement->rowCount();
$statement->closeCursor();

// Get the last product ID that was automatically generated
$product_id = $db->lastInsertId();

// Display a message to the user
if ($success) {
    echo "<p>$row_count row(s) was inserted with this ID: $product_id</p>";
} else {
    echo "<p>No rows were inserted.</p>";
}
```
```

Figure 19-4  How to work with prepared statements (part 2 of 2)