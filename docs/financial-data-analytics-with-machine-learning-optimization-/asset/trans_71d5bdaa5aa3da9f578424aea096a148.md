

[Figure 14.11](#c14.xhtml#c14-fig-0011) 说明了两种可能的场景。左侧，`K = 4` 和 `L = 3`，`A₁ = {1, 2}`，`A₂ = ∅` 和 `A₃ = {3}`。右侧，有四个真实簇和五个虚拟簇，使得 `A₁ = {3, 4}`，`A₂ = {1, 2}` 和 `A₃ = {5}`。接下来，我们陈述限制方差大小和真实簇均值之间距离的假设。综合起来，这些提示了为什么 CH 指数的最优性在真实簇数 `K` 时达到。

![FIGURE 14.11 Illustrations for upper B Subscript k, k equals 1 comma ellipsis comma upper K (colored circle) and the artificial clusters (divided by boundaries in dashed lines).](images/c14f011.png)

**FIGURE 14.11** Illustrations for `Bₖ`, `k = 1, …, K` (colored circle) and the artificial clusters (divided by boundaries in dashed lines).

在以下内容中，我们旨在证明对于任何 `a > 0` 使得

(14.19) `(1 - (p / a)^(-p)) * exp(-(a² - p²) / (2p)) * (C / δ - 2a) ≥ (√(3K) / q) * √(Σ Var(x_ji) / (Σ pₖ · ||μ_|k·|| - ||μ||²))`

则我们有 `r∞(L) < r∞(K)`。

