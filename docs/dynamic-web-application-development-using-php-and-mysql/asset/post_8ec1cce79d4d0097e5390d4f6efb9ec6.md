
$floFahrenheit. This indicates that the function expects to receive a value when it is invoked, which it will store in the variable $floFahrenheit:

```
function fahrenheitToCelsius($floFahrenheit) {
```

The second difference is the function invocation which now includes a constant value to pass to the function:

```
fahrenheitToCelsius(100);
```

The result of the above script is correct:

100°F = 37.777777778°C

We can rewrite the script slightly to prove that we can pass a variable value:

```
<?php
// File: example13-8.php

echo "<p>Fahrenheit To Celsius</p>";

function fahrenheitToCelsius($floFahrenheit) {
    $floCelsius = (5/9)*($floFahrenheit-32);
    echo "<p>$floFahrenheit<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
}

$floFahrenheitOne = 100;
fahrenheitToCelsius($floFahrenheitOne);
?>
```

The above script illustrates two important things. Firstly that we can pass a variable directly to a function:

```
fahrenheitToCelsius($floFahrenheitOne);
```

However, it also indicates that the name of a variable passed to a function doesn't have to be the same as the argument the function receives:

```
function fahrenheitToCelsius($floFahrenheit) {
```

| NOTE | When a function receives a value, it copies this into its argument and so it doesn't matter what name it is given. |
|------|-------------------------------------------------------------------------------------------------------------------|

## Multiple arguments

Functions can be written to accept multiple arguments. The following script illustrates this by making our temperature conversion function a little more flexible. The function is now able to accept two arguments and make conversions either way between Celsius and Fahrenheit:

```
<?php
// File: example13-9.php

echo "<p>Temperature Converter</p>";
```

We can adapt the above script to illustrate that we can invoke functions from within a loop construct:

```
<?php
// File: example13-10.php

function temperatureConvert($floTemp, $strType) {
    if ($strType == "F") {
        $floCelsius = (5/9)*($floTemp-32);
        echo "<p>$floTemp<sup>o</sup>F = $floCelsius<sup>o</sup>C</p>";
    }
    else {
        $floFahrenheit = (9/5)*$floTemp+32;
        echo "<p>$floTemp<sup>o</sup>C = $floFahrenheit<sup>o</sup>F</p>";
    }
}

echo "<h2>Some nice holiday temperatures:</h2>";
for($intCount=25;$intCount<40;$intCount++)
    temperatureConvert($intCount, "C");
?>
```

The output from the above script is illustrated in Figure 13.4.

## Default arguments

Sometimes it is useful if functions have default arguments. This allows us to invoke a function without the need to pass all the arguments to it if we don’t want to. Default arguments are assigned in the function declaration. Consider the following script which modifies our previous temperature conversion function. The modification assumes that if only the temperature is sent then the temperature type is Celsius.

```
<?php
// File: example13-11.php

function temperatureConvert($floTemp, $strType = "C") {
    if ($strType == "F") {
        $floCelsius = (5/9)*($floTemp-32);
        echo "<p>$floTemp<sup>o</sup>F = 
                $floCelsius<sup>o</sup>C</p>";
    }
    else {
        $floFahrenheit = (9/5)*$floTemp+32;
        echo "<p>$floTemp<sup>o</sup>C = 
                $floFahrenheit<sup>o</sup>F</p>";
    }
}

echo "<h2>Some nice holiday temperatures:</h2>";
for($intCount=25;$intCount<40;$intCount++)
    temperatureConvert($intCount);
?>
```

Note that only one of the function arguments has a default value:

```
function temperatureConvert($floTemp, $strType = "C") {
```

### FIGURE 13.4 Functions in loops

![](img/b2471264f405d17994ef173e4b9cec92_401_0.png)

### Some nice holiday temperatures:

- 25°C = 77°F
- 26°C = 78.8°F
- 27°C = 80.6°F
- 28°C = 82.4°F
- 29°C = 84.2°F
- 30°C = 86°F
- 31°C = 87.8°F
- 32°C = 89.6°F
- 33°C = 91.4°F
- 34°C = 93.2°F
- 35°C = 95°F
- 36°C = 96.8°F
- 37°C = 98.6°F
- 38°C = 100.4°F
- 39°C = 102.2°F

Also, note that the function invocation no longer specifies the temperature type:

```
temperatureConvert($intCount);
```

The output for the above script is the same as that shown in Figure 13.4. In some of our examples of user-defined functions, we have shown that we can pass values to the function and these can be used to affect the functionality of the function itself. What we have not yet seen is how we can return a value from a function.

## Returning a value

The keyword ‘return’ is used to return a value from a function:

```
return value;
```

