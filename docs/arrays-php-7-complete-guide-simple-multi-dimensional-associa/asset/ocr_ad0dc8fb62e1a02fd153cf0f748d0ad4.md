The function will apply changes to each element, as shown in the function passed (add_info), to the array passed to produce a new array with the keys intact. In this example This value is appended to the value of each position in the array to produce a new array.

array_product — calculates the product of values in an array

“array_product() returns the product of values in an array.”

Syntax:

number array_product ( array $array )

Example:

```
$product = array(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```

```
print array_product($product);
```

Output:

3628800

In this example will multiply:

```
1 x 2 x 3 x 4 x 5 x 6 x 7 x 8 x 9 x 10 = 362880
```

array_rand — Pick one or more random entries out of an array

“Picks one or more random entries out of an array, and returns the key (or keys) of the random entries.”

Syntax: