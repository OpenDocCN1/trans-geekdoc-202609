# Core PHP Programming

```
print(count($list));
print(" elements");

?>
```

# Arrays

The functions in this section operate on arrays. Some of them sort the arrays; some of them help you find and retrieve values from arrays. Chapter 5, "Arrays," discusses arrays in depth.

# array array(...)

The array function takes a list of values separated by commas and returns an array. This is especially useful for creating one-off arrays to be passed to functions. Elements will be added to the array if you use square brackets, which means they are numbered consecutively starting at zero. You may use the => operator to specify index values.

```
<?
//create an array
$myArray = array(
    "Name"=>"Leon Atkinson",
    "Profession"=>array("Programmer", "Author",
    "Residence"=>"Martinez, "California"
);
?>
```

# array array_count_values(array data)

The array_count_values function returns counts for each distinct value in the data argument. The returned array is indexed by the values of the data argument. Although the example below uses an array of numbers, array_count_values will count the appearance of elements that contain any other data type.

Figure 9-1. array_count_values.