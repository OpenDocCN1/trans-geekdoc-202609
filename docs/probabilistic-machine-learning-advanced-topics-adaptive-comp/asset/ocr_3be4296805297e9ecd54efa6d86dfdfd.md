# ### 3.8.2 Bayes model averaging

If our goal is to perform predictions, we are better off averaging over all models, rather than predicting using just one single model. That is, we should compute the **posterior predictive distribution** using

```
$p(y|\mathcal{D}) = \sum_{m \in \mathcal{M}} p(y|m)p(m|\mathcal{D})$
```

This is called Bayes model averaging [Hoe+99]. This is similar to the machine learning technique of **ensembling**, in which we take a weighted combination of predictors. However, it is not the same, as pointed out in [Min00b], since the weights in an ensemble do not need to sum to 1. In particular, in BMA, if there is a single best model, call it \( m^* \), then in the large sample limit, \( p(m|\mathcal{D}) \) will become a degenerate distribution with all its weight on \( m^* \), and the other members of \( \mathcal{M} \) will be ignored. This does not happen with an ensemble.

# ### 3.8.3 Estimating the marginal likelihood

To perform Bayesian model selection or averaging, we need to be able to compute the marginal likelihood in Equation (3.280), also called the evidence. Below we give a brief summary of some suitable methods. For more details, see e.g., [FW12].

# #### 3.8.3.1 Analytic solution for conjugate models

If we use a conjugate prior, we can compute the marginal likelihood analytically, as we discussed in Section 3.4.5.4. We give a worked example in Section 3.8.1.1.

# #### 3.8.3.2 Harmonic mean estimator

A particularly simple estimator, known as the **harmonic mean estimator**, was proposed in [NR94]. It is defined as follows:

```
$p(\mathcal{D}) \approx \left( \frac{1}{S} \sum_{s=1}^S \frac{1}{p(\mathcal{D}|\theta_s)} \right)^{-1}$
```

where \( \theta_s \sim p(\theta) \) are samples from the prior. This follows from the following identity:

```
$\mathbb{E} \left[ \frac{1}{p(\mathcal{D}|\theta)} \right] = \int \frac{1}{p(\mathcal{D}|\theta)} p(\theta|\mathcal{D}) d\theta$
$= \int \frac{1}{p(\mathcal{D}|\theta)} \frac{p(\mathcal{D}|\theta)p(\theta)}{p(\mathcal{D})} d\theta$
$= \frac{1}{p(\mathcal{D})} \int p(\theta) d\theta = \frac{1}{p(\mathcal{D})}$
```

(We have assumed the prior is proper, so it integrates to 1.)

Unfortunately, the number of samples needed to get a good estimate is generally very large, since most samples from the prior will have low likelihood, making this approach useless in practice. Indeed,