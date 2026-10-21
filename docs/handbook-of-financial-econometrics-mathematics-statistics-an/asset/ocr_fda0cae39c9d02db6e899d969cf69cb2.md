# Time-Series Analysis: Components, Models, and Forecasting

a brief outline of the ARIMA modeling procedure is in order. (see Nelson (1973) or Nazem (1988), for details of the ARIMA procedure.)

The ARIMA process uses the following three steps as (1) Identification, (2) Estimation and (3) Forecasting.

The first step is to identify the appropriate model. Identification involves determining the degree of differencing necessary to make the series stationary and to determine the form (ARIMA or ARMA) and order of the process.

After a suitable model is identified, the parameters φ1,…,φp,Θ1,…,Θq, need to be estimated. The final step in the ARIMA process is to use the model for forecasting. Oftentimes the adequacy of the model is checked by using the model to forecast within the sample. This allows a comparison of the forecasted values to the actual values. If the model is determined to be adequate, the model can be used to forecast future values of the series. Further discussion of ARIMA models can be found in Hamilton (1994) and Tsay (2010).



Numerous approaches running from sophisticated multiple-equation regression techniques to rather naïve extrapolations or intuitive estimates are being utilized to produce forecasts. Bessler and Brandt (1979) examined three alternative procedures for forecasting time-dependent quarterly observations on hog, cattle, and broiler prices along with composite forecasts based on various linear combinations of these three procedures. The alternative methods for forecasting these prices are econometric models, time-series (ARIMA), and expert opinion.

The results obtained by Bessler and Brandt for selected performance measures (mean-squared error and turning points) applied to the forecasts of each method over the period 1976 quarter I through 1979 quarter II suggest that no method consistently outperformed or was outperformed by the other two methods. In terms of mean-squared error performance forecasts based on the ARIMA processes are lowest for hog and cattle prices, while the econometric model gives lowest mean-squared error forecasts for broiler prices.

The mean forecast error is determined by taking the average of the difference between the summation of the overpredictions and the summation of the underpredictions. A negative sign would indicate that the average forecast series is above the mean of the actual series; a positive sign suggests an average forecast which is low. The mean absolute forecast error is simply the average of the absolute values of the forecast errors.