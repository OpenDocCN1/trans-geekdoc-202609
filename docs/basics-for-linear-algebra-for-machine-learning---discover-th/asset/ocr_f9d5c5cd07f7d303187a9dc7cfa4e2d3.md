An invisible diagonal line can be drawn through the matrix from top left to bottom right on which the matrix can be flipped to give the transpose.

A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \\ 5 & 6 \end{pmatrix} (11.2)

A^T = \begin{pmatrix} 1 & 3 & 5 \\ 2 & 4 & 6 \end{pmatrix} (11.3)

The operation has no effect if the matrix is symmetrical, e.g. has the same number of columns and rows and the same values at the same locations on both sides of the invisible diagonal line.

The columns of $A^T$ are the rows of $A$.

> — Page 109, Introduction to Linear Algebra, Fifth Edition, 2016.

We can transpose a matrix in NumPy by calling the T attribute.

```
# transpose matrix
from numpy import array
# define matrix
A = array([
    [1, 2],
    [3, 4],
    [5, 6]])
print(A)
# calculate transpose
C = A.T
print(C)
```

Listing 11.1: Example of creating a transpose of a matrix.

Running the example first prints the matrix as it is defined, then the transposed version.

```
[[1 2]
 [3 4]
 [5 6]]
[[1 3 5]
 [2 4 6]]
```

Listing 11.2: Sample output from creating a transpose of a matrix.

The transpose operation provides a short notation used as an element in many matrix operations.

# 11.3 Inverse

Matrix inversion is a process that finds another matrix that when multiplied with the matrix, results in an identity matrix. Given a matrix A, find matrix B, such that AB = I^n or BA = I^n.

AB = BA = I^n (11.4)