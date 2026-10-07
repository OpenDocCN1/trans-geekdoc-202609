# ANCOVA as a Special Case of Multiple Regression

According to Cohen's rough guidelines, large, medium, and small effect sizes in ANOVA correspond to f values of .40, .25, and .10, respectively. If we use these values in G*Power 3.1 for ANOVA and choose

+   1. F tests the Test Family;
2. ANOVA, fixed effects, omnibus, one-way as the Statistical test;
3. A priori: Compute required sample size – given α, power and effect size as the Type of power analysis;

then insert Number of groups = 3 (as in the current example), α = .05, and desired power = .80, and we find that the required numbers of participants per group are 22, 53, and 323, respectively.

The major change when we perform calculations for ANCOVA is that the variance, σ², is adjusted for differences in the covariate and should be smaller; is, σ²ANCOVA = σ²(1 - ρ²), where ρ is the within-groups correlation between the dependent variable and covariate. Therefore, for ANCOVA, the quantity that should be used in place of f_ANCOVA in G*Power 3.1

```
$f_{ANCOVA} = f_{ANOVA} \frac{1}{\sqrt{1-\rho^2}}$ (24.6)
```

For large values of ρ, f_{ANCOVA} can be much larger than f_{ANOVA}; therefore, power may be considerably larger for an ANCOVA than for the corresponding ANOVA, and the required sample sizes will be smaller.

In the current example, the correlation between proportion correct on the test and test score is approximately .6 in each of the tests. If we substitute ρ = .6 into Equation 24.6, we see that the ANOVA f values are each multiplied by $\sqrt{1/(1-.6^2)}$ = 1.25 when we perform ANCOVA power calculations. For large, medium, and small ANOVA effect sizes, we find that the required numbers of participants in each group for α = .05 are .3125, and .124. Using G*Power 3.1, we find that power = .80 are 14, 34, and 210 for medium, and small effect sizes, smaller than the group sizes of 22, 52, and 323 found earlier for ANOVA. (The same estimated sample sizes are found in G*Power using the ANCOVA f values whether the statistical test is ANCOVA or ANOVA.) If the within-group correlations between the covariate and the dependent are smaller, r = .3, the power advantage for ANCOVA is reduced. The ANOVA f values are now multiplied by a smaller number, $\sqrt{1/(1-.3^2)}$ = 1.048, so that the ANCOVA sample sizes required to achieve power = .80 are 20, 48, and 294, respectively.

# 24.7 Extensions of ANCOVA

# 24.7.1 Factorial ANCOVA

The multiple regression approach to ANCOVA can be readily extended to factorial designs. For example, if we consider a two-factor design described in the previous section, the ANCOVA tests for A, C, and AC are provided by