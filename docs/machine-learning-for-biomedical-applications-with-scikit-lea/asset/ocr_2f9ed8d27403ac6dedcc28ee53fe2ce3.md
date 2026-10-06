# Machine Learning for Biomedical Applications

As a result, some nodes now have more than two neighbors. The degree matrix calculates the total number of neighbors for each node (by summing each row or each column):

```
$D = \text{diag}(\sum_{j} \mathbf{A}_{sym}) = \begin{pmatrix} 3 & 0 & 0 & 0 & 0 & 0 \ 0 & 2 & 0 & 0 & 0 & 0 \ 0 & 0 & 2 & 0 & 0 & 0 \ 0 & 0 & 0 & 5 & 0 & 0 \ 0 & 0 & 0 & 0 & 2 & 0 \ 0 & 0 & 0 & 0 & 0 & 2 \end{pmatrix} \quad (5.78)$
```

Finally, the Laplacian matrix is calculated as:

```
$L = \mathbf{D} - \mathbf{A}_{sym} = \begin{pmatrix} 3 & -1 & -1 & -1 & 0 & 0 \ -1 & 2 & 0 & -1 & 0 & 0 \ -1 & 0 & 2 & -1 & -1 & 1 \ -1 & -1 & -1 & 5 & -1 & -1 \ 0 & 0 & 0 & -1 & 2 & -1 \ 0 & 0 & 0 & 0 & -1 & 0 \end{pmatrix} \quad (5.79)$
```

# 5.7.2 Deriving the embedding solution

From the graph we need to calculate the coordinates of a new space in which Euclidean distances approximate geodesics along the manifold. This objective can be summarized by the following cost function:

```
$C = \sum_{i,j} (y_i - y_j)^2 \mathbf{A}_{ij}, \quad (5.80)$
```

where $\mathbf{A}_{ij}$ indexes the symmetric adjacency matrix (dropping the 'sym' notation for clarity) and $y_i$ and $y_j$ represent the coordinates of the lower-dimensional Euclidean space we are trying to find. It is hoped that this function can be minimized if we place points that are close together in the original data together in the new low-dimensional space because $\mathbf{A}_{ij}$ is nonzero only when $(x_i - x_j)^2$ is low. At the same time, we avoid the trivial solution where all points get onto a single location (i.e., either $y_i = 0$ or $y_i = y_j$). We can find a solution by multiplying out our cost function and substituting for $\mathbf{D}_{ii} = \sum_{j} \mathbf{A}_{ij}^2$ as follows:

```
$C = \sum_{i,j} (y_i - y_j)^2 \mathbf{A}_{ij} \quad (5.81)$
```

```
$C = \sum_{i,j} (y_i^2 + y_j^2 - 2y_iy_j) \mathbf{A}_{ij} \quad (5.82)$
```

$^{24}$ And through using the symmetry $\mathbf{D}_{ij} = \sum_{i} \mathbf{A}_{ij}$.