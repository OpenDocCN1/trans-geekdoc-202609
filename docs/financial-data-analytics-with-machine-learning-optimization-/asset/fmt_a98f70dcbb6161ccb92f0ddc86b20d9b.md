
Let us present several numerical examples to illustrate these claims. We consider a Clayton copula with the parameter `θ = 1`, whose generator is given by `ψ(t) = t^(-1) - 1`. We use the `R` package `copula` to simulate the Clayton copula with some given marginals. By generating `10^7` data points from the corresponding joint distributions, we plot the V@R ratios of `(V@R_p(s)) / (Σ(i=1 to d) V@R_p(x_i))` in the `y`-axis against the probability level `p` in the `x`-axis, with `d = 2, 5`. Illustrations for various scenarios are depicted in [Figures 8.22](#c08.xhtml#c08-fig-0022) to [8.24](#c08.xhtml#c08-fig-0024).

## (VII) Extreme-value Copulae

Finally, we introduce the family of extreme-value copulae, whose first construction dates back to [15](#c08.xhtml#c08-bib-0015), [22](#c08.xhtml#c08-bib-0022). A copula `C` is called an *extreme-value copula* if there exists a copula `C_F` such that

```
(C_F(u_1^(1/n), ..., u_d^(1/n)))^n → C(u_1, ..., u_d) as n → ∞
```

for all `(u_1, ..., u_d) ∈ [0, 1]^d`. The copula `C_F` is said to be in the *domain of attraction* of the copula `C`. A closely related concept is *max-stability:* a `d`-dimensional copula `C` is *max-stable* if it satisfies

```
C(u_1, ..., u_d) = (C(u_1^(1/m), ..., u_d^(1/m)))^m
```
