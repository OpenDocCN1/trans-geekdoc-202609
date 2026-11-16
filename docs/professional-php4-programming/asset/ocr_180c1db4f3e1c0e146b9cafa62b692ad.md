```
<?php
//Sample_Switch.php
$color = "peach";
switch ($color) {
case "peach":
    echo("Peach is my favorite color <br>");
case "pink":
    echo("Pink is my favorite color");
}
?>
```

This would produce the unexpected result of both pink and peach being the favorite color. This is syntactically a valid construct, that is this might have been useful to us if we wanted to express a logical OR condition between the two cases (see below). The lack of a break statement after the first echo statement caused the execution to fall through and execute the next statement.

# Logical Errors

Logical errors are those that have very little to do with the language constructs themselves. In fact, logical errors occur with code that is syntactically and semantically correct. Logical errors occur when the programmer writes code hoping it would do something whereas the code turns out to do something else. The classic example is misspelt variable names that take a bad turn, as PHP does not require variables to be declared before hand. These errors are hard to trace unless you have good test cases. Let us take a look at the following code for an example of a logical error:

```
<?php
//Logical_Error.php
for ($i = 1; $i < 10; $i++)
    print("Number: " . $i . "<br>");
?>
```

Here the programmer intended the script to print the numbers 1 to 10, inclusive. However, since the comparison operator was < as opposed to <= the last comparison 10 < 10 did not succeed and only the numbers 1 to 9 were printed.

The foreach construct available in PHP4 prevents such an error from creeping in when dealing with arrays. As a rule of thumb it is a good idea to use the foreach constructor when iterating over arrays.

# Environmental Errors

Environmental errors are a result of factors extraneous to the program and often go undetected by test cases designed to catch syntax, semantic, and logical errors. In fact, these errors crop up only when external entities such as files, network connections, and input data assume a form or behave in a manner unexpected by the program. For example, consider a script which opens files for write operations on the server's local disk. This script might work fine in a development environment, but will fail in a production environment where disk access privileges might be much more restrictive than on the development workstation.