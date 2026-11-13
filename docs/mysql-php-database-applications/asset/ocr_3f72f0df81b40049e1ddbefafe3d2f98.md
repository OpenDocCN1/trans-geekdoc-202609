Keep in mind that certain functions will have optional arguments and that a few will take no arguments at all. Take the `substr()` function, for example. This function takes a large string and extracts a smaller string from it by using index numbers that are provided as arguments. The letters in the original (larger) string are numbered (starting with 0 at the leftmost end), and the arguments refer to these numbers. To get everything from the second character in a string on, you would use the following code:

```
$str = substr ($str_var,1);
```

However, the `substr()` function also has an optional third argument, which you can use to limit the size of the string that it returns. A positive value counts forward from the position given in the second argument. A negative value counts backwards from the end of the string. So to get everything from the second character to the next-to-last character in a string, you would use the following code:

```
$new_str = substr ($str_var,1,-1);
```

We'll point out optional arguments as we move through the functions. The details of working with `substr()` will be covered later in the chapter.

On a few occasions a function will take no arguments at all. A good example is `time()`, which returns the current Unix timestamp. When this is the case, in the description of the function in the documentation, the keyword `void` will be used to explicitly tell you that the function takes no arguments:

```
int time ( void)
```

# # Return values

When using a function, you should always be aware of what the function will return – specifically, what variable type. In the previous case, `str_replace()` returns a string. What you do with this string is your business. You could assign it to a variable or print it out, or do whatever else seems appropriate. The following code echoes its output string:

```
//assign to variable
$new_str = str_replace("Jay", "John", $str);
//print directly
echo str_replace("Jay", "John", $str);
```

Note that functions can return arrays, integers, doubles (floating-point numbers), objects, floats (long floating-point values), or (sometimes) Boolean values. In Chapter 5 you saw a good example of a function that returns a Boolean value (that is, TRUE or FALSE). If you want to determine whether a variable is an array you can use the `is_array()` function, as in the following.