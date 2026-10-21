Equation (114.11) is the Covariance-Time Function (C-T Function) as denoted in Hawawini (1980). The ratio $\frac{\rho_{XY}^{s}+\rho_{XY}^{-s}}{\rho_{XY}}$ is called the $q$-ratio of order $s$. It is the sum of lead ($\rho_{XY}^{s}$) and lag ($\rho_{XY}^{-s}$) intertemporal cross-correlation coefficients for order $s$ in unit (unaggregated) returns divided by the contemporaneous cross-correlation coefficient ($\rho_{XY}$). And we denote this ratio as $q_{XY}^{s}$.

From equations (114.10), (114.11) and definitions of the coefficient of systematic risk, we obtain

```
$$\beta_{a}^{2} = \frac{\text{Cov}(X_{t}, Y_{t})[N + \Gamma_{N}]}{\text{Var}(X_{t})[N + \text{P}_{N}]}$$ $$= \beta_{u}^{2} \times \frac{N + \sum_{s=1}^{N-1} (N - s) q_{XY}^{s}}{N + 2 \sum_{s=1}^{N-1} (N - s) \rho_{X}^{s}}. \tag{114.13}$$
```

Denote the time aggregation factor as $\Phi(N) = \frac{N+\sum_{s=1}^{N-1} (N-s) q_{XY}^{s}}{N+2 \sum_{s=1}^{N-1} (N-s) \rho_{X}^{s}}$. Therefore, the ex ante systematic risk associated with additive rates of return is frequency-dependent. The direction and the magnitude of the time aggregation effect on the estimation of systematic coefficient is then given by the sign and absolute value of the difference between $\Phi(N)$ and 1. It is reasonable to imply that the time aggregation effect is positive (aggregated beta is larger than the unaggregated one) if $\Phi(N)$ is larger than 1. While the effect is believed to be negative if $\Phi(N)$ is smaller than 1. Furthermore, we can speculate that for the variation in time interval, larger difference between the Phi multiplier, $\Phi(N)$, and 1 would indicate bigger gap between aggregated and unaggregated estimations of beta.

In Section 114.3, we will test our result by calculating the $\Phi$'s for each firms and different time frequency and compare it with the actual changing trend of beta.

# 114.2.2 Impacts of time aggregation on beta under multiplicative assumption

Continuing our discussion under multiplicative rates of return assumption with Schwartz and Whitcomb’s (1977) $T$-year market model for any $i$th firm or portfolio. In multiplicative framework, $R_{TMj} = \frac{I_{Tj} - I_{Tj-1}}{I_{Tj-1}}$, the “market” simple rates of return over the $j$th sub-period of length $T$. $R_{Tij} = \frac{P_{Tj} + D_{Tj} - P_{Tj-1}}{P_{Tj-1}}$, the simple rate of return over the $j$th subperiod of length $T$