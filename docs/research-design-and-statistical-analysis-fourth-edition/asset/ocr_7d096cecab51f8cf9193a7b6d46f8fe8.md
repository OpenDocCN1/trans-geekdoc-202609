# ANCOVA as a Special Case of Multiple Regression 651

except that the comparison is among adjusted means and the error term contains corrections for the covariate. For a completely randomized design, the recommended test statistic is

```
$$\hat{\Psi}_{\psi(adj)} = \frac{\hat{Y}_{HE(adj)} + \hat{Y}_{LE(adj)}}{2}$$\n$\hat{S}_{\psi(adj)} = \sqrt{\frac{\sum w_i^2}{n_j} (1 + \frac{MS_{S(A)}}{MS_{S(A/X)}})}$$$
```

where $MS_{S(A)}$ and $SS_{S(A/X)}$ are the between-participant mean square and the within-participant sum of squares when an ANOVA is with the covariate as the dependent variable and A as the treatment factor. Substituting into the equation, we have

```
$$\hat{t}_{\psi(adj)} = \frac{.534 - .419/2}{\sqrt{(.020)(1.5/16)}(1 + \frac{184.333}{9170.312})} = .135 / .044 = 3.089$ with 44 df$$
```

We can reject the null hypothesis at $p = .003$. We observed a larger value of the test statistic using the adjusted means, although we lost one error degree of freedom. In this example, the numerator of the $t$ ratio is slightly larger for the adjusted means than for the unadjusted means. However, the main source of the difference in the $t$ values is attributable to the smaller error term after adjusting for the covariate (.044) than before the adjustment (.054).

The procedure used for testing contrasts of adjusted means is appropriate when participants are assigned at random to treatments. However, in observational studies where participants are not randomly assigned to conditions, the recommended error term is different; specifically, it contains a correction that depends on the specific contrast that is tested,

```
$$\hat{S}_{\psi(adj)} = \sqrt{\frac{\sum w_i^2}{n_j} + \frac{(\sum w_i \hat{X}_i)^2}{SS_{S(A/X)}}}$$$
```

This equation follows from the expression for the standard error of a predicted score when we considered bivariate regression. The implication for performing analysis is that researchers must select the error term that is appropriate to their research design. For a good discussion of these issues, see Huitema (1980).

```
> summary(aov(data=dat, X ~ text))
Df Sum Sq Mean Sq F value Pr(>F)
text 2 369 184.3 0.905 0.412
Residuals 45 9170 203.8
```

Figure 24.4 R results of ANOVA with X as the dependent measures and text as the treatment factor.