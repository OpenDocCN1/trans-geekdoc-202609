![](bbox=[0.29335, 0.053579999999999996, 0.70665, 0.39642])

Fig. 5. Comparison of actual and predicted load using (i) RNN without Feature Selection (ii) RNN with RRelief (iii) RNN with MI (iv) RNN with RFE (v) RNN with RMR-RFE.

load using RFE. The comparison illustrates the forecast load is much closer to actual. Fig. (v) proved the strength of proposed method of RNN with RMR-HFS. The forecast load of RNN with RMR-HFS is much closer to actual load compared to all features, RNN with MI, RNN with RFE, and RNN with RFE and RFE.

Fig. (iii) presents the comparison of forecast load of LSTM with feature selection actual load. Fig. (iv) compares the forecast of LSTM that includes feature selection actual. The LSTM-RFS forecast has much deviation from the actual value. The inclusion of feature selection reduces the forecasting performance. Fig. (ii) compares actual and forecast load of LSTM with RFE. It produces better results than LSTM with all features, LSTM with MI filter. Fig. (iii) compares forecast of LSTM with MI filter compared to LSTM without feature selection. Fig. (vi) shows comparison of actual and forecast load of LSTM with RFE.

superiority of each method (MLP, RNN, LSTM) by the RMR-HFS compared to other feature selection (RRelief, MI and RFE). Overall, the LSTM with RMR-HFS achieved better prediction performance to other methods such as MLP, RNN, RNN-HFS, RNN with RRelief, RNN with MI, RNN with RFE, LSTM with RMR-HFS, LSTM with RRelief, and LSTM with MI. As the graph in Fig. (v), the portion of the Fig. (a) is observed with only 5 samples in Fig. (b). The comparison of forecast load of different methods on the training samples and test samples is shown in Fig. (b). It shows that the graph of RMR-LSTM is much closer to actual load compared to others. It shows the superiority performance of the proposed method RMR-LSTM over others.

The performance of the prediction model can also be evaluated in many ways. The MAPE, and RMSE are used as additional evaluation measures for performing forecasting methods. The MAPE and RMSE are calculated as follows:

```
$$MAPE = \frac{100}{n} \sum_{t=1}^{n} \left| \frac{Y_t - F'_t}{Y_t} \right| ; \quad (12)$
```

```
$RMSE = \sqrt{rac{1}{n} \sum_{t=1}^{n} [Y_t - F'_t]^2} ; \quad (13)$
```

where 'n' represents the number of instances, '$Y_t$' represents the actual value for the observation time and '$F'_t$' represents the forecast for the

The comparison of actual and predicted load by all the methods with without feature selection for the example of 200 samples is shown in Fig. (a). The graph for the forecast results shows that LSTM-R-HFS without feature selection. The LSTM with proposed method RMR-HFS dominates others by producing forecast results much closer to actual.