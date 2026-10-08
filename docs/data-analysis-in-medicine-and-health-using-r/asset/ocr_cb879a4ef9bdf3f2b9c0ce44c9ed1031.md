# 10.6 Quasi-Poisson Regression for Overdispersed Data

We utilized family "quasipoisisson" option in the glm specification before just to easily obtain the scaled Pearson chi-square statistic without knowing what it is. So, what is a Quasi-Poisson regression? For a typical Poisson regression analysis, we rely on maximum likelihood estimation method. It assumes that the mean (of the count) and its variance are equal, or variance divided by mean equals 1. For that reason, we expected scaled Pearson chi-square statistic to be close to 1 so as indicate good fit of the Poisson regression model.

So if this assumption of "mean variance" is violated? Whenever the variance is larger than the mean for that model, we can call this overdispersion. In particular, it will affect a Poisson regression model by underestimating the standard errors of the coefficients. So, we may have narrower confidence intervals and smaller p-values (i. more likely to have false positive results) than we could have obtained. In handling the overdispersion issue, one may use a negative binomial regression, or more flexible by using quasi-Poisson regression that relies on quasi-likelihood estimation method (Fleiss et al., 2003).

To demonstrate a quasi-Poisson regression is not difficult because we already did that when we wanted to obtain scaled Pearson chi-square statistic before in the previous sections. As an example, we repeat the same model for count. We fit the standard Poisson regression model,

```
pois_attack_all1 = glm(attack ~ , data = asthma, family = "poisson")
```

Then we fit the same model using quasi-Poisson regression,

```
qpois_attack_all1 = glm(attack ~ , data = asthma, family = "quasipoisisson")
```

Now, pay attention to the standard errors and confidence intervals of each model. You can spot the differences between the two? (Hints: std.error, p.value, conf.low and conf.high columns).

```
# Poisson
tidy(pois_attack_all1, conf.int = TRUE)
```

```
## A tibble: 4 x 7
## term estimate std.error statistic p.value conf.low conf.high
## <chr> <dbl <dbl <dbl <dbl <dbl>
```