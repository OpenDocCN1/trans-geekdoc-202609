+   12. If there were no errors, add the record to the database:

```
if (empty($add_product_errors)) {
    $q = 'INSERT INTO non_coffee_products (non_coffee_category_id,
        name, description, image, price, stock) VALUES (?, ?, ?, ?, ?, ?)';
    $stmt = mysqli_prepare($dbc, $q);
    mysqli_stmt_bind_param($stmt, 'isssdi', $_POST['category'],
        $name, $desc, $_SESSION['image']['new_name'], $_POST['price'],
        $_POST['stock']);
    $name = strip_tags($_POST['name']);
    $desc = strip_tags($_POST['description']);
    mysqli_stmt_execute($stmt);
}
```

As explained in Chapter 7, to use prepared statements, the first step is to define the query, using placeholders (the question marks) in lieu of actual values. Then the statement is prepared. Next, the placeholders are bound, by type, to PHP variables. The second argument to the mysqli_stmt_bind_param() function indicates that the first placeholder is an integer, the next three are strings, the fifth is a decimal, and the last is another integer.

Four of the values to be used in the query come from $_POST and $_SESSION directly. The other two values will come from local variables, after the strip_tags() function is applied.

If you have problems when executing this script, you can use the following line (after preparing the statement) to see what the problem is:

```
if (!$stmt) echo mysqli_stmt_error($stmt);
```

+   13. If the query created a new record, print a message and perform some cleanup:

```
if (mysqli_stmt_affected_rows($stmt) == 1) {
    echo '<h4>The product has been added!</h4>';
    $_POST = array();
    $_FILES = array();
    unset($file, $_SESSION['image']);
}
```

If one row was affected, a message will be printed, and the variables will be reset (because the form will be shown again, and it shouldn't display the previous values).