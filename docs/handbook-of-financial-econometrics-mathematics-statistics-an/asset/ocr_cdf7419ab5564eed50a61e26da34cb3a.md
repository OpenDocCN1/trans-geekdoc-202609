# Appendix 68A

Fieller (1932) has obtained a marginal density function of a ratio of two normal random variables. The distribution function ψ(v) of the estimated Treynor’s measure can be obtained from Fieller’s equation (68.24) by letting the correlation coefficient to be zero:

ψ(v) = 1/π · σ₁σ₂/(σ₂² + v²σ₁²) · e^{-½{(β²/σ₁²)+[(μ−R_f)²/σ²]}} + e^{-½{[(μ−R_f)−αβ]²/(σ₂²v²σ₁²)}} · [−βσ₂² − vσ₁²(μ−R_f)]/[π(σ₂²+v²σ₁²)^{3/2}] ∫₀ʰ e^{-½μ²} du −∞ < v < ∞,

where v = (R̄ − R_f)/β̂,

σ₁² = Var(β̂) = σ_ε² / Σ₁ⁿ (R_Mt − R̄_M)²,

and

σ₂² = Var(R̄ − R_f) = σ² / n  (σ = Var(R_u)).

# Appendix 68B

The derivation of E(R̄ − R_f)/β̂ by independent property of (R̄ − R_f) and truncated β̂,

E( (R̄ − R_f)/β̂ ) = E(R̄ − R_f) · E(1/β̂) = (μ − R_f) · E(1/β̂).  (68B.1)

The last equality is obtained using the following lemma: if x₁ and x₂ are independent, then E[g₁(x₁)g₂(x₂)] = E[g₁(x₁)] · E[g₂(x₂)] where g₁(x₁) and g₂(x₂) are real-valued (measurable) functions of x₁ and x₂. In our case, we identify R̄ and 1/β̂ as g₁(x₁) and g₂(x₂), respectively. See Roussas (1973, p. 123, Lemma 3). Thus, E(1/β̂) is determined as follows:

E(1/β̂) = ∫ₐᵇ 1/β̂ · 1/[k√(2π)σ_β̂] · exp[−½((β̂−β)/σ_β̂)²] dβ̂,  (68B.2)