# Table 38.6: Estimated parameters of the t-Gumbel copula in modeling the dependence between credit risk, market risk and operational risk.

|  | Component copulas | Weight parameters | Association parameters |
|---|---|---|---|
| t-Gumbel copula | t copula | $w_t = 0.42$ | $R = \begin{pmatrix}1 & -0.71 & 0.49 \\ 1 & -0.17 \\ 1\end{pmatrix}$, $\nu = 12$ |
|  | Gumbel copula | $w_{Gu} = 0.58$ | $\alpha = 1.24$ |

Note: See Section 38.3.2 for the definitions of these parameters in the t-Gumbel copula. Specifically, −0.71 is the correlation coefficient of credit risk and market risk, 0.49 is the coefficient of credit risk and operational risk, and −0.17 is the coefficient of market risk and operational risk.

# Table 38.7: Total risk of Chinese banks by t-Gumbel copula.

| Confidence level | 90% | 95% | 99% | 99.9% | 99.97% |
|---|---|---|---|---|---|
| Total risk | 0.80 | 0.99 | 1.64 | 3.65 | 5.77 |

Note: Unit of total risk is %, with the denominator of risk-weighted asset.

to derive one annual loss. Repeat this process 10,000,000 times, and finally the annual VaR can be calculated based on 10,000,000 simulated annual losses. In this way, the total risk over a one year time horizon at different confidence levels is shown in Table 38.7.

As the confidence level increases, VaR of the total risk becomes larger, ranging from 0.80% to 5.77%. Generally, the choice of confidence level depends on the bank’s target credit ratings. BCBS recommends that the economic capital requirement should be set to protect against losses over one year at 99.9% level, which is roughly equivalent to the default risk of an A-rated corporate bond (BCBS, 2006). The China Banking Regulatory Commission (CBRC) also stipulates 99.9% as the standard confidence level. Therefore, at this confidence level, the total risk of Chinese listed banks is 3.65%, which provides a reference for economic capital allocation.

# 38.4.3 Results analysis

To examine whether the constructed mixture copulas can satisfactorily capture the dependence structure between the three types of risks, the performance of these mixture copulas is compared with seven other major risk integration approaches comprehensively.