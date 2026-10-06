# Chapter 4: Decisions and Loops

The built-in abs () function determines the absolute value of a number. For example, abs (3) is 3, and
ab (-3) is also 3.

The next loop in the script is also a do...while loop, which contains the main body of the code.
The first code inside the loop uses decision-making to simulate the pigeon's homing instinct. It simply checks
to if the x coordinate of the pigeon is greater or less than the x coordinate of the home square, and
adjusts the pigeon's x coordinate appropriately. The y coordinate is adjusted in the same way:

// Move the pigeon closer to home

```
if ($pigeonX < $homeX)
$pigeonX++;
else if ($pigeonX > $homeX)
$pigeonX--;

if ($pigeonY < $homeY)
$pigeonY++;
else if ($pigeonY > $homeY)
$pigeonY--;
```

Note that if the x or y coordinate of the pigeon matches the corresponding home coordinate, there's no
adjust the pigeon's coordinate. Here is no else code branch.

The last section of code within the loop is concerned with displaying the current map. This code itself
prises two nested loops for move through all the x and y coordinates of the map. For each
s square, the code displays a + symbol if the square matches the coordinates of the home
position, and a % symbol if the square matches the coordinates. Otherwise, it displays a ().
After each square, it adds a space character (unless it's the last square on row):

// Display the current map

```
echo <div class="map" style="width: ' . $mapSize . 'em;"><pre>';

for ($y = 0; $y < $mapSize; $y++) {
    for ($x = 0; $x < $mapSize; $x++) {
        if ($x == $homeX && $y == $homeY) {
            echo '<span class="home">+</span></span>'; // Home
        } elseif ($x == $pigeonX && $y == $pigeonY) {
            echo '<span class="pigeon">%</span></span>'; // Pigeon
        } else {
            echo '<span class="empty">.</span></span>'; // Empty square
        }
        echo ($x == $mapSize - 1) ? " " : "";
    }
}

echo "\n";

echo "</div>\n";
```