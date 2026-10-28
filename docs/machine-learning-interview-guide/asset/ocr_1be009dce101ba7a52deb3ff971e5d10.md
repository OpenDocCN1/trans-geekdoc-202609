followed by steps allowing for the description of the trend in an explicit manner.

+   - **Statistical tests**: To check for the trend, one must conduct statistical tests for trend, such as the Mann-Kendall test or the augmented Dickey-Fuller test. These tests aid in determining whether the obtained results are statistically significant concerning the trends identified in indicators.
+   - **ML models**: Use ML models especially for techniques that work for time series data to capture more detailed patterns on the data.

The process of decomposing and forecasting trends of time series data is a combination of graphical analysis, statistical procedures, and modeling strategies. Therefore, a method that corresponds to the nature of the trend, linear or non-linear has to be selected. It is also important to appraise and remodel from time to time as the nature of the data changes.

# Question 12: Can ARIMA be used for multivariate time series forecasting?

**Answer**: ARIMA is primarily designed for univariate time series forecasting, where only one variable is observed and predicted over time. However, when dealing with multivariate time series forecasting, advanced variants of the ARIMA model can be applied. Nevertheless, the advanced variants of the ARIMA model include the **Vector Autoregressive Integrated Moving Average (VARIMA)** and the **Vector Autoregressive Moving Average with exogenous variables (VARMAX)** for multivariate time series forecasting.

VARIMA models generalize ARIMA and involve the use of lagged values of all variables in the model extending to the other related time series variables. This allows one to