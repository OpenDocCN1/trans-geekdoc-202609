| Onshore wind farm | Site coordinates | Mean | SD |
| :--- | :--- | :--- | :--- |
| Amakhala Emoyeni, SA (a) | −32.17° N, 25.95° E | 6.264 | 3.198 |
| Clyde, Scotland (b) | 55.46° N, 03.65° W | 3.829 | 1.626 |
| Gansu, China (c) | 40.20° N, 96.90° E | 4.000 | 2.477 |
| McCain Foods, UK (d) | 52.56° N, 0.172° W | 6.491 | 3.519 |
| Shepherds Flat, USA (e) | 45.70° N, 120.06° W | 6.074 | 2.618 |
| Akhfenir, Morocco (f) | 27.95° N, 12.00° W | 3.096 | 1.505 |
| Offshore wind farm | Site coordinates | Mean | SD |
| Amrumbank, Germany (Aa) | 54.50° N, 7.80° E | 11.176 | 4.962 |
| Anholt, Denmark (Bb) | 56.60° N, 11.21° E | 8.999 | 3.537 |
| Gemini, Netherlands (Cc) | 54.03° N, 5.96° E | 7.577 | 4.174 |
| HornsRev 2, Denmark (Dd) | 55.60° N, 7.59° E | 11.183 | 4.546 |
| Veja Mate, Germany (Ee) | 54.31° N, 5.87° E | 11.490 | 4.685 |
| Walney, UK (Ff) | 54.04° N, 5.92° W | 11.342 | 5.015 |

For onshore wind farm sites, the datasets labeled are **a**, **b**, **c**, **d**, **e**, and **f**. For dataset **a**, GBM outperforms all the prediction models in terms of RMSE and NMSE. For predicting ramp-up and ramp-down events, TSVR outperforms GBM and RFR. In terms of $R^2$, TSVR gives the best fit close to 1.00, whereas $\varepsilon$-SVR gives a value greater than 1.00 causing over-fitting. The over-fitting in prediction is avoided by using RFR and GBM. Figs. 7.10–7.12 illustrate scatter plots for the different onshore datasets.

Similarly, for offshore wind farm datasets (**Aa**, **Bb**, **Cc**, **Dd**, **Ee** & **Ff**), Figs. 7.13–7.15 illustrate scatter plots.

TSVR outperforms all the models in terms of RMSE and NMSE for predicting wind speed, whereas for predicting ramp events, TSVR gives the best result in terms of $R^2$. Further, since the datasets are large sized, TSVR, $\varepsilon$-TSVR, RFR, and GBM take less computation time than conventional $\varepsilon$-SVR. The detailed performance metrics for onshore wind farm sites are depicted in Tables 7.4, 7.5, and 7.6.

Among different regressors, TSVR gives a minimum prediction error for ramp-up and ramp-down events for datasets **c** and **d**. In terms of RMSE, for dataset **c**, TSVR outperforms $\varepsilon$-TSVR, LSSVR, RFR, and GBM by 85%, 84.2%, 98.3%, and 97.6%, respectively.

From the performance metrics of the onshore wind sites we can observe that the decision tree ensemble methods like random forest and gradient boosted machines result in significantly lower RMSE and NMSE than supervised machine learning models. For example, for dataset **a**, $\varepsilon$-SVR