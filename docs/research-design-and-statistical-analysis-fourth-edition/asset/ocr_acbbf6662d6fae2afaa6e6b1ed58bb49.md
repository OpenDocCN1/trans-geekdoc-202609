# 762 Answers to Selected Exercises

Notice that the SS for A and SA (error) are one-third their values from part (a) because each "score" is an average of three scores in the original data.

| Source | EMS |
|---|---|
| S | $\sigma_e^2 + a\sigma_{SB}^2 + ab\sigma_B^2$ |
| A | $\sigma_e^2 + a\sigma_{SAB}^2 + b\sigma_{SA}^2 + n\sigma_{AB}^2$ |
| B | $\sigma_e^2 + a\sigma_{AB}^2 + na\sigma_B^2$ |
| SA | $\sigma_e^2 + a\sigma_{SAB}^2 + b\sigma_B^2$ |
| SB | $\sigma_e^2 + a\sigma_{SB}^2$ |
| AB | $\sigma_e^2 + a\sigma_{SAB}^2 + n\sigma_{AB}^2$ |
| SAB | $\sigma_e^2 + a\sigma_{SAB}^2$ |

+   (d) When B is random, we need a quasi-F test for A. $F_1^A = \frac{MS_A}{MS_{SA} + MS_{AB} - MS_{SAB}} = 33.136$.$\nFrom Equation 14.8, $df_{error} = 1.84$, so $p = .035$.$\n(e) Averaging over levels of B and analyzing the data as if there were only $a$ scores per participant ignores the AB and SAB variability that contribute to the mean square if B has random effects. Thus, procedure often leads to an inflated Type 1 error rate.

14.5 We need to estimate population variances under both assumptions:

| A, fixed | B random |
|---|---||
| S | $(MS_S - MS_{SAB})/ab = 16.000$ | $(MS_S - MS_{SAB})/ab = 16.000$ |
| A | $(a-1)(MS_A - MS_{SAB})/ab = 533$ | $(a-1)(MS_A - MS_{SA} - MS_{SAB})/abn = .08$ |
| B | $(b-1)(MS_B - MS_{SAB})/ab = 1.04$ | |
| SA | $MS_{SA} - MS_{SAB}/b = 2.80$ | $MS_{SA} - MS_{SAB}/b = 2.80$ |
| SB | $(MS_{SB} - MS_{SAB})/a = 7.33$ | $(MS_{SB} - MS_{SAB})/a = 7.33$ |
| AB | $(a-1)(b-1)(MS_{AB} - MS_{SAB})/abn = 1.813$ | $MS_{AB} - MS_{SAB}/n = 27.20$ |
| SAB | $MS_{SAB} = 10.00$ | $MS_{SAB} = 10.00$ |

+   ($\alpha$) $\omega_G^2(A) = \sigma_e^2 / (\sigma_e^2 + a\sigma_{SAB}^2 + n\sigma_{AB}^2 + \sigma_A^2) = .015$.

+   (b) Now B and AB estimate variances under the denominator. $\omega_G^2(A) = .002$.

+   14.7 (a) > summary(ao_ev=data,data="S","Y",between=c("A"),within=c("B"))\ Contrasts to contr.sum for the following variables: A

Univariate Type III Repeated-Measures ANOVA Asphericity

| Sum sq DF Error SS den DF F value Pr(F) |
|---|---|---|---|---|---||
| (Intercept) 8800.2 | 1 | 66.222 | 4 | 531.5570 | 2.09e-05 *** |
| A | 490.0 | 1 | 66.222 | 4 | 29.6510 | 0.005524 *** |
| B | 447.4 | 2 | 16.444 | 8 | 108.8378 | 1.579e-06 *** |
| A:B | 14.8 | 2 | 16.444 | 8 | 3.5946 | 0.076952 |