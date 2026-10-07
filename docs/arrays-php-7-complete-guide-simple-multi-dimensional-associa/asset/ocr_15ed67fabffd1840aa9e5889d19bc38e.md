This function will ignore a defferences in the key (subscript). It uses the user supplied function to compare values. If the values match, the key and value from the first array ($first_array) are returned.

In this example, first name, address, city, and zip code are returned because they exist in both arrays, even though the keys (subscripts) vary in each array.

The user can modify the comparison shown (such as using === instead of ==) to determine what is ‘equal’. The function must return a value < 0, 0, and > 0.

```
print_r(array_uintersect($first_array, $second_array, "strcmp\));
```

A PHP compare function can be used instead of a user defined function. These could include strcmp, strcasecmp, strnatcasecmp, substrcmp, or other PHP comparison functions that return < 0, 0, or > 0 as a result.