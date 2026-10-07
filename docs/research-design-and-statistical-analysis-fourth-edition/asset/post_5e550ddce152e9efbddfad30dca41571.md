
# Research Design and Statistical Analysis

| Mean | Std. deviation | Std. error mean | 95% Confidence interval | df | Sig. (2-tailed) |
|---|---|---|---|---|---|
| $A_1 - A_2$ | 0.833 | 0.642 | 0.262 | 0.159 1.508 3.177 | 5 | .025 |
| $A_2 - A_3$ | 2.053 | 0.950 | 0.388 | 1.056 3.050 5.294 | 5 | .003 |

There are several points to note: First, the standard deviations of the differences are different for the two tests. This is because each difference is tested against a measure of the variability of that, not against an error term from the ANOVA (Table 14.4). Second, the test is conservative not only because of the criterion alpha (i.e., .05/9) but because the degrees of freedom are (n-1) or 5 in this example. The confidence does not take into consideration the fact that we have nine tests. The appropriate CI should be based on the $t$ level required for significance at the .005 level, not the .05 level. Appendix Table C.3, or using $qt(.0052, df=5, lower=FALSE)$ in R, the critical value at the .005 level (two-tailed) is 4.773. Therefore, the CI bounds for the comparison between the $A_1, B_3$ and $A_2, B_3$, means ($\bar{Y}_{23} - \bar{Y}_{12}$) are $0.833 - (0.262)(4.773) = -0.418$ and 2.084. Using the appropriate critical value of $t$, 0 is within the CI and thus a possible value for the interaction effect.

## 14.8. Tests of Interaction Contrasts

A more direct way of understanding the reason for the significant AB interaction in Table 14.4 might be to test interaction contrasts. In Figure 14.1, we note that $\bar{Y}_{13} - \bar{Y}_{12}$ is smaller than $\bar{Y}_{23} - \bar{Y}_{12}$ or $\bar{Y}_{23} - \bar{Y}_{13}$. This suggests that we focus on these contrasts: $\psi_1 = [(4.81 - 5.02) - (5.41 - 4.58)]$ and $\psi_2 = [..., 3.41]$. One way to test these two interaction contrasts is to use the Transform option in SPSS, or mutate in the [plyr] package in R, to create new "scores" for each participant: $(A_1, B_3) - (A_1, B_j) - (A_2, B_3) - (A_2, B_j)$ and $(A_2, B_3) - (A_2, B_j) - (A_3, B_3) - (A_3, B_j)$. We can then use one-sample tests to assess these contrasts. For $\psi_1$, $t=1.87$ and for $\psi_2$, $t=4.917;2$. If we had selected the two interaction contrasts before looking at the data, we would have used the Dunn-Bonferroni procedure to control the FWE at .05 by evaluating each contrast at .052=.025. However, determining that these were of interest after viewing Figure 14.1, and noting there are nine possible $2 \times 2$ contrasts, we set alpha at .059=.056. With 5 df the critical value of $t$ is 4.773 and therefore only the test of $\psi_2$ has a significant result. The AB interaction result in Table 14.4 seems to largely reflect this interaction embedded within the larger design.

### 14.8.4 Mixed Designs

Tests of contrasts in designs involving both between- and within-participants factors follow the approaches previously. When analyzing effects of between-participants factors, the methods available are those described for completely randomized designs in Chapters 10 to 15. Software makes it easy to test contrasts to understand main effects of between-participants factors. For example, SPSS may offer "options" the Repeated Measures module and have a choice of several multiple comparison procedures. The procedures each report pairwise comparisons but use different methods to control FWE. The researcher should be warned, however, that some of the options are not wise because they lack power as methods for controlling error rate across the set of all pairwise comparisons; for example, Scheffé is not a good choice of procedures in this context.

If a researcher is interested in analyzing the main effects of a within-participants factor or an interaction involving a within-participants factor, the available options are the same as that for any repeated-measures design. Software will make pairwise comparisons of means at different levels of within-participants factors. In addition, as described in the preceding subsections, interaction contrasts may be performed to analyze how a within-participants comparison (e.g., pairwise or more complex contrast) varies over levels of between factors. As discussed in the context of repeated-measures designs, contrasts should be planned and the Dunn-Bonferroni procedure used to control FWE. If contrasts are unplanned, the control of FWE with Dunn-Bonferroni is justified if the set of contrasts consists of all possible contrasts of the same form (i.e., all pairwise or $2 \times 2$ interactions).

