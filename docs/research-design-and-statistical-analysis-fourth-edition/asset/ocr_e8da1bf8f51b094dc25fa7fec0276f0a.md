their difference: psi = 8.281 - (-3.75) = 12.031. To obtain a CI, we psi +/- $s_{psi}$ 12.031 +/- $s_{psi}$ 2.00, $s_{psi} = sqrt((2/4n)MS_{error})$, where $n$ is the number of scores on which each mean is based, and $s_{error}$ comes from the between-participants analysis of the differences: $s_{psi} = sqrt(2 / 32)* = 3.510$. The 95% CI is 12.031 +/- (2.00)(3.510) = [5.01, 19.03]$, which doesn't include 0.

(c) Select the data for one format at a time and run an ANOVA on the difference scores. (i) In the test condition $f = sqrt(3 / 32).(110) = .102$, a small effect.
ii) In the web condition, some direction of Cohen's f is 0. In either condition, instructions have little effect on the difference between the two dependent measures, relative to the error variance.

(d) Using G*Power, we enter f = .1, numerator df = 3, groups = , alpha = .05 and power = .8. The result is N = 109, or 274/instruction condition.

# Chapter 15

15.1 Select the cases where A = 1 (or 2 or 3) and then run a between-participants ANOVA with B as a fixed factor.

| Source | df | MS |
|---|---|--|
| B/A1 | 1,808,925.00 | 4 | 452,231.00 |
| B/A2 | 623,512.15 | 4 | 155,788.04 |
| B/A3 | 695,324.34 | 4 | 173,831.09 |

Summing the SS, we get 3,127,761.5, which matches the $SS_{B/A}$ shown in Table 15.3. Averaging the MS, we get 260,646.71, which matches the $MS_{B/A}$ shown in Table 15.3.

| Source | df | MS |
|---|---|--|
| S | 19 | $\sigma^2_1+50\sigma^2_2$ |
| M | 4 | $\sigma^2_2+20\sigma_{Items/M}/10\sigma^2_{SM}+200	heta^2_M$ |
| Items/M | 45 | $\sigma^2_2+20\sigma^2_{Items/M}$ |
| SM | 76 | $\sigma^2_2+10\sigma^2_{SM}$ |
| SItems/M | 855 | $\sigma^2_2$ |

The main effect of T is measured with a quasi-F = $MS_ / (MS_{Items/M} + MS_{SM} - MS_{Items/M})$. Numerator df = 4, Denominator df = $(MS_{Items/M} + MS_{SM} - MS_{Items/M})^2 / (MS^2_{Items/M} / 45 + MS^2_{SM} / 76 + MS^2_{SItems/M} / 855)$

```
> avov_out<-summary(aov(data,-Y-R*V*Items %in%(R*V)))
> avov_out
id Df Sum Sq Value F Pr(F)
R 9 14.91 1.661 0.10371
R 1 0.41 0.41 0.406 0.52495
V 1 34.44 34.44 34.541 2.78-08 ***
id:R 9 9.34 1.04 1.041 0.41033
id:V 10 10.70 1.19 1.193 0.30937
R:V 1 8.41 8.41 8.428 0.00428 **
id:R 9 11.35 1.26 1.264 0.26143
R:Items 16 40.00 2.50 2.507 0.00206 **
Residuals 144 143.63 1.000
```