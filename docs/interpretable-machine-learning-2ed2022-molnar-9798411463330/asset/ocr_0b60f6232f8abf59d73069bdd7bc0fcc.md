# CHAPTER GLOBAL MODEL-AGNOSTIC METHODS

interaction statistic of 1 between two features means that each single PD function is constant and the effect on the prediction only comes through the interaction. The H-statistic can also be larger than 1, which is more difficult to interpret. This can happen when the variance of the 2-way interaction is larger than the variance of the 2-dimensional partial dependence plot.

Mathematically, the H-statistic proposed by Friedman and Popescu for the interaction between feature j and k is:

```
$H_{jk}^2 = \frac{\sum_{i=1}^n [PD_{jk}(x_j^{(i)}, x_k^{(i)}) - PD_j(x_j^{(i)}) - PD_k(x_k^{(i)})]^2}{\sum_{i=1}^n PD_{jk}^2(x_j^{(i)}, x_k^{(i)})}$
```

The same applies to measuring whether a feature j interacts with any other feature:

```
$H_j^2 = \frac{\sum_{i=1}^n [PD_j(x_j^{(i)}) - PD_{-j}(x_j^{(i)})]^2}{\sum_{i=1}^n PD_{-j}^2(x_j^{(i)})}$
```

The H-statistic is expensive to evaluate, because it iterates over all data points and at each point the partial dependence has to be evaluated which in turn is done with all $n$ data points. In the worst case, we need $2n^2$ calls to the machine learning models to predict function to compute the two-way H-statistic (j vs. k) and $3n^2$ for the total H-statistic (j vs. all). To speed up the computation, we can sample from the $n$ data points. This has the disadvantage of increasing the variance of the partial dependence estimates, so if you are sampling to reduce the computational burden, makes the H-statistic unstable. So you sure to sample enough data points.

Friedman and Popescu also propose a test statistic to evaluate whether the H-statistic differs significantly from zero. The null hypothesis is the absence of interaction. To generate the interaction statistic under the null hypothesis, you must be able to adjust the model so that it has no interaction between feature j and k or others. This is not possible for all types of models. This test is model-specific, not model-agnostic, and as not covered here.

The interaction strength statistic can also be applied in a classification setting if the prediction is a probability.

# 7.3.3 Examples

Let us see what feature interactions look like in practice! We measure the interaction strength of features in a support vector machine that predicts the number of rented bikes based on weather and calendrical features. The following plot shows the feature interaction H-: