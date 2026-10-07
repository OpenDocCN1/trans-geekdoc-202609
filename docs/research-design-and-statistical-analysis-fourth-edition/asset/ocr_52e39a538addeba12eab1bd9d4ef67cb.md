# One-Factor Repeated-Measures Designs 361

question whether the probability of success depends upon the problem type. In general, $Y_{ij} = 1$ or 0, indicating a success or failure by participant $i$ in condition $j$. If $p_j$ is the probability of a success in the population of responses under $A_j$ the null hypothesis is

```
$H_0 : p_1 = p_2 = \dots = p_a$
```

The Q statistic is defined as

```
$Q = SS_{AS} / MS_{AS/S}$ (13.20)
```

$MS_{AS/S}$ is the average of $n$ variances where each variance was based on the $a$ scores for a participant. Q is distributed as chi square when $n$ is large and the population correlation for any pair of conditions is the same as for any other pair. Therefore, the null hypothesis is rejected when $Q$ exceeds the critical value of $\chi^2$ on $a - 1$.

The $\chi^2$ distribution rests on the assumption that the variable of interest is normally distributed. Under the central limit theorem, this assumption is essentially true for proportions when $n$ is large. For the Q test, the effective $n$ does not include any participants who either excels or all failures. Based on several simulation studies, Myers, DiCecco, White, and Borden (1982) recommended that the effective number of participants should be at least 16. When $n$ is small, empirical rejection rates of true hypotheses are less than the nominal alpha, and power is quite low.

Again, statistical packages also include the Q test. For example, SPSS provides a Q test in the Nonparametric Tests / Legacy Dialogs under related samples. In R, one option uses the CochraneQTest in the [DesTools] package. The 0/1 data can also be submitted to a repeated-measures ANOVA. In fact, Myers et al. (1982) report that the $F$ and Q tests have very similar Type 1 error rates for $n \ge 16$; within smaller $n$, the $F$ test Type 1 error may be inflated.

# 13.11 Nonparametric Tests and Assumptions

Although is often assumed that nonparametric tests are assumption-free, this is not the case. The Friedman and rank-transformation tests require the usual assumptions of ANOVA for repeated-measures, but with respect to the ranks rather than the order. The WSR is a test of the null hypothesis that the median is zero only if the population of difference is symmetric. Cochran’s Q test rests on the assumption that the correlations for pairs of treatments are the same in the population and requires a sufficient sample size to warrant use of the $\chi^2$ tests to evaluate significance. deciding whether to analyze the data of a repeated-measures design with ANOVA versus one of the nonparametric tests requires the researcher pay close attention to the characteristics of the data and their correspondence (or lack thereof) with the assumptions of the statistical procedures under consideration.

# 13.12 Summary

In this chapter, we considered the analysis of data from a repeated-measures design in which participants were tested on several trials, or at randomly sequenced levels of an independent variable. Within context, we addressed the following topics:

+   The distinction between additive and nonadditive structural models and the problems that may be encountered when data include participant × treatment interactions.