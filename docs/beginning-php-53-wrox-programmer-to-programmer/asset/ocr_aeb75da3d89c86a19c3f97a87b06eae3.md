# Appendix A: Solutions to Exercises

```
// Initialize the minefield
for ($x=0; $x<$fieldSize; $x++) {
    $minefield[$x] = array();
    for ($y=0; $y<$fieldSize; $y++) {
        $minefield[$x][$y] = false;
    }
}

// Add the mines
for ($i=1; $i<=$numMines; $i++) {
    do {
        $mineX = rand(0, 19);
        $mineY = rand(0, 19);
    } while ($minefield[$mineX][$mineY]);
    $minefield[$mineX][$mineY] = true;
}

// Display the minefield
echo "pre";
for ($y=0; $y<$fieldSize; $y++) {
    for ($x=0; $x<$fieldSize; $x++) {
        echo ($minefield[$x][$y]) ? "**" : ". ";
    }
}
echo "</pre";
?>
</body>
</html>
```

The first script outputs a page header and some configuration variables: `$fieldSize` to hold the size of one side of the minefield grid, and `$numMines` to specify the number of mines to be placed in the field.

Next the script creates a new array, `$minefield`, and loops through all 20 elements of the array. For each element, it creates a nested array and stores it in the element, loops through the first 20 elements of the nested array, setting their values to `false`, which signifies an empty square. (This initialization process isn't strictly necessary because PHP creates arrays on-the-fly as they're needed; however, it's a good idea to initialize the minefield to default so that you know exactly what's in the minefield.)

After initializing, the script adds the mines. It does this by creating a loop that counts from 1 to the number of mines to create (`$numMines`). Within the loop, the script generates a random $x and $y$ position for the new mine, and does a `do...while` to ensure the chosen position doesn't already contain a mine. If it does, the `do...while` loop continues with a new random position until an empty spot is found. It then creates the mine by setting the appropriate array element to `true`.

682