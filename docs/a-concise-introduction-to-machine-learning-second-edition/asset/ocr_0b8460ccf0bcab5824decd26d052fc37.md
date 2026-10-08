This distribution has a larger kurtosis than the normal distribution, often displayed in real world applications. Hyväräinen et al. (2001) give a thorough treatment of ICA. In this text, however, we continue to assume that u has a normal distribution.

The linear transformation of a normally distributed variable is also normally distributed with matrix $\mathbf{W} + \mathbf{W}^	op$. Since $\mathbf{S}$ is symmetric, $\mathbf{WW}$ orthogonal can be diagonalized by a $\mathbf{K}\mathbf{K}^	op$ orthogonal matrix $\mathbf{WSW}^	op$ such that $\mathbf{S} = \mathbf{QDQ}^	op$, where $\mathbf{D}$ is a $K \times K$ diagonal matrix with positive entries, since $\mathbf{S}$ is positive definite. If $\mathbf{S}$ had an eigenvalue 0, the dimension of the space $\mathbf{u}$ could be reduced further, because alone loses information in the data. The covariance matrix can then be written as $[\mathbf{W}^{1/2}(\mathbf{W}^	op)^{1/2}]^2$. Thus we can assume without loss of generality $\mathbf{S}=\mathbf{I}$, since this assumption results in a different $\mathbf{W}$ to consider. Since $\mathbf{Q}$ is an orthogonal matrix and orthogonality is preserved when multiplying by an orthogonal matrix, we continue to assume that the columns of $\mathbf{W}$ are orthogonal. The multiplication by $\mathbf{D}^{1/2}$ only results in a scaling and thus the columns of $\mathbf{W}$ remain orthogonal. Equally, we can assume zero mean for $\mathbf{u}$, since no nonzero mean can be absorbed in $\mathbf{m}$.

```
$$\mathbf{v} \sim \mathcal{N}(\mathbf{m}, \mathbf{WW}^	op + \sigma^2\mathbf{I}).$$
```

Let $\mathbf{C} = \mathbf{WW}^	op + \sigma^2\mathbf{I}$. The likelihood of the dataset $\mathcal{D} ={\mathbf{v}_1, \dots, \mathbf{v}_N\}$ is given

```
$$\prod_{n=1}^N \frac{1}{\sqrt{2\pi|\mathbf{C}|}} \exp\left(-\frac{1}{2}(\mathbf{v}_n - \mathbf{m})^	op\mathbf{C}^{-1}(\mathbf{v}_n - \mathbf{m})\right).$$
```

```
$$\mathcal{L} = -\frac{ND}{2}\log(2\pi) - \frac{N}{2}\log|\mathbf{C}| - \sum_{n=1}^N (\mathbf{v}_n - \mathbf{m})^	op\mathbf{C}^{-1}(\mathbf{v}_n - \mathbf{m}).$$
```

Using A.2.3, the derivative with respect to $\mathbf{m}$ is

```
$$\frac{\partial}{\partial\mathbf{m}}\mathcal{L} = \sum_{n=1}^N \mathbf{C}^{-1}(\mathbf{v}_n - \mathbf{m}) = \mathbf{C}^{-1}\left[\sum_{n=1}^N (\mathbf{v}_n - \mathbf{m})\right].$$
```

This can be only zero, if

```
$$\mathbf{m} = \frac{1}{N}\sum_{n=1}^N \mathbf{v}_n = \mathbf{\mu}.$$
```

Hence, the sample mean $\mathbf{\mu}$ is the Maximum-Likelihood Estimate for $\mathbf{m}$ and we insert this into the expression for $\mathcal{L}$.