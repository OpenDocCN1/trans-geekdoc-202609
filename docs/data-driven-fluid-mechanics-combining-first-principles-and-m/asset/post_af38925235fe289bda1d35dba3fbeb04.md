
**y = Xz.** If we assume that we have inner products defined on $\mathbb{C}^m$ and $\mathbb{C}^n$ by $\langle z_1, z_2 \rangle_m$ and $\langle y_1, y_2 \rangle_n$, respectively, then the adjoint of a matrix $\boldsymbol{A}$ is defined as the matrix that satisfies

$$\langle A z_1, y_2 \rangle_n = \langle z_1, A^* y_2 \rangle_m.\tag{6.3}$$

That is, the adjoint is what you get if you move an operator to the other side of an inner product. As an aside, note that (6.3) can be very useful in its own right: if one of $m$ or $n$ is much smaller than the other, then it can be substantially easier to evaluate this inner product in the lower-dimensional space. Note also that this definition of an adjoint reduces to the conjugate transpose matrix in the case where the inner products are the “standard”, that is,

$$\langle z_1, z_2 \rangle_m = z_2^{\dagger} z_1, \qquad \langle y_1, y_2 \rangle_n = y_2^{\dagger} y_1,\tag{6.4}$$

where $\cdot^{\dagger}$ denotes the conjugate transpose.

## 6.2.2 The Singular Value Decomposition: Properties

This section lists various properties of the SVD that will be utilized in this chapter. We do not give proofs for all of these properties, and interested readers are encouraged to consult standard references in linear algebra (e.g., Van Loan & Golub 1983, Strang 1988, Horn & Johnson 2012) for further details.

### Optimality

The best rank-$r$ approximation to a matrix $\boldsymbol{X}$ (in a least-squares sense) is obtained by taking the first $r$ components of the SVD of $\boldsymbol{X}$. That is, if $\boldsymbol{X}_r$ is a rank-$r$ approximation of $\boldsymbol{X}$, we have

$$\argmin_{\boldsymbol{X}_r} \|\boldsymbol{X} - \boldsymbol{X}_r\|_F = \boldsymbol{\Phi}_r \boldsymbol{\Sigma}_r \boldsymbol{\Psi}_r^*,\tag{6.5}$$

where $\boldsymbol{\Phi}_r$ and $\boldsymbol{\Psi}_r$ are the first $r$ columns of $\boldsymbol{\Phi}$ and $\boldsymbol{\Psi}$ in the SVD of $\boldsymbol{X}$, and $\boldsymbol{\Sigma}_r$ is a diagonal matrix consisting of the first $r$ singular values of $\boldsymbol{X}$. Here the subscript $F$ denotes the Frobenius norm, given by

$$\|\boldsymbol{X}\|_F = \sqrt{\sum_{j=1}^{n}\sum_{k=1}^{m} |X_{jk}|^2} = \sqrt{\sum_{j=1}^{\min(n,m)} \sigma_j^2},\tag{6.6}$$

which is the same as the Euclidean norm if we were to squeeze the entries of the matrix $\boldsymbol{X}$ into a single long vector. As will be seen later, this property is responsible for the “optimality” of the POD. We also observe from the right inequality in (6.6) a direct connection between the Frobenius norm and the singular values of a matrix. Intuitively, this connection exists because the singular values contain all of the information about the size of the components in the matrix $\boldsymbol{X}$, with the $\boldsymbol{\Phi}$ and $\boldsymbol{\Psi}$ matrices containing orthonormal vectors. Looking again at the quantity that is
minimized on the left-hand side of (6.5), this connection between the Frobenius norm and the SVD also leads to

$$\min_{X_r} \|X - X_r\|_F = \sqrt{\sum_{j=r+1}^{\min(n,m)} \sigma_j^2}.\tag{6.7}$$

As an additional aside, note that we could also consider the $L_2$ operator norm of a matrix, defined by

$$\|X\|_2 = \max_{\|\psi\|_2=1} \|X\psi\|_2 = \sigma_1,\tag{6.8}$$

