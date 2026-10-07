
## 350 Research Design and Statistical Analysis

In the one-factor repeated-measures design, investigators often calculate *partial* $\eta^2$:

$$\eta_p^2(A) = \frac{SS_A}{SS_A + SS_{SA}} \quad (13.7)$$

From the sums of squares in Table 13.2, $\eta_o^2(A) = 47.778 / (47.778 + 20.96) = .188$. We can request this value using the `effect="pes"` in the `anova_test` function in the `stats` package in R. It is also the computation in SPSS if an effect size is requested in the *General Linear Model/Repeated-Measures* module. However, a limitation of Equation 13.7 is that it is not comparable to Equation 13.6 because Equation 13.6 includes variability due to individual differences, whereas Equation 13.7 omits such variability. Therefore, we follow Olejnik and Algina (2003), we use the general $\eta^2$:

$$\eta_o^2(A) = \frac{SS_A}{SS_A + SS_{SA} + SS_S} \quad (13.8)$$

Again turning to the SS column in Table 13.2, $\eta_o^2(A) = 47.778 / (47.778 + 779.1 + 20.96) = .046$. This is the default effect size reported by the `anova_test` function (labeled "ges"); see Figure 13.2. In the one-factor repeated-measures design, the denominator of the general statistic is the total sum of squares, provided that the numerator represents a factor with fixed effects. Note that $\eta$ and general $\eta$ are identical in the one-factor repeated-measures design; however, the denominator of the general statistic is usually not the total sum of squares, so the two statistics are different in multi-factor designs. We will consider such designs in the next chapter.

As stated in Chapter 8, $\eta^2$ has the advantage of being easily calculated and easily understood as a proportion of *sample* variance, but it tends to overestimate the proportion of *population* variance due to the independent variable. The next statistic provides a somewhat better estimate of the effect of the independent variable in the population.

### 13.7.2 $\omega^2$ (Omega-Squared), the Proportion of Population Variance

Typically, researchers have reported estimates of *partial* $\omega^2$, which is the variance among the population treatment divided by the sum of that variance and the population error variance:

$$\omega_p^2(A) = \frac{\sigma_A^2}{\sigma_A^2 + \sigma_e^2} \quad (13.9)$$

With $\eta^2$, we recommend calculating a statistic that takes individual differences into account so that values of $\omega^2$ may be compared across designs. General $\omega^2$ is defined as

$$\omega_o^2(A) = \frac{\sigma_A^2}{\sigma_A^2 + \sigma_e^2 + \sigma_S^2} \quad (13.10)$$

## One-Factor Repeated-Measures Designs

If the additive model applies to a data set, the expected mean squares in Table 13.2 suggest the following estimates of the variances:

$$\hat{\sigma}_A^2 = \left( \frac{MS_A - MS_{SA}}{n} \left[ \frac{a-1}{a} \right] \right)$$
$$\hat{\sigma}_S^2 = \left( \frac{MS_S - MS_{SA}}{a} \right)$$

and

$$\hat{\omega}_g^2 = MS_{SA} \quad (13.11)$$

Substituting these estimates from Equation 13.10 and multiplying the numerator and denominator by $an$, we have

$$\omega_g^2(A) = \frac{(MS_A - MS_{SA})(a-1)}{(MS_A - MS_{SA}) + n(MS_S - MS_{SA}) + anMS_{SA}} \quad (13.12)$$

We can obtain this estimate from research reports even when mean squares are not reported if we provide the $F$ ratios and degrees of freedom. Dividing the numerator and denominator of Equation 13.12 by $MS_{SA}$, and noting that $F_A = MS_A / MS_{SA}$ and $F_s = MS_S / MS_{SA}$ we have

$$\omega_g^2(A) = \frac{(a-1)(F_A-1)}{(a-1)F_A + nF_s + (a-1)(n-1)} \quad (13.13)$$

If $F_s$ is less than one, the estimate is assumed to be zero.

For the data set of Table 13.1, we substitute the $F$ ratios and values of $a$ and $n$ into Equation 13.13, and find that

$$\omega_g^2(A) = \frac{(4-1)(3.001-1)}{(4-1)(3.001)+(14)(12.295)} = .030$$

We estimate that the variation in seasons accounts for about 3% of the total population variance.

In many circumstances, the nonadditive model will be a more accurate description of the data. In that, the formula for $\omega^2$ must include

$$\omega_g^2(A) = \frac{\sigma_A^2}{\sigma_A^2 + \sigma_S^2 + \sigma_{SA}^2} \quad (13.14)$$

We still use Equation 13.12 or 13.13 to estimate general $\omega^2$ because it is not possible to obtain estimates of all four variance terms; the resulting estimate is positively biased. Under the nonadditive model, Equation 13.12 estimates

$$\omega_g^2(A) = \frac{\sigma_A^2}{\sigma_A^2 + \sigma_S^2 + \sigma_{SA}^2 + [(a-1)/a]\sigma_{SA}^2} \quad (13.15)$$

Equation 13.12 underestimates the denominator of general $\omega^2$ and consequently overestimates the proportion of variance. In addition to the problem of obtaining an unbiased estimate, we must consider the practical implications. (The text continues here).
