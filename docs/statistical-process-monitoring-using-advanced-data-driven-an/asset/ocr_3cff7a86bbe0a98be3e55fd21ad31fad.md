From now on, we consider that autoscaled data is zero-mean centered with unit variance,

![](bbox=[0.32, 0.155, 0.68, 0.245])

The scaled data **X** can be expressed using singular value decomposition (SVD) as a product of two factors:

X = t_1 w_1^T + t_2 w_2^T + \cdots + t_m w_m^T = T W^T , \quad (2.10)

where T ∈ R^{n×m} represents a matrix of the principal components (PCs) and W ∈ R^{m×m} is the loading matrix. The PCs are linear combinations of the original data, and each PC is not correlated with the others. The loading matrix is frequently calculated through SVD of the covariance matrix S of the data X:

S = \frac{1}{n-1} X^T X = W \Lambda W^T \quad \text{with} \quad W W^T = W^T W = I_n , \quad (2.11)

where, Λ = diag(σ_1^2, ..., σ_m^2) is a matrix comprising eigenvalues of S arranged diagonally in decreasing magnitude. The eigenvalues λ_i are equal to the variance of the PC t_i, σ_i^2 (i.e., var(w_i^T X) = λ_i).

In the presence of cross-correlated multivariate data, X, the first l PCs (where k < m) are sufficient for preserving relevant information in the original data. One important step in PCA model development is to select the number of PCs.

# Criteria for selecting the number of principal components to use

A core step in designing LVR approaches is selecting by the number of LVs, l, to appropriately extract relevant information from the received data. In other words, the prediction performance of the designed LVR model is influenced by the choice of the number of LVs, l. Accordingly, an appropriate estimation of the number of LVs is necessary to avoid the problem of the model underfitting or overfitting the data. Some of these techniques are briefed below:

+   * **The scree test.** The scree plot displays the variance caught by every PC against the number of the PCs [31]. Then, the number of PCs to retain are obtained by finding the value of the eigenvalue λ corresponding to the profile with an elbow shape (i.e., the profile is no longer linear). This identification procedure is easy to visualize but it could be not easy for automatic implementation.

+   * **Parallel analysis.** Parallel analysis compares the variance profile to that obtained by assuming independent variables, to determine the number of PCs. Specifically, l is determined at the point where the two profiles cross [31, 32].

+   * **The cumulative percentage variance (CPV) procedure.** The CPV procedure has been commonly employed to find the number of PCs explaining a certain