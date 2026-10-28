+   - Detection of residual patterns: Serial correlation of the model residuals is checked to ensure that there is no further pattern or information left in the model. Generally high autocorrelation of residuals may also point towards the lack of an appropriate model.
+   
+   - Signal vs. noise differentiation: It helps in decomposing signals that are important for analysis from noise since temporarily shifted data is almost identical to original data. This means that if there are peaks in the autocorrelation function, then the system shows some level of systematic correlation and if the oscillations are random, then the autocorrelation should be low or even non-existent.

In summary, we can identify that autocorrelation is the starting point of time series analysis. It assists in identifying temporal coverages, decides the most appropriate models to use, check for stationarity and determines if the chosen predictive models incorporate the right temporal associations in the results. Knowledge of autocorrelation is crucial when analyzing and predicting the future trends for time series data.

# Question 9: How can you transform non-stationary time series data into a stationary form?

Answer: General decomposition states that irrespective of the type of time series data collected, non-stationary data need to be transformed into stationary form before use in various time series analysis.

Here are some common methods for achieving stationarity:

+   - Differencing: Determine the value of the first-order difference between two successive series. This can be done once (first-order differencing) or repeatedly until the series becomes stationary, abbreviated as D1 for first-order differencing if carried out once.