TΨₜT⁻¹ and Φₛ = TΨₛT⁻¹, which satisfy the following equations

U₂ = U₁Φₜ and U₄ = U₃Φₛ  (21)

Let μₗ and νₗ for l = 1, 2, ···, L be the corresponding eigenvalues of Φₜ and Φₛ. Thus the estimates of ω and θ can be given as follows

ω̂ = 2/[L(L + 1)] Σₗ₌₁ᴸ μₗ,

θ̂ = arcsin( (2c Σₗ₌₁ᴸ νₗ) / (L(L + 1)ω̂ fₛ d) )  (22)

It can be seen from (20) that the estimation accuracy of θ̂ depends on that of ω̂.

# C. Spatio-temporal Signal Model in the Presence of Multi-pitch

To solve the problem of joint estimation of the DOA and pitch in the multi-pitch case, a multi-channel and multi-pitch harmonic multiple signal classification (MC-HMUSIC) method was presented in [34], where a two dimensional search is required to obtain the estimates of the pitch and DOA. To further reduce the computational complexity of the 2-D search in the MC-HMUSIC method, a two-stage DOA and pitch estimation method based on a subspace approach, i.e., MCOW-HUMUSIC, was recently proposed in [35]; however, the two 1-D searches and an iterative procedure for the refined estimation are still required for the MCOW-HMUSIC method. Furthermore, the coupling of the pitch and DOA parameters is still required and poses a significant problem. In this subsection, a generalization of the previously proposed ESPRIT method for joint DOA and pitch estimation of the single pitch case to the multi-pitch case is derived.

Following a procedure similar to the single pitch case, with model in (1), for a given integer M and satisfying RM > Σₚ₌₁ᴾ Lₚ, one can construct the following data vector

X(n) = S(n) + Q(n), n = 0, 1, ···, N − M,  (23)

where

X(n) = [ x₀(n) ··· x₀(n + M − 1); ⋮ ⋱ ⋮; xᴿ₋₁(n) ··· xᴿ₋₁(n + M − 1) ].  (24)

The part of the signal of interest S(n) in X(n) can be rewritten as

S(n) = Σₚ₌₁ᴾ Σₗ₌₁ᴸₚ βₚ,ₗ(n) aₛ(lϕₚ) aₜᵀ(lωₚ).  (25)

where

βₚ,ₗ(n) = αₚ,ₗeʲˡωₚⁿ,

aₛ(ϕₚ) = [1 eʲϕₚ ··· eʲ⁽ᴿ⁻¹⁾ϕₚ]ᵀ,

aₜ(ωₚ) = [1 eʲωₚ ··· eʲ⁽ᴹ⁻¹⁾ωₚ]ᵀ.  (26)

Stacking the columns of X(n) into a new vector model x(n) gives

x(n) = vec{X(n)}
= s(n) + q(n) = Az(n) + q(n),  (27)

with

A = [A⁽¹⁾(ω₁, ϕ₁), ···, A⁽ᴾ⁾(ωᴾ, ϕᴾ)],  (28)

A⁽ᵖ⁾ = [a(ωₚ, ϕₚ), ···, a(Lₚωₚ, Lₚϕₚ)], p = 1, ···, P,  (29)

a(lₚωₚ, lₚϕₚ) = aₜ(lₚωₚ) ⊗ aₛ(lₚϕₚ),  (30)

z(n) = [α₁,₁eʲω₁ⁿ, ···, α₁,ᴸ₁eʲᴸ¹ω₁ⁿ, ···, αᴾ,₁eʲωᴾⁿ, ···, αᴾ,ᴸᴾeʲᴸᴾωᴾⁿ]ᵀ

For n = 0, 1, ···, N − M, we first define the following vector with X(n),

Yᴿᴹ×⁽ᴺ⁻ᴹ⁺¹⁾ = [x(0) x(1) ··· x(N − M)]
= A[z(0) z(1) ··· z(N − M)]
  + [q(0) ··· q(N − M)].  (31)

Thus, the above spatio-temporal signal model for the multi-pitch case can be reduced to the case of a single pitch in the previous section when P = 1 in (23).

# D. Joint Estimation of DOA and Pitch in the Multi-pitch Case Using ESPRIT: Multichannel Multi-Pitch ESPRIT (MMP-ESPRIT)

To use the ESPRIT method for joint estimation of DOA and pitch in the multi-pitch case, the singular value decomposition (SVD) of the data matrix Y is expressed by

Y = UΣVᴴ = [Uₛ Uₙ] [Σₛ 0; 0 Σₙ] Vᴴ,  (32)

where the column vectors of Uₛ and Uₙ span the signal subspace and noise subspace, respectively. The diagonal elements of Σₛ are composed of the P₀ = Σₚ₌₁ᴾ Lₚ largest singular values of Y, and one also has that Uₛ = AT for a nonsingular position matrix T.

Using the shift invariance structure of a(lωₚ, lϕₚ) in A, we can obtain the following two equations,

A₁Ψₜ = A₂,  (33)
A₃Ψₛ = A₄,  (34)

where Aᵢ = WᵢᵀA, i = 1, 2, 3, 4. Ψₜ and Ψₛ are defined as

Ψₜ = diag(Ψₜ₁, ···, Ψₜᴾ)
Ψₜₚ = diag(eʲωₚ, ···, eʲᴸᴾωₚ)
Ψₛ = diag(Ψₛ₁, ···, Ψₛᴾ)
Ψₛₚ = diag(eʲϕₚ, ···, eʲᴸᴾϕₚ).  (35–36)

Accordingly, one can also obtain the following equations by the subspace property,

U₂ = U₁Φₜ and U₄ = U₃Φₛ,  (37)

where

U₁ = W₁Uₛ and U₂ = W₂Uₛ,