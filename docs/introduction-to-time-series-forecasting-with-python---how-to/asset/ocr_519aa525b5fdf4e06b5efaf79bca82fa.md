![](bbox=[0.15, 0.14, 0.85, 0.66])

![](bbox=[0.09, 0.75, 0.9, 0.78])

Undoubtedly, the Box-Cox transform has done something to the time series and may be useful. Before proceeding to test the ARIMA model with the transformed data, we must have a way to reverse the transform in order to convert predictions made with a model trained on the transformed data back into the original scale. The `boxcox()` function used in the example finds an ideal lambda value by optimizing a cost function. The lambda is used in the following