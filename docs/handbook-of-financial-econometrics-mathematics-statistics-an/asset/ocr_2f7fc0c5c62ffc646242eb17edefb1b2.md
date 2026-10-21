# Table 70.6: Out-of-sample analysis.

| Parameter | Bank of America | Wells Fargo | J.P. Morgan | CitiGroup | AIG |
|---|---|---|---|---|---|
| **VG-NGARCH:** | | | | | |
| β₀ | 0.00001 | 0.0098 | 0.0023 | 0.0049 | −0.0111 |
| β | 1.1626 | 1.0759 | 1.1666 | 1.2582 | 1.6120 |
| R² | 0.6575 | 0.6148 | 0.6407 | 0.6482 | 0.7006 |
| F | 963.8306 | 801.2075 | 895.3023 | 924.9720 | 1174.7 |
| p-value | 0 | 0 | 0 | 0 | 0 |
| **GARJI:** | | | | | |
| β₀ | −0.0392 | −0.0206 | −0.0221 | −0.0333 | −0.0659 |
| β | 1.3681 | 1.2472 | 1.3284 | 1.4201 | 1.5145 |
| R² | 0.6500 | 0.5727 | 0.6317 | 0.6470 | 0.6631 |
| F | 932.1904 | 672.7951 | 861.0316 | 919.9395 | 988.0498 |
| p-value | 0 | 0 | 0 | 0 | 0 |

# 70.4.3 Forecasting the probability of large price movements

The performance of the VG-NGARCH model can be examined based on its ability to predict large price movements due to extreme events. Define a large price movement event as the log-return exceeds 0.05 or is less than −0.05. From (70.8)–(70.12), the ex ante probability of large price movements is given by

P(|Y_t| >0.05 | F_{t-1}) = ∫_0^∞ [1 − Φ((0.05 − (m + φ_t + θg))/(σ√g))] h(g)dg + ∫_0^∞ Φ((−0.05 − (m + φ_t + θg))/(σ√g)) h(g)dg, (70.21)

where h(g) denotes the probability density function of a gamma distribution with shape and scale parameters ν_t and 1, respectively. For the GARJI model, the ex post probability of at least one jump occurring is given by

P(n_t ≥ 1 | F_{t-1}) = 1 − P(n_t = 1 | F_{t-1}), (70.22)

where the ex post probability distribution P(n_t | F_{t-1}) is given in (70.6). Compared to the ex ante probability of large price movements by the VG-NGARCH model in (7.21), the ex post probabilities of at least one jump by the GARJI model in (7.22) are more susceptible to moderate price movements. For example, the VG-NGARCH identifies June 16, 2006 with log-returns −0.0103, −0.0040, −0.0109, −0.0067, and −0.0027 as large price