
The main concern with each of the divergence based DP measures is a lack of transparency of how the attacker can best distinguish the hypotheses `o ∼ ℳ(d)` and `o ∼ ℳ(d')`. The next section introduces the `f`-DP framework which provides a hypothesis testing based approach. It introduces trade-off functions that capture all the information needed for fully characterizing privacy leakage; a trade-off function can be used to derive any divergence based DP guarantee like those discussed above (but not the other way around), see Appendix B in [11]. Rather than extracting a divergence based DP guarantee from a trade-off function for DP-SGD, we will keep the trade-off function itself as it has an easy transparent interpretation.

## 2.4 Gaussian differential privacy

Dong et al. [11] introduced the state-of-the-art DP formulation based on hypothesis testing. From the attacker's perspective, it is natural to formulate the problem of distinguishing two neighboring data sets `d` and `d'` based on the output of a DP mechanism `ℳ` as a hypothesis testing problem:

`H₀ : the underlying data set is d` vs. `H₁ : the underlying data set is d'`.

Here, neighboring means that either `|d ∖ d'| = 1` or `|d' ∖ d| = 1`. More precisely, in the context of mechanism `ℳ`, `ℳ(d)` and `ℳ(d')` take as input representations `r` and `r'` of data sets `d` and `d'` which are 'neighbors.' The representations are mappings from a set of indices to data samples with the property that if `r(i) ∈ d ∩ d'` or `r'(i) ∈ d ∩ d'`, then `r(i) = r'(i)`. This means that the mapping from indices to data samples in `d ∩ d'` is the same for the representation of `d` and the representation of `d'`. In other words, the mapping from indices to data samples for `d` and `d'` only differ for indices corresponding to the differentiating data samples in `(d ∖ d') ∪ (d' ∖ d)`. In this sense the two mappings (data set representations) are neighbors.

We define the Type I and Type II errors by

`α[ϕ] = 𝔼[o ∼ ℳ(d)][ϕ(o)]` and `β[ϕ] = 1 − 𝔼[o ∼ ℳ(d')][ϕ(o)]`,

where `ϕ ∈ [0, 1]` denotes the rejection rule which takes the output of the DP mechanism as input. We flip a coin and reject the null hypothesis with probability `ϕ`. The optimal trade-off between Type I and Type II errors is given by the trade-off function

```
T(ℳ(d), ℳ(d'))(α) = inf_ϕ {β_ϕ : α_ϕ ≤ α},
```

for `α ∈ [0, 1]`, where the infimum is taken over all measurable rejection rules `ϕ`. If the two hypotheses are fully indistinguishable, then this leads to the trade-off function `1 − α`. We say a function `f ∈ [0, 1] → [0, 1]` is a trade-off function if and only if it is convex, continuous, non-increasing, and `0 ≤ f(x) ≤ 1 − x` for `x ∈ [0, 1]`.

We define a mechanism `ℳ` to be `f`-DP if `f` is a trade-off function and

`T(ℳ(d), ℳ(d')) ≥ f`

for all neighboring `d` and `d'`. Proposition 2.5 in [11] is an adaptation of a result in [56] and states that a mechanism is `(ϵ, δ)`-DP if and only if the mechanism is `f[ϵ, δ]`-DP, where

`f[ϵ, δ](α) = max {0, 1 − δ − e^(ϵ)α, (1 − δ − α)e^(−ϵ)}`.

We see that `f`-DP has the `(ϵ, δ)`-DP formulation as a special case. It turns out that the original DP-SGD algorithm can be tightly analyzed by using `f`-DP.

### 2.4.1 Gaussian DP

In order to proceed, [11] first defines Gaussian DP as another special case of `f`-DP as follows: We define the trade-off function

`G[μ](α) = T(𝒩(0, 1), 𝒩(μ, 1))(α) = Φ(Φ^(−1)(1 − α) − μ)`,

where `Φ` is the standard normal cumulative distribution of `𝒩(0, 1)`. We define a mechanism to be `μ`-Gaussian DP if it is `G[μ]`-DP. Corollary 2.13 in [11] shows that a mechanism is `μ`-Gaussian DP if and only if it is `(ϵ, δ(ϵ))`-DP for all `ϵ ≥ 0`, where

```
δ(ϵ) = Φ(−ϵ/μ + μ/2) − e^ϵ Φ(−ϵ/μ − μ/2).
```
(2.7)

Suppose that a mechanism `ℳ(d)` computes some function `u(d) ∈ ℝⁿ` and adds Gaussian noise `𝒩(0, (cσ)²I)`, that is, the mechanism outputs `o ∼ u(d) + 𝒩(0, (cσ)²I)`. Suppose that `c` denotes the sensitivity of function `u(·)`, that is,

```
∥u(d) − u(d')∥ ≤ c
```
