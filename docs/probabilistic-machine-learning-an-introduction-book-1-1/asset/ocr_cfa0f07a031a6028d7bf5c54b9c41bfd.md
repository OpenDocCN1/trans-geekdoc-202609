is $p(y|\mathbf{x},\boldsymbol{\theta}) = \mathcal{N}(y|\mathbf{w}^\top\mathbf{x},\beta^{-1})$ and the prior is $p(\mathbf{w}) = \mathcal{N}(\mathbf{w}|\mathbf{0},\alpha^{-1}\mathbf{I})$. We assume the observation variance $\sigma^2 = 1/\beta$ is known. Let $\lambda = \alpha/\beta$ index the different model families. In Sec. 4.4.5.2, we used cross validation to estimate the optimal $\lambda$. In this section, we pick the value of $\lambda$ with the maximum marginal likelihood. More precisely, we evaluate the log marginal likelihood (evidence) of the model as in Sec. 11.6.6.1. In Fig. 4.6b, we plot the negative log marginal likelihood $\mathcal{L}(\lambda)$ vs $\log(\lambda)$. We see that it has roughly the same shape as the CV curve. In particular, their minima occur for the same value of $\lambda$.

Furthermore, since $\mathcal{L}(\lambda)$ is a continuous function of $\lambda$ (unlike the CV estimate), we can use gradient-based optimization to find $\hat{\lambda}$. This can be easily extended to the case where we have many hyperparameters. See Sec. 11.6.6 for details.

# 7.6.5 Information criteria

The marginal likelihood can be difficult to compute, since it requires marginalizing over the entire parameter space. Furthermore, the result can be quite sensitive to the choice of prior. In this section, we discuss some other related metrics for model selection that incorporate a complexity penalty, and which therefore do not require the use of a validation set. These are known as **information criteria**.

The basic idea is to start with the **deviance**, which is two times the negative log likelihood:

```
deviance(m) \triangleq -2 \sum_{n=1}^{N} \log p(y_n|\hat{\boldsymbol{\theta}}_m, m) \tag{7.198}
```

(The factor of 2 is for historical reasons, since it cancels out the factor of 1/2 that arises with a Gaussian likelihood.) We know that selecting the model with smallest deviance will result in overfitting, so we add some form of complexity penalty to get

```
J(m) = -2L(m) + C(m) \tag{7.199}
```

where $L(m)$ is the log likelihood, and $C(m)$ is the complexity penalty for model $m$. We discuss different choices for $L$ and $C$ below. See e.g., [GHV14] for further details.

# 7.6.5.1 The Bayesian information criterion (BIC)

The **Bayesian information criterion** or **BIC** [Sch78] uses a complexity term of the form

$C(m) = \log(N) \times \text{dof}(m)$ \tag{7.200}

where $N$ is the size of the training set and “dof” stands for **degrees of freedom** of the model. If we interpret the dof as the number of parameters in the model, then we can derive the BIC as the log marginal likelihood of a Gaussian approximation to the posterior, as we discuss in Sec. 7.7.2.

In particular, from Eq. (7.229), we have

$\log p(\mathcal{D}) \approx \log p(\mathcal{D}|\hat{\boldsymbol{\theta}}_{\text{map}}) + \log p(\hat{\boldsymbol{\theta}}_{\text{map}}) - \frac{1}{2}\log |\mathbf{H}|$ \tag{7.201}