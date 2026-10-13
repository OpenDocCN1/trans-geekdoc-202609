
# Projection onto the weighted ℓ₁ ball B_{ℓ₁}[w, ρ]

1. Form the vector `[|θ₁|/w₁, …, |θₗ|/wₗ]ᵀ ∈ ℝˡ`.

2. Sort the previous vector in a nonascending order, so that `|θ_{τ(1)}|/w_{τ(1)} ≥ … ≥ |θ_{τ(l)}|/w_{τ(l)}`. The notation `τ` stands for the permutation, which is implicitly defined by the sorting operation. Keep in mind the inverse `τ⁻¹`, which is the index of the position of the element in the original vector.

3. `r₁ := l`.

4. Let `m = 1`. While `m ≤ l`, do:

    1. **(a)** `m* := m`.

    2. **(b)** Find the maximum `j*` among those `j ∈ {1, 2, …, rₘ}` such that:
       ```
       |θ_{τ(j)}| / w_{τ(j)} > (∑_{i=1}^{rₘ} w_{τ(i)}|θ_{τ(i)}| - ρ) / (∑_{i=1}^{rₘ} w_{τ(i)}²)
       ```

    3. **(c)** If `j* = rₘ` then break the loop.
