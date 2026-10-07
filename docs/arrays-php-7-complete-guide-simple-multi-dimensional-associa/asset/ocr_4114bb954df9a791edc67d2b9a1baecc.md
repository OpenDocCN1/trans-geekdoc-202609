print array_reduce($numerical_values, "multiply", -5). \<br>\>; // start with a $value of -5

This call starts with an initial value of -5 (which is placed in $value). The result (as seen above) is a negative value.

print array_reduce($numerical_values, "divide", 5). \<br>"; //start with a $value of 5

This call starts with the 5 being placed into $value before each element value is divided.

array_sum — calculates the sum of values in an array

“Returns the sum of values as an integer or float.”

# Syntax:

# array_sum

# Example:

$sum = array(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

print array_sum($sum);

# Output:

55

In this example the values is the array are added together.

1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10 = 55

array_unique — removes duplicate values from an array