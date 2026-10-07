Listing 2.11 displays the contents of np2array2.py that illustrates how to compute exponents of the elements in a NumPy array.

# LISTING 2.11: np2array2.py

```
import numpy as np

# -1 = "the last element in ..." (row or col)

arr1 = np.array([[1,2,3), (4,5,6), (7,8,9), (10,11,12]])
print('arr1:', arr1)
print('arr1[-1,]:', arr1[-1,:])
print('arr1[:-1]:', arr1[:-1,:])
print('arr1[-1:-1]:', arr1[-1:-1])
```

Listing 2.11 contains a NumPy array called by four print statements, each of which displays a different subrange of values in arr1. The output from launching Listing 2.11 is:

```
arr1': array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9],
       [10, 11, 12]])
arr1[-1,]:', array([10, 11, 12])
arr1[:-1]:', array([[3, 6, 9]])
arr1[-1:-1]:', array([[12]]))
```

# OTHER USEFUL NUMPY METHODS

In addition to the NumPy methods that you saw in the code samples prior to this section, the following (often intuitively-named) NumPy methods are also very useful.

+   - The method np.zeros() initializes an array with 0 values.
- The method np.ones() initializes an array with 1 values.
 The method np.empty() initializes an array with 0 values.
The method np.arange() provides a range of numbers:
The method np.shape() displays the shape of an object: