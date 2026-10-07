# 654 Research Design and Statistical Analysis

It may help to describe the situation using diagrams. When Y is adjusted for the effects of the covariate, X treatment effects are interpreted in terms of vertical separation of the group regression lines instead of the marginal group means. Suppose that the lines in panel of Figure 24.6 represent lines obtained separately for two treatment groups. Parallel lines, illustrated in Panel (a), indicate that the treatment effects are the same for each value of the covariate. In this case, we can identify the treatment effects with the vertical distance between the lines at X. On the other hand, nonparallel lines, illustrated in Panels (b) and (c), indicate that the treatment effects are not the same for each value of the covariate. In Panel (b), the two lines intersect at X = X, but differ considerably for high and low values of X. In Panel (c), there is a separation between the two lines at X = X, but the separation is larger for X and smaller for small X. For Panels (b) and (c), it does not make sense to consider the average separation of the two lines; rather, it is more interest to determine what values of X, if any, the separations are significant.

If the slopes of the population regression lines are reasonably homogeneous as evidenced by parallel lines in the data set, we may proceed with the standard ANCOVA and be confident of conclusions regarding differences between adjusted group means. In practice, researchers will first test the homogeneity of regression slope by testing the interaction of the factor with the covariate (see Section 23.4). The interaction effect can be accomplished with software, assuming that the factor is text and X is the covariate and including the text × X interaction in the model (see Figure 24.5 for R output from this analysis). If the interaction is not significant, as in these data, the ANCOVA is justified. However, many textbooks recommend abandoning ANCOVA if the test is significant. However, the strict dichotomy between equal and unequal slopes is an oversimplification of the problem of comparing regression lines. Small differences in slope may not seriously affect the validity of the ANCOVA and, for large samples, homogeneity may be rejected when the slope differences are small (and conversely, for small samples, the test for homogeneity may not have much power). Therefore, it may be worth proceeding cautiously with ANCOVA even in the presence of modest heterogeneity.

If the group slopes are sufficiently different to cause concern about interpreting the effect of groups in the ANCOVA, it is appropriate to analyze the interaction of the

```
> Anova(data = dat,Y ~ text * X),type=3)
Table (Type III tests)
```

Response: Y

| Sq Df F value Pr(>F)
(Intercept) 0.00290 1 0.1395 0.71069
 0.04765 2 1.1463 0.32755
X 0.13529 1 6.5091 0.01446 *
text:X 0.01412 2 0.3407 0.71325
Residuals 0.87298 42

Sign. codes: 0 **** 0.001 *** 0.01 ** 0.05 * 0.1 . ' 1

Figure 24.5 R output on the test of homogeneity of slope of Y on the different levels of text.