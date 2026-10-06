# Part II: Learning the Language

Strictly speaking, an argument is a value that you pass to a function, and a parameter is the variable within the function that receives the argument. In practice, programmers often use the two terms interchangeably.

To specify parameters for your function, insert one or more variables within the parentheses, as follows:

```
function myFunc($oneParameter, $anotherParameter) {
  // (do stuff here)
}
```

You can include as many variables as you like. For each parameter you specify, a corresponding argument needs to be passed to the function when it's called. The arguments passed to the function are then placed in these variables. Here's an example:

```
<!DOCTYPE html PUBLIC-////W3//DTD HTML 1.0 Strict//EN">
"http://www.w3.org/TR/html1/DTD/html-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>Saying hello with style</title>
  <link rel="stylesheet" type="css" href="common.css" />
</head>
<body>
  <h1>Saying hello with style</h1>
</body>
</html>
```

```
<?php

helloStyle($font, $size) {
  echo "<p style='font-family: $font; font-size:${size}em;\>Hello, world!</p>";
}

helloStyle("Helvetica", 2);
helloStyle("Times", 3);
helloStyle("Courier", 1.5);


</body>
</html>
```

This code creates a function, helloStyle(), that has two parameter variables: $font and $size. These variables are then used within the function to set the font and size of the text CSS.

> By the way, curly bracket syntax used in the code ($size) is useful when you need to include some letters andor numbers — in this case, em — immediately after a variable name. You can find out more about this syntax in Chapter 5.

Next, the code calls helloStyle() function three times, passing different arguments each time. For each call, the $font parameter takes the value of the first argument, and the $size parameter takes the value of the second.

Notice the order of the arguments in the function calls matches the order of the parameters in the function definition.