# One Factor Between-Participants Designs 197

**Table 8.3** The analysis of variance for the one-factor-between-participants design (a) General form of the ANOVA

| Source | df | SS | MS | F |
|---|---|---|---|-|
| Total | an - 1 | $\sum_{j=1}^{n}\sum_{i=1}^{a}(Y_{ij} - \bar{Y}_{..)^2$ | | |
| A | a - 1 | $\sum_{i=1}^{a}(\bar{Y}_{i.} - \bar{Y}_{..})^2$ | $SS_{A/A}/df_A$ | $MS_A/MS_{S/A}$ |
| S/A | a(n - 1) | $\sum_{j=1}^{n}\sum_{i=1}^{a}(Y_{ij} - \bar{Y}_{j.})^2$ | $SS_{S/A}/df_{S/A}$ | |

(b) ANOVA of the data of Table 8.1

| | Sum of squares | df | Mean square | F | p-value |
|---|---|---|---|---|-|
| Method | 173.90 | 3 | 57.967 | 3.230 | .034 |
| Error | 646.00 | 36 | 17.944 | | |
| Total | 819.90 | 39 | | | |

this with numerical results in some form. *Panel b* presents the output for the data of Table 8.1. The results are significant at the .05 level, indicating that there are differences among the means of the populations defined by the four study methods. Figure 8.1 hints that this is due to the poorer performance of the control condition, although reaching conclusion would require additional attention. There are a range of interesting questions that the omnibus F test leaves unanswered. For example, are all three experimental methods significantly superior to the control condition? Do the means of the three experimental methods differ from each other? We will consider comparisons of means within subsets of conditions, called *contrasts*, in Chapter 10.

We might also ask whether the differences among the four population means are large enough to be of practical significance. As we noted discussing effect size measures in Chapter 6, statistical significance is not the same as practical or theoretical significance.

# 8.4.5 Using Software for the One-Factor Between-Participants ANOVA

We can use R or SPSS to obtain the ANOVA table for the data of Table 8.1. In each package, begin by importing the data file, Table_8.1_Memory.xlsx, which has two columns showing the *Method* for each participant and the other showing the resulting *Score*. In R, the imported data can be assigned to a data frame, which we call MemData for this example. Then, use the *aov* function in the [stats] package to run the calculations and the *summary* function in the [base] package to organize the output into an ANOVA table: `summary(aov(data = MemData, Score ~ Method))`. The “Score ~ Method” tells *aov* to run the ANOVA on the data in Score as a function of Method.