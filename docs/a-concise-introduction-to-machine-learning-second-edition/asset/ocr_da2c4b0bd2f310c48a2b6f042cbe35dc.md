$\mathcal{N}(0,\sigma^2)$ is meaningless. The confidence we place in the predictions should only be informed by the data, and be independent of the dictionary of basis functions.

Let $\mathcal{S}$ be a subset of the samples. This could be all samples or a suitable set of neighbourhoods of $\mathbf{x}$. We estimate the probability distribution of $t_*$ to be normal with mean and variance

```
$$\begin{aligned} \hat{m} &= \text{mean}\{t_i\}, \ \mathbf{x}_i \in \mathcal{S} \ \hat{\sigma}^2 &= \text{var}\{t_i\}, \ \mathbf{x}_i \in \mathcal{S} \end{aligned}$
```

With this estimate, the expected change, when considering $x_*$, in the log

```
$$\mathbb{E}[\Delta L] = \int_{-\infty}^{\infty} \log \left( \frac{1}{\sqrt{2\pi\sigma_*^2}} \right) \int_{-\infty}^{\infty} \frac{\exp \left( \frac{(t_*-m_*)^2}{2\sigma^2} \right)}{\sqrt{2\pi\sigma^2}} dt_* = \frac{\sigma^2 + (\hat{m}-m_*)^2}{2\sigma^2}$
```

The second term is the important one. If the predictive probability distribution does not match the data in the neighbourhood, the expected change in the logarithm of the marginal likelihood is negative. This expected change creates an uncertainty map with the largest negative values being the most uncertain regions. The uncertainty map can guide the data gathering, whenever additional samples are necessary.

Next we consider the problem of collinearity. When basis functions are added to the model, collinearity can be introduced. In this case the functions of $D$ become linearly or nearly dependent. In practical terms, this means that there are infinitely many models which explain the data equally well, since linear combinations of basis functions can be exchanged for each other. For example, assume that the basis functions are derived from a kernel $k: \mathbb{R}^d \times \mathbb{R}^d \to \mathbb{R}$. That is

```
$d_j(\mathbf{x}) = k(\mathbf{x}, \mathbf{x}_j)$
```

This model space is dependent on the data. If two sampling points lie close together, then the corresponding basis functions are very similar and the corresponding columns of $D$ are nearly linearly dependent, since the basis functions are evaluated at the same sampling points. In the following we derive a technique which checks for collinearity while the algorithm is executed.

Since at initialization only one basis function is employed, the columns of $D$ are at initialization linearly independent. Assume that the columns of $D$ remained linearly independent and that $d_j(\mathbf{x})$ is a candidate basis function to be added to the model. The columns of $D$ are linearly independent,