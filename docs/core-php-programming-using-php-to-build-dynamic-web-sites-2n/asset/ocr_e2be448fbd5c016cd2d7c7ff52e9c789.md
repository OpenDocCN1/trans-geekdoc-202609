# Core PHP Programming

# The do...while Statement

You can rely the decision to continue executing a loop until the end by using a do...while statement. Listing 3.8 retools Listing 3.7. You will notice a difference unless you run the script on a Friday. On the Fridays it will print nothing in its list of days. The new version will put Friday in the list because the body of the loop is executed before currentDate is tested. Switching to a do...while loop, the loop lists the days until next Friday.

# Listing 3.8 Using do...while to Print Day Names

```
<?
/*
** get the current date in number of seconds
*/
$currentDate = time();
/*
** print some text explaining the output
*/
print("Days left before next Friday:\n");
print("<OL>\n\ndo {
    /*
** print day name
*/
    print("<LI>" . date("l", $currentDate) . "\n");
    /*
** add 24 hours to currentDate
*/
    $currentDate += (60 * 60 * 24);
}
while (date("l", $currentDate) != "Friday");
print("</OL>\n");
?>
```

# The for Statement

Strictly speaking, the for loop is unnecessary. Any for loop can be implemented as easily as a while loop. What for offers no new functionality, but a better structure for building the most common loops. Many loops involve incrementing a counter variable every time the loop, iterating until maximum is reached.

Imagine that you wanted to step through the numbers 1 through 10. Using while, you would first set a variable to be 1. Then you would make a while loop that tests if your counter is less or equal to 10. Inside the code block you would increment your counter, making sure you do this as the last statement in the block.

IT-SC book