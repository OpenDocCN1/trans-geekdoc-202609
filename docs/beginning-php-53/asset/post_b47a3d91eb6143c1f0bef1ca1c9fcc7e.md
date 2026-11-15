
## Exercises

- 1. Write an error handler, `myErrorHandler()`, that emails any `E_WARNING` or `E_USER_WARNING` messages to your email address, and logs other errors in a `non_serious_errors.log` file. Test your handler with code that generates both an `E_USER_WARNING` and an `E_USER_NOTICE` error.

- 2. Create a PHPUnit test case that tests all aspects of the `Circle` class defined in `inheritance.php` in Chapter 8.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_710_0.png)

## Solutions to Exercises

## Chapter 2

### Exercise Solution

The trick here is to make a second call to date(), passing in the appropriate characters to display the current date. Here’s how you might write the script (including comments where appropriate):

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Hello</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>
<?php
// Get the current time in a readable format
$currentTime = date( 'g:i:s a' );
// Get the current date in a readable format
$currentDate = date( 'M j, Y' );
// Display greeting, time and date to the visitor
echo "Hello, world! The current time is $currentTime on $currentDate";
?>
</h1>
</body>
</html>
```

## Chapter 3

### Exercise 1 Solution

Write a PHP script such as this:

```php
<?php
$x = 5;
$x = $x + 1;
$x += 1;
$x++;
echo $x;
?>
```

### Exercise 2 Solution

Write a PHP script such as this:

```php
<?php
$x = 3;
$y = 4;
echo "Test 1 result: " . ($x == $y) . "<br />";
echo "Test 2 result: " . ($x > $y) . "<br />";
echo "Test 3 result: " . ($x <= $y) . "<br />";
echo "Test 4 result: " . ($x != $y) . "<br />";
?>
```

## Chapter 4

### Exercise 1 Solution

You could write this script many ways. The following solution creates a for loop to count the numbers, then uses the ? (ternary) operator and a switch construct to determine if each number is odd, even, or prime.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Testing the Numbers 1-10</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Testing the Numbers 1-10</h1>
<table border="1">
<tr>
<th>Number</th>
<th>Odd or Even?</th>
<th>Prime?</th>
</tr>
<?php
for ( $i = 1; $i <= 10; $i++ ) {
$oddEven = ( $i % 2 == 0 ) ? "Even" : "Odd";
switch ( $i ) {
case 2:
case 3:
case 5:
case 7:
$prime = "Yes";
break;
default:
$prime = "No";
break;
}
?>
<tr>
<td><?php echo $i?></td>
<td><?php echo $oddEven?></td>
<td><?php echo $prime?></td>
</tr>
<?php
}
?>
</table>
</body>
</html>
```

### Exercise 2 Solution

