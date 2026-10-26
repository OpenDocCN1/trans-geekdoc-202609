The following result can be used with Lemma 4.8 to obtain the uniform convergence of training statistics to the test statistics (e.g. test loss). The resulting bound can then be used with Lemma 3.11 to obtain oracle inequalities for empirical risk minimization.

# Lemma 4.11

Let ψ_trn: ℱ × 𝒵^n → ℝ, ψ_val: ℱ × 𝒵^n → ℝ, ψ_tst: ℱ × 𝒟 → ℝ be appropriately training (where 𝒟 denotes probability distributions on 𝒵), validation, and test statistics. Assume that for any δ₁ ∈ (0,1), the following uniform convergence result holds. With probability at least 1 − δ₁ over randomly drawn training and validation sets (𝒮_n, 𝒮'_n) ∼ 𝒟^{2n},

∀ f ∈ ℱ: ψ_val(f, 𝒮'_n) ≤ ψ_trn(f, 𝒮_n) + ε_n^1(δ₁).

Moreover, assume ∀ f ∈ ℱ, we have with probability 1 − δ₂ over randomly drawn 𝒮'_n ∼ 𝒟:

ψ_tst(f, 𝒟) ≤ ψ_val(f, 𝒮'_n) + ε_n^2(δ₂).

Then the following uniform convergence statement holds. With probability at least 1 − δ₁ − δ₂,

∀ f ∈ ℱ: ψ_tst(f, 𝒟) ≤ ψ_trn(f, 𝒮_n) + ε_n^1(δ₁) + ε_n^2(δ₂).

Proof Let Q(f, 𝒮_n) = ψ_tst(f, 𝒟) − ψ_trn(f, 𝒮_n) − (ε_n^1(δ₁) + ε_n^2(δ₂)), and let E be the event that sup_{f ∈ ℱ} Q(f, 𝒮_n) ≤ 0. We pick f̂(𝒮_n) ∈ ℱ so that if E holds, then we choose an arbitrary Q(f̂(𝒮_n), 𝒮_n) ≤ 0, and if E does not hold, we choose f̂(𝒮_n) so that Q(f̂(𝒮_n), 𝒮_n) > 0. We consider sample (𝒮_n, 𝒮'_n) ∼ 𝒟^{2n}. For simplicity, in the following, we let f̂ = f̂(𝒮_n). The uniform convergence condition of the theorem implies that with probability at least 1 − δ₁, the following event holds:

E₁: ψ_val(f̂, 𝒮'_n) ≤ ψ_trn(f̂, 𝒮_n) + ε_n^1(δ₁).

Note that the validation data 𝒮'_n is independent of the training data 𝒮_n. Therefore 𝒮'_n is also independent of f̂. Therefore the condition of the theorem implies that with probability at least 1 − δ₂, the following event holds:

E₂: ψ_tst(f̂, 𝒟) ≤ ψ_val(f̂, 𝒮'_n) + ε_n^2(δ₂).

If both events E₁ and E₂ hold, then

ψ'_tst(f̂, 𝒟) ≤ ψ_val(f̂, 𝒮'_n) + ε_n^2(δ₂) ≤ ψ_trn(f̂, 𝒮_n) + ε_n^1(δ₁) + ε_n^2(δ₂).

The definition of f̂ implies that E holds. Therefore Pr(E) ≥ Pr(E₁ & E₂) ≥ 1 − δ₁ − δ₂. This implies the desired bound.

In the literature, one can also obtain a different bound by considering the independence relationship between f̂ and E₂. We leave the derivation as an exercise.