# Part II: Working with PHP

SORT() If there is no second argument, this function will sort an array in ascending or alphabetical order.

```
void sort (array array [, int sort_flags])
```

The flags can be:

+   * SORT_NUMERIC—compare items numerically
* SORT_STRING—compare items as strings

If the array you wish to sort has only numbers, PHP will sort the array numerically; if the array contains only strings, it will be sorted alphabetically. If the array has a mix of strings and numbers, it defaults to sorting by a string.

![](bbox=[0.161, 0.386, 0.225, 0.442])

PHP4 offers many other ways to sort arrays. Please look at the manual entries for asort(),ksort(),rsort(),and usort().

# Print functions

There are a few functions that you can use to print information to the screen. Only two pop up in this book, but you should be aware of all the functions listed in this section.

# PRINT FUNCTIONS USED IN THIS BOOK

In this case the "functions" may be something of a misnomer. For instance, print() is probably better described as a language construct. In any case, you will use all of these very much like you will use functions; thus, they are included here.

PRINT As you would expect, this prints what you specify.

```
print
```

ECHO This also isn't a function, but a language construct. We use it constantly throughout this book, so at this point you probably know what it does.

```
echo
```

Keep in mind that you can mix variables and code within double quotes.

```
$var = "this string";necho "Please print $var";
```