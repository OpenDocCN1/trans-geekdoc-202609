
```r
library(AER)
bvar <- vcovHC(fit)
round(bvar, 1)
```

| | (Intercept) | Solar.R | Wind | Temp | Month | Day |
| :-- | :-- | :-- | :-- | :-- | :-- |
| (Intercept) | 432.9 | 0.1 | -13.3 | -3.6 | -3.2 | 0.3 |
| Solar.R | 0.1 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| Wind | -13.3 | 0.0 | 0.8 | 0.1 | -0.2 | -0.1 |
| Temp | -3.6 | 0.0 | 0.1 | 0.1 | -0.1 | 0.0 |
| Month | -3.2 | 0.0 | -0.2 | -0.1 | 1.8 | 0.0 |
| Day | 0.3 | 0.0 | -0.1 | 0.0 | 0.0 | 0.1 |

This is the sampling covariance matrix of the coefficients; variances are along the diagonal. To get the standard error, which is the sampling standard deviation, you need to take the square root of the diagonal variance estimate.

```r
sqrt(bvar["Wind","Wind"])
[1] 0.9128877
```

This is much larger (about 40% larger) than the standard error of 0.645 from the R output. The assumption of homoskedasticity yields an artificially small uncertainty estimate. To see why this happens, consider the fitted residuals shown in Figure 2.10: the heteroskedasticity is clear, with much larger residuals occurring on low-wind days.

![](img/315929ad4bddd26368466d02e06e2385_94_0.png)

FIGURE 2.10: Fitted residuals from the airquality OLS regression.

The HC standard errors are useful, and you will use them often. There is also an interesting relationship between HC standard errors and the bootstrap. It turns out that, for OLS, the parameter variance estimates you get from the nonparametric bootstrap are actually *approximated* by the HC procedure.[^13] That is, you can use the HC standard errors as a fast alternative to bootstrapping for OLS. This relationship also implies that the assumption of the normal distribution in Equation 2.28 is not especially important for the HC standard errors—they are robust to deviations from Gaussianity in the errors. To illustrate, we can run a quick bootstrap on the *airquality* data.

```python
B <- 10000
beta <- vector(length=B)
n <- nrow(airquality)
for (b in 1:B) {
  bs = sample.int(n, n, replace=TRUE)
  bsfit <- lm(Ozone ~., data=airquality, subset=bs)
  beta[b] <- coef(bsfit) ["Wind"]
}
sd(beta)
[1] 0.8753398
```

To a first decimal place, the standard error matches that of the HC procedure. The sampling distributions are illustrated in Figure 2.11.

![](img/315929ad4bddd26368466d02e06e2385_95_0.png)

FIGURE 2.11: Estimated sampling distributions for the wind coefficient in our airquality regression. HC denotes the heteroskedastic consistent procedure, and vanilla refers to the usual results that rely upon homoskedasticity.

All of the uncertainty estimators discussed so far—all of those shown in Figure 2.11—assume independence between observations. The HC procedure, for example, keeps zeros on the off diagonals in $\hat{\boldsymbol{\Sigma}}$. There are additional procedures and tools you can use in the case of dependence between observations. Sandwich estimators that allow for dependence, sometimes called clustered standard errors, will be discussed in Chapter 5; these techniques are commonly used when estimating treatment effects in randomized controlled trials. You can also deal with dependency by modeling it in your regression, making the dependence between observations explicit by including them in each other’s mean functions. In the next section, we discuss how to model such dependence in the specific context of spatial and temporal processes.

## SPACE AND TIME

Much of the material in this book is focused on independent observations. For example, independence was key in our development of deviance and likelihood in the previous section. However, many events that occur geographically near to each other, or one after the other, can be dependent. For example, maybe sales are always higher in spring/summer, or when one restaurant has a busy night, the neighboring restaurants also gain traffic from those who couldn’t get a table. In this section we'll figure out how to deal with such information.

Fortunately, the main tricks for working with space-time dependence fit within a standard regression framework. You simply include the variables behind dependence in your set of inputs, controlling for trends in time (e.g., month) and space (e.g., regional location) and for auto-regression, which is dependence between neighboring outcomes.

Traditional statistics texts spend a large amount of time carefully hand-building these trend and autoregressive effects. Fortunately, the regularization and model selection material of later chapters lets us simply include a huge set of possible space/time variables and rely upon the data to tell us what works best. Thus, the remainder of this section will focus on helping you understand the universe of space-time effects rather than telling you how to choose among them.

As a simple example, consider the series of monthly total international airline passengers shown in **Figure 2.12**. We see an increasing monthly oscillation around an upward trend. If we want to do *linear* regression and it appears that noise is increasing over time, we likely need a transformation. Passenger numbers are like sales volume—they are always positive and are often discussed in percentage terms. This suggests that we should be working on the log scale. Indeed, **Figure 2.13** shows that log passenger volume has a roughly constant oscillation and a plausibly linear trend.

![](img/315929ad4bddd26368466d02e06e2385_97_0.png)

FIGURE 2.12: International air passengers.

![](img/315929ad4bddd26368466d02e06e2385_97_1.png)

FIGURE 2.13: Same counts on log scale.

Including time as a continuous variable $t$ (i.e., date 1, 2, 3, . . . ) and with month $m_{t}$ denoting the calendar month at time $t$, a regression model that includes a linear time trend and monthly fixed effects is

$$
\log(y_{t})=\alpha+\beta t+\beta m_{t}+\epsilon t.
$$

We can use $glm$ to fit this in R, after creating a time variable and factorizing the months:

```r
month <- factor(airline$Month)
time <- (year-min(year))*12 + airline$Month
air <- glm(log(passengers) ~ time + month)
```

Figure 2.14 shows the fitted values for this regression. It seems that the linear trend and month effects do a nice job of summarizing the passenger traffic (on log scale).

![](img/315929ad4bddd26368466d02e06e2385_98_0.png)

Now de-trending is easy. If your data include dates, then you should create indicator variables for, say, each year, month, and day. The most important thing to remember is to proceed hierarchically: if you are going to include an effect for may-1981, then you should also include broader effects for may and for 1981. This allows the model to use the latter effects as baselines, and the may-1981 effect will only summarize deviations from this base. In the language of Chapter 3, may-1981 will be “shrunk” toward baseline levels for may and 1981. The same logic applies for space: if you condition on counties, then you should also include broader state and region effects.

A more subtle issue is that of *autocorrelation*. Consider the residuals for the passenger regression shown in **Figure 2.15**. There appears to be stickiness in the series: when residuals are high in one month, they are often high the next month. The errors appear correlated in time, such that $\varepsilon_{t}$ is related to $\varepsilon_{t-1}$. That relationship violates our basic *independence* assumption, which holds that $\varepsilon_i \perp\!\perp \varepsilon_j$ for all $j \neq i$.

![](img/315929ad4bddd26368466d02e06e2385_99_0.png)

FIGURE 2.15: Log-count residuals from our passenger regression.

This phenomenon is called *autocorrelation*: correlation with yourself. Time-series data is simply a collection of observations gathered over time. For example, suppose $y_1 \dots y_T$ are weekly sales, daily temperatures, or five-minute stock returns. In each case, you might expect what happens at time $t$ to be correlated with time $t - 1$. For example, suppose you measure temperatures daily for several years. Which would work better as an estimate for today's temperature:

- The average of the temperatures from the previous year?
- The temperature on the previous day?

In most cases, yesterday's temperature is most informative. That means you view the *local* dependence as more important than the broad annual pattern.

You can summarize dependence with an autocorrelation function (ACF) that tracks “lag-$l$” correlations:

$$
\mathrm{acf}(l) = \mathrm{cor}(\varepsilon_t, \varepsilon_{t-l}). \quad (2.32)
$$
