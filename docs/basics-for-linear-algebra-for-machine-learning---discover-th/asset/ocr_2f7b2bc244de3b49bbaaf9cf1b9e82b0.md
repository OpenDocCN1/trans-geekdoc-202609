```
Sigma = diag(s)
# reconstruct matrix
B = U.dot(Sigma.dot(V))
print(B)
```

Listing 16.5: Example of reconstructing a square matrix from a SVD.

Running the example prints the original 3 x 3 matrix and the version reconstructed directly from the SVD elements.

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]

[[ 1.  2.  3.]
 [ 4.  5.  6.]
 [ 7.  8.  9.]]
```

Listing 16.6: Sample output from reconstructing a square matrix from a SVD.

# 16.5 Pseudoinverse

The pseudoinverse is the generalization of the matrix inverse for square matrices to rectangular matrices where the number of rows and columns are not equal. It is also called the Moore-Penrose Inverse after two independent discoverers of the method or the Generalized Inverse.

Matrix inversion is not defined for matrices that are not square. [...] When A has more columns than rows, then solving a linear equation using the pseudoinverse provides one of the many possible solutions.

> — Page 46, Deep Learning, 2016.

The pseudoinverse is denoted as $A^+$, where $A$ is the matrix that is being inverted and $+$ is a superscript. The pseudoinverse is calculated using the singular value decomposition of A:

$A^+ = V \cdot D^+ \cdot U^T$ (16.4)

Or, without the dot notation:

$A^+ = V \cdot D^+ \cdot U^T$ (16.5)

Where $A^+$ is the pseudoinverse, $D^+$ is the pseudoinverse of the diagonal matrix $\Sigma$ and $V^T$ is the transpose of $V^T$. We can get $U$ and $V$ from the SVD operation.

$A = U \cdot \Sigma \cdot V^T$ (16.6)

The $D^+$ can be calculated by creating a diagonal matrix from $\Sigma$, calculating the reciprocal of each non-zero element in $\Sigma$, and taking the transpose if the original matrix was rectangular.

$\Sigma = \begin{pmatrix} s_{1,1} & 0 & 0 \\ 0 & s_{2,2} & 0 \\ 0 & 0 & s_{3,3} \end{pmatrix}$ (16.7)