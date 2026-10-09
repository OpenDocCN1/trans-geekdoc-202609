What are these statistics? We need to introduce two complementary concepts:

+   - *Likelihood* is the probability of your data given parameters. You want to make it as big as possible.
- *Deviance* measures to the distance between data and fit. You want to make it as small as possible.

These two quantities are mirror images of each other, and they are tied together through a mathematical relationship:

```
Deviance = -2log[Likelihood] + C. (2.17)
```

More precisely, the deviance is -2 times the difference between log likelihoods for your fitted model and for a “fully saturated” model where you have as many parameters as observations. The term corresponding to this fully saturated model gets wrapped into C, which is a constant we can mostly ignore. We view deviance as a cost to be minimized. This is the guiding principle behind the way we estimate our models. Ignoring the complexities of model selection and regularization (next chapter), and using lhd(β) to denote the likelihood function, our model coefficients are fit to achieve

```
β̂ = argmin {- 2/n log lhd(β)}. (2.18)
```

Because of the relationship between deviance and likelihood, this deviance minimization strategy is commonly referred to as *maximum likelihood estimation* (MLE).

Let’s work through an example with linear regression and Gaussian (normal) errors. The probability model is y ~ N(x’β, σ²), where the Gaussian probability density function is

```
N(x’β, σ²) = 1 / sqrt(2πσ²) exp[- ((y - x’β)²) / (2σ²)]. (2.19)
```

Given n independent observations, the likelihood (i.e., the probability of the data) is