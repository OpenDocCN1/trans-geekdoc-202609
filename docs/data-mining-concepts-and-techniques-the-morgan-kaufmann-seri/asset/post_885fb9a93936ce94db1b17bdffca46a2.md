
fall into the following form:

$$
\begin{aligned}
\min \quad & a + \mathbf{b}^T \mathbf{x} + \frac{1}{2} \mathbf{x}^T \mathbf{C} \mathbf{x} \\
s.t. \quad & \mathbf{Px} \le \mathbf{d} \\
& \mathbf{Qx} = \mathbf{e}.
\end{aligned}
$$
(A.48)

Without loss of generality, we can assume that matrix C is symmetric.
A typical example is *constrained regression analysis*

$$
\begin{aligned}
\min_{\mathbf{x}} \quad & ||\mathbf{Ax} - \mathbf{b}||_2^2 \\
s.t. \quad & |\mathbf{l}[i]| \le \mathbf{x}[i] \le \mathbf{u}[i], \forall i,
\end{aligned}
$$
(A.49)

which is equivalent to

$$
\begin{aligned}
\min_{\mathbf{x}} \quad & \mathbf{x}^T \mathbf{A}^T \mathbf{A} \mathbf{x} - 2\mathbf{b}^T \mathbf{A} \mathbf{x} + \mathbf{b}^T \mathbf{b} \\
s.t. \quad & |\mathbf{l}[i]| \le \mathbf{x}[i] \le \mathbf{u}[i], \forall i.
\end{aligned}
$$
(A.50)

There are versatile solutions toward various QPs. In this section, we provide a solution toward the *equality-constrained QPs (EQPs)* and solutions for the general QPs can be found in the bibliographic notes. EQPs are QPs where only equality constraints exist, and their objective functions fall into the following form:

$$
\begin{aligned}
\min \quad & \mathbf{b}^T \mathbf{x} + \frac{1}{2} \mathbf{x}^T \mathbf{C} \mathbf{x} \\
s.t. \quad & \mathbf{Qx} = \mathbf{e},
\end{aligned}
$$
(A.51)

where the constant term is dropped. If \(\mathbf{x}^*\) is a solution of an EQP, a necessary condition is to have a \(\boldsymbol{\lambda}^*\) vector satisfying the following *KKT system*:

$$
\left[ \begin{array}{cc} \mathbf{C} & \mathbf{Q}^T \\ \mathbf{Q} & 0 \end{array} \right] \left[ \begin{array}{c} -\mathbf{p} \\ \boldsymbol{\lambda}^* \end{array} \right] = \left[ \begin{array}{c} \mathbf{b} + \mathbf{Cx} \\ \mathbf{Qx} - \mathbf{e} \end{array} \right],
$$
(A.52)

where \(\mathbf{x}\) is an estimation of the solution and \(\mathbf{x}^* = \mathbf{x} + \mathbf{p}\). If \(\mathbf{Q}\) is positive definite, based on Eq. (A.52) we can obtain \(\boldsymbol{\lambda}^*\) from the following equation:

$$(\mathbf{Q} \mathbf{C}^{-1} \mathbf{Q}^T) \boldsymbol{\lambda}^* = \mathbf{Q} \mathbf{C}^{-1} \mathbf{b} + \mathbf{e}.$$
(A.53)

Hence \(\mathbf{p}\) can be obtained from the following equation:

$$
\mathbf{Cp} = \mathbf{Q}^T \boldsymbol{\lambda}^* - \mathbf{b} - \mathbf{Cx},
$$
(A.54)

by which we can obtain the final solution \(\mathbf{x}^*\).

## A.3 Matrix and linear algebra

### A.3.1 Linear system Ax = b

In this section, we discuss three types of linear systems Ax = b: (1) \(\mathbf{A} \in \mathbb{R}^{n \times n}\) is a standard square matrix, (2) \(\mathbf{A} \in \mathbb{R}^{n \times m}\), n > m, A has more rows than columns (overdetermined), and (3) \(\mathbf{A} \in \mathbb{R}^{n \times m}\), n < m, A has less rows than columns (underdetermined).

#### Standard square system

If A is invertible, we could directly solve it with the matrix inverse A^{-1}:

```
Ax = b => x = A^{-1}b. (A.55)
```

Iterative methods provide an indirect way to solve the linear system. Widely used iterative methods include Jacobi method, Richardson method, Krylov subspace methods, and so on. The key idea of iterative methods is to choose suitable S and d and set up an iteration in the form of

```
x^{(k+1)} = Sx^{(k)} + d. (A.56)
```

In each iteration, the residual error \(\|\mathbf{x}^{(k)} - \mathbf{x}^*\|\) is reduced where \(\mathbf{x}^*\) is the solution to Ax = b. After several iterations, \(\mathbf{x}^{(k)}\) converges to \(\mathbf{x}^*\).

A preconditioning method aims to find a simpler matrix P, which is close to A, that is, (A - P) has low rank or small norm. Then, we solve P^{-1}Ax = P^{-1}b instead of Ax = b because working on P^{-1}A is usually faster. Some typical choices of P include the diagonal matrix with the main diagonal of A, triangular matrix copying the corresponding part of A, and so on.

