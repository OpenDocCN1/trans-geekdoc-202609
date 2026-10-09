![](bbox=[0.15, 0.13, 0.8, 0.48])

Figure 32.4: Box and whisker plots of the training set for the Champagne Sales dataset.

The observations suggest perhaps some growth trend over the years and outliers that may be a part of the seasonal cycle. This yearly view of the data is an interesting avenue and could be pursued further by looking at summary statistics from year-to-year and changes in summary stats from year-to-year.

# # 32.6 ARIMA Models

In this section, we will develop Autoregressive Integrated Moving Average, or ARIMA, models for the problem. We will approach modeling by both manual and automatic configuration of the ARIMA model. This will be followed by a third step of investigating the residual errors of the chosen model. As such, this section is broken down into 3 steps:

+   1. Manually Configure the ARIMA.
2. Automatically Configure the ARIMA.
3. Review Residual Errors.