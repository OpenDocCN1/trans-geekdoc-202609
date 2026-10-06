# 132 Machine Learning for Biomedical Applications

in the columns that represent the closest neighbors of that node.^{22} Finally, we need A to be symmetric, or otherwise the derivation of the Laplacian will not hold. Thus, the matrix A is symmetrized as $A_{ij}=A_{ji}$.

Let’s step through the following simple example for the data matrix X with 6 examples, each with 2 features:

```
$X = \begin{pmatrix} 4 & 3 \ 1 & 3 \ 4 & 4 \ 2 & 2 \ 3 & 0 \ 2 & 0 \end{pmatrix} (5.71)$
```

To calculate the adjacency matrix A, we must first estimate the sum of square distances (SSD) between all points. Let us do this for the first data point. We write the calculation in the style of Python broadcasting as:

```
$x_0 - X = \begin{pmatrix} 4 & 3 \ 4 & 3 \ 4 & 4 \ 4 & 2 \ 4 & 3 \ 4 & 3 \end{pmatrix} = \begin{pmatrix} 0 & 0 \ 3 & 0 \ 0 & -1 \ 2 & 1 \ 1 & 3 \ 2 & 3 \end{pmatrix} (5.72)$
```

To calculate the SSD for this point, we need to square^{23} and sum the distances:

```
$$\sum_j (x_0 - X_j)^2 = \sum_j \begin{pmatrix} 0 & 0 \ 3 & 0 \ 0 & -1 \ 2 & 1 \ 1 & 3 \ 2 & 3 \end{pmatrix}^2 = \sum_j \begin{pmatrix} 0 & 0 \ 9 & 0 \ 0 & 1 \ 4 & 1 \ 1 & 9 \ 4 & 9 \end{pmatrix} = 5 \ (5.73)$
```

> $^{22}$ Note that it is common practice to binarize A; however, weighted adjacency matrices can also be used.

> $^{23}$ * Represents element-wise multiplication.