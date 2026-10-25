
# Part V

# Factorization

# Chapter 14

## Matrix Decompositions

Many complex matrix operations cannot be solved efficiently or with stability using the limited precision of computers. Matrix decompositions are methods that reduce a matrix into constituent parts that make it easier to calculate more complex matrix operations. Matrix decomposition methods, also called matrix factorization methods, are a foundation of linear algebra in computers, even for basic operations such as solving systems of linear equations, calculating the inverse, and calculating the determinant of a matrix. In this tutorial, you will discover matrix decompositions and how to calculate them in Python. After completing this tutorial, you will know:

- What a matrix decomposition is and why these types of operations are important.
- How to calculate an LU and QR matrix decompositions in Python.
- How to calculate a Cholesky matrix decomposition in Python.

Let's get started.

## 14.1 Tutorial Overview

This tutorial is divided into 3 parts; they are:

- What is a Matrix Decomposition
- LU Decomposition
- QR Decomposition
- Cholesky Decomposition

## 14.2 What is a Matrix Decomposition

A matrix decomposition is a way of reducing a matrix into its constituent parts. It is an approach that can simplify more complex matrix operations that can be performed on the decomposed matrix rather than on the original matrix itself. A common analogy for matrix decomposition is the factoring of numbers, such as the factoring of 10 into 2 × 5. For this reason, matrix decomposition is also called matrix factorization. Like factoring real values, there are

## 13.4.4 Tensor Division

The element-wise division of one tensor with another tensor with the same dimensions results in a new tensor with the same dimensions where each scalar value is the element-wise division of the scalars in the parent tensors.

\( A = \begin{pmatrix} a_{1,1,1} & a_{1,2,1} & a_{1,3,1} \\ a_{2,1,1} & a_{2,2,1} & a_{2,3,1} \end{pmatrix}, \begin{pmatrix} a_{1,1,2} & a_{1,2,2} & a_{1,3,2} \\ a_{2,1,2} & a_{2,2,2} & a_{2,3,2} \end{pmatrix} \) (13.14)

\( B = \begin{pmatrix} b_{1,1,1} & b_{1,2,1} & b_{1,3,1} \\ b_{2,1,1} & b_{2,2,1} & b_{2,3,1} \end{pmatrix}, \begin{pmatrix} b_{1,1,2} & b_{1,2,2} & b_{1,3,2} \\ b_{2,1,2} & b_{2,2,2} & b_{2,3,2} \end{pmatrix} \) (13.15)

\( C = \frac{A}{B} \) (13.16)

\( C = \begin{pmatrix} \frac{a_{1,1,1}}{b_{1,1,1}} & \frac{a_{1,2,1}}{b_{1,2,1}} & \frac{a_{1,3,1}}{b_{1,3,1}} \\ \frac{a_{2,1,1}}{b_{2,1,1}} & \frac{a_{2,2,1}}{b_{2,2,1}} & \frac{a_{2,3,1}}{b_{2,3,1}} \end{pmatrix}, \begin{pmatrix} \frac{a_{1,1,2}}{b_{1,1,2}} & \frac{a_{1,2,2}}{b_{1,2,2}} & \frac{a_{1,3,2}}{b_{1,3,2}} \\ \frac{a_{2,1,2}}{b_{2,1,2}} & \frac{a_{2,2,2}}{b_{2,2,2}} & \frac{a_{2,3,2}}{b_{2,3,2}} \end{pmatrix} \) (13.17)

In NumPy, we can divide tensors directly by dividing arrays.

```
# tensor division
from numpy import array
# define first tensor
A = array([
    [[1,2,3], [4,5,6], [7,8,9]],
    [[11,12,13], [14,15,16], [17,18,19]],
    [[21,22,23], [24,25,26], [27,28,29]]])
# define second tensor
B = array([
    [[1,2,3], [4,5,6], [7,8,9]],
    [[11,12,13], [14,15,16], [17,18,19]],
    [[21,22,23], [24,25,26], [27,28,29]]])
# divide tensors
C = A / B
print(C)
```

### Listing 13.7: Example of tensor Hadamard product.

Running the example prints the result of multiplying the tensors.

```
[[[ 1  4  9]
  [ 16 25 36]
  [ 49 64 81]]]

[[121 144 169]
 [196 225 256]
 [289 324 361]]]

[[441 484 529]
 [576 625 676]
 [729 784 841]]]
```

### Listing 13.8: Sample output from tensor Hadamard product.

### Listing 13.9: Example of dividing tensors.

Running the example prints the result of dividing the tensors.

```
[[[ 1.  1.  1.]
  [ 1.  1.  1.]
  [ 1.  1.  1.]]]

[[ 1.  1.  1.]
 [ 1.  1.  1.]
 [ 1.  1.  1.]]

[[ 1.  1.  1.]
 [ 1.  1.  1.]
 [ 1.  1.  1.]]]
```

### Listing 13.10: Sample output from dividing tensors.

