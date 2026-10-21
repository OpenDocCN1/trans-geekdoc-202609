Matytsin, A. (1999). Modelling Volatility and Volatility Derivatives. In Columbia Practitioners Conference on the Mathematics of Finance.
Matytsin, A. (2000). Perturbative analysis of volatility smiles. Work. Pap.
Merton, R. C. (1976). Option Pricing when Underlying Stock Returns are Discontinuous. Journal of Financial Economics, 3(1-2), 125-144.
Rebonato, R. (2004). Volatility Correlation. John Wiley & Sons Ltd., second edition.
Scott, L. (1987). Option Pricing When the Variance Changes Randomly: Theory, Estimation, and An Application. Journal of Financial and Quantitative Analysis, 22, 419-438.
Wiggins, J. (1987). Option Values Under Stochastic Volatilities. Journal of Financial Economics, 19, 351-372.
Wharton Research Data Services. “OptionMetrics” wrds.wharton.upenn.edu.

# Appendix 33A: Brief Review of Stochastic Volatility Models

Volatility was identified as the focal quantity for option pricing by Black and Scholes (1973). In the Black-Scholes framework volatility is assumed to be a deterministic process. Randomness entered the model via the Brownian motion driving the underlying asset. Later contributions, starting with Merton (1976) recognized the presence of jumps. Another strand of research, initiated by the constant elasticity of variance (CEV) model of Cox (1975), made stochastic volatility an adapted stochastic process and investigated different functional forms for volatility. A different approach to option pricing allows the variance process to be influenced by its own source of randomness. The general form of the stochastic volatility model (without jump components) is:

```
dS_t = r_{RN} S_t dt + f(S_t V_t) dW_{s,t}^Q,

dV_t = μ_V(V_t) dt + g(V_t) dW_{v,t}^Q,

dW_{s,t}^Q dW_{v,t}^Q = ρ dt, (33A.1)
```

where r_{RN} is the risk-neutral drift parameter, f(S_t, V_t) is a diffusion function in the equation for the underlying asset, and g(V_t) is a diffusion function in the equation for the variance, W_{i,t}^Q (i = {s, v}) are Brownian motions under the risk-neutral measure Q and ρ is the instantaneous correlation coefficient.

Hull and White (1987), Scott (1987), and Wiggins (1987) are the original contributions that launched the research into stochastic volatility. While Hull and White (1987) take both the stock and variance processes to be lognormal, Scott (1987) postulates an Ornstein-Uhlenbeck process for the variance with μ_V(V_t) = -λ(V_t - v̄) and g(V_t) = γ, where λ, v̄ and γ are positive constants.