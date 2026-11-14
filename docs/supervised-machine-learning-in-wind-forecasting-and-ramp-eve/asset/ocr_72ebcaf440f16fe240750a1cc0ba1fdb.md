![](bbox=[0.14, 0.1, 0.89, 0.28])

Figure 6.10 Flowchart for ARIMA-EMD-based hybrid wind forecasting model.

The steps for determining the intrinsic mode function (IMFs) and residue of a time series are the following:

+   - For a given time-series \(a(t)\), locate local maximum and minimum and interpolate to form \(a_u(t)\) and \(a_l(t)\) as upper and lower envelopes.
+   - Work out the mean of upper and lower envelopes \(a_m(t) = \frac{a_u(t)+a_l(t)}{2}\).
+   - Obtain a detailed component \(a_d(t)\) by subtracting the mean component from the original time series as \(a_d(t) = a(t) - a_m(t)\).
+   - Obtain first IMF and residue if \(a_m(t)\) and \(a_d(t)\) fulfill anyone of the stopping criteria. Stopping criteria: (i) mean envelope developed by maxima and minima should be zero, and (b) number of zero crossings and extrema should differ by one or zero.
+   - Repeat the previous steps until you obtain the first IMF and residue.

Fan et al. [20] discussed an EMD-SVR-based hybrid model for predicting electrical load in Australian markets where particle swarm optimization is used to determine optimal SVR parameters. Results reveal that the model proposed by Fan et al. performs better when compared to benchmark models like PSO-BP and PSO-SVR. In the field of predicting of ship motion and wave height, Duan et al. [21,22] studied an EMD-based autoregressive (AR)-SVR model, where the nonlinearity in ship motion and wave height is captured by an EMD process. The results reveal significant improvement achieved by EMD-AR-SVR model over AR and SVR models. Xiang et al. [23] explored an SVR-ANN model based on empirical mode decomposition for predicting rainfall in China. Three different datasets are taken, and SVR is tested for short-term predictions, whereas ANN is tested for long-term predictions. The results reveal significant improvement in terms of RMSE and MAE for EMD-SVR and EMD-ANN methods when compared to traditional methods. Yu et al. [24] presented a model based on