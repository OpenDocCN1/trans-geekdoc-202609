
Once the array is flipped, these entries will look like this:

```
[$copy] => (c)
[&reg;] => (r)
```

Then strtr() replaces each value to its key. So in the end this code will make sure that any character that needs to be represented by an HTML entity will be.

Note that if an array has two identical values before being flipped, only one can survive in the flipped array. You can't have two array elements with same key. If there is a conflict the element in the right-most position will be maintained.

### ARRAY_MERGE()

As you can probably guess, this function merges, or concatenates, two or more arrays.

```
array array_merge (array array1, array array2 [, array ...])
```

If any of the arrays contain the same associative keys, the elements in the right-most array will be preserved.

### ARRAY_SPLICE()

This function takes the array indicated in the first argument and removes all elements following the offset specified in the second argument. It can then insert additional elements.

```
array array_splice (array input, int offset [, int length [, array replacement]])
```

If the offset is a positive number, the elements will be counted from the left; if the offset is a negative number, all items to the left of the indicated number will be deleted. The optional third argument can indicate how many elements after the offset you wish to delete. For example:

```
$knicks_array = array ("Childs", "Sprewell", "Ewing",
"Johnson","Houston");
array_splice($knicks_array, 2,1);
```

will remove elements starting at offset 2 and remove only one element. So “Ewing” will be deleted from this array. array_splice() also gives you the ability replace the deleted portion with another array. So, to account for trades, you can do this.

```
$knicks_array = array ("Childs", "Sprewell", "Ewing",
"Johnson","Houston");
$new_knicks = array ( "Longley","Rice");

array_splice($knicks_array, 2,1,$new_knicks);
```

Following this code, $knicks_array would contain six elements: Childs, Sprewell, Longley, Rice, Johnson, Houston.

Note that the value returned by this function is an array of the deleted items. In the code that follows, $traded_knicks will be an array with one element, “Ewing”.

```
$traded_knicks = array_splice($knicks_array, 2,1);
```

### COUNT()

This returns the number of elements in an array, and is frequently used with loops.

```
int count (mixed var)
```

For example:

```
$array = array(1,2,3,4,5);
for($i=0; $i<count($array); $i++)
{
    echo $array[$i] . "<br>\n";
}
```

Note that sizeof() is a synonym for count().

## ARRAY FUNCTIONS NOT USED IN THIS BOOK

Again, there are many great array functions in PHP 4. Here are some of the highlights (from my point of view, anyway).

### ARRAY_COUNT_VALUES()

This nifty function will return an associative array, the keys of which will be all of the unique values within the array.

```
array array_count_values (array input)
```

The values of the resulting array will be an integer representing the number of times the value appears within the array.

```
$array = array("yes","no","no","yes","why");
$result = array_count_values($array);
```

After this $result will contain:

```
[yes] => 2, [no] => 2, [why] => 1
```

### ARRAY_DIFF()

If given two arrays, this function will return all of the elements that are in the first array, but not in the second array.

```
array array_diff (array array1, array array2 [, array ...])
```

For example:

```
$knicks = array("sprewell", "houston", "Ewing", "childs");
$all_stars = array("mourning", "houston", "carter", "davis", "miller");
$non_knick_allstars = array_diff($all_stars, $knicks);
```

Note that in the returned array, the elements maintain the keys they had in the array from which they were taken. So after running this code, $non_knick_allstars will contain the following:

```
[0] => mourning, [2] => carter, [3] => davis, [4] => miller
```

Additional arrays can be added to the function. For example,

```
$knicks = array("sprewell", "houston", "Ewing", "childs");
$all_stars = array("mourning", "houston", "carter", "davis", "miller");
$non_knick_allstars = array_diff($all_stars, $knicks, array("carter"));
```

Given this, “carter” will also be removed from the returned array.

### ARRAY_INTERSECT()

This returns the array elements that two (or more) arrays have in common.

```
array array_intersect (array array1, array array2 [, array ...])
```

### ARRAY_POP()

The array_pop() function returns the last element in an array, and removes that element from the original array.

```
mixed array_pop (array array)
```

For example, $array = array(1,2,3,4,5);
$int = array_pop($array);

After this runs, $array will contain (1,2,3,4), and $int will contain 5.

### ARRAY_PUSH()

This function will add elements to the array indicated in the first argument.

```
array_push (array array, mixed var [, mixed ...])
```

The additional arguments will be values you wish to tack onto the array.

```
$array = array (1,2,3);
array_push($array,4,5,6);
```

The resulting array will contain 1,2,3,4,5,6.

### ARRAY_RAND()

This function will pick one or more random elements from an array.

```
mixed array_rand (array input [, int num_req])
```

Note that it does not pick the value; rather it picks the key of the chosen elements. For instance, given the following,

```
srand ((double) microtime() * 1000000);
$names = array("jay", "brad", "john", "Jeff");
$rand_keys = array_rand ($names, 2);
```

$rand_keys will contain an array with two numbers. To get the values from the $names array, you will first need to get to the key value extracted by array_rand(), and so you will need to use something like this:

```
echo $names[$rand_keys[0]];
```

![](img/de0823012275cf4ceebdb822a56e6b71_179_0.png)

Seed the random number generator only once per script.

### SHUFFLE()

This function randomizes the elements in an array.

```
void shuffle (array array)
```

You will need to seed the random number generator before using it. For instance:

```
srand ((double) microtime() * 1000000);
shuffle ($array);
```

### IN_ARRAY()

This very convenient function will search all of the values of an array, and return TRUE if the value in the first argument is found in the array in the second argument.

```
bool in_array (mixed needle, array haystack)
```

You might be wondering if there is an in_keys() function. Actually, there is no need for such a function, because the following will serve the same purpose.

```
if(isset($array["key"]))
```

### SORT()

If there is no second argument, this function will sort an array in ascending or alphabetical order.

```
void sort (array array [, int sort_flags])
```

The flags can be:

- SORT_NUMERIC — compare items numerically
- SORT_STRING — compare items as strings

If the array you wish to sort has only numbers, PHP will sort the array numerically; if the array contains only strings, it will be sorted alphabetically. If the array has a mix of strings and numbers, it defaults to sorting by a string.

![](img/de0823012275cf4ceebdb822a56e6b71_180_0.png)

> PHP4 offers many other ways to sort arrays. Please look at the manual entries for asort(), ksort(), rsort(), and usort().

## Print functions

There are a few functions that you can use to print information to the screen. Only two pop up in this book, but you should be aware of all the functions listed in this section.

## PRINT FUNCTIONS USED IN THIS BOOK

In this case the word “functions” may be something of a misnomer. For instance, print() is probably better described as a language construct. In any case, you will use all of these very much like you will use functions; thus, they are included here.

**PRINT** As you would expect, this prints what you specify.

```
print
```

**ECHO** This also isn't a function, but a language construct. We use it constantly throughout this book, so at this point you probably know what it does.

```
echo
```

Keep in mind that you can mix variables and code within double quotes.

```
$var = "this string";
echo "Please print $var";
```
