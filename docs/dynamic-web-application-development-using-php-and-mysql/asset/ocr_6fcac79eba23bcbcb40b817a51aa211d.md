as we would not know the length of the string in advance. To overcome this, PHP has a function called ‘strlen’ (string length) which returns the number of characters in a string:

```
`length = strlen(string);`
```

We are going to explain how to create our own functions in Chapter 13, but for now it is probably worth explaining what a PHP function is and how we can use some of those prewritten and provided with the language. A function is an associated group of statements which, when invoked, executes those statements. Functions can be written to receive values which they then process and affect the result produced by the associated statements. Functions can return a single piece of data, such as an integer or string. Figure 11.3 illustrates graphically that a function can be viewed as a ‘black box’ with data being sent to it and the result being returned.

> **NOTE** — Exactly how the function performs its ‘magic’ within the box is not known to the user.

In the case of the ‘strlen’ function, it can accept a single string value and return the length of the string. The use of the function is shown in the following script:

```
```php
<?php
// File: example11-2.php

$strName = "Simon Stobart";

$intStringLength = strlen($strName);
echo "<p>The string is $intStringLength characters long</p>";
?>
```
```

In the above script, the value of $strName is passed to the function and the resulting string length is stored in variable $intStringLength. The output from the script is:

```
`The string is 13 characters long`
```

![](bbox=[0.047, 0.698, 0.696, 0.944])