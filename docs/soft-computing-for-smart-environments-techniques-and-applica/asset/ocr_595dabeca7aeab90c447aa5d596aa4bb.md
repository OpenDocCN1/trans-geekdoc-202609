# TABLE 8.7

Defuzzified Decision Matrix for Alternatives in Terms of Sub-Factors

| Criteria | Alternatives |  |  | |
|---|---|---|---|---|
|  | SMS₁ | SMS₂ | ... | SMSₘ |
| C₁ | x₁₁ = [u₁₁ᶜ, θ₁₁ᶜ] | x₁₂ = [u₁₂ᶜ, θ₁₂ᶜ] | ... | x₁ₘ = [u₁ₘᶜ, θ₁ₘᶜ] |
| C₂ | x₂₁ = [u₂₁ᶜ, θ₂₁ᶜ] | x₂₂ = [u₂₂ᶜ, θ₂₂ᶜ] | ... | x₂ₘ = [u₂ₘᶜ, θ₂ₘᶜ] |
| ⋮ | ⋮ | ⋮ | ⋱ | ⋮ |
| Cₙ | xₙ₁ = [uₙ₁ᶜ, θₙ₁ᶜ] | x₃₂ = [u₃₂ᶜ, θ₃₂ᶜ] | ... | xₙₘ = [uₙₘᶜ, θₙₘᶜ] |

Step 12: Compute the normalized decision matrix according to Eq. (8.9) for advantageous criteria and Eq. (8.10) for non-advantageous criteria.

$$X_{ij}=\frac{[x_{ij}-Min(x_{ij})]}{[max(x_{ij})-Min(x_{ij})]}$$ (8.9)

$$X_{ij}=\frac{[max(x_{ij})-x_{ij}]}{[max(x_{ij})-Min(x_{ij})]}$$ (8.10)

Step 13: Compute the evaluative dissimilarities of i th substitute for other substitutes.

Step 14: Calculate the preference function for the normalized decision matrix P_j(a, b) according to Eqs. (8.11) and (8.12).

$$P_j(a,b)=0\text{ if }R_{aj}\le R_{bj}$$ (8.11)

$$P_j(a,b)=(R_{aj}-R_{bj})\text{ if }R_{aj}>R_{bj}$$ (8.12)

Step 15: Compute the weighted preference matrix according to Eq. (8.13) and the combined preference function according to Eq. (8.14).

$$w_j p_j(a,b)$$ (8.13)

$$\pi(a,b)=\frac{\sum_{j=1}^{n} w_j p_j(a,b)}{\sum_{j=1}^{n} w_j},\text{ where }p_j(a,b)\text{ is the preference function}$$ (8.14)