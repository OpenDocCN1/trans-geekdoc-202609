# Protease Cleavage Pattern Discovery

between these two sets of centres is parameterised by the projection direction (model parameters) or the mapping weight vector w.

The uncertainty in the raw multi-dimensional data space is measured by two co-variance matrices for two classes. They are denoted by $\Sigma_1$ and $\Sigma_2$. The relationship between the mapping space variance and the raw space covariance matrices is defined below,

```
$S_W = \mathbf{w}^t(\Sigma_2 + \Sigma_1)\mathbf{w}$ (3.7)
```

Suppose the distance between two mapping centres is denoted by $	au_2 - 	au_1 = \mathbf{u}_2 - \mathbf{u}_1$. A discrimination ratio as the mapping quality associated with the discrimination power of a classifier is defined as below,

```
$R(\mathbf{w}) = \frac{S_B}{S_W} = \frac{\mathbf{w}^t(\mathbf{u}_2 - \mathbf{u}_1)}{\mathbf{w}^t(\Sigma_2 + \Sigma_1)\mathbf{w}}$ (3.8)
```

If $R(\mathbf{w})$ is optimised (maximised), the mapping vector $\mathbf{w}$ is said to be a good projection direction and is able to maximise the separation between two classes in the raw space. In the projection space, the distance between two mapping centres in the $\hat{y}$ space will be maxim and the variance of two clusters have an identical covariance matrix, hence an identical volume, i.e., $\Sigma_1 = \Sigma_2 = \Sigma$. Mapping $R(\mathbf{w})$ leads to the solution of a LDA model shown below [Duda, et al., 2000],

```
$\hat{\mathbf{w}} \propto \Sigma^{-1}(\mathbf{u}_2 - \mathbf{u}_1)$ (3.9)
```

In other words, the calculation of the mean vectors $(\mathbf{u}_1$ and $\mathbf{u}_2)$ of the covariance matrix $(\Sigma)$ leads to the solution of the estimated or optimised projection direction $(\hat{\mathbf{W}})$. A simple two-dimensional data set shown in Table 3.1 is used to demonstrate how an LDA model can be constructed using the principle discussed above. Based on this data set, the mean vectors for each class can be calculated using the equation below,

```
$\mathbf{u}_k = \frac{1}{N_k} \sum_{n=1}^{N_k} \mathbf{x}_n^k$ (3.10)
```