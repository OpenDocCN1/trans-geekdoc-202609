# 572 Research Design and Statistical Analysis

interval tells us that the range of possible values is quite wide; converting from $ho^2$ to $ho$, the lower limit of the 95% CI is .31 and the upper limit is .75.

An expression for the variance of $R^2$ is given by

```
$Var(R^2) = 4\rho^2(1-\rho^2)^2 \frac{(N-p-1)}{(N^2-1)(N+3)} \quad (21.1)$
```

where $N$ is the total number of cases, $p$ is the number of predictors, and $ho^2$ is the square of the population multiple correlation coefficient (Olkin & Finn, 1995). For example, if we consider the regression of TC on age, BMI, beck\_d, beck\_a, and dirwd1 for women aged 20–65 with BMI scores of 40 or less, and take the value of $R^2$ from Figure 21.6 as our estimate of $ho^2$, the variance of $R^2$ is estimated by

```
$4(..3558)(1-.3558)^2 \frac{(131^2-1)}{(131)(133)} = 0.004$
```

We can approximate the 95% CI for $ho^2$ using a normal distribution, with the following formula:

```
$R^2 \pm z_{025}SE(R^2) = .3558\pm1.96\sqrt{.1240}$
```

that, an interval extends from approximately .23 to .48. In R, the $ci.R2$ function in the [MBESS] package computes this confidence interval more precisely, taking $R^2$, $N$, and $p$ ($K$) as input: $ci.R2(R=.3558, N=131, K=5)$ returns $[0.199, .466]$. The intervals are not identical in this case because because the sampling distribution of $R^2$ is not exactly normal, an issue that is better addressed with software.

We should point out that the methods discussed in this section will not be accurate unless the assumption of multivariate normality is satisfied and the predictor variables have been specified in advance.

# 21.4.3 Testing the Hypothesis $\beta_1 = \beta_{np}$ and Finding Confidence Intervals for $\beta_1$

A significant test of the overall regression equation implies that at least one of the predictors is linearly related to $Y$. We want to explain how the individual $X$ variables contribute to the prediction of $Y$. Under the usual assumptions, the ratio

```
$\frac{b_1-\beta_1}{SE(b_1)}$
```

will be distributed as $t$ with $N-1-p$ $df$. Therefore, if we can estimate the standard error, we can test the hypothesis that the population intersection, $eta_0$, or any of the population regression coefficients, $eta_j$, are equal to any constant. In practice, the null hypothesis $eta=0$ is usually tested. Rejection of this hypothesis implies that $X$, makes a significant contribution to the predictability of $Y$ when it is added to the other variables in the equation. For example,