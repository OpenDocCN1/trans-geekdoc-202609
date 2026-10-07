
# Answers to Selected Exercises

11.5 (a) The variance differs markedly; we use Welch's t. Using Equations 10.8-10, we compute $t' = 4.1 / 1.598 = 2.565$ and $df' = 13.49$. In R we use the $qt$ function to find the critical $t$ for a two-tailed test when there are four planned contrasts and FWE = $.05; qt(1 - 0.025 / 2, 13.49) = 2.88$. Since $2.565 < 2.88$, we do not reject the null hypothesis.

(b) Again we use Welch's t with the Dunn-Bonferroni adjusted to $p$. $df' = 6.19$ and $t' = 2.718$. There are five comparisons to control, so each gets $\alpha = .01, qt(.01 / 2, 6.19) = 3.66$. We cannot reject the null, $t' = 2.718 < 3.666$.

11 (a) Let $Y =$ Younger, $D =$ Older, and $W =$ We. $H_0: [\mu_{YW} - \mu_{DW}] = [\mu_{DW} - \mu_{YW}] = 0$. Weights: $1, -1, 1, -1$. $n = 20$; $S_B = 20((72.50 - 83.25) - (72.25 - 89.90)) / 2 = 140$, so the result in Table 9.12.

(b) Let $S =$ Summary and $A =$ Argument. $H_0: [\mu_{SA} - \mu_{AS}] = [\mu_{AS} - \mu_{SA}] = 0$. $S_{SA} = 10^0 ((71.25 - 76.50) - (70.55 - 88.25)) / 2$.

11 (a) The difference in means is $4.8$ and far less than the 4-1 rule), so we use Tukey's HSD. $s_q = \sqrt{MS_{AB}/nb} = \sqrt{120/20} = 2.45$. The CI is in R, we compute $q = \text{qtukey}(n=5, df=9) = 3.94$. The CI is $-4.8 / (3.94)(2.345) = (16.6 + 14.7) / 2(1 / 10)(13.5) = 5.74$. and we cannot reject the null hypothesis.

(c) The critical $t(90) = 1.99; 3.774 > 1.99$ so we reject the null. (ii) Now $EC = F = 3 / 0.16$ and the critical $t$ is $2.46$. (iii) The Scheffé procedure is needed. $S = \sqrt{4(F_{E,90})} = \sqrt{4(2.47)} = 3.14$; reject if $|t_{ab}| > S$.