#### Overdetermined system

Suppose \(\mathbf{A}\) has independent columns, \(\operatorname{rank}(\mathbf{A}) = m\), we have

```
Ax = b <=> A^T Ax = A^T b <=> x = (A^T A)^{-1} A^T b, (A.57)
```

which gives the solution minimizing ||Ax - b||^2.

When A^T A is not invertible, the least square solution is x = A^+b where A^+ is the pseudo-inverse of A. Specifically, we first perform singular value decomposition (SVD) on A and obtain A = UΣV^T, then we have A^+ = VΣ^{-1}U^T.

#### Underdetermined system

For underdetermined system, there are many least square solutions, and it turns out that A^+b is the least square solution with the smallest norm ||x||^2. Similar to the overdetermined system, when \(\mathbf{A}\) has independent rows, \(\operatorname{rank}(\mathbf{A}) = n\), we have

```
Ax = b <=> x = A^T (AA^T)^{-1} b. (A.58)
```

In some cases, we want to regularize the linear system with an \(\ell^2\) penalty term. Thus our optimization goal becomes

```
Minimize ||Ax - b||^2 + δ^2||x||_2^2, (A.59)
```

where \(\delta^2\) is the weight of the penalty term. It is equivalent to solve \((\mathbf{A}^\top \mathbf{A} + \delta^2 \mathbf{I})\mathbf{x} = \mathbf{A}^\top \mathbf{b}\), and this approach is called ridge regression.

### A.3.2 Norms of vectors and matrices

#### Norms of vectors

The norm of a vector is defined as a function mapping from vector space \(V\) to a real value: \(\|\cdot\| : V \rightarrow \mathbb{R}\). Given a vector \(\mathbf{v}\), it measures the length of the vector \(\|\mathbf{v}\|\). For each \(\mathbf{v}, \mathbf{w} \in V\) and \(c \in \mathbb{R}\), these three properties always hold:

- Positive definite: \(\|\mathbf{v}\| \ge 0\) and \(\|\mathbf{v}\| = 0 \Longleftrightarrow \mathbf{v} = 0\).
- Absolutely homogeneous: \(\|c\mathbf{v}\| = |c| \|\mathbf{v}\|\), where \(|c|\) is the absolute value of \(c\).
- Triangle inequality: \(\|\mathbf{v} + \mathbf{w}\| \le \|\mathbf{v}\| + \|\mathbf{w}\|\).

Here, we give the definitions of some widely used vector norms:

- \(\ell^1\) norm (Manhattan Norm): \(\|\mathbf{v}\|_1 = \sum_i |\mathbf{v}[i]|\).
- \(\ell^2\) norm (Euclidean Norm): \(\|\mathbf{v}\|_2 = \sqrt{\sum_i \mathbf{v}[i]^2} = \sqrt{\mathbf{v}^\top \mathbf{v}}\).
- \(\ell^\infty\) norm: \(\|\mathbf{v}\|_\infty = \max_i |\mathbf{v}[i]|\).

#### Norms of matrices

Induced matrix norm could be induced by the vector norm with:

\(\|\mathbf{A}\| = \max_{\mathbf{v} \neq 0} \frac{\|\mathbf{A}\mathbf{v}\|}{\|\mathbf{v}\|}\).

In addition to the properties that the vector norm satisfies, induced matrix norm has the following properties, that is, for all \(\mathbf{A}, \mathbf{B}\) and \(\mathbf{v}\), \(\|\mathbf{A}\mathbf{v}\| \le \|\mathbf{A}\| \|\mathbf{v}\|\) and \(\|\mathbf{A}\mathbf{B}\| \le \|\mathbf{A}\| \|\mathbf{B}\|\).

Here, we introduce how to compute some typical matrix norms:

- \(\ell^1\) norm is the largest \(\ell^1\) norm of the columns of \(\mathbf{A}\): \(\|\mathbf{A}\|_1 = \max_j \sum_i |\mathbf{A}[i, j]|\).
- \(\ell^2\) norm is the largest singular value of \(\mathbf{A}\): \(\|\mathbf{A}\|_2 = \sqrt{\maxeig(\mathbf{A}^T \mathbf{A})}\), where \(\maxeig(\cdot)\) denotes the maximum eigenvalue.
- \(\ell^\infty\) norm is the largest \(\ell^1\) norm of the rows of \(\mathbf{A}\): \(\|\mathbf{A}\|_\infty = \max_i \sum_j |\mathbf{A}[i, j]|\).
- Frobenius norm comes from the singular values \(\sigma_i\) (\(i = 1, \dots, r\)) of \(\mathbf{A}\), that is, \(\|\mathbf{A}\|_F^2 = \sigma_1^2 + \cdots + \sigma_r^2\), where \(r\) is the rank of matrix \(\mathbf{A}\). It could also be derived with: \(\|\mathbf{A}\|_F = \sum_{ij} |\mathbf{A}[i, j]|^2\).

### A.3.3 Matrix decompositions

