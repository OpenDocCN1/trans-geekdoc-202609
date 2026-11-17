and tend to use it without much thought. However, this is a biased estimator. It can be shown that the unbiased estimator for \(\sigma^2\) is actually

```
\(\hat{\sigma}^2 = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})^2.\) (2.5.6)
```

However, both estimators are consistent meaning that, in the limit as \(n \to \infty\), they both converge to the true variance. In machine learning, the bias-variance trade-off is an important concept to understand in detail. This is why we need to introduce the bias of estimators at this stage.

# 2.5.3 Maximum-Likelihood Estimation

We are now ready to derive estimators from distributions using a well-known procedure called *maximum-likelihood estimation* (MLE). The reason we are interested in such a procedure is that estimators derived using MLE inherit all the nice properties described in the last section, assuming some mild regularity conditions. The basic idea is that if we have an i.i.d. random variable \(X\) with sample observations of \(x_1, x_2, \dots, x_n\) and we seek to estimate a parameter, \(\theta\), using an associated distribution, then MLE can be used to construct a suitable estimator with some nice properties.

Specifically, if we have a PDF, \(f_\theta(x)\), and we wish to estimate \(\theta\), then we can construct a likelihood function as follows:

```
\(L(x_1, x_2, \dots, x_n; \theta) = \prod_{i=1}^n f_\theta(x_i).\) (2.5.7)
```

This likelihood function is the joint density of i.i.d. observations from \(f_\theta(x)\). Since they are i.i.d., we can take the product of the distributions. We want to find the \(\theta\) that maximizes \(L(x_1, x_2, \dots, x_n; \theta)\) and this will constitute an estimate of our unknown parameter, \(\theta\). In effect, we are trying to find the \(\theta\) that would best represent the distribution from which our \(x_i\) values were drawn. This is a key point to understand: we are given the distribution \(f_\theta(x)\) and asking what value of \(\theta\) would be most likely to be associated with it, given set of \(x_i\) values. There is an implicit assumption or belief that the \(x_i\)’s were drawn from a specific distribution but the assumption may not be true. This is worth keeping in mind when using MLE. It does not guarantee that the data came from the given distribution. Rather, the estimate \(\hat{\theta}\) is the one that maximizes the likelihood function if the data were sampled from the given distribution.

The estimate itself is denoted by \(\hat{\theta}\). Then to find this value, we use

```
\(\hat{\theta} = \underset{\theta \in \mathbb{R}}{\text{argmax}} L(x_1, x_2, \dots, x_n; \theta) = \underset{\theta \in \mathbb{R}}{\text{argmax}} \prod_{i=1}^n f_\theta(x_i).\) (2.5.8)
```

This notation simply states that we should find the \(\theta\) that maximizes the likelihood function. In other words, MLE finds the estimate \(\hat{\theta}\) that maximizes the probability that the \(n\) observation, \(x_1, x_2, \dots, x_n\), were sampled from the distribution \(f_\hat{\theta}(x)\).

The way to find \(\hat{\theta}\) is to take the derivative of the likelihood function with respect to \(\theta\) and set it to 0. The procedure is facilitated by taking the logarithm of the likelihood function, the so-called log-likelihood form, as follows:

```
\(\ell(x_1, x_2, \dots, x_n; \theta) = \log L(x_1, x_2, \dots, x_n; \theta) = \sum_{i=1}^n \log(f_\theta(x_i)).\) (2.5.9)
```