### 14.8.5 Designs With Multiple Repeated-Effects Factors

In the examples of contrasts presented thus far, we have dealt only with designs in which all factors are fixed except participants. When a second repeated-effects factor is included in a design, we found that tests of effects often necessitate use of quasi-F ratios because both participants and item variability are considered random effects. Similarly, when we conduct contrasts within designs in which both participants and item variability have random effects, the error terms must also account for participant and item variability, so quasi-F tests are still in order.

Table 14.12 presented an example of a repeated-measures design with eight participants, six words, and two fonts where the task was to name as quickly as possible. Our substantive interest was whether the type of font influenced naming. The test of font required a quasi-F ratio where the denominator was based on combination ($MS_{Font} + MS_{Words} - MS_{Words\times Font}$). Imagine an extension of this design where four types of fonts are tested; the design includes factors that have random effects (i.e., participants and the within-participants factor of words) as well as two within-participants factors that have fixed effects (i.e., font and illumination). How are we to carry out such comparisons? As before, our general recommendation is that for any comparison a researcher wishes to make, only the data from conditions should be compared in the analysis. For example, if the researcher wished to compare the results for Gothic font with Roman font, the data for the other fonts would be excluded. An ANOVA would be conducted specifying two levels of font; all levels of the other variables (i.e., participants, words, illumination) would be fully represented in the analysis. An F test of font would be conducted as in the overall ANOVA; the mean square for font would be tested against the combination ($MS_{S} + MS_{swFont} - MS_{swFont}$). A significant result would allow the researcher to conclude that Gothic and Roman differed in their ability.

It is important to note that the combination of mean squares is the error term same as in the ANOVA on the complete data set but its value will differ because it is based on a subset of the data. If the sphericity assumption is met in the ANOVA on the complete data set, that would justify the error term from the overall analysis. In our experience, the sphericity assumption is frequently violated in overall analysis.

## 14.9 Effect Size

### 14.9.1 The S × A × B Design

Common measures of effect size include partial eta-squared and partial omega-squared. However, as was noted in Chapter 13, both measures suffer from the limitation that their denominators change across designs. Because it is desirable to have measures of effect size that are comparable across designs, we have argued for the use of general eta-squared and general omega-squared as measures of effect size (Olenik & Algina, 2003).

The denominator of general eta-squared is the sum of squares terms for the effect plus the sum of squares including participant variance. For example, in $S \times A \times B$ design, general eta-squared for A is computed as:

$$\eta_g^2 = \frac{SS_{A}}{SS_{SA} + SS_{AB} + SS_{SAB}}{SS_{Total} - SS_{B} - SS_{AB}} (14.12)$$

However, as noted in Chapter 13, general eta-squared tends to overestimate the proportion of population variance to a variable. For that reason, we prefer general omega-squared as a measure of effect size.

The definition of general omega-squared ($\omega_g^2$) in the $S \times A \times B$ design is like that in Chapter 13 for the one-within-participants $(S \times A)$ design. For example, if A and B are extrinsic factors, we define $\omega_g^2$ as:

$$\omega_g^2(A) = \frac{\sigma_A^2}{\sigma_A^2 + \sigma_{SA}^2 + \sigma_{SAB}^2} (14.13)$$

Unfortunately, $\omega_g^2(A)$ presents a problem because the interaction terms cannot be estimated from expected mean squares in Table 14.2. An approximate solution is obtained if we assume that $\sigma_{SAB}^2 = 0$. With this modification, the $EMS$ of Table 14.2 provide estimates of the variances in Equation 14.13. Those estimates are presented in Table 14.4. Substituting into Equation 14.13, multiplying numerator and denominator by $abn$ and $MS_{SAB}$ terms, we get:

$$\omega_g^2(A) = \frac{(a-1)(MS_A - MS_{SA})}{(a-1)(MS_{A} - MS_{SA}) + n[(MS_{S} + aMS_{SA} + bMS_{SB}) + (ab-1-b)MS_{SAB}]} (14.14)$$
