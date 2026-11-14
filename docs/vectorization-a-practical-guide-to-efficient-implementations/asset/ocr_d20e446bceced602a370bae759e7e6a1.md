```
```python
"""Implement ragged matrix using a dense matrix with
~ paddings."""
# Find the maximum length
n = np.array(n)
max_n = np.max(n)
# Construct and repeat arrange
r = np.arange(max_n)[None, :]
# Masking with broadcasting
mask = r > n[:, None]
r = np.where(mask, pad, r)
# Flatten
if flattened:
    # Flatten
    r = np.ravel(r)
    # Remove padding values
    r = np.compress(r != pad, r)

return r
```
```

+   * Line 7 ensures that the list input `n` that specifies the desired lengths of the range arrays is an `np.ndarray` which will later be used for broadcasting.
+   * Line 8 determines the maximum size of the range array.
+   * Line 10 creates the initial range array, up to the maximum array length.
+   * Line 12 creates the mask to retain values less than the size of the array specified by `n`. This is done by broadcasting the column vector of array lengths and the row vector of the range array initialized in Line 10. The resulting mask is a matrix of size `(len(n), max_n)`. Note that we are sacrificing memory spaces in exchange for subsequent opportunities for vectorization. In some worst-case scenarios, one range array may be much longer than the rest of the range arrays. In this case, the majority of the elements are padding values, or the matrix is sparse (a concept that we will discuss in Chapter 7).
+   * Line 13 uses `np.where` to replace values according to the `mask`. If the `mask` value is `True`, then we replace the value in `r` with the `pad` value, e.g. `-1`; otherwise, we retain the value inside `r`.
+   * Lines 15-19 implement the logic when we need to return a flat array. Otherwise, we will simply return the matrix with each row being a ranged array with paddings.
+   * Line 17 flattens the 2D matrix to a 1D vector.
+   * Line 19 removes the padding values.

In order to prepare for the case study in Section 5.3.3, I have also translated the above function from NumPy to Tensorflow. Notice that we need extra effort to make sure the data types are consistent before performing each operation.