with the second equality arising because the unit vector $\psi$ that maximizes $\|X\psi\|_2$ is the first right singular vector of $X$, $\psi_1$. Moreover, note that (6.5) also holds when the Frobenius norm is replaced by the operator $L_2$ norm. In this case, the equivalent of (6.7) is

$$\min_{X_r} \|X - X_r\|_2 = \sigma_{r+1}.\tag{6.9}$$

### Relationship between left and right singular vectors

Let $\phi_j$ and $\psi_j$ denote the $j$th left and right singular vectors (i.e., the $j$th columns of $\Phi$ and $\Psi$) of a matrix $X$, respectively, with corresponding singular value $\sigma_j$. These are related by

$$\sigma_j \phi_j = X \psi_j,\tag{6.10}$$

$$\sigma_j \psi_j = X^* \phi_j.\tag{6.11}$$

These relationships follow from the fact that $X\Psi = \Phi\Sigma\Psi^*\Psi = \Phi\Sigma$, and similarly $X^*\Phi = \Psi\Sigma\Phi^*\Phi = \Psi\Sigma$.

### Relationship to eigendecompositions

The left and right singular vectors are eigenvectors of the matrices $XX^*$ and $X^*X$ respectively, with

$$XX^* \phi_j = \sigma_j^2 \phi_j,\tag{6.12}$$

$$X^*X \psi_j = \sigma_j^2 \psi_j.\tag{6.13}$$

These relationships readily follow from (6.10) and (6.11). Note also that the correlation matrices $XX^*$ and $X^*X$ are both Hermitian, since $(XX^*)^* = XX^*$ and $(X^*X)^* = X^*X$.

### Permutation of rows and columns

Suppose we want to rearrange the rows of $X$. We can represent this rearrangement via left multiplication of $X$ by a permutation matrix $P$ (i.e., $P$ is a matrix with exactly one 1 in each row and column, and zeros elsewhere). An SVD of $PX$ is given by

$$PX = (P\Phi)\Sigma\Psi^*.\tag{6.14}$$

Similarly, if $Q$ is a permutation matrix that rearranges the columns of $X$ via right multiplication, then $XQ$ has the SVD

$$XQ = \Phi\Sigma(\Psi Q)^*.\tag{6.15}$$

### Dyadic expansion

The SVD can be expanded as a sum of rank-1 matrices via

$$\boldsymbol{X} = \boldsymbol{\Phi\Sigma\Psi}^* = \sum_{j=1}^{q} \sigma_j \phi_j \psi_j^*.\tag{6.16}$$

### Computing the SVD with a weighted inner product

In practice, the numerical computation of the SVD is most typically done using inbuilt routines (e.g., numpy.linalg.svd in Python). Such routines implicitly assume that the SVD is to be computed with standard inner products for both the columns and rows of the matrix, as in (6.4). This section details how such standard routines may be utilized to perform the SVD with a nonstandard inner product. In particular, suppose that we replace the standard inner products by

$$\langle z_1,z_2\rangle_m = z_2^\dagger W_m z_1,\quad \langle y_1,y_2\rangle_n = y_2^\dagger W_n y_1,\tag{6.17}$$

where as before $z_j$ and $y_j$ are rows and columns of the matrix, respectively. In order for these to satisfy the definition of an inner product, the weight matrices $W_m$ and $W_n$ must be positive definite. Note that the adjoint of $X$ with these inner products is given by

$$X^* = W_m^{-1} X^\dagger W_n,\tag{6.18}$$

which comes from the fact that

$$\begin{aligned}
\langle y, Xz\rangle_n &= z^\dagger X^\dagger W_n y \\
&= z^\dagger W_m W_m^{-1} X^\dagger W_n y \\
&= \langle (W_m^{-1} X^\dagger W_n) y, z\rangle_m \\
&:= \langle X^* y, z\rangle_m.
\end{aligned}$$

