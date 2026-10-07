# 286 Research Design and Statistical Analysis

“after the fact” we are capitalizing on chance and, in effect, investigating the family of all possible outcomes. Therefore, the methods we present are quite conservative because they control the probability of at least one Type 1 error in a very large set of possible contrasts.

# 10.9.1 Scheffé’s Method

Assuming that the populations are normally distributed and have equal variances, Scheffé’s (1959) method maintains the FWE at its nominal level when the family consists of all possible contrasts associated with a source of variance. With the fifth-to-eighth multiplication speeds in the study by Royer et al. (1999) as an example, we assumed that we not anticipated the pattern of means in Table 10.2. After viewing the data, we observe that the sixth-eighth grades had very similar means, higher than the fifth-grade mean. We might wish to test whether the mean of the fifth-grade response times differs significantly from that of the three sixth-to-eight grades. Box 10.8 describes the Scheffé procedure and illustrates its application to the contrast of the fifth-grade mean with the average of the other three means.

10.8 Scheffé’s Method to Test $H_0: (1/3)(\mu_i + \mu_j) - \mu_s = 0$ (Royer Speed Data)

+   1. Calculate the t statistic to test the contrast of interest (see Equation 10.5).
2. Compare the computed value of $t$ with $S = \pm\sqrt{df_1 \cdot F_{FWE,df_1,df_2}}$ where $df_1$ and $df_2$ are the numerator and denominator degrees of freedom.
3. For the arithmetic experiment, $df_1 = 3$ and $df_2 = 36$; if FWE = .05, the critical F is approximately (from Appendix Table C.5) $F_{FWE,df_1,df_2} = 2.88$. Therefore,

$S = \pm\sqrt{(3)(2.88)} = 2.94

+   4. Reject the null hypothesis $t > S$ or $t < -S$. To test the null hypothesis, $t = 5.23$. Because $5.21 > 2.94$, we reject $H_0$.
5. The formula for the confidence interval is

$\hat{\psi} \pm s_{\psi}\sqrt{df_1 \cdot F_{FWE,df_1,df_2}}$

where $\hat{\psi} = .680$ and $s_{\psi} = \sqrt{MS_{S/A}(\sum\mu_i^2 / n_i)} = .130$. Therefore, the bounds on $(\mu_i + \mu_j + \mu_k) - 3\mu_s$ are $.680 \pm (1.130)(2.94) = [.298, 1.062].

+   6. To return to original scale, these bounds must be divided by three; the bounds $(1/3)(\mu_i + \mu_j + \mu_k) - \mu_s$ are $.099$ and $.354$.
7. Alternatively, using the SchefféTest in the [DescTools] package in R. It takes an $aov$ model as input, as well as a vector or matrix of the contrast or contrasts of interest, and returns $\psi$ and confidence intervals. For example, SchefféTest(aov(data = M, M_Speed = grade), contrasts = list(c(-1, 1/3, 1/3, 1/3))) provides the same values as in step 6.