**Table 7.10 Log energy entropy for ramp event signals.**

| Dataset | Model | WT | EMD |
|---|---|---|---|
| a | TSVR | 6.6094 × 10³ | 5.6985 × 10³ |
| | RFR | 6.2866 × 10³ | 5.5948 × 10³ |
| | GBM | 6.7926 × 10³ | 5.5943 × 10³ |
| Aa | TSVR | 1.7259 × 10⁴ | 1.5646 × 10⁴ |
| | RFR | 2.0676 × 10⁴ | 1.2297 × 10⁴ |
| | GBM | 2.0776 × 10⁴ | 1.4621 × 10⁴ |

Such signal decompositions are used to assess the randomness in the ramp event signal by calculating the log energy entropy of predicted ramp signals based on TSVR, RFR, and GBM as shown in Table 7.10.

For a particular prediction model, the log energy entropy based on WT is greater than that of EMD, suggesting higher-order randomness in the ramp event signal. As far as uncertainties are concerned, the decomposition-based prediction models yield better ramp prediction than single methods as listed in the literature. In the current work, wind power ramp events are studied for six onshore and six offshore wind farm sites. Wind speed data for March 2019 with 10-min sampling interval are collected. The available data are transformed to a hub height of 90 m for all the datasets. The threshold value is chosen as 10% of nominal wind power, based on which the ramp event points are assessed for absolute error. The machine learning-based prediction models are compared with the benchmark persistence model. TSVR-based model gives minimum error for both ramp-up and ramp-down events. The coefficient of performance (R²) for RFR and GBM in case of offshore wind farm datasets is found to be close to 1.00, which indicates a good agreement between predicted and actual values. Further, it is observed that the error in predicting ramp-down event is greater than in ramp-up event.

Overall, machine learning-based prediction models are good approximators for analyzing short-term wind ramps. Randomness in wind power ramp series in case of TSVR, RFR, and GBM is evaluated using signal decomposition techniques, and with RFR the randomness is minimal. Machine intelligent models like TSVR and GBM affirm a stable grid operation in the presence of large ramp-up and ramp-down events. Among the regressors, ε-TSVR outperforms TSVR, LS-SVR, and ε-SVR in terms of absolute error. Ramp events are analyzed for different hub heights, and