
```
[0.  4. ]
a^2=  [[ 1. 25.]
       [ 0. 64.]]
[1 2 2]]
```

![](img/37669628775ca7a07835165249fef088_23_0.png)

Fig. 3.5. Element-wise summation. In element-wise operations, the operator performs on corresponding elements from matrices.

## 3.5. Array Manipulation

After becoming familiar with NumPy arrays, now it’s time to learn how to play with arrays and learn some techniques.

### 3.5.1 Indexing

First, let’s define and slice an array:

```python
# Import NumPy library
import numpy as np

# Create a matrix
A = np.array([[2,1,3,4],[5,2,9,4],[5,2,10,1],[2,2,11,-1]])
print('A=\n', A)

# Extract the first two rows
# Remember 0:2 in indexing means {0,1} and does NOT include 2!
# Using : merely, means ALL!
print('The first two rows= \n', A[0:2,:])

# Extract the first three rows and the last two columns
# -2: means the second to the last to the end!
# 0:3 mean {0,1,2}
print('The first three rows and last two columns= \n', A[0:3,-2:])

# Let’s point to one element
# The second row (index 1) and third column (index 2)
# Remember Python indexing starts from zero!!
print('The second row and third column= \n', A[1,2])
```

```
A=
  [[ 2  1  3  4]
   [ 5  2  9  4]
   [ 5  2 10  1]
   [ 2  2 11 -1]]
The first two rows=
  [[2 1 3 4]
   [5 2 9 4]]
The first three rows and last two columns=
  [[ 3  4]
   [ 9  4]
   [10  1]]
The second row and third column=
  9
```

![](img/37669628775ca7a07835165249fef088_24_0.png)

Fig. 3.6. Left figure: Shows the A[0:3,-2:] which is the first three rows and the last two columns. Right figure: Shows A[1,2] which is only one single element located in second row and third column.

Let’s review the code above. At line 11, I used sliced indexing by selecting from a range of indices. At line 21, I only used integer indices. We can simply combine both, but there might be a difference in the output matrix rank. Check the example below:

```python
# Import NumPy library
import numpy as np

# Create a matrix
A = np.array([[2,1,3,4],[5,2,9,4],[5,2,10,1],[2,2,11,-1]])
print('A=\n', A)

# Extract the first row and all columns using two approaches
print('The first row with slice indexing= \n', A[0:1,:]) # Slice indexing
print('The first row with integer indexing= \n', A[0,:])  # Integer indexing
print('The first row shape slice indexing= \n', A[0:1,:].shape) # Slice indexing
print('The first row shape integer indexing= \n', A[0,:].shape)  # Integer indexing
```

```
A=
[[ 2  1  3  4]
 [ 5  2  9  4]
 [ 5  2 10  1]
 [ 2  2 11 -1]]
The first row with slice indexing=
[[2 1 3 4]]
The first row with integer indexing=
[2 1 3 4]
The first row shape slice indexing=
(1, 4)
The first row shape integer indexing=
(4,)
```

If you see the results, the shape of the matrix would be different. Basically, **with slice indexing, we have a rank-2 matrix** and **with integer indexing, we will have a rank-1 matrix**. Be careful about this difference when you are dealing with NumPy indexing. We later talk about the matrix rank concept in detail.

### 3.5.2 Shaping

```python
# Import NumPy library
import numpy as np

# Create a matrix
A = np.array([[2,1,3,4],[5,2,9,4],[5,2,10,1]])
print('A=\n', A)
print('Shape of A=\n', A.shape)

# Reshape A to the new shape of (2,6)
B = A.reshape(2,6)
print("B: \n", B)

# Reshape A to the new shape of (4,-1)
# If we use -1, the remaining dimension will be chosen automatically
C = A.reshape(4,-1)
print("C: \n", C)
# Flatten operation
print("Flatten A: \n", A.ravel())
```

```
A=
  [[ 2  1  3  4]
  [ 5  2  9  4]
  [ 5  2 10  1]]
Shape of A=
(3, 4)
B:
  [[ 2  1  3  4  5  2]
  [ 9  4  5  2 10  1]]
C:
  [[ 2  1  3]
  [ 4  5  2]
  [ 9  4  5]
  [ 2 10  1]]
Flatten A:
[ 2  1  3  4  5  2  9  4  5  2 10  1]
```

The question is how reshaping operations work? Above we had the matrix A of size (3,4) with 12 (3 × 4) total elements. When we use np.reshape, the default NumPy order is “C-style”, i.e., the rightmost index “changes the fastest” for the processing operation. Let’s use the above example of using .ravel() to flatten the matrix: The first element is obviously A₀,₀ and the next one is A₀,₁. The processing and creating the new array is as below when using .ravel():

