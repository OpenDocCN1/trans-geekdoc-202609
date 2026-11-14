# Electricity Production Prediction by Microsoft Azure

Figure 28. Statistical indicators of the predictive model

| Metric | Value |
| :--- | :--- |
| Mean Absolute Error | 440.350931 |
| Root Mean Squared Error | 525.079805 |
| Relative Absolute Error | 0.44413 |
| Relative Squared Error | 0.191822 |
| Coefficient of Determination | 0.808178 |

![](bbox=[0.532, 0.165, 0.792, 0.365])

Figure 29. Converting a model to a web service

![](bbox=[0.125, 0.436, 0.843, 0.568])

+   - Mean Absolute Error (MAE) – defines the average absolute value of the error between the actual and predicted values.
+   - The Root Mean Square Error (RMSE) is the root mean square error, which takes into account the deviation of each point from the mean multiplied by the number of observations.
+   - Relative Absolute Error (RAE) is the relative absolute error that determines the relative accuracy of the forecast compared to the output.
+   - Relative Squared Error (RSE) is the relative squared error that takes into account the deviation of each point from the mean multiplied by the number of observations.
+   - Coefficient of determination (R-squared) is a coefficient of determination that indicates how well the model explains the variance of the original data. The overall rating for each source of electricity is presented in the Table. 2.

Analyzing the obtained data, the following conclusions can be made. AES has a high coefficient of determination ($R^2$) indicating a high degree of correspondence between actual and predicted values (approximately 95.5%). Low values of MAE and RMSE indicate sufficient accuracy of the model in predicting energy values. TES has a high coefficient of determination and low values of MAE and RMSE, which indicate the high accuracy of the model in predicting energy parameters. Block TES shows good