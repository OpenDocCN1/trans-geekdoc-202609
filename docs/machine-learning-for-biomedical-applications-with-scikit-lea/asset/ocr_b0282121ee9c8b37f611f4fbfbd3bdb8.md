# 5.4.5 Implementing PCA in Python

Whether you implement PCA using the covariance method or SVD, implementation always starts in the same way: You must demean the data matrix. Following this, eigenvectors and eigenvalues are estimated using either SVD or the covariance method. Assuming the data matrix X has shape $(n_{examples}, n_{features})$ and we are interested in the covariance between features not examples, PCA may run from the following steps:

+   1. Mean center the data matrix $X_C = X - X$ using numpy.mean, Make sure to specify which axis you want to average over (in this case you are looking for a mean value for each feature)
2. Estimate the principal components through either:
   - The covariance method:
     - Estimate the data covariance matrix using Eq. (5.38), implemented using numpy.matmul(...).
     - Estimate the eigenvector and eigenvalues of the covariance matrix using Lambda, numpy.linalg.eig(...).
     - This will return unsorted eigenvalues (Lambda) and eigenvectors (U).
     - Sort eigenvalues and eigenvectors into descending order using numpy.argsort.$10
   - The SVD method:
     - Estimate the singular values and values using U, Lambda, numpy.linalg.svd(...).
     - This will return left singular vectors (U), right singular vectors ($VH^{11}$) and singular values (Lambda)
     - calculate eigenvalues from singular values by implementing Eq. (5.55).

# 5.4.6 PCA for dimensionality reduction

For datasets that have more features than examples, the action of projecting all points onto their PCA components ($Y = XCU$) reduces dimensionality automatically since the total number of nonzero components is at most equal to the smallest dimension of the data matrix (matrix rank $r \le min(n, n)$). Often, the rank of the data covariance matrix may be less as a result of correlation between features. For example, predicting neonatal brain age from the volume of various regions, where we have strong correlation in their trends of growth (Figs. 5.7a and 5.8a). A cumulative distribution of the PCA eigenvalues derived from the full set (Fig. 5.8b) shows

> $^{10}$ numpy.argsort will return the indices that sort an array in ascending the order. This can be used and permute the eigenvalue and eigenvector matrices.

> $^{11}$ Here, VH corresponds to $V^T$; columns of U and rows of VH are the singular vectors.