For a tuple of integers, these functions return a multidimensional array with the specified dimensions. You can specify the array's element type with the zeros and ones function's dtype keyword argument:

lick here to view code image

```
In [3]: np.ones((2, 4), dtype=int)
Out[3]:
array([[1, 1, 1, 1],
       [1, 1, 1, 1]])
```

The array returned by full contains elements with the second argument's value and type:

lick here to view code image

```
In [4]: np.full((3, 5), 13)
Out[4]:
array([[13, 13, 13, 13, 13],
       [13, 13, 13, 13, 13],
       [13, 13, 13, 13, 13]])
```

# 7.5 CREATING ARRAYS FROM RANGES

NumPy provides optimized functions for creating arrays from ranges. We focus on simple evenly spaced integer and floating-point ranges, but NumPy also supports nonlinear ranges. ¹

¹ https://docs.scipy.org/doc/numpy/reference/routines.array-creation.html.

# Creating Integer Ranges with arange

Let's use NumPy's arange function to create integer ranges—similar to using built-in function range. In each case, arange first determines the resulting array's number of elements, allocates the memory, then stores the specified range of values in the array:

lick here to view code image

```
In [1]: import numpy as np
```