When your program reaches this point, it will display the value of the variable and then stop. Of course, the fact that the variable is blank means that you won't see anything, so you might prefer:

```
echo "XYZ" . $room[1] ;
exit();
```

You can now look on the generated web page for XYZ, and you'll know where to expect to see the room number displayed alongside.

And one final addition, which will also help. Change the code to:

```
echo "XYZ" . $room[1]; #debug
exit();                #debug
```

This way, once the program is working properly, you can easily search for the lines with the comment in order to remove them.

If all this effort doesn't bring the bug out of the woodwork, then move your debug code further up the file, to just after the place where $room[1] is initially defined. Hopefully, its value at that point should be correct. So somewhere between those two points it's being changed. All that remains is to position your debug code, in turn, just after every line that changes (or which you suspect might change) the value of $room[1]. Chances are, the problem will be down to a simple mis-spelling, eg rooms rather than room, or "1" rather than 1.

If you want to output the values of an entire array rather than a single variable, you don't have to write a for... loop to do it. PHP has such a feature built in. Assuming there's a problem with one or more elements of the $rooms array, and you want to see the whole array rather than just element 1, use var_dump. The following code:

```
<?php
$rooms[1] = "ABC";
$rooms[2] = "DEF";
$rooms[3] = "GHI";

echo "<pre>";
var_dump($rooms);
echo "</pre>";
?>
```

Produces the following output: