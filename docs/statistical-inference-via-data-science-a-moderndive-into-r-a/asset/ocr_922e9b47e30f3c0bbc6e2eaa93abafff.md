# 396 10 Inference for Regression

Recall also that we drop the first level as level will be accounted for by the intercept in the model. As we did in the simple linear case, we assume linearity between the response and the regressors holds and apply the linear model described in Subsection 10.4.1 to each observation in the sample. If we express the model in terms of the $ith$ observation,

```
$y_i = eta_0 + \beta_1x_{i1} + \beta_2x_{i2} + \beta_3x_{i3} + \beta_0D_{i2} + \beta_0D_{i3} + \beta_0D_{i4} + \epsilon_i$
```

where, the $ith$ observation in the sample, $x_{i1}$ represents the aroma score, $x_{i2}$ the flavor score, $x_{i3}$ the moisture_percentage, $D_{i2}$ the dummy variable for Asia, $D_{i3}$ the dummy variable for North America, and $D_{i4}$ the dummy variable for South America. Recall that $i$ represents any observation in the sample. Alternatively, we could present the model for all the observations:

```
$y_1 = \beta_0 + \beta_1x_{11} + \beta_2x_{12} + \beta_3x_{13} + \beta_0D_{12} + \beta_0D_{13} + \beta_0D_{14} + \epsilon_1$
$y_2 = \beta_0 + \beta_1x_{21} + \beta_2x_{22} + \beta_3x_{23} + \beta_0D_{22} + \beta_0D_{23} + \beta_0D_{24} + \epsilon_2$
:
$y_n = \beta_0 + \beta_1x_{n1} + \beta_2x_{n2} + \beta_3x_{n3} + \beta_0D_{n2} + \beta_0D_{n3} + \beta_0D_{n4} + \epsilon_n$
```

The extension of the least-squares method applied to multiple regression. We have to retrieve the coefficients that minimize the *sum of squared residuals*:

```
$\sum_{i=1}^n [y_i -(\beta_0 + \beta_1x_{i1} + \beta_2x_{i2} + \beta_3x_{i3} + \beta_0D_{i2} + \beta_0D_{i3} + \beta_0D_{i4})]^2$.
```

This optimization problem is similar to the simple linear case, and it is solved using calculus. We have more equations to deal with; now seven equations in our coffee example, each connected with the coefficient estimators that need to be estimated. The solutions to this problem are reached by using matrices and matrix calculus, and they are the regression coefficients introduced in Chapter 6 and Subsection 6.1.2. They are called the *least-squares estimators*: $b_0$ is the least-square estimator of $\beta_0$, $b_1$ is the least-square estimator of $\beta_1$,

The fitted values, residuals, estimator of the variance ($s^2$), and standard deviation (s), are direct extensions to the simple linear case. In the general case, with $p$ regressors, the fitted values are

```
$$\hat{y}_i = b_0 + b_1x_{i1} + b_2x_{i2} + \dots + b_px_{ip}$,
```

the residuals are $e_i = y_i - \hat{y}_i$, and the model variance estimator is

```
$s^2 = \frac{\sum_{i=1}^n(y_i - \hat{y}_i)^2}{n-p}
```

where $p$ is the number of coefficients. When applying these formulas to the coffee scores example, the fitted values are