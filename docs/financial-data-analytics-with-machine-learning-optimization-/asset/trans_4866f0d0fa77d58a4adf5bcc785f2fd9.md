

在贝叶斯推断中，我们可以选择几乎任何任意分布作为先验分布 `π(·)`。然而，在实践中，我们通常更倾向于选择 `π(μ)`，它可以简化后验分布的表达式（[1.15](#c01.xhtml#c01-disp-0062））。一种常见的选择可以由似然函数的*共轭先验*概念来证明，使得先验分布本身及其对应的后验分布属于同一分布族。例如，前面章节中引入的先验分布 `μ ~ N(μ₀, σ₀²)` 是正态分布样本似然函数的共轭先验，因为后验分布 `μ | x = x̃ ~ N(μₙ, βₙ⁻¹)` 也是正态分布。

让我们通过研究正态分布中两个参数 `μ` 和 `σ²` 均未知的扩展情况来说明该技术。为了记号简洁，我们使用精度 `λ = σ⁻²` 代替方差，则有 `x | (μ = μ, λ = λ) ~ N(μ, λ⁻¹)`。在观测值 `x = (x₁, ..., xₙ)` 下，似然函数读取：

![FIGURE 1.5 Predictive distributions of normal xₙ₊₁ for various values of n via Bayesian inference.](images/c01f005.png)

[**FIGURE 1.5**](#c01.xhtml#R_c01-fig-0005) Predictive distributions of `xₙ₊₁` for various values of `n` via Bayesian inference.

[(1.25)](#c01.xhtml#R_c01-disp-0076)
```
f(x | μ, λ) = ∏ᵢ₌₁ⁿ fₓ|μ,λ(xᵢ | μ, λ),
```

where `fₓ|μ,λ(xᵢ | μ, λ) = √(λ / 2π) exp(-λ(xᵢ - μ)² / 2)`.

我们接下来考虑*正态-伽马分布*，记为 `NormalGamma(μ₀, β₀, β₀/2 + 1, b)`，具有以下联合概率密度函数：

