Strictly speaking, an argument is a value that you pass to a function, and a parameter is the variable within the function that receives the argument. In practice, programmers often use the two terms interchangeably.

To specify parameters for your function, insert one or more variable names between the parentheses, as follows:

```
function myFunc( $oneParameter, $anotherParameter ) {
  // (do stuff here)
}
```

You can include as many parameter variables as you like. For each parameter you specify, a corresponding argument needs to be passed to the function when it’s called. The arguments passed to the function are then placed in these parameter variables. Here’s an example:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Saying hello with style</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Saying hello with style</h1>
<?php
function helloWithStyle( $font, $size ) {
  echo "<p style=\"font-family: $font; font-size: {$size}em;\">Hello, world!</p>";
}
helloWithStyle( "Helvetica", 2 );
helloWithStyle( "Times", 3 );
helloWithStyle( "Courier", 1.5 );
?>
</body>
</html>
```

This code creates a function, helloWithStyle(), that has two parameter variables: $font and $size. These variables are then used within the function to set the font and size of the text via CSS.

By the way, the curly bracket syntax used in the code ${size}em is useful when you need to include some letters and/or numbers — in this case, em — immediately after a variable name. You can find out more about this syntax in Chapter 5.

Next, the code calls the helloWithStyle() function three times, passing in different arguments each time. For each function call, the $font parameter takes on the value of the first argument, and the $size parameter takes on the value of the second argument.

Notice how the order of the arguments in the function calls matches the order of the parameters in the function definition.