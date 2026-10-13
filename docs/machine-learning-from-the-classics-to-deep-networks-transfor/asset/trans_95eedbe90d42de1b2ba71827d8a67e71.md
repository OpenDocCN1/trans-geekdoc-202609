

## 优化问题

$$
\text{minimize} \quad \frac{1}{2}||X\mathbf{v}||^{2},
$$

subject to

$$
||\mathbf{v}||^{2} = 1,
$$

$$
\mathbf{v} \perp \{\mathbf{v}_{1}, \dots, \mathbf{v}_{k-1}\}, \quad k \neq 1,
$$

where $||\cdot||$ denotes the Euclidean norm.

## 习题

### 6.8
Show that projecting the rows of $X$ onto the $k$-rank subspace, $V_{k} = \text{span}\{\mathbf{v}_{1}, \dots, \mathbf{v}_{k}\}$, results in the largest variance, compared to any other $k$-dimensional subspace, $Z_{k}$.

### 6.9
Show that the squared Frobenius norm is equal to the sum of the squared singular values.

### 6.10
Show that the best $k$-rank approximation of a matrix $X$ of rank $r > k$, in the Frobenius norm sense, is given by

$$
\widehat{X} = \sum_{i=1}^{k} \sigma_{i} \mathbf{u}_{i} \mathbf{v}_{i}^{T},
$$

where $\sigma_{i}$ are the singular values and $\mathbf{v}_{i}, \mathbf{u}_{i}, i = 1, 2, \dots, k$ are the corresponding right and left singular vectors of $X$, respectively. Then show that the approximation error is given by

$$
\sqrt{\sum_{i=k+1}^{r} \sigma_{i}^{2}}.
$$

### 6.11
Show that $\widehat{X}$, as given in Problem 6.10, also minimizes the spectral norm and that

$$
||X - \widehat{X}||_{2} = \sigma_{k+1}.
$$

### 6.12
Show that the Frobenius and spectral norms are unaffected by multiplication with orthogonal matrices, i.e.,

