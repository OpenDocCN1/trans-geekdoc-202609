# Table 6.10: Analysis of the prediction capabilities of various models.

|  | RAF | RWF | RAWP | RIF |
|---|---|---|---|---|
| The intervention analysis integrated into ARIMA-GARCH model | 0.444 | 0.111 | 4.000 | 0.444 |
| ECM | 0.444 | 0.111 | 4.000 | 0.444 |
| The intervention analysis integrated into transfer function model | 0.777 | 0 | ∞ | 0.222 |
| Simple average combination forecasting model | 0.444 | 0.111 | 4.000 | 0.444 |
| Minimum error combination forecasting model | 0.777 | 0 | ∞ | 0.222 |

Notes: (1) RAF is the ratio of accurate forecasts. RWF is ratio of worst forecasts. RAWF is ratio of accurate to worst forecasts. RIF is ratio of inaccurate forecasts. (2) Good predictive quality requires higher RAF & RAWP and lower RWF & RIF. Data Source: Compiled by the researchers.

# Table 6.11: Analysis of the prediction capabilities of various terms — the intervention analysis integrated into transfer function model.

|  | RAF | RWF | RAWP | RIF | MAPE | RMSE |
|---|---|---|---|---|---|---|
| Predict 3 month | 1 | 0 | ∞ | 0 | 1.092% | 1.253 |
| Predict 6 month | 1 | 0 | ∞ | 0 | 1.112% | 1.333 |
| Predict 9 month | 0.777 | 0 | ∞ | 0.222 | 1.248% | 1.455 |
| Predict 12 month | 0.777 | 0 | ∞ | 0.222 | 1.334% | 1.795 |

Data Source: Compiled by the researchers.

# Table 6.12: Analysis of the prediction capabilities of various terms — minimum error combination forecasting model.

|  | RAF | RWF | RAWP | RIF | MAPE | RMSE |
|---|---|---|---|---|---|---|
| Predict 3 month | 1 | 0 | ∞ | 0 | 0.886% | 1.026 |
| Predict 6 month | 1 | 0 | ∞ | 0 | 1.008% | 1.219 |
| Predict 9 month | 0.777 | 0 | ∞ | 0.222 | 1.114% | 1.316 |
| Predict 12 month | 0.777 | 0 | ∞ | 0.222 | 1.241% | 1.527 |

Data Source: Compiled by the researchers.

maintain robustness. According to the results, the use of outlier detection could effectively pinpoint the external effects in time-series; and the intervention method could increase the fitness of the in-sample model; moreover, that could increase out-of-sample predictive accuracy and maintain robustness as well.