If there exists an integer 1 ≤ H' ≤ ℬ such that Δρ(A − H', H') ≤ 0, then Δρ(G, H) is strictly decreasing in H for H' ≤ H ≤ ℬ.

Proof. Similar to the proof of Lemma 46.6, we have for A ≥ 2 and 1 ≤ H ≤ ℬ,

Δρ(G, H) = ρ(G, H) − ρ(G + 1, H − 1) = [λ[1 − π_I(0)] ω/G − η Σ_{n=1}^S n π_I(n)/G − γ − α H/G − β Σ_{k=0}^{H−1} (H − k) π_C(k)/G] − [λ[1 − π_I(0)] ω/(G+1) − η Σ_{n=1}^S n π_I(n)/(G+1) − γ − α (H−1)/(G+1) − β Σ_{k=0}^{H−2} (H − k −1) π_C(k)/(G+1)] = [λ[1 − π_I(0)] ω − η Σ_{n=1}^S n π_I(n) − α A − β Σ_{k=0}^{H−1} (A − k) π_C(k)] / [G(G+1)].

If there exists an H' ∈ {1, …, ℬ} such that Δρ(A − H', H') ≤ 0, then it follows that Δρ(G, H) is strictly decreasing in H for H' ≤ H ≤ ℬ, since π_C(k) > 0 for 0 ≤ k ≤ A and G decreases as H increases.

# Theorem 46.5:

Given inventory base stock level S, rate parameters λ, μ, ν, and financial parameters ω, η, γ, α, β, ℓ, let G and H be any capital investment and credit limit parameters, respectively, such that their sum A = G+H is constant. Then, the equilibrium rate of return ρ of equation (46.30) is maximized at (G*, H*), where

H* = { 0, if A = 1 or π_C(0) ≥ [λ[1 − π_I(0)] ω − η Σ_{n=1}^S n π_I(n)]/(β A) − α/β ; max{ H : 1 ≤ H ≤ ℬ, Σ_{k=0}^{H−1} (A − k) π_C(k) < 1/β [ λ[1 − π_I(0)] ω − η Σ_{n=1}^S n π_I(n) − α A ] } , otherwise } (46.34) and G* = A − H* , (46.35) where ℬ = min { A − 1, ⌊ ℓ/(ℓ+1) A ⌋ } .