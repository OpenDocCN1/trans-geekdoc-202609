
# Research Design and Statistical Analysis

for these different types of families. It will be useful to keep in mind that the same test and confidence interval calculations may be applied in every case that we consider. All that changes from one situation to another is the method of determining a critical value of t.

## 10.6 Controlling the FWE for Families of K Planned Contrasts Using Methods Based on the Bonferroni Inequality

We begin with some general methods that are applicable whenever several sets are planned. These methods apply not only to tests of differences among means, but also to tests of hypotheses about other parameters, as proportions or correlations. Note that it is not necessary that the omnibus F be significant prior to testing planned contrasts with the methods described in this section. In fact, power is lost by requiring a significant F before carrying out planned tests with these methods. What is critical that the contrasts are decided before the data are collected and a method for evaluating significance of the tests used that maintains the familywise error rate at or below a reasonable level, presumably .05 or .10.

Equation 10.12 describes the relation between FWE and EC when the K tests are independent. Because this condition holds, a more general statement of the relation is



> $FWE \le 1 - (1 - EC)^K$

In other words, the FWE is to or less than the term on the inequality holding when the tests are not independent. Furthermore, if K tests are conducted with error rates $EC_1, EC_2, \dots, EC_K$,

> $FWE \le \sum_{K} EC_K$

where $EC_K$ is the probability of a Type 1 error for the Kth contrast. The relationship expressed in Equation 10.14 is known as the Bonferroni inequality, and it is the basis for several procedures for testing planned contrasts. From the inequality, it follows that each of the K contrasts that make up the family is tested at $EC = FWE/K$, the probability of a Type 1 error for the family cannot exceed the FWE. For example, if the family contains five planned contrasts, FWE will not be larger than .05 if each contrast is tested at the .01 level.

To illustrate methods based on the Bonferroni inequality, we reconsider the memory experiment results summarized in Table 10.1. Table 10.4 contains an analysis of variance data, including results of the three contrasts we considered earlier (Equations 10.2a–10.2c). The significance values for the three contrasts in Table 10.4(c) are the ECs. According to this criterion, and assuming $\alpha = .05$, the average of the three methods yields significantly better recall than the control condition (Contrast 1), but neither of the other comparisons are significant. However, the reported p-values do not take into consideration the fact that three tests were performed on the means. Therefore, we will consider how each of two methods controls the FWE for this set of three tests.

### 10.6.1 The Dunn-Bonferroni Method (Dunn, 1961)

The Dunn-Bonferroni method for controlling FWE follows from Equation 10.14. If there are contrasts, the FWE will not exceed a nominal value if the EC is set at that value given by K. For example, assuming an FWE of .05, we test the three contrasts in Table 10.1 at the .017 (0.5/3) alpha-level. The statistics are reported in Table 10.4; Equation 10.5 provides the formula for the t when variances are assumed equal, and Equations 10.8-10.10 provide the formulas for the t and df when variances are not assumed equal. If the p-value is available, we can control the FWE by comparing p FWE/K and rejecting $H_0$ only for contrasts where p < FWE/K. Looking at Table 10.4 for our example, we would evaluate each of our contrasts at the .0167 level. Equivalently, the p.adjust function in R's [base] package, with the method = “bonferroni” option, multiplies input vector of p-values by K, where K = the number of tests (i.e., the number of p-values); the resulting adjusted p-values may be compared to any desired α. For example, p.adjust(c(.005, .587, .465), method = “bonferroni”) returns three adjusted p-values (0.015, 1.000, and 1.000), for which the hypothesis corresponding to the first p-value is significant when α = .05.

Table 10.4 Output of tests for three contrasts of means in a memory experiment
(a) ANOVA

| Method | Sum of squares | df | Mean square | F | Sig |
|---|---|---|---|---|---|
| | 173.900 | 3 | 57.967 | 3.230 | .034 |
| Residuals (Error) | 646.000 | 36 | 17.944 | | |

(b) Contrast coefficients

| Contrast | Control | Loci | Image | Rhyme |
|---|---|---|---|---|
| 1 | 3 | -1 | -1 | -1 |
| 2 | 0 | 1 | 1 | -2 |
| 3 | 0 | 1 | -1 | 0 |

(c) Contrast tests

| Contrast | Estimate | Std. error | t | df | Sig. (2-tailed) |
|---|---|---|---|---|
| Assumes equal variances | | | | | |
| 1 | -13.80 | 4.640 | -2.974 | 36 | .005 |
| 2 | 1.80 | 3.281 | 0.544 | 36 | .587 |
| 3 | 1.40 | 1.894 | 0.739 | 36 | .465 |
| Does not assume equal variances | | | | | |
| 1 | -13.80 | 3.902 | -3.537 | 21.949 | .002 |
| 2 | 1.80 | 3.345 | 0.538 | 20.466 | .596 |
| 3 | 1.40 | 2.112 | 0.660 | 17.672 | .518 |

