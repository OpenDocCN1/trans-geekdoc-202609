When you pass a tuple to a function, attempting to modify the tuple’s immutable elements results in a TypeError:

# lick here to view code image

```
In [5]: numbers_tuple = (10, 20, 30)

In [6]: numbers_tuple
Out[6]: (10, 20, 30)

In [7]: modify_elements(numbers_tuple)
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
ipython-input-7-9339741cd595> in <module>()
----> 1 modify_elements(numbers_tuple)

<ipython-input-1-27acb8f8f44c> in modify_elements(items)
      2 """Multiplies all element values in items by 2."""
      3 for i in range(len(items)):
----> 4     items[i] *= 2
      5 
      6 

TypeError: 'tuple' object does not support item assignment
```

Recall that tuples may contain mutable objects, such as lists. Those objects still can be modified when a tuple is passed to a function.

# A Note Regarding Tracebacks

The previous traceback shows the two snippets that led to the TypeError. The first is snippet [7]’s function call. The second is snippet [1]’s function definition. Line numbers precede each snippet’s code. We’ve demonstrated mostly single-line snippets. When an exception occurs in such a snippet, it’s always preceded by ---> 1, indicating that line 1 (the snippet’s only line) caused the exception. Multiline snippets like the definition of modify_elements show consecutive line numbers starting at 1. The notation ---> 4 above indicates that the exception occurred in line 4 of modify_elements. No matter how long the traceback is, the last line of code with ---> caused the exception.

# 5.8 SORTING LISTS

Sorting enables you to arrange data either in ascending or descending order.