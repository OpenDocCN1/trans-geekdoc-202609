# Multi-Factor Between-Participants Designs 221

# 9.2 The Two-Factor Design: The Structural Model

# 9.2.1 The Model Equation

In these designs, there are two independent variables, $A$ and $B$, with $a$ levels of $A$, $b$ levels of $B$, and $n$ scores in each of the $ab$ cells. A score will be represented as $Y_{ijk}$, the $i$th score of the $j$th level of $A$ and the $k$th level of $B$. We want to test hypotheses about population means and therefore need a model that relates the observed scores to the means of the populations formed by the combinations of the variables $A$ and $B$ to the error component of each score. These population parameters and the sample statistics estimate them are presented in Table 9.1.

Consider a specific combination of levels $A$ and $B$, say $A_j$ and $B_k$. In terms of the Wiley-Voss experiment described in 9.1, this cell be formed by the combination of the two formats and one of the four instructions. Because the same combination of treatments is applied to everyone in that, the scores in the population corresponding to $A_j$ and $B_k$, should vary only because of error variance due to individual differences in factors such as ability, motivation, and physical state, or differences in other factors that can affect performance. Stating this more formally,

```
$Y_{ijk} = \mu_{jk} + \varepsilon_{ijk}\quad(9.1)
```

where $\mu_{jk}$ is defined in Table 9.1 as the mean of the population formed by $A_j$ and $B_k$, and $\varepsilon_{ijk}$ is the error component of the $i$th score in the cell formed by $A_j$ and $B_k$ in the experiment.

Now consider the possibility that scores in different combinations of treatments may differ systematically. It is useful to express the deviation of a score from the grand mean of the populations by subtracting $\mu$ from both sides of Equation 9.1:

```
$Y_{ijk} - \mu = (\mu_{jk} - \mu) + \varepsilon_{ijk}\quad(9.2)
```

| Population parameters | Estimates |
| --- | --- |
| $\mu_{jk} = \text{mean of the population of scores at } A_j \text{ and } B_k$ | $\bar{Y}_{cdotjk} = \sum_{i} Y_{ijk} / n$ $
| $\mu_{j.} = \sum_{k} \mu_{jk} / b = \text{mean of the populations in condition } A_j$ | $\bar{Y}_{jcdot} = \sum_{i,k} Y_{ijk} / nb$ |
| $\mu_{\cdot k} = \sum_{j} \mu_{jk} / a = \text{mean of the populations in condition } B_k$ | $\bar{Y}_{\cdot k} = \sum_{i,j} Y_{ijk} / na$ |
| $\mu = \sum_{j,k} \mu_{jk} / ab = \text{mean of all populations}$ | $\bar{Y}_{\cdot\cdot} = \sum_{i,j,k} Y_{ijk} / nab$ |
| $\varepsilon_{ijk} = Y_{ijk} - \mu_{jk} = \text{error component of } Y_{ijk}$ | |