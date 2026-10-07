# More About Bivariate Regression 513

If we can assume that the measurement error in X is random and the error component is uncorrelated with $X_{\mu}$ we have $E(b)=0$ and $\sigma_X^2=\sigma_{\mu}^2+\sigma_{\epsilon}^2$. In the case of regressing height on weight, this situation might occur if the scale we use to measure weight was noisy but biased – say on some trials it gives high readings and on others, low readings, but the tendency to read high or low is not related to any characteristic of the person being weighed.

If $\epsilon, \delta$, and $X$, are all normally and independently distributed, the regression of $Y$ on $X$ will be linear with a slope of

```
$$\beta_1 = \beta_{lt} \frac{\sigma_Y}{\sigma_X} = \beta_{lt}r_{XY}$ $(19.13)$
```

where $eta_{lt}$ is the “true” slope (i.e., the slope of the equation that would be obtained by regressing $Y$ on $X$) and $\sigma_X^*=\sigma_X/\sigma_{\epsilon}$ is the reliability of $X$ (i.e., the proportion of the variation in the actual $X$ scores is accounted for by the true scores). Even if $X$, is not normally distributed, the results hold for large samples and approximately for small samples when the reliability is high. The implication of the magnitude of the true slope and the amount of underestimation depends directly on the amount of measurement error. If there is an error in measuring $X$, the slope, $b$, underestimates the true slope. If there is a great deal of measurement error, the reliability will be low, and $\beta$, will be much closer to zero than the true slope.

The situation is if we cannot assume that $X$, is independent of the error component. Suppose, for example, we do not use a scale to measure weight, but instead ask each participant to provide a self-report. These estimates of weight will probably contain systematic as random error because the reported weights will be less than the true weights, especially for participants who are seriously overweight. Moreover, the degree of underreporting may be greater for some subgroups of participants than others. The net result is a correlation between the predictor variable and the error component, violating the assumptions made in the last section for the case in which $X$ is a random variable. Given this type of violation, OLS regression provides neither unbiased nor consistent estimators. Possible remedies for dealing with correlated predictors and error components exist, but they are beyond the scope of this text (see, for example, Berk, 2004).

Although discussion of measurement sometimes gets lost in terms of regression, it is critically important. We should always try to use the most reliable measures we can and should always be aware of the consequences of using poor measures. If we can get in trouble using measures of weight, what can happen if we poorly constructed assessments of psychological variables.

# 19.6 Unstandardized vs Standardized Regression Coefficients

When we regress $Y$ on $X$, we get the regression equation

```
$$\hat{Y} = b_0 + b_1X$
```

We can also choose to look at the standardized regression equation; that is, the equation that would result if the regression was performed using z scores,

```
$$\hat{z}_Y = b'_1z_X = r_{zX}$
```