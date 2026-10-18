
Note that for all five families, a larger value of the parameter `θ` indicates a stronger dependence; all (except the Frank copula) reduce to the independence copula when `θ` takes the minimum value in the respective ranges, while for the Frank copula, the limiting case with `θ` approaching 0 corresponds to the independence copula. The scatter plots for the bivariate case of these five copula families, each based on 2,000 simulated points, are depicted in [Figures 8.20](#c08.xhtml#c08-fig-0020) and [8.21](#c08.xhtml#c08-fig-0021).

Knowing all of the above, we examine the asymptotic behaviour of the Value-at-Risk, as the probability level approaches 1, of the aggregate loss of a portfolio of risks `x₁, …, x_d` whose dependence is given by an Archimedean copula. More precisely, we assume that

```
P(x₁ > x₁, x₂ > x₂, …, x_d > x_d) = ψ^[−1](Σᵢ₌₁^d ψ(F̄ᵢ(xᵢ)))
```

where `F̄ᵢ` is the survival function of `xᵢ`, `ψ: [0, 1] → [0, ∞)` is a generator that is *regularly varying*.

FIGURE 8.20 Scatter plots for bivariate risks by using different Archimedean copulae in R.

FIGURE 8.21 Scatter plots for bivariate risks by using different Archimedean copulae in R (continued).

1. when `α* > 1`, `V@R` is asymptotically subadditive:

```
lim sup (p→1) V@R_p(s) / Σⱼ₌₁^d V@R_p(xⱼ) ≤ 1;
```

2. when `0 < α* < 1`, `V@R` is asymptotically superadditive:

```
lim inf (p→1) V@R_p(s) / Σⱼ₌₁^d V@R_p(xⱼ) ≥ 1;
```
