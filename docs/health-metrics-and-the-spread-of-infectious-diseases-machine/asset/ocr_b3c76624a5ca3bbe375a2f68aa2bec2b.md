# Predictive Modelling and Beyond

```
components(dcmp) |> fabletools::autoplot()

components(dcmp) |>
as_tssible() |>
autoplot(value) +
ge_line(aes(y = trend),
  linetype="dashed") +-
labs(title = "Trend line of SDI in France")
```

STL decomposition
value = trend + remainder

![](bbox=[0.118, 0.235, 0.89, 0.403])

(a) Components of SDI in France

(b) Trend line of SDI in France

9.5 Autocorrelation of SDI in France

# 9.4.2 Autocorrelation and Stationarity

Autocorrelation is very important in time series analysis as it explains whether past values influence values. If a variable today is similar to what was yesterday or last month, we say it has autocorrelation at lag 1 or k.

```
$r_k = \frac{\sum_{t=k+1}^{T}(y_t - \bar{y})(y_{t-k} - \bar{y})}{\sum_{t=1}^{T}(y_t - \bar{y})^2}$
```

where:

+   * $r_k$ is the autocorrelation coefficient at lag $k,
* $y_t$ is the value of the time series at time $t$,
* $ar{y}$ is the mean of the series,
* $T$ is the total number of time points.

Time series exhibit no autocorrelation, or no predictable relationship between observations at different time points, are referred to as white noise series, where each value is essentially a random draw from the same distribution, with constant mean and variance, with no pattern recognition.

On the contrary, the presence of autocorrelation, or statistically significant correlations between current and past values, indicates the absence of white noise. This means the time series has temporal structure, which can be modelled for prediction. For example, positive autocorrelation suggests that (high) or (low) values tend to be followed by similarly high (or (low)) values, while negative autocorrelation implies an alternating pattern.