# Multi-Factor Between-Participants Designs 233

three-factor design concisely so that we reinforce the basic concepts already developed for the simpler one- and two-factor designs.
The general case of the three-factor between-participants design involves $a$ levels of $A$, $b$ levels of $B$, $c$ and $n$ scores in each of the $abc$ cells. The relevant indices are

```
$i = 1, 2,...,n; j = 1, 2,...,a; k = 1, 2,...,b$; and $m = 1, 2,...,c$
```

The structural model looks like that for the two-factor experiment except that there are now three two-factor interactions (AB, AC, and BC) and there is the three-factor interaction:

```
$Y_{ijkm} = \mu + \alpha_j + eta_k + \gamma_{im} + (\alpha\gamma)_{jm} + (eta\gamma)_{km} + (\alphaeta)_{jk} + \varepsilon_{ijkm}$  (9.9)
```

In definitions of population means, with estimates of those means, are presented in Table 9.8. The only new definition is that of the interaction effect for the cell $ABeta_k$ is the difference between the cell mean and the grand mean, adjusted for all main and first-order interaction effects that contribute to the cell.
The sums of squares follow directly from the parameter estimates by squaring each term in the Estimate column of Table 9.8 and over the indices. The results of this process are presented in Table 9.9 together with the degrees of freedom. The new $df$ term is $(a-1)(b-1)(c-1)$, $df_{abc}$. By subtracting the main and two-factor from $abc$, the between-cells df.
The means are obtained, by dividing sums of degrees of freedom. $MS_{ABC}$ the average within-cell variance, is the error term against all main and interaction terms are tested. In other designs, the expected mean squares provide the rationale for this choice of error terms; these are presented in Table 9.10. The EMS have been derived from the structural model (Equation 9.9) under the usual assumptions that the scores in the $abc$ treatment populations are independently distributed and that the population variances all equal $\sigma^2$. In addition, all three factors are assumed to have fixed effects; that is, the levels have been arbitrarily selected and not randomly sampled from a universe of treatment levels.

# Table 9.8 Parameters of the structural model for a three-factor design

| Source | Population mean | Estimate |
|---|---||
| A | $\alpha_j = \mu_{j..} - \mu_{...}$ | $	ilde{Y}_{j..} - 	ilde{Y}_{...}$ |
| B | $eta_k = \mu_{.k.} - \mu_{...}$ | $	ilde{Y}_{.k.} - 	ilde{Y}_{...}$ |
| C | $\gamma_m = \mu_{..m} - \mu_{...}$ | $	ilde{Y}_{..m} - 	ilde{Y}_{...}$ |
| AB | $(\alphaeta)_{jk} = \mu_{jk.} - \mu_{...} - eta_k$ | $	ilde{Y}_{jk.} - 	ilde{Y}_{j..} - 	ilde{Y}_{.k.} + 	ilde{Y}_{...}$ |
| AC | $(\alpha\gamma)_{jm} = \mu_{j.m.} - \mu_{...} - \alpha_j$ | $	ilde{Y}_{j.m.} - 	ilde{Y}_{j..} - 	ilde{Y}_{..m} + 	ilde{Y}_{...}$ |
| BC | $(eta\gamma)_{km} = \mu_{.km} - \mu_{...} - eta_k$ | $	ilde{Y}_{.km} - 	ilde{Y}_{.k.} - 	ilde{Y}_{..m} + 	ilde{Y}_{...}$ |
| ABC | $(\alphaeta\gamma)_{jkm} = \mu_{jkm} - \mu_{...}$ | $	ilde{Y}_{jkm} - 	ilde{Y}_{j..} - 	ilde{Y}_{.k.} - 	ilde{Y}_{..m} - 	ilde{Y}_{.jk} - 	ilde{Y}_{j.m} - 	ilde{Y}_{.km} + 	ilde{Y}_{...}$ |
| Error | $\varepsilon_{ijkm}$ | $	ilde{Y}_{ijkm} - 	ilde{Y}_{jkm}$ |