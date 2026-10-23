Let us approximate this with a second order Taylor series expansion:

```
\mathbb{KL}\left(p_{\boldsymbol{\theta}}\|p_{\boldsymbol{\theta}'}\right) \approx -\boldsymbol{\delta}^{\top}\mathbb{E}\left[\nabla\log p_{\boldsymbol{\theta}}\left(\mathbf{x}\right)\right] - \frac{1}{2}\boldsymbol{\delta}^{\top}\mathbb{E}\left[\nabla^{2}\log p_{\boldsymbol{\theta}}\left(\mathbf{x}\right)\right]\boldsymbol{\delta} \tag{E.25}
```

Since the expected NLL is zero (from Eq. (E.6)), the first term vanishes, so we have

```
\mathbb{KL}\left(p_{\boldsymbol{\theta}}\|p_{\boldsymbol{\theta}'}\right) \approx \frac{1}{2}\boldsymbol{\delta}^{\top}\mathbf{F}(\boldsymbol{\theta})\boldsymbol{\delta} \tag{E.26}
```

where **F** is the FIM

```
\mathbf{F} = -\mathbb{E}\left[\nabla^{2}\log p_{\boldsymbol{\theta}}\left(\mathbf{x}\right)\right] = \mathbb{E}\left[\left(\nabla\log p_{\boldsymbol{\theta}}\left(\mathbf{x}\right)\right)\left(\nabla\log p_{\boldsymbol{\theta}}\left(\mathbf{x}\right)\right)^{\top}\right] \tag{E.27}
```

# ## E.3 Sampling distributions

In frequentist statistics, uncertainty is not represented by the posterior distribution of a random variable, but instead by the **sampling distribution** of an **estimator**. Let us now define these terms,

As explained in the section on decision theory in Sec. 8.1, an estimator is a decision procedure that specifies what action to take given some observed data. In the context of parameter estimation, where the action space is to return a parameter vector, we will denote this by \(\boldsymbol{\theta} = \pi(\mathcal{D})\). For example, \(\boldsymbol{\theta}\) could be the maximum likelihood estimate, the MAP estimate, or the method of moments estimate.

The sampling distribution of an estimator is the distribution of results we would see if we applied the estimator multiple times to different datasets sampled from some distribution; in the context of parameter estimation, it is the distribution of \(\boldsymbol{\theta}\), viewed as a random variable that depends on the random sample \(\mathcal{D}\). In more detail, imagine sampling \(S\) different data sets, each of size \(N\), from some true model \(p(\mathbf{x}|\boldsymbol{\theta}^{\star})\) to generate

```
\hat{\mathcal{D}}^{(s)} = \left\{ \mathbf{x}_{n} \sim p(\mathbf{x}_{n}|\boldsymbol{\theta}^{\star}) : n = 1 : N \right\} \tag{E.28}
```

We denote this by \(\mathcal{D}^{(s)} \sim \theta^{\star}\) for brevity. Now apply the estimator to each \(\mathcal{D}^{(s)}\) to get a set of estimates, \(\left\{\boldsymbol{\theta}(\mathcal{D}^{(s)})\right\}\). As we let \(S \rightarrow \infty\), the distribution induced by this set is the sampling distribution of the estimator. More precisely, we have

```
p\left(\pi(\hat{\mathcal{D}})=\boldsymbol{\theta}|\hat{\mathcal{D}} \sim \boldsymbol{\theta}^{\star}\right) \approx \frac{1}{S}\sum_{s=1}^{S}\delta(\boldsymbol{\theta}=\pi(\mathcal{D}^{(s)})) \tag{E.29}
```

In some cases, we can compute this analytically (assuming we know \(\boldsymbol{\theta}^{\star}\)), as we discuss in Sec. E.3.1, although typically we need to approximate it by Monte Carlo. In both cases, we have to deal with the issue that \(\boldsymbol{\theta}^{\star}\) is unknown, as we will discuss.

# ### E.3.1 Exact sampling distribution of the MLE

In some cases, it is possible to analytically derive the sampling distribution of an estimator. We give an example below.