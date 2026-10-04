
# foreach

You can apply the same block of code to each value in a specified array with the foreach statement:

```
foreach ($arrayvalue, as $currentvalue) {
    //these lines will execute as long as there is a value in $arrayvalue
    echo $currentvalue;
    echo "<br>\n";
}
```

![](img/7b817c5b51395b5dcaba58e6a2bc6daa_633_0.png)

# PHP Functions

In this appendix, we have listed some of the functions that will be applicable to those of you using the Apache/PHP/MySQL components. PHP has numerous other functions available to you, and a complete listing can be found in the manual at the source Web site, www.php.net.

Note that some of the functions listed here have optional parameters that can be used to further specify the function (noted in brackets in our listing). In the interest of simplicity, some of those optional parameters have not been explained here, so you are encouraged to visit the source Web site for more information.

## Apache/PHP Functions

PHP uses these functions with the Apache server.

| PHP Function | Description |
|--- |--- |
| apache_child_terminate() | Stops the Apache server from running after the PHP script has been executed. |
| apache_lookup_uri(filename) | Returns information about the URI in file-name as a class. |
| apache_note(note_name [, note_value]) | Returns or sets values in the Apache notes as strings. |
| apache_request_headers() | Returns all HTTP headers as arrays. |
| apache_response_headers() | Returns all Apache response headers as arrays. |
| apache_setenv(variable, value, [bool]) | Sets an Apache subprocess environment variable. |

## Appendix C

| PHP Function | Description |
| --- | --- |
| ascii2ebcdic(string) | Converts ASCII code to EBCDIC, opposite of ebcdic2ascii. |
| ebcdic2ascii(string) | Converts EBCDIC to ASCII code, opposite of ascii2ebdic. |
| getallheaders() | Returns all HTTP request headers as arrays. |
| virtual(filename) | Performs an Apache subrequest, returns an integer. |

## Array Functions

You can perform these functions on arrays of information.

| Function | Description |
| --- | --- |
| array([...]) | Depending on the parameters, this creates an array of values. |
| array_change_key_case(array, case) | Converts the keys in the named array to either all uppercase or all lowercase. |
| array_chunk(array, size[, keep_keys]) | Splits the array into chunks based on the named parameters. |
| array_combine(keys, values) | Combines two arrays with equal number of keys and values. |
| array_count_values(array) | Counts the number of times each value appears, and returns results in array format. |
| array_diff_assoc(arrays) | Finds the values from the first array that do not appear in subsequent arrays, unlike array_diff, this takes keys into account. |
| array_diff(arrays) | Opposite of array_intersect, finds the values from the first array that do not appear in subsequent arrays, and returns results in array format. |
| array_fill(array, number, value) | Fills an array with named value, a named number of times. |
| array_filter(array[], criteria) | Returns only values that fit the named criteria. |
| array_flip(array) | Flips the array values keys and returns results in array format. |
| array_intersect_assoc(arrays) | Finds the values from the first array that do not appear in subsequent arrays, unlike array_intersect, this takes keys into account. |
| array_intersect(arrays) | Opposite of array_diff, finds the values from the first array that appear in subsequent arrays, and returns results in array format. |
| array_key_exists(array, search) | Verifies whether or not a keys exists for an array. |
| array_keys(array[, search_value]) | Will find either all the keys in the named array, or those containing the search_value, and returns results in array format. |
| array_map(criteria, array) | Applies a criteria to every element of the array. |
| array_merge(arrays) | Merges arrays together and returns results in an array. If two arrays have the same string keys, the later array will overwrite an earlier key, and if two arrays have the same keys keys the array will be appended instead of overwritten. |
| array_merge_recursive(arrays) | Similar to array_merge, but the values of the arrays are appended. |
| array_multisort(array[, mixed]) | Sorts either a multidimensional array or several arrays at a time. |
| array_pad(array, size, pad_value) | Copies the existing array and pads the named size and returns value in array format. |
| array_pop(array) | Similar to array_shift, except this deletes the last value of an array and returns what was deleted. |
| array_push(array, variables) | Similar to unshift, except this adds the named values to the end of the array. |
| array_rand(array [, number]) | Chooses a random value from the named array if “number” is specified, chooses “number” of random values from the named array. The random value that was chosen is returned (if more than one value is chosen, results in array format). |
| array_reduce(array, function) | Reduces the array to a single function based on the named parameters. |
| array_reverse(array) | Reverses the order of the values in the array, and results are returned in array format. |
| array_search(exp, array) | Searches the array for the named expression and returns the key if it exists. |
| array_shift(array) | Similar to array_pop, except this deletes the first value of an array and returns what was deleted. |
| array_slice(array, offset[, length]) | Based on the named offset, this will create a sub-array from the original array. New array that is returned will be length (if named). |
| array_splice(array, offset[, length, new_values]) | Based on the named offset, this will remove a section of the array (and replace it with new values if named). |
| array_sum(array) | Calculates the sum of the values in the named array. |
| array_unique(array) | Deletes any duplicate values in array, and returns new array. |
| array_unshift(array, variables) | Similar to array_push, except this adds the named values to the beginning of an array and returns the number of updated values in the array. |
| array_values(array) | Returns an array with the values in the named array. |
| array_walk(array, function [.parameter]) | Applies the named function (based on named parameters) to every value in the array. |
| asort(array) | Sorts the array in descending order (while maintaining the key/value relationship). |
| sort(array) | Sorts the array in ascending order (while maintaining the key/value relationship). |
| compact(variables) | Merges the variables into one array, returns results in array format. |
| count(array) | Equal to sizeof, this counts the number of values in the named array and returns the results in an integer format. |
| current(array) | Displays the values in the named array. |
| each(array) | Creates an array with the key and value of the current element of the named array, and returns results in array format. |
| end(array) | Sets the last value as the current. |
| extract(array[, type, prefix]) | Takes the named array and imports values into the symbol table. The type option directs server what to do if there is a conflict, and prefix adds a prefix to variable names. |
| in_array(value, array) | Lets you know whether or not a specified value exists in the array. |

## PHP Functions

| Function | Description |
| --- | --- |
| key (array) | Returns the key for the current value in the array |
| krsort (array) | Sorts the keys in the array in reverse order and maintains the key/value relationship |
| ksort (array) | Sorts the keys in the array and maintains the key/value relationship |
| list (variables) | Lists the named variables |
| natsort (array) | Uses "natural ordering" to sort alphanumeric strings (case-sensitive) |
| casesort (array) | Uses "natural ordering" to sort alphanumeric strings (case-insensitive) |
| next (array) | The opposite of prev, returns the value of the "next" element from the current element and returns false if the current element is the last element |
| pos (array) | Returns the value of the current element |
| prev (array) | The opposite of next, returns the value of the "before" the current element, and returns false if the current element is the first element in the array |
| range (low, high) | Creates a new array of integers between the parameters, and returns results in an array format |
| reset (array) | Sets the current element as the first element in the array, and returns its value |
| rsort (array) | The opposite of sort, this sorts the array in descending order |
| shuffle (array) | Shuffles the array in random order |
| sizeof (array) | Equal to count, returns the number of values in the array |
| sort (array) | The opposite of rsort, this sorts the array in ascending order |
| usort (array, function) | Using the named function, this sorts the array accordingly and maintains the key /value relationship |
| uksort (array, function) | Using the named function, this sorts the array by key |
| usort (array, function) | Using the named function, this sorts the array by value |
