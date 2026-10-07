# One Factor Between-Participants Designs 191

$\alpha_j = (\mu_j - \mu)$; because $\alpha_j$ (Greek alpha) is the difference between the mean of the $j$th treatment population and the grand mean of all the populations, it represents the effect of the $j$th treatment on the $j$th population. Therefore, we can rewrite Equation 8.2:

```
$Y_{ij} = \mu + \alpha_j + \varepsilon_{ij} \qquad (8.3)$
```

Equation 8.3 is a *structural equation*: It defines the structure of a score obtained in a one-factor between-participants experiment. In words, the structure of a score is

$score = grand mean + treatment effect + error component$

The parameters in Equation 8.3 are rather abstract and not very useful unless we tie them to statistics that we can calculate from our data. To do this, we need to estimate the population means, the treatment effects, and the error terms. We have the following parameter estimates:$3$

| Parameter | $\mu$ | $\mu_j$ | $\alpha_j$ | $\varepsilon_{ij}$ |
|---|---|---|---||
| Estimate | $\hat{\mu}$ | $\hat{\mu}_j$ | $\hat{\alpha}_j$ | $\hat{Y}_{ij} - \hat{Y}_j$ |

$Y_{ij}$ is the score of the $i$th person in the $j$th group, $\hat{Y}_j$ is the mean of all the scores in the $j$th data set. For example, in Table 8.1, $Y_{23}$ is 16, the score of the second person in the image condition; $\hat{Y}_4$ is 10.5, the mean of the rhyme condition; and $\hat{Y}$ is 9.95, the grand mean.

With the structural equation as a basis, we can now begin to calculate the necessary terms to draw inferences from our data.

# 8.4 The Analysis of Variance (ANOVA)

The ANOVA involves partitioning the variability of all the scores into two components, called *sums of squares*. In turn these are divided by their degrees of freedom to form mean squares, the ratio of mean squares, the $F$ ratio, provides a test of the hypothesis that all the treatments have the same effect. In what follows, we consider each of these aspects of the ANOVA.

# 8.4.1 Sum of Squares

As Equation 8.3 implies, scores can vary because of the effects of the independent variable (these contribute to the $\alpha_j$) and because of the effects of uncontrolled variables (these contribute randomly to the $\varepsilon_{ij}$). If we separate those two sources of variance in our data, we will have the basis for deciding how much, if any, of the variance is due to the independent variable.

The structural equation suggests an approach to partitioning variability. If we rewrite Equation 8.3 by subtracting $\mu$ from both sides, we can express the deviation of a score