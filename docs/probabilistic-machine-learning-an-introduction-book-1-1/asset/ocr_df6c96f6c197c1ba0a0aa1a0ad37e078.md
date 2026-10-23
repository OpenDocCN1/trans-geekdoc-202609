where

$$p(m|\mathcal{D}) = \frac{p(\mathcal{D}|m)p(m)}{\sum_{m\in\mathcal{M}} p(\mathcal{D}|m)p(m)}\tag{7.189}$$

is the posterior over models. If the prior over models is uniform, $p(m)=1/|\mathcal{M}|$, then the MAP model is given by

$$\hat{m} = \underset{m\in\mathcal{M}}{\operatorname{argmax}}\,p(\mathcal{D}|m)\tag{7.190}$$

The quantity $p(\mathcal{D}|m)$ is given by

$$p(\mathcal{D}|m) = \int p(\mathcal{D}|\boldsymbol{\theta},m)p(\boldsymbol{\theta}|m)d\boldsymbol{\theta}\tag{7.191}$$

This is known as the **marginal likelihood**, or the **evidence** for model $m$. Intuitively, it is the likelihood of the data averaging over all possible parameter values, weighted by the prior $p(\boldsymbol{\theta}|m)$. If all settings of $\boldsymbol{\theta}$ assign high probability to the data, then this is probably a good model.

# 7.6.1.1 Example: polynomial regression

As an example of Bayesian model selection, we will consider polynomial regression in 1d. Fig. 7.22 shows the posterior over three different models, corresponding to polynomials of degrees 1, 2 and 3 fit to $N=5$ data points. We use a uniform prior over models, and use empirical Bayes to estimate the prior over the regression weights (see Sec. 11.6.6). We then compute the evidence for each model (see Sec. 11.6 for details on how to do this). We see that there is not enough data to justify a complex model, so the MAP model is $m=1$. Fig. 7.23 shows the analogous plot for $N=30$ data points. Now we see that the MAP model is $m=2$; the larger sample size means we can safely pick a more complex model.

# 7.6.2 Bayes model averaging

So far, we have focused on picking the single best model. However, if our goal is to perform prefiction, we can get better results if we marginalize out over all models, by computing

$$p(y|\mathbf{x},\mathcal{D}) = \sum_{m\in\mathcal{M}} p(y|\mathbf{x},m)p(m|\mathcal{D})\tag{7.192}$$

This is called **Bayesian model averaging** or **BMA** (see e.g., [Dra95; RMH97] for further discussion). If we use a uniform prior over models, this becomes

$$p(y|\mathbf{x},\mathcal{D}) \propto \sum_{m\in\mathcal{M}} p(y|\mathbf{x},m)p(\mathcal{D}|m)\tag{7.193}$$

Essentially this requires performing prediction using an **ensemble** of models, weighted by their marginal likelihood. If the set of models is very large, we may still be able to get good results using an equally weighted random selection of models.