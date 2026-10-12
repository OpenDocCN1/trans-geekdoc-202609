
## Ans: The ability of `numpy` to treat arrays with different dimensions or shape in a uniform way is known as broadcasting.

We can do broadcasting with the help of broadcast method.

![](OEBPS/images/77.jpg)

**Output:**

```
(4, 1)
(5, 1)
(6, 1)
(4, 2)
(5, 2)
(6, 2)
(4, 3)
(5, 3)
(6, 3)
```

### Q14: Explain rules of broadcasting.

*   Whenever two arrays have different dimensions the shape of the one with fewer dimensions is adjusted by padding with ones on its leading (left) side.
*   If there is a difference in the shape of the two arrays, it does not match in any dimension, then dimension is stretched to match the other shape for that array with shape one.
*   An error is raised in case the dimension and sizes disagree, and neither is equal to 1.

### Q15: Explain some statistical measures supported by numpy.

*Ans*:

*   **amin**: Find the minimum value row wise or column wise
*   **mean**: Finds the mean value of given dataset
*   **std**: Finds standard deviation of given dataset
*   **var**: Finds variance of given dataset
*   **average**: Finds weighted average in which average is calculated based upon frequency of occurrence of variables
*   **percentile**: Calculates various percentile intervals mostly around 25, 50 and 75%
*   **ptp**: Calculates peak to peak values in a given dataset
*   **median**: Calculates median from given dataset

![](OEBPS/images/78.jpg)

```
print (np.ptp(a, axis = 0) )
print('percentile axis 1')
print (np.percentile(a,50, axis = 1) )
print('percentile axis 0')
print (np.percentile(a,50, axis = 0) )
print('median')
print (np.median(a, axis = 0) )
print('mean')
print (np.mean(a, axis = 0) )
a = np.array([1,2,3,4])
wts = np.array([4,3,2,1])
print('average')
print (np.average(a,weights = wts) )
print('std')
print (np.std([1,2,3,4]))
print('var')
print (np.var([1,2,3,4]))
```

**Output:**

```
a
[[3 7 5]
 [8 4 3]
 [2 4 9]]
amin 1
[3 3 2]
amin 0
[2 4 3]
ptp
7
ptp axis 0
[6 3 6]
percentile axis 1
[5. 4. 4.]
percentile axis 0
[3. 4. 5.]
median
[3. 4. 5.]
mean
[4.33333333 5. 5.66666667]
average
2.0
std
1.118033988749895
var
1.25
```

### Q16: Explain functions available in numpy.linalg.

*Ans*:

*   **dot(a, b[, out])**: Dot product of two arrays.
*   **linalg.multi_dot(arrays)**: Compute the dot product of two or more arrays in a single function call, while automatically selecting the fastest evaluation order.
*   **vdot(a, b)**: Return the dot product of two vectors.
*   **inner(a, b)**: Inner product of two arrays.
*   **outer(a, b[, out])**: Compute the outer product of two vectors.
*   **matmul(a, b[, out])**: Matrix product of two arrays.
*   **tensordot(a, b[, axes])**: Compute tensor dot product along specified axes for arrays >= 1-D.
*   **einsum(subscripts, *operands[, out, dtype, •])**: Evaluates the Einstein summation convention on the operands.
*   **linalg.matrix_power(M, n)**: Raise a square matrix to the (integer) power `n`.
*   **kron(a, b)**: Kronecker product of two arrays.
*   **linalg.cholesky(a)**: Cholesky decomposition.
*   **linalg.qr(a[, mode])**: Compute the qr factorization of a matrix.
*   **linalg.svd(a[, full_matrices, compute_uv])**: Singular Value Decomposition.
*   **Matrix eigenvalues linalg.eig(a)**: Compute the eigenvalues and right eigenvectors of a square array.
*   **linalg.eigh(a[, UPLO])**: Return the eigenvalues and eigenvectors of a Hermitian or symmetric matrix.
*   **linalg.eigvals(a)**: Compute the eigenvalues of a general matrix.
*   **linalg.eigvalsh(a[, UPLO])**: Compute the eigenvalues of a Hermitian or real symmetric matrix.
*   **linalg.norm(x[, ord, axis, keepdims])**: Matrix or vector norm.
*   **linalg.cond(x[, p])**: Compute the condition number of a matrix.
*   **linalg.det(a)**: Compute the determinant of an array.
*   **linalg.matrix_rank(M[, tol])**: Return matrix rank of array using SVD method.
*   **linalg.slogdet(a)**: Compute the sign and (natural) logarithm of the determinant of an array.
*   **trace(a[, offset, axis1, axis2, dtype, out])**: Return the sum along diagonals of the array.
*   **linalg.solve(a, b)**: Solve a linear matrix equation, or system of linear scalar equations.
*   **linalg.tensorsolve(a, b[, axes])**: Solve the tensor equation a x = b for x.
*   **linalg.lstsq(a, b[, rcond])**: Return the least-squares solution to a linear matrix equation.
*   **linalg.inv(a)**: Compute the (multiplicative) inverse of a matrix.
*   **linalg.pinv(a[, rcond])**: Compute the (Moore-Penrose) pseudo-inverse of a matrix.
*   **linalg.tensorinv(a[, ind])**: Compute the 'inverse' of an N-dimensional array.

