
## 6.1.2.1 Moreau decomposition

A useful technique for computing some kinds of proximal operators leverages a result known as **Moreau decomposition**, which states that

\(\boldsymbol{x} = \text{prox}_f(\boldsymbol{x}) + \text{prox}_{f^*}(\boldsymbol{x}) \quad (6.18)\)

where \(f^*\) is the convex conjugate of \(f\) (see Section 6.5).

For example, suppose \(f = || \cdot ||\) is a general norm on \(\mathbb{R}^D\). It can be shown that \(f^* = I_{\mathcal{B}}\), where

\(\mathcal{B} = \{ \boldsymbol{x} : ||\boldsymbol{x}||^* \le 1 \} \quad (6.19)\)

is the unit ball for the dual norm \(|| \cdot ||^*\), defined by

\(||\boldsymbol{z}||^* = \sup \{ \boldsymbol{z}^T \boldsymbol{x} : ||\boldsymbol{x}|| \le 1 \} \quad (6.20)\)

Hence

\(\text{prox}_{\lambda f}(\boldsymbol{x}) = \boldsymbol{x} - \lambda \text{prox}_{f^*/\lambda}(\boldsymbol{x}/\lambda) = \boldsymbol{x} - \lambda \text{proj}_{\mathcal{B}}(\boldsymbol{x}/\lambda) \quad (6.21)\)

Thus there is a close connection between proximal operators of norms and projections onto norm balls that we will leverage below.

## 6.1.2.2 Projection onto box constraints

Let \(\mathcal{C} = \{ \boldsymbol{x} : \boldsymbol{l} \le \boldsymbol{x} \le \boldsymbol{u} \}\) be a box or hyper-rectangle, imposing lower and upper bounds on each element. (These bounds can be infinite for certain elements if we don't want to constrain values along that dimension.) The projection operator is easy to compute elementwise by simply thresholding at the boundaries:

\(\text{proj}_{\mathcal{C}}(\boldsymbol{x})_d = \begin{cases} l_d & \text{if } x_d \le l_d \\ x_d & \text{if } l_d \le x_d \le u_d \\ u_d & \text{if } x_d \ge u_d \end{cases} \quad (6.22)\)

For example, if we want to ensure all elements are non-negative, we can use

\(\text{proj}_{\mathcal{C}}(\boldsymbol{x}) = \boldsymbol{x}_+ = [\max(x_1, 0), \dots, \max(x_D, 0)] \quad (6.23)\)

## 6.1.2.3 \(\ell_1\) norm

Consider the 1-norm \(f(\boldsymbol{x}) = ||\boldsymbol{x}||_1\). The proximal projection can be computed componentwise. We can solve each 1d problem as follows:

\(\text{prox}_{\lambda f}(x) = \underset{z}{\text{argmin}} \lambda |z| + \frac{1}{2}(z-x)^2 \quad (6.24)\)

One can show that the solution to this is given by

\(\text{prox}_{\lambda f}(x) = \begin{cases} x - \lambda & \text{if } x \ge \lambda \\ 0 & \text{if } |x| \le \lambda \\ x + \lambda & \text{if } x \le -\lambda \end{cases} \quad (6.25)\)

This is known as the **soft thresholding operator**, since values less than \(\lambda\) in absolute value are set to 0 (thresholded), but in a differentiable way. This is useful for enforcing sparsity. Note that soft thresholding can be written more compactly as

\(\text{SoftThreshold}_\lambda(x) = \text{sign}(x) (|x| - \lambda)_+ \quad (6.26)\)

where \(x_+ = \max(x, 0)\) is the positive part of \(x\). In the vector case, we define \(\text{SoftThreshold}_\lambda(\boldsymbol{x})\) to be elementwise soft thresholding.

## 6.1.2.4 $\ell_2$ norm

Now consider the $\ell_2$ norm $f(\boldsymbol{x}) = \|\boldsymbol{x}\|_2 = \sqrt{\sum_{d=1}^D x_d^2}$. The dual norm for this is also the $\ell_2$ norm. Projecting onto the corresponding unit ball $\mathcal{B}$ can be done by simply scaling vectors that lie outside the unit sphere:

$\text{proj}_{\mathcal{B}}(\boldsymbol{x}) = \begin{cases} \frac{\boldsymbol{x}}{\|\boldsymbol{x}\|_2} & \|\boldsymbol{x}\|_2 > 1 \\ \boldsymbol{x} & \|\boldsymbol{x}\|_2 \le 1 \end{cases}$ (6.27)

Hence by the Moreau decomposition we have

$\text{prox}_{\lambda f}(\boldsymbol{x}) = (1 - \lambda/\|\boldsymbol{x}\|_2)_+\boldsymbol{x} = \begin{cases} (1 - \frac{\lambda}{\|\boldsymbol{x}\|_2})\boldsymbol{x} & \text{if } \|\boldsymbol{x}\|_2 \ge \lambda \\ 0 & \text{otherwise} \end{cases}$ (6.28)

This will set the whole vector to zero if its $\ell_2$ norm is less than $\lambda$. This is therefore called **block soft thresholding**.

## 6.1.2.5 Squared $\ell_2$ norm

Now consider using the _squared_ $\ell_2$ norm (scaled by 0.5), $f(\boldsymbol{x}) = \frac{1}{2}\|\boldsymbol{x}\|_2^2 = \frac{1}{2} \sum_{d=1}^D x_d^2$. One can show that

$\text{prox}_{\lambda f}(\boldsymbol{x}) = \frac{1}{1 + \lambda}\boldsymbol{x}$ (6.29)

This reduces the magnitude of the $\boldsymbol{x}$ vector, but does not enforce sparsity. It is therefore called the **shrinkage operator**.

More generally, if $f(\boldsymbol{x}) = \frac{1}{2}\boldsymbol{x}^\mathbf{T}\mathbf{A}\boldsymbol{x} + \boldsymbol{b}^\mathbf{T}\boldsymbol{x} + c$ is a quadratic, with **A** being positive definite, then

$\text{prox}_{\lambda f}(\boldsymbol{x}) = (\mathbf{I} + \lambda\mathbf{A})^{-1}(\boldsymbol{x} - \lambda\boldsymbol{b})$ (6.30)

A special case of this is if $f$ is affine, $f(\boldsymbol{x}) = \boldsymbol{b}^\mathbf{T}\boldsymbol{x} + c$. Then we have $\text{prox}_{\lambda f}(\boldsymbol{x}) = \boldsymbol{x} - \lambda\boldsymbol{b}$. We saw an example of this in Equation (6.12).

## 6.1.2.6 Nuclear norm

The **nuclear norm**, also called the **trace norm**, of an $m \times n$ matrix **A** is the $\ell_1$ norm of its singular values: $f(\mathbf{A}) = \|\mathbf{A}\|_* = \|\boldsymbol{\sigma}\|_1$. Using this as a regularizer can result in a low rank matrix. The proximal operator for this is defined by

$\text{prox}_{\lambda f}(\mathbf{A}) = \sum_i (\sigma_i - \lambda)_+ \boldsymbol{u}_i \boldsymbol{v}_i^\mathbf{T}$ (6.31)

where $\mathbf{A} = \sum_i \sigma_i \boldsymbol{u}_i \boldsymbol{v}_i^T$ is the SVD of **A**. This operation is called **singular value thresholding**.

## 6.1.2.7 Projection onto positive definite cone

Consider the cone of positive semidefinite matrices $\mathcal{C}$, and let $f(\mathbf{A}) = I_{\mathcal{C}}(\mathbf{A})$ be the indicator function. The proximal operator corresponds to projecting **A** onto the cone. This can be computed using

$\text{proj}_{\mathcal{C}}(\mathbf{A}) = \sum_i (\lambda_i)_+ \boldsymbol{u}_i \boldsymbol{u}_i^\mathbf{T}$ (6.32)

where $\sum_i \lambda_i \boldsymbol{u}_i \boldsymbol{u}_i^\mathbf{T}$ is the eigenvalue decomposition of **A**. This is useful for optimizing psd matrices.

## 6.1.2.8 Projection onto probability simplex

Let \(\mathcal{C} = \{\boldsymbol{x} : \boldsymbol{x} \ge 0, \sum_{d=1}^D x_d = 1\} = \mathbb{S}_D\) be the probability simplex in \(D\) dimensions. We can project onto this using

\(\text{proj}_\mathcal{C}(\boldsymbol{x}) = (\boldsymbol{x} - v\mathbf{1})_+\) (6.33)

The value \(v \in \mathbb{R}\) must be found using bisection search. See [PB+14, p.183] for details. This is useful for optimizing over discrete probability distributions.

## 6.1.3 Proximal point methods (PPM)

A proximal point method (PPM), also called a proximal minimization algorithm, iteratively applies the following update:

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \mathcal{L}}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \mathcal{L}(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.34)

