wavelet-LSSVR, wavelet-TSVR, and wavelet-ε-TSVR. The forecasting accuracy is evaluated by computing various performance metrics like root mean squared error (RMSE), mean absolute error (MAE), sum of squared residuals (SSR), sum of squared deviation of testing samples (SST), sum of squared error of testing samples (SSE), index of agreement (IOA), and Theil's U1 and U2 statistics [16]. Mathematically, these metrics are expressed as

```
RMSE = \left[ \frac{1}{n} \sum_{i=1}^{n} (\hat{x}_i - x_i)^2 \right]^{1/2} , \quad \text{MAE} = \left[ \frac{1}{n} \sum_{i=1}^{n} |\hat{x}_i - x_i| \right] , \quad (6.3)
```

```
SSR/SST = \frac{\sum_{i=1}^{n} (\hat{x}_i - \bar{x})^2}{\sum_{i=1}^{n} (x_i - \bar{x})^2}, \quad \text{SSE/SST} = \frac{\sum_{i=1}^{n} (\hat{x}_i - x_i)^2}{\sum_{i=1}^{n} (x_i - \bar{x})^2}, \quad (6.4)
```

```
IOA = 1 - \sum_{i=1}^{n} (\hat{x}_i - x_i)^2 \Big/ \sum_{i=1}^{n} (|\hat{x}_i - \bar{x}| + |x_i + \bar{x}|)^2 ,
```

```
U1 = \sqrt{ \frac{1}{n} \times \sum_{i=1}^{n} (\hat{x}_i - x_i)^2 } \Big/ \left( \sqrt{ \frac{1}{n} \times \sum_{i=1}^{n} x_i^2 } + \sqrt{ \frac{1}{n} \times \sum_{i=1}^{n} \hat{x}_i^2 } \right) ,
```

```
U2 = \sqrt{ \frac{1}{n} \times \sum_{i=1}^{n} \left( (x_{i+1} - \hat{x}_{i+1}) / x_i \right)^2 } \Big/ \sqrt{ \frac{1}{n} \times \sum_{i=1}^{n} \left( (x_{i+1} - \hat{x}_i) / x_i \right)^2 } ,
```

where \(\hat{x}_i, x_i\), and \(\bar{x}\) are the predicted, actual, and mean values of the testing samples. Theil's U1 and U2 statistics are important metrics, often used in finance and banking sector to determine the forecast accuracy and quality. The statistic U1 determines how accurate the forecast is, whereas U2 determines the quality of the forecast. Fig. 6.3 shows the block diagram of forecasting through the hybrid wavelet-SVR method.

# Description of datasets

To test the hybrid wavelet-SVR, wind farm sites from Spain, Western Massachusetts (USA), South Dakota (USA), Victoria (Australia), and India are chosen with their descriptive statistics listed in Table 6.1.

Fig. 6.4 shows the wind speed variations for these wind farm sites:

+   Paxton, MA: The wind site is located in western Massachusetts with 42°18'11.6" and 71°53'50.9" as its coordinates. The wind speed is measured every 10 minutes with cup anemometers installed at a height of 78 m above the ground. The wind speed data ranges from January 1, 2011, to January 7, 2011, 22:30 h.