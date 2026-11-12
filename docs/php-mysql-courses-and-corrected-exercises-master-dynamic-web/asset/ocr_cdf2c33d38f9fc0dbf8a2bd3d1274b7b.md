```
$age = 30; // An integer
$price = 19.99; // A floating-point number
$name = 'John'; // A character string
$message = "John is 20!"; // Another string
$is_true = true; // A Boolean (true)
$is_false = false; // A Boolean (false)
$salary = null; // No value is assigned to the variable
```

```
// Display the data type of each variable
echo gettype($age) . "<br>"; // Display "integer".
echo gettype($price) . "<br>"; // Display "double"
echo gettype($name) . "<br>"; // Display "string"
echo gettype($message) . "<br>"; // Display "string"
echo gettype($is_true) . "<br>"; // Display "boolean"
echo gettype($is_false) . "<br>"; // Display "boolean"
echo gettype($salary) . "<br>"; // Display "NULL".
?>
```

The code in this example uses the **gettype()** function to get the data type of each variable, then uses **echo** to display each data type with a **<br>** tag to jump to the next line in the HTML output.
Finally, the code output will be something like this: