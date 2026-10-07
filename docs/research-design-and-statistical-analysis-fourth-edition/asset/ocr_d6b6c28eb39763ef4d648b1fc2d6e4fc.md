# Nested and Counterbalanced Variables 417

Table 15.12 ANOVA of the data in Table 15.10

| SV | df | SS | MS | Error term | F | p |
|---|---|---|---|---|---|--|
| Reader (C) | 1 | 2,211.13 | 2,211.13 | quasi-P | 10.16 | 0.01 |
| Row | 2 | 72.33 | 36.17 | S/C Row | 0.14 | 0.87 |
| C × Row | 2 | 1,204.00 | 602.00 | S/C Row | 2.27 | 0.13 |
| Context (A) | 18 | 4,776.08 | 265.34 | BCR | 645.69 | 0.002 |
| Blocks (B) | 2 | 136.75 | 68.38 | WSR | 0.92 | 0.41 |
| AC | 2 | 34.33 | 17.17 | C × BCR | 3.10 | 0.24 |
| BC | 2 | 53.58 | 26.79 | WSR | 0.40 | 0.67 |
| BCR | 2 | 1.08 | 0.54 | WSR | 0.01 | 0.99 |
| C × BCR | 2 | 11.08 | 5.54 | WSR | 0.08 | 0.92 |
| WSR | 36 | 1,341.17 | 74.51 | | | |

> $F_{C} = MS_{C} / (MS_{BC} + MS_{S/C \times Row} - MS_{WSR})$ with $df_{denom} = (MS_{BC} + MS_{S/C \times Row} - MS_{WSR})^2 / (MS_{df/BC} + MS_{S^2 \times C} / df_{df/WSR}(df_{WSR})) = 10.70$

# 15.6 Summary

In this chapter, we described structured models and analyses for two modifications of the repeated-measures designs of the preceding two chapters:

+   * Hierarchical designs that involve the nesting of stimuli within levels of the independent variable.
* Latin square designs that involve assigning treatments to levels of a nuisance variable so that the assignment is counterbalanced over groups of participants.

These designs have advantages and disadvantages relative to each other and to the repeated-measures and mixed designs of Chapter 14. Hierarchical designs, by nesting stimuli within levels of the within-participants factor, A, avoid effects of repeating stimuli. However differences among sets of items contribute to the error variance against which the effects of A are tested. Latin squares reduce error variance due to blocking factors as trial blocks of items. However, they do so at a cost of degrees of freedom, and therefore power of the hypothesis test. The choice of design will depend on factors such as the nature of the independent variable, the response required of the participant, the number of available participants, and the number of levels of the independent variable.

Hierarchical models are very flexible in their application and are particularly useful in dealing with designs as those in this chapter. Many different assumptions about the effects of variables and the pattern of variances and covariances can be readily incorporated in this approach. Also, missing scores are not a problem. The price for these and other benefits is paid in both the complexity of the approach and the decisions imposed during the analysis of data. A discussion of the models and the analyses is beyond the scope of