# Table 11.3 Tukey's HSD test for pairwise comparisons of the organizational means

```
> m<-pairs(emmeans(memout,-Org)) #Tukey's HSD for pairwise comparisons of Organization
NOTE: Results may be misleading due to outcome in interactions
m
```

| contrast estimate SE df t_ratio p.value |
|---|---|---|---|---||
| A - N | 5.39 | 1.1 | 189 | 4.889 | <0.001 |
| A - R | 7.35 | 1.1 | 189 | 6.661 | <0.0001 |
| N - R | 1.95 | 1.1 | 189 | 1.772 | 0.1819 |

Results are averaged over the levels of: Delay
P value adjustment: tukey method for comparing a family of 3 estimates
> conf(e)#confidence intervals for these differences

| contrast estimate SE df lower_Cl upper_Cl |
|---|---|---|---|---||
| A - N | 5.39 | 1.1 | 189 | 2.788 | 8.00 |
| A - R | 7.35 | 1.1 | 189 | 4.742 | 9.95 |
| N - R | 1.95 | 1.1 | 189 | -0.651 | 4.56 |

Results are averaged over the levels of: Delay
Confidence level used: 0.95
Conf-level adjustment: tukey method for comparing a family of 3 estimates

> Note: The standard error for these tests = $\sqrt{MS_{error}(2/66)}$ the use of the error mean square from the ANOVA results based on the assumption of homogeneity of variance, and it is the number of scores at each organizational level.

and the mean of the subsequent levels. Similarly, in R, the command contrasts(datOrg) <- contr.helmmert(3) assigns contrasts to the Org factor of the data frame called dat, which has three levels. In this case, the comparisons are between each level of the factor and the mean of the previous levels, thus R's "contr.helmmert" contrasts are sometimes reverse Helmert or difference contrasts. Using named contrasts like this requires careful attention to the levels within the factor of interest. Additionally, the meaning of "helmert" (and other named contrasts) can vary across software, it is wise to confirm that the contrasts being calculated are those you intended.

The results of the Helmert contrasts are summarized in Table 11.4. The significance level reported here is not adjusted for the fact that the test was post hoc. Therefore, to evaluate significance, use the Scheffé criterion as in Box 10:8.

+   1. From Table 11.4, calculate t by dividing the contrast by the standard error (6.37, 955) = 6.67.
2. Compare the computed value t 6 with $\sqrt{df_1 \cdot F_{0.5,df_1,df_2}} = \sqrt{2F_{0.5,189}} = 2.47$.
The result is significant.
3. The confidence interval also fail to take into consideration that the test is post hoc. From Chapter 10, the bounds are

CI bounds = $\hat{\phi} \pm s_s$
= 6.37 + (.955)(2.47)
= 4.01, 8.73