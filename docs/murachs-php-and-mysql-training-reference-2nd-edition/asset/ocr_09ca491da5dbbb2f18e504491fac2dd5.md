# How to code a function

# The syntax

```
```php
function function_name([parameter_list]) {
    // statements that are executed by the function
}
```
```

# A function with one parameter that returns an array of products

```
```php
function get_products_by_category($category_id) {
    global $db;
    $query = 'SELECT * FROM products
              WHERE products.categoryID = :category_id
              ORDER BY productID';
    $statement = $db->prepare($query);
    $statement->bindValue(":category_id", $category_id);
    $statement->execute();
    $products = $statement->fetchAll();
    $statement->closeCursor();
    return $products;
}
```
```

# A function with four parameters that adds a product

```
```php
function add_product($category_id, $code, $name, $price) {
    global $db;
    $query = 'INSERT INTO products
              (categoryID, productCode, productName, listPrice)
              VALUES
              (:category_id, :code, :name, :price)';
    $statement = $db->prepare($query);
    $statement->bindValue(':category_id', $category_id);
    $statement->bindValue(':code', $code);
    $statement->bindValue(':name', $name);
    $statement->bindValue(':price', $price);
    $statement->execute();
    $statement->closeCursor();
}
```
```

# How to call a function

# A function call with one argument and a returned array

```
$products = get_products_by_category($category_id);
```

# A function call with four arguments and no returned value

```
add_product($category_id, $code, $name, $price);
```

# Description

+   - When you create a function, you can code a parameter list within parentheses. A parameter list contains one or more parameters.
+   - To return data from a function, you code a return statement in the body of the function. This statement ends the execution of the function and returns the specified value.
+   - A variable that’s declared outside of a function isn’t available within the function. This is called a variable’s scope, and you’ll learn more about it in chapter 13. For now, you can use the global keyword to make the variable available in the function.