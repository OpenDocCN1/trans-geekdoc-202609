by the correlation coefficient, ρ_ij,13 then V_j,t+1 = λ_j R_j,t + ε_j,t+1 = λ_j ρ_ij R_i,t + ε_j,t+1. To specify the stock return of market i associated with an expected risk from market j, we write: R_i,t+1 = γ_ij E(V_j,t+1) + ε_ij,t+1; using the information contained in V_j,t+1 and taking an expectation, we yield: R_i,t+1 = γ_ij λ_j ρ_ij R_i,t + ε_ij,t+1. Thus, the risk-return dynamic relations, including leverage effects across markets and autocorrelations in stock return and downside risk, are summarized in equation (58.9).

```
[R_i,t+1; V_j,t+1] = [γ_ij λ_j ρ_ij  γ_ij φ_j; λ_j ρ_ij  φ_j] [R_i,t; V_j,t] + u_ij,t+1. (58.9)
```

Equation (58.9) is a more general specification, since the imposition of λ_j = 0 (the absence of cross-market leverage effects) or ρ_ij = 0 (R_j,t and R_i,t are uncorrelated) would lead to equation (58.6). λ_j can be calculated through λ_j = λ_j ρ_ij / ρ_ij.

Table 58.3 reports the estimated results of equations (58.8) and (58.9). The leverage effect, a negative relation between downside risk and the lagged return, is present in some Asian markets, including Hong Kong, Thailand, and Malaysia, where λ_i < 0. It appears that the coefficients of the downside risk become less significant after incorporating the leverage effect, implying that the leverage effect is imperative for some markets.14 However, the evidence suggests that the leverage effect displays only in some markets, not in all of the markets. The cross-market leverage effects from most Asian countries to China are more apparent, implying that the lagged return shocks on Asian countries will subsequently increase downside risk in China. This evidence is not in agreement with the claim that Chinese stocks are typically insulated from external disturbances. On the other hand, the cross-market leverage effects of most Asian countries on the US are relatively milder and do not present a consistent sign, especially in the Korean, Hong Kong, and Indonesian markets.15

With respect to the estimated coefficients of γ_ii for Asian markets, we find mixed signs and the level of significance is less satisfactory although the

13 This presumption of stock returns is reasonable, since stock markets in general tend to comove due to the existence of common factors in tranquil periods or contagion effects in crisis periods (Chiang et al., 2007). Similarly, we can model the spillover effect from downside risk.

14 The magnitudes of coefficients are lower from 0.363 to 0.252 for Hong Kong, from 0.339 to 0.314 for Thailand, and from 0.455 to 0.211 for Malaysia.

15 As shown in Table 58.5, this mixed sign issue will be resolved after the long memory phenomenon has been taken care of.