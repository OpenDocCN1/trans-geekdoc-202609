# 750 Answers to Selected Exercises

(c) The new error MS is [(18)(32) + (40)(30)] / (18 + 40) = 30.621

| Source | df | MS | |
|---|---|---||
| M | 1 | 3627 | $\sigma_e^2 + 4\sigma_{G/M}^2 + 40\sigma_M^2$ |
| X | 1 | 128 | $\sigma_e^2 + 400\sigma_X^2$ |
| MX | 1 | 123 | $\sigma_e^2 + 20\sigma_{MX}^2$ |
| G/M | 18 | 420 | $\sigma_e^2 + 4\sigma_{G/M}^2$ |
| Pooled error | 58 | 30.62 | $\sigma_e^2$ |

The new error MS is [(18)(32) + (40)(30)] / (18 + 40) = 30.621.

+   (d) $F_M (1,18) = 3627 / 420 = 8.64$ is unchanged from part (a); $F_X (1,58) = 128 / 30.62 = 4.18, p = .045$ (significant); $F_{MX} (1,58) = 123 / 30.62 = 4.02, p = .050$ (significant).
(e) The ratio for a test of GX/M is approximately 1, indicating that this potential source of variability does not contribute to the variance in the population.

# Chapter 10

+   10.1) $H_0: .5(\mu_{F1} + \mu_{F2}) - \mu_c \ge 0; H_a: .5(\mu_{F1} + \mu_{F2}) - \mu_c < 0$. To test $H_0$, calculate
nt = \frac{.5(14.6 + 14.9) - 13.8}{\sqrt{MS_{S/A}\frac{5^2 + 1^2}{20}}} = 1.734$. The $MS_e$ is based on five with 20 cells per group, or $5(20-1) = 95$ df. $1 - pt(1.734, 95) = 0.043 = p$-value.
(b) $H_0: .5(\mu_{F1} + \mu_{F2}) - \mu_c = 0; H_a: .5(\mu_{F1} + \mu_{F2}) - \mu_c \neq 0. =(.5(11.8 + 11.7) - 13.8) = -.548$ which is clearly significant, $p < .0002$.
(c) $H_0: .5(\mu_{F1} + \mu_{F2}) - .5(\mu_{F1} + \mu_{F2}) = 0; H_a: .5(\mu_{F1} + \mu_{F2}) - .5(\mu_{F1} + \mu_{F2}) \neq 0$.
t(t) = \frac{(14.6 + 14.9) - (11.8 + 11.7)}{2}}{\sqrt{\frac{4(5^2 + 5^2) + (-5)^2)}{20}}} = 3.477$. Reject the null hypothesis.
(a) as $t = (9 - 2) / \sqrt(2 / 5)} = 5.593, df = 5*(5 - 1) = 20, K = 4, FWE = 0.025$ two-tailed). Use $(1 - .05 / 4, df = 20)$ to find the critical value of $2.74$ for which can be found in Table C.8. We reject the null using the Dunn-Bonferroni method. For Dunnett's test, the critical value of $d = 2.74$
(b) Use Tukey's HSD and find the critical value of $q$; $q(95,n)$ returns 20. Equation 1018 says reject the null whenever $t + q / \sqrt(2)$, so here $4.534 + 4.23 / \sqrt(2) = 2.999$, the difference is significant.
(c) The critical values, smallest to largest, for the Dunnett, Dunn-Bonferroni, and Tukey HSD tests. These indicate the relative power of the tests; Dunnett has the highest power because the critical value is the lowest. Tukey's HSD test has the lowest power but allows us to test a larger number of comparisons.
(d) The Clis estimate +/- critical value $* \sqrt{MS(2 / n)} = 7$ +/- critical value $* \sqrt{(4 / 5)}$; many critical value is the critical $(2.70, 2.74, 2.99)$. The Clis are