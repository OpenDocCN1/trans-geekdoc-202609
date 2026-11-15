> **Note**
> The same rules apply to this function as those for comparison operators. With string comparisons, the ASCII position of the character is decisive; that is, a distinction is made between upper- and lowercase. With Strict, it is a check for absolute equality or inequality.

# 8.4 Transform

In the extensive universe of array helper functions, we first show you the most important ones for transforming, splitting, and joining arrays. You will also learn how to convert variables into arrays and vice versa.

> **Note**
> Most array auxiliary functions can also be more or less easily replicated with the normal array functions. However, there is hardly anyone who wants to do this work.

# 8.4.1 Adding and Removing

You can imagine an array like a stack. The first element created is the first element in the stack; the last element added is the last.

Let's take a look at the four functions that PHP offers for this:

+   - array_pop(Array) removes the last element of the array and returns it. If there is no element, then the function returns zero.
+   - array_push(Array, Value, Value ...) adds the value or values to the end of the array. You automatically receive the highest indices. The size of the array is increased by the specified number of elements. The total number of elements is returned.

+   - array_shift(Array) removes the first element of the array and changes the numerical index of all other elements (associative indices remain unaffected). In the following example, Saturday disappears and Sunday has the index 0:

```
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
array_shift($days);
```

The function returns the removed element, or zero in the case of an empty array.

+   - array_unshift(Array, Value, Value ...) adds new values to the beginning of the array and returns the number of elements the array has afterward.