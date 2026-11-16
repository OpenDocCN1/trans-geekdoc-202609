arguments 12, 27 and 36 are assigned to the parameters value1, value2 and value3, respectively.

To determine the largest value, we process one value at a time:

+   • Initially, we assume that value1 contains the largest value, so we assign it to the local variable max_value. Of course, it’s possible that value2 or value3 contains the actual largest value, so we still must compare each of these with max_value.

+   • The first if statement then tests value2 > max_value, and if this condition is True assigns value2 to max_value.

+   • The second if statement then tests value3 > max_value, and if this condition is True assigns value3 to max_value.

Now, max_value contains the largest value, so we return it. When control returns to the caller, the parameters value1, value2 and value3 and the variable max_value in the function’s block—which are all local variables—no longer exist.

# Python’s Built-In max and min Functions

For many common tasks, the capabilities you need already exist in Python. For example, built-in max and min functions know how to determine the largest and smallest of their two or more arguments, respectively:

lick here to view code image

```
In [6]: max('yellow', 'red', 'orange', 'blue', 'green')
Out[6]: 'yellow'

In [7]: min(15, 9, 27, 14)
Out[7]: 9
```

Each of these functions also can receive an iterable argument, such as a list or a string. Using built-in functions or functions from the Python Standard Library’s modules rather than writing your own can reduce development time and increase program reliability, portability and performance. For a list of Python’s built-in functions and modules, see

https://docs.python.org/3/library/index.html