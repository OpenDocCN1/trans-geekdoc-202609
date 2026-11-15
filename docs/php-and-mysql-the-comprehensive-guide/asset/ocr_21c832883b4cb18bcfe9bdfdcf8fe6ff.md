Or you can save the array in a variable beforehand:

```
$ibw_stockprice = array("1.1.2020" => 232, "1.1.2025" => 254);
$stockprices = array("IBW" => $ibw_stockprice);
```

To access the elements of the associative array, you can then use the syntax with square brackets:

```
$stockpries["IBW"]["1.1.2020"]
```

For example, the last line accesses the price of IBW stock on January 1, 2020. This value prints 232. Multidimensional arrays are walked through recursively by some PHP functions, such as array_walk_recursive(). In this case, recursive means that all subordinate arrays and their elements are also traversed.

# ## 8.2 Arrays and Loops

Square brackets can be used to access individual elements of an array. In practice, however, the most common task is to iterate through an array. This iteration is usually achieved using loops. However, there are also some functions that can be used as alternatives.

Before we get to the concrete solutions, a few thoughts on arrays in PHP. As you have already read, arrays with a numerical index are actually associative. Internally, the index and value are stored in the order in which they are added to the array. We will deal with this in the output sequence in a moment.

# ### 8.2.1 "for"

The for loop simply runs through a numeric array in the order of the indices. To do this, you must use the count(Array) function to determine how many elements the array contains. Then send for on its journey (see Figure 8.6).

```
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
for ($i = 0; $i < count($days); $i++) {
    print $days[$i] . "<br />";
}
?>
```

# Listing 8.4 The "for" Loop for an Array ("array_for.php")

The for loop works quite well, but only under two conditions:

+   - The array has no associative indices, only numerical indices.