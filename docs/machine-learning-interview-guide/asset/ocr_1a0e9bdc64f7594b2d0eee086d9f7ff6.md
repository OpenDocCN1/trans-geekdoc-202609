useful for modeling time series with short-term shock characteristics.

# Question 4: What is the I component of ARIMA?

Answer: In the case of ARIMA, integrated (I) means differencing as a way of making a time series stationary (A stationary time series is one whose properties, like mean and variance, do not change over time).

In ARIMA models, the d term depicts the level of integration where differencing is done on the time series data until a stationary data is arrived at. These differencing eliminate trends and seasonality from the series. It makes the process of modeling the series by means of AR and moving average compositions easier.

Thus, the integrated part of ARIMA identifies the number of diffs required to make the time series stationary before the application of the auto-regressive and moving average parts.

# Question 5: How does differencing help in making a time series stationary?

Answer: Differencing is among the most frequently applied procedures for making a time series stationary. For a time series, stationarity is defined by the fact that the statistics, such as the mean value, variance, and auto covariance, do not vary with time.

If a time series is non-stationary, there are signs of trends or seasonality showing in the graph. For instance, to counter the previously mentioned patterns, differencing is used to subtract the previous observation from the current one. Differencing removes trends and seasonality, making the data fluctuate around a constant mean.

Due to the removal of the trend and seasonality information, differencing renders the data stationary,