# Merging Arrays

array_combine - creates an array by using one array for keys and another for its values

“Creates an array using the values from the keys array as keys and the values from the values array as the corresponding values.”

Syntax:

```
array_combine ( array $keys , array $values )
```

Example:

```
$first_names = array('Pete’, ‘Sally’, ‘Fred’);
$last_names = array('Smith’, ‘Parisi’, ‘Jones’);
$names = array_combine($last_names,

print_r($names);
```

Output:

Array

```
(
[Smith] => Pete
[Parisi] => Sally
[Parisi] => Sally
)
```

This example uses the $last_names array to populate the keys and the $first_names array to populate the values.

array_intersect_assoc — computes the intersection of arrays with additional index check

“array_intersect_assoc() returns an array containing all the values of array1 that are present in all arrays. Note that the keys are used in the comparison unlike in array_intersect().”

This function compares arrays and returns what is common in both arrays. The index and the value must both be the same.

Syntax: