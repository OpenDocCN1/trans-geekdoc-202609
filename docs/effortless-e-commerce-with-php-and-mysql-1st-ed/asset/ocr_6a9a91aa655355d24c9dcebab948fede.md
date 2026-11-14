Finally, both values are returned as an array. Because this function returns an array, you must use the `list()` function when calling it:

```
list($type, $id) = parse_sku($sku);
```

The `list()` function assigns to the variables — $type and $id — the values returned by the code on the right side of the equation.

The most appropriate place to define these two functions is within the already existing `product_functions.inc.php` script, found in the `includes` directory. Go ahead and do that before proceeding.

# MAKING A SHOPPING CART

After defining the stored procedures and the helper functions, three files must be created:

+   - cart.php will do all the work (it’s the controller).
+   - cart.html is the view file for the cart.
+   - emptycart.html is the view file if there’s nothing in the cart.

Let's create these files now, starting with the PHP script.

# Creating the PHP Script

As in Chapter 8, thanks to the use of stored procedures and included HTML files, the PHP script itself becomes surprisingly short and quite tidy. The entire `cart.php` is only 50 lines of code, including comments and blank lines! Most of the script is logic that invokes the correct stored procedure based on how the script is accessed.

+   1. Create a new PHP script in your text editor or IDE to be named `cart.php` and stored in the Web root directory.

+   2. Include the configuration file:

```
<?php
require ('./includes/config.inc.php');
?>
```

+   3. Check for, or create, a user session ID:

```
if (isset($_COOKIE['SESSION'])) {
$uid = $_COOKIE['SESSION'];
```