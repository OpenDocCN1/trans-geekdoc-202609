![](bbox=[0.07, 0.06, 0.93, 0.36])

Figure 6. MAE, RMSE, and r² values of different ML algorithms with (a) strategy I, (b) strategy II, and (c) strategy III for η′ prediction. (d–f) Performance of the best regression models on the training and testing data set in each strategy.

| model | r² | MAE | RMSE |
|---|---|---|---|
| \multicolumn{4}{c}{Strategy I} |
| linear | 0.560 | 0.122 | 0.155 |
| SVR | 0.731 | 0.093 | 0.121 |
| GBR | 0.822 | 0.050 | 0.099 |
| RF | 0.851 | 0.049 | 0.090 |
| XGB | 0.862 | 0.048 | 0.087 |
| LGBM | 0.872 | 0.050 | 0.084 |
| \multicolumn{4}{c}{Strategy II} |
| linear | 0.712 | 0.096 | 0.126 |
| SVR | 0.805 | 0.079 | 0.103 |
| GBR | 0.859 | 0.049 | 0.088 |
| RF | 0.874 | 0.045 | 0.083 |
| XGB | 0.881 | 0.046 | 0.081 |
| LGBM | 0.881 | 0.045 | 0.081 |
| \multicolumn{4}{c}{Strategy III} |
| linear | 0.760 | 0.089 | 0.115 |
| SVR | 0.798 | 0.078 | 0.105 |
| GBR | 0.860 | 0.050 | 0.087 |
| RF | 0.894 | 0.042 | 0.076 |
| XGB | 0.879 | 0.045 | 0.081 |
| LGBM | 0.901 | 0.038 | 0.074 |

![](bbox=[0.52, 0.41, 0.93, 0.6])

Figure 7. Ten-fold cross-validation RMSE of the LGBM model based on all possible subsets containing 1–10 features.

From Figure 8a, it can be observed that the two most important features affecting the W_rec′ prediction model are E and ΔP, both of which are important parameters for measuring the energy storage performance of capacitors. As their values increase, a larger W_rec′ is obtained, which is consistent with our physical knowledge. Figure 8c,e visualizes the tendency of E values and ΔP values, as well as the corresponding SHAP values. It can be observed that as E values increase, ΔP values also increase, and similarly, the SHAP values of E also increase. When E values exceed approximately 120, the corresponding SHAP values are all positive, indicating that higher applied

electric fields are more conducive to achieving higher energy storage densities. When ΔP values exceed 15, most of the corresponding SHAP values are also positive, suggesting that larger ΔP values are more likely to result in higher energy storage densities.

From Figure 8b, it can be observed that the two most important features affecting the η′ prediction model are DV and R. To better visualize the relationship between features and SHAP values, a SHAP dependence plot of DV and R for the LGBM η′ model was generated, as shown in Figure 8d. It can be observed that when the value of DV exceeds 1.81, it tends to drive the energy storage efficiency toward lower values. This implies that to obtain BaTiO3-based ceramic materials with high energy storage efficiency, it is necessary to control the value of the valence electron distance to be less than 1.81. As can be seen from Figure 8f, when the value of the ionic radius exceeds 2.55, it will also exert a negative influence on the η′ model prediction.

Experimental Validation. To verify that the model can be accurately applied in actual experiments, a series of xBaTiO3-