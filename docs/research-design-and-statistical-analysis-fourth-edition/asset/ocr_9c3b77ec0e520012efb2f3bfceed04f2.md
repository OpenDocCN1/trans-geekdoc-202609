# Nested and Counterbalanced Variables 413

Table 15.9 Two analyses of the data of Table 15.5

| SV | df | MS | B Fixed F | p | B Random F | p |
|---|---|---|---|---|---|--|
| G (AB)' | 3 | 1125.00 | 0.53 | 0.67 | 0.53 | 0.67 |
| S/G | 16 | 21.36 | | 2.60 | 0.06 | | 0.10 |
| A | 3 | 28.88 | | 0.06 | 3.29 | |
| B | 3 | 25.62 | 2.30 | 0.09 | 2.30 | 0.09 |
| BCR (AB)' | 6 | 8.78 | 0.79 | 0.58 | | |
| WSR | 48 | 11.12 | | | | |

* A and B are tested against WSR.
* B is tested against BCR.

however, that in the replicated Latin square design a single source of variance – BCR – has the appropriate EMS to serve as the error term to test the effect of A. Unless there is a large effect of A, this F will lack power because the df associated with BCR will typically be small when the Latin square is large. Despite the large value of the F statistic in the random-effects case, the p-value is larger than in the fixed-effects test of A, reflecting the reduced degrees of freedom.

To increase power the test of A when B has random effects, some researchers choose to pool the BCR (AB') and WSR means when there is strong evidence that there is no AB interaction (σAB = 0). The advantage of pooling is that it results in a large gain in errors of freedom. In the absence of convincing evidence that there is no AB interaction, pooling will result in a positively biased test of A (see Section 14.6.1).

# 15.4.3 Alternative Analyses of the Replicated Latin Square Design

It is not uncommon for researchers to conduct statistical analyses that are not entirely consistent with their experimental designs. The design currently under consideration is a good case in point.

One common inappropriate approach to analyzing the replicated Latin square design is to ignore the Groupb and blocking variables and treat it as a one-factor repeated-measures design. The only sources of variance distinguished are Participants, A, and the SA interaction, with the effect of A being tested against SA. In the recommended analysis summarized in the right panel of Table 15.7, the repeated-measures analysis corresponds to pooling the Groupb sums of squares with the sums of squares for the S/G term, and more importantly pooling the sums of squares with B and BCR sums of squares for the WSR term. If B is assumed to have fixed effects, the pooling of B, BCR, and WSR sums of squares has the unfortunate consequence of inflating the error term for the test of treatment effect, A. As a result, the test of A will be negatively biased and Type 2 errors are likely to increase (Pollack & Well, 1995). In that case, an experiment designed to reduce variance through systematic manipulation of the blocking variable actually results in lower power because the statistical analysis is incompatible with the experimental design. In contrast, if B is assumed to have random effects, the pooling of B, BCR, and WSR will underestimate the appropriate error term, and thus the test of A will be positively biased.