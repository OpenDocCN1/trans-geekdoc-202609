# One-Factor Repeated-Measures Designs 359

approaches to missing data in psychological research. The details of the estimation procedures are beyond the level of this book, but we will discuss the topic a bit more when we study correlation and regression.

# 13.11 Nonparametric Procedures for Repeated-Measures Designs

In previous chapters, we have discussed the implications of violations of the assumptions of statistical tests. We have found that such violations may result in distortions of Type 1 error rates or loss of power. In such situations, we have found that nonparametric procedures often have advantages over the conventional F and t tests. For example, in Chapter 8, two tests based on ranks were presented, the Kruskal-Wallis F test and the rank-transformation test (Iman & Conover, 1981). These tests are often more powerful than the F test when the treatment population distributions have heavy tails or are skewed. Similar analyses of ranked scores can be applied to repeated-measures designs. We will consider these as a test for situations in which all scores are either zeros or ones.

# 13.11.1 Friedman's $\chi^2$ (Chi Square) Test

In the first procedure (we consider, the scores for each participant are assigned ranks from 1 (for the lowest) to a (for the highest); tied scores are assigned the median, or midrank, of their ranks. The test statistic is approximately distributed as chi under the null hypothesis that, for each participant, all sequences of ranks are equally likely. If this null hypothesis is true, differences between conditions in the mean ranks are due to chance than to the effects of the independent variable.

Several programs consider Friedman's (1993) $\chi^2$; for example, SPSS's nonparametric module (select Legacy Dialogs, then K Related Samples) takes the original data as its input and yields a statistic distributed approximately as $\chi^2$ when Friedman's $\chi^2$ is selected from the available options. Similarly, in R the *friedman_test* function in the *rstatix* package provides the same calculations. For the Seasons depression data of Table 13.1, the result is $\chi^2 = 6.738, p = .081$.

# 13.11.2 The Rank-Transformation F Test (F.)

An ANOVA based on ranks has been proposed by Iman, Hora, and Conover (1984); also see Hora & Iman, 1988). There are two steps:

+   1. Assign ranks to all *an* scores from smallest to largest, assigning midranks in case of ties. Unlike, unlike Friedman's procedure, each participant's scores are not ranked separately.

+   2. Do the standard $S \times A$ ANOVA on the rank values. This means that the $Y_{ij}$ have been converted to $R_{ij}$ which can be submitted to any program that analyses data from a repeated-measures design.

When the $R_{ij}$ transforms the data of Table 13.1 are analyzed, $F = 3.44$ with $p = .026$ (see Exercise 13.11). The Greenhouse–Geisser and Huynh–Feeldman estimates are .83 and 1, almost identical to those in the ANOVA of the original data, but the p-values are lower, .035 and .026.