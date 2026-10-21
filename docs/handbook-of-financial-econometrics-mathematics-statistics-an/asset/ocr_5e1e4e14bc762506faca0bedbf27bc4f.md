where α(τ) = α + F_ε^{-1}(τ). We then rewrite the regression as

$$y_t = \theta' Z_t + \varepsilon_t \tag{92.8}$$

and

$$Q_{y_t}(\tau \mid \Omega_t) = \theta(\tau)' Z_t, \tag{92.9}$$

as the τth conditional quantile function of y_t, where Koenker and Bassett (1978) has ρ_τ = μ(τ − I(μ < 0)); thus, the τth quantile regression delivers the least absolute deviation (LAD) estimate of the co-integration model.

# ## 92.3 Empirical Results and Analysis

# ### 92.3.1 Unit root test for the spot gold price and futures gold price

We first followed the unit roots of variables suggested by the ADF (1979), Phillips-Perron (PP, 1998), and Kwiatkowski et al. (KPSS, 1992) tests. Table 92.2 shows that gold spot prices and four futures prices are integrated in the order 1(I(1)). These indicate that all contracts, including spot and gold futures of 1-, 2-, 3-, and 6-month, have unit roots. This also means that

Table 92.2: Results of the unit root tests.

| Variables | ADF-test Level | ADF-test 1st diff | PP-test Level | PP-test 1st diff | KPSS-test Level | KPSS-test 1st diff |
|---|---|---|---|---|---|---|
| Spot price | 1.024 | -63.887** | 1.035 | -63.885** | 6.682 | 0.602** |
| 1 month future gold price | 1.020 | -62.179** | 0.998 | -62.175** | 6.678 | 0.579** |
| 2 months future gold price | 1.011 | -62.014** | 0.991 | -62.006** | 6.677 | 0.583** |
| 3 months future gold price | 1.001 | -62.149** | 0.986 | -62.142** | 6.675 | 0.581** |
| 6 months future gold price | 1.085 | -62.017** | 1.053 | -62.016** | 6.671 | 0.598** |

Note: ** means significance <0.01.