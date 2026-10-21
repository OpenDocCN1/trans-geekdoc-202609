σ² = 2(ln(S/X)+rT)/T . Now we are checking second-order conditions under both the two cases:

∂²g(d1)/∂σ² = ∂g'(d1)/∂σ 
= g'(d1) ∂d1/∂σ * d1 d2 /σ + g(d1) (d1 d2 /σ )' 
= g(d1) (d1 d2 /σ )² - g(d1) (d1² + d2² + d1 d2)/σ² 
= g(d1) (d1² d2² - d1² - d2² - d1 d2 ) / σ² .

First-order conditions give that either d1 = 0 or d2 = 0. When d1 = 0, ∂²g(d1)/∂σ² = g(d1) (-d2² / σ²) < 0. Similarly, when d2 = 0, ∂²g(d1)/∂σ² = g(d1) (-d1² / σ²) < 0. ∂²g(d1)/∂σ² < 0 holds under both cases, therefore, g(d1) and f'(σ) are simultaneously maximized.

From the above discussion, we know that the starting point σ1 should be chosen by maximizing the partial derivative of call option respective to volatility f'(σ), as given in equation (106.7):

σ₁² = |ln(S/X) + rT| 2/T . (106.7)

Manaster and Koehler (1982) claimed that by starting with the above σ1, implied variance estimate converges monotonically quadratically.

Brenner and Subrahmanyam (1988) applied Taylor series expansion to the cumulative normal function at zero up to the first order in the Black-Scholes option pricing model.

For at-the-money options, they set the underlying asset price S equal to the present value of exercise price Xe^{-rT}, i.e., S = Xe^{-rT}, then d1 and d2 in equation (106.1) are

d1 = 1/2 σ√T , (106.8)
d2 = -1/2 σ√T .

Taylor series expansion is applied to the cumulative normal function at zero, while ignoring all the remaining terms beyond d1:

N(d1) = N(0) + N'(0)d1 + ⋯ = 1/2 + 1/√(2π) d1 + o(d1) . (106.9)