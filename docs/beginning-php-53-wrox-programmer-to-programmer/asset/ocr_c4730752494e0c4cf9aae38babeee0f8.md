```
for ( $y = 0; $y < $mapSize; $y++) {
    for ( $x = 0; $x < $mapSize; $x++) {
        if ( $x == $homeX && $y == $homeY ) {
            echo '<span class="home"></span>'; // Home
        } else if ( $x == $pigeon1X && $y == $pigeon1Y ) || ( $x == $pigeon2X && $y == $pigeon2Y ) {
            echo '<span class="pigeon"></span>'; // Pigeon
        } else {
            echo '<span class="empty"></span>'; // Empty space
        }
        echo ( $x != $mapSize - 1 ) ? " *" : "";
    }
    echo "\n";
}
echo "</pre></div>\n";

while ( $pigeon1X != $homeX || $pigeon1Y != $homeY || $pigeon2X != $homeX || $pigeon2Y != $homeY );
?>

<body>
</html>
```

# Chapter 5

# Exercise 1 Solution

Thanks to the flexibility of the printf() function, it's easy to format a date practically any way you want. Here's how to format the date in mm/dd/yyyy format:

```
printf("%02d/%02d/%02d", 3, 24, 2008 ); // Displays "03/24/2008*"
```