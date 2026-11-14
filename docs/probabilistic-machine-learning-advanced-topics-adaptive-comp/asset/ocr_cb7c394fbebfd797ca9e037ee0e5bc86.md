that all the eigenvalues are less than 1 [SBG07]. Of course, if all the eigenvalues are less than 1, then \(\mathbb{E}[\boldsymbol{z}_t] = \mathbf{0}\) for large \(t\), so the state will return to the origin. Fortunately, when we add noise, the state becomes non-zero, so the model does not degenerate.

# 29.8.4 Bayesian LDS

SSMs can be quite sensitive to their parameter values, which is a particular concern when they are used for forecasting applications (see Section 29.12.1), or when the latent states or parameters are interpreted for scientific purposes (see e.g., [AM+16]). In such cases, it is wise to represent our uncertainty about the parameters by using Bayesian inference.

There are various algorithms we can use to perform this task. For linear-Gaussian SSMs, it is possible to use variational Bayes EM [Bea03; BC07] (see Section 10.3.5), or blocked Gibbs sampling (see Section 29.8.4.1). Note, however, that \(\boldsymbol{\theta}\) and \(\boldsymbol{z}\) are highly correlated, so the mean field approximation can be inaccurate, and the blocked Gibbs method can mix slowly. It is also possible to use collapsed MCMC in which we marginalize out \(\boldsymbol{z}_{1:T}\) and just work with \(p(\boldsymbol{\theta}|\boldsymbol{y}_{1:T})\), which we can sample using HMC.

# 29.8.4.1 Blocked Gibbs sampling for LDS

This section is written by Xinglong Li.

In this section, we discuss blocked Gibbs sampling for LDS [CK94b; CMR05; FS07]. We alternate between sampling from \(p(\boldsymbol{z}_{1:T}|\boldsymbol{y}_{1:T}, \boldsymbol{\theta})\) using the forwards-filter backwards-sampling algorithm (Section 8.2.3.5), and sampling from \(p(\boldsymbol{\theta}|\boldsymbol{z}_{1:T}, \boldsymbol{y}_{1:T})\), which is easy to do if we use conjugate priors.

In more detail, we will consider the following linear Gaussian state space model with homogeneous parameters:

```
\(p(\boldsymbol{z}_t|\boldsymbol{z}_{t-1}, \boldsymbol{u}_t) = \mathcal{N}(\boldsymbol{z}_t|\mathbf{F}\boldsymbol{z}_{t-1} + \mathbf{B}\boldsymbol{u}_t, \mathbf{Q})\quad\)(29.110)
\(p(\boldsymbol{y}_t|\boldsymbol{z}_t, \boldsymbol{u}_t) = \mathcal{N}(\boldsymbol{y}_t|\mathbf{H}\boldsymbol{z}_t + \mathbf{D}\boldsymbol{u}_t, \mathbf{R})\quad\)(29.111)
```

The set of all the parameters is \(\boldsymbol{\theta} = \{\mathbf{F}, \mathbf{H}, \mathbf{B}, \mathbf{D}, \mathbf{Q}, \mathbf{R}\}\). For the sake of simplicity, we assume that the regression coefficient matrix \(\mathbf{B}\) and \(\mathbf{D}\) include the intercept term (i.e., the last entry of \(\boldsymbol{u}_t = 1\)).

We use conjugate MNIW priors, as in Bayesian multivariate linear regression Section 15.2.9. Specifically,

```
\(p(\mathbf{Q}, [\mathbf{F}, \mathbf{B}]) = \text{MNIW}(\mathbf{M}_{z0}, \mathbf{V}_{z0}, \nu_{q0}, \Psi_{q0})\quad\)(29.112)
\(p(\mathbf{R}, [\mathbf{H}, \mathbf{D}]) = \text{MNIW}(\mathbf{M}_{y0}, \mathbf{V}_{y0}, \nu_{r0}, \Psi_{r0})\quad\)(29.113)
```

Given \(\boldsymbol{z}_{1:T}, \boldsymbol{u}_{1:T}\) and \(\boldsymbol{y}_{1:T}\), the posteriors are also MNIW. Specifically,

```
\(\mathbf{Q}|\boldsymbol{z}_{1:T}, \boldsymbol{u}_{1:T} \sim \text{IW}(\nu_{q1}, \Psi_{q1})\quad\)(29.114)
\([\mathbf{F}, \mathbf{B}]|\mathbf{Q}, \boldsymbol{z}_{1:T}, \boldsymbol{u}_{1:T} \sim \mathcal{MN}(\mathbf{M}_{z1}, \mathbf{Q}, \mathbf{V}_{z1})\quad\)(29.115)
```

where the set of hyperparameters \(\{\mathbf{M}_{z1}, \mathbf{V}_{z1}, \nu_{q1}, \Psi_{q1}\}\) of the posterior MNIW can be obtained by replacing \(\mathbf{Y}, \mathbf{A}, \mathbf{X}\) in Equation (15.105) with \(\boldsymbol{z}_{2:T}, [\mathbf{F}, \mathbf{B}]\), and \([\boldsymbol{z}_{t-1}^T, \boldsymbol{u}_t^T]_{t=2:T}^T\), respectively. Similarly,

```
\(\mathbf{R}|\boldsymbol{z}_{1:T}, \boldsymbol{u}_{1:T}, \boldsymbol{y}_{1:T} \sim \text{IW}(\nu_{r1}, \Psi_{r1})\quad\)(29.116)
\([\mathbf{H}, \mathbf{D}]|\mathbf{R}, \boldsymbol{z}_{1:T}, \boldsymbol{u}_{1:T}, \boldsymbol{y}_{1:T} \sim \mathcal{MN}(\mathbf{M}_{y1}, \mathbf{R}, \mathbf{V}_{y1}),\quad\)(29.117)
```