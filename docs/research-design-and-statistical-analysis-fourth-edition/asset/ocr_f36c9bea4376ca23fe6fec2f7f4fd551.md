# Contrasting Means in Between-Subjects Designs 275

# 10.6.1 The Dunn-Bonferroni Method (Dunn, 1961)

The Dunn-Bonferroni method for controlling FWE follows from Equation 10.14. If there are contrasts, the FWE will not exceed a nominal value if the EC is set at that value given by K. For example, assuming an FWE of .05, we test the three contrasts in Table 10.1 at the .017 (0.5/3) alpha-level. The statistics are reported in Table 10.4; Equation 10.5 provides the formula for the t when variances are assumed equal, and Equations 10.8-10.10 provide the formulas for the t and df when variances are not assumed equal. If the p-value is available, we can control the FWE by comparing p FWE/K and rejecting $H_0$ only for contrasts where p < FWE/K. Looking at Table 10.4 for our example, we would evaluate each of our contrasts at the .0167 level. Equivalently, the p.adjust function in R's [base] package, with the method = “bonferroni” option, multiplies input vector of p-values by K, where K = the number of tests (i.e., the number of p-values); the resulting adjusted p-values may be compared to any desired α. For example, p.adjust(c(.005, .587, .465), method = “bonferroni”) returns three adjusted p-values (0.015, 1.000, and 1.000), for which the hypothesis corresponding to the first p-value is significant when α = .05.

Table 10.4 Output of tests for three contrasts of means in a memory experiment
(a) ANOVA

| Method | Sum of squares | df | Mean square | F | Sig |
|---|---|---|---|---||
| | 173.900 | 3 | 57.967 | 3.230 | .034 |
| Residuals (Error) | 646.000 | 36 | 17.944 | | |

(b) Contrast coefficients

| Contrast | Control | Loci | Image | Rhyme |
|---|---|---|---|--|
| 1 | 3 | -1 | -1 | -1 |
| 2 | 0 | 1 | 1 | -2 |
| 3 | 0 | 1 | -1 | 0 |

(c) Contrast tests

| Contrast | Estimate | Std. error | t | df | Sig. (2-tailed) |
|---|---|---|---|---|--|\| Assumes equal variances | | | | | |
| 1 | -13.80 | 4.640 | -2.974 | 36 | .005 |
| 2 | 1.80 | 3.281 | 0.544 | 36 | .587 |
| 3 | 1.40 | 1.894 | 0.739 | 36 | .465 |
| Does not assume equal variances | | | | | |
| 1 | -13.80 | 3.902 | -3.537 | 21.949 | .002 |
| 2 | 1.80 | 3.345 | 0.538 | 20.466 | .596 |
| 3 | 1.40 | 2.112 | 0.660 | 17.672 | .518 |