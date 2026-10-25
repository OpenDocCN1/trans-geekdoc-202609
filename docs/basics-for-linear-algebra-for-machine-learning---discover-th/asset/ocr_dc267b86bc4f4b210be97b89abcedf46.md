PCA is an operation applied to a dataset, represented by an \( n \times m \) matrix \( A \) that results in a projection of \( A \) which we will call \( B \). Let's walk through the steps of this operation.

```
$$
A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \\ a_{3,1} & a_{3,2} \end{pmatrix}
$$
(18.1)
```

```
$$
B = PCA(A)
$$
(18.2)
```

The first step is to calculate the mean values of each column.

```
$$
M = mean(A)
$$
(18.3)
```

Next, we need to center the values in each column by subtracting the mean column value.

```
$$
C = A - M
$$
(18.4)
```

The next step is to calculate the covariance matrix of the centered matrix \( C \). Correlation is a normalized measure of the amount and direction (positive or negative) that two columns change together. Covariance is a generalized and unnormalized version of correlation across multiple columns. A covariance matrix is a calculation of covariance of a given matrix with covariance scores for every column with every other column, including itself.

```
$$
V = cov(C)
$$
(18.5)
```

Finally, we calculate the eigendecomposition of the covariance matrix \( V \). This results in a list of eigenvalues and a list of eigenvectors.

```
$$
values, vectors = eig(V)
$$
(18.6)
```

The eigenvectors represent the directions or components for the reduced subspace of \( B \), whereas the eigenvalues represent the magnitudes for the directions. The eigenvectors can be sorted by the eigenvalues in descending order to provide a ranking of the components or axes of the new subspace for \( A \). If all eigenvalues have a similar value, then we know that the existing representation may already be reasonably compressed or dense and that the projection may offer little. If there are eigenvalues close to zero, they represent components or axes of \( B \) that may be discarded. A total of \( m \) or less components must be selected to comprise the chosen subspace. Ideally, we would select \( k \) eigenvectors, called principal components, that have the \( k \) largest eigenvalues.

```
$$
B = select(values, vectors)
$$
(18.7)
```

Other matrix decomposition methods can be used such as Singular-Value Decomposition, or SVD. As such, generally the values are referred to as singular values and the vectors of the subspace are referred to as principal components. Once chosen, data can be projected into the subspace via matrix multiplication.

```
$$
P = B^T \cdot A
$$
(18.8)
```

Where \( A \) is the original data that we wish to project, \( B^T \) is the transpose of the chosen principal components and \( P \) is the projection of \( A \). This is called the covariance method for calculating the PCA, although there are alternative ways to calculate it.