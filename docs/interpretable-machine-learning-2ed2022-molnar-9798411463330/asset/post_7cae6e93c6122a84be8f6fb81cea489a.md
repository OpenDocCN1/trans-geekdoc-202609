
## CHAPTER 4 INTERPRETABLE MODELS

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_71_0.png)

On 76 of the 200 days you had no coffee at all and on the most extreme day you had 7. Let us naively use a linear model to predict the number of coffees using sleep level, stress level and work yes/no as features. What can go wrong when we falsely assume a Gaussian distribution?

A wrong assumption can invalidate the estimates, especially the confidence intervals of the weights. A more obvious problem is that the predictions do not match the “allowed” domain of the true outcome, as the following figure shows.

The linear model does not make sense, because it predicts negative number of coffees. This problem can be solved with Generalized Linear Models (GLMs). We can change the link function and the assumed distribution. One possibility is to keep the Gaussian distribution and use a link function that always leads to positive predictions such as the log-link (the inverse is the exp-function) instead of the identity function. Even better: We choose a distribution that corresponds the generating process and an appropriate link function. Since the outcome is a count, the Poisson distribution is a natural choice, along with the logarithm as link function. In this case, the data even generated with the Poisson distribution, so the Poisson GLM is the perfect choice. The fitted Poisson GLM leads to the following distribution of predicted values:

No negative amounts of coffees, looks much better now.

## Interpretation of GLM weights

The assumed distribution together with the link function determines how the estimated feature weights are interpreted. In the coffee count example, I used a GLM with Poisson distribution and log link, implies the following relationship between the expected outcome and the features (str, sleep) and work (wrk).

```
$ln(E(coffee|str, slp, wrk)) = \beta_0 + \beta_{str}x_{str} + \beta_{slp}x_{slp} + \beta_{wrk}x_{wrk}$
```

To interpret weights we invert the link function so that we can interpret the effect of the features on the expected outcome and not the logarithm of the expected outcome.

```
$E(coffee|str, slp, wrk) = exp(\beta_0 + \beta_{str}x_{str} + \beta_{slp}x_{slp} + \beta_{wrk}x_{wrk})$
```

Since all the weights are in the exponential, the effect interpretation is not additive, but multiplicative, $exp(a+b) = exp(a) \times exp(b)$. The interpretation is the actual weights of the toy example. The following table lists the estimated weights and exp(weights) together with the 95% confidence interval:

Increasing the stress level by one multiplies the expected number of coffees by the factor 1.12. Increasing the sleep quality by one point multiplies the expected number of coffees by the factor 0.86. The predicted number of coffees on a day is 2.23 times the number of coffees.

## 4.3 GLM, GAM AND MORE

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_72_0.png)

Figure 4.10: Predicted number of coffees dependent on stress, sleep and work. The linear model predicts negative values.

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_72_1.png)

Figure 4.11: Predicted number of coffees dependent on stress, sleep and work. The GLM with Poisson assumption and log link is an appropriate model for this dataset.

Table 4.4: Weights in the Poisson model

| weight | exp(weight) [2.5%, 97.5% ] |
|---|---|
| (Intercept) | -0.16 | 0.85 [0.54, 1.32] |
| stress | 0.12 | 1.12 [1.07, 1.18] |
| sleep | -0.15 | 0.86 [0.82, 0.90] |
| workYES | 0.80 | 2.23 [1.72, 2.93] |

### 4.3.2 Interactions

The linear model assumes that the effect of one feature is independent of the others. But often, the effect of one feature depends on the level of another. To capture this, we add interaction terms to the linear model. How can we get the linear model to include interactions? If we want to consider the interaction between a categorical and numerical feature, we would add a column. Suppose our data looks like this:

| Intercept | workY | temp | workY.temp |
|---|---|---|---|
| 1 | 1 | 25 | 25 |
| 1 | 0 | 12 | 0 |
| 1 | 0 | 30 | 0 |
| 1 | 1 | 5 | 5 |

The first column serves to estimate the intercept. The second column is the encoded work feature. Columns three and four are for the weather feature, which requires two columns because you need to capture the effect for three categories, one of which is the reference category. The rest of the columns capture the interactions. The interaction of two categorical features works similarly. We create additional features which represent combinations of categories. For each category of both features (except for the reference category), we create a new feature that is 1 if both features have a certain category, otherwise 0.

For two numerical features, the interaction column is even easier to construct: We simply multiply both numerical features.

There are approaches to automatically detect and add interaction terms. One of them can be found in the RuleFit chapter. The RuleFit algorithm mines interaction terms and then estimates a linear model including interactions.

## Example

Let us return to the bike rental prediction task which we have already modeled in the linear model chapter. This time, we additionally consider an interaction between the temperature and the working day feature. This results in the following estimated weights and confidence intervals.
