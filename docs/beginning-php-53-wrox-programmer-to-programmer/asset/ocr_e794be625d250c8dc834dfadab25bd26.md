# Chapter 6: Arrays

explode() is often useful when you need to read a line of comma- or tab-separated data from a file and convert the data to an array of values.

Other string-to-array functions include preg_split() for splitting based on regular expressions (see Chapter 18), and str_split() for splitting a string into characters (or into fixed-length chunks) — see http://www.php.net/manual/en/function.str-split.php for details.

If you want to do the opposite of explode() and glue array elements into one long string, you use — implode(). This takes two arguments: the string of characters to place between each element in the string, and the array containing the elements to place for. The following code joins the elements in $fruitArray to form one long string, $fruitString, with each element separated by a comma:

```
$fruitArray = array("apple", "banana", "strawberry", "peach");
$fruitString = implode(",", $fruitArray);

// Displays apple,pear,banana, strawberry, peach
echo $fruitString;
```

# Converting an Array to a List of Variables

The final array-manipulation tool you learn about in this chapter is list(). It constructs an easy way to put the values of an array into separate variables. Consider the following code:

```
$myBook = array("The Grapes of Wrath", "John Steinbeck", 1939);
```

```
$title = \$myBook[0];
$author = \$myBook[1];
$pubYear = \$myBook[2];
```

```
echo \$title . "<br/>"; // Displays "The Grapes of Wrath"
echo \$author . "<br/>"; // Displays "John Steinbeck"
echo \$pubYear . "<br/>"; // Displays "1939"
```

It works, but is long-winded. list() comes into play. You use it as follows:

```
$myBook = array("The Grapes of Wrath", "John Steinbeck", 1939);
list(	itle, \$author, \$pubYear) = \$myBook;
```

```
echo \$title . "<br/>"; // Displays "The Grapes of Wrath"
echo \$author . "<br/>"; // Displays "John Steinbeck"
echo \$pubYear . "<br/>"; // Displays "1939"
```

Note that list() only works with indexed arrays, and it assumes the elements are indexed consecutively starting from zero (so the first element has an index of 0, the second has an index of 1, and so on).

137