#### Eigenvalues and eigendecomposition

Given a square matrix \(\mathbf{A} \in \mathbb{R}^{n \times n}\), if \(\lambda \in \mathbb{R}\) and \(\mathbf{x} \in \mathbb{R}^n \setminus \{\mathbf{0}\}\) satisfy that \(\mathbf{A}\mathbf{x} = \lambda \mathbf{x}\), we call \(\lambda\) an eigenvalue of \(\mathbf{A}\) and \(\mathbf{x}\) is the corresponding eigenvector.\(^1\) From \(\mathbf{A}\mathbf{x} = \lambda \mathbf{x}\), we have \((\mathbf{A} - \lambda \mathbf{I})\mathbf{x} = 0\). Since \(\mathbf{x}\) is not a zero vector, we have that \(\mathbf{A} - \lambda \mathbf{I}\) is not invertible, and its determinant must be zero. To compute all the eigenvalues of A, we need to solve the roots of equation \(\det(\mathbf{A} - \lambda \mathbf{I}) = 0\). Since the equation has n degrees for λ, there are n eigenvalues in total, with possible duplicates.

- The sum of eigenvalues equals to the trace: \(\operatorname{tr}(\mathbf{A}) = \sum_{i=1}^n \lambda_i\).
- The product of eigenvalues equals to the determinant: \(\det(\mathbf{A}) = \prod_{i=1}^n \lambda_i\).

When matrix A has n independent eigenvectors, it could be decomposed into

```
A = X\Lambda X^{-1},
```

where the columns of X are the n eigenvectors of A, and \(\Lambda\) is a diagonal matrix whose diagonal entries are the n eigenvalues of A. This decomposition is named as eigendecomposition. Notice the symmetric matrix always has n independent eigenvectors and could always be eigendecomposed. From A = X\Lambda X^{-1}, we have A^k = X\Lambda^k X^{-1}, which means the eigenvalues of A^k are \(\lambda_1^k, \cdots, \lambda_n^k\). Besides, for each v \in R^n, it could be written as v = c_1 x_1 + \cdots + c_n x_n. This gives an easier way to compute A^k v:

```
A^k v = c_1 \lambda_1^k x_1 + \cdots + c_n \lambda_n^k x_n.
```

#### Singular value decomposition (SVD)

Given a matrix \(\mathbf{A} \in \mathbb{R}^{m \times n}\) with rank r, the SVD of A is written as

```
A = U \Sigma V^T,
```

where \(\mathbf{U} \in \mathbb{R}^{m \times n}\) is the orthogonal matrix containing orthonormal eigenvectors of \(\mathbf{A}\mathbf{A}^T\), \(\mathbf{V} \in \mathbb{R}^{n \times n}\) is the orthogonal matrix containing orthonormal eigenvectors of \(\mathbf{A}^T \mathbf{A}\), \(\Sigma \in \mathbb{R}^{m \times n}\) is a matrix that satisfies \(\Sigma_{ii} = \sigma_i\), \(i = 1, \cdots, r\), and the other entries are all zeros. Here, we call \(\sigma_1, \cdots, \sigma_r\) singular values. The singular values are all positive and in the descending order. Notice that different from eigendecomposition, SVD is applicable for any rectangular matrix.

To compute SVD, we first perform eigendecomposition on \(\mathbf{A}^T \mathbf{A}\) and obtain the orthogonal eigenvectors \(\mathbf{v}_1, \cdots, \mathbf{v}_r\). From the form of SVD, we know that \(\mathbf{A}\mathbf{v}_k = \mathbf{u}_k \sigma_k\), \(k = 1, \cdots, r\). Hence \(\mathbf{u}_k = \frac{\mathbf{A}\mathbf{v}_k}{\sigma_k}\), \(k = 1, \cdots, r\). For the last n - r columns of V, we have \(\mathbf{A}\mathbf{v}_k = 0\), \(k = r + 1, \cdots, n\). Therefore \(\mathbf{v}_{r+1}, \cdots, \mathbf{v}_n\) are the orthogonal basis from the nullspace of A. Similarly, \(\mathbf{u}_{r+1}, \cdots, \mathbf{u}_m\) are the orthogonal basis from the nullspace of \(\mathbf{A}^T\).

With SVD, A could be written as the sum of rank one matrices:

```
A = \sigma_1 u_1 v_1^T + \cdots + \sigma_r u_r v_r^T.
```

This provides important factors for matrix approximation. Specifically, singular values \(\sigma_1, \sigma_2, \cdots, \sigma_r\) are ordered according to its importance. The first term \(\sigma_1 u_1 v_1^T\) is the closest rank one matrix to A, which means \(\|\mathbf{A} - \mathbf{B}\|\) achieves the minimum value in terms of both \(\ell_2\) norm and Frobenius norm only if rank one matrix \(\mathbf{B} = \sigma_1 u_1 v_1^T\). Furthermore, \(\mathbf{A}_k = \sigma_1 u_1 v_1^T + \cdots + \sigma_k u_k v_k^T\) is the closest rank k approximation to A.
