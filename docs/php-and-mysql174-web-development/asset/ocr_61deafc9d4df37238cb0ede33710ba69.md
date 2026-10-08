The call to fopen() fails, the function will return false. It will also cause PHP to emit a warning_level error (E_WARNING). You can deal with the error in a more user-friendly way by suppressing PHP's error message and giving your own:

The @ symbol in front of the fopen() tells PHP to suppress errors resulting from the function call. Usually, it's a good idea to know when things go wrong, but in this case we're going to deal with that problem elsewhere.

You can also write this line as follows:
$fp = @fopen("$document_root/../orders/orders.txt", 'a');

Using this method tends to make it less obvious that you are using the error suppression operator, so it may make your code harder to debug.

# Note

In general, use of the error suppression operator is not considered good style, so consider it a shortcut for now. The method described here is a simplistic way of dealing with errors. We look at a more elegant method for error handling in Chapter 7, “Error and Exception Handling.” But one thing at a time.

The if statement tests the variable $fp to see whether a valid file pointer was returned from the fopen() call; if not, it prints an error message and ends script execution.

The output when using this approach is shown in Figure 2.3.