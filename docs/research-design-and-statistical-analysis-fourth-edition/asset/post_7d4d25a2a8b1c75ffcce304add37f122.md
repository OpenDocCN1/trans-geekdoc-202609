
## Research Design and Statistical Analysis

As always, when several contrasts are tested, we should control Type 1 error across the set of comparisons. The procedures for controlling familywise error (FWE) rate were discussed in Chapter 10. If there are several planned contrasts, we can use the Dunn-Bonroni method. For post hoc contrasts, if we wish to use the Scheffé test, the t statistics obtained earlier can be referred to the criterion $[|t|]_{FWE,N,a-1}$. For the Tukey hoc test of pairwise differences, the same test statistic can be used with +1 and -1. If the covariate is a fixed-effect variable, the test statistic is referred to $q_{FWE,a}/\sqrt{f2}$, where $q$ is a critical value of the Studentized random statistic which was used with the Tukey test in Chapter 10. There is one consideration in the current context: if the covariate is a random variable, as is usually the case, Bryan and Paulson (1976) show that $q$ should be replaced by $q_{FWE,a}$, a value of the Studentized random statistic in which is the number of covariates. Tables of the generalized Studentized random statistic are available in Huite 1980 and Kirk 1995) or using the Tukey function in R (see Section 10.7.1).

## Using Software to Adjust Means and Test Contrasts

To adjust the means for the covariate in R, use the effect function in the [effects] package. It takes as the results of an ANCOVA and information on which to be adjusted: `effect("text, ancova")` returns the adjusted means for each level of the test factor. In SPSS, use the ANCOVA as described in Section 24.2, then click the EM Means bar and move text to the box labeled Display Means, click Continue and OK. The adjusted means will appear as Estimated Means and a footnote to tell you of the value of the covariate that was used for the adjustments (i.e., $X=62.35$).

To compute contrasts in R, we can set up a matrix of contrasts as described in Box 10.1. Include the option `contrasts=list(test=mat)` in the `lm` function described in Section 24.2: `summary(lm(data=data, Y ~text + X, contrasts=list(test=mat)))` provides the estimates using adjusted means, their standard errors, and significance tests.

In SPSS, the test conditions are ordered alphabetically (HE, LE, S), so we should be able to compute the contrast using the Helmert contrasts that are available from the Contrast within the ANCOVA. However, doing so produces an erroneous value of the contrast, suggesting a bug in the software. This serves as a clear reminder to check results against known values to confirm that the calculations are as expected. As an example, we confirmed that the Helmert contrasts in SPSS accurately reproduce the contrast with unadjusted values from an ANOVA on these data; only the ANCOVA contrasts are faulty.

## 24.4 Assumptions and Interpretation in ANCOVA

When ANCOVA is used instead of ANOVA, increases in power may be achieved at the cost of greater complexity and more assumptions. The standard assumptions for ANCOVA break down into two groups. In ordinary ANOVA, some assumptions are necessary for the ratio of adjusted means to be distributed as F. However, unless certain assumptions are made, the ANCOVA F may test a different null hypothesis than ordinary ANOVA, and the adjusted means may be biased estimates of the population means. With most other regression-related procedures, given that we have access to sophisticated statistical software, the computations are the least of our worries. As always, the greatest lies in interpretation. We now discuss the assumptions underlying ANCOVA and the consequences of violating them.

### 24.4.1 Normality and Homogeneity of Variance

In ANCOVA, it is assumed that the conditional distributions of Y at different values of X are normal and have equal variances, just as in regression. In general, the consequences of violating assumption are similar to those for ANOVA, with the exception that they depend to some extent on the distribution of the covariate (see Huitem, 1980, for a more detailed discussion of these assumptions). ANCOVA is unlikely to be severely biased by violations of the normality and homogeneity of variance assumptions provided there are equal numbers of participants in each group and the covariate itself is normally distributed.

### 24.4.2 Linearity

As we have so discussed, ANCOVA adjusts for differences in the covariates by removing the variability accounted for by a linear regression on X. If there is a systematic component to the relationship between X and Y, the use of linear regression will not remove all the variability in Y potentially accounted for by X. The effect of moderate nonlinearity is a slight negative bias in the ANCOVA F test. However, strongly nonlinear relationships result in severely biased F tests if ANCOVA is used (Artiquoll, 1964). Consider, for example, a situation where there is a quadratic component to the relationship between Y and the covariate. If the curvature is ignored and the $X^2$ in the model is omitted, it will contribute to the error component, resulting in bias.

If the nature of the nonlinearities is complex, transformations of Y or polynomial ANCOVA (see 24.7.3) may be used. It is recommended that the linearity assumption be checked as a preliminary step in using ANCOVA. Plotting the scatter diagrams for each group offers a quick check and a significance test for nonlinearity which has previously been discussed.

### 24.4.3 Assumption of Homogeneity of Regression Slopes

In ANCOVA we adjust for differences in the covariates by using regression. In doing so, for each group we use a common slope. ... [Note: The provided OCR seems to have repetitive/disrupted sections in the source between page breaks; based on the text provided, the logical flow is reconstructed below.]

(Note: The text "ANCOVA as a Special Case of Multiple Regression 653" appears to be a header/footer in the original document and is integrated into the flow below.)

## Research Design and Statistical Analysis (Cont.)

... [The text continues based on the provided OCR segments] ...

If the slopes of the population regression lines are reasonably homogeneous as evidenced by parallel lines in the data, we may proceed with the standard ANCOVA and be confident of conclusions regarding adjusted group means. In practice, researchers will first test the homogeneity of regression slope by testing the interaction of the factor with the covariate (see Section 23.4). The interaction effect can be accomplished with software, assuming that the factor is text and X is the covariate and including the text × interaction in the model (see Figure 24.5 for R output). If the interaction is not significant, as in these data, the ANCOVA is justified.
