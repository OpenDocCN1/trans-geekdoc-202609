
Now look at the switch statement. The first case compares the $mine variable to the one called $one. The second case compares the $mine variable to the one called $two. Then I’ve provided a default case. And when you open this .php file in a browser, voilà! The comparison succeeds, and you see the word one appear in your browser. Amazing. I’m going to go tell my friends about this; C++, for example, doesn’t let you use strings in a switch statement.

## Breaking and Continuing Your Loops

If you’re inside a loop, whether it’s a for loop, a while loop, or a do-while loop, you may occasionally need to include a special situation where the loop ends early. A realistic example of this is if you’re writing a program that’s looking up data in a database and you encounter an error.

You can abort a loop early by using a break statement. Here’s a rather contrived example:

```php
<?php
$number = 0;
while ($number < 10) {
    print "$number<br>\n";
    if ($number == 5) {
        break;
    }
    $number++;
}
?>
```

Instead of looking up data in a database and seeing if the lookup failed, I just test if the number is 5. But you can get the idea from this code: If the number is 5, I call the break statement, which breaks me out of the while loop prematurely. Here’s the HTML output:

```
0<br>
1<br>
2<br>
3<br>
4<br>
5<br>
```

You also may need to stop the current iteration but continue executing the loop with the next iteration. To do that, use the continue keyword. Here’s an example:

```php
<?php
$number = 0;
while ($number < 10) {
    if ($number == 5) {
        $number += 2;
        continue;
    }
    print "$number<br>\n";
    $number++;
}
?>
```

In this example, if the number is 5, I want to skip over the print statement. Further, I want to add 2 to the current number. And so I do a special situation for 5 in the form of an if statement, and then I do a continue to skip over the rest of the code and go right to the next iteration. In the next iteration, the value of $number is 7, because I added 2 to $number. Of course, you can also implement this with an else statement and no continue, like in the following example:

```php
<?php
$number = 0;
while ($number < 10) {
    if ($number == 5) {
        $number += 2;
    } else {
        print "$number<br>\n";
        $number++;
    }
}
?>
```

It's up to you whether you want to use a continue statement or an if-else block. However, I find that often the continue statement is more convenient when if-else blocks make for messier, more complex code.

## Building HTML Tables with Loops

One cool thing you can do with some of these control structures is to build HTML tables. Remember that PHP is a scripting language for creating dynamic HTML pages.

Typically, you want to read your data from a database (such as MySQL) and then display the data in the form of a table on an HTML page. However, to keep things simple, in this example I’ll skip the MySQL stuff and just use some hardcoded data that I put in an array. (For more on arrays, see Book V, Chapter 5; for more on MySQL, see Book VI.) Here goes:

```php
<html><title>Houses For Sale</title>
<body>
The following houses are for sale. They are all next to each
other.
Please make your decision fast, because they are going
quickly.
<table border="1">
<tr>
<td><b>Address</b></td>
<td><b>Hauntings</b></td>
<td><b>Termite Count</b></td>
</tr>
<?php
// Initialize the data
$Houses[1]['address'] = '123 Main St.';
$Houses[1]['hauntings'] = 5;
$Houses[1]['termites'] = 6920;
$Houses[2]['address'] = '125 Main St.';
$Houses[2]['hauntings'] = 10;
$Houses[2]['termites'] = 9563225;
$Houses[3]['address'] = '124 Main St.';
$Houses[3]['hauntings'] = 2;
$Houses[3]['termites'] = 4279;
$fields =
array(1=>'address',2=>'hauntings',3=>'termites');
for ($housenum=1; $housenum<=3; $housenum++) {
    print "<tr>\n";
    for ($fieldnum=1; $fieldnum<=3; $fieldnum++) {
        $fieldname = $fields[$fieldnum];
        print "<td>".$Houses[$housenum][$fieldname]."</td>\n";
    }
    print "</tr>\n";
}
?>
</table>
</body></html>
```

This code is pretty self-explanatory. You can see the HTML (before the PHP code) that sets up the table with the <table> tag. Then the code includes some HTML tags that create a row in the table. Next comes the PHP code, which traverses through a two-dimensional array, using two for loops, an outer one and an inner one. The outer loop traverses through the houses; the inner loop moves through the data for the particular house.

When you open this .php file in a browser, you see a table containing the data, as shown in Figure 4-1. (Hmmm . . . looks like the house in the middle is the source of the trouble.)

![](img/3f967ab8a8fddc723173059f56621648_429_0.png)

Figure 4-1:
You can use PHP to build a table. But I don't recommend buying the houses.

## Chapter 5: Arrays and Functions

### In This Chapter

- Gathering data into arrays
- Looping through arrays
- Copying arrays
- Working with multidimensional arrays
- Writing your own functions

Like most reputable languages, PHP allows you to store large amounts of data inside arrays and to divide up your programs into functions. PHP implements these two features a little differently from other languages, which provides you with some extra power over what some other languages offer. In this chapter, I show you how you can make arrays and functions work not just for you, but also with you.

### Gathering Data into Arrays

An array is a variable that contains multiple storage slots, as opposed to a simple variable (sometimes called a scalar), which stores only a single data item. (If you want to find out more about arrays, I provide a quick introduction in Book III, Chapter 4.)

PHP arrays are a little different from those in some other languages in that you can index the array based on any value, not just a number starting at 0. For example, if you want an array to store the names of the lead actors in various movies, you can use the movie name as the index of the array. Here’s an example:

```php
<?php
$movies = array(
    "The Matrix" => "Keanu Reeves",
    "Raiders of the Lost Ark" => "Harrison Ford",
    "Forrest Gump" => "Tom Hanks",
    "Men in Black" => "Will Smith"
);
print $movies["The Matrix"];
?>
```

This example uses the language construct array() to create an array and store it in the $movies variable. The first array item's index is The Matrix, and its value is Keanu Reeves. The second array item's index is Raiders of the Lost Ark, and its value is Harrison Ford. After declaring the array, I print to the HTML the value in the array's first item. Notice that I reference it by its index, which is The Matrix.

You're not limited to using just strings for the indexes; the indexes can be either strings or integers. If you want your indexes to be integers — in which case, the first item in the array has index 0, the next one has index 1, the next has index 2, and so on — you can leave out the indexes in the declaration:

```php
<?php
$names = array("Suzy", "Carousel", "Jennifer", "Jeff");
print $names[1];
?>
```

In this example, the first item — the one with the value Suzy — has index 0. The second has index 1, and so on. I then print to the HTML the item with index 1, which has the value Carousel.

![](img/3f967ab8a8fddc723173059f56621648_431_0.png)

If you attempt to create an array whose indexes are floating point numbers, you will find that it almost works. At first glance, it may appear that the process is working fine. However, in reality, the PHP processor truncates any float indexes to integers. Thus, $myarray[1.5] is the same as $myarray[1].

PHP lets you intermix specifying and not specifying an index when you initialize an array. Doing so isn't the best programming style, but you might have a situation where you need it. Look at the following example:

```php
<?php
$nums = array(
  1 => 2,  2 => 4,
  5 => 10, 6 => 12,
  14, 16, 18
);
print "1,{$nums[1]}<br>\n";
print "2,{$nums[2]}<br>\n";
print "3,{$nums[3]}<br>\n";
print "4,{$nums[4]}<br>\n";
print "5,{$nums[5]}<br>\n";
print "6,{$nums[6]}<br>\n";
print "7,{$nums[7]}<br>\n";
print "8,{$nums[8]}<br>\n";
print "9,{$nums[9]}<br>\n";
?>
