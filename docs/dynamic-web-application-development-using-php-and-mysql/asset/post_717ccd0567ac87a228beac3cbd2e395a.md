
Passing of variables by reference permits the function to modify the original variable value. Consider the example below:

```
<?php
// File: example13-16.php

function reverseIt(&$strString) {
    $strString = strrev($strString);
}
$strName = "Simon";
echo "<p>$strName ";
reverseIt($strName);
echo "reversed is $strName</p>";
?>
```

The above script outputs the following:

Simon reversed is nomiS

### Calling functions within functions

Functions can invoke functions from within themselves. Consider the following script:

```
<?php
// File: example13-17.php
function decimal($floNum) {
    $floNum = round($floNum, 2);
    return $floNum;
}

function multiply($floNumber) {
    $floNumber *= 3.12;
    echo "<p>$floNumber</p>";
    $floNumber = decimal($floNumber);
    echo "<p>$floNumber</p>";
}

$floNumber = 5.2234;
multiply($floNumber);
?>
```

In this script a floating point number is defined and passed to function multiply():

```
$floNumber = 5.2234;
multiply($floNumber);
```

The function multiplies the number by 3.12 and then displays its current value:

```
$floNumber *= 3.12;
echo "<p>$floNumber</p>";
```

FIGURE 13.6 Output from a function calling another function

![](img/b2471264f405d17994ef173e4b9cec92_406_0.png)

It then invokes function decimal(), passing it the value of $floNumber and assuming that the value is returned. Finally the number is displayed:

```
$floNumber = decimal($floNumber);
echo "$floNumber";
```

Function decimal() receives the variable and using a predefined function round() rounds the value to two decimal places and returns this value:

```
function decimal($floNum) {
    $floNum = round($floNum, 2);
    return $floNum;
}
```

The output from the above script is illustrated in Figure 13.6.

### Recursive functions

A recursive function is one which calls itself. Recursive functions are useful in evaluating certain types of mathematical functions. The following example is a recursive function used to calculate whether a number is a power of 2:

```
<?php
// File: example13-18.php

function isPowerOfTwo($intNumber) {
    if ($intNumber == 1)
        return "<p>yes</p>";
    elseif ($intNumber%2 == 1)
        return "<p>no</p>";
    else {
        $intNumber /= 2;
        return isPowerOfTwo($intNumber);
    }
}

echo isPowerOfTwo(256) ;
?>
```

In this example, the number 256 is checked to see if it is a power of two or not by passing it to the isPowerOfTwo() function:

```
echo isPowerOfTwo(256) ;
```

When the function is invoked an if statement checks to see if the number is equal to one. If so the value 'yes' is displayed. If not then another if statement is used to check if the remainder of dividing the current value of $intNumber by 2 is equal to 1. If this is true then the value 'no' is displayed:

```
if ($intNumber == 1)
    return "<p>yes</p>";
elseif ($intNumber%2 == 1)
    return "<p>no</p>";
```

If the number does not satisfy either of these statements then it is divided by 2 and the function calls itself (by using the return keyword) and the process is repeated:

```
$intNumber /= 2;
return isPowerOfTwo($intNumber);
```

In this example the output generated is:

yes

## 13.2 Separating source files

Functions allow us to divide up our code into manageable pieces; however another way of dividing up code is to separate up a large PHP script into several smaller ones. This allows you to share and reuse parts of your scripts more easily.

Consider the following script:

```
<?php
// File: example13-19.php

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
?>
```

The above script is simply the temperatureConvert() function from a previous example. Now consider:

```
<?php
// File: example13-20.php

include_once ("example13-19.php");

echo "<h2>Some nice holiday temperatures:</h2>";
for($intCount=25;$intCount<40;$intCount++)
    temperatureConvert($intCount);
?>
```

The above script uses the ‘include_once’ statement to include a copy of the ‘example13-19.php’ script at the point indicated. The output from this script is the same as shown in Figure 13.4.

> **NOTE** The difference between ‘include’ and ‘include_once’ is that ‘include_once’ will only include the file once even if asked to include it a second time.

The ‘require’ and ‘require_once’ statements operate in exactly the same way as the ‘include’ and ‘include_once’ statements operate. The only difference is in how they handle failure. With ‘require’ and ‘require_once’, if a file is not located then a fatal error is generated and execution of the script is terminated.

## 13.3 Getting the time and date

Being able to access the system time and date is a very useful ability. Dates and times can be used for a variety of tasks, from the simple activity of being able to display the correct date and time on your web page to creating a time stamp of when a database record was created.

Both the date and time can be accessed through a single function called getdate():

```
$array = getdate();
```

The getdate() function returns an array containing the current date and time. The array is a string-indexed array and the index values are described in Table 13.1.

The following script illustrates accessing the date using the getdate() function:

```
<?php
// File: example13-21.php

$arrDate = getdate();

$intSeconds = $arrDate['seconds'];
$intMinutes = $arrDate['minutes'];
```

FIGURE 13.7 Date function

![](img/b2471264f405d17994ef173e4b9cec92_410_0.png)

This function returns a string consisting of two parts:

'msec sec'

The value of ‘sec’ is the number of seconds, which have passed since midnight on 1st January 1970. The ‘msec’ part of the string is the microseconds fraction of the current second. Here is the function in a script:

```
<?php
// File: example13-22.php

$strSecs = microtime();
echo "<p>$strSecs</p>";
?>
```

At the time of execution the output from the above script was:

0.29059500 1131475671

While we realize that the microtime() function does not seem very impressive it is actually very useful. We shall return to this function later in the chapter when we come to generate random numbers.

### Checking for a valid date

Sometimes a user is required to enter a date via a form. It is good practice to check that the date is in fact valid although it is not immediately obvious, for example, which of the following dates are valid:

-   6,29,2005
-   13,19,2005
-   2,28,2005
-   2,29,2000

The above randomly seeds the random number generator with a random number produced from when the current time is obtained from the microtime() function. We are now ready to obtain random numbers and the function rand() enables us to do this. The format of this function is:

```
$number = rand();
```

The rand() function can be invoked without any parameters and this returns a random number, the maximum and minimum values of which are outside your control. However, you can limit the range of random numbers produced by including start and end parameters, like this:

```
$number = rand($start, $end);
```

The following script illustrates generating a random number between 1 and 6. This script could be therefore used to represent the roll of a dice:

```
<?php
// File: example13-24.php

srand( (double) microtime() * 1000000);
$intRandVal = rand(1,6);
echo "<p>Random Number: $intRandVal</p>";
?>
```

## 13.5 Fruit-machine example

We are going to put together the knowledge we have learned on the subject of functions and random numbers to create a fruit-machine script. The script uses some simple images to represent the fruits in our fruit machine. These are illustrated in Figure 13.8.

These images are stored in the ‘graphics’ sub-directory below where the script is stored:

```
<?php
// File: example13-25.php

$arrFruits = array (1=>"apple", 2=>"orange", 3=>"lemon", 4=>"plum");

function randomNumber ($intStart, $intEnd) {
    srand( (double) microtime() * 1000000);
    $intRandVal = rand($intStart,$intEnd);
    return $intRandVal;
}

$strFirst = $arrFruits[randomNumber(1,4)];
$strSecond = $arrFruits[randomNumber(1,4)];
$strThird = $arrFruits[randomNumber(1,4)];

echo "<h2>Try your luck at the fruit machine ...</h2>";
echo "<table width='450'><tr>";
echo "<td><img src='graphics/$strFirst.gif' alt='$strFirst'/></td>";
```