(d) Let $R =$ Retires; $S =$ Students. $H_0: [[\mu_{RL} - \mu_{LR}]/2 - [\mu_{LL} - \mu_{LS}]/2 - [\mu_{LS} - \mu_{MS}]/2] = 0$; $\pi = ((16.6 + 14.7) / 2(2(1 / 10)) = (18.5 + 19.6) = 5.74$. $t_{crit}(90) = 1.99$ so the 95% CI $s_{pi} = \sqrt{110^*(4).(25/10) + 2(1/10)} = 5.74$ is $-7.3 /(1.99)(5.74) = -18.72$. Zero is in the null hypothesis contained.

# Chapter 12

12 (a) $summary(aor(data = data, Y - A)) =$ completely randomized design

| | DF | Sum Sq | Mean Sq | F value | Pr(>F) |
|---|---|---|---|---|---|
| A | 2 | 861 | 430.6 | 2.431 | 0.097 |
| #Residuals | 57 | 10097 | 177.1 | | |
| A | 2 | 861 | 430.6 | 3.411 | 0.00419 * |
| B | 3 | 3269 | 1089.7 | 8.633 | 0.0001 *** |
| A:B | 6 | 768 | 128.1 | 1.014 | 0.42724 |
| Residual | 48 | 6059 | 126.2 | | |

If blocking constructs vary (i.e., if either $MS_{AB} = 0$ or $MS_B = 0$), then that variance is reflected in a larger $MS_{AB}$ when the data are treated as a completely randomized design.

(b) $summary(aor(data = data, Y - A)) =$ treatments blocks. We see a significant effect of blocking, and the effect of A that we saw in (a) is now significant because the variance due blocking has been removed from the error variance.

12.3 (a) $f = \sqrt{2 / 60} / (430.6 - 126.2) / \sqrt{126.2} = 0.284$; (b) $f = \sqrt{2 / 60} / (430.6 - 126.2) / \sqrt{175.3} = 0.241$; (c) Using $G^*$, power of the (one-way) randomized design is 0.35; power of the (main effects and interactions) blocks design is 0.468; (d) To obtain $N=.468$ with $f=.241$ and thus in a one-way randomized design, we need $N=84$ or $28$; (e) a priori calculation with $f = .284$, numerator $df=2, 3$, we get $N=123$. $N^*=138/170$ participants needed in the randomized design for power. We use a larger sample size ($N=71$) if $f=.241$ in a one-way design seeking power $=8$. The relative efficiency of two designs estimates the ratio of sample needed to achieve the same power.

12.5 (a) In R, $cor(X, Y)$ shows that $r = .0845$. $(1 - r^2) = .993$ which is much larger than the SS total in ANCOVA. The ratio of $SS_{total}$ is $10879.75/10957.933$; (b) $s^2_{SA} = (-7499+2710.5+8.3)/\sqrt{1736+3591.5+1874.2} = .002$, which is within rounding error of the $SS_{SA}$ in ANCOVA.

12.7 (a) $\sigma^2_A = \frac{2}{12}(32.25-3.92)=4.72$; $\sigma^2_B = \frac{3}{12}(18.33-3.92)=3.60$; $\sigma^2_W=3.60+3.92=7.52; f=\sqrt{4.72/7.52}=0.79$; (b) power=.965; (c) power=.53, is lower than the repeated-measures design because subject variability appears in the error variance. (d) The repeated-measures design would require $N=19$, assuming the correlation from (b) and with three measurements each. The between-subjects completely randomized design require $N=207$; (e) As the correlation decreases, less-subject-variance is removed from the error term in a repeated-measures design, meaning a larger sample size is required for the same power. With a correlation of 0, $N=69$ to have power $=9$ in the RM design. That means $3 \times 69 = 207$ independent observations are required for that power, the same as in the completely randomized design in part (d).

12.9 (a) $estMSE_{RM}=(4)(13+32.96)/5=12.30$; (b) $AdjustedMSE_{RM}=(13/15)(19/17)(12.30/7.13)=1.67$. The Latin Square design is more efficient in this, and we fewer participants to achieve the same power.

# Chapter 13

13.1 (a, b)

```
summary(aov(dat, Y ~ A + Error(S)))
## Error: S
```

# Answers to Selected Exercises 759

| | Df | Sum Sq | Mean Sq | F value | Pr(>F) |
|---|---|---|---|---|---|
| #Residuals | 3 | 70.67 | 23.56 | | |
| #Error: S:A | | | | | |
| #A | 2 | 6.500 | 3.250 | 2.854 | 0.135 |
| #Residuals | 6 | 6.833 | 1.139 | | |

$EMS$
S $\sigma_e^2 + 3\sigma_A^2$
A $\sigma_e^2 + 40\sigma_A^2$
S:A $\sigma_e^2$.

$\hat{\sigma}_a^2 = \frac{a-1}{a}\hat{\sigma}_A^2 = \frac{a-1}{n}(MS_A - MS_{SA}) = \frac{2.21}{3} = 0.352
$\hat{\sigma}_S^2 = \frac{a-1}{n}(MS_S - MS_{SA}) = 7.472\sigma_e^2 = 1.139$;
Then $\omega_g^2(A) = \frac{\hat{\sigma}_A^2}{\hat{\sigma}_A^2 + \hat{\sigma}_S^2} = \frac{0.352}{0.352 + 7.472} = 0.039$

(d) No. The participants show interaction effects.

| | | A_2 | A_3 | |
|---|---|---|---|---|
| | $Y_1$ | $\eta_{\alpha_1}$ | $Y_2$ | $\eta_{\alpha_2}$ | $Y_3$ | $\eta_{\alpha_3}$ | $\mu_i$ |
| $S_1$ | 12 | -1.45 | 14 | 1.05 | 15 | 0.30 | 3.7 |
| $S_2$ | 9 | -0.25 | 8 | -0.25 | 10 | 0 | 9 |
| $S_3$ | 10 | -0.05 | 8 | -0.55 | 12 | 0.70 | 10.3 |
| $S_4$ | 8 | -1.25 | 6 | -0.25 | 7 | -1.00 | 7 |
| | $\mu_j$ | 9.75 | | 9.25 | | 11.0 |

13.3 (summary(anova=Log, Value = FactorA + Error(id/Factor))
## Error: id

| | Df | Sum Sq | Mean Sq | F value | Pr(>F) |
|---|---|---|---|---|---|
| #Residuals | 5 | 105.56 | 21.12 | | |
| #Error:id:Factor | | | | | |
| #FactorA | 2 | 216.55 | 108.28 | 21.93 | 0.00021 *** |
| #Residuals | 10 | 49.38 | 4.94 | | |

$MS_{AA} = 4.94$
Mean A1 - Mean A2 = -1.33; $t(10) = -1.33/\sqrt{49*(1/6+1/6)}$. With $df=10$, $p=.016$.

(b) var(A1–A2) = 1.10, $t(5) = -1.33/\sqrt{10/6) = -3.106$. With $df=5$, $p=.013$.
(c) The variances in the three levels of A are 2.94, 26.1, and 25.4. The SE based on the ANOVA MS is inflated by the variance of group 3, a condition that is not involved in the difference of interest. The test part from (b) is preferred for that reason.

13.5 (a) summary(aov(data=dat,Y ~ A+Error(S/A))
## Error: S

| | Df | Sum Sq | Mean Sq | F value | Pr(>F) |
|---|---|---|---|---|---|
| #Residuals | 7 | 59.09 | 8.441 | | |

## Error: S:A

| | Df | Sum Sq | Mean Sq | F value | Pr(>F) |
|---|---|---|---|---|---|
| A | 3 | 3.763 | 1.2542 | 6.35 | 0.00311 |
| #Residuals | 21 | 4.148 | 0.1975 | | |

1-pf(6.3, df1=3*(1/3), df2=1*(1/3)) = p = .04 among the lower-bound epsilon adjustment. In both cases, we can reject the null hypothesis that the $\mu$ are all equal.

(b) Using the Dunn-Bonferroni method (Tukey-s HSD assumes independently distributed means), if the $FWE = .05, \alpha = .05/.06$ (two-tailed). We want the value of $t$ (7) that cuts .004 in each tail: $ql(.004, df=7, lower.tail=FALSE)=3.67$ The means are 3.275 and 4.175 and the standard deviation of the difference is .804. Therefore, the .95 simultaneous conf-interval for this difference is $(4.175-3.275) + (3.67)(.804/\sqrt(8)) = [-0.14, 1.94].
