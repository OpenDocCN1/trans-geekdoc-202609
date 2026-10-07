282 Research Design and Statistical Analysis

# 10.7.5 When Variances Are Unequal

Both the Tukey HSD test and the Tukey-Kramer test assume equal variances across treatment so an alternative test is needed when the homogeneity of variance assumption is violated. In Chapter 8, in our analysis of the effects of educational level upon depression scores of males in the Seasons study, we find that the variances were quite heterogeneous. Several methods have been proposed to deal with this problem. Most use Welch's t and $df'$ (see Section 10.3.3) but differ in the criterion which $t'$ is evaluated. In the Games and Howell test (1976), $t'$ is compared with $d_{WE,a,df'} / \sqrt{2}$. The procedure is illustrated in Box 10.5 using the Seasons depression data.

# 10.5 The Games–Howell Procedure for Testing All Pairwise Comparisons When Variances Are Not Equal

+   1. Compute Welch's $t'$ and $df'$, using Equations 6.15 and 6.16. For the HS and C statistics of Table 10.3, Panel $a$, we have:

```
$t' = \frac{\tilde{Y}_{HS} - \tilde{Y}_{C}}{\sqrt{\frac{s_{HS}^2}{n_{HS}} + \frac{s_{C}^2}{n_{C}}}} = \frac{6.903 - 3.674}{\sqrt{\frac{34.541}{19} + \frac{5.970}{33}}} = 2.284$
```

and

```
$df' = \frac{\left(\frac{s_{HS}^2}{n_{HS}} + \frac{s_{C}^2}{n_{C}}\right)^2}{\left(\frac{s_{HS}^2}{(n_{HS}-1)}ight)^2 + \left(\frac{s_{C}^2}{(n_{C}-1)}ight)^2} = \frac{\left(\frac{34.541}{19} + \frac{5.970}{33}\right)^2}{(19)^2(18) + (33)^2(32)} \approx 22$
```

+   2. Obtain the critical value of $f$ from Appendix Table C.8 or R's qtukey function. Using our example with $df=22$, interpolate in Table C.8 between $df=20$ and $df=24$, with $a=4, FWE=.05$. The critical $q$ value is approximately 3.93. Then $t_{0.04,2} = 3.93 / \sqrt{2} = 2.779$

+   3. Because $2.284 < 2.779$, we reject $H_0: \mu_{HS} = \mu_{C}$. In similar fashion, values of $t'$ and $df'$ can be calculated for each of the five pairwise comparisons. Note that the critical value of $t$ must be recalculated for each the $df'$ likely to change for each comparison.

+   4. Alternatively, use the *games_howell_test* function in the [rststat] package in R to see all pairwise comparisons simultaneously. For example, if the data from Table 10.3 is in a data frame called *games_howell_test*, mean\_d ~ educ.level, detailed = TRUE will return all 6 pairwise comparisons, including each $t'$, $df'$, adjusted $p$-value, and confidence interval. The *conf.level* option allows selection of confidence level and thus FWEs.