Confidence intervals based on FWE have a form like those we encountered in Chapter 6 (see Equation 6.11); in general,

$CI = \hat{\psi} \pm t_{FWE/K}S_{\psi}$

Consider Contrast 1 in Table 10.4. Inserting from Table 10.1, we have

$\hat{\psi}_1 = (3)(6) + (-1)(2) + (-1)(7) + (-1)(5) = -13.80$

Assuming equal, the standard error of this contrast is given in Table 10.4 as 4.640; it is calculated as in the denominator of Equation 10.5:

$s_{\hat{\psi}} = \sqrt{\frac{MS_{}}{n}}$

The critical value of $t$, $t_{FWE}$, can be obtained using the $qt$ function in R assuming $df=36$ and two-tailed $p=0.0167$; $qt(0.0167/2, df=36, lower.tail=FALSE)$ returns a $t$ value of 2.51. Alternatively, $t$ can be interpolated from Appendix C.6. Substituting values into Equation 10.5, the confidence bounds for $\psi_1$ are

$CI = -13.80 \pm (2.51)(4.640) = [-25.446, -2.54]$

We are not quite done. Our coefficients were 1, -1/3, -1/3, and -1/3 and multiplied by 3 to use integer weights. We return to the original scale by dividing the interval bounds by 3, finding -8.48 and .717. We would follow the procedure for constructing confidence intervals for the other contrasts in our example.

When confidence intervals are based on the FWE, they are interpreted differently when they are based on the EC. It may help to understand the difference if we assume random replications of the memory experiment. In each replication, a set of three intervals, each of the planned experiments in Table 10.1, is calculated. We expect that in 95% of the replications, all intervals will contain the true (population) value of the contrast. Thus, we are 95% confident that all the confidence intervals in the family are accurate statements; that is, we are 95% confident that all three intervals contain the value of the population parameter being estimated.

### 10.6.2 Hochberg's Sequential Method (1988)

Sequential methods (also referred to as stepwise, or multest) test contrasts in several stages. Some of these methods such as Duncan's (1955) and Newman-Keuls (Keuls, 1952; Newman, 1939) fail to adequately control the Type 1 error rate and will not be considered. A limitation of all sequential methods is that confidence limits cannot be calculated. However, sequential methods confer a power advantage over the Dunn-Bonferroni procedure if the researcher is solely interested in a set of tests.

There are several methods for controlling FWE for a family of planned hypothesis tests. The simplest of these are Holm's sequentially rejective method (1979), and Hochberg's step-up method (1988). The Hochberg method is the more powerful of the two; it is described in Box 10.2. The power of this procedure can be increased, but at the cost of greater complexity (Hommel, 1988; Rom, 1990).

**Box 10.2 Hochberg's (1988) Sequential Testing Method**

1. Order the K contrasts according to their p-values with $p_i$ being the smallest and $p_k$ being the largest. In the example of Table 10.4, the contrasts would be ordered: $\psi_j, \psi_i,$ and $\psi_k$.
2. If $p_k \le FWE$, all null hypotheses are rejected. If not, consider the next largest p-value, $p_{k-1} \le FWE/2$, reject the null hypothesis corresponding to $k-1$ and all remaining contrasts. If this test is not significant, test whether $p_{k-2} \le FWE/3$, and so on. Using the example and assuming $FWE=.05$, we first compare .587 with .05. This fails and we compare the next largest p-value, .033, against .05/2 or .025. This is the only significant contrast, so we can reject only $H_{\psi_i}: \psi_i = 0$.
4. Equivalently, in R the $p.adjust$ function in [base], with method = "hochberg" option, multiplies an input vector of p-values by $K$, where $K=1$ for the largest p-value, 2 for the next largest, and so on. These adjusted p-values may be compared to any preferred $\psi_i$. For the contrasts in Table 10.4, $p.adjust(.033, .005, .587, method = "hochberg") returns 0.066, .015, and .587. With $\alpha=.03$, we can reject only $H_{\psi_i}: \psi_i = 0$.

## 10.7 Testing All Pairwise Contrasts

### 10.7.1 The Studentized Range Statistic

We present several methods for controlling FWE across pairwise comparisons; all the methods are based on $q$, the Studentized range statistic. This statistic is the range of a set of observations from a normally distributed population, divided by the estimated standard deviation of the population. If the observations group means,

$q = \frac{\bar{Y}_{max} - \bar{Y}_{min}}{S_{\bar{Y}}} \quad (10.16)$

