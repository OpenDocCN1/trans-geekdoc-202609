+   - Choose η, ν, w₁, w₂ ←ᴿ ℤₚ* and set h₀ := g^η and k₀ := Γ₂ (g^{w₂})^{1/(ν w₁)}.
+   - Pick ϑ₁, ϑ₂, ϑ₃, τ₂, τ₃ ←ᴿ ℤₚ* and set ξ₁ := Γ₁·g^{ϑ₁}, ξ₂ := (Γ₁)^{τ₂}·g^{ϑ₂}, ξ₃ := (Γ₁)^{τ₃}·g^{ϑ₃}.
+   - For each i ∈ {0,1,2,…,ℓ}, select πᵢ ←ᴿ ℤₚ* and then set uᵢ := g^{πᵢ}.
+   - Choose H₁ : {0,1}* → {0,1}^ℓ and H₂ : {0,1}* → ℤₚ* from appropriate families of collision-resistant hash functions.

Finally, ℬ gives the public parameters

𝒫𝒫 := [Σ, δ, g₂, Y, {hᵢ}ᵢ∈Uₛ, {kᵢ}ᵢ∈Uₑ, h₀, k₀, ω₁, ω₂, ω₃, ω₀, {uᵢ}ᵢ₌₁^ℓ, H₁, H₂, 𝒲, Πₛₑ, KDF, ℳ, 𝒰] to 𝒜.

These parameters have the same distribution as in the real construction from 𝒜’ view.

# Query Phase 1. 𝒜 adaptively issues the following queries.

+   - DecKey Query: The simulation of this query is analogous to the simulation of the Extract query described in the security proof of (t,t)-ABS small universe scheme [16]. That is, when 𝒜 submits [A_d, δ_d] as input for decryption key 𝒟𝒦_{A_d,δ_d}, ℬ responds as in [16].

+   - SignKey Query: For any request of signing key query on [A_s, δ_s], ℬ chooses η₁, η₂, …, η_{s-1} ←ᴿ ℤₚ* and implicitly defines f_i(x) := a + ηx + η₂x² + ⋯ + η_{s-1}x^{s-1}. For each i ∈ A_s, it sets S_i := (Γ₂)^{η_i} g^{-η₂^{i}} (Γ₁)^η Π_{j=1}^{i-1} (Γ₂)^{η_j}. The signing key 𝒮𝒦_{A_s,δ_s} := [δ_s, {S_i, i ∈ A_s}] will be given to 𝒜. It is not difficult to see that the signing key simulated by ℬ is a well-formed key in 𝒜’s point of view.

+   - Unsigncrypt Query: When 𝒜 asks for a Unsigncrypt query on the input [𝒞𝒯, W_v, A_d, δ_d], where 𝒞𝒯 := [W_e, ct := [m, C, {C_i : i ∈ W_e}]], σ := {σ_i : i ∈ W_s}, C_e, γ, δ_s], ℬ checks Equations 9.1 and 9.2, and |A_d ∩ W_e| ≥ δ_d. If any one of these three tests does not hold, it outputs ⊥. Otherwise, if |A_d ∩ W_e*| < δ_d, then ℬ obtains the decryption key 𝒟𝒦_{A_d,δ_d} by performing DecKey query for the tuple [A_d, δ_d] and returns the output of Unsigncrypt(𝒫𝒫, 𝒞𝒯, W_v, 𝒟𝒦_{A_d,δ_d}) to 𝒜. If |A_d ∩ W_e*| ≥ δ_d, ℬ cannot execute the DecKey query and then it responds as follows. First ℬ computes β = H₂(ct || σ || W_e || W_v || δ_s), and checks whether β + γτ₂ + τ₃ = 0 which happens with probability at most 1/p. If so, it aborts (we refer to this event as abort) and outputs a random bit. Else if C := g^α, ℬ can compute Y^α as e(C_e · C^{-(β₁+γτ₂+τ₃)}, Γ₂^{(β+γτ₂+τ₃)^{-1}}) = Y^α where β = H₂(ct || σ || W_e || W_v || δ_s). Now, ℬ returns msg = SE-Dec(KDF(Y^α || W_e || W_v), m) to 𝒜.

# Challenge. 𝒜 outputs two equal length messages msg₀*, msg₁* ∈ ℳ and a signing attribute set W_s* ⊂ U_s. ℬ selects a random bit μ ∈ {0,1} and signcrypts msg_{μ}* under the challenge encryption attribute set W_e* and signing attribute set W_s* in the following way.