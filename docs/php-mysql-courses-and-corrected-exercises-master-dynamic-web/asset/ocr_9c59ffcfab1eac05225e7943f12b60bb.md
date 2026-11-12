In this syntax, $param1 is a mandatory parameter, while $param2 is an optional parameter with a default value.

When the function is called, if no argument is passed for $parametre2, its default value will be used. Otherwise, the value passed during the call will replace the default value.

Here's an example of how to use functions with default parameters:

```
<?php
function greet($name = "My friend") {
   echo "Hello, $name!";
}

// Function calls with and without parameter specification
greet(); // Display "Hello, My friend!"
echo "<br>"; // Line break
greet("Alice"); // Display "Hello, Alice!
?>

```

In this example, the greet() function accepts a $name parameter with a default value of "My friend". When the function is called with no arguments, it uses this default value. When an argument is passed, it replaces the default value, hence the following result obtained from executing this code: