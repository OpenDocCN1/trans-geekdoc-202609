| Metric | Formula |
|---|---|
| \( R^2 \) | \( \frac{\sum_{i=1}^n (\hat{x}_i - \bar{x})^2}{\sum_{i=1}^n (x_i - \bar{x})^2} \) |
| RMSE | \( \left( \frac{1}{n} \sum_{i=1}^n (\hat{x}_i - x_i)^2 \right)^{1/2} \) |
| MAE | \( \frac{1}{n} \sum_{i=1}^n |\hat{x}_i - x_i| \) |
| MAPE | \( \frac{1}{n} \sum_{i=1}^n |\hat{x}_i - x_i| \times 100\% \) |

where \( \xi_t \) is an independent process with mean zero, and \( \phi = [\phi_1, ..., \phi_p] \) and \( \theta = [\theta_1, ..., \theta_q] \) are the parameters of the AR and MA processes, respectively. ARMA models can be studied in a much more simplified manner by using the lag operator \( L \). When applied \( k \) times, the lag operator moves index of the variable back by \( k \) times. Given a quantity \( \gamma \), the lag operation for \( k \) times yields \( L^k(\gamma) = y_{t-k} \). In general, an ARMA process can be mathematically expressed as

```
ARMA : \( \phi L(y_t) = \theta L(\xi_t) \),
AR : \( \phi L(y_t) = \xi_t \),
MA : \( y_t = \theta L(\xi_t) \).
```

As an example, we consider forecasting wind speed based on time-series modeling. The wind speed data of 2 months (Jan 1, 2017–March 31, 2017) for Praia Formosa, Brazil, is taken. The autocorrelation of the wind speed time series is calculated, and the orders \( p \) and \( q \) for ARMA model are set. To assess the model accuracy, error metrics like root mean squared error (RMSE), mean absolute error (MAE), mean absolute percentage error (MAPE), and \( R^2 \) are calculated and listed in Table 3.1.

The \( \mathcal{L}_2 \) norm or Euclidean distance of residuals is also used for investigating the forecast accuracy, which is expressed as

```
\( \| \mathcal{L} \|_2 = \sqrt{\sum_{i=1}^n (x_i - \hat{x}_i)^2} \)
```

where \( x_i \) is the actual value, and \( \hat{x}_i \) is the predicted value for \( n \) samples.