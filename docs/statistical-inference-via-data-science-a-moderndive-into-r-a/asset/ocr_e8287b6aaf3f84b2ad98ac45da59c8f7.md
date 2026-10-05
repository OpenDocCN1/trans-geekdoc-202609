The construction of a 95% confidence interval for $eta_0$ follows exactly the same steps using $b_0, SE(b_0)$, and the same critical value $q$ as the degrees of freedom for the $t$-distribution are exactly the same, $n-2$:

```
$b_0 \pm q \cdot SE(b_0) =79.459 \pm 1.981 \cdot 7.311 ==(-14.112, 14.854)$
```

The results of the confidence intervals are valid only if the linear model assumptions are satisfied. We discuss these assumptions in Section 10.2.6.

# 10.2.4 Hypothesis test for population slope

To perform a hypothesis test for $eta_1$, the general formulation of a two-sided test is

```
$H_0 : \beta_1 = B \nH_A : \beta_1 \neq B$
```

When $B$ is the hypothesized value for $eta_1$. Recall the terminology, notation, and definitions related to hypothesis tests we introduced in Section 9.3. A hypothesis test consists of a test between two competing hypotheses: (1) a *null hypothesis* $H_0$ versus (2) an *alternative hypothesis* $H_A$.

# Test statistic

A *test statistic* is a point estimator used for hypothesis testing. Here, the $t$-test statistic is given by

```
$t = \frac{b_1 - B}{SE(b_1)}$
```

This test statistic follows, under the null hypothesis, a $t$-distribution with $n-2$ degrees of freedom. A particularly useful test is whether there is a linear association between the explanatory variable and the response, which is equivalent to testing:

```
$H_0 : \beta_1 = 0 \nH_1 : \beta_1 \neq 0$
```

For example, we may use this to determine whether there is a linear relationship between the duration of the Old Faithful geyser eruptions (*duration*) and the waiting time to the next eruption (*waiting*). The *null hypothesis* $H_0$ assumes that the population slope $eta_1$ is 0. If this is true, there is *no linear relationship* between the *duration* and waiting times. When performing a hypothesis test, we assume that the null hypothesis $H_0 : \beta_1 = 0$ is true and try to find evidence against it based on the data observed.