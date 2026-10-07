# More About Bivariate Regression 499

ε is a random error component. We further assume that the error component, ε, is independently and normally distributed with mean 0 and variance $\sigma^2$, that is,

```
E($\varepsilon_i$) = 0
```

```
Var($\varepsilon_i$) = $\sigma_\varepsilon^2$ for all $i$ (homogeneity of variance or homoscedasticity)
```

```
cov($\varepsilon_i, \varepsilon_{i'}$) = 0 when $i = i'$ (independence)
```

Because we have values of Y at each value of X, there is a distribution of Y scores at each value of X. The conditional distribution of Y at a given value of X has a population mean, which we denote by the symbol $\mu_{Y|X}$. Our assumptions about the population regression line imply that $\mu_{Y|X}$ lies on the straight line $\mu_{Y|X} = \beta_0 + \beta_1X$, and that the deviation of Y from its conditional population mean is due to random error. If the relationship between X and Y is not linear, our error will include more than random variability, and the significance may be biased. In this model, X is assumed to be a fixed-effect variable that is measured without error. In other words, the values of X have been selected by the researcher and that, if we replicated the study, the same values of X would be used. If these conditions are satisfied, it can be shown that $\hat{b}_1$ and $\hat{b}_0$, the least-squares estimators of $eta_1$ and $eta_0$ that we developed in Chapter 17, are unbiased (e.g., $E(\hat{b}_1)=\beta_1$) and consistent (i.e., as the sample sizes are larger, the estimates more closely approximate the parameter values). The estimates

```
$b_1 = r \frac{S_Y}{S_X}$
```

and

```
$b_0 = \bar{Y} - b_1\bar{X}$
```

In the next sections, we discuss how to make statistical inferences about the slope and intercept of the regression equation and about predictions made by the equation. In every case, we can find confidence intervals for $	heta$, the population parameter of interest, by finding

```
$\hat{	heta} \pm t_{\alpha/2}SE(\\hat{	heta})$
```

and can test hypotheses about $\theta$ using the test statistic

```
$t = \frac{\hat{	heta} - \theta_{byp}}{SE(\\hat{	heta})}$
```

where $\hat{	heta}$ is the estimate of $\theta$ from the sample and $SE(\\hat{	heta})$ is the estimated standard error of $\hat{	heta}$. For example, the 95% confidence interval for $\beta_1$ is given by $\beta_1 \pm t_{.025}SE(\\hat{b}_1)$.

The general form of both Equations 19.4 and 19.5 should be familiar: They have appeared in many of the previous chapters. We are also familiar with estimating $\beta_0$ with $b_0$ (Equation 19.3) and $\beta_1$ with $b_1$ (Equation 19.2). All that remains, then, is to learn how