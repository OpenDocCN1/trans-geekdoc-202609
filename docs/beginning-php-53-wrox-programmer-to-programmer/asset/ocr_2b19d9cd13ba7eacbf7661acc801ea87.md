# Part II: Learning the Language

The __call() method is where the meat of the class lies:

```
public function __call($methodName, $arguments) {
    if ( in_array($methodName, CleverString::$$allowedFunctions) ) {
        array_shift($arguments, $this->$theString);
        return call_user_func_array($methodName, $arguments);
    } else {
        die ("<p>CleverString::$methodName doesn't exist</p>");
    }
}
```

The first method stores the method that was called in a $methodName parameter, and the array containing any passed arguments is stored in the $arguments parameter.

The next method checks if $methodName is contained in the CleverString::$allowedFunctions array. This is a private static property, created at the start of the class, which contains the allowed method name:

```
private static $$allowedFunctions = array("strlen", "strtoupper", "strpos");
```

If $methodName is not one of the three functions, the script terminates with an error message:

```
die ("<p>CleverString::$methodName doesn't exist</p>");
```

This ensures that only the string strlen(),strtoupper(), and strpos() can be called via the class. In reality, for this simple example, the script allows only these three functions to be called. Generally, for security it's a good idea to check methods of this nature against a list of allowed methods.

Once $methodName has been successfully validated, the method adds the object's stored string value, $this->$theString, to the start of the $arguments array:

```
array_shift($arguments, $this->$theString);
```

This is because built-in functions—including the three that this is capable of calling—expect the string to be passed on the first argument that is passed to them.

Finally, the __call() method is ready to call the appropriate string function. It does use the PHP function call_user_func_array(), which expects the function name as the first argument, and the argument list—as an array—the __call() method returns the return value from the string function back to the method's calling:

```
return call_user_func_array($methodName, $arguments);
```

The script tests the class by creating a new CleverString object, setting its string value to "Hello!", displaying the stored string value, and various methods to operate on the string:

```
$myString = new CleverString;
$myString->setString("Hello!");
echo "<p>The string is: " . $myString->getString() . "</p>";
echo "<p>The length of the string is: " . $myString->strlen() . "</p>";
echo "<p>The string in uppercase letters is: " . $myString->strtoupper() . "</p>";
```