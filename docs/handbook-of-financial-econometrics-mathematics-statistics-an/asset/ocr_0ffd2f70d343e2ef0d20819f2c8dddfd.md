# Constant Elasticity of Variance Option Pricing Model

implying

Q(z;2n, k) + Q(k; 2 - 2n, z) = 1, (109.43)

with degrees of freedom 2 - 2n of Q(k;2 - 2n, z) can be a non-integer.

From equation (109.42), we can obtain the noncentral Chi-square Q(2y; 2/2(2-β),2x) with 2 - 2/(2 - β) degrees of freedom and the non-centrality parameter 2x can be represented by another noncentral Chi-square distribution 1 - Q(2x; 2/2(2 - β),2y) with degrees of freedom 2/(2 - β) and the noncentrality parameter 2y. The standard definition of noncentral Chi-square distribution in Section 109.3 has integer degrees of freedom. If the degree of freedom is not an integer, we can use equation (109.43) to transfer the original noncentral Chi-square distribution into another non-central Chi-square distribution. Thus, we obtain an option pricing formula for the CEV model in terms of the complementary noncentral Chi-square distribution function Q(z;u,k) which is valid for any value of β less than 2, as required by the model.

Substituting equation (109.41) into equation (109.34), we obtain

C = S_t e^{-aτ} Q (2y; 2 + 2/(2 - β),2x) - K e^{-rτ} (1 - Q (2x; 2/(2 - β),2y)), (109.44)

where y = k* K^{2-β}, x = k* S_t^{2-β} e^{(r-a)(2-β)τ}, k* = 2(r - a)/(σ²(2 - β)) (e^{(r-a)(2-β)τ} - 1)) and a is the continuous proportional dividend rate. The corresponding CEV option pricing formula for β > 2 can be derived through a similar manner.

When β > 2 (see Emanuel and Macbeth 1982, Chen and Lee 1993), the call option formula is as follows:

C = S_t e^{-aτ} Q (2x; 2/(β-2),2y) - K e^{-rτ} (1 - Q (2y; 2/(β-2),2x)). (109.45)

We note that from the evaluation of the option pricing formula C, especially C₂, as given in (109.34), we have

2k* S_T^{2-β} ~ χ²_v (λ), (109.46)

where

v = 2 - 2/(2 - β),

λ = 2k* S_t^{2-β} e^{(r-a)(2-β)τ},

and a is the continuous proportional dividend rate.