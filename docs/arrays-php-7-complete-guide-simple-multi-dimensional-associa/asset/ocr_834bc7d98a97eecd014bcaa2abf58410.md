# Searching Arrays

array_count_values — counts all the values of an array

“Returns an array using the values of array as keys and their frequency in array as values.”

Syntax:

```
array array_count_values ( array $array )
```

Example:

```
$silly_array = array("hey", "hey", "hey", "what", "is", "this", "unsure", "unset");
print_r(array_count_values($silly_array));
```

Output:

Array

```
(
[hey] => 3
[what] => 1
[is] => 1
[this] => 1
[unsure] => 2
)
```

This example counts the frequency of the values in $silly_array. It creates an array that uses the value as an index and the frequency as the value.

array_column - returns the values from a single column in the input array.

“array_column() returns the values from a single column of the input, identified by the column_key. Optionally, an index_key may be provided to index the values in the returned array by the values from the index_key column of the input.”

Syntax:

```
array array_column ( array $input, mixed $column_key [ , mixed $index_key = null ] )
```

Example:

```
$customer_record = array (
```