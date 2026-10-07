
infer the consequences of equal, proportional, and disproportional cell frequencies for ANOVA. The cell means are as follows:

| B1 | B2 | B3 |
|---|---|---|---|
| A1 | 12 | 8 | 22 |
| A2 | 8 | 6 | 13 |
| A3 | 1 | 3 | 16 |

+   a) Assume that the cell frequencies are all the same. (i) Calculate the row and column means. (ii) Subtract each value of $\hat{\alpha}_i$, from the three cell means in the corresponding row. How do the column means of this adjusted matrix compare with those in part (i)?

b) Assume the original cell means presented earlier. This time, however, assume the following cell frequencies ($n_{ij}$):

| B1 | B2 | B3 |
|---|---|---|---|
| A1 | 4 | 8 | 12 |
| A2 | 3 | 6 | 9 |
| A3 | 1 | 2 | 3 |

Redo (i)-(iii) of part (a). In before calculating the row, column, and grand means; the means being averaged were weighted by the corresponding frequency. For example, the mean of the first row is [(4(12)+(8)+(12)/22)]/24. Similarly, the grand mean is the weighted average of the 12 means (of row or column means).

+   c) Again assume the original set of means. This, the $n_{ij}$ are as follows:

| B1 | B2 | B3 |
|---|---|---|---|
| A1 | 5 | 10 | 4 |
| A2 | 5 | 5 | 10 |
| A3 | 10 | 3 | 5 |

Again do (i)-(iii).

+   d) Review your answer to problem and draw a conclusion about the effects of equal, proportional, and disproportional cell frequencies about the partitioning in ANOVA.

9.19 [Utility of EMS] Eighty students taking a class in statistics are divided into 20 study groups, each consisting of two women and two men. Ten of the students are instructed in class by one method, and the remaining 10 are taught by a different method. Much of the analysis is summarized next:

| Source | df | EMS |
|---|---|---|---|
| Method (M) | 1 | 3627 | $\sigma_\epsilon^2 + 4\sigma_{g/m}^2 + 408^2$ |
| Sex (X) | 1 | 128 | $\sigma_\epsilon^2 + 2\sigma_{g/m}^2 + 408^2$ |
| MX | 1 | 123 | $\sigma_\epsilon^2 + 2\sigma_{g/m}^2 + 208^2_{mix}$ |
| Groups/method (G/M) | 18 | 420 | $\sigma_\epsilon^2 + 4\sigma_{g/m}^2$ |
| GX/M | 18 | 32 | $\sigma_\epsilon^2 + 2\sigma_{g/m}^2$ |
| Residual | 40 | 30 | $\sigma_\epsilon^2$ |

# 260 Research Design and Statistical Analysis

a) Calculate the appropriate F statistics for M, X, and MX. Report whether each is significant.

The investigator reanalyzes the data, pooling the GX/M with the residual error term. The resulting sources of variance are as follows:

| Source | df | MS | EMS |
|---|---|---|---|
| Method (M) | 1 | 3,627 | |
| Sex (X) | 1 | 128 | |
| MX | 1 | 123 | |
| G/M | 18 | 32 | |

b) What assumption would justify this reanalysis?

c) In view of your answer to (a), fill in the EMS column. Also provide the df and MS for the pooled residual.

d) Recalculate the F ratios and report whether each is significant. What are the consequences of the reanalysis?

e) What is the justification for the reanalysis?

9.20 [Using R with real data] [palpenguins] package in R contains a data set penguins (Horst et al., 2020). Install the package and use penguins to see the variables included. Three species of penguins were studied over a period of 3 years.

+   a) Does bill length differ across species? Be sure to consider other possible sources of variance in your response.

+   b) The sample sizes vary across species and year. Redo your analysis from part (a) assuming different types of squares. Which analysis is most justified?

# Notes

+   1 This assumption means that the selected levels of A are the levels of interest; we cannot generalize our conclusions to other possible levels of A from our statistical analysis. We will consider random effects beginning in Chapter 13.

+   2 The arguments are true from a statistical perspective, and conclusions about the presence or absence of an interaction on the dependent variable (DV) may be made with confidence. However, as well as other disciplines, the dependent measure may use an indirect way to assess the underlying, latent, variable of interest. For example, we use reaction times (RT) as a measure of memory. The function mapping the latent variable to the DV is unknown, and a significant interaction in the DV does not necessarily entail a significant interaction in the latent variable.

+   3 Note that if the null hypothesis is true, we have the central F distribution. However, if the null hypothesis is not true, we have the noncentral F distribution.

+   4 Strictly speaking, if the null hypothesis is true, we have the central F distribution whose cutoffs are presented in Appendix C.5.

Note that if the null hypothesis is true, we have the central F distribution. However, if the null hypothesis is not true, we have the noncentral F distribution.

Let $\gamma$ be the sum of all variance estimates involving an; then, $f(Effect) = \sqrt{\frac{2}{df_{effect}/df_{\epsilon}} + \gamma}$.

# Chapter 10

# Contrasting Means in Between-Subjects Designs

# 10.1 Overview

In Chapter 8, we learned how to test the hypothesis that the means of all populations are equal. Although a significant F provides evidence that the means are not equal, it does not reveal the differences among the means. For example, in the study of the effects of educational level on depression scores (see Table 8.5), we are left with questions such as: Does the mean for the population having only high school education differ from that for the population having some education? Does the mean for the population with only high school education differ from the mean with more than high school education? Within the context of multi-factor designs we might ask these questions, and whether such differences depend on the gender identity of the participant.

Answering such questions requires minor modifications of the t statistics presented in Chapter 6. Evaluating significance, however, is an issue when several tests are performed on a set of group means. Just as the probability of at least one head increases as the number of coin tosses increases, so does the probability of least one Type 1 error increase as more significance tests are performed. The set of contrasts is referred to as a family, and the probability that the family contains at least one Type 1 error is referred to as the familywise error rate, or FWE. There are many factors that influence the FWE and methods for controlling it. The goals of this chapter are as follows:

- To extend the t for independent groups to testing contrasts of any form within a between-participants design.
- To introduce a distinction between controlling the probability of a Type 1 error for an individual comparison, EC (for "error rate per comparison") and controlling the probability of a Type 1 error within a family of comparisons, FWE.
- To distinguish among several different kinds of families of contrasts and present appropriate methods for controlling the FWE for each kind of family.
- To explain the relationship between ANOVA and test of contrasts.

We begin by developing these issues and applications in the context of a single-factor design. Once the procedures for testing contrasts are established, we will extend them to multi-factor designs with emphasis on analyzing interactions.
