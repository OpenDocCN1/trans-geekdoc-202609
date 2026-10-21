Thus, the option pricing formula for the CEV model as given in (109.44) that can be obtained directly from the payoff function

max(S_T - K, 0) = { S_T - K, if S_T > K, 0, otherwise, }

(109.47)

by taking the expectation of (109.47), with S_T having the distribution given by (109.46).

Before concluding this subsection we consider that the noncentral Chi-square distribution will approach log-normal as β tends to 2. Since when either λ or v approaches to infinity, the standardized variable

χ²_v(λ) - (v + λ) / √(2(v + 2λ))

tends to N(0,1) as either v → ∞ or λ → ∞. Using the fact that (x^a - 1)/a will approach to ln x as a → ∞, it can be verified that

χ²_v(λ) - (v + λ) / √(2(v + 2λ)) = 2k* S_T^{2-β} - (v + λ) / √(2(v + 2λ)) = [2r* S_T^{2-β} - (1 - β)σ²(e^{r*τ(2-β)} - 1) - 2r* S_t^{2-β} e^{r*τ(2-β)} ] / σ²(e^{r*τ(2-β)} - 1) × √[ σ²(e^{r*τ(2-β)} - 1)/(2 - β) / ((1 - β)σ²(e^{r*τ(2-β)} - 1) + 4r* S_t^{2-β} e^{r*τ(2-β)}) ] = ln S_T - [ln S_T + (r* - σ²/2)τ ] / σ√τ ,

where r* = r - a. Thus,

ln S_T | ln S_T ~ N ( ln S_T + (t - a - σ²/2)τ , σ²τ ),

(109.48)

as β → 2^-. Similarly, equation (109.48) also holds when β → 2^+. From equation (109.45), we have 2k* S_T^{2-β} ~ χ²_v(λ), where v = 2 + 2/(β - 2) if β > 2. Thus, we clarify the result of equation (109.48).

# 109.5 Some Computational Considerations

As noted by Schröder (1989), equation (109.39) allows the following iterative algorithm to be used in computing the infinite sum when z and k are not