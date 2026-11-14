

- 3. After standardization, the absolute differences of the corresponding elements of reference sequence and decision sequence are calculated, that is, \(\Delta_{ik} = |x'_{0t} - x'_{ik}|, i = 1, 2, ..., n, k = 1, 2, ..., m\).

- 4. \(\Delta_{\min} = \min(\Delta_{ik})\) and \(\Delta_{\max} = \max(\Delta_{ik})\) are calculated.

- 5. The rational coefficient between the reference sequence \(x'_{0t}\) and decision sequence \(x'_{it}\) are calculated using

```
\(r(x'_{0t}, x'_{it}) = \frac{\Delta_{\min} + \rho \times \Delta_{\max}}{\Delta_{it} + \rho \times \Delta_{\max}},\quad (8.26)\)
```

where \(\rho \in (0, 1)\) is called the distinguish coefficient. Usually, \(\rho = 0.5\) is taken for all the calculations.

- 6. The grey relational degrees

```
\(r(X_0, X_i) = \frac{1}{n} \sum_{t=1}^n r(x'_{0t}, x'_{it}), \quad i = 1, 2, ..., m, \quad (8.27)\)
```

are calculated and ordered in descending order. Then the first \(j\)th inputs are selected to forecast wind speed in the presence of wakes.

In this study, GRA is used to identify the upwind turbines that significantly affect the given downwind turbine. The wake wind speed due to an individual upwind turbine is treated as the decision sequence and freestream wind speed \(u_0\) are treated as the reference sequence \(X_0\). The short-term wind speed forecasting is carried without and without GRA, and the forecasting results in terms of RMSE are compared for the proposed bilateral Gaussian wake model and benchmark models.

## 8.4 Results

This section throws light on the framework for short-term forecasting in the presence of wind wakes for two different wind farm layouts, that is, five-turbine wind farm layout (Fig. 8.4) and 15-turbine wind farm layout (Fig. 8.13). Wind speed data are collected for two data sets, a wind farm WBZ tower Hull, Boston Harbor, Massachusetts, and another one located in Sotavento, Galicia, Spain. Table 8.3 shows the descriptive statistics for the two wind farms with their sampling time.

Fig. 8.10 shows the wind speed time series for the two wind farms WBZ tower Hull and Sotavento, Galicia, Spain. These two datasets D1 (500 data points) and D2 (720 data points) are obtained at every 10 minutes and every hour, respectively, in the period of March 1–30, 2018.

Table 8.3 Descriptive statistics for wind speed for WBZ tower Hull, MA, and Sotavento, Spain.

| Wind Farm | Dataset | Max (m/s) | Min (m/s) | Mean (m/s) | Std Dev |
|---|---|---|---|---|---|
| WBZ tower, MA | D1 | 10.14 | 0.36 | 4.4966 | 2.3143 |
| Sotavento, Spain | D2 | 17.53 | 0.35 | 7.1768 | 2.8009 |

![](img/b53e39e35231af65df8ccaa99eb28bee_172_0.png)

The short-term wind speed forecasting, that is, 10 minutes for D1 and 1 hour for D2, is analyzed on the basis of standard metrics like RMSE, the sum of squared residuals, and the sum of squared deviations of testing samples (SST). Mathematical expressions for these metrics are

```
RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (\hat{X}_i - X_i)^2} \times 100\%, \quad SSR/SST = \frac{\sum_{i=1}^{N} (\hat{X}_i - \bar{X})^2}{\sum_{i=1}^{N} (X_i - \bar{X})^2}, \quad (8.28)
```

where $\hat{X}_i, X_i$, and $\bar{X}$ are the predicted, actual, and mean values of the $N$ testing samples. Lower the RMSE and value better the forecasting model. A high SSR/SST ratio indicates a good agreement between actual and estimated values of testing samples.

### 8.4.1 Forecasting results for five-turbine wind farm layout

The forecasting process involves first calculating the wind speed received by the downwind turbine under wake effect from individual upwind turbines. The wind farm layouts for five-turbine wind farm and 15-turbine farm are selected. In the case of wind farm layout with five turbines, wind farms WT_4 and WT_5 are the downwind turbines. The wake flow speeds for both wind turbines are calculated using Jensen's and Frandsen's models. The turbine parameters for both wind farm layouts are chosen the same for simplicity and are listed in Table 8.1.

