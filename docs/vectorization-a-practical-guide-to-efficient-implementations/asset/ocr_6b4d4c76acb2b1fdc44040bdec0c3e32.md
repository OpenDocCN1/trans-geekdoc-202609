# Figure 7.7 lil_matrix example.

![](bbox=[0.604, 0.112, 0.888, 0.278])

```
```python
from scipy.sparse import lil_matrix
A = lil_matrix([
    [0, 0, 0, 2, 0],
    [1, 0, 0, 0, 0],
    [0, 0, 1, 0, 0],
    [0, 2, 0, 0, 0],
    [0, 0, 2, 1, 2],
])
```
```

The data structures are

```
```python
A.rows = [ [3], [0], [2], [1], [2,3,4] ]
A.data = [ [2], [1], [1], [2], [2,1,2] ]
```
```

lil_matrix offers a very simple and flexible interface to slice data. A key advantage of using lil format to slice the matrix is that it allows row and column indices to be broadcasted.

Suppose we have an array of row indices rows and column indices cols, to slice out a subset of the sparse matrix for every rows and cols, we can do

```
```python
rows = rows[:, np.newaxis] # column vector
cols = cols[np.newaxis, :] # row vector
mat_lil[rows, cols] += np.ones(
    (rows.size, cols.size)
) # add one to these slices
mat_lil[rows, cols] = ... # assigning these subset of slices
```
```

For very large matrices, however, it is recommended to construct them using coo_matrix.