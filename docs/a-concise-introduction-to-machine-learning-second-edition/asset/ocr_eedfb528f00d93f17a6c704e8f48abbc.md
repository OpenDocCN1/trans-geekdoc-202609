| degree | $x^5$ | $x^4$ | $x^3$ | $x^2$ | $x$ | 1 |
|---|---|---|---|---|---||}{
| 0 | 0 | 0 | 0 | 0 | 0 | 0.0092 |
| 1 | 0 | 0 | 0 | 0 | 1.0 | -0.501 |
| 2 | 0 | 0 | 0 | 0.079 | 0.92 | -0.49 |
| 3 | 0 | 0 | 4.8 | -0.61 | 1.1 | -0.49 |
| 4 | 0 | -1.5 | | -4.2 | | -0.61 |
| 5 | -63 | 163 | -164 | 81 | -19 | 1.5 |

The coefficients of the linear average polynomial are nearly the true solution $x-0.5$, and the even quadratic polynomial gets close to the true solution with a relatively small coefficient of $x^2$. The large coefficients in the high order polynomials indicate that a lot of bending is necessary to fit the training data. It is worth looking at the variance of the coefficients:

| | $x^5$ | $x^4$ | $x^3$ | $x^2$ | $x$ | 1 |
|---|---|---|---|---|---||}{
| 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0.01 | 0.0035 |
| 2 | 0 | 0 | 0 | 0.42 | 0.051 | 0.033 |
| 3 | 0 | 0 | 0.50 | 31.9 | 9.03 | 0.3 |
| 4 | 0 | 1227 | 5030 | 2869 | 324.1 | 5.3 |
| 5 | 338000 | 216000 | 182900 | 39548 | 20873 | 182.1 |

With increasing complexity of the model, the models for different datasets become very different, showing that the models are susceptible to small changes in the training data. Too much complexity leads to overfitting and a large variance in the models. These can be separated formally.

We need to generalize to all datasets. This means looking at the expected error that a particular model space gives rise to. Given a model space, let $f(\mathbf{x})$ be an approximation to the underlying process generating the data by $\mathbf{t}(\mathbf{x})$. It is common to look at the expected squared

> $E[(\mathbf{t}(\mathbf{x}) - f(\mathbf{x}))^2]$

where $\mathbf{t}(\mathbf{x}) = \mathbf{f}(\mathbf{x}) + \epsilon$. In the following, this is decomposed into error components.

Now $\mathbf{t}(\mathbf{x})$ is a deterministic process, and $\mathbb{E}[\mathbf{t}(\mathbf{x})]=\mathbf{t}(\mathbf{x})$, which implies $\mathbb{E}[\mathbf{f}(\mathbf{x})]=\mathbf{f}(\mathbf{x})$, since the noise has zero mean. Similarly,

```
\text{var}[\mathbf{t}] = \mathbb{E}[(\mathbf{t}(\mathbf{x}) - \mathbb{E}[\mathbf{t}(\mathbf{x})])^2] \n\mathbb{E}[(\mathbf{f}(\mathbf{x}))^2] = \text{var}[\mathbf{f}(\mathbf{x})] + \mathbb{E}[\epsilon^2] = \sigma^2$.
```

Contrary to $\mathbf{t}(\mathbf{x})$, $\mathbf{f}(\mathbf{x})$ is not deterministic, because it depends on the dataset which was used to calculate the model. However, it is independent of