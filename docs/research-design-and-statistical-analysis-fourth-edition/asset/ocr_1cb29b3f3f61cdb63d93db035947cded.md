# # A tibble: 4 x 3

# Groups: sex [Z]
sex employed `n(O)`
<dbl <dbl <int>
1 1 252
2 2 33
3 1 1 184
4 1 2 59

We could use a chi-squared test of independence, finding employment status and sex are not independent:

```
> chisq_test(dat$employed,dat$sex)
# A tibble: 1 x 6
n statistic p df method p.signif
* <int> <dbl <int> <chr>
1 528 13.8 0.000199 1 Chi-square test ***
```

Or, we can use correlation. Testing the correlation does not usually test independence, but it does when both variables are dichotomous:

```
> cor.test(dat$employed,dat$sex)
Pearson's product-moment correlation
```

data: dat$employed and dat$sex
t = 3.8819, df = 526, p-value = 0.0001168
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
0.0827337 0.24867745
sample estimates:

```
cor
0.166887
```

25.7 Our crude measure of education is a significant predictor of depression score for both men and women. When education is included as a predictor along with the three measures of physical activity, education remains a significant predictor of depression score but the activity measures are not (although leisure activity does not miss by much). Clearly, level of education is related to scores on the depression scale.