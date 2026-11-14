

## Figure 6.3 Forecasting using wavelet transform and machine intelligent models.

![](img/b53e39e35231af65df8ccaa99eb28bee_99_0.png)

### Table 6.1 Descriptive statistics for wind speed at various wind farm sites.

| Wind farm (Dataset) | Max (m/sec) | Min (m/sec) | Mean (m/sec) | Std Dev |
|---|---|---|---|---|
| Sotavento, Spain (A) | 13.23 | 0.41 | 4.6072 | 1.9395 |
| Paxton, MA (B) | 14.39 | 0.35 | 6.9209 | 2.3734 |
| Blandford, MA (C) | 13.73 | 0.30 | 6.0553 | 2.1242 |
| Bishop & Clerks, MA (D) | 13.31 | 0.36 | 6.7065 | 2.5923 |
| Beresford, SD (E) | 15.06 | 0.58 | 5.4729 | 2.9828 |
| AGL Macarthur (F) | 9.05 | 1.92 | 6.2926 | 1.5035 |
| Muppandal (G) | 8.48 | 0.71 | 4.8878 | 1.4641 |

### Sotavento, Spain
(Dataset: A)

### Paxton, MA
(Dataset: B)

### Blandford, MA
(Dataset: C)

### Bishop & Clerks, MA
(Dataset: D)

### Beresford, SD
(Dataset: E)

### AGL Macarthur, Victoria
(Dataset: F)

Wind speed (m/sec)

Samples/ 10min

Samples/ hr

Figure 6.4 Wind speed for datasets A through F.

- Sotavento, Spain: The wind farm is located in Sotavento, Galicia, Spain, with latitude 43°21'35.9'' and longitude −7°52'47.9''. The dataset chosen is for the month of October 2017, where the wind speed is measured hourly.

- Blandford, MA: Blandford is situated at 42.223° N and 72.968° E with wind speed recorded at a height of 60 m above the ground with a cup anemometer at every 10 minutes. The wind speed data ranges from January 1, 2011, to January 7, 2011, 22:30 h.

- Bishop & Clerks, MA: Wind monitoring site is located at 41.574° N and 70.249° E with anemometer installed at height of 15 m above ground. The data ranges from January 1, 2011, to January 7, 2011, 22:30 h and is recorded every 10 minutes.

- Beresford, South Dakota: The wind site is located at 43.088° N and 96.786° E and ranges from March 1, 2006, 22:20 h to March 8, 2006, 20:50 h. Wind speed is recorded every 10 minutes at 20 m height.

- AGL Macarthur, Victoria, Australia: This wind farm is located at 38.049° S and 142.190° E with 420 MW installed capacity featuring 140 V112-3.0 Vestas wind turbines. Hourly wind speed data are taken from February 26, 2019, 00:00 h to March 5, 2019, 23:00 h [17].

- Muppandal, Kanyakumari, India: Located in Kanyakumari, Tamil Nadu; it has a capacity of 1500 MW. Wind speed data for the month of January 2019 are recorded at 10 minute intervals [18].

The autocorrelation function (ACF) plots depict the correlation of time-series samples with itself at different lag instants. Mathematically, ACF at lag instant k for a time series St is expressed as

$$r_k = \frac{\sum_{i=1}^{N-k} \left( S_t - \overline{S} \right) \left( S_{t+k} - \overline{S} \right)}{\sum_{i=1}^{N} \left( S_t - \overline{S} \right)^2}.$$ (6.5)

Fig. 6.5 illustrates the periodicity of the wind speed time series for all datasets.

For datasets A to E, we find that lag instants of 1 and 2 are significantly dominant, indicating strong correlation. However, the autocorrelation for dataset F is negative for lag order 7.

## 6.4 Results and discussion

A hybrid model is built on wavelet decomposition technique and a machine intelligent SVR model, where 80% of data are used for training, and

![](img/b53e39e35231af65df8ccaa99eb28bee_102_0.png)

Figure 6.5 Periodicity of wind speed time series for Sotavento, Paxton, Blandford, Bishop & Clerks, Beresford, and AGL Macarthur.

the rest for testing. TSVR and ε-TSVR forecasting models are evaluated vis-a-vis ε-SVR and LS-SVR models. For ε-TSVR, we assume that the regularization factors C1 = C2 and C3 = C4. Similarly for TSVR, we select \( C_1 = C_2 \). Since the regularization parameter sets a soft limit on the tolerance error, selecting an optimal value of \( C \) has significant impact on forecast accuracy. Further, since overfitting during training phase causes low accuracy, regularization becomes an important aspect of machine learning regression.

The kernel function used for building the regression models is the radial basis function (RBF) with bandwidth \( \sigma \): \( k(x, x_i) = \exp \left( - \frac{\|x - x_i\|^2}{2\sigma^2} \right) \). The hyperparameters \( C_1, C_2, C_3, \) and \( C_4 \) along with RBF bandwidth \( \sigma \) are chosen from a set \( 2^i, i = -9, -8, \dots, 9, 10 \). Optimal parameters can be tuned manually or by grid search algorithm. Datasets related to four wind farm sites labeled A, B, C, and D are chosen to test the performance of hybrid forecasting model. Dataset A consists of 720 samples out of which 80% (576) are used for training process and 20% (144) are used for testing. Similarly, for datasets B, C, and D, 800 samples are used for training and 200 for testing.

Tables 6.2 and 6.3 depict various performance indices for wavelet-based hybrid SVR models. For dataset A, \( \varepsilon \)-TSVR and TSVR outperformed \( \varepsilon \)-SVR by 41.95% and 84.25%, respectively, in terms of RMSE. Similarly, for datasets B, C, and D, \( \varepsilon \)-TSVR outperforms \( \varepsilon \)-SVR by 3.537%, 63.03%, and 59.60%, respectively, in terms of RMSE. Among all the models, \( \varepsilon \)-TSVR and TSVR outperform LS-SVR and \( \varepsilon \)-SVR quantitatively in terms of RMSE and MAE for all the datasets. In \( \varepsilon \)-SVR the size of the Lagrangian matrix is large and uses inequality constraints; however, LS-SVR uses equality constraints and is faster in computation.

Further, TSVR is a mixture of \( \varepsilon \)-SVR and LS-SVR and uses two quadratic programming formulations with better generalizing capability. LS-SVR spends the minimum processor time due to a smaller-sized optimization problem. \( \varepsilon \)-TSVR takes less time than classical \( \varepsilon \)-SVR and TSVR, and among the four datasets, B, C, and D take more or less the same computation time for the respective models. The ratios SSR/SST and SSE/SST give an estimate of goodness of fit. The SSR/SST ratio value greater than 1 implies overfitting during training process, which is not desirable during the testing phase. Among all regressors, TSVR obtains optimal SSR/SST and SSE/SST ratios. An optimal SSR/SST ratio is close to 1 but not greater than 1. When overfitting occurs, SSR/SST takes a value greater than 1, which ultimately reduces forecast accuracy. Forecasting is assessed from statistical point of view by determining the index of agreement (IOA) and Theil's U1 and U2 statistics for all the models.

### Table 6.2 Performance metrics of wavelet-ε-SVR, LS-SVR, TSVR, and ε-TSVR.

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

