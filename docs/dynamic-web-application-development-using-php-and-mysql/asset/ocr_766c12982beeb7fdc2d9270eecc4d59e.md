by a pair of parentheses which enclose a comma-separated list of arguments (if there are any). The script statements making up the function are enclosed within braces.

> **NOTE** — Even if there are no arguments to a function then the parentheses still need to be included.

We shall examine how functions ‘return’ a value a little later. However, for now let us examine how to create a function:

```
```php
<?php
// File: example13-1.php

echo "<p>Fahrenheit To Celsius</p>";
function fahrenheitToCelsius() {
    $floFahrenheit = 212;
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}
?>
```
```

The above script defined a function called fahrenheitToCelsius() which receives no arguments. The associated script within the function converts a Fahrenheit temperature value into a Celsius one. However, when we run the script, the code within the function is not processed. The reason is that we haven’t invoked the function. In the above script, we would do this with the call:

```
```php
fahrenheitToCelsius();
```
```

So, for example:

```
```php
<?php
// File: example13-2.php

echo "<p>Fahrenheit To Celsius</p>";

function fahrenheitToCelsius() {
    $floFahrenheit = 212;
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}

fahrenheitToCelsius();
?>
```
```

The output from the above script is:

```
```text
212°F = 100°C
```
```

> **NOTE** — In PHP, it doesn’t matter if the function is defined before or after the function invocation!