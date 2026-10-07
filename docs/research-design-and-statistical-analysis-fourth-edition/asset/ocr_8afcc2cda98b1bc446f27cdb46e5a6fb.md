# Comparing Experimental Designs and Analyses 335

c) Now use G*Power’s option for ANOVA Fixed effects Omnibus oneway. Assuming the value of f calculated in part (a), estimate post hoc power for the completely randomized design.

d) Assuming we wished to redo the experiment to detect a medium sized effect (f = .25) with power = .9 and α = .05, how many observations would be required for each design?

e) How the relation between the required sample size change as r decreases?

12.8 [Comparing LS and RM designs] Five experts taste each of five wines and rate on a 100-point scale. The order of presentation is counterbalanced over the five participants, each wine appears in each of the five positions in the sequence of tasting. Let A be the wines and C be the position in time. The data, also present on the website in the file EX12_8, are organized by wines (A) and position in time (C):

| A1 | A2 | A3 | A4 | A5 | C1 | C2 | C3 | C4 | C5 |
|---|---|---|---|---|---|---|---|---|--|
| 82 | 80 | 84 | 81 | 82 | 83 | 80 | 84 | 81 |
| 89 | 91 | 84 | 79 | 84 | 79 | 89 | 84 | 91 |
| 88 | 87 | 88 | 84 | 86 | 87 | 84 | 88 |
| 88 | 86 | 95 | 77 | 77 | 88 | 86 | 89 | 95 |
| 86 | 86 | 78 | 79 | 78 | 79 | 86 | 86 |

a) Often researchers ignore the blocking factor, C, and carry out the following ANOVA:

| Source | df | SS | MS | F | p |
|---|---|---|---|---||
| Subjects (S) | 4 | | | | |
| Wines (A) | 4 | | | | |
| SA | 16 | | | | |

Complete the table.

b) A similar analysis can be performed, ignoring A, and having participants C and SC as the sources. This analysis.

c) Subtract SS, from part (b) from SS_{SA} in part (a). Call the result SS_{Residual}. Also subtract SS_S from part (a) from SS_{SC} in part (b). How does this compare with the residual sum of squares?

d) As we did for Table 12.7, we can carry out a complete Latin square ANOVA. The sources and dfs are as follows:

| Source | df | SS | MS | F | p |
|---|---|---|---|---||
| Subjects (S) | 4 | | | | |
| Wines (A) | 4 | | | | |
| Time (C) | 4 | | | | |
| Residual | 4 | | | | |