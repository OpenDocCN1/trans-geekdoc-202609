# 6.1.2.8 Projection onto probability simplex

Let \(\mathcal{C} = \{\boldsymbol{x} : \boldsymbol{x} \ge 0, \sum_{d=1}^D x_d = 1\} = \mathbb{S}_D\) be the probability simplex in \(D\) dimensions. We can project onto this using

\(\text{proj}_\mathcal{C}(\boldsymbol{x}) = (\boldsymbol{x} - v\mathbf{1})_+\) (6.33)

The value \(v \in \mathbb{R}\) must be found using bisection search. See [PB+14, p.183] for details. This is useful for optimizing over discrete probability distributions.

# 6.1.3 Proximal point methods (PPM)

A proximal point method (PPM), also called a proximal minimization algorithm, iteratively applies the following update:

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \mathcal{L}}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \mathcal{L}(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.34)

where we assume \(\mathcal{L} : \mathbb{R}^n \to \mathbb{R} \cup \{+\infty\}\) is a closed proper convex function. The advantage of this method over minimizing \(\mathcal{L}\) directly is that sometimes adding quadratic regularization can improve the conditioning of the problem, and hence speed convergence.

# 6.1.3.1 Stochastic and incremental PPM

PPM can be extended to the stochastic setting, where the goal is to optimize \(\mathcal{L}(\boldsymbol{\theta}) = \mathbb{E}_{q(\boldsymbol{z})} [\ell(\boldsymbol{\theta}, \boldsymbol{z})]\), by using the following stochastic update:

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \ell_t}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \ell_t(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.35)

where \(\ell_t(\boldsymbol{\theta}) = \ell(\boldsymbol{\theta}, \boldsymbol{z}_t)\) and \(\boldsymbol{z}_t \sim q\). The resulting method is known as stochastic PPM (see e.g., [PN18]). If \(q\) is the empirical distribution associated with a finite-sum objective, this is called the incremental proximal point method [Ber15]. It is often more stable than SGD.

In the case where the cost function is a linear least squares problem, one can show [AEMI18] that the IPPM is equivalent to the Kalman filter (??), where the posterior mean is equal to the current parameter estimate, \(\boldsymbol{\theta}_t\). The advantage of this probabilistic perspective is that it also gives us the posterior covariance, which can be used to define a variable-metric distance function inside the prox operator, as in Equation (6.7). We can extend this to nonlinear problems using the extended KF (??).

# 6.1.3.2 SGD is PPM on a linearized objective

We now show that SGD is PPM on a linearized objective. To see this, let the approximation at the current iterate be

\(\hat{\ell}_t(\boldsymbol{\theta}) = \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\) (6.36)

where \(\boldsymbol{g}_t = \nabla_\boldsymbol{\theta} \ell_t(\boldsymbol{\theta}_t)\). Now we compute a proximal update to this approximate objective:

\(\boldsymbol{\theta}_{t+1} = \text{prox}_{\eta_t \hat{\ell}_t}(\boldsymbol{\theta}_t) = \text{argmin}_\boldsymbol{\theta} \hat{\ell}_t(\boldsymbol{\theta}) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2\) (6.37)

We have

\(\nabla_\boldsymbol{\theta} \left[ \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\mathsf{T}(\boldsymbol{\theta} - \boldsymbol{\theta}_t) + \frac{1}{2\eta_t}||\boldsymbol{\theta} - \boldsymbol{\theta}_t||_2^2 \right] = \boldsymbol{g}_t + \frac{1}{\eta_t}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\) (6.38)

Setting the gradient to zero yields the SGD step \(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta_t \boldsymbol{g}_t\).