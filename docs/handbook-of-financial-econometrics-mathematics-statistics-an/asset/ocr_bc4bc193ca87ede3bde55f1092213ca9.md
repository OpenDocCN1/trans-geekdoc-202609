(conditional on a jump occurring) that is lognormally, identically, and independently distributed over time, with the unconditional mean μ_J. The standard deviation of ln[1 + J(t)] is σ_J, q(t) is a Poisson jump counter with intensity λ, that is, Pr{dq(t) = 1} = λdt and Pr{dq(t) = 0} = 1 − λdt, κ_v, θ_v/κ_v and σ_v are respectively the speed of adjustment, long-run mean, and variance coefficient of the diffusion volatility V(t), q(t) and J(t) are uncorrelated with each other or with ω_S(t) and ω_v(t).

The interest rate process is assumed to follow the single-factor Cox et al. (1985) process

```
dR(t) = [θ_R − κ_R R(t)]dt + σ_R √R(t) dw_R(t),  (51A.4)
```

where κ_R, θ_R/κ_R, and σ_R are the speed of adjustment, long-run mean, and volatility coefficient of the R(t) process, w_R(t) is a standard Brownian Motion assumed to be uncorrelated with any other process in the economy.

Note that the volatility risk V(t), interest rate risk R(t), and jump risk J(t)dq(t) are all rewarded in their valuation framework. The factor prices for V(t) and R(t) are respectively b_v V(t) and b_r R(t) for some constants b_v and b_r. These factors are implicitly reflected in (51A.2) and (equation 51A.4) and adjusted through κ_v and κ_R, respectively. Therefore, the risk premiums have been internalized in the stochastic structure rather than being assumed to be zero.

The European call option price with strike price K and term-to-expiration τ by Bakshi et al. (1997) is shown as follows:

```
C(t, τ) = S(t) Π₁(t, τ; S, R, V) − K B(t, τ) Π₂(t, τ; S, R, V),  (51A.5)
```

where the risk-neutral probabilities, Π₁ and Π₂, are recovered from inverting the respective characteristic functions (see Bates, 1996b, 2000; Heston, 1993; for similar treatments)

```
Π_j(t, τ; S(t), R(t), V(t)) = 1/2 + 1/π ∫₀^∞ Re[ e^{-i φ ln[K]} f_j(t, τ, S(t), R(t), V(t); φ) / (i φ) ] dφ,  (51A.6)
```

for j = 1,2, with the characteristic functions f_j respectively given in (51A.7) and (51A.8). The price of a European put option on the same stock can be