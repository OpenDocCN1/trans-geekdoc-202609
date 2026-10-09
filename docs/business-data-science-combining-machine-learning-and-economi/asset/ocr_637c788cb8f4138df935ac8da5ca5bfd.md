an assumption that you are bringing to your analysis, as is the model that defines your likelihood. The *posterior* distribution—the probability distribution on your parameters after observing data—is then available via Bayes rule:

```
$$\text{p}(\Theta|X) = \frac{\text{p}(\Theta|X)\pi(\Theta)}{\text{p}(X)} \propto \text{p}(\Theta|X)\pi(\Theta). \quad (1.10)$$
```

Here, recall that \propto stands for “proportional to.” The *marginal likelihood*,

```
$$\text{p}(X) = \int \text{p}(\Theta|X)\pi(\Theta)d\Theta,$$
```

is the probability of the data under the assumed likelihood model after averaging all possible values of \Theta. Since it doesn’t depend upon \Theta, the nominal target of inference, p(X) is mostly a nuisance for Bayesian inference. The computational strategy of estimating Equation 1.10 via Markov chain Monte Carlo (MCMC)${}^{10}$ is a successful attempt to circumvent the need to explicitly calculate p(X). This strategy is largely responsible for the explosion of Bayesian inference during the 1990s and 2000s.

A good way to get an intuition for Bayesian inference is to play around with *conjugate models*. These are prior and likelihood combinations such that, as you accumulate data, the posterior distribution remains in the same family as the prior. The mechanics of posterior updating can be written out and made explicit. One intuitive example is the beta-binomial model where you have binomial trials with constant success probability *q*. The prior distribution for *q* is a beta distribution:

```
$$\pi(q) = \text{Beta}(q; \alpha, \beta) \propto q^{\alpha-1}(1-q)^{\beta-1}\mathbb{1}_{[q \in (0,1)]}. \quad (1.11)$$
```

For example, the Beta(1, 1) prior yields \pi(q) = \mathbb{1}_{[q \in (0, 1)]}, the familiar uniform distribution. Again, note that the \propto symbol means “is proportional to” and in Equation 1.11 we are ignoring a normalizing constant that ensures $\int_{0}^{1}\pi(q)dq = 1$ for all \alpha, \beta > 0.

Each binomial realization can be viewed as a combination of Bernoulli trials (e.g., tosses of a weighted coin) where *x* = 1 with probability *q* and *x* = 0 with probability 1 − *q*. Under a Beta(*a*, *b*) prior distribution on *q*, the *posterior* distribution for *q* after a single Bernoulli realization for *x* becomes