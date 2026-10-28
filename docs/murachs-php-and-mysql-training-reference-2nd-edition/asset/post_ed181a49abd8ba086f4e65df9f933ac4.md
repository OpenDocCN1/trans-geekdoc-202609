
## How to set the error mode for PDO

Figure 19-5 shows how to set the error mode for PDO. By default, PDO uses the “exception” mode when it connects to the database. As a result, if there’s an error when connecting to the database, PDO emits a standard PHP warning message, and it throws an exception that you can catch and handle.

After that, however, PDO uses the “silent” error mode by default when executing SQL statements. As a result, if there’s an error executing a SQL statement, PDO doesn’t throw an exception and it doesn’t issue a standard PHP warning. Instead, it sets the error in the database object (for dynamic SQL statements) or in the statement object (for prepared SQL statements). Then, to view the error, you can use the errorCode and errorInfo methods on the database or statement object. However, this requires that you check for errors after each database call.

Since “silent” mode doesn’t emit a PHP warning, it’s more difficult to debug than the other two modes. As a result, you’ll typically want to use one of the other two modes when you’re testing and debugging. That way, PDO emits a traditional PHP warning that PHP displays on your web page if you encounter an error. This makes it easy for you to view the error message and debug the problem. However, you usually don’t want to display these error messages to the users of your production applications.

For new web applications, it makes sense to use the “exception” error mode. This error mode allows you to use a try/catch statement to catch any exceptions that are thrown by PDO. Since this approach doesn’t require you to check for errors after each database call, it provides a flexible way to handle errors. In addition, if you catch all the exceptions that might be thrown and handle them appropriately, this works well for production applications.

The first example in this figure shows how to use the PDO class to set the error mode. Here, the code creates an array of options. This array contains a single element that sets the error mode attribute of the PDO object to the “exception” mode. Then, this code passes that array as the optional fourth parameter to the constructor of the PDO class. Although this example only sets a single option, you can include multiple options in the options array if that’s necessary.

The second example shows another way to set the error mode. This technique allows you to set the error mode after you create the PDO object. To do that, you use the setAttribute method of the PDO object to set the error mode attribute to the correct error mode.

The third example shows how to use a try/catch statement to catch the PDOException objects that might be thrown when you attempt to execute a SQL statement. Here, the SELECT statement incorrectly refers to the “product” table instead of the “products” table. As a result, when the code attempts to execute the prepared SELECT statement, it throws a PDOException. Then, execution jumps into the catch block. Within the catch block, the code uses the getMessage method of the exception to get the error message. Then, it displays the message and exits the script.

## The three error modes for PDO

| Name | Description |
|---|---|
| `ERRMODE_SILENT` | This is the default error mode. PDO sets the error in the database or statement object, but it doesn’t emit a PHP warning message or throw an exception. To access the error, you can use the errorCode() and errorInfo() methods on the database or statement object. However, this requires you to check the error code after each database call. |
| `ERRMODE_WARNING` | PDO sets the error and doesn’t throw an exception as in “silent” mode, but does emit a PHP warning message. This setting is useful during testing and debugging. |
| `ERRMODE_EXCEPTION` | PDO sets the error as in “silent” mode and throws a PDOException object that reflects the error code and error message. This setting is also useful during testing and debugging, and it makes it easier for you to structure your error-handling code. |

### How to use the constructor of the PDO class to set the error mode

```php
$dsn = 'mysql:host=localhost;dbname=my_guitar_shop';
$username = 'mgs_user';
$password = 'pa55word';
$options = array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION);

try {
    $db = new PDO($dsn, $username, $password, $options);
} catch (PDOException $e) {
    $error_message = $e->getMessage();
    echo "<p>Error connecting to database: $error_message </p>";
    exit();
}
```

### How to use the setAttribute method to set the error mode

```php
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

### How to use a try/catch statement to catch PDOException objects

```php
try {
    $query = 'SELECT * FROM product';
    $statement = $db->prepare($query);
    $statement->execute();
    $products = $statement->fetchAll();
    $statement->closeCursor();
} catch (PDOException $e) {
    $error_message = $e->getMessage();
    echo "<p>Database error: $error_message </p>";
    exit();
}
```

### Description

- When you use PDO to execute SQL statements, you can choose between one of three error modes. Of these error modes, we recommend the “exception” error mode.

Figure 19-5 How to set the error mode for PDO

## A model in PDO

Figure 19-6 shows the code for a model that works with the database named my_guitar_shop2. This model uses prepared statements, and it uses the “exception” error mode. In the next chapter, you’ll see how you can use this model with the Product Manager application. For now, though, you can focus on the functions that it provides for retrieving, adding, updating, and deleting the data in the categories and products tables.

This figure begins by showing the code for the database.php file. Although this code isn’t technically part of the model, I have included it here because it creates the database connection variable ($db) that’s used by the functions in the model. This code uses the database named my_guitar_shop2 and sets the error mode to the “exception” mode. As a result, if PDO encounters an error when executing SQL statements, it throws an exception.

The database.php file also defines a function named display_db_error that’s used by the other functions in the model to display a database error to the user. To start, this function uses the global keyword to get access to the $app_path variable. This variable is needed by the header for the db_error.php file, and you’ll learn more about how this works in the next chapter. Then, this function displays the db_error.php file and exits the script.

The category_db.php file contains the get_categories function that returns a two-dimensional array of categories from the database. In addition, it contains the get_category method that returns a one-dimensional array for the specified category. Both of these methods use prepared statements. They use the fetchAll and fetch methods of the statement object to return arrays. And they use try/catch statements to catch and handle any errors that occur. If an error occurs, they call the display_db_error function of the database.php file to display the error and exit the script.

The benefit of returning an array instead of the PDOStatement object is that it separates the database layer (the model) from the presentation layer (the view). Another approach would be to return the PDOStatement object. Although this approach mixes the database layer (the model) with the presentation layer (the view), it can run more efficiently for result sets that are large. In this case, though, the categories table is small enough that there’s little downside to returning a two-dimensional array.

The product_db.php file contains the functions for retrieving, adding, updating, and deleting the products in the database. For the most part, these functions work like the functions in the category_db.php file.

The first two functions retrieve product data. Here, the get_products_by_category function returns a two-dimensional array of products for the specified category ID. Then, the get_product function returns a one-dimensional array for the product with the specified product ID.

The next three functions allow the user to add, update, and delete a product. To start, the add_product function accepts six parameters. Then, it binds these parameters to the named parameters in the INSERT statement, and it executes the statement. Last, it returns the product ID that MySQL automatically generates when it inserts the row in the database.

The update_product function accepts seven parameters, it binds these parameters to the named parameters in the UPDATE statement, and it executes the statement. Then, it returns the number of rows that were affected by the UPDATE statement. Since each product has a unique product ID, this function returns a value of 1 if an existing product ID is specified. Otherwise, it returns a value of 0. As a result, the code that calls this function can check this value and take an appropriate action.

The delete_product function accepts the product ID as a parameter, it binds the value for this parameter to the named parameter in the DELETE statement, and it executes the statement. Like the update_product function, this function returns a value of 1 if one row was deleted and a value of 0 if no rows were deleted.
