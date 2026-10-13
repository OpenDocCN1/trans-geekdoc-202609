
### Pseudoinverse matrix and SVD

$X^T X v_i = \lambda_i v_i, \quad i = 1, 2, \dots, r.$

Moreover, because $X X^T$ and $X^T X$ are symmetric matrices, it is known from linear algebra that their eigenvalues are real.^[40]

$$\mathbf{u}_i = \frac{1}{\sigma_i} X \mathbf{v}_i, \quad i = 1, 2, \ldots, r.$$

Thus, we can write

$$\sum_{i=1}^{r} \sigma_i \mathbf{u}_i \mathbf{v}_i^T = X \sum_{i=1}^{r} \mathbf{v}_i \mathbf{v}_i^T = X \sum_{i=1}^{l} \mathbf{v}_i \mathbf{v}_i^T = X V V^T,$$

where we used the fact that for eigenvectors corresponding to $\sigma_i = 0 \ (\lambda_i = 0)$, $i = r+1, \dots, l$, $X \mathbf{v}_i = 0$. However, due to the orthonormality of $\mathbf{v}_i$, $i = 1, 2, \dots, l$, $V V^T = I$ and the claim in Eq. (6.14) has been proved. □
