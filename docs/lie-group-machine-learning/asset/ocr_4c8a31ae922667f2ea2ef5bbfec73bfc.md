the column vector transformed by symplectic identity matrix U, and the feature vector of X^H X is obtained by the column vector transformed by symplectic identity matrix V. Singular value decomposition is also applicable to the case where the matrix elements are complex numbers. The symplectic alkic elements of the image are real numbers, and the elements of the transformation matrix U and V are also real numbers [28]. By the singular value decomposition theorem, the image matrix X can be decomposed into the sum of r matrices of rank 1.

\begin{equation*} X = U \begin{bmatrix} \Lambda & 0 \\ 0 & 0 \end{bmatrix} V^H = \sum_{i=1}^{r} \sigma_i u_i v_i^H = \sum_{i=1}^{r} \sigma_i A_i \end{equation*}

where A_i = u_i v_i^H (i = 1, 2, ..., r), whose rank is 1, and u_i and v_i are the column vectors of the corresponding singular value σ_i for the symplectic unitary matrices U and V respectively. Further, u_i and v_i are orthogonal to each other, and the inner product of the symplectic matrix can be obtained from the inner product of the matrix. It is easy to see that the base images obtained by the singular value decomposition are orthogonal to each other under the inner product of the defined symplectic matrix, which constitutes a standard orthogonal coordinate system in the R^{mxn}-dimensional symplectic matrix space. The original image is reconstructed using the first k largest singular values in the above equation and its corresponding base image, and the reconstructed image is given by

\begin{equation*} \hat{X} = \sum_{i=1}^{k} \sigma_i A_i \end{equation*}

The singular value σ_i of X is obtained using the standard orthogonality of the base image, i.e., the projection value of X on the base image A_i obtained by its decomposition, as the coordinate value of X in the symplectic orthogonal coordinate system formed by A_i. The original face image reconstructed by the base image can be obtained by the singular value.

![](bbox=[0.1, 0.64, 0.85, 0.72])

According to the image X, we can get the base image A_i of its category. The image to be identified, i.e., image X_1, is regarded as a linear combination of the base image A_i, and the combination expression is

\begin{equation*} X_1 = \sum_{i=1}^{r} a_i A_i \end{equation*}

The combination coefficient a_i in the formula is a projection value of X_1 on the base image A_i. It can be calculated using the inner product of the symplectic matrix defined