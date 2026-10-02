
The RMSE is expressed as

RMSE = 1/M sqrt( sum_{m=1}^{M} (p_m^a - p_m^f)^2 )  (9)

The MARNE is the absolute difference between the actual and forecast wind speed, normalized to the maximum wind speed:

MARNE = 1/M sum_{m=1}^{M} |p_m^a - p_m^f| / max(p_m^a) × 100  (10)

As benchmarks for the proposed model test, the individual applications of FFNN and ANFIS are used.

## 3. Simulation Results

### 3.1. Wind Speed Forecasting

Computational intelligence-based systems are a favourable scheme in recent years in various variable predictions, such as electric load, over traditional time series models. However, a careful selection of inputs and a proper training phase are essential for the model’s successful implementation and utilization. The selection of the types of inputs is crucial to the forecasting success. In the present study, various input combinations are examined. The objective is to test computational intelligence-based models for the case of incomplete data. Three models are compared that refer to an FFNN, an ANFIS, and a proposed FFNN-ANFIS. After the decision of the types of inputs, i.e., Case#1–Case#5, the next test is to define the number of inputs. This number refers to the historical values of the used parameters: wind speed, temperature and wind direction. With the application of the Sample Autocorrelation Function (SAF), the historical values are evaluated based on the correlation of the present value. Figure 5 displays the SAF that resembles the minute-ahead wind speed set. Only the first 20 values are displayed. It is shown that the correlation is decreasing progressively when the lagged value becomes more time distant. The same conclusions are drawn from the 10 min ahead set. The first five values are selected as inputs for the models. Also, the corresponding values of temperature and wind direction are proportionally selected.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_23_0.png)

Figure 5. Sample autocorrelation function values of the wind speed data set.

Employing the minute-ahead set and the data set of Case#1, a series of experiments were conducted for the purpose of defining the optimal FFNN and ANFIS structures. The optimal FFNN structure has one hidden layer. The tangent sigmoid function is used both for the hidden and output layers. The number of training epochs is set equal to 100. The optimal number of neurons in the hidden layer is defined also by series of simulations. It differs among the various cases. Thus, a series of FFNN executions took place to track the number of hidden layers that minimize the RMSE indicator.

Concerning the optimal ANFIS topology, the Sugeno inference method is selected together with Gaussian membership functions.

The scores of the forecasting models on the assessment indicators are presented at Tables 1 and 2. Table 1 refers to the 1-min-ahead horizon and Table 2 to the 10-min-ahead horizon. The rows of the Tables correspond to the different cases. According to the results of Table 1, the proposed model outperforms the FFNN and ANFIS in all test cases, highlighting the significance of using combined forecasts. The prediction accuracy improvement that is obtained with the proposed model is more evident in the data sets of Case#3, Case#4, and Case#5. FFNN leads to better results compared to ANFIS in Case#2, Case#3, and Case#5 when using the MAE indicator. Also, the FFNN leads to better results in Case#1 according to the RMSE and MARNE measures. However, it scores in MARNE = 4.2353% in Case#2, a value that is higher than the respective of ANFIS. While in most experiments the FFNN appears more robust, it can be suggested over the ANFIS in the minute-ahead wind speed prediction problem.

### Table 1. Comparison of the forecasting models considering the minute-ahead horizon.

|  | MAE |  |  | RMSE |  |  | MARNE (%) |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  | FFNN | ANFIS | FFNN-ANFIS | FFNN | ANFIS | FFNN-ANFIS | FFNN | ANFIS | FFNN-ANFIS |
| Case#1 | 0.3683 | 0.3675 | 0.3673 | 0.5576 | 0.5578 | 0.5563 | 2.3365 | 2.3311 | 2.3298 |
| Case#2 | 0.3676 | 0.3682 | 0.3664 | 0.7510 | 0.5592 | 0.5551 | 2.5952 | 2.3356 | 2.3242 |
| Case#3 | 0.4123 | 0.4443 | 0.3887 | 0.7237 | 0.9163 | 0.6435 | 2.6153 | 2.8185 | 2.4658 |
| Case#4 | 0.4406 | 0.4210 | 0.4091 | 0.9206 | 0.8044 | 0.7511 | 2.7947 | 2.6703 | 2.5952 |
| Case#5 | 0.1021 | 0.1324 | 0.0812 | 0.1528 | 0.2052 | 0.1301 | 0.6477 | 0.8403 | 0.5601 |

### Table 2. Comparison of the forecasting models considering the 10-min-ahead horizon.

