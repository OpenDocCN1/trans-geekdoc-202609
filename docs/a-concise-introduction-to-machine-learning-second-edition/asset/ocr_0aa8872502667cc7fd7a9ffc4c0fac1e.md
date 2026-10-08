Seek the largest $K$ eigenvalues $\lambda_k$ of $\mathbf{\Sigma}$ with corresponding eigenvectors $\mathbf{w}_k, k=1, \dots, K$. Using the above expression for $\mathbf{\Sigma}$, these vectors satisfy

$$\Phi(I - \frac{1}{N}\mathbf{E})\mathbf{\Phi}^T\mathbf{w}_k = N\lambda_k\mathbf{w}_k$

Multiplying through with $(I - \frac{1}{N}\mathbf{E})\mathbf{\Phi}^T$ from the left and using the idempotence of $I - \frac{1}{N}\mathbf{E}$, this becomes

$$(I - \frac{1}{N}\mathbf{E})\mathbf{\Phi}^T\mathbf{\Phi}(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k = N\lambda_k(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k.$$

Here the vector

$$\mathbf{w}_k = (I - \frac{1}{N}\mathbf{E})\mathbf{w}_k \quad (7.14)$

is an eigenvector of $(I - \frac{1}{N}\mathbf{E})$, symmetric matrix $\mathbf{\Phi}^T\mathbf{\Phi}(I - \frac{1}{N}\mathbf{E})$ with eigenvalue $\lambda_k = N\lambda_k$. Note, that due to $I - \frac{1}{N}\mathbf{E}$ being idempotent, we have $(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k = \mathbf{w}_k$. Thus, the components of the sum reduce to
$(i, j)$ entry of $\mathbf{w}_k$ is the inner product

$$\phi(v_i)^T\phi(v_j) = k(v_i, v_j).$$

**K = $\mathbf{\Phi}^T\mathbf{\Phi}$ is the *kernel matrix*. *Kernel Principal Component Analysis* calculates the eigenvalues $N\lambda_k$ and eigenvectors $\mathbf{w}_k$ of $(I - \frac{1}{N}\mathbf{E})\mathbf{\Phi}^T\mathbf{\Phi}(I - \frac{1}{N}\mathbf{E})$ from (7.14) from the left with $/N$, gives Equation

$$\mathbf{w}_k = \frac{1}{N}\mathbf{\Phi}(I - \frac{1}{N}\mathbf{E})\mathbf{\Phi}^T\mathbf{w}_k = \lambda_k\mathbf{w}_k.$

Hence, $\mathbf{w}_k$ is a linear combination of the images $\phi(v_1), \dots, \phi(v_N)$,

$$\mathbf{w}_k = \frac{1}{N}\sum_{n=1}^N \mathbf{w}_n\phi(v_n),$

$\ar{w}_k, n=1, \dots, N$, are the coefficients of $\mathbf{w}_k$. In practice, this calculation is never done, since we are only interested in expressing any data point $v$ in the basis formed by the principal components, i.e. the value of the projections

$$\mathbf{w}_k^T\phi(v) = \frac{1}{N\lambda_k}\mathbf{\Phi}^T\phi(v) = \frac{1}{N\lambda_k}\phi(v_1)^T\phi(v) \vdots \ \phi(v_N)^T\phi(v)$

$$\mathbf{w}_k = \frac{1}{N\lambda_k}k(v_1, v_k) \vdots \ k(v_N, v_k)$

It remains to specify the length of $\mathbf{w}_k$. The principal components have length one, this translates into a condition on the length of $\mathbf{w}_k$.

$$\1 = \mathbf{w}_k^T\mathbf{w}_k = \frac{1}{(N\lambda_k)^2}\mathbf{w}_k^T\mathbf{\Phi}^T\mathbf{\Phi}\mathbf{w}_k,$

$= \frac{1}{(N\lambda_k)^2}\mathbf{w}_k^T(I - \frac{1}{N}\mathbf{E})\mathbf{K}(I - \frac{1}{N}\mathbf{E})\mathbf{w}_k = \frac{1}{N\lambda_k}\mathbf{w}_k^T\mathbf{w}_k,$