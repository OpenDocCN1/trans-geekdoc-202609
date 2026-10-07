386 Research Design and Statistical Analysis

# 14.6.6 Some Other Issues in Using Quasi-F Tests

The construction of quasi-F ratios provides a general solution to the problem of testing effects in designs with multiple random-effects factors. However, researchers often encounter an obstacle to this approach. In many studies, observations are missing and therefore not all $S \times A \times B$ combinations are available. If so, it will be impossible to calculate $MS_{AB}$ and, the the quasi-F statistic cannot be calculated. A conservative remedy in this situation is to calculate a minimum quasi-F ($minF'$; Clark, 1973; Forster & Dickinson, 1976);

```
$minF' = MS_{SA} / (MS_{AB} + MS_{SA}) \quad (14.11)$
```

When observations are missing, $minF'$ and the denominator $df$ are calculated as a function of $F_i$ and $F_{ij}$; the formulas are presented in Box 14.2. The test based on $minF'$ is somewhat conservative because it lacks an estimate of $MS_{SAB}$.

+   1. Find the average of the scores in each $S \times A$ combination; presumably there are a few scores in each combination even if some values are missing. Compute

```
$F_1 = MS_{SA} / MS_{SA}$
```

+   2. Find the average of the scores in each $A \times B$ combination. Compute

```
$F_2 = MS_{SA} / MS_{AB}$
```

+   3. Compute

```
$minF' = \frac{F_1 F_2}{F_1 + F_2}$
```

and

```
$df_{error} = \frac{(F_1 + F_2)^2}{F_1^2 / df_{AB} / df_{SA}}$
```

The numerator $df$ are $a - 1$.

What about the effects of violations of the sphericity assumption upon the distribution of $F$? Somewhat surprisingly, Maxwell and Bray (1986) found that nonsphericity does not inflate the Type 1 error rate for $F'$. Their article presents an interesting discussion of the reasons for this.

Finally, a comment on the power of quasi-F tests. We know that the number of participants in an experiment is an important determinant of the power of statistical tests. This is is