# Multi-Factor Repeated-Measures and Mixed Designs 373

Table 14.7 ANOVA formulas (a) and EMS (b) for the mixed design
(a) Partitioning degrees of freedom and sums of squares

| Sources of variance | df | Sums of squares |
| --- | --- | --- |
| Total | abn - 1 | $\sum_i\sum_j\sum_k(Y_{ijk} - ar{Y}_{\cdot\cdot})^2$ |
| Between-subjects (S) | an - 1 | $b\sum_i\sum_k(Y_{ijk} - ar{Y}_{\cdot\cdot})^2$ |
| A (Instructions) | a - 1 | $bn\sum_j(Y_{ijk} - ar{Y}_{i\cdot\cdot})^2$ |
| S/A | $a(n-1)$ | $SS_S - SS_A$ |
| Within-subjects (W SS) | $an(b-1)$ | $SS_{total} - SS_S$ |
| B (Time) | b - 1 | $an\sum_i(Y_{ijk} - ar{Y}_{\cdot\cdot})^2$ |
| AB | $(a-1)(b-1)$ | $n\sum_i\sum_j(Y_{ijk} - ar{Y}_{ij\cdot})^2 - SS_A - SS_B$ |
| B $	imes$ S/A | $a(n-1)(b-1)$ | $SS_{Wk} - SS_B - SS_{AB}$

(b) Expected mean squares

| Source | EMS |
| --- | --- |
| A | $\sigma_\epsilon^2 + b\sigma_{S/A}^2 + bn\sigma_A^2$ |
| S/A | $\sigma_\epsilon^2 + b\sigma_{S/A}^2$ |
| B | $\sigma_\epsilon^2 + \sigma_{SB/A}^2 + an\sigma_B^2$ |
| AB | $\sigma_\epsilon^2 + \sigma_{SB/A}^2 + n\sigma_{AB}^2$ |
| B $	imes$ S/A | $\sigma_\epsilon^2 + \sigma_{SB/A}^2$

previously. If we ignore the factor B, the design is a one-factor design with participants nested within levels of A. In the one-factor-between-participants design, an - 1 df are divided between the A and participants-within-A sources. If we ignore A, we have the S $	imes$ B design of Chapter 13; there is a participants term (S), a B term, and an AB interaction. However, part of the SB variance is potentially due to the interaction of A and B and so the variability is partitioned into an AB and a B $	imes$ S/A term, as shown in Table 14.7.
From the EMS of B in Table 14.7, we see that the between-participants factor, A, is tested against the S/A source. This is the same as in a one-factor-between-participants design. Differences along the $\alpha$ reflect not only the effects of A and errors of measurement, but also individual differences because there are different participants at each level of A. It is important to recognize that the term $\sigma_\epsilon^2$, has a different meaning in the current design than it had in Chapter 8. In the one-factor design of Chapter 8, $\sigma_\epsilon^2$, encompassed both within-subject variability due to individual differences and measurement errors. However, in the current design, individual differences contribute only to between-participants factors; therefore, $\sigma_\epsilon^2$ denotes only measurement errors and $\sigma denotes individual differences.
In the within-participants portion of the design, the B and AB terms are tested against the residual error, $MS_{B/S/A}$. This is because the nested interaction effects of participants and B contribute to both the AB and B variance. This is analogous to the way we tested in the repeated-measures designs in Chapter 13 and Section 14.2 of the current chapter.