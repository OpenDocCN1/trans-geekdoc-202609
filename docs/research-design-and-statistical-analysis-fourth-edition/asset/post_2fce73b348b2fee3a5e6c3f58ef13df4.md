
# One-Factor Repeated-Measures Designs 365

**13.10** [Friedman's chi-squared test] For the data of Exercise 13.8, test the effects of A, using Friedman's $\chi^2$.

**13.11** [Cochran's Q test] Twenty people underwent a 1-week program to help them quit cigarette smoking. The researchers running the program checked the progress of the participants after 3, 6, and 9 months. The results follow with a 1 signifying the individual has smoked at least once during the preceding 3-month period and a zero indicating that the individual has not smoked during that period.

# Participants

| Period | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---||| 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 | 0 | 1 | 1 | 0 | | |
| 2 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 |
| 3 | 1 | 1 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 1 | 0 | 1 | 0 | 1 | 1 | 0 | 1 | 1 | 0 | - |

The investigators want to know whether there has been a significant change in the percentage of smokers over the three periods in the follow-up study. Perform an analysis to answer this question and state your conclusion.

**13.12** [Repeated-measures ANOVA on real data] The file EX13_12.xlsx in the Exercises page of the book's website contains hours/day exposure to daylight for the oldest group of participants in the Seasons study. This was of interest to the researchers because it is believed that daylight affects mood.

- a) For the participants who identify as female (i.e., sex = 1), perform an analysis of variance on the *DIRWDC* (direct exposure to daylight during weekdays) scores across seasons; 1 = winter, 2 = spring, 3 = summer, 4 = fall. Interpret the results.
- b) Calculate general $\omega^2$ for the effects of seasons.

- 1 The complete data set is on the *Seasons* page on the book's website; go to *Data Files*, *Seasons*. The data in Table 13.1 are also in the file *Male_D* under *35.*

- 2 For clarity, we have created data in which the sample variances of difference scores are identical. In a real data set, there would be differences due to error variance; if the population variances were homogeneous, we would not expect marked differences among the sample variances.

- 3 The Roy-Bose method is as follows. Assume a contrast – e.g., $C = \hat{Y}_1 - (1/2)(\hat{Y}_2 + \hat{Y}_3)$. $C$ is considered to be significantly different from zero if $C > (n-1)(a-1)F_{a-1,n-a} + a$.

# Chapter 14

# Multi-Factor Repeated-Measures and Mixed Designs

# 14.1 Overview

In this chapter, we extend our discussion of repeated-measures designs to designs involving two or more factors. These factors may all be within-participants or a mix of within- and between-participants factors. We refer to the latter as mixed designs; they are also called split-plot designs in reference to their early appearance in agricultural experiments. In both pure repeated-measures designs and mixed designs, it is important to distinguish variables that have fixed effects and those that have random effects. As we discussed in Chapter 13, this distinction has implications not only for the interpretation of results but also for expected mean squares and, consequently, for hypothesis tests and measures of effect size.

The chapter is organized as follows:

- We first consider pure repeated-measures designs in which all independent variables except participants have fixed effects.
- We then turn to mixed designs in which each participant is at only one level of A but is tested at all levels of B and both A and B are fixed-effect factors.
- We extend each of these designs to include more than two factors.
- Following these developments, we introduce analyses involving a random-effects variable (in addition to participants) and consider the implications for the expected mean squares and the F test.
- Finally, procedures for considering the treatment means within the designs are developed, and effect size measures and a priori power calculations are presented for both classes of design.

# 14.2 The S × A × B Design With A and B Fixed

In a conventional, two-factor repeated-measures design, n randomly sampled participants are tested at every combination of levels of the other factors. If there are two within-participants factors, A and B with b levels, respectively, each participant is tested ab times. For example, consider a hypothetical experiment modeled on a study of factors affecting facial recognition (Murray, & Rhodes, 2000). Investigators presented participants with several faces differing with respect to the type of distortion (three levels) and the orientation of the face (three levels), a simplification of their experiment nine combinations of orientation and distortion, with the order of presentation randomly determined for each participant.

# Multi-Factor Repeated-Measures and Mixed Designs 367

14.2.1 The Structural Model and Expected Mean Squares (EMS)

We assume that $Y_{ijk}$, the score from participant $i$ in the cell formed by $A_j$ and $B_k$, is composed of a true score and error; i.e., $Y_{ijk} = \mu + \varepsilon_{ijk}$. We may rewrite this in terms of the grand mean and the deviation of the true score from that: $Y_{ijk} = \mu + (\mu_{ijk} - \mu) + \varepsilon_{ijk}$.

Under a nonadditive model, we assume that individual differences $(\eta_i)$, the effects of $A (\alpha_j)$ and $B (\beta_k)$, and their interactions contribute to the difference between $\mu_{ijk}$ and $\mu$. Substituting these effects for $\mu_{ijk} - \mu$, we have: $Y_{ijk} = \mu + \alpha_j + \beta_k + (\eta\alpha)_{ij} + (\eta\beta)_{ik} + (\alpha\beta)_{jk} + (\eta\alpha\beta)_{ijk} + \varepsilon_{ijk}$.

The parameters and their variances are defined in Table 14.1 and the sums-of-squares (SS) formulas and EMS are in Table 14.2. The EMS are those for $S \times A$ design:

