dimensionality reduction, preserving crucial information.

# Question 4: Can you describe the steps involved in performing PCA?

Answer: The steps involved in performing PCA are:

+   • Standardization: If necessary, it may be normalized by making mean = 0 and variance = 1 for all features, which is good for an analysis.

+   • Compute covariance matrix: Determine the covariance matrix of the standardized data, which measures the correlation and variance of each pair of the features.

+   • Eigenvalue decomposition: Factorize the covariance matrix into its eigenvectors and eigenvalues. Eigenvectors give directions of maximum variance or the PC, while the eigenvalues give the amount of variance captured by each eigenvector.

+   • Select PCs: Sort the eigenvectors in increasing order of the eigenvalues associated with them. Choose the first K eigenvectors that contain the largest amount of variance in the data to be our PC matrix.

+   • Projection: Transform the original data with the selected PCs to get data with fewer dimensions. This is done using the formula where the data matrix is multiplied by the PC matrix using the dot product.

Such steps make it possible to decrease the data dimensionality keeping most of the variance that will allow to carry out analysis, visualization or additional data processing in a lower-dimensional space.

# Question 5: How do you interpret the PC obtained from PCA?