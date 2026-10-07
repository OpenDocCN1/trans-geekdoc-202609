# Nested Counterbalanced Variables 411

The results of the two analyses are then used to obtain the partitioning summarized in the right panel of Table 15.7. In this analysis, we are able to distinguish not three, but four within-partitions sources of variability – the treatment variable, A; the blocking variable, B; a “between-cells residual” term as $(S_{GA} - S_{HB})$, or equivalently $(S_{GB} - S_{AB})$; and a term that we call “within-partitions residual” (WSR), which corresponds to SA/G from our original analysis or, equivalently, SB/G from our second analysis. The $df$ for the between-cells residual (BCR) term is assumed as the difference between the $df$ for the GA interaction and the $df$ for the main effect of $B$; that $df_{BCR} = df_{GA} - df_{B} = (a-1)^2 - (a-1) = (a-1)(a-2)$. The $df$ for the remaining terms are fixed in the usual fashion.

The right-most partitioning is what we recommend for this experimental design. An astute reader may wonder why the partitioning does not explicitly contain a treatments × blocks (AB) interaction. In fact, every possible combination of A and B is represented in the design, so it is possible to recover information about the interaction. However, there is a confounding effect in the design that prevents us from identifying a single term representing the AB interaction. Groups may differ because each represents a different subset of assignments to blocks; that is, a subset of AB interaction (see Exercise 15.8). This accounts for $(a-1)$ of the $(a-1)(a-1)$ associated with the interaction. The remaining AB interaction variability is embedded in the BCR source. A simple demonstration of this is to show that the sum of squares for AB is divided between the G and BCR sources; from Table 15.6.

$SS_{AB} = 5 \times [(7.6 - 8.425)^2 + (10 - 8.425)^2 + \dots + (3.8 - 8.425)^2] - 86.65 - 76.85 = 86.45$

$SS_G + SS_{BCR} = 33.75 + 52.20$, which also equals 86.45. Furthermore, we view the Groups and BCR sources as capturing some of the AB interaction variability. The AB interaction is confounded with the Groups and BCR sources.

With the partitioning of the variability established, we are now able to consider alternative models of the data, corresponding expected mean squares, and the results F.

# 15.4.2 Expected Mean Squares and F Tests

We assume the following model for the replicated-square design:

> $Y_{ijkm} = \mu + \eta_{ijm} + \alpha_j + (a\beta)_{jk} + \varepsilon_{ijkm} \quad (15.3)$

where $i$ indexes the participant within a row of the Latin square ($i=1, 2, \dots, n$), $j$ indexes the effect of $A$ ($j=1, 2, \dots, a$), $k$ indexes the level of $B$ ($k=1, 2, \dots, b$), and $m$ indexes the row within the group ($m=1, 2, \dots, a$). The population of participant effects, the $\eta_{ijm}^0$, are assumed to be independent and normally distributed with mean zero and variance $\sigma^2_{S/G^C}$. The effects of $A$, the $\alpha_j$, are assumed to be fixed. $B$ may have fixed or random effects, the $eta_{jk}$ and the AB interaction effects, $(a\beta)_{jk}$, are distributed independently and normally with mean zero and respective variances $\sigma^2_B$ and $\sigma^2_{AB}$.

The expected mean squares for the replicated Latin design are presented in Table 15.8. Note that there are two panels: one containing the $EMS$ when $B$ is assumed to have fixed effects and another when $B$ is assumed to have random effects. In both panels, the AB interaction variability contributes to the Group and BCR expectations, as we showed