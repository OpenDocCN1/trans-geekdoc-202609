+   - A scalar value is a literal number, string, or Boolean value. A scalar value cannot contain operators, variables, or function calls.
+   - The *include path* specifies the directories to search for included files.
+   - In PHP, all functions are stored in the global namespace. As a result, you must be careful to avoid naming conflicts for function names. However, as of PHP 5.3, you can store functions in a *namespace* other than the global namespace. This provides a flexible way to avoid naming conflicts.
+   - A *variable function* is a function name stored in a variable as a string.
+   - A *callback* is a function that's passed as an argument to another function. You can use a variable function in a callback.
+   - An *anonymous function* is a function that doesn't have a name. You can store an anonymous function in a variable and use it as a variable function.
+   - A *closure* is an inner function that has access to the outer function's variables.

# # Exercise 13-1 Modify the Shopping Cart application

In this exercise, you can modify and enhance the library of functions for a simplified version of the Shopping Cart application.

# ## Open and test the application

+   1. Run the application that's stored in the ex_starts/ch13_ex1 directory.
+   2. Test this application by adding items to the cart, by modifying items, and by emptying the cart.
+   3. Open the index.php and cart.php files for this application and review the code. Note that the code in the cart.php file uses the $_SESSION variable within the library of cart functions.

# ## Pass the cart by value

+   4. Modify the parameters for the functions in the cart.php file so the first parameter for each function is a cart array that's passed by value like this:

```
function add_item($cart, $key, $quantity) {}
function update_item($cart, $key, $quantity) {}
function get_subtotal($cart) {}
```

+   5. Modify the code for the functions so they use the $cart parameter. To do that, you can use the $cart parameter instead of getting the cart array from the global $_SESSION array.
+   6. Modify the code in the index.php file so it uses these functions instead of getting the cart array from the global $_SESSION array. That way, you only need to get the cart array from the $_SESSION array at the beginning of the script. However, you need to set the cart array in the $_SESSION array each time you change the contents of the cart.