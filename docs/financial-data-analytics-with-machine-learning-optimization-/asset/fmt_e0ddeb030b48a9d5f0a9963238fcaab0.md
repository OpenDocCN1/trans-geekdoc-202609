
Recall that a classification tree corresponds to a partition of the space of feature vectors `D` into `D₁, ..., Dₘ`, corresponding to the predicted labels `c₁, ..., cₘ`. This then induces the partition of the dataset `S` into `S₁, ..., Sₘ`, where `Sₖ = {(x, y) ∈ S : x ∈ Dₖ}`. Generally speaking, for a given sample `S = {(xᵢ, yᵢ)}ᵢ₌₁ⁿ`, we aim to construct a classification tree `T`, whose number of terminal leaf nodes is denoted by `T` (see [Figure 13.5](#c13.xhtml#c13-fig-0005) for an illustration), that minimizes the classification error:

[(13.14)](#c13.xhtml#R_c13-disp-0046)

```
R(T) := (1/n) Σₗ₌₁ᵀ Σ₍xᵢ,yᵢ₎∈Tₗ 1{yᵢ ≠ ȳ_Tₗ},
```

where `Tₗ` is the set of data points at the `l`-th terminal node, for `l = 1, ..., T`, and `ȳ_Tₗ` is the majority vote for a particular label using all data points in `Tₗ`:

(13.15)

```
ȳ_Tₗ := arg max_{c∈Y} Σ₍xᵢ,yᵢ₎∈Tₗ 1{yᵢ = c},
```