## 13.5 Tensor Product

The tensor product operator is often denoted as a circle with a small x in the middle. We will denote it here as \(\otimes\). Given a tensor \(A\) with \(q\) dimensions and tensor \(B\) with \(r\) dimensions, the product of these tensors will be a new tensor with the order of \(q + r\) or, said another way, \(q + r\) dimensions. The tensor product is not limited to tensors, but can also be performed on matrices and vectors, which can be a good place to practice in order to develop the intuition for higher dimensions. Let's take a look at the tensor product for vectors.

\(a = \begin{pmatrix} a_1 \\ a_2 \end{pmatrix}\) (13.18)

\(b = \begin{pmatrix} b_1 \\ b_2 \end{pmatrix}\) (13.19)

\(C = a \otimes b\) (13.20)

\(C = \begin{pmatrix} a_1 \times \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} \\ a_2 \times \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} \end{pmatrix}\) (13.21)

Or, unrolled:

\(C = \begin{pmatrix} a_1 \times b_1 & a_1 \times b_2 \\ a_2 \times b_1 & a_2 \times b_2 \end{pmatrix}\) (13.22)

Let's take a look at the tensor product for matrices.

\(A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{pmatrix}\) (13.23)

$$B = \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix}$$ (13.24)

$$C = A \otimes B$$ (13.25)

$$C = \begin{pmatrix} a_{1,1} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} & a_{1,2} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} \\ a_{2,1} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} & a_{2,2} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} \end{pmatrix}$$ (13.26)

Or, unrolled:

$$C = \begin{pmatrix} a_{1,1} \times b_{1,1} & a_{1,1} \times b_{1,2} & a_{1,2} \times b_{1,1} & a_{1,2} \times b_{1,2} \\ a_{1,1} \times b_{2,1} & a_{1,1} \times b_{2,2} & a_{1,2} \times b_{2,1} & a_{1,2} \times b_{2,2} \\ a_{2,1} \times b_{1,1} & a_{2,1} \times b_{1,2} & a_{2,2} \times b_{1,1} & a_{2,2} \times b_{1,2} \\ a_{2,1} \times b_{2,1} & a_{2,1} \times b_{2,2} & a_{2,2} \times b_{2,1} & a_{2,2} \times b_{2,2} \end{pmatrix}$$ (13.27)

The tensor product can be implemented in NumPy using the `tensordot()` function. The function takes as arguments the two tensors to be multiplied and the axis on which to sum the products over, called the sum reduction. To calculate the tensor product, also called the tensor dot product in NumPy, the axis must be set to 0. In the example below, we define two order-1 tensors (vectors) with and calculate the tensor product.

```
# tensor product
from numpy import array
from numpy import tensordot
# define first vector
A = array([1,2])
# define second vector
B = array([3,4])
# calculate tensor product
C = tensordot(A, B, axes=0)
print(C)
```

### Listing 13.11: Example of tensor product.

Running the example prints the result of the tensor product. The result is an order-2 tensor (matrix) with the lengths 2 × 2.

```
[[3 4]
 [6 8]]
```

### Listing 13.12: Sample output from tensor product.

The tensor product is the most common form of tensor multiplication that you may encounter, but there are many other types of tensor multiplications that exist, such as the tensor dot product and the tensor contraction.

## 13.6 Extensions

This section lists some ideas for extending the tutorial that you may wish to explore.

- Update each example using your own small contrived tensor array data.
- Implement three other types of tensor multiplication not covered in this tutorial with small vector or matrix data.
- Write your own functions to implement each tensor arithmetic operation.

If you explore any of these extensions, I'd love to know.

## 13.7 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 13.7.1 Books

- _A Student's Guide to Vectors and Tensors_, 2011. http://amzn.to/2kmUvvF
- Chapter 12, Special Topics, _Matrix Computations_, 2012. http://amzn.to/2B9xnLD
- _Tensor Algebra and Tensor Analysis for Engineers_, 2015. http://amzn.to/2C6gzCu

### 13.7.2 API

- The N-dimensional array. https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.ndarray.html
- numpy.tensordot() API. https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.tensordot.html

### 13.7.3 Articles

- Tensor algebra on Wikipedia. https://en.wikipedia.org/wiki/Tensor_algebra
- Tensor on Wikipedia. https://en.wikipedia.org/wiki/Tensor
- Tensor product on Wikipedia. https://en.wikipedia.org/wiki/Tensor_product
- Outer product on Wikipedia. https://en.wikipedia.org/wiki/Outer_product

## 13.8 Summary

In this tutorial, you discovered what tensors are and how to manipulate them in Python with NumPy. Specifically, you learned:

- That tensors are a generalization of matrices and are represented using n-dimensional arrays.
- How to implement element-wise operations with tensors.
- How to perform the tensor product.

### 13.8.1 Next

This was the end of the part on matrices, next is the part on matrix factorization, starting with a gentle introduction to matrix decomposition methods.
