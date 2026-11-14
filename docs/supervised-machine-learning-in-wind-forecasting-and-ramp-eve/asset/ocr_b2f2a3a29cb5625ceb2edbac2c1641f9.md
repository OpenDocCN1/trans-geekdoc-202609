# Table 6.2 Performance metrics of wavelet-ε-SVR, LS-SVR, TSVR, and ε-TSVR.

| Dataset | Model | RMSE | IOA | MAE | U1 | SSR/SST | U2 | SSE/SST | CPU time |
|---|---|---|---|---|---|---|---|---|---|
| A | ε-SVR | 0.1423 | 1.0000 | 12.254 | 0.0233 | 0.9434 | 1.1281 | 0.064 | 5.7964 |
| | LS-SVR | 0.1097 | 1.0000 | 8.4668 | 0.0028 | 0.9417 | 0.9665 | 0.0038 | 0.5924 |
| | TSVR | 0.0224 | 1.0000 | 1.4877 | 0.0011 | 0.9821 | 0.9496 | 0.0008 | 3.1864 |
| | ε-TSVR | 0.0823 | 1.0000 | 7.6699 | 0.00116 | 0.9694 | 0.0150 | 0.0021 | 2.4421 |
| | Persistence | 0.7241 | 0.9991 | 71.41 | 0.0913 | 1.0192 | 1.1331 | 0.2925 | 0.3024 |
| B | ε-SVR | 0.0424 | 1.0000 | 6.8172 | 0.0138 | 1.0055 | 0.0645 | 0.0003 | 11.244 |
| | LS-SVR | 0.0329 | 1.0000 | 4.6550 | 0.00340 | 0.9862 | 0.0466 | 0.0001 | 0.8165 |
| | TSVR | 0.0148 | 1.0000 | 2.0444 | 0.0008 | 0.9965 | 0.0072 | 0.00003 | 6.2343 |
| | ε-TSVR | 0.0409 | 1.0000 | 6.8764 | 0.0021 | 0.9884 | 0.0130 | 0.0003 | 3.6897 |
| | Persistence | 0.7825 | 0.9998 | 66.31 | 0.0731 | 1.0197 | 1.0000 | 0.1437 | 0.2560 |

From Table 6.2 we observe that ε-TSVR and TSVR models outperform ε-SVR, LS-SVR, and persistence models in terms of Theil's U1 and U2 statistics, thereby indicating that the accuracy of the two models is superior to the rest. Fig. 6.6 shows the forecasting results of the four variants of SVR for four wind farm sites. The forecast accuracy of ε-TSVR and TSVR is further tested using the Diebold–Mariano (DM) test. The DM statistic test assumes a null hypothesis wherein two forecasting models have similar accuracy [19].

Consider an actual time series $y_t$ and forecasted time series $\hat{y}_{1t}$ and $\hat{y}_{2t}$. The error between actual and forecasted time series is $e_{it} = \hat{y}_{it} - y_t$. Mathematically, the DM test can be expressed as

$H_0: e_{1t} - e_{2t} = 0, \quad H_1: e_{1t} - e_{2t} \neq 0, \quad \forall t;$ (6.6)

$H_0$ and $H_1$ represent the null and alternative hypotheses.