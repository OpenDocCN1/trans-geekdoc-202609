The total variability is measured by \(VT(\mathbf{R}) = \text{tr}(\mathbf{R}) = 2\), and the proportion of it is explained by \(Y_1\) is \(\lambda_1 / VT(\mathbf{R}) = 1.72/2 = 86\%\). The correlation coefficients between \(Y_1\) and the variables \(Z_i\) are:

\(\text{corr}(Y_1, Z_1) = \frac{e_{11}\sqrt{\lambda_1}}{\sqrt{r_{11}}} = 0.93, \text{corr}(Y_1, Z_2) = 0.93.\) (6.23)

The first principal component of \(\mathbf{R}\) now gives equal greater weight to the variables \(X_1\) and \(X_2\). As discussed in Problem 4.2, it would be more appropriate to calculate the principal components from \(\mathbf{R}\). The determination of the principal components can also be conducted through MATLAB functions. In order to calculate the principal components, the following procedure is applied (Algorithm 6.1).

# **ALGORITHM 6.1 DETERMINATION OF THE PRINCIPAL COMPONENTS**

+   1. Load the data into MATLAB.
+   2. Subtract the mean of each column of data from the corresponding column. This is done to ensure that the data is centered around the origin, which is a requirement for PCA.
+   3. Compute the covariance matrix of the data. This can be done using the cov function in MATLAB.
+   4. Compute the eigenvectors and eigenvalues of the covariance matrix. This can be done using the eig function in MATLAB. The eigenvectors are the principal components, and the eigenvalues are the variances of the data along each principal component.
+   5. Sort the eigenvectors and eigenvalues in descending order of eigenvalues. This will give you the principal components in order of importance, with the first component having the highest variance.
+   6. Project the data onto the principal components by multiplying the data matrix with the matrix of eigenvectors.
+   7. You can also visualize the data in the PCA space using the scatter function in MATLAB with the projected data.

Note: PCA is a powerful tool, but it should be used with caution. It is sensitive to the scale of the data, so it’s recommended to standardize the data before running PCA. Also, it can only be used on linear relationships, so it may not be appropriate for certain types of data or problems.

The code presented in Program 6.2 illustrates the necessary steps to perform the determination of the principal components from the data of matrix \(\mathbf{A}\).