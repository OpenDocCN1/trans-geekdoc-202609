

A set `X ⊆ ℝᵖ` is said to be *convex* if for any two points `x₁, x₂ ∈ X`, the line segment joining them is still contained in `X`, that is, `αx₁ + (1 − α)x₂ ∈ X` for any `α ∈ (0, 1)`. A set `X ⊆ ℝᵖ` is said to be *compact* if `X` is closed and bounded.

![FIGURE 11.17 (a) A compact convex set; (b) A convex, but non‐compact, set; (c) A compact non‐convex set.](images/c11f017.png)

**FIGURE 11.17** (a) 紧凑凸集；(b) 凸但非紧凑集；(c) 紧凑非凸集。

![FIGURE 11.18 The two paths of optimizations taken with respect to von Neumann's Minimax Theorem.](images/c11f018.png)

[**FIGURE 11.18**](#c11.xhtml#R_c11-fig-0018) 关于冯·诺伊曼极小极大定理的两条优化路径。

在下面的证明中，我们将展示，在 [定理 11.1](#c11.xhtml#c11-fea-0002) 的假设下，`f` 的鞍点 `(x₀, y₀)` 始终存在，按定义，该点满足

```
max_{y ∈ Y} f(x₀, y) = f(x₀, y₀) = min_{x ∈ X} f(x, y₀);
```

此外，鞍点的存在实际上意味着 ([11.26](#c11.xhtml#c11-disp-0057)) 的有效性：

```
max_{y ∈ Y} min_{x ∈ X} f(x, y) = max_{y ∈ Y} f(x₀, y) = f(x₀, y₀) = min_{x ∈ X} f(x, y₀) = min_{x ∈ X} max_{y ∈ Y} f(x, y).
```

这里，最左侧的表达式对应于 [图 11.18](#c11.xhtml#c11-fig-0018) 中蓝色的下方路径，而最右侧的项对应于同一图中红色的上方路径。两条路径都汇聚于同一点 `(x₀, y₀)`。然而，一般来说，即使 `f` 的鞍点不存在，极小极大定理仍然成立。

