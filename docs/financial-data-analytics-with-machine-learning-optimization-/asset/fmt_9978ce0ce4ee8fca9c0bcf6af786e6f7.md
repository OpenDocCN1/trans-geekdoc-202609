
[Figure 14.11](#c14.xhtml#c14-fig-0011) illustrates two possible scenarios. On the left, `K = 4` and `L = 3`, `A₁ = {1, 2}`, `A₂ = ∅` and `A₃ = {3}`. On the right, there are four true clusters and five artificial clusters such that `A₁ = {3, 4}`, `A₂ = {1, 2}` and `A₃ = {5}`. Next, we state the assumption that confines the sizes of variances and the distances between true cluster means. Combined, these hint at why the optimality of CH index is attained at the true cluster number `K`.

![FIGURE 14.11 Illustrations for upper B Subscript k, k equals 1 comma ellipsis comma upper K (colored circle) and the artificial clusters (divided by boundaries in dashed lines).](images/c14f011.png)

**FIGURE 14.11** Illustrations for `Bₖ`, `k = 1, …, K` (colored circle) and the artificial clusters (divided by boundaries in dashed lines).

In the following, we aim to show that for any `a > 0` such that

(14.19) `(1 - (p / a)^(-p)) * exp(-(a² - p²) / (2p)) * (C / δ - 2a) ≥ (√(3K) / q) * √(Σ Var(x_ji) / (Σ pₖ · ||μ_|k·|| - ||μ||²))`

then we have `r∞(L) < r∞(K)`.
