
$$
\widehat{\boldsymbol{\theta}} = \arg\min_{\boldsymbol{\theta} \in \mathbb{R}^{l}} \left( \sum_{n=1}^{N} \left( y_n - \mathbf{x}_n^T \boldsymbol{\theta} \right)^2 + \lambda \lVert \boldsymbol{\theta} \rVert_1 \right) = \arg\min_{\boldsymbol{\theta} \in \mathbb{R}^{l}} \left( \left( \mathbf{y} - X\boldsymbol{\theta} \right)^T \left( \mathbf{y} - X\boldsymbol{\theta} \right) + \lambda \lVert \boldsymbol{\theta} \rVert_1 \right).
$$

![Equation](images/B9780443292385000159/si47.png) (9.6)

Following the discussion with respect to the bias term given in Section [3.8](#Chp003_65-117_B9780443292385000093.xhtml) and in order to simplify the analysis, we will assume hereafter, without harming generality, that the data are of zero mean values. If this is not the case, the data can be centered by subtracting their respective sample means.

It turns out that the task in Eq. [(9.6)](#Chp009_417-462_B9780443292385000159.xhtml#deq8) can be equivalently written in the following two formulations:

$$
\widehat{\boldsymbol{\theta}}: \quad \min_{\boldsymbol{\theta} \in \mathbb{R}^{l}} \left( \mathbf{y} - X\boldsymbol{\theta} \right)^T \left( \mathbf{y} - X\boldsymbol{\theta} \right), \quad \text{s.t.} \quad \lVert \boldsymbol{\theta} \rVert_1 \leq \rho,
$$

![Equation](images/B9780443292385000159/si48.png) (9.7)

or