where we assume \(\mathcal{L} : \mathbb{R}^n \to \mathbb{R} \cup \{+\infty\}\) is a closed proper convex function. The advantage of this method over minimizing \(\mathcal{L}\) directly is that sometimes adding quadratic regularization can improve the conditioning of the problem, and hence speed convergence.

## 6.1.3.1 Stochastic and incremental PPM

PPM can be extended to the stochastic setting, where the goal is to optimize \(\mathcal{L}(\boldsymbol{\theta}) = \mathbb{E}_{q(\boldsymbol{z})} [\ell(\boldsymbol{\theta}, \boldsymbol{z})]\), by using the following stochastic update:

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \ell_t}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \ell_t(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.35)

where \(\ell_t(\boldsymbol{\theta}) = \ell(\boldsymbol{\theta}, \boldsymbol{z}_t)\) and \(\boldsymbol{z}_t \sim q\). The resulting method is known as stochastic PPM (see e.g., [PN18]). If \(q\) is the empirical distribution associated with a finite-sum objective, this is called the incremental proximal point method [Ber15]. It is often more stable than SGD.

In the case where the cost function is a linear least squares problem, one can show [AEMI18] that the IPPM is equivalent to the Kalman filter (??), where the posterior mean is equal to the current parameter estimate, \(\boldsymbol{\theta}_t\). The advantage of this probabilistic perspective is that it also gives us the posterior covariance, which can be used to define a variable-metric distance function inside the prox operator, as in Equation (6.7). We can extend this to nonlinear problems using the extended KF (??).

## 6.1.3.2 SGD is PPM on a linearized objective

We now show that SGD is PPM on a linearized objective. To see this, let the approximation at the current iterate be

\(\hat{\ell}_t(\boldsymbol{\theta}) = \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\) (6.36)

where \(\boldsymbol{g}_t = \nabla_\boldsymbol{\theta} \ell_t(\boldsymbol{\theta}_t)\). Now we compute a proximal update to this approximate objective:

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \hat{\ell}_t}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \hat{\ell}_t(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.37)

We have

\(\nabla_\boldsymbol{\theta} \left[ \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{\theta} - \boldsymbol{\theta}_t) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2 \right] = \boldsymbol{g}_t + \frac{1}{\eta_t}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\) (6.38)

Setting the gradient to zero yields the SGD step \(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta_t \boldsymbol{g}_t\).
