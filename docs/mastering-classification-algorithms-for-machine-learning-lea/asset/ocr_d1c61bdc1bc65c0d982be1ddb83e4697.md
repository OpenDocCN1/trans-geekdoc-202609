# Mastering Classification Algorithms for Machine Learning

We will boost the weights of the data points where a wrong prediction is made by a factor of $\alpha$. We will also reduce the weights of the data points where the correct predictions were made by a factor of $\alpha$.

The formula for calculating $\alpha$ is as follows:

```
$\alpha = \eta \ln \frac{1-r}{r}$
```

Here $\eta$ is the hyperparameter for the learning rate. For simplicity, we assume that we set $\eta$ as 1. (It represents natural log or log).

So, we get $\alpha = 1 * \ln \frac{1-0.2}{0.2} = \ln \frac{0.8}{0.2} = \ln 4 = 1.386$

Using $\alpha$, we will calculate the new weights for all the data points. We calculate the new weights for the data points where wrong predictions have been made.

```
newWeightwrongPrediction = oldWeightwrongPrediction * ea
```

If $\alpha$ is positive, the new weight will be greater than the old weight. As we apply this formula to the data points where wrong predictions have been made, these data points will get boosted.

Alongside this, we will reduce the weights of the data points where the correct predictions have been made using the following formula.

```
newWeightcorrectPrediction = oldWeightcorrectPrediction * e-alpha
```

In this case, if $\alpha$ is positive, the new weight will be less than the old weight.

We calculate the new weights for the data points using these formulae, as shown in Table 8.7:

| x | y | Weight | $\hat{y}_1$ | New Weight |
|---|---|---|---|---|
| 0 | 0 | 0.1 | 0 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 1 | 0 | 0.1 | 0 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 2 | 0 | 0.1 | 1 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 3 | 0 | 0.1 | 1 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 4 | 1 | 0.1 | 1 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 5 | 1 | 0.1 | 1 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 6 | 0 | 0.1 | 0 | $0.1 * e^{\ln4} = 0.1 * 4 = 0.4 |
| 7 | 0 | 0.1 | 0 | $0.1 * e^{\ln4} = 0.1 * 4 = 0.4 |
| 8 | 1 | 0.1 | 0 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |
| 9 | 1 | 01 | 1 | $0.1 * e^{-\ln4} = 0.1 * 0.25 = 0.025 |

Table 8.4: New weights calculated for each data point