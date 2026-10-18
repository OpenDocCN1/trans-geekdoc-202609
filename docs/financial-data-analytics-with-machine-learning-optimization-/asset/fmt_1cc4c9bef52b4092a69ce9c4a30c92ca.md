
Then `x := h(u, γ₁)` and `z := h(1 - u, γ₂)` form a pair of antithetic variables.

*Proof.* We first prove a special case: if the deterministic functions `g₁(θ)` and `g₂(θ)` are increasing in `θ ∈ ℝ`, then for any random variable `x`, the variables `g₁(x)` and `g₂(x)` are positively correlated. To this end, let `x̃` be another random variable which is independent of `x` yet has the same distribution as that of `x`. As both `g₁` and `g₂` are increasing, clearly `(g₁(x) - g₁(x̃))(g₂(x) - g₂(x̃)) ≥ 0` for any `x, x̃ ∈ ℝ`, and so

```
E((g₁(x) - g₁(x̃))(g₂(x) - g₂(x̃))) ≥ 0.
```

Expanding the terms gives

```
E(g₁(x)g₂(x)) + E(g₁(x̃)g₂(x̃)) ≥ E(g₁(x̃)g₂(x)) + E(g₁(x)g₂(x̃)).
```
