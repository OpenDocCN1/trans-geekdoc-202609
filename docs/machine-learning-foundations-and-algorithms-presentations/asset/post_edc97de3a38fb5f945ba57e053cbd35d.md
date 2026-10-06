
# Optimization of the Hyperparameters

- In GPs, the parameters $w$ can be integrated out in closed form
- Yet, no closed form solution exists for the hyper-parameters

Objective: Log-likelihood of the training data on the prior

$\beta^* = \arg \max_{\beta} \log \mathcal{N}(\boldsymbol{y}|\mathbf{0}, \boldsymbol{C}_\beta)$
= \arg \max_{\beta} - \frac{1}{2} \log |\boldsymbol{C}_\beta| - \frac{1}{2} \boldsymbol{y}^T \boldsymbol{C}_\beta^{-1} \boldsymbol{y} - \frac{N}{2} \log(2\pi)$

- Need to be optimized via gradient descent (only batch)
- Non-convex, multiple optima
- Only a small number of hyper-parameters
- Very flexible representation, beware of overfitting (would be better to do that on validation set!)

# Example: Gene Expression

- Given gene expression levels in the form of a time series
- Want to detect if a gene is expressed or not, fit a GP to each gene [Kalaitzis and Lawrence, 2011]

RESEARCH ARTICLE Open Access

# A Simple Approach to Ranking Differentially Expressed Gene Expression Time Courses through Gaussian Process Regression

Alfred A Kalaitzis and Neil D Lawrence*

Abstract
**Background:** The analysis of gene expression from time series underpins many biological studies. Two basic forms of analysis recur for data of this type: removing inactive (quiet) genes from the study and determining which genes are differently expressed. Often these analysis stages are applied disregarding the fact that the data is drawn from a time series. In this paper we propose a simple model for accounting for the temporal nature of the data based on a Gaussian process.
**Results:** We review Gaussian process (GP) regression for estimating the continuous trajectories underlying in gene expression time-series. We present a simple approach to machine learning which genes, or cases of the time series in the form of expression ratios, quantitative difference. We assess via ROC curves the curves

# Example: GP Log-Likelihood

- Contour plot of the log-likelihood
- We can see multiple optima in the plot
- SNR = signal to noise ratio (ratio between lambda and sigma)

![](img/f01928df50903c99ce023dd3c527a33d_885_0.png)

# Example: Multiple Optima

- Optimum 1: length scale of 1.2221 and log10 SNR of 1.9654
- Log-likelihood is -0.22317.

![](img/f01928df50903c99ce023dd3c527a33d_886_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_886_1.png)

log10 length scale

# Example: Multiple Optima

- Optimum 2: length scale of 1.5162 and log10 SNR of 0.21306
- Log-likelihood is -0.23604.

![](img/f01928df50903c99ce023dd3c527a33d_887_0.png)

log10 length scale | Machine Learning | KIT | SS2024

# Example: Multiple Optima

- Optimum 3: length scale of 2.9886 and log10 SNR of -4.506
- Log-likelihood is -2.1056.

![](img/f01928df50903c99ce023dd3c527a33d_888_0.png)

# GPs: Summary

- GPs are a non-parametric Bayesian approach to regression with possibly infinite feature spaces
- Can estimate predictive uncertainty by integrating out model uncertainty
- Resulting prediction equations are “straightforward” and obtained in closed-form because of the Gaussian properties
- Hyperparameter optimization more complex, non-convex and expensive
- While GP for Regression is computationally very expensive, it is one of the most principled approaches to statistical learning for regression
- For small data-sets, they typically also outperform Neural Nets by a large margin

# Self-test questions

- What is the major advantage of GPs over Kernel Ridge Regression?
- Why are GPs a Bayesian approach?
- What principle allowed deriving GPs from a Bayesian regression point of view?

# Variational Inference

Machine Learning, SS2024

Prof. Gerhard Neumann
KIT, Institut für Anthrophomatik und Robotik

# Motivation

In Bayesian Learning, we need to sample from complex (posterior) distributions...

```
$p(\theta|\mathcal{D}) = \frac{p(\mathcal{D}|\theta)p(\theta)}{p(\mathcal{D})}$$
```

Yet, these sampling from these distributions is quite inefficient...

- Can theoretically be done via Monte-Carlo Markov Chain Sampling
- Computationally very expensive

Can we approximate $p(\theta|\mathcal{D})$ by a simpler distribution?

- Yes: Optimization!
- Optimization on distributions is called Variational Inference

# Learning Outcome for today

What we will learn today:
- Define Variational Inference (VI)
- Understand how to measure distances between distributions
- Understand why we use reverse KL
- Learn methods to optimize the reverse KL

# Agenda for today

**Variational Inference:**

- I-projection versus M-projection

**Algorithms:**
- Bayes
- Natural Gradients

# Variational Inference

We want to approximate an intractable distribution

$p^*(x) = \frac{p(x)}{Z}$

with a tractable distribution $q(x)$

# What does intractable mean?

- We cannot evaluate the constant $Z$
- Its hard to sample from $p^*(x)$
- Can be done using Monte-Carlo (MCMC), but very expensive

![](img/f01928df50903c99ce023dd3c527a33d_895_0.png)

# When is this useful?

- Approximating posterior distributions
- Latent variable models

# How can we do that?

We can minimize a divergence measure

$q^* = \text{argmin}_q D(q, p^*)$

Commonly used divergence:

- **Reverse KL:** Mode-seeking
- Generative model might be arbitrary poor
- $q$ might have high density where $p^*(x)$ is low

# # Comparison of the projections for VI

# Information

![](img/f01928df50903c99ce023dd3c527a33d_897_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_897_1.png)

$KL(q(x)||p^*(x)) = \int q(x) \log \frac{q(x)}{p^*(x)} dx$

- No need to know normalizer of $p^*$
- Good generative model (all samples are representative)
- Hard to optimize even for simple $q$
- Might miss areas with probability mass

$KL(p^*(x)||q(x)) = \int p^*(x) \log \frac{p^*(x)}{q(x)} dx$

- **Forward forcing:** If $p^*(x)$ is small, $q(x)$ needs be small
- Easy to optimize
- Covers all areas with high probability
- Needs samples from $p^*$

# Optimization of the I-Projection

arg \min_{q} KL(q(x)||p^*(x)) = \int_{x} q(x) \log \frac{q(x)}{p^*(x)} dx$

# ## Gaussian variational approximations:

- Most common approximation

### Mean-field approximation
$q_{\mu,\sigma}(x) = \mathcal{N}(\boldsymbol{\mu}, \text{diag}(\boldsymbol{\sigma}^2))$

### Full covariance approximation
$q_{\mu,\boldsymbol{\Sigma}}(x) = \mathcal{N}(\boldsymbol{\mu}, \boldsymbol{\Sigma})$

### GMM approximation
$q_{\theta}(x) = \sum_{o} p(o)\mathcal{N}(\boldsymbol{\mu}_{o}, \boldsymbol{\Sigma}_{o})$

# ## Algorithms :

- Bayes-By-Backprop Reparameterization trick
  - Only works for mean-field approximation,
  - very slow for full covariance case

- Natural Gradients with trust regions (RL Lecture)
  - Works well for full covariance case
  - Has been extended to GMM case [Arenz 2020]
