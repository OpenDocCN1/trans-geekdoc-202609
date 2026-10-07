# 372 Research Design and Statistical Analysis

# 14.3.1 The Structural Model and EMS for the Mixed Design

In designs such as the Table in Table 14.S, $n$ participants are tested at $A_i$, $n$ other participants are tested at $A_j$, and so on. All $an$ participants are tested at each of the $b$ levels of the independent variable $B$. Therefore, $ab - 1$ df must be accounted for in the analysis of variance. With respect to notation, we refer to $Y_{ijk}$ where $i$ indexes the participant $(i = 1, 2, \dots, n)$, $j$ indexes the level of the within-participants $(j = 1, 2, \dots, a)$, and $k$ indexes the level of the within-participants $(k = 1, 2, \dots, b)$. In Table 14.S, $n=6$, $a=3$, and $b=4$.

As always, the structural model underlies the partitioning of the total variability in the ANOVA. The model used for the data in Table 14.5 is

```
$Y_{ijk} = \mu + \alpha_j + \eta_{ij} + eta_k + (\alphaeta)_{jk} + (\etaeta)_{kj} + \varepsilon_{ijk}$  (14.2)
```

There are important differences between this equation and Equation 14.1 for the $S 	imes A 	imes B$ design. These differences rest on nested variables and crossed variables. Participants are nested within different participants at each level of $A$; the same is for SB interaction effects. We have indicated these relationships by inserting a slash before $j$ in the subscripts for participants and SB effects at levels of $A$ $[n_{ij}(\etaeta)_{kj}]$. Also, because SB effects are nested at levels of $A$, there are no SAB interaction effects in the model. In contrast, SB interaction effects because participants cross with $B$, that is, all participants are tested at all levels of $B$. The parameters and their variances are defined in Table 14.6.

Table 14.7 contains the sources of variance, $df$ and $SS$ formulas, and the EMS. The sources of variance- and within-participants terms follow Equation 14.2. In panel $A_i$, we have organized them into between- and within-participants to emphasize the relationship of designs encountered

# Table 14.6 Components of the structural model for the mixed design

| Population parameter | Definition | Variance |
| --- | --- | --- |
| $\eta_{ij}$ | $\mu_{ij} - \mu_j$ | $\sigma_{S/A}^2 = E(\eta_{ij}^2)$ |
| $\alpha_j$ | $\mu_j - \mu$ | $\sigma_{\alpha}^2 = \sum_{k} \alpha_j^2 / a$ |
| $eta_k$ | $\mu_k - \mu$ | $\sigma_{eta}^2 = \sum_{i,j} eta_k^2 / ab$ |
| $(\etaeta)_{kj}$ | $(\mu_{ij} - \mu_j) - \eta_{ij} - eta_k$ | $\sigma_{SB/A}^2 = E((\etaeta)_{kj}^2) / b$ |
| $(\alphaeta)_jk$ | $(\mu_{jk} - \mu_k) - \alpha_j - eta_k$ | $\sigma_{AB}^2 = \sum_{i,j} (\alphaeta)_{jk}^2 / ab$ |
| $\varepsilon_{ijk}$ | $Y_{ijk} - Y_{jk}$ | $\sigma_{\varepsilon}^2 = E(Y_{ijk} - Y_{jk})^2$ |

> Note: $\mu_i = E(Y_i)$, $\mu_{ij} = E(\mu_{ij})$, $\mu_j = \sum_k \mu_{ijk} / b$, $\mu_k = \sum_{i,j} \mu_{ijk} / ab$, $\mu_i = \sum_{j,k} \mu_{ijk} / ab$, $\mu_{ij} = E[\sum_k \mu_{ijk} / b] / a$, and $\mu = E(\mu_j)$. The random effects—$\eta_{ij}$, $(\etaeta)_{kj}^{j}$, and $\varepsilon_{ijk}$—are assumed to be normally distributed with mean zero and variance as noted in the table.