# More About Correlation 477

of these samples and ordering them. If we bootstrapped 1,000 samples, the 95% confidence interval for ρ would be defined by the 25th and 975th largest correlations; the 90% confidence interval would be defined by the 50th and 95th largest correlations. In SPSS, begin the analysis as described in Section 18.2.4, then click on the Bootstrap bar and tick the box to Perform bootstrapping. A desired Number of samples, recognizing that running more samples results in better defined but also takes more time to run. We recommend no fewer than 1,000 samples. For the third-graders in the Royer data set, a bootstrap of the 28 children with both multiplication and accuracy scores resulted in confidence bounds of .152 and .830 for 1,000 bootstrapped samples, .165 and .823 with 10,000 samples; both intervals are wider than the CI based on the Fisher transformation discussed in Section 18.2.3 (.274 to .788). Bootstrapping in R is extremely flexible and runs much more quickly than in SPSS, but does require some modest amount of coding ability and the use of the boot.ci functions in the [package]. An example is included in Appendix 18.2.

# 18.2.6 Testing Independent Correlations Differ

Another question is to ask about relationships between two variables is whether they differ in magnitude. For example, the relationship between high school GPA and college GPA differ for people who identify as men and those who identify as women or nonbinary? It is possible to test whether the correlation between X and Y is the same in two different populations. We can test H$_0$: ρ$_1$ = ρ$_2$ by using the test statistic

```
$z = \sqrt{rac{1}{N_1-3} + rac{1}{N_2-3}}$ $ (18.4)
```

As an example of using Equation 18.4 with real data, the correlation between subtraction and multiplication accuracy for the 28 third-graders in the Royer data set is .594; for the 25 fifth-graders, it is .225. To determine whether these correlations are significantly different at α = .05, we can substitute in Equation 18.4. If we do so, we obtain

```
$z = (.684 - .229) / .292 = 1.56$
```

This is less than the upper critical value of z$_{crit}$ = 1.96, so we do not have sufficient evidence to reject the null hypothesis that the correlations in the populations of third- and fifth-graders are equal.
Suppose we want to run the study again with a larger sample. We can readily do a priori power calculations for this test if we are willing to specify the size of the effect, q = Z$_1$ - Z$_2$. For example, if we assume that the two population correlations are .594 and .225, so that q = .684-.229 = .455, we can use G*Power 3.1 to show that the sample size necessary to have power = .90 for a two-tailed test of H$_0$: ρ₁ = ρ₂ at α = .05 in each group (see Figure 18.4). However, we should be cautious using these calculations when we design research using correlations from small samples. The 95% CI for the correlation between subtraction and multiplication accuracy for third-graders extends from .284 to .792, and the 95% CI for fifth-graders extends from -.206 to .583. In this situation, we should perform several different power calculations to assess the magnitude of the task