To make a gamma-neutral portfolio, we should trade ω_o* = −Γ/Γ_o options. Because the position of option changes, the new portfolio is not delta-neutral. We should change the position of the underlying asset to maintain delta-neutral.

For example, the delta and gamma of a particular call option are 0.7 and 1.2, respectively. A delta-neutral portfolio has a gamma of −2,400. To make a delta-neutral and gamma-neutral portfolio, we should add a long position of 2,400/1.2 = 2,000 shares and a short position of 2,000 × 0.7 = 1,400 shares in the original portfolio.

# 86.5 Vega (ν)

The vega of an option, ν, is defined as the rate of change of the option price respective to the volatility of the underlying asset:

ν = ∂Π/∂σ

where Π is the option price and σ is volatility of the stock price. We next show the derivation of vega for various kinds of stock options.

# 86.5.1 Derivation of vega for different kinds of stock options

For a European call option on a non-dividend stock, vega can be shown as

ν = S_t √τ · N'(d₁). (86.21)