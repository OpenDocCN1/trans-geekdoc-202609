variances [Min01a]:

\(\mu^t_{ijl} = \mu^{t-1}_{ijl} + \tau^{t-1}_{ijl} \frac{\partial \ln Z_t}{\partial \mu^{t-1}_{ijl}}\) (17.49)

\(\tau^t_{ijl} = \tau^{t-1}_{ijl} - (\tau^{t-1}_{ijl})^2 \left[ \left( \frac{\partial \ln Z_t}{\partial \mu^{t-1}_{ijl}} \right)^2 - 2 \frac{\partial \ln Z_t}{\partial \tau^{t-1}_{ijl}} \right]\) (17.50)

In the forwards pass, we compute \(Z_t\) by propagating the input \(\boldsymbol{u}_t\) through the model. Since we have a Gaussian distribution over the weights, instead of a point estimate, this induces an (approximately) Gaussian distribution over the values of the hidden units. For certain kinds of activation functions (such as ReLU), the relevant integrals (to compute the means and variances) can be solved analytically, as in GP-neural networks (Section 18.7). The result is that we get a Gaussian distribution over the final layer of the form \(\mathcal{N}(\boldsymbol{\eta}_t | \boldsymbol{\mu}, \boldsymbol{\Sigma})\), where \(\boldsymbol{\eta}_t = f(\boldsymbol{u}_t; \boldsymbol{w}_t)\) is the output of the neural network before the GLM link function induced by \(p_t(\boldsymbol{w}_t)\). Hence we can approximate the partition function using

\(Z_t \approx \int p(\boldsymbol{y}_t | \boldsymbol{\eta}_t) \mathcal{N}(\boldsymbol{\eta}_t | \boldsymbol{\mu}, \boldsymbol{\Sigma}) d\boldsymbol{\eta}_t\) (17.51)

We now discuss how to compute this integral. In the case of probit classification, with \(y \in \{-1, +1\}\), we have \(p(y | \boldsymbol{x}, \boldsymbol{w}) = \Phi(y\eta)\), where \(\Phi\) is the cdf of the standard normal. We can then use the following analytical result

\(\int \Phi(y\eta) \mathcal{N}(h | \mu, \sigma) d\eta = \Phi \left( \frac{y\mu}{\sqrt{1+\sigma}} \right)\) (17.52)

In the case of logistic classification, with \(y \in \{0, 1\}\), we have \(p(y | \boldsymbol{x}, \boldsymbol{w}) = \text{Ber}(y | \sigma(\eta))\); in this case, we can use the probit approximation from Section 15.3.6. For the multiclass case, where \(\boldsymbol{y} \in \{0, 1\}^C\) (one-hot encoding), we have \(p(y | \boldsymbol{x}, \boldsymbol{w}) = \text{Cat}(\boldsymbol{y} | \text{softmax}(\boldsymbol{\eta}))\). A variational lower bound to \(\log Z_t\) for this case is given in [GDFY16].

Once we have computed \(Z_t\), we can take gradients and update the Gaussian posterior moments, before moving to the next step.

# 17.5.4 Online variational inference for DNNs

A natural approach to online learning is to use variational inference, where the prior is the posterior from the previous step. This is known as **streaming variational Bayes** [Bro+13]. In more detail, at step \(t\), we compute

\(\boldsymbol{\psi}_t = \underset{\boldsymbol{\psi}}{\text{argmin}} \underbrace{\mathbb{E}_{q(\boldsymbol{\theta} | \boldsymbol{\psi})} [\ell_t(\boldsymbol{\theta})] + D_\text{KL} (q(\boldsymbol{\theta} | \boldsymbol{\psi}) \| q(\boldsymbol{\theta} | \boldsymbol{\psi}_{t-1}))}_{-\mathcal{L}_t(\boldsymbol{\psi})}\) (17.53)

\(= \underset{\boldsymbol{\psi}}{\text{argmin}} \mathbb{E}_{q(\boldsymbol{\theta} | \boldsymbol{\psi})} [\ell_t(\boldsymbol{\theta}) + \log q(\boldsymbol{\theta} | \boldsymbol{\psi}) - \log q(\boldsymbol{\theta} | \boldsymbol{\psi}_{t-1})]\) (17.54)

where \(\ell_t(\boldsymbol{\theta}) = -\log p(\mathcal{D}_t | \boldsymbol{\theta})\) is the negative log likelihood (or, more generally, some loss function) of the data batch at step \(t\).