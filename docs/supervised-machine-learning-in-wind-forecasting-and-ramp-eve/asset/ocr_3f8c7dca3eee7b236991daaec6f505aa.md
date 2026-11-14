# Table 8.6 Grey correlation degree and ranking for 12-turbine layout for D1 and D2.

| Grey correlation degree | D1 Value | D1 Rank | D2 Value | D2 Rank |
|---|---|---|---|---|
| r(u0, u3,12) | 0.8218 | 3 | 0.6644 | 5 |
| r(u0, u4,12) | 0.8529 | 1 | 0.6748 | 4 |
| r(u0, u5,12) | 0.7809 | 5 | 0.7065 | 3 |
| r(u0, u7,12) | 0.7228 | 6 | 0.8246 | 1 |
| r(u0, u9,12) | 0.8234 | 2 | 0.5940 | 6 |
| r(u0, u10,12) | 0.7917 | 4 | 0.7260 | 2 |

# Table 8.7 Forecasting results for wind turbine WT12 for datasets D1 and D2.

Dataset | Metric | Jensen's model without GRA | Jensen's model with GRA
|---|---|---|---|
D1 | RMSE (%) | 5.86 | 4.66
 | SSR/SST | 0.9866 | 1.0224
D2 | RMSE (%) | 8.06 | 6.86
 | SSR/SST | 1.0519 | 1.2934

Frandsen's model
without GRA | with GRA
D1 | RMSE (%) | 4.78 | 4.38
 | SSR/SST | 1.0933 | 1.0818
D2 | RMSE (%) | 6.38 | 6.21
 | SSR/SST | 1.0297 | 1.3603

Proposed model
without GRA | with GRA
D1 | RMSE (%) | 4.82 | 2.56
 | SSR/SST | 1.0599 | 1.0190
D2 | RMSE (%) | 5.52 | 4.72
 | SSR/SST | 1.0363 | 1.0150

used. For dataset D1, the inputs to the SVR model are wavelet decomposition signals of effective wind speed u12off (a5; d1, d2, d3, d4, and d5) and wind speed series uij due to upwind turbines WTi, i = 3, 4, 5, 7, 9, 10. The short-term wind speed is forecasted for WT12 once without GRA and once with GRA, that is, only selected inputs (u5,12; u7,12; u10,12) based on their rankings are used to forecast the effective input at WT12. Table 8.7 shows the performance metrics based on Jensen’s, Frandsen’s, and the proposed model.