1 − δ/2,

φ(w, Sₙ) ≤ φ(w, D) + √[2 Var_{Z∼D}[φ(w,Z)] ln(2/δ) / n] + M ln(2/δ)/(3n)
≤ φ(w, D) + √[2(c₀² + c₁ φ(w, D)) ln(2/δ) / n] + M ln(2/δ)/(3n)
≤ φ(w, D) + √[2c₀² ln(2/δ)/n] + √[2c₁ φ(w, D) ln(2/δ)/n] + M ln(2/δ)/(3n)
≤ (1 + 0.5α) φ(w, D) + √[2c₀² ln(2/δ)/n] + (3c₁ + αM) ln(2/δ)/(3αn).

The first inequality used Bennett’s inequality for the sum of independent random variables. The second inequality used the variance condition. The third inequality used √[a + b] ≤ √a + √b. The last inequality used √[2ab] ≤ 0.5αa + b/α.

Moreover, from Theorem 6.41 with h(φ(w,·)) = h′(w), we obtain with probability 1 − δ/2:

(1 − 5α) φ(ŵ, D) ≤ φ(ŵ, Sₙ) − 5α φ(ŵ, D) + 5α h′(ŵ) + 5r₀ + √[2c₀² ln(2/δ)/n] + (3c₁ + 4αM) ln(2/δ)/(3αn)
= φ(ŵ, Sₙ) + 5α h₀(ŵ) + 5r₀ + √[2c₀² ln(2/δ)/n] + (3c₁ + 4αM) ln(2/δ)/(3αn)
≤ φ(w, Sₙ) + 5α h₀(w) + ε′ + 5r₀ + √[2c₀² ln(2/δ)/n] + (3c₁ + 4αM) ln(2/δ)/(3αn).

The first inequality used Theorem 6.41. The second inequality used (6.1). By taking the union bound of the two inequalities, we obtain with the probability at least 1 − δ:

(1 − 5α) φ(ŵ, D) ≤ [(1 + 0.5α) φ(w, D) + 5α h₀(w)] + ε′ + 5 rₙ^{h′}(α, G, D) + 5α[φ(w, D) + h₀(w)] + 7 √[2c₀² ln(2/δ)/n] + (7c₁ + 10αM) ln(2/δ)/(αn),

where we used ln(2/δ) ≥ 1 to simplify the result. By taking the inf over w ∈ Ω on the right-hand side, we obtain the first bound. By using Proposition 6.40, we obtain

5 rₙ^{h′}(α, G, D) ≤ 10 eₙ^{0.5α h′}(G, D) + 5α[φ(w, D) + h₀(w)].
Substitute into the previous inequality, and take the inf over w ∈ Ω on the right-hand side, we obtain the second bound.