[A₀,₀, A₀,₁, A₀,₂, A₀,₃, A₁,₀, …, A₂,₃]

## 3.6. Conclusion

In this chapter, you learned how to use NumPy. You also realized how important it is for Machine Learning purposes. But clearly this introduction is NOT a panacea for all your NumPy needs nor it is flawless! You always need to explore more. You can learn more efficiently if you practice on your own. Use the above codes as a starter code and try to play around with them. If you would like to know more about NumPy, you can refer to [8–10].

## Chapter 4: Matrix Operations

This chapter is dedicated to describe how we work with matrices and vectors. The discussion about vectors is straightforward and most of the content of this chapter is dedicated to matrix operations.

### 4.1. Introduction

Have you ever wondered why you need to know matrix operations? The answer is very simple: To work with matrices! Above all, the assumption is that you are familiar with the basic definitions (Chapter 2). In this chapter, the most important matrix and vector operations that we need and frequently encounter in Machine Learning are described.

### 4.2. Matrix Transpose

The transpose of a matrix is an operator which switches the row and column indices of the matrix. As a result, after transposing a matrix, we have a new matrix and is denoted as A^T. Therefore, the i^th row, j^th column elements of A are the j^th row and i^th column elements of A^T, respectively. Assume we show A^T with matrix B, then we have the following:

**B**_{j,i} = **A**_{i,j}

We can have the following example to clarify better:

$$\begin{bmatrix}2 & 3 & 1 \\ 3 & -4 & 2.2\end{bmatrix}^T = \begin{bmatrix}2 & 3 \\ 3 & -4 \\ 1 & 2.2\end{bmatrix}$$

Calculation of a matrix transpose is very easy with Python. For instance, you can try the following code:

```python
# Use Numpy package
import numpy as np

# Define a 3x2 matrix using np.array
A = np.array([[1, 2.2], [4, 7], [8, -2]])
"""A = [[ 1.   2.2]
      [ 4.   7. ]
      [ 8.  -2. ]]"""

print("A is: {}".format(A))
print("The shape of A is: {}".format(A.shape))

# Use transpose() method
B = A.transpose()
"""B = [[ 1.   4.   8. ]
      [ 2.2  7.  -2. ]]"""

print("B is: {}".format(B))
print("The shape of B is: {}".format(B.shape))
```

```
A is: [[ 1.   2.2]
  [ 4.   7. ]
  [ 8.  -2. ]]
The shape of A is: (3, 2)
B is: [[ 1.   4.   8. ]
  [ 2.2  7.  -2. ]]
The shape of B is: (2, 3)
```

NOTE: It is worth noting that (A^T)^T = A.

### 4.3. Identity Matrix

Identity matrix, which is denoted as I_n, is a square matrix (number of rows = number of columns = n) that all its elements along the main diagonal are 1's and the other elements are zero. For example, we can have the following 4 × 4 identity matrix:

$$\begin{bmatrix}1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1\end{bmatrix}$$

You can create the above matrix using the following code:

```python
# Use Numpy package
import numpy as np

# Define an Identity matrix
# Ref: https://docs.scipy.org/doc/numpy/reference/generated/numpy.eye.html
A = np.eye(4)
```

### 4.4. Adding Operation

Adding two matrices is possible only if both matrices have the same shape. Assume C = A + B. Let’s get back to Python and define the same two matrices defined above. After that, we will add them together:

```python
# Use Numpy package
import numpy as np

# Define a 3x2 matrix using np.array
A = np.array([[1, 2.2], [4, 7], [8, -2]])

# Use transpose() method
B = A.transpose()

# Create a matrix similar to A in shape but filled with random
#     numbers
# Use *A.shape argument
A_like = np.random.randn(*A.shape)

# Add two matrices of the same shape
M = A + A_like
print("M equals to: ", M)

# Add two matrices with different shape
C = A + B
print("C equals to: ", C)
```

You should get the following output:

```
M equals to:  [[ 2.4212905   2.88158481]
 [ 4.34872344  5.01038501]
 [ 7.58194231 -2.0192284 ]]
--------------------------------------------------------------------------

ValueError                              Traceback (most recent
    call last)
<ipython-input-35-293b043ce9a9> in <module>()
     16
     17 # Add two matrices with different shape
---> 18 C = A + B
     19 print("C equals to: ", C)
```
