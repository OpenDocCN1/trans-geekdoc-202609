
Moreover, even if the data are distributed according to Gaussians, it may still be preferable to adopt the logistic regression formulation instead of that in Eq. [(7.36)](#Chp007_293-342_B9780443292385000135.xhtml#deq62). In the latter formulation, the covariance matrix has to be estimated, amounting to `𝒪(l²/2)` parameters. The logistic regression formulation involves only `l + 1` parameters. That is, once we know about the linear dependence of the log ratio on `x`, we can use this a priori information to simplify the model. Of course, assuming that the Gaussian assumption is valid, if one can obtain good estimates of the covariance matrix, employing this extra information can lead to more efficient estimates, in the sense of lower variance. The issue is treated in [12]. This is natural, because more information concerning the distribution of the data is exploited. In practice, it turns out that using the logistic regression is, in general, a safer bet compared to the linear discriminant analysis (LDA).

The parameter vector `θ` is estimated via the ML method applied on the set of training samples, `(y[n], x[n])`, `n = 1, 2, …, N`, `y[n] ∈ {0, 1}`. The likelihood function can be written as

```
P(y_1,...,y_N; θ) = ∏_{n=1}^N (σ(θ^T x_n))^{y_n} (1 - σ(θ^T x_n))^{1 - y_n}.  (7.37)
```

Indeed, if `x[n]` originates from class `ω[1]`, then `y[n] = 1` and the corresponding probability is given by `σ(θ^T x[n])`. On the other hand, if `x[n]` comes from `ω[2]`, then `y[n] = 0` and the respective probability is given by `1 - σ(θ^T x[n])`. Assuming independence among the successive observations, the likelihood is given as the product of the respective probabilities.

Usually, we consider the negative log-likelihood given by
