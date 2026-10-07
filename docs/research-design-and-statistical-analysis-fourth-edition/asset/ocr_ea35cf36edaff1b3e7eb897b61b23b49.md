# Contrasting Means in Between-Subjects Designs 277

Hochberg's step-up method (1988). The Hochberg method is the more powerful of the two; it is described in Box 10.2. The power of this procedure can be increased, but at the cost of greater complexity (Hommel, 1988; Rom, 1990).

**Box 10.2 Hochberg's (1988) Sequential Testing Method**

1 Order the K contrasts according to their p-values with $p_i$ being the smallest and $p_k$ being the largest. In the example of Table 10.4, the contrasts would be ordered: $\psi_j, \psi_i,$ and $\psi_k$.
2 If $p_k \le FWE$, all null hypotheses are rejected. If not, consider the next largest p-value, $p_{k-1} \le FWE/2$, reject the null hypothesis corresponding to $K-1$ contrast and all remaining contrasts. If this test is not significant, test whether $p_{k-2} \le FWE/3$, and so on.
3 Using the example of Table 10.4 and assuming $FWE=.05$, we first compare .587 with .05. This fails and we compare the next largest p-value, .033, against .05 /2 or .025. This is the only significant contrast, so we can reject only $H_{\psi_i}: \psi_i = 0$.
4 Equivalently, in R the $p.adjust$ function in [base], with method = "hochberg" option, multiplies an input vector of p-values by $K$, where $K=1$ for the largest p-value, 2 for the next largest, and so on. These adjusted p-values may be compared to any preferred $\psi_i$. For the contrasts in Table 10.4, $p.adjust(.033, .005, .587, method = "hochberg") returns 0.066, .015, and .587. With $\alpha=.03$, we can reject only $H_{\psi_i}: \psi_i = 0$.

To summarize, the choice between the Dunn-Bonferroni and the Hochberg methods depends on whether the researcher wants confidence intervals. The Hochberg method is more powerful when conducting hypothesis tests but does not yield confidence intervals. Both the Sidak and Hochberg methods are available in SPSS, but the results are based on comparisons of members of all pair of groups.

# 10.7 Testing All Pairwise Contrasts

# 10.7.1 The Studentized Range Statistic

We present several methods for controlling FWE across pairwise comparisons; all the methods are based on $q$, the Studentized range statistic. This statistic is the range of a set of observations from a normally distributed population, divided by the estimated standard deviation of the population. If the observations group means,

```
$q = \frac{\bar{Y}_{max} - \bar{Y}_{min}}{S_{\bar{Y}}} \quad (10.16)
```