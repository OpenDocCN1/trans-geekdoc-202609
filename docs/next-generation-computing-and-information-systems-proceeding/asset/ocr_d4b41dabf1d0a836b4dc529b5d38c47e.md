FBProphet is harnessed to model the prediction of the NDVI for the collected data. As opposed to time-based dependence, FBProphet considers forecasting to be a curve-fitting problem. The date column is upsampled to daily frequency by interpolating it daily to increase the data size to get more accurate predictions, and the NDVI values have been linearly interpolated to fill in any missing values, Figure 6.

The training data contains all the NDVI values from the beginning of the time series up to the cutoff date, while the testing data contains all the NDVI values from the cutoff date to the end of the time series. The plot in Figure 7 shows the NDVI values over time, with the training data in green and the testing data in blue. The y-axis ranges from -1 to 1, and the x-axis shows the years. The plot demonstrates how the data has been split into training and testing sets based on the cutoff date of 2020-01-01.

![](bbox=[0.22, 0.265, 0.8, 0.435])

Figure 7. Train and test data split.

![](bbox=[0.22, 0.495, 0.8, 0.665])

Figure 8. Forecasting the results on original data.

The FB Prophet model is applied to NDVI data with daily seasonality set to false and frequency for the prediction set to daily. It can be seen from the results that actual NDVI data is infrequent, whereas the model trains based on daily observation. More frequent data is expected to improve the prediction significantly. The MSE of the trained model is **0.0137**, the MAE is **0.100**, the RMSE is **0.11**, and the average score is **0.077**. The shaded region in Figure 8 shows how uncertain the prediction is coming timeline. The wider the shaded region, the more uncertainty there is in the forecast, and the narrow part relatively offers certainty in the prediction. Our approach yields valuable results and can generate a list of potential wastelands targeted for agricultural enhancement. Finding special events that trigger a change in NDVI data, such as natural disasters, drought or forest fire, can be included in the FB Prophet Model for much more robust prediction. The prediction error can be identified and added as a regressor to enhance the model further.