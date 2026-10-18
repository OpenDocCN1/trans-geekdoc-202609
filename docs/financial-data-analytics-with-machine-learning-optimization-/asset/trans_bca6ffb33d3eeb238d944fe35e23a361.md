

Let `x₁, ..., xₙ` be iid categorical variables taking `K` (`K << n`) different possible values labelled as `A₁, ..., Aₖ`. Denote by `p₍K₎ = (p₁, ..., pₖ)ᵀ` where `pⱼ = P(x = Aⱼ)` such that `∑ⱼ₌₁ᴷ pⱼ = 1`. The maximum likelihood estimator `p̂₍K₎ = (p̂₁, ..., p̂ₖ)ᵀ` of `p₍K₎` can be obtained by maximizing the log-likelihood function

```
ℓ(p₍K₎) = ln ∏ᵢ₌₁ⁿ ∏ⱼ₌₁ᴷ pⱼ^yᵢⱼ = ∑ᵢ₌₁ⁿ ∑ⱼ₌₁ᴷ yᵢⱼ ln pⱼ
```

subject to the constraint of `p₁ + ... + pₖ = 1`, where `yᵢⱼ := 1{xᵢ = Aⱼ}`. In order to solve this constrained optimization problem, we consider the associated `Lagrangian` with the multiplier `λ`:

```
L(p₍K₎, λ) := ∑ᵢ₌₁ⁿ ∑ⱼ₌₁ᴷ yᵢⱼ ln pⱼ + λ(1 - ∑ⱼ₌₁ᴷ pⱼ).
```

