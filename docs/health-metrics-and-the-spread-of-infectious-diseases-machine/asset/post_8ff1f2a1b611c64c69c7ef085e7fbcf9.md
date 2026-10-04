
# Predictive Modelling and Beyond

```r
components(dcmp) |> fabletools::autoplot()

components(dcmp) |>
as_tssible() |>
autoplot(value) +
ge_line(aes(y = trend),
  linetype="dashed") +
labs(title = "Trend line of SDI in France")
```

STL decomposition
value = trend + remainder

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_162_0.png)

(a) Components of SDI in France

(b) Trend line of SDI in France

## 9.5 Autocorrelation of SDI in France

### 9.4.2 Autocorrelation and Stationarity

Autocorrelation is very important in time series analysis as it explains whether past values influence values. If a variable today is similar to what was yesterday or last month, we say it has autocorrelation at lag 1 or k.

```r
$r_k = \frac{\sum_{t=k+1}^{T}(y_t - \bar{y})(y_{t-k} - \bar{y})}{\sum_{t=1}^{T}(y_t - \bar{y})^2}$
```

where:

- $r_k$ is the autocorrelation coefficient at lag $k$,
- $y_t$ is the value of the time series at time $t$,
- $\bar{y}$ is the mean of the series,
- $T$ is the total number of time points.

Time series that exhibit no autocorrelation, or no predictable relationship between observations at different time points, are referred to as white noise series, where each value is essentially a random draw from the same distribution, with constant mean and variance, with no pattern recognition.

On the contrary, the presence of autocorrelation, or statistically significant correlations between current and past values, indicates the absence of white noise. This means the time series has temporal structure, which can be modelled for prediction. For example, positive autocorrelation suggests that (high) or (low) values tend to be followed by similarly high (or (low)) values, while negative autocorrelation implies an alternating pattern.

## Example: SDI Time Series Analysis

```r
r_k = {> 0 positive autocorrelation (e.g., trends)
< 0 negative autocorrelation (e.g., alternating pattern)
≈ 0 no autocorrelation (white noise)} (9.9)
```

To check for autocorrelation in our data, we can use the ACF() function from the {feasts} package:

```r
sdi_fr_ts |
ACF(value) |
autoplot()
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_163_0.png)

**Figure 9.6** Autocorrelation Function of SDI in France. The blue dashed lines represent the 95% confidence interval for the null hypothesis: There is no autocorrelation at lag k.

The output clearly shows that our data displays autocorrelation, this validates the use of time series models such as ARIMA, which rely on autocorrelated structure.

To assess whether the series is **stationary**, we use a specific test, the KPSS test or **Augmented Dickey-Feller test**. If this test, generally defined as unit root test, indicates non-stationarity, we can apply a **first-order difference** to remove the trend and convert it into a stationary series.

To apply the KPSS test we use the features() function from {feetools} package and specify the test to use:unitroot_kpss. The {urca} might be needed for this task; if needed `install.packages("urca")`.

```r
sdi_fr_ts |
features(value,
```

> ³-KPSS Test, October 12, 2023, https://en.wikipedia.org/w/index.php?title=KPSS_test&oldid=117971435.

## 146 Predictive Modelling and Beyond

```r
features = unitroot_kpss
#> A tibble: 1 x 2
#> kpss_stat kpss_pvalue
#> <dbl> <dbl>
#> 1 1.09 0.01
```

A p-value = 0.01, which is less than 0.05, indicates strong evidence against the null hypothesis of stationarity.

In summary, the presence of autocorrelation combined with the non-stationarity result from the KPSS test suggests that the series has a trend or random component, and is not stationary.

> A fundamental concept in time series analysis is stationarity. A time series is said to be stationary when its statistical properties do not change over time. This means the mean, variance, and autocorrelation structure remain constant throughout the series. On the other hand, a non-stationary time series exhibits properties that change over time—for example, a long-term trend, changing volatility, or evolving seasonal patterns.

In this case we apply the first-order differencing (differences = 1) to the data before applying models that assume stationarity, such as ARIMA.

$y_t = y_t - y_{t-1}$ (9.10)

Differencing transforms the series by subtracting each observation from its previous value, removing trends and stabilizing the mean over time. This transformation often makes the mean and variance more stable, and is essential because non-stationary time series can lead to unreliable or misleading model results.

```r
# Apply first-order differencing to remove trend
sdi_fr_diff <- sdi_fr_ts | 
mutate(diff_value = difference(value, differences = 1))
sdi_fr_diff | head()
#> A tibble: 6 x 4 [1]
#> location year value diff_value
#> <chr> <dbl> <dbl>
#> 1 France 1990 0.738 NA
#> 2 France 1991 0.743 0.00500
#> 3 France 1992 0.725 0.00700
#> 4 France 1993 0.755 0.00500
#> 5 France 1994 0.759 0.00400
#> 6 France 1995 0.763 0.00400
```

```r
sdi_fr_diff | 
ggplot(aes(x = year, y = diff_value)) +
geom_line() + 
labs(title = "First-order Differenced SDI (France)", nx = "Year", y = "Differenced SDI")
```

# First-order Differenced SDI (France)

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_165_0.png)

**Figure 9.7** First-order Differenced SDI (France)

## 9.4.3 Partial Autocorrelations

The **Partial Autocorrelation Function (PACF)** removes the effects of intermediate lags. It is a measure of the direct relationship between a time series and its lagged values. The PACF allows for a more specific identification of how many lags to include in the AR part of the ARIMA model. The number of autoregressive (AR) terms (p) is determined by the number of significant lags in the PACF plot.

```r
sdi_fr_ts |>
PACF(value) |
autoplot()

sdi_fr_ts |>
gg_tsdisplay(y = value, plot_type = "partial")
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_165_1.png)

**(a)** PACF   **(b)** gg_tsdisplay

**Figure 9.8** Partial Autocorrelations of SDI in France

In this plot we can see that the PACF shows a significant spike at 1, indicating that the first lag is important for predicting the current value. The subsequent lags are not significant, suggesting that only the first lag should be included in the ARIMA model.

## 9.4.4 ARIMA model

The ARIMA model forecasts time series values based on past observations.

- In time series analysis, the terms forecast and predict are sometimes used interchangeably, but there's a subtle distinction:
- Forecast typically refers to estimating future values based on a model trained on historical data.
- Predict can more generally refer to estimating outcomes, including within-sample estimates (e.g., fitting values during model training).

Auto-ARIMA model is used to establish the best fit by combining autoregressive, moving average, and differencing components. However, careful analysis of stationarity, autocorrelations, and the residuals are required to fine-tune the model and improve forecasting accuracy.

The ARIMA(value) function automatically selects the p, d, and q values.
In general, the ARIMA model is defined as

> ARIMA(p, d, q) = AR(p) + I(d) + MA(q)                          (9.11)

where:

- AR(p) is the autoregressive part of the model, which uses past values of the time series to predict future values.
- I(d) is the integrated part of the model, which represents the differencing of the time series to make it stationary.
- MA(q) is the moving average part of the model, which uses past forecast errors to predict future values.

The ARIMA() function from the {fable} package automatically selects the appropriate degree of differencing to achieve stationarity and fits the ARIMA model accordingly. The report() function provides a summary of the fitted model, including parameter estimates and diagnostic statistics.

```r
fit <- sdi_fr_ts |
model(ARIMA(value))

fit |> report(
# Series: value
# Model: ARIMA(1,1,0) w/ drift
#
# Coefficients:
#       ar1      constant
#       0.5971    0.0013
#       s.e.     0.1562    0.0002
#>
```
