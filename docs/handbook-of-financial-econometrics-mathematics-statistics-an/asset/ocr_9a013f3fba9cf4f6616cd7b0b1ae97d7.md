# Table 58.3: Estimates from a bivariate VAR system with leverage effect.

|  | γ_ii (1) | γ_ij(j=US) (2) | γ_ij(j=China) (3) | λ_i (4) | λ_j=US (5) | λ_j=China (6) |
|---|---|---|---|---|---|---|
| Korea | -0.299* (-2.07) | -1.394 (-1.45) | 1.156*** (3.40) | 0.257* (1.71) | 0.026*** (3.26) | -0.094*** (-9.80) |
| Hong Kong | 0.252* (1.80) | -0.698* (-1.79) | 0.214* (1.78) | -0.099** (-1.99) | 0.068*** (5.68) | -0.038*** (-2.71) |
| Indonesia | -0.580* (-1.84) | -1.394 (-1.47) | 0.713** (2.12) | 0.126 (1.15) | 0.040*** (5.00) | -0.048*** (-4.92) |
| Thailand | 0.314*** (2.22) | -0.219* (-1.70) | 0.382 (1.32) | -0.040** (-2.61) | -0.033*** (-6.88) | -0.048*** (-4.31) |
| Singapore | 0.125 (0.78) | -0.212 (-1.31) | 0.558*** (2.63) | -0.015 (-1.05) | -0.049*** (-7.20) | -0.079*** (-5.00) |
| Taiwan | -0.788 (-1.14) | -0.201 (-1.55) | 0.527* (1.81) | 0.004 (0.30) | -0.015*** (-3.06) | -0.012 (-1.09) |
| Malaysia | 0.211 (1.25) | -0.571* (-1.73) | -0.061 (-0.61) | -0.053*** (-3.44) | 0.008 (0.63) | 0.009 (0.54) |

Notes: This table reports the estimated results of equations (58.8) and (58.9).

```
[R_{i,t+1}; V_{i,t+1}] = [[γ_ii λ_i, γ_ii φ_i]; [λ_i, φ_i]] [R_{i,t}; V_{i,t}] + u_{i,t+1} (58.8)
```

```
[R_{i,t+1}; V_{j,t+1}] = [[γ_ij λ_j ρ_ij, γ_ij φ_j]; [λ_j ρ_ij, φ_j]] [R_{i,t}; V_{j,t}] + u_{ij,t+1} (58.9)
```

where λ_i indicates the financial leverage effect from the local country, λ_j indicates the financial leverage effect from the local market to the US or China, γ_ii is the downside risk aversion parameter, and γ_ij is the cross-country downside risk aversion parameter. The numbers in parentheses are t statistics. *, ** and *** indicate that the coefficient is significantly different from zero at the 10%, 5% and 1% levels, respectively. The weekly dataset covers seven Asian markets: S. Korea, Hong Kong, Indonesia, Thailand, Singapore, Taiwan and Malaysia. Both the United States and China are viewed as the dominating countries. The sample spans the period 1997–2011, with 783 weekly observations for each variable.

cross-market coefficients of γ_ij with Chinese market are positive and statistically significant. The evidence suggests that the incorporation of the leverage effect does not seem to help in resolving the issue of the inconclusive signs of γ_ii on the risk–return relation. Rather, we suspect that the indeterminacy of the estimated parameters between stock returns and downside risk due to the interaction of the leverage effect and the risk feedback effect may complicate the parametric relations. Essentially, it may originate from the failure of the model of the long memory of the VaR series. In the following section, we shall turn to the investigation of the long memory effect.