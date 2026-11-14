![](bbox=[0.1, 0.08, 0.9, 0.38])

# Prior

The conjugate prior is known as the **inverse Wishart** distribution, which is a distribution over positive definite matrices, as we explained in Section 2.2.5.5. This has the following pdf:

```
IW(\boldsymbol{\Sigma} \mid \tilde{\boldsymbol{\Psi}}, \tilde{\nu}) \propto |\boldsymbol{\Sigma}|^{-(\tilde{\nu}+D+1)/2} \exp \left( -\frac{1}{2} \text{tr}(\tilde{\boldsymbol{\Psi}} \boldsymbol{\Sigma}^{-1}) \right)
```

Here \tilde{\nu} > D - 1 is the degrees of freedom (dof), and \tilde{\Psi} is a symmetric pd matrix. We see that \tilde{\Psi} plays the role of the prior scatter matrix, and N_0 \triangleq \tilde{\nu} + D + 1 controls the strength of the prior, and hence plays a role analogous to the sample size N.

# Posterior

Multiplying the likelihood and prior we find that the posterior is also inverse Wishart:

```
p(\boldsymbol{\Sigma} \mid \mathcal{D}, \boldsymbol{\mu}) \propto |\boldsymbol{\Sigma}|^{-\frac{N}{2}} \exp \left( -\frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \mathbf{S}_\mu) \right) |\boldsymbol{\Sigma}|^{-(\tilde{\nu}+D+1)/2}
\exp \left( -\frac{1}{2} \text{tr}(\boldsymbol{\Sigma}^{-1} \tilde{\boldsymbol{\Psi}}) \right)
= |\boldsymbol{\Sigma}|^{-\frac{N+(\tilde{\nu}+D+1)}{2}} \exp \left( -\frac{1}{2} \text{tr} \left[ \boldsymbol{\Sigma}^{-1} (\mathbf{S}_\mu + \tilde{\boldsymbol{\Psi}}) \right] \right)
= \text{IW}(\boldsymbol{\Sigma} \mid \tilde{\boldsymbol{\Psi}}, \tilde{\nu})
\tilde{\nu} = \tilde{\nu} + N
\tilde{\boldsymbol{\Psi}} = \tilde{\boldsymbol{\Psi}} + \mathbf{S}_\mu
```

In words, this says that the posterior strength \tilde{\nu} is the prior strength \tilde{\nu} plus the number of observations N, and the posterior scatter matrix \tilde{\Psi} is the prior scatter matrix \tilde{\Psi} plus the data scatter matrix \mathbf{S}_\mu.