Wind turbine WT_4 experiences wake from WT_1 and WT_2, whereas WT_5 experiences wake from WT_1, WT_3, and WT_4. The distance x_{ij} between upwind WT_i and downwind turbines WT_j has already been listed in Section 8.2.4. After calculation of wake flow speed using (8.3) and (8.4), the wake flow speed time series is analyzed for grey correlation analysis by comparing it with a reference sequence X_0 (here the freestream wind speed u_0). The grey correlation degree (GCD) r(u_0, u_{ij}) obtained thereafter is arranged in descending order of its magnitude, and the first jth inputs are selected. In the case of five-turbine layout the GCD was found for wind speed series u_15, u_35, and u_45 to select inputs for forecasting wind speed for turbine WT_5. The GRA results for u_15, u_35, and u_45 are highlighted in Table 8.4.

Table 8.4 Grey correlation degree and its ranking for five-turbine layout for datasets D1 and D2.

| Grey correlation degree | D1 Value | D1 Rank | D2 Value | D2 Rank |
|---|---|---|---|---|
| r(u_0, u_15) | 0.7074 | 3 | 0.5867 | 3 |
| r(u_0, u_35) | 0.8529 | 1 | 0.6748 | 1 |
| r(u_0, u_45) | 0.8234 | 2 | 0.5940 | 2 |

The GCDs in descending order are r(u_0, u_35) > r(u_0, u_45) > r(u_0, u_15), where u_35 and u_45 are the inputs to the SVR model to forecast the wind speed for WT_5. The wind speed for WT_5 is also forecasted without considering GRA by selecting all the wake causing wind turbines as input to the SVR model. The effective wind speed is decomposed into approximate signal (a5) and detail signals (d1, d2, d3, d4, d5) using five-level Daubechies 4 (db4) wavelet transform.

The forecasting is done using SVR model where the data are divided as the training set (first 80%) and testing set (remaining 20%). The SVR model uses the radial basis function (RBF) as a kernel function. The SVR hyperparameters are chosen from the set {2^i, i = -9, -8, ..., 10}. This choice of the search space enables us to determine optimal parameters from a finite set of real numbers and leads to fast computation. We selected the RBF kernel function for SVR forecasting, the bandwidth was chosen as \(\sigma = 2^5\), and the regularization constant \(\gamma\) was taken as \(2^2\) [36].

Table 8.5 Forecasting results for wind turbine \(WT_5\) for datasets D1 and D2.

| Dataset | Metric | Jensen's model without GRA | Jensen's model with GRA |
|---|---|---|---|
| D1 | RMSE (%) | 6.53 | 5.84 |
| | SSR/SST | 1.0897 | 1.0124 |
| D2 | RMSE (%) | 12.93 | 11.86 |
| | SSR/SST | 1.0483 | 1.0488 |
| Frandsen's model | | | |
| | | without GRA | with GRA |
| D1 | RMSE (%) | 3.68 | 3.31 |
| | SSR/SST | 1.0986 | 1.0928 |
| D2 | RMSE (%) | 9.02 | 6.43 |
| | SSR/SST | 1.0552 | 1.0578 |
| Proposed model | | | |
| | | without GRA | with GRA |
| D1 | RMSE (%) | 2.86 | 2.56 |
| | SSR/SST | 1.1087 | 1.1902 |
| D2 | RMSE (%) | 7.33 | 4.91 |
| | SSR/SST | 1.0270 | 1.0020 |

Table 8.5 shows the forecasting results for wind turbine \(WT_5\) based on Jensen’s and Frandsen’s wake models for the two datasets D1 and D2.

The wind forecast accuracy for Frandsen’s model outperforms Jensen’s model. Using our proposed model, short-term wind forecasting is carried out for datasets D1 and D2, and the results are studied with respect to benchmark models. For dataset D1, the RMSE is found to be less than in Jensen’s and Frandsen’s models. For dataset D1, without GRA, the RMSE is 2.86%, and for dataset D2, the RMSE is 7.33%. For dataset D1, the RMSE value without GRA-based Jensen’s model is 6.53%, and based on Frandsen’s model, it is 3.68%. The SSR/SST ratio for Jensen’s model is 1.0897, and using Frandsen’s model, it is 1.0986. By incorporating GRA in our forecasting model, the RMSE for Frandsen’s model is 3.31%, and for Jensen’s model, it is 5.84%. The SSR/SST ratio for Frandsen’s model is found to be better than for Jensen’s model, thus suggesting better wind speed forecasting based on this model. A high SSR/SST ratio implies a good agreement between actual and estimated values.

