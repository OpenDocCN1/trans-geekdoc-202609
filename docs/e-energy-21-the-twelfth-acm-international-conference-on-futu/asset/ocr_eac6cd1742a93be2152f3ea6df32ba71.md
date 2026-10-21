![](bbox=[0.07, 0.1, 0.96, 0.26])

# Figure 5: Flexibility prediction results using best performing models from Table 2 with user temperature threshold of 0.5°C

![](bbox=[0.08, 0.31, 0.47, 0.42])

# Figure 6: Diagram visualizing MAFE and RMSE correlation of all the trained models during experiments

was used for NIST Net-Zero, NYSERDA S40, and NYSERDA S44 datasets.

For scenario ForcedOn, data for flexibility prediction performance evaluation were also collected from the test set. Records were selected, where heat pump power was above a predefined power threshold for at least 45 minutes from start. The threshold for mode ForcedOn was 1.5kW for NIST Net-Zero dataset, 2.14kW for NYSERDA S44 dataset, and 0.92kW for the NYSERDA S40 dataset.

Flexibility was predicted using FLEX_PREDICT defined in Algorithm 1. Lower and upper bounds T_ind_lower, T_ind_upper were calculated by adding and subtracting an indoor temperature threshold value from the last known indoor temperature to get upper and lower bounds, respectively. 0.5°C was selected as the indoor temperature threshold value. No adjustment for predictive model error was used in initial experiments (ε = 0).

Quantitative flexibility prediction performance. Flexibility prediction using trained predictive models experiments show that HeatFlex is capable of predicting flexibility with a high degree of accuracy. As seen in Figure 5, best performing trained temperature predictive models perform well across all three datasets.

For the NIST Net-Zero dataset, the average MAFE error for scenario Off was 0.1, with underestimated flexibility being the only type of error. For scenario ForcedOn, MAFE was 0.28, with underestimated error MAUFE constituting for over 95% of total error. The best performing model for flexibility prediction was the GRU (c=16, m=16), followed closely by LSTM (c=16, m=16). Notably, both GRU (c=16, m=16) and LSTM (c=16, m=16) had more than 3 times higher RMSE indoor temperature predictive error than the best performing indoor temperature predictive model LSTM (c=32, m=96), which had the worst total MAFE for both modes across all 7 models. This

indicates that temperature predictive model RMSE does not always translate into better flexibility prediction MAFE error.

For NYSERDA S40 dataset, the average MAFE error for scenario Off was 0.8 with overestimated flexibility constituting over 95% of total error. All of the models performed very similarly, predicting flexibility within 5% of the average 0.8. The average MAFE for ForcedOn, excluding the SARIMAX model results, was 0.98. SARIMAX underperformed significantly with MAFE of 2.5. The best performing model for flexibility prediction was the GRU (c=16, m=16).

For NYSERDA S44 dataset, the average MAFE error for scenario Off was 1.1. Similarly to the results on the NYSERDA S40 dataset overestimated flexibility made up over 90% of the total error. For predicting flexibility for ForcedOn, the average error was 1.35, with overestimated flexibility error MAOFE constituting for around 60% of the total error. The best performing model for flexibility prediction was the LSTM (c=16, m=16), which was also the best performing temperature predictive model (as seen in Table 2).

Correlation analysis of predictive model error and predicted flexibility. Trained model flexibility prediction results were also analysed to identify if a numeric relationship exists between indoor temperature predictive model error and predicted flexibility error. Figure 6 visualizes the bivariate correlation between trained model RMSE and the mean MAFE for scenarios Off and ForcedOn. The figure shows that in models of all three datasets there is a positive correlation between RMSE and MAFE. However, the correlation is non-linear and has a lot of outliers, meaning that indoor temperature RMSE is a reasonable metric for estimating flexibility error MAFE, but higher indoor temperature model accuracy does not always translate into more accurate flexibility prediction.

Adjustment for predictive model error results. In HeatFlex, indoor temperature prediction and flexibility prediction is separated, allowing adjusting for trained indoor temperature predictive model error during flexibility prediction. One adjustment strategy is to use the ε adjustment variable in the flexibility prediction algorithm (as defined in Algorithm 1). If ε > 0, it reduces the range between user defined comfort bounds. As seen in Figure 7 the user comfort bound reduction forces the predictive models to underestimate flexibility, reducing MAOFE error at the cost of increasing MAUFE, which might be a preferable trade-off, depending on the use-case. An alternative strategy for adjusting for predictive model error is to widen the user comfort bounds by negotiating with the end-user. It could