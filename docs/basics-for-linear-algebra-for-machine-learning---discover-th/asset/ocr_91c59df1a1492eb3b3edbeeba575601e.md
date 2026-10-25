— Page 115, No Bullshit Guide To Linear Algebra, 2017.

The notation for a matrix is often an uppercase letter, such as $A$, and entries are referred to by their two-dimensional subscript of row $(i)$ and column $(j)$, such as $a_{i,j}$. For example, we can define a 3-row, 2-column matrix:

$A = ((a_{1,1}, a_{1,2}), (a_{2,1}, a_{2,2}), (a_{3,1}, a_{3,2}))$

It is more common to see matrices defined using a horizontal notation.

$A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \\ a_{3,1} & a_{3,2} \end{pmatrix}$

A likely first place you may encounter a matrix in machine learning is in model training data comprised of many rows and columns and often represented using the capital letter $X$. The geometric analogy used to help understand vectors and some of their operations does not hold with matrices. Further, a vector itself may be considered a matrix with one column and multiple rows. Often the dimensions of the matrix are denoted as $m$ and $n$ or $m \times n$ for the number of rows and the number of columns respectively. Now that we know what a matrix is, let's look at defining one in Python.

# 9.3 Defining a Matrix

We can represent a matrix in Python using a two-dimensional NumPy array. A NumPy array can be constructed given a list of lists. For example, below is a 2 row, 3 column matrix.

```
# create matrix
from numpy import array
A = array([[1, 2, 3], [4, 5, 6]])
print(A)
```

Listing 9.1: Example of creating a matrix.

Running the example prints the created matrix showing the expected structure.

```
[[1 2 3]
 [4 5 6]]
```

Listing 9.2: Sample output from creating a matrix.

# 9.4 Matrix Arithmetic

In this section will demonstrate simple matrix-matrix arithmetic, where all operations are performed element-wise between two matrices of equal size to result in a new matrix with the same size.