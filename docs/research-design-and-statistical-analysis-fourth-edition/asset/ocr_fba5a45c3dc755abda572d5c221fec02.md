# One-Factor Repeated-Measures Designs 345

Table 13.4 Data for a toy population of four participants with interaction effects present

| | $A_1$ | | $A_2$ | | $A_3$ | | |
|---|---|---|---|---|---|---||
| | $Y_{i1}$ | $(\eta)_{i1}$ | $Y_{i2}$ | $(\eta)_{i2}$ | $Y_{i3}$ | $(\eta)_{i3}$ | $\mu_i$ | $\eta_i$ |
| $S_1$ | 8 | -1 | 10 | 1 | 9 | 0 | 9 | -5 |
| $S_2$ | 10 | 3 | 9 | 2 | 2 | -5 | 7 | 2.5 |
| $S_3$ | 11 | -1 | 12 | 0 | 13 | | 12 | 2.5 |
| $S_4$ | 9 | -1 | 7 | -3 | 14 | 4 | 10 | 5 |
| $\mu_j$ | 9.5 | | 9.5 | | 9.5 | | | |

Note: $S_1$ and $S_2$ are sampled from the population, and constitute the "experiment".

row is; this is an algebraic result of the definition of an interaction effect. Now assume an "experiment" in which $S_1$ and $S_2$ are selected by random sampling. Taking the "data" from the two participants in the experiment, we find that the means at the levels of $A_i$, $Y^*_{ij}$, are 9, 9.5, and 5.5. Although the treatment means, $\mu_i$, are identical, the sample means, $Y^*_{ij}$, are not. This is not because of error of measurement, because there is none in this artificial data set. It is entirely due to the fact that the sampled interaction effects are different at the three levels of A. By randomly sampling participants, we also have sampled their interactions with the factors of $A_i$ sometimes sampled interactions will raise certain treatment means, and in others samples they could reduce the very same treatment means. This random sampling of only some of the population interaction effects at each treatment level is why $\sigma^2_{SA}$ contributes to the variability among the $Y^*_{ij}$ and therefore to $MS^*_{SA}$. Which means will be most raised or lowered relative to their population values depend on the pattern of interaction effects that have been sampled from each treatment population.

One other point follows from Table 13.4. Because A is a fixed-effects variable, each participant includes the average of all interaction components in the corresponding row. Average is zero and therefore the interaction variance does not contribute to differences between participant means and, accordingly, does not contribute to $MS_A$.

Returning to the seasonal depression data shown in Table 13.1 and Figure 13.1, we can see that these data are not consistent with the additive model. Four participants were randomly sampled from the sample, and their individual depression scores are shown in Figure 13.1. These data reveal large differences in the pattern of participants' depression scores over the seasons. For example, Participant 2 has a higher depression score in the fall than the summer, whereas Participant 1's depression scores are lowest in the fall and higher in the spring. These differences are random Participant $	imes$ Season (SA) interaction effects. The EMS for the nonadditive model in Table 13.3 shows that these SA interaction effects influence both the $MS_A$ and the $MS_{SA}$. Despite this unwanted influence, the $F$ ratio for the effect of A is computed in the same way for the additive and nonadditive models. Although the computations are the same, nonadditivity has several consequences, which we will consider next.