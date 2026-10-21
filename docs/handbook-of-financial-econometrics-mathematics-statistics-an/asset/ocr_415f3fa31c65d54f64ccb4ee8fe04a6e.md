estimate the MEG coefficient. A numerical method can then be used to estimate the hedge ratio that maximizes the objective function given by equation (11.10).

# 11.3.5 *Estimation of generalized semivariance (GSV)-based hedge ratios*

The GSV can be estimated from the sample by using the following sample counterpart:

$$V_{\delta,\alpha}^{\mathrm{sample}}(R_h)=\frac{1}{N}\sum_{i=1}^{N}(\delta-R_{h,i})^{\alpha}U(\delta-R_{h,i}), \qquad (11.30)$$

where

$$U(\delta-R_{h,i})=\begin{cases}1 & \text{for } \delta\ge R_{h,i},\\0 & \text{for } \delta<R_{h,i}.
\end{cases}$$

Similar to the MEG technique, the optimal GSV hedge ratio can be estimated by choosing the hedge ratio that minimizes the sample GSV, $V_{\delta,\alpha}^{\mathrm{sample}}(R_h)$. Numerical methods can be used to search for the optimum hedge ratio. Similarly, the M-GSV hedge ratio can be obtained by minimizing the mean-risk function given by equation (11.12), where the expected return on the hedged portfolio is replaced by the sample average return and the GSV is replaced by the sample GSV.

One can instead use the kernel density estimation method suggested by Lien and Tse (2000) to estimate the GSV, and numerical techniques can be used to find the optimum GSV hedge ratio. Instead of using the kernel method, one can also employ the conditional heteroscedastic model to estimate the density function. This is the method used by Lien and Tse (1998).

# 11.4 Hedging Horizon, Maturity of Futures Contract, Data Frequency, and Hedging Effectiveness

In this section, we discuss the relationship among the length of hedging horizon (hedging period), maturity of futures contracts, data frequency (e.g., daily, weekly, monthly, or quarterly), and hedging effectiveness.

Since there are many futures contracts (with different maturities) that can be used in hedging, the question is whether the MV hedge ratio depends on the time to maturity of the futures contract being used for hedging.