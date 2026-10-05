388

10 Inference for Regression

We then use the get_ci() function with level = 0.95 to compute the 95% confidence interval for $\beta_1$. Note that setting the point_estimate argument to the observed_slope of 0.371 sets the center of the confidence interval.

```
se_ci <- bootstrap_distn_slope |
get_ci(level = 0.95, type = "se", point_estimate = observed_slope)
se_ci
```

```
# A tibble: 1 x 2
lower_ci upper_ci
<dbl>
1 0.311278 0.430912
```

The resulting standard error-based 95% confidence interval for $\beta_1$ of (0.311, 0.431) is slightly different than the percentile-based confidence interval. Note that neither of these confidence intervals contains 0 and are entirely located above 0. This is suggesting that there is in fact a meaningful positive relationship between waiting times and duration for Old Faithful eruptions.

# 10.3.2 Hypothesis test for population slope using infer

Let's know a hypothesis test of $H_0 : \beta_1 = 0$ vs. $H_A : \beta_1 \neq 0$. We will use the infer package, which follows the hypothesis testing paradigm in the “There is only one test” in Figure 9.11.

Let's first think what it means for $\beta_1$ to be zero as assumed in the null hypothesis $H_0$. We recall if $\beta_1 = 0$, then this is saying there is no relationship between the waiting time and duration. Thus, assuming this null hypothesis $H_0$ means in our “hypothesized universe” there is no relationship between waiting and duration. consequence.

We construct the null distribution of the fitted slope $b_1$ by performing the steps that follow. Recall from Section 9.3 on terminology, notation, and definitions related to hypothesis testing where we defined the null distribution: the sampling distribution of our test statistic $b_1$ assuming the null hypothesis $H_0$ is true.

+   1. specify() the variables of interest in old_faithful_2024 with the formula: 
waiting ~ duration.

+   2. hypothesize() the null hypothesis of independence. Recall from Section 9.4 that this is an additional step that needs to be added for hypothesis testing.

+   3. generate() replicates by permuting/shuffling values from the original sample of 114 eruptions. We generate reps = 1000 replicates using type = "permute" 
here.

+   4. calculate() the test statistic of interest: the fitted slope $b_1$.