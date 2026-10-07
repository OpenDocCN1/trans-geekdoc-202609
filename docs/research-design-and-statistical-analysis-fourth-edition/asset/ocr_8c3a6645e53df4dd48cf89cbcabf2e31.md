# Integrated Analysis I 175

> > t.test(data = dat, Y ~ Method) #two-sample Welch's t'

```
data: Y by Method
t = -1.586, df = 47.291, p-value = 0.1355
alternative hypothesis: true difference in means between group Control and group Drug is not equal to 0
95 percent confidence interval:
-3.5332902 0.4932902
sample estimates:
mean in group Control   mean in group Drug
16.84                   18.36
```

Figure 7.3 Results of Welch's t test on the means in Table 7.1.

Y — Method, you can read as an instruction to compare Y as a function of Method using an unequal-variance independent groups test, we obtain the result in Figure 7.3. A comparable analysis in SPSS is the independent t test in the Compare Means and Proportions section of analysis pull-down menu (see Section 6.4.5).
Three points are apparent from the:

+   1. The observed t is negative because t.test compares the conditions in alphabetical order: Control — Drug has a mean of -1.52. It doesn't matter which condition is called Y and which is Y, in Equation 6.16; the statistical conclusions are the same.
2. The confidence interval for the difference between the means is, ranging from -3.5 to 0.49, meaning a benefit of the drug that 3.5 items reached, a disadvantage of half an item, on. The true population difference either is or not contained within the confidence interval. If we repeated this experiment many times, 95% of the resulting confidence intervals would include the population difference.
3. Presumably, we are only interested if the drug has an advantage. Therefore, the alternative to the null hypothesis is one-tailed and the reported p-value of .136 should be halved (or we could use a one-tailed test using t.test(data = dat, Y ~ Method, alternative = “less”); either way, the one-tailed test yields p = .068. Thus, by conventional criteria, we cannot reject the null hypothesis of no difference between the two population means.

# 7.6 The Standardized Effect Size (Cohen's d)

The difference between group means is one measure of the effect of the drug. The standardized effect size provides an measure that takes the variability into account. From Equation 6.19, $d = (ar{Y}_{drug}-ar{Y}_{control})/s_{pooled}$. When the ns are equal, the pooled variance is the average of the two variances. From the values in Table 17.1, $s_{pooled}^2 = 1/2(3.115^2+7.492^2)$, or 12.522. The square root of the pooled variance is 3.539, therefore, $d = (18.36-16.84)/3.539 = .43$. By Cohen's (1988) guidelines, this is close to a medium-size effect for the comparison of two independent means. However, using the getbesg function in R (see Section 6.7.2), we found the 95% confidence interval bounds on the effect size to -.13 and 1.02, indicating that the population effect was somewhere between a very small advantage of the placebo and a very large advantage of the memory pill. Once again, we lack strong evidence that the pill aids memory.