# 12.2.2 How to choose the appropriate laplacian matrix

The Laplacian matrices used in the spectral estimation learning method are obtained by the deformation of the similarity matrix and the degree matrix. The commonly used Laplacian matrices have three forms:

```
$L = D - W \qquad (12.4)$
$L_{sym} = D^{-\frac{1}{2}} L D^{-\frac{1}{2}} = I - D^{-\frac{1}{2}} W D^{-\frac{1}{2}} \qquad (12.5)$
$L_{rw} = D^{-1} L = I - D^{-1} W \qquad (12.6)$
```

where $W$ is a similar matrix, $D$ is a degree matrix (or diagonal matrix), $D_{ii} = \sum_{j=1}^{n} w_{ij}$, and $I$ is the identity matrix.

At present, the specific environment of these three forms of Laplacian matrix has not been solved well. In [20], Brand et al. proposed a preliminary research scheme. If the diagonal element $d_{ii}$ in degree matrix $D$ is approximate, then the Laplace and dimensionality reduction results obtained by choosing any form of the matrix are basically the same. By contrast, the difference is considerable.

# 12.2.3 Selecting the appropriate feature vector

In the study of manifold dimensionality reduction and clustering with the spectral estimation method, choosing the eigenvectors to be mapped and selecting and calculating the eigenvectors are difficult problems in the study of spectral theory. In [21], it has been shown that not every feature vector contains the geometric features of the cluster space or the low-dimensional space. If a useless or irrelevant feature vector is chosen, severe dimensionality reduction or clustering failure might occur. For example, three sample data sets with overlapping portions are shown in Figure 12.2(a).

$k=1$, $k=2$, $k=3$ feature vectors are selected for clustering, and the clustering results are shown in Figure 12.2(b)–(d). It can be seen that different feature vectors are selected for clustering, and their effects are different.

For researchers, it is only necessary to select characteristic vectors that contain manifold geometric characteristics. The original spectral estimation learning methods usually choose the eigenvectors of the first $k$ eigenvalues of the Laplacian matrix to solve them. These methods are based on the assumptions of no noise interference and non-sparse data sets. However, in the presence of noise and data sets in real data, such a selection method is prone to error. In this section, an improved feature vector algorithm is proposed, which not only can select the appropriate number of feature vectors, but can also be applied to data clustering with noise.

The spectra of manifolds cannot be obtained by their eigenvalues, but they need to be obtained by other manifold methods. For example, consider the case when we want to reduce the dimensions of the face images of a person aged 40. The spectral