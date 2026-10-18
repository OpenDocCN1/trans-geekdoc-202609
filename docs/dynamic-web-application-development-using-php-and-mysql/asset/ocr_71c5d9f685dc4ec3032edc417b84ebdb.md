The above randomly seeds the random number generator with a random number produced from when the current time is obtained from the microtime() function. We are now ready to obtain random numbers and the function rand() enables us to do this. The format of this function is:

```
number = rand ();
```

The rand() function can be invoked without any parameters and this returns a random number, the maximum and minimum values of which are outside your control. However, you can limit the range of random numbers produced by including start and end parameters, like this:

```
number = rand (start, end);
```

The following script illustrates generating a random number between 1 and 6. This script could be therefore used to represent the role of a dice:

```
<?php
// File: example13-24.php

srand( (double) microtime() * 1000000);
$intRandVal = rand(1,6);
echo "<p>Random Number: $intRandVal</p>";
?>
```

# 13.5 Fruit-machine example

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

echo "<h2>Try your luck at the fruit machine &ellipsis;... </h2>";
echo "<table width='450'><tr>";
echo "<td><img src='graphics/$strFirst.gif' alt='$strFirst'/></td>";
```