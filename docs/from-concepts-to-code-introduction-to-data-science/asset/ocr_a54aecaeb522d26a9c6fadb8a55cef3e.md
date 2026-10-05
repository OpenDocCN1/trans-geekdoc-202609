data should include observations from a period of heightened risk. For cyclical data, it is important to include at least one cycle in the dataset.

# 17.4 Outcomes Analysis

At this stage, we have reviewed the model components, the data, and the predictors in the model. Next, we will want to understand the utility of the model outputs. The *outcomes analysis* step will compare model outputs to actual outcomes. We might investigate specific cases that arise frequently. Alternatively, we might make predictions on a batch of data and compute a metric, as we did when evaluating regression performance.

The process of *backtesting* is a form of outcomes analysis that compares actual outcomes to model predictions from a sample period not included in the training data. We might use historical data from the same period as the training data to evaluate performance which is sometimes called *out-of-sample testing*. We might use recently collected data to measure model performance for *out-of-sample testing*. Table 17.1 shows out-of-sample test results comprising predictions from model $m_1$ and actual outcomes.

# TABLE 17.1: Out-of-Sample Test Results

| index | prediction_$m_1$ | actual |
|---|---|--|
| 0 | 0.20 | 0.06 |
| 1 | -0.10 | -0.04 |
| 2 | 0.70 | 0.45 |
| 3 | 0.45 | 0.63 |
| 4 | 0.15 | 0.11 |

The metrics we have discussed earlier can be used to understand how the model is performing in aggregate. This may include adjusted R-squared and RMSE for fitting linear regression models. For logistic regression models, precision, recall, and F1 score may be useful. Metrics should also be collected over time for *ongoing model performance monitoring*, which we will discuss shortly. Based on the out-of-sample errors in this case, the RMSE is 0.15. This can be verified by computing the squared errors between each prediction and its associated actual value, computing the average squared error, and taking the square root.