|  | MAE |  |  | RMSE |  |  | MARNE (%) |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  | FFNN | ANFIS | FFNN-ANFIS | FFNN | ANFIS | FFNN-ANFIS | FFNN | ANFIS | FFNN-ANFIS |
| Case#1 | 0.4316 | 0.4296 | 0.4287 | 0.6258 | 0.6265 | 0.6240 | 4.2280 | 4.2088 | 4.2008 |
| Case#2 | 0.4323 | 0.4295 | 0.4292 | 0.6253 | 0.6263 | 0.6239 | 4.2353 | 4.2077 | 4.2054 |
| Case#3 | 0.4706 | 0.4985 | 0.4605 | 0.7569 | 0.9373 | 0.6851 | 4.6104 | 4.8841 | 4.5115 |
| Case#4 | 0.4654 | 0.4936 | 0.4528 | 0.7155 | 0.8719 | 0.6689 | 4.5594 | 4.8363 | 4.4367 |
| Case#5 | 0.1227 | 0.1572 | 0.1101 | 0.1693 | 0.2226 | 0.1556 | 1.077 | 1.5409 | 0.9967 |

Among the types of data inputs, Case#5 leads to considerably lower errors indicating the benefit of transforming the volatile wind data into the wavelet domain. This is evident in all measures and especially in MARNE. Considering the MAE indicator, Case#2 leads to better predictions if the latter is held with FFNN or the hybrid model. On the contrary, the data of Case#1, i.e., using only wind speed values is more suitable for ANFIS. Using wind speed, temperature, and wind direction as inputs, the prediction is less credible. This implies again for FFNN and the proposed model. ANFIS scores MAE = 0.4443 with the data of Case#3. The aforementioned conclusions are identical when the evaluation is held with the RMSE or MARNE. Therefore, by combining wind speed and direction data the forecasting procedure is strengthened. The use of temperature is not recommended for the test set under study. According to the above analysis, the combination of the FFNN and ANFIS that is fed with the wind speed data transformed in the wavelet domain is the recommended model for minute-ahead forecasts under the limitation of many incomplete data entries.

According to the findings presented in Table 2, it is evident that the 10-min-ahead wind speed prediction problem is a more difficult task. A possible reason for this is the decrease that is accomplished between current and past values of the minute time frame measurements. This means that the 10-min data are less correlated since the minute correlation lowers due to the averaging of the one-minute data for the purpose of transforming them in the 10-min intervals. The proposed FFNN-ANFIS model is more accurate than the rest in all types of data sets. Again the 10-min-ahead problem benefits from the implementation of the wavelet transform. The data of Case#5 provide more robust predictions independently of the model used.

A further comparison of the models is held via the AE distribution over time. The MAE indicator receives one value for a specific prediction, for example for a given number of neurons in the hidden layer. It is essential to examine the error distribution over the focusing period. Using the AE indicator, the analysis can be scaled to minutes. This concept strengthens the conclusions drawn from the models comparison. Figure 6 presents the AE distribution per Case. The figure refers to the 1-min-ahead prediction horizon while the forecasting is achieved with the proposed FFNN-ANFIS model. The discrete peaks correspond to large error values, which can be considered as indicators of the model’s poor performance for the specific minute. The data of Case#1–Case#4 lead to some high peaks of the AE shape. These are mainly met in December days. The lowest errors are mostly gathered in September days. As the time horizon progresses, the peaks become more frequent. Hence, extreme weather conditions worsen the credibility of the predictions. Some late autumn and winter wind speeds are difficult to effectively be predicted in the coastal site under study. The mean values of AE are 0.3673, 0.3664, 0.4123, 0.4210, and 0.1021 for Case#1, Case#2, Case#3, Case#4, and Case#5, respectively. Some parallel conclusions with the above results can be made for the 10-min-ahead horizon. The corresponding results are graphically presented in Figure 7. In the 10-min-ahead problem, the implementation of the wavelet transform is more advantageous compared to the minute-ahead case. Case#5 increases the accuracy by a large portion. The mean values of AE are 0.4288, 0.4293, 0.4706, 0.4654, and 0.1227 for Case#1, Case#2, Case#3, Case#4, and Case#5, respectively.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_25_0.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_25_1.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_25_2.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_25_3.png)

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_25_4.png)

Figure 6. Absolute error of the proposed model corresponding at (a) Case#1, (b) Case#2, (c) Case#3, (d) Case#4, and (e) Case#5 of the 1-min-ahead prediction horizon.
