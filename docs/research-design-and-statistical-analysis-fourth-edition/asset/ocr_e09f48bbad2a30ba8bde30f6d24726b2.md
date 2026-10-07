# Research Design and Statistical Analysis

```
$\tilde{Y}_1 = b_{E0} + b_{E1}(1) + b_{E2}(0) = b_{E0} + b_{E1} \quad (23.1)$
```

Similarly, for $A_j$ and $A_{j'}$, respectively, we have

```
$\tilde{Y}_2 = b_{E0} + b_{E1}(0) + b_{E2}(1) = b_{E0} + b_{E2} \quad (23.2)$
```

and

```
$\tilde{Y}_3 = b_{E0} + b_{E1}(-1) + b_{E2}(-1) = b_{E0} - b_{E1} - b_{E2} \quad (23.3)$
```

Adding Equations 23.1-23.3, we obtain $3b_{E0} = 	ilde{Y}_1 + 	ilde{Y}_2 + 	ilde{Y}_3$, so that

```
$b_{E0} = \frac{	ilde{Y}_1 + \tilde{Y}_2 + \tilde{Y}_3}{3} = \tilde{Y}_U$
```

Here, $	ilde{Y}_U$ is the weighted average of the group means. If there are equal numbers of scores in each of the groups, $	ilde{Y}_U$ will equal $	ilde{Y}_j$, the grand mean of all the scores. We can now write the coefficients of the dummy variables as deviations from the unweighted mean of the group means. Substituting $b_{E0} = \tilde{Y}_U$ into Equations 23.1 and 23.2, and solving, we obtain the formulas and numerical results for $b_{E1}$ and $b_{E2}$ that are presented in Panel $b$ of Table 23.1. For equal $n$ designs, the regression coefficients correspond exactly to the estimated mean components of the ANOVA, $\hat{\alpha}_j$. That is, because $	ilde{Y}_j = \hat{\mu}_j$, and $	ilde{Y}_U = \hat{\mu}$.

```
$b_{E1} = \tilde{Y}_1 - \tilde{Y}_U = \hat{\mu}_1 - \hat{\mu} = \hat{\alpha}_1$
```

and

```
$b_{E2} = \tilde{Y}_2 - \tilde{Y}_U = \hat{\mu}_2 - \hat{\mu} = \hat{\alpha}_2$
```

Furthermore, because of the requirement $\Sigma\alpha_j = 0, \hat{\alpha}_3$ can be found as

```
$\hat{\alpha}_3 = -\hat{\alpha}_1 - \hat{\alpha}_2 = -b_{E1} - b_{E2}$
```

# Dummy Coding

A second way to code variables is to use dummy coding, for which the dummy variables only take on the values 0 and 1, as illustrated by $X_{D1}$ and $X_{D2}$ in Panel $b$ of Table 23.1. For dummy coding, the dummy variables are defined as

```
$X_{Dj} = 1$ for scores at level $A_j$, and
```

```
= 0$ otherwise
```

Note that we only need $a-1$ dummy variables to code a groups, one group, referred to as the reference group, will receive 0s on all the dummy variables. Because there are three levels of $A$ in the current example, we require two dummy variables to account for all the between-group variability. Scores at $A_1$ receive a 1 on $X_{D1}$ and