$W_n$ and $W_m$ are often positive diagonal matrices, where the diagonal entries contain integration weights. Henceforth, we assume that this is the case, which makes the definition of their square roots $W_m^{1/2}$ and $W_n^{1/2}$ unambiguous. The SVD of $X$ with these inner products can be computed as follows:

- 1. Form the weighted matrix $X_w = W_n^{1/2} X W_m^{-1/2}$.
- 2. Compute the SVD of the weighted matrix $X_w = \Phi_w \Sigma \Psi_w^\dagger$ using standard routines.
- 3. The singular vectors (which are orthonormal with respect to their respective norms) are given by columns $\phi_j$ and $\psi_j$ of $\Phi = W_n^{-1/2} \Phi_w$ and $\Psi = W_m^{-1/2} \Psi_w$, respectively, with corresponding singular values as given in $\Sigma$.

With this computation, it is easy to verify that the identified singular vectors are orthonormal with respect to their respective inner products ($\Phi^\dagger W_n \Phi = I$, $\Psi^\dagger W_m \Psi = I$), and that they satisfy the eigenvalue problems discussed in Section 6.2.2 for the general inner products and adjoints:

$$X_w X_w^\dagger (\phi_w)_j = \sigma_j^2 (\phi_w)_j,$$
$$(W_n^{1/2} X W_m^{-1/2})(W_m^{-1/2} X^\dagger W_n^{1/2})(W_n^{1/2} \phi_j) = \sigma_j W_n^{1/2} \phi_j,$$
$$X(W_m^{-1} X^\dagger W_n)\phi_j = \sigma_j^2 \phi_j,$$
$$X X^* \phi_j = \sigma_j^2 \phi_j,$$

and similarly

$$X_w^\dagger X_w (\psi_w)_j = \sigma_j^2 (\psi_w)_j,$$
$$(W_m^{-1/2} X^\dagger W_n^{1/2})(W_n^{1/2} X W_m^{-1/2})(W_m^{1/2} \psi_j) = \sigma_j W_m^{1/2} \psi_j,$$
$$(W_m^{-1} X^\dagger W_n) X \psi_j = \sigma_j^2 \psi_j,$$
$$X^* X \psi_j = \sigma_j^2 \psi_j,$$

where here $(\phi_w)_j$ and $(\psi_w)_j$ are the $j$th columns of $\Phi_w$ and $\Psi_w$, respectively.

## 6.3 The Proper Orthogonal Decomposition of Discrete Data

Suppose that we measure data that is a function of both space and time, and assemble all data into a matrix, such that each column of the matrix represents a “snapshot” of all data that is measured at a given instance in time, while each row consists of all of the measurements of a given quantity across all times. For example, if we measure two components of the velocity of a fluid ($u$ and $v$) at spatial locations $x_1, x_2, \dots, x_{n_x}$, and at times $t_1, t_2, \dots, t_m$, then the data matrix becomes the $n \times m$ matrix

$$X = \begin{bmatrix} u(x_1,t_1) & u(x_1,t_2) & \cdots & u(x_1,t_m) \\ u(x_2,t_1) & u(x_2,t_2) & \cdots & u(x_2,t_m) \\ \vdots & \vdots & \ddots & \vdots \\ u(x_n,t_1) & u(x_n,t_2) & \cdots & u(x_n,t_m) \\ v(x_1,t_1) & v(x_1,t_2) & \cdots & v(x_1,t_m) \\ v(x_2,t_1) & v(x_2,t_2) & \cdots & v(x_2,t_m) \\ \vdots & \vdots & \ddots & \vdots \\ v(x_n,t_1) & v(x_n,t_2) & \cdots & v(x_n,t_m) \end{bmatrix}, \qquad (6.19)$$

where $n = 2n_x$, since there are two measurements for each spatial location. Note that we are not making any assumptions concerning the spatial or temporal resolution of our data, or in what quantity or quantities are being measured. The only implicit assumption that we are making in forming $X$ is that we measure the same quantities for each snapshot. We next subtract from each column of $X$ a base condition $y_0$. Most typically, this is the mean of all of the columns in $X$, though it need not always be.
