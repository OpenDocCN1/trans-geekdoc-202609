
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_216_0.png)

Figure 7.9 Medium-range forecasts for station NP201. (a) Rainfall used in the water-level predictions; (b) three-year water-level prediction for TDNN model; (c) first 200 days magnified; (d) days 400–600 magnified.

time period of the short-term forecasts as a result of more rainfall forecasted (Fig. 7.9c).

The medium-range water-level forecasts of the LSTM model shows more variability in the predictions (also observed in the short-term forecasts for the LSTM), possibly due to the complexity of that model or to the hyperparameters of the model compared with the TDNN. However, the general trends observed in the predictions of the TDNN model are also seen in the predictions of the LSTM model (Fig. 7.10).

**Table 7.3** Measured and forecasted rainfall and water level.

| Day | Rainfall at t + 6 (mm) — Measured | Rainfall at t + 6 (mm) — Forecasted | Water level at t + 7 (m) — Measured | Water level at t + 7 (m) — Predicted | Peak |
|---:|---:|---:|---:|---:|---:|
| 37 | 0.0 | 0.0 | 1.49 | 1.49 | 1 |
| 38 | *19.6* | 5.3 | *1.63* | 1.51 | |
| 39 | 18.0 | 1.9 | 1.65 | 1.54 | |
| 40 | 0.0 | 0.6 | 1.65 | 1.6 | |
| 76 | 0.0 | 1.1 | 1.33 | 1.36 | 2 |
| 77 | *25.9* | 4.6 | *1.58* | 1.38 | |
| 78 | 4.3 | *19.1* | 1.59 | *1.65* | |
| 79 | 0.0 | 21.4 | 1.58 | 1.53 | |
| 80 | 0.0 | 0.0 | 1.57 | 1.54 | |
| 91 | 0.0 | 0.0 | 1.52 | 1.49 | 3 |
| 92 | *26.7* | *30.0* | *1.66* | *1.60* | |
| 93 | *39.4* | *46.3* | *1.66* | *1.66* | |
| 94 | 0.0 | 13.1 | 1.66 | 1.60 | |

*Note:* Measured and forecasted rainfall and water level corresponding to the peaks in water level for the 7-day prediction. The underlined values show the data points of high rainfall, and the corresponding water-level peaks. The shaded values show forecasted rainfall peaks and the corresponding water-level peaks except for peak 1.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_217_0.png)

**Figure 7.10** Medium-range forecasts for station NP201. (a) Three-year water-level prediction for LSTM model; (b) first 200 days magnified; (c) days 400–600 magnified.

Since the two ML models have different training sets based on the data partitioning, the references made between the two do not represent a true comparison. As the main aim of the research is to compare them with a numerical model and not each other, the references made were for the purpose of discussing the performance of both models and not to determine which ML model is better.

The characteristics observed in the results presented for both the short-term and medium-range water-level forecasts at station NP201 were also observed in the results for the other stations. The performances of these models are presented in Appendix Tables 7.A1 and 7.A2.

## 7.6.4. Comparison of the ML Model With the Numerical Model

The BISECT model (Swain & Lohmann, 2019) simulates surface water on a 10 min time step, so daily average water-level predictions are used for comparison in this study. When comparing the daily water-level prediction from each model, the results are promising as they relate to water-level forecasting in the southern Everglades. The ML models are able to predict peaks and troughs much better than the numerical model (Fig. 7.11). The sections of the BISECT model water-level prediction that correspond to troughs in the graphs of the measured data appear to be flattened. This flattening of the troughs is because only the surface water component of the BISECT model was considered for comparison, because the ML models also are solely based on surface water. Regardless, the peaks are much more accurately predicted by the ML models and would suggest that, were the groundwater component of the BISECT model added, its overall performance would improve; but the ML models may still predict more accurately. The BISECT model can have a bias in water levels, which varies from station to station, such as the low overall mean values seen at station NP201 in Figure 7.11. The causes of some of these biases are unknown, but others are from uncertainties in the numerical grid formulation, where a good model fit at one location can correspond to a poor fit at another location. The ML models represent locations independent of each other, so adjusting for a better fit at one location does not affect other locations. The BISECT model is able to capture the general seasonal variations and fluctuations in water level, however it is less precise than the ML models, due to the properties of the numerical model described earlier, and how its inputs and outputs are processed.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_219_0.png)

**Figure 7.11** A 24 hr water-level forecast comparison of ANN and BISECT model outputs to measured water level at station NP201.

Similar characteristics are observed when comparing the output of the BISECT model to the ML water-level prediction for the remaining four stations investigated. In each case, the ML models outperformed the BISECT model in predicting water level 1 day ahead.

An improvement in water-level forecasting could be of significant importance in the southern Everglades where such a vast water-control system exists. The ML models proved to be better than the BISECT model in predicting water level 1 day ahead for each location investigated and could complement the BISECT model in monitoring and analyzing the region’s hydrology. Applications where water-level forecasts are required could benefit from these more accurate local forecasts, increasing the quality and accuracy of ecological studies and assessments, and aid in the CERP.

## 7.7. Conclusions and Future Directions

The following itemizes conclusions and future directions.

- 1. Machine Learning is a good complement to the conventional numerical models used in the southern Everglades for predicting water levels and thus hydroperiods for water manager and ecologic studies. The accuracy of water-level predictions from both ML models improved when compared with an existing numerical model.

- 2. A rational choice of predictors that affect water level positively contributed to the performance of ML models. Also, the water level inputs are the most influential variables on the predictions.
- 3. Incorporation of weather predictions from numerical models as inputs to ML models improved water-level forecasting, particularly at greater lead times (7 and 10 days). Skill and accuracy of the numerical weather models is a limiting factor in achieving accuracy in water-level forecasts.
- 4. Incorporation of volumetric discharge releases from water-control structures into the ML models (where applicable) had a positive effect on the accuracy of water-level forecasts.

A future focus on improving the accuracy of weather forecast models or selecting weather models that perform well at forecasting rainfall could be beneficial. A local model for south Florida based on the Weather Research and Forecasting (WRF) code (https://www.mmm.ucar.edu/weather-research-and-forecasting-model) could provide some improvement in the accuracy of the rainfall forecasts because this is a mesoscale model and as a result has a higher resolution than the global ECMWF model. Rainfall forecasts from the WRF model could be corrected using gauged data through different methods. Additionally, using future scheduled releases instead of measured ones at each forecast horizon could lead to improvements in system management through better tailoring of these releases based on the predictions. Finally, medium-range forecasts could explore the use of ensemble (committee) models, as were used by Fenicia et al. (2007), Kayastha et al. (2013), and Zhang et al. (2022). Ensemble models can be created by classifying water levels into several classes (e.g., low, medium, and high), training several ML models, each responsible for its own class of data, and then combining them using a dynamic weighting scheme (Zhang et al., 2018; Zhang et al, 2022, equation (6)). Such an approach typically leads to higher performance from a combined ensemble of many ML models with different strengths and weaknesses.

## Disclaimer

Any use of trade, firm, or product names is for descriptive purposes only and does not imply endorsement by the U. S. government.
