# Figure 7.4 csr_matrix example.

![](bbox=[0.12, 0.11, 0.4, 0.28])

where

+   - data is a row-wise flattened array
+   - indices are indices of the columns
+   - indptr is a pointer for data and indices, an array of cumulative length of rows, with the max of its element as the length of the data or indices

# 7.1.4 Block Sparse Row Matrix (bsr_matrix)

bsr_matrix has all the advantages of csr_matrix. In addition, when data is dense at certain regions of the matrix, arithmetic operations can be even more efficient than csr_matrix. This dense region of the matrix is called a “block,” which is a dense matrix of arbitrary size (R, C). To efficiently store the sparse matrix in the bsr format, it is required that the block size are all the same and are divisible by the number of rows and columns, i.e. if the block size is (R, C) and matrix size is (M, N), then it is required that M % R = 0 and N % C = 0.

The bsr sparse matrix representation has the following structure:

+   - data: A K x R x C matrix, where K is the number of blocks, and R and C are the dimensions of each block
+   - indices: Length K array, column indices of the blocks
+   - indptr: Length K + 1 array, pointers of block data and indices

For the example matrix shown in Figure 7.5, the bsr representation can be constructed as

```
from scipy.sparse import bsr_matrix
A = bsr_matrix((
    [0, 0, 0, 0, 3, 3],
    [0, 0, 0, 0, 3, 3],
    [1, 1, 0, 0, 0, 0],
    [1, 1, 0, 0, 0, 0],
    [0, 0, 2, 2, 0, 0],
    [0, 0, 2, 2, 0, 0]
))
```