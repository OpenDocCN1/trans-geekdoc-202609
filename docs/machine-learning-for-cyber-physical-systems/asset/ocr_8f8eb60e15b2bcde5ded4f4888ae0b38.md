![](bbox=[0.135, 0.135, 0.86, 0.195])

Fig 2: Work-flow for data-driven condition-monitoring on measurement stations

# 3.1 Z-score normalization

It is assumed that \( x[k] \in \mathbb{R} \) with \( k = 1 ... K \) is the time series of a process variable with mean value \( \mu \) and standard deviation \( \sigma \). Hence, the set of all process variables is described as

\( X = \left[ x_1[k], x_2[k], ..., x_p[k] \right] \) (1)

With \( p \) being the number of process variables resulting in the matrix \( X \in \mathbb{R}^{(K \times P)} \). Finally, the z-score normalization is defined as

\( Z = \frac{x_j - \mu_j}{\sigma_j} \) (2)

With \( = 1 ... P \). As mentioned, the PCA is calculated using the matrix \( Z \) containing the normalized process variables.

# 3.2 Principal Component Analysis

The principal component analysis (PCA) is a procedure of multivariate statistics to structure large data sets. In that case it is used for model reduction. The main concept is to perform an orthogonal transformation to map the set of correlated variables into a set of linear, uncorrelated ones. Mathematically, the principal components then cover the variance accounted for in the data set. The calculation of the principal components is carried out by computing the eigenvectors of the covariance matrix being defined as:

\( \Sigma = \begin{bmatrix} \sigma_{11}^2 & \sigma_{12}^2 & \cdots & \sigma_{1p}^2 \\ \sigma_{12}^2 & \sigma_{22}^2 & \cdots & \sigma_{2p}^2 \\ \vdots & \vdots & \ddots & \vdots \\ \sigma_{1p}^2 & \sigma_{2p}^2 & \cdots & \sigma_{pp}^2 \end{bmatrix} \) (3)

with \( \sigma_{ij}^2 \) being the covariance of the two standardized variables \( z_i[k] \) and \( z_j[k] \) in the variable set. Next, the eigenvalues \( \lambda \) of the covariance matrix are calculated and sorted in ascending order. This results in the final diagonal matrix \( \Lambda \in \mathbb{R}^{P \times P} \) defined as

\( \Lambda = \begin{bmatrix} \lambda_1 & 0 & 0 \\ 0 & \ddots & 0 \\ 0 & 0 & \lambda_p \end{bmatrix} \text{with } \lambda_1 \ge \cdots \ge \lambda_p \) (4)

In a next step, the corresponding eigenvectors of the eigenvalue matrix \( \Lambda \) are calculated and summarized in columns. This results in the matrix \( \Gamma \in \mathbb{R}^{P \times P} \)