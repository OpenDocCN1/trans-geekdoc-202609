$C = \sum_{i} y_i^2 \mathbf{D}_{ii} + \sum_{j} y_j^2 \mathbf{D}_{jj} - 2 \sum_{i,j} y_i y_j \mathbf{D}_{ij} \quad (5.83)$

$C = \mathbf{y}^T\mathbf{D}\mathbf{y} - \mathbf{y}^T\mathbf{Ay} \quad (5.84)$

$C = \mathbf{y}^T\mathbf{Ly} \quad (5.83)$

Thus, we need the $y$ that minimizes $\mathbf{y}^T\mathbf{Ly}$ subject to the constraint that $y_i \neq 0$. We have seen this before for PCA in Eq. (5.43), with the exception that in this case we are looking to minimize and not maximize the objective function. From this we know that the solution to this optimization problem is the Laplacian eigenvector corresponding to the smallest eigenvalue. However, this is zero and corresponds to the constant eigenvector $1$, making it also undesirable because it corresponds to the solution $y_i = y_j$. Solutions are therefore given by the eigenvectors corresponding to the $N$ smallest nonzero eigenvalues. More specifically, for a 2D embedding, we need the two smallest nonzero eigenvalues. Unlike PCA, there is no need to project data onto the eigenvectors—the Laplacian eigenvectors are the embedding.

# 5.7.3 The normalized graph Laplacian

Strictly speaking, most implementations of Laplacian eigenmaps do not use $L = \mathbf{D}-\mathbf{A}$, but instead seek solutions to the generalized eigenvector problem $L\mathbf{y} = \lambda\mathbf{Ay}$. This corresponds to estimating eigenvectors of the normalized graph Laplacian $\mathbf{L = \mathbf{D}^{-1/2}\mathbf{D}-\mathbf{A}^{-1/2}$. If the graph is regular and most vertices have approximately the same degree, then the normalized Laplacian and unnormalized Laplacian will generate very similar results. However, if the degrees in the graph are widely distributed, it is more stable to use a normalized Laplacian. By default, this is the approach taken by scikit-learn.

# 5.7.4 Implementing Laplacian eigenmaps in scikit-learn

Laplacian eigenmaps may be implemented in scikit-learn using the SpectralEmbedding function from the manifold class. As for PCA and ICA, it is possible to tune the dimensionality of the embedding using the n\_components argument. Another hyperparameter for tuning is $k$, i.e., the number of neighbors retained in the adjacency matrix $A$. This is defined through the $n\_neighbors$ argument.

```
# from sklearn.manifold import SpectralEmbedding

# set dimensionality=2 and k-NN to 10
model=SpectralEmbedding(n_components=2,n_neighbors=10)
# fit and transform the data
Z = model.fit_transform(X)
# Z is an n x 2 dimensional embedding of X
```