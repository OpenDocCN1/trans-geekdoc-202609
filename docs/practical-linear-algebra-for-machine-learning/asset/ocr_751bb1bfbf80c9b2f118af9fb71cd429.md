# Matrix Eigendecomposition

Assume we have the square matrix of $A \in \mathbb{R}^{N\times N}$ which has $N$ linear independent eigenvectors $\mathbf{v}^i$, $i \in 1,\ldots,N$. Then, we can factorize matrix $A$ as below:

$$A = V\Lambda V^{-1}$$

where $V \in \mathbb{R}^{N\times N}$ is the square matrix whose $j^{th}$ column is the eigenvector $\mathbf{v}^j$ of $A$, and $\Lambda$ is the diagonal matrix whose diagonal elements are the corresponding eigenvalues, $\Lambda_{jj} = \lambda_j$.

Above, we basically concatenate eigenvectors $\mathbf{v}^i$ to form the $V$ matrix as below:

![](bbox=[0.429, 0.368, 0.572, 0.46])

# 7.2.3 Discussion on Matrix Eigendecomposition

Note that *we can only factorize* **diagonalizable matrices** as above. But the question is what is a diagonalizable matrix?

# Diagonalizable Matrix

Assume we have the square matrix of $A \in \mathbb{R}^{N\times N}$. It is called diagonalizable or nondefective if there exists an invertible matrix $H$ such that $HAH^{-1}$ is a diagonal matrix.

let’s have a more precise definition of a matrix being singular or non-singular.

# Singular Matrix

Assume we have the square matrix of $A \in \mathbb{R}^{N\times N}$. It is called singular if and only if any of the eigenvalues $(\lambda)$ are zero.

Under some circumstances, we can calculate the **matrix inverse** using the decomposition.