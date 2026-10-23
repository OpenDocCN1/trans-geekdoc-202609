This method is known as **projected gradient descent**. See Fig. 5.15 for an illustration.

For example, consider the box constraints $\mathcal{C} = \{\boldsymbol{\theta} : \mathbf{l} \le \boldsymbol{\theta} \le \mathbf{u}\}$. The projection operator in this case can be computed elementwise by simply thresholding at the boundaries:

$$\operatorname{proj}_{\mathcal{C}}(\boldsymbol{\theta})_d = \begin{cases} l_d & \text{if } \theta_k \le l_k \\ x_d & \text{if } l_k \le \theta_k \le u_k \\ u_d & \text{if } \theta_k \ge u_k \end{cases}\tag{5.125}$$

For example, if we want to ensure all elements are non-negative, we can use

$$\operatorname{proj}_{\mathcal{C}}(\boldsymbol{\theta}) = \boldsymbol{\theta}_+ = [\max(\theta_1,0),\dots,\max(\theta_D,0)]\tag{5.126}$$

See Sec. 11.5.9.2 for an application of this method to sparse linear regression.

# 5.6.2 Proximal operator for $\ell_1$-norm regularizer

Consider a linear predictor of the form $f(\mathbf{x};\boldsymbol{\theta}) = \sum_{d=1}^D \theta_d x_d$. If we have $\theta_d = 0$ for any dimension $d$, we ignore the corresponding feature $x_d$. This is a form of **feature selection**, which can be useful both as a way to reduce overfitting as well as to improve model interpretability. We can encourage weights to be zero (and not just small) by penalizing the $\ell_1$ norm,

$$||\boldsymbol{\theta}||_1 = \sum_{d=1}^D |\theta_d|\tag{5.127}$$

This is called a **sparsity inducing regularizer.**

To see why this induces sparsity, consider two possible parameter vectors, one which is sparse, $\boldsymbol{\theta} = (1,0)$, and one which is non-sparse, $\boldsymbol{\theta}' = (1/\sqrt{2},1/\sqrt{2})$. Both have the same $\ell_2$ norm

$$||(1,0)||_2^2 = ||(1/\sqrt{2},1/\sqrt{2})||_2^2 = 1\tag{5.128}$$

Hence $\ell_2$ regularization (Sec. 4.4.3) will not favor the sparse solution over the dense solution. However, when using $\ell_1$ regularization, the sparse solution is cheaper, since

$$||(1,0)||_1 = 1 < ||(1/\sqrt{2},1/\sqrt{2})||_1 = \sqrt{2}\tag{5.129}$$

See Sec. 11.5 for more details on sparse regression.

If we combine this regularizer with our smooth loss, we get

$$\mathcal{L}(\boldsymbol{\theta}) = \text{NLL}(\boldsymbol{\theta}) + \lambda ||\boldsymbol{\theta}||_1\tag{5.130}$$

We can optimize this objective using proximal gradient descent. The key question is how to compute the prox operator for the function $f(\boldsymbol{\theta}) = ||\boldsymbol{\theta}||_1$. Since this function decomposes over dimensions $d$, the proximal projection can be computed componentwise. We can solve each 1d problem as follows:

$$\operatorname{prox}_{\lambda f}(\theta) = \arg\min_z \lambda |z| + \frac{1}{2}(z - \theta)^2\tag{5.131}$$