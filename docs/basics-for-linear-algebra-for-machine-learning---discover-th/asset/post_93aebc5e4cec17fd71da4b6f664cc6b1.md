
[[1 2 3]
[4 5 6]
[7 8 9]]
-9.51619735393e-16

Listing 11.8: Sample output from creating the determinant of a matrix.

Like the trace operation, alone, the determinant operation is not interesting, but it offers a simpler notation and it is used as an element in other key matrix operations.

## 11.6 Rank

The rank of a matrix is the estimate of the number of linearly independent rows or columns in a matrix. The rank of a matrix M is often denoted as the function rank().

rank(A) (11.10)

An intuition for rank is to consider it the number of dimensions spanned by all of the vectors within a matrix. For example, a rank of 0 suggest all vectors span a point, a rank of 1 suggests all vectors span a line, a rank of 2 suggests all vectors span a two-dimensional plane. The rank is estimated numerically, often using a matrix decomposition method. A common approach is to use the Singular-Value Decomposition or SVD for short. NumPy provides the matrix_rank() function for calculating the rank of an array. It uses the SVD method to estimate the rank. The example below demonstrates calculating the rank of a matrix with scalar values and another vector with all zero values.

```
# vector rank
from numpy import array
from numpy.linalg import matrix_rank
# rank
v1 = array([1,2,3])
print(v1)
vr1 = matrix_rank(v1)
print(vr1)
# zero rank
v2 = array([0,0,0,0,0])
print(v2)
vr2 = matrix_rank(v2)
print(vr2)
```

Listing 11.9: Example of calculating the rank of vectors.

Running the example prints the first vector and its rank of 1, followed by the second zero vector and its rank of 0.

```
[1 2 3]
1
[0 0 0 0]
0
```

Listing 11.10: Sample output from creating the rank of vectors.

The next example makes it clear that the rank is not the number of dimensions of the matrix, but the number of linearly independent directions. Three examples of a 2 × 2 matrix are provided demonstrating matrices with rank 0, 1 and 2.

```
# matrix rank
from numpy import array
from numpy.linalg import matrix_rank
# rank 0
M0 = array([
    [0,0],
    [0,0]])
print(M0)
mr0 = matrix_rank(M0)
print(mr0)
# rank 1
M1 = array([
    [1,2],
    [1,2]])
print(M1)
mr1 = matrix_rank(M1)
print(mr1)
# rank 2
M2 = array([
    [1,2],
    [3,4]])
print(M2)
mr2 = matrix_rank(M2)
print(mr2)
```

Listing 11.11: Example of creating the rank of matrices.

Running the example first prints a zero 2 × 2 matrix followed by the rank, then a 2 × 2 with a rank 1 and finally a 2 × 2 matrix with a rank of 2.

```
[[0 0]
 [0 0]]
0
[[1 2]
 [1 2]]
1
[[1 2]
 [3 4]]
2
```

Listing 11.12: Sample output from creating the rank of matrices.

## 11.7 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

- Modify each example using your own small contrived array data.
- Write your own functions to implement one operation.
- Research one example where each operation was used in machine learning.

If you explore any of these extensions, I'd love to know.

## 11.8 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 11.8.1 Books

- Section 3.4 Determinants. _No Bullshit Guide To Linear Algebra_, 2017. http://amzn.to/2k76D4
- Section 3.5 Matrix inverse. _No Bullshit Guide To Linear Algebra_, 2017. http://amzn.to/2k76D4
- Section 5.1 The Properties of Determinants, _Introduction to Linear Algebra_, Fifth Edition, 2016. http://amzn.to/2AZ7R8j
- Section 2.3 Identity and Inverse Matrices, _Deep Learning_, 2016. http://amzn.to/2B3MsuU
- Section 2.11 The Determinant, _Deep Learning_, 2016. http://amzn.to/2B3MsuU
- Section 3.D Invertibility and Isomorphic Vector Spaces, _Linear Algebra Done Right_, Third Edition, 2015. http://amzn.to/2BGuEqI
- Section 10.A Trace, _Linear Algebra Done Right_, Third Edition, 2015. http://amzn.to/2BGuEqI
- Section 10.B Determinant, _Linear Algebra Done Right_, Third Edition, 2015. http://amzn.to/2BGuEqI

### 11.8.2 API

