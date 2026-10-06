# Machine Learning for Biomedical Applications

![](bbox=[0.135, 0.083, 0.833, 0.303])

**Figure 5.6** A scale along the $\mathbf{v} = \left(egin{pmatrix} 1 \ 1 \end{pmatrix}ight)$ axis of magnitude 3.

# Matrix diagonalization

We can see from Fig. 5.6 that this represents the same transformation as before (a stretch of 3 along one axis and 1 along the other) this time along the $\mathbf{v}_1 = \left(egin{pmatrix} 1 \ 0 \end{pmatrix}ight)$ and $\mathbf{v}_2 = \left(egin{pmatrix} 0 \ 1 \end{pmatrix}ight)$ axes. Thus, eigenvectors $\mathbf{v}_1, \mathbf{v}_2$ represent the same transform in a rotated coordinate basis. More specifically, it can be shown that the eigenvectors of any symmetric matrix $\mathbf{A}_2$ form an orthogonal basis from which the matrix may be diagonalized

> $$\mathbf{A}_2\mathbf{V} = \mathbf{\Lambda}\mathbf{V}$$
$$(5.33)$
$\rightarrow \mathbf{V}^{-1}\mathbf{A}_2\mathbf{V} = \mathbf{V}^{-1}\mathbf{\Lambda}\mathbf{V}$$
$$(5.34)$
$\= \mathbf{\Lambda}$$
$$(5.35)$
$\= \mathbf{A}$$
$$(5.36)$

Here, Eq. (5.33) is a matrix equivalent of Eq. (5.6), the columns of $\mathbf{V}$ represent all eigenvectors of $\mathbf{A}_2$, and $\mathbf{\Lambda}$ is a diagonal matrix of all eigenvalues. For the example of this case, $\mathbf{A}_2 = \left(egin{pmatrix} \frac{3}{2} & \frac{1}{2} \ \frac{1}{2} & \frac{3}{2} \end{pmatrix}\right)$, $\mathbf{\Lambda} = \left(egin{pmatrix} 3 & 0 \ 0 & 1 \end{pmatrix}\right)$.

# 5.4. Principal component analysis

Using this principle, PCA works by estimating the eigenvectors of the (symmetric) data covariance matrix to return a reduced orthogonal eigen represents the directions of maximal variance in the data. As a demonstration of how this works, consider our again brain-volume data set, which pairs brain volumes of babies with their gestational age at the time of the scan. We see from Fig. 5.7a that the growth patterns of various regions are highly correlated. This means that knowledge of one strongly informs prediction of the other, meaning that consideration of both features is redundant. In PCA the objective is to search for the vector $\mathbf{v}_1$ which, once