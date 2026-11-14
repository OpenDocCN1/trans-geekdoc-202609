# Table 5.3 Performance metrics for gradient boosted machines model.

| RMSE | MSE | SSR/SST | SSE/SST | U1 | U2 |
|---|---|---|---|---|---|
| 25.0592 | 627.55 | 0.8084 | 0.0795 | 0.0975 | 0.4546 |

# Table 5.4 Performance metrics for GBM model for crude oil prediction.

| Model | RMSE | SSE/SST | MSE | U1 | SSR/SST | U2 |
|---|---|---|---|---|---|---|
| GBM | 0.6486 | 0.0085 | 0.4207 | 0.0076 | 0.8420 | 0.6925 |
| Persistence | 1.1553 | 0.1340 | 1.3347 | 0.0254 | 1.1625 | 1.1235 |

the dataset into training (800) and testing (606) sets. An optimal number of trees is determined through cross validation.

Table 5.3 depicts the performance metrics for rainfall prediction. Results reveal that GBM outperforms RF model in terms of RMSE and SSR/SST. Both RF and GBM model give similar predictive performance and can be used for time series with highly nonlinear nature.

# 5.2.2 Crude oil price prediction: a case study

Prices of crude oil change everyday and are often studied from prediction point of view by various oil companies. Common prediction models may fail to deliver accurate values for oil prices under which a company may suffer losses in a long run. Similar to RF model, the predictions are performed for GBM model with predictors as detail and approximate signals of the price time series. The time series is divided into training and testing sets in a similar fashion like that in the random forest model case.

In terms of RMSE as depicted by Table 5.4, GBM is an inferior model compared to RF model and gives a low SSR/SST value. However, the prediction performance is found to be much better than that of the persistence algorithm, where the problem of overfitting prevails as indicated by a high SSR/SST value.

Fig. 5.8 illustrates the prediction time series for crude oil price and is tested against the persistence model.

This chapter highlights decision tree ensemble-based regression models for time-series prediction. Random forest and gradient boosted machines use the principle of bagging and boosting, respectively, to arrive at the best prediction. The use of decision tree models for regression is best suited