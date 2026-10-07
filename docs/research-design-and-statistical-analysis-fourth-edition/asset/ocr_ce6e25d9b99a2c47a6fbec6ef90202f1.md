# Regression With Qualitative and Quantitative Variables

interactions are adjusted for all other effects in the design, resulting in tests of the usual interaction null hypothesis

```
$H_0 : \mu_{jk} - \mu_{j'k} - \mu_{jk'} + \mu_{j'k'} = 0 \text{ for all } j, j', k, \text{ and } k'$
```

However, the three methods produce different tests of the main effects, as would be expected given their different ways of attributing variance to A. Given this, on what basis are we to decide which approach, if any, to use? Our view is that the proper analysis depends upon which researcher assumes to be the bias of confounding sources of variance in the design.

If the variables in the study are manipulated, or if the data in the cells can be viewed as samples from naturally occurring, equal-sized treatment populations, then the unequal cell sizes in the sample reflect random sampling error. That is, we may plan to have equal cell sizes but fail to obtain them because of chance occurrences as equipment failures or participants failing to show up. In this event, it makes sense to give each cell in the design the same weight. The corresponding overall null hypothesis is of interest that the un averages of the c population means at each level of A are equal. That is,

```
$\mu_1 = \mu_2 = \dots = \mu_a$.
```

where

```
$\mu_j' = \frac{1}{c} \sum_k \mu_{jk}$
```

is the unweighted mean of the cell means at the jth level of A. It can be shown (e.g., Myers & Well, 1995) that Method 1 tests this hypothesis. Therefore, Method 1 (which uses Type III of squares) is recommended when unequal cell frequencies occur by chance, as is usually the case in experimental designs. This analysis is summarized in Table 23.4 and illustrated in Table 23.5.

An alternative scenario is that unequal cell sizes in a sample reflect systematic variation in the sizes of cell populations. This would often be the case in observational studies. If we have reliable information about the relative sizes of the cell populations, we can use the cell weights. If we do not have such information, we can use the cell frequencies as weights. In this case, the overall A null hypothesis of interest states that the weighted means of A are equal. That is,

```
$\mu_1' = \mu_2' = \dots = \mu_a'$.
```

where

```
$\mu_j' = \frac{1}{n_j} \sum_k n_{jk} \mu_{jk}$
```