The function returns control to the location where it was invoked from when the keyword ‘return’ is encountered. Let us modify our script to illustrate a function return:

```
<?php
// File: example13-12.php

function temperatureConvert($floTemp, $strType = "C") {
    if ($strType == "F")
        $floAnswer = (5/9)*($floTemp-32);
    else
        $floAnswer = (9/5)*$floTemp+32;
    return $floAnswer;
}

echo "<h2>Some nice holiday temperatures:</h2>";
for($intCount=25;$intCount<40;$intCount++) {
    $floFahrenheit = temperatureConvert($intCount);
    echo "<p>$intCount<sup>o</sup>C = $floFahrenheit<sup>o</sup>F</p>";
}
?>
```

The above script is a rewrite of the temperatureConvert() function so that it uses the keyword ‘return’ to return the answer to the temperature conversion:

```
return $floAnswer;
```

The ‘for’ loop invoking the function is also slightly modified so that the value returned from the function is stored in a variable $floFahrenheit:

```
for($intCount = 25;$intCount<40;$intCount++) {
    $floFahrenheit = temperatureConvert($intCount);
    echo "$intCount<sup>o</sup>C = $floFahrenheit<sup>o</sup>F<br>";
}
```

The output from the above script is the same as that in Figure 13.4.

| NOTE | When the function has executed the flow of control of the program it returns to the point in the script immediately after where it was called. |
|------|-----------------------------------------------------------------------------------------------------------------------------------------------|

It is possible to directly output the value returned from a function. Consider this modification to the above script:

```
<?php
// File: example13-13.php

function temperatureConvert($floTemp, $strType = "C") {
    if ($strType == "F")
        $floAnswer = (5/9)*($floTemp-32);
    else
        $floAnswer = (9/5)*$floTemp+32;
```

```
return $floAnswer;
}
echo "<h2>Some nice holiday temperatures:</h2>";
for($intCount=25;$intCount<40;$intCount++)
    echo "<p>$intCount<sup>o</sup>C = " . temperatureConvert($intCount) . "<sup>o</sup>F</p>";
?>
```

The only difference between the above script and ‘example13-12.php’ is that the echo construct and function call have been combined:

```
echo "$intCount<sup>o</sup>C = " . temperatureConvert($intCount) . "<sup>o</sup>F<br>";
```

## Returning more than one value

We mentioned previously that functions within PHP cannot return more than one value. What is more correct is that they can return only a single type. Arrays can be used to ‘get around’ the issue of functions being able to return a single value.

The following script illustrates the use of an array to return more than one ‘item’ from a function:

```
<?php
// File: example13-14.php

function temperatureConvert($floTemp, $strType = "C") {
    if ($strType == "F") {
        $floAnswer = (5/9)*($floTemp-32);
    } else
        $floAnswer = (9/5)*$floTemp+32;

    $arrResult = array();
    $arrResult[] = $floAnswer;
    $arrResult[] = $strType;
    return $arrResult;
}
echo "<h2>Some nice holiday temperatures:</h2>";
$floCelsius = 99.9;
$arrResult = temperatureConvert($floCelsius);
echo "<p>$floCelsius<sup>o</sup>" . $arrResult[1] . " = " . $arrResult[0] . "<sup>o</sup>F</p>";
?>
```

In this script the function temperatureConvert declares an array and assigns into the array the values of $floAnswer and $strType. The array is then returned from the function:

```
$arrResult = array();
$arrResult[] = $floAnswer;
$arrResult[] = $strType;
return $arrResult;
```

The function invocation receives the returned value from the function (which is an array) and accesses each of the values within the array:

```
```php
$arrResult = temperatureConvert($floCelsius);
echo "<p>$floCelsius<sup>o</sup>" . $arrResult[1] . " = " .
$arrResult[0] . "<sup>o</sup>F</p>";
```
```

The output from the above script is illustrated in Figure 13.5.

### FIGURE 13.5 ‘Multiple’ return values

![](img/b2471264f405d17994ef173e4b9cec92_404_0.png)

## Arguments passed by value

All of our examples of passing arguments to functions thus far are examples of passing by value. This means that a copy of the variable is passed. If that value is changed in the function, the value of the variable outside the function remains unchanged. Therefore this script:

```
```php
<?php
// File: example13-15.php

function reverseIt($strString) {
    $strString = strrev($strString);
}

$strName = "Simon";
echo "<p>$strName ";
reverseIt($strName);
echo "reversed is $strName</p>";
?>
```
```

doesn’t work as intended and produces the output:

```
Simon reversed is Simon
```

## Arguments passed by reference

PHP supports passing a variable to a function ‘by reference’. To pass a variable by reference, we simply include the character & before the variable name in the function definition. The
