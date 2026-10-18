
Here, `x` is bounded above by `M > 1` such that the summation over `k ∈ K_M` only ranges from 0 to `⌊log₁₀ M⌋ - 1`, i.e. the sum is taken over all `⌊log₁₀ M⌋` numbers of blue empty boxes in [Figure 4.1](#c04.xhtml#c04-fig-0001), and there is an additional remainder term corresponding to when `z` falls in the interval `(⌊log₁₀ M⌋, ⌈log₁₀ M⌉]`, i.e., the red shaded box in [Figure 4.1](#c04.xhtml#c04-fig-0001). These blue empty boxes represent the interval `(log₁₀ n + k, log₁₀ (n + 1) + k)` for `k = 0, ..., ⌊log₁₀ M⌋ - 1`. Notice that any possible red shaded box lying in `(⌊log₁₀ M⌋, ⌊log₁₀ M⌋ + 1)` does not contribute to the sum, and the term `ν_{n, remainder}` may be smaller in size than the blue empty boxes.

![FIGURE 4.1 Summation over k ∈ K_M under the ν measure.](images/c04f001.png)

[**FIGURE 4.1**](#c04.xhtml#R_c04-fig-0001) Summation over `k ∈ K_M` under the `ν` measure.

We next consider the following quotient which is the probability of `d₁(x) = n` under the density `f_x^(M)`:

```
StartLayout 1st Row 1st Column StartFraction μ(x ∈ [1, M], d₁(x) = n) Over μ(x ∈ [1, M]) EndFraction 2nd Column equals ⌊log₁₀ M⌋ · StartFraction log₁₀(n + 1) - log₁₀ n Over log₁₀ M EndFraction plus StartFraction ν_{n, remainder} Over log₁₀ M EndFraction 2nd Row 1st Column Blank 2nd Column long right-arrow log₁₀(n + 1) - log₁₀ n = log₁₀(1 + 1/n) comma, as M → infinity period EndLayout
```

