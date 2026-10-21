statistic $(d_{\text{EML}}-0)/\sigma_d$. Similarly, we test the estimate of $d_{\text{GPH}}$ and present the results in the column labeled $t_d=1$ for the test statistic $(d_{\text{GPH}}-1)/\sigma_d$, and in the column labeled $t_d=0$ for the test statistic $(d_{\text{GPH}}-0)/\sigma_d$. These estimated statistics indicate that the null hypothesis is consistently rejected at a high level of significance,$^{20}$ suggesting that neither the $I(1)$ nor the $I(0)$ appears to be an appropriate process for dealing with the original VaR series for the markets under investigation. In fact, the fractional integrated process not only provides a more flexible form for dealing with the existence of long memory, but it also helps to mitigate the imbalance problem arising from the risk–return regression setting.

In the parametric estimation, we employ the ARFIMA(1,$d$,0) because it best satisfied the goodness-of-fit model as indicated by the smallest AIC value. The estimated values of $\phi^*_{i,1,\text{EML}}$ from the EML method are reported in Table 58.4. The evidence indicates that $\phi^*_{1,\text{EML}}$ values are mainly positive and significant, showing some sort of risk momentum. The exceptions are the US and Taiwan: the coefficients for these two markets are negative, exhibiting a reversal pattern. On the other hand, the AR(1) coefficients estimated from the GPH method, $\phi^*_{i,1,\text{GPH}}$, are negative, suggesting that the downside risk series reverting to the mean or has a persistent degenerating process. This market behavior is more consistent with the stability condition.

# 58.4.3 Estimates of the adjusted downside risk and return dynamics by a VAR model

One econometric issue that we face in testing the downside risk–return relation is that downside risk entails a long memory property. As a result, the test regression appears to be unbalanced with a stationary return process on the left-hand side and a fractionally integrated process in downside risk on the right-hand side of the test equation. To address this issue, we employ the fractional filter, $(1-L)^d$, and define $\Delta^d=(1-L)^d$, to deal with the long memory inherent in the VaR series.

The VAR system, expressing the joint dynamics of excess returns and the VaR, with a long memory adjustment is expressed as

$$
\begin{bmatrix}
R_{i,t+1}\\
\Delta^d V_{i,t+1}
\end{bmatrix}
=
\begin{bmatrix}
\gamma^*_{ii}\lambda^*_i & \gamma^*_{ii}\phi^*_i\\
\lambda^*_i & \phi^*_i
\end{bmatrix}
\begin{bmatrix}
R_{i,t}\\
\Delta^d V_{i,t}
\end{bmatrix}
+ \mathbf{u}_{i,t+1},
\tag{58.12}
$$