- numpy.ndarray.T API. https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.ndarray.T.html
- numpy.linalg.inv() API. https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.linalg.inv.html
- numpy.trace() API. https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.trace.html
- numpy.linalg.det() API. https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.linalg.det.html
- numpy.linalg.matrix_rank() API. https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.linalg.matrix_rank.html

### 11.8.3 Articles

- Transpose on Wikipedia. https://en.wikipedia.org/wiki/Transpose
- Invertible matrix on Wikipedia. https://en.wikipedia.org/wiki/Invertible_matrix
- Trace (linear algebra) on Wikipedia. https://en.wikipedia.org/wiki/Trace_(linear_algebra)
- Determinant on Wikipedia. https://en.wikipedia.org/wiki/Determinant
- Rank (linear algebra) on Wikipedia. https://en.wikipedia.org/wiki/Rank_(linear_algebra)

## 11.9 Summary

In this tutorial, you discovered important linear algebra matrix operations used in the description of machine learning methods. Specifically, you learned:

- The Transpose operation for flipping the dimensions of a matrix.
- The Inverse operations used in solving systems of linear equations.
- The Trace and Determinant operations used as shorthand notation in other matrix operations.

### 11.9.1 Next

In the next chapter you will discover sparsity and sparse matrices.

## Chapter 12

## Sparse Matrices

Matrices that contain mostly zero values are called sparse, distinct from matrices where most of the values are non-zero, called dense. Large sparse matrices are common in general and especially in applied machine learning, such as in data that contains counts, data encodings that map categories to counts, and even in whole subfields of machine learning such as natural language processing. It is computationally expensive to represent and work with sparse matrices as though they are dense, and much improvement in performance can be achieved by using representations and operations that specifically handle the matrix sparsity. In this tutorial, you will discover sparse matrices, the issues they present, and how to work with them directly in Python. After completing this tutorial, you will know:

- That sparse matrices contain mostly zero values and are distinct from dense matrices.
- The myriad of areas where you are likely to encounter sparse matrices in data, data preparation, and sub-fields of machine learning.
- That there are many efficient ways to store and work with sparse matrices and SciPy provides implementations that you can use directly.

Let's get started.

## 12.1 Tutorial Overview

This tutorial is divided into 5 parts; they are:

- 1. Sparse Matrix
- 2. Problems with Sparsity
- 3. Sparse Matrices in Machine Learning
- 4. Working with Sparse Matrices
- 5. Sparse Matrices in Python

## 12.2 Sparse Matrix

A sparse matrix is a matrix that is comprised of mostly zero values. Sparse matrices are distinct from matrices with mostly non-zero values, which are referred to as dense matrices.

A matrix is sparse if many of its coefficients are zero. The interest in sparsity arises because its exploitation can lead to enormous computational savings and because many large matrix problems that occur in practice are sparse.

> — Page 1, Direct Methods for Sparse Matrices, Second Edition, 2017.

The sparsity of a matrix can be quantified with a score, which is the number of zero values in the matrix divided by the total number of elements in the matrix.

```
sparsity = \frac{\text{count of non-zero elements}}{\text{total elements}} (12.1)
```

Below is an example of a small 3 × 6 sparse matrix.

```
A = \begin{pmatrix} 1 & 0 & 0 & 1 & 0 & 0 \\ 0 & 0 & 2 & 0 & 0 & 1 \\ 0 & 0 & 0 & 2 & 0 & 0 \end{pmatrix} (12.2)
```

The example has 13 zero values of the 18 elements in the matrix, giving this matrix a sparsity score of 0.722 or about 72%.

## 12.3 Problems with Sparsity

Sparse matrices can cause problems with regards to space and time complexity.

### 12.3.1 Space Complexity

Very large matrices require a lot of memory, and some very large matrices that we wish to work with are sparse.

In practice, most large matrices are sparse — almost all entries are zeros.

> — Page 465, Introduction to Linear Algebra, Fifth Edition, 2016.

An example of a very large matrix that is too large to be stored in memory is a link matrix that shows the links from one website to another. An example of a smaller sparse matrix might be a word or term occurrence matrix for words in one book against all known words in English. In both cases, the matrix contained is sparse with many more zero values than data values. The problem with representing these sparse matrices as dense matrices is that memory is required and must be allocated for each 32-bit or even 64-bit zero value in the matrix. This is clearly a waste of memory resources as those zero values do not contain any information.
