# ### 3.1.2.5 Plugin approximation

Now suppose we use a plug-in approximation to the posterior predictive, \(p(\boldsymbol{y}|\mathcal{D}) \approx p(\boldsymbol{y}|\hat{\boldsymbol{\theta}})\), where \(\hat{\boldsymbol{\theta}}\) is the MLE or MAP estimate, analogous to the discussion in Section 3.1.1.5. In Figure 3.6(c-d), we show the behavior of this approximation. In both cases, it predicts the smallest enclosing rectangle, since that is the one with maximum likelihood. However, this does not extrapolate beyond the range of the observed data.
We also see that initially the predictions are narrower, since very little data has been observed, but that the predictions become broader with more data. By contrast, in the Bayesian approach, the initial predictions are broad, since there is a lot of uncertainty, but become narrower with more data. In the limit of large data, both methods converge to the same predictions. (See **??** for more discussion of the plug-in approximation.)

# ## 3.2 Informative priors

When we have very little data, it is important to choose an informative prior.

For example, consider the classic **taxicab problem** [Jay03, p190]: you arrive in a new city, and see a taxi numbered \(t=27\), and you want to infer the total number \(T\) of taxis in the city. We will use a uniform likelihood, \(p(t|T) = \frac{1}{T} \mathbb{I}(T \ge t)\), since we assume that we could have observed any taxi number up the maximum value \(T\). The MLE estimate of \(T\) is \(\hat{T}_{\text{mle}} = t = 27\). But this does not seem reasonable. Instead, most people would guess that \(T \sim 2 \times 27 = 54\), on the assumption that if the taxi you saw was a uniform random sample between 0 and \(T\), then it would probably be close to the middle of the distribution.

In general, the conclusions we draw about \(T\) will depend strongly on our prior assumptions about what values of \(T\) are likely. In the sections below, we discuss different possible informative priors for different problem domains; our presentation is based on [GT06].

Once we have chosen a prior, we can compute the posterior as follows:

```
\(p(T|t) = \frac{p(t|T)p(T)}{p(t)}\) \\
(3.13)
```

where

```
\(p(t) = \int_0^\infty p(t|T)p(T)dT = \int_t^\infty \frac{p(T)}{T}dT\) \\
(3.14)
```

We will use the posterior median as a point estimate for \(T\). This is the value \(\hat{T}\) such that

```
\(p(T \ge \hat{T}|t) = \int_{\hat{T}}^\infty p(T|t)dT = 0.5\) \\
(3.15)
```

Note that the posterior median is often a better summary of the posterior than the posterior mode, for reasons explained in **??**.

# ### 3.2.1 Domain specific priors

At the top of Figure 3.7, we show some histograms representing the empirical distribution of various kinds of scalar quantities, specifically: the number of years people live, the number of minutes a movie lasts, the amount of money made (in 1000s of US dollars) by movies, the number of lines of a poem, and the number of years someone serves in the US house of Representatives. (The sources for these data is listed in [GT06].)

At the bottom, we plot \(p(T|t)\) as a function of \(t\) for each of these domains. The solid dots are the median responses of a group of people when asked to predict \(T\) from a single observation \(t\). The solid line is the posterior median computed by a Bayesian model using a domain-appropriate prior (details below). The dotted line is the posterior median computed by a Bayesian model using an uninformative \(1/T\) prior. We see a remarkable correspondence between people and the informed Bayesian model. This suggests that people can implicitly use an appropriate kind of prior for a wide range of problems, as argued in [GT06]. In the sections below, we discuss some suitable parametric priors which catpure this behavior. In [GT06], they also consider some datasets that can only be well-modeled by a non-parametric prior. Bayesian inference works well in that case, too, but we omit this for simplicity.