![](bbox=[0.235, 0.197, 0.762, 0.335])

(a) Viewing the plane spanned by two principal components.

(b) Viewing the data along one of the principal components.

Figure 7.6: Probabilistic Principal Component Analysis for three-dimensional data.

In other words, $\sigma^2$ is the average of all the other eigenvalues apart from $\lambda_1,...,\lambda_K$. As mentioned before, $\sigma^2$ explains the data protruding beyond the $K$-dimensional subspace of the feature space. This needs to be as small as possible. Therefore $\lambda_1\lambda_K$ are chosen to be the $K$ largest eigenvalues of $\Sigma$. The value of $K$ itself is chosen such that $\sigma^2$ is acceptably small. The likelihood takes value

```
$$\mathcal{L} = -\frac{N}{2}[D\log(2\pi) + (D-K)\log(\frac{1}{D-K}\sum_{k=K+1}^D \lambda_k^2) + \sum_{k=1}^K \log \lambda_k + D)]$$
```

Figure 7.6 illustrates the concepts. The data is viewed from two angles, first looking onto the plane spanned by the two principal components and secondly looking along one of the principal components. The latter angle shows that not all data points lie in the plane of the two principal components. The noise variance $\sigma^2$ explains this deviation and is equal to the smallest eigenvalue of the sample covariance matrix of this data.

In this section we derived PCA by maximizing the likelihood. More generally, Raviri et al. (2023) show that many techniques for dimensionality reduction optimize a lower bound of the likelihood. The method in the next section utilises this lower bound to maximize the likelihood iteratively.

# 7.3 Expectation-Maximization

The previous section was based on the assumption that the data samples $\mathbf{v}_1,...,\mathbf{v}_N$ are related to vectors in a lower dimensional space via a linear mapping given by (7.2) with additive Gaussian noise with zero mean and covariance matrix $\sigma^2I$. Therefore, each $\mathbf{v}_n$ follows a conditional normal distribution with mean $\mathbf{Wu}_n + \mathbf{m}$ and covariance matrix $\sigma^2I$, where $n=1,...,N$,