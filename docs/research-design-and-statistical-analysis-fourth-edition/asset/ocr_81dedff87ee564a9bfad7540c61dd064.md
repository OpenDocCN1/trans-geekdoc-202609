# 416 Research Design and Statistical Analysis

Table 15.11 Analysis of the design of Table 15.10 assuming B has random effects

| SV | df | EMS | Error term |
|---|---|---|---|
| C | c - 1 | $\sigma_{\epsilon}^2 + \sigma_{C\times Row}^2 + an\sigma_{BC}^2 + a^2n_C^2$ | quasi-F |
| Row (AB)' | a - 1 | $\sigma_{\epsilon}^2 + \sigma_{C\times Row}^2 + an\sigma_{AB}^2$ | S/C × Row |
| C × Row (ABC)' | $(a - 1)(c - 1)$ | $\sigma_{\epsilon}^2 + a\sigma_{C\times Row}^2 + n\sigma_{ABC}^2$ | S/C × Row |
| S/C × Row | $ac - 1$ | $\sigma_{\epsilon}^2 + \sigma_{C\times Row}^2$ | |
| A | a - 1 | $\sigma_{\epsilon}^2 + nc\sigma_{AB}^2 + ac\sigma_A^2$ | BCR |
| B | a - 1 | $\sigma_{\epsilon}^2 + an\sigma_{AB}^2$ | WSR |
| AC | $(a - 1)(c - 1)$ | $\sigma_{\epsilon}^2 + n\sigma_{ABC}^2 + an\sigma_{BC}^2$ | C × BCR |
| BC | $(a - 1)(c - 1)$ | $\sigma_{\epsilon}^2 + n\sigma_{BC}^2$ | WSR |
| BCR (AB)' | $(a - 1)(a - 2)$ | $\sigma_{\epsilon}^2 + nc\sigma_{AB}^2$ | WSR |
| C × BCR (ABC)' | $(a - 1)(c - 2)(c - 1)$ | $\sigma_{\epsilon}^2 + n\sigma_{ABC}^2$ | WSR |
| WSR | $ac(a - 1)(n - 1)$ | $\sigma_{\epsilon}^2$ | |

Note: If B has fixed effects, the underlined components are deleted from the EMS, and the error terms change accordingly.

Main and interaction effects are calculated as in all preceding chapters. Recall that the term labeled “WSR” is $SA/C \times Rows$, using the notation familiar from repeated-measures designs. The only terms calculations might pose a problem are the BCR (between cells residual) and interaction with C. These can be viewed as differences between terms derived from standard mixed-design ANOVAs. This observation forms the basis for using computer program capable of handling two-between-participants variables ($C, Row$) and one within-participants variable ($A$ or $B$) can be used to do two analyses. In one analysis, specify $A$ as the within-participants variable and obtain $SS_A$; in the other, specify $B$ as the within-participants variable and obtain $SS_B$. Then:

$SS_{BCR} = (SS_{BC\times Row} - SS_{C\times Row}) = (SS_{B\times Row} - SS_{AC}).$

The results will be the same if $SS_B$ is subtracted from $SS_{Row}$ and $SS_{BC}$ is subtracted from $SS_{Ab:Row}$. The entries in the EMS column in Table 15.11 were assuming that $B$ has random effects, as when $B$ represents time periods. If $B$ is a fixed-effects variable, the expected mean squares and error terms are changed, as described in the Table 15.11.

Table 15.12 presents the numerical results for the analysis of the data set in Table 15.10. The results are clear: Good readers are faster than slow readers, context has an effect on reading times, and no interactions approach significance.