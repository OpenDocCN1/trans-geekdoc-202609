Or without the dot notation:

$$A = LL^T$$ (14.7)

Where \( A \) is the matrix being decomposed, \( L \) is the lower triangular matrix and \( L^T \) is the transpose of \( L \). The decompose can also be written as the product of the upper triangular matrix, for example:

$$A = U^T \cdot U$$ (14.8)

Where \( U \) is the upper triangular matrix. The Cholesky decomposition is used for solving linear least squares for linear regression, as well as simulation and optimization methods. When decomposing symmetric matrices, the Cholesky decomposition is nearly twice as efficient as the LU decomposition and should be preferred in these cases.

While symmetric, positive definite matrices are rather special, they occur quite frequently in some applications, so their special factorization, called Cholesky decomposition, is good to know about. When you can use it, Cholesky decomposition is about a factor of two faster than alternative methods for solving linear equations.

> — Page 100, *Numerical Recipes: The Art of Scientific Computing*, Third Edition, 2007.

The Cholesky decomposition can be implemented in NumPy by calling the `cholesky()` function. The function only returns \( L \) as we can easily access the \( L \) transpose as needed. The example below defines a \( 3 \times 3 \) symmetric and positive definite matrix and calculates the Cholesky decomposition, then the original matrix is reconstructed.

```
# Cholesky decomposition
from numpy import array
from numpy.linalg import cholesky

# define symmetrical matrix
A = array([
    [2, 1, 1],
    [1, 2, 1],
    [1, 1, 2]])
print(A)
# factorize
L = cholesky(A)
print(L)
# reconstruct
B = L.dot(L.T)
print(B)
```

# Listing 14.5: Example of calculating an Cholesky decomposition.

Running the example first prints the symmetric matrix, then the lower triangular matrix from the decomposition followed by the reconstructed matrix.

```
[[2 1 1]
 [1 2 1]
 [1 1 2]]

[[ 1.41421356  0.          0.        ]
 [ 0.70710678  1.22474487  0.        ]]
```