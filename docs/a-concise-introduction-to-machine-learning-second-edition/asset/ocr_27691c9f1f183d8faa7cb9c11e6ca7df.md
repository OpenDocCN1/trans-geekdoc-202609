finite, in which case $\alpha_i$ is updated to this value. Note that in when the optimal $\alpha_i$ is infinite and $d_i(x)$ is already excluded from the model, no action is necessary. In all cases, $\Sigma$ and its inverse $C$ have to be updated, since $A$ has changed.

The matrices $\mathbf{D}$ and $\Sigma$ change during the run of the algorithm. However, they stay comparatively small compared to the number $M$ of basis functions in the dictionary and the sample number $N$. The matrix $\mathbf{C}$ is subject to rank 1 updates as basis functions are added, deleted or their hyperparameters re-estimated. These rank 1 updates are the addition or subtraction of the outer product of the basis function evaluated at the sample points with itself derived from the hyperparameter updates. However, in practice $C$ and inverse are not calculated.

It should be noted here that the dictionary of basis functions does not need to be static; a new basis function can be created, evaluated, and possibly added to the model at any point.

In the update formula, where the logarithm of the marginal likelihood $\mathcal{L}$ is denoted by $\Delta\mathcal{L}$ and updated quantities are denoted by a

**Addition:** In this case,

```
$$\Delta\mathcal{L} = \frac{Q_i^2}{S_i} + \log \frac{S_i}{Q_i^2}$
```

```
$$\hat{\Sigma} = \left( \Sigma + \sigma^{-2}\Sigma_{ii}\mathbf{D}_i^T\mathbf{D}_i - \sigma^{-2}\Sigma_{ii}\mathbf{D}_i^T\mathbf{\Sigma} / \Sigma_{ii} \right)$
```

```
$$\hat{\mu} = \left( \mu_i - \sigma^{-2}\mu_i\mathbf{\Sigma}^T\mathbf{D}_i / \Sigma_{ii} \right)$
```

where $\Sigma_{ii} = (\alpha_i + S_i)^{-1}$ and $\mu_i = \Sigma_{ii}Q_i$.

**Deletion:** The index $j$ denotes the column of $\mathbf{D}$ which is to be removed, when $d_j$ is removed from the current model. $\Sigma_j$ is the $j^{th}$ element of $\Sigma$ and $\Sigma_{ij}$ is the $j^{th}$ element of $\mu$ is $\mu_j$.

```
$$\Delta\mathcal{L} = \frac{Q_j^2}{S_j} - \log \left(1 - \frac{S_j}{\alpha_j} \right)$
```

```
$$\hat{\Sigma} = \Sigma - \frac{1}{\Sigma_{jj}}\Sigma_j\mathbf{\Sigma}_T^T$$
```

```
$$\hat{\mu} = \mu - \frac{\mu_j}{\Sigma_{jj}}\mathbf{\Sigma}_j$
```

After these updates the $j^{th}$ row and column needs to be removed from $\Sigma$ and the $j^{th}$ element from $\mu$.

**Re-estimation:** Defining

```
$$\kappa_j = (\Sigma_{jj} + (\tilde{\alpha}_i - \alpha_i)^{-1})^{-1}$
```