| Table 14.1 Components of the structural model for the $S \times A \times B$ design | Population Definition | Variance |
|---|---|---|
| $\eta_i$ | | | $\sigma_S^2 = E(\eta_i^2)$ |
| $\alpha_j$ | $\mu_j - \mu$ | $\sigma_A^2 = \sum_{j=1}^a \alpha_j^2 / a$ |
| $\beta_k$ | $\mu_k - \mu$ | $\sigma_B^2 = \sum_{k=1}^b \beta_k^2 / b$ |
| $(\eta\alpha)_{ij}$ | $(\mu_{ij} - \mu) - \eta_i - \alpha_j$ | $\sigma_{SA}^2 = E(\sum_{j=1}^a (\eta\alpha)_{ij}^2 / a)$ |
| $(\eta\beta)_{ik}$ | $(\mu_{ik} - \mu) - \eta_i - \beta_k$ | $\sigma_{SB}^2 = E(\sum_{k=1}^b (\eta\beta)_{ik}^2 / b)$ |
| $(\alpha\beta)_{jk}$ | $(\mu_{jk} - \mu) - \alpha_j - \beta_k$ | $\sigma_{AB}^2 = E(\sum_{j=1}^a \sum_{k=1}^b (\alpha\beta)_{jk}^2 / ab)$ |
| $(\eta\alpha\beta)_{ijk}$ | $(\mu_{ijk} - \mu) - \eta_i - \alpha_j - \beta_k - (\eta\alpha)_{ij} - (\eta\beta)_{ik} - (\alpha\beta)_{jk}$ | $\sigma_{SAB}^2 = E(\sum_{j=1}^a \sum_{k=1}^b (\eta\alpha\beta)_{ijk}^2 / ab)$ |
| $\varepsilon_{ijk}$ | $Y_{ijk} - \mu_{ijk}$ | $\sigma_\varepsilon^2 = E((Y_{ijk} - \mu_{ijk})^2)$ |

**Note:** $\mu_{ijk} = E(Y_{ijk})$, $\mu_{ij} = \sum_k \mu_{ijk}/b$, $\mu_{ik} = \sum_j \mu_{ijk}/a$, $\mu_i = \sum_j \sum_k \mu_{ijk}/ab$, $\mu_j = E(\mu_{ij}|A_j)$, $\mu_k = E(\mu_{ik}|B_k)$, and $\mu = E(\mu_i) = \sum_j \sum_k \mu_{ijk}/ab$. The random effects - $\eta_i$, $(\eta\alpha)_{ij}$, $(\eta\beta)_{ik}$, and $\varepsilon_{ijk}$ - are assumed to be normally distributed with mean zero and variance, as noted in the table.

# Research Design and Statistical Analysis

Table 14.2 ANOVA for an S × A × B design; A and B fixed effects

| Source | df | SS | EMS | F |
|---|---|---|---|---|
| S | n-1 | $ab\sum_{i=1}^n(\tilde{Y}_{i..}-\tilde{Y}_{\..})^2$ | $\sigma_e^2 + ab\sigma_S^2$ | |
| A | a-1 | $nb\sum_{j=1}^a(\tilde{Y}_{.j}-\tilde{Y}_{\..})^2$ | $\sigma_e^2 + b\sigma_{SA}^2 + nb\sigma_A$ | |
| SA | (n-1)(a-1) | $b\sum_{i=1}^n\sum_{j=1}^a(\tilde{Y}_{ij.}-\tilde{Y}_{..})^2$ | $\sigma_e^2 + b\sigma_{SA}^2$ | |
| B | b-1 | $na\sum_{k=1}^b(\tilde{Y}_{.k}-\tilde{Y}_{\..})^2$ | $\sigma_e^2 + a\sigma_{SB}^2 + nb\sigma_B$ | |
| SB | (n-1)(b-1) | $a\sum_{i=1}^n\sum_{k=1}^b(\tilde{Y}_{ik.}-\tilde{Y}_{..})^2$ | $\sigma_e^2 + a\sigma_{SB}^2$ | |
| AB | (a-1)(b-1) | $n\sum_{j=1}^a\sum_{k=1}^b(\tilde{Y}_{.jk}-\tilde{Y}_{\..})^2$ | $\sigma_e^2 + n\sigma_{AB}^2$ | |
| SAB | (n-1)(a-1)(b-1) | $SS_{total} - SS_S - SS_{SA} - SS_{SB} - SS_{AB} - SS_{SAB}$ | $\sigma_e^2 + \sigma_{SAB}^2$ | |

14.2.2 An Example of the $S \times A \times B$ ANOVA

Table 14.3 (the data are also in the file *Table 14.3 SAB Data on the Tables* page) presents the data for our experiment on face perception. The scores in Table 14.3 are hypothetical averages of several photos in each condition, but the pattern of the means plotted in Figure 14.1 is similar to the pattern in the Murray et al. (2000) article.

Table 14.4 presents the results of the ANOVA of the $S \times A \times B$ data in Table 14.3. The degrees of freedom and sums of squares can be verified using the formulas in Table 14.2. The $F$ tests are based on the nonadditive model, assuming $A$ and $B$ both have fixed effects and participants are a random sample from an infinitely large population of participants. As the EMS in Table 14.2 dictate, A is tested against SA, B is tested against SB, and AB is tested against SAB.

Chapter 13. As was the case there, A is tested against SA mean square. Similarly, B and AB are tested against SB and SAB respectively.