The trick here is to store two sets of pigeon coordinates representing the two pigeons, and then expand both the “flying” logic and the loop conditions to allow for both pigeons. For example, the first do . . . while loop should only exit once both pigeons are positioned more than half the map size away from the home base, and the second do...while loop should exit when both pigeons have flown home. Therefore the loop conditions and decisions within the script need to be a bit more complex:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Homing Pigeons Simulator</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
div.map { float: left; text-align: center; border: 1px solid #666;
background-color: #fcfcfc; margin: 3px; padding: 1em; }
span.home, span.pigeon { font-weight: bold; }
span.empty { color: #666; }
</style>
</head>
<body>

<?php

$mapSize = 10;

// Position the home and the pigeons
do {
    $homeX = rand ( 0, $mapSize-1 );
    $homeY = rand ( 0, $mapSize-1 );
    $pigeon1X = rand ( 0, $mapSize-1 );
    $pigeon1Y = rand ( 0, $mapSize-1 );
    $pigeon2X = rand ( 0, $mapSize-1 );
    $pigeon2Y = rand ( 0, $mapSize-1 );
} while ( ( abs($homeX - $pigeon1X) < $mapSize/2 ) && ( abs( $homeY - $pigeon1Y )
< $mapSize/2 ) || ( ( abs($homeX - $pigeon2X ) < $mapSize/2 ) && ( abs( $homeY
- $pigeon2Y ) < $mapSize/2 ) ) );

do {

// Move the pigeons closer to home
if ( $pigeon1X < $homeX )
    $pigeon1X++;
elseif ( $pigeon1X > $homeX )
    $pigeon1X--;
if ( $pigeon1Y < $homeY )
    $pigeon1Y++;
elseif ( $pigeon1Y > $homeY )
    $pigeon1Y--;

if ( $pigeon2X < $homeX )
    $pigeon2X++;
elseif ( $pigeon2X > $homeX )
    $pigeon2X--;
if ( $pigeon2Y < $homeY )
    $pigeon2Y++;
elseif ( $pigeon2Y > $homeY )
    $pigeon2Y--;

// Display the current map
echo '<div class="map" style="width: ' . $mapSize . 'em;"><pre>';
for ( $y = 0; $y < $mapSize; $y++ ) {
  for ( $x = 0; $x < $mapSize; $x++ ) {

    if ( $x == $homeX && $y == $homeY ) {
      echo '<span class="home"></span>'; // Home
    } elseif ( ( $x == $pigeon1X && $y == $pigeon1Y ) || ( $x == $pigeon2X &&
$y == $pigeon2Y ) ) {
      echo '<span class="pigeon"></span>'; // Pigeon
    } else {
      echo '<span class="empty"></span>'; // Empty square
    }
    echo ( $x != $mapSize - 1 ) ? " " : "";
  }
  echo "\n";
}
echo "</pre></div>\n";
} while ( $pigeon1X != $homeX || $pigeon1Y != $homeY ||
$pigeon2X != $homeX || $pigeon2Y != $homeY );
?>
</body>
</html>
```

## Chapter 5

### Exercise 1 Solution

Thanks to the flexibility of the `printf()` function, it's easy to format a date practically any way you want. Here's how to format the date in mm/dd/yyyy format:

```php
printf( "%02d/%02d/%d", 3, 24, 2008 ); // Displays "03/24/2008"
```

### Exercise 2 Solution

To emulate `str_pad()` in its most basic form, all you need to do is use a while loop to keep adding spaces to the right of the string until the desired length is reached. To display the results, make sure you surround the strings in HTML `<pre> ...</pre>` tags so that you can see the padding. Here's an example:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Emulating str_pad()</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Emulating str_pad()</h1>

<?php

$myString = "Hello, world!";
$desiredLength = 20;

echo "<pre>Original string: '$myString'</pre>";

while ( strlen( $myString ) < 20 ) {
    $myString .= " ";
}

echo "<pre>Padded string: '$myString'</pre>";
?>
</body>
</html>
```

## Chapter 6

### Exercise 1 Solution

The solution to this exercise is relatively simple, but it contains some important concepts:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Adding Author Names</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Adding Author Names</h1>

<?php
$authors = array( "Steinbeck", "Kafka", "Tolkien", "Dickens", "Milton", "Orwell" );

$books = array(
    array(
        "title" => "The Hobbit",
        "authorId" => 2,
        "pubYear" => 1937
    ),
    array(
        "title" => "The Grapes of Wrath",
        "authorId" => 0,
        "pubYear" => 1939
    ),
    array(
        "title" => "A Tale of Two Cities",
        "authorId" => 3,
        "pubYear" => 1859
    ),
    array(
        "title" => "Paradise Lost",
        "authorId" => 4,
        "pubYear" => 1667
    ),
    array(
        "title" => "Animal Farm",
        "authorId" => 5,
        "pubYear" => 1945
    ),
    array(
        "title" => "The Trial",
        "authorId" => 1,
        "pubYear" => 1925
    ),
);

foreach ( $books as &$book ) {
    $book["authorName"] = $authors[$book["authorId"]];
}

echo "<pre>";
print_r( $books );
echo "</pre>";
?>
</body>
</html>