### Q17: How to save numpy data from memory to flat file?

*Ans*: numpy data can be stored in **npy** format files which are custom serialized or they can be stored in text file.

![](OEBPS/images/79.jpg)

### Q18: What is the use of where and extract?

*Ans*: Both **where** and **extract** are used to match data based on the conditions.

Where sample:

![](OEBPS/images/80.jpg)

**Extract:** Specifies data and corresponding condition.

![](OEBPS/images/81.jpg)

### Q19: What is the use of ndenumerate?

*Ans*: **ndenumerate** return the co-ordinates and corresponding values in the co-ordinates.

```
A = np.array([[11, 22], [33, 43]])
for index, x in np.ndenumerate(a):
    print(index, x)
```

**Output:**

```
(0, 0) 11
(0, 1) 22
(1, 0) 33
(1, 1) 43
```

### Q20: Explain how can we draw a histogram using numpy?

*Ans*: Consider the following code:

![](OEBPS/images/82.jpg)

The output given will be as follows:

![](OEBPS/images/83.jpg)

**The `print(be)` method** in the above prints bin while the hist prints the corresponding count.

# CHAPTER 4

# Pandas Interview Questions

*Note: [Q: Question Number and Ans: Answer]*

### Q1: What is Pandas?

*Ans*: Pandas is a third party module which helps in easier representation of data in memory to perform analysis. Pandas help in faster representation and processing of data.

### Q2: How does Pandas represent data?

*Ans*: Pandas data representation is in similar line to an excel sheet which consists of row and columns.

Columns in Pandas are known as series.

Collection of series is called data frame.

Thus, data frame is the unit of representation of data which is collection of various series.

Shown is the representation of data frame:

![](OEBPS/images/84.jpg)

### Q3: How to create Series?

*Ans*:

![](OEBPS/images/85.jpg)

### Q4: How to create Data frame?

*Ans*: Data frame can be created directly from dictionary or it can also be created by combining various series.

![](OEBPS/images/86.jpg)

**Output:**

![](OEBPS/images/87.jpg)

### Q5: How are missing values represented in data frame?

*Ans*: Consider the following example:

![](OEBPS/images/88.jpg)

### Q6: Explain the process of creating indexes w.r.t. pandas?

*Ans*: Indexes can be created using `pd.Index` function. Indexes support intersection and union.

![](OEBPS/images/89.jpg)

### Q7: Explain various attributes associated with series.

*Ans*:

*   **axes**: Stands for row.
*   **dtype**: The data type of the object is given by this attribute.
*   **empty**: Checks if series is empty.
*   **ndim**: The dimensions of data are given back.
*   **size**: Size or number of elements from data are given.
*   **values**: Gets the values in the form of ndarray.
*   **head()**: The first n rows are returned.
*   **tail()**: The last n rows are returned.

```
import pandas as pd
import numpy as np
s = pd.Series(np.random.randn(4))
print('series',s)
print('axes',s.axes)
print('Empty',s.empty)
print("Dimensions:")
print(s.ndim)
print ("Size of the object:")
print (s.size)
print ("Underlying data is:")
print (s.values)
```
