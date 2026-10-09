```
ARIMA(2, 0, 0) RMSE=7.697
ARIMA(2, 1, 0) RMSE=7.713
ARIMA(2, 1, 1) RMSE=7.417
ARIMA(2, 2, 0) RMSE=10.373
ARIMA(4, 0, 0) RMSE=7.693
ARIMA(4, 1, 0) RMSE=7.578
ARIMA(4, 1, 1) RMSE=7.474
ARIMA(4, 2, 0) RMSE=8.956
ARIMA(6, 0, 0) RMSE=7.666
ARIMA(6, 1, 0) RMSE=7.293
ARIMA(6, 1, 1) RMSE=7.553
ARIMA(6, 2, 0) RMSE=8.352
ARIMA(8, 0, 0) RMSE=7.549
ARIMA(8, 1, 0) RMSE=7.549
ARIMA(8, 2, 0) RMSE=8.126
ARIMA(8, 2, 1) RMSE=7.608
ARIMA(10, 0, 0) RMSE=7.581
ARIMA(10, 1, 0) RMSE=7.574
ARIMA(10, 2, 0) RMSE=8.093
ARIMA(10, 2, 1) RMSE=7.608
ARIMA(10, 2, 2) RMSE=7.636
Best ARIMA(6, 1, 0) RMSE=7.293
```

Listing 26.12: Example output of grid searching ARIMA configuration on the Daily Female Births dataset.

# ## 26.6 Extensions

The grid search method used in this tutorial is simple and can easily be extended. This section lists some ideas to extend the approach you may wish to explore.

+   * **Seed Grid.** The classical diagnostic tools of ACF and PACF plots can still be used with the results used to seed the grid of ARIMA parameters to search.
* **Alternate Measures.** The search seeks to optimize the out-of-sample root mean squared error. This could be changed to another out-of-sample statistic, an in-sample statistic, such as AIC or BIC, or some combination of the two. You can choose a metric that is most meaningful on your project.
* **Residual Diagnostics.** Statistics can automatically be calculated on the residual forecast errors to provide an additional indication of the quality of the fit. Examples include statistical tests for whether the distribution of residuals is Gaussian and whether there is an autocorrelation in the residuals.
* **Update Model.** The ARIMA model is created from scratch for each one-step forecast. With careful inspection of the API, it may be possible to update the internal data of the model with new observations rather than recreating it from scratch.
* **Preconditions.** The ARIMA model can make assumptions about the time series dataset, such as normality and stationarity. These could be checked and a warning raised for a given of a dataset prior to a given model being trained.