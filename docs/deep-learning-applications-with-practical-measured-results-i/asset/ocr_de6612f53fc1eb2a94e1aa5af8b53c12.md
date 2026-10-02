to fill in missing values. The wind speed feature is label encoded (integer encoded). We apply the new dataset to every algorithm in later experiments.

# 4.3. Evaluation Criteria

Three evaluation metrics, root mean squared error (RMSE), root relative squared error (RRSE) and empirical correlation coefficient (CORR) for multivariate forecasting, are used and defined as:

RMSE = sqrt( 1/N sum_{i=1}^{N} (y_i^t - \hat{y}_i^t)^2 ), (12)
RRSE = sqrt( sum_{(i,t) in Omega_Test} (Y_{it} - \hat{Y}_{it})^2 ) / sqrt( sum_{(i,t) in Omega_Test} (Y_{it} - mean(Y))^2 ), (13)
CORR = 1/n sum_{i=1}^{n} [ sum_t (Y_{it} - mean(Y_i))(\hat{Y}_{it} - mean(\hat{Y}_i)) / sqrt( sum_t (Y_{it} - mean(Y_i))^2 (\hat{Y}_{it} - mean(\hat{Y}_i))^2 ) ], (14)

where Y, \hat{Y} \in \mathbb{R}^{n \times T} are ground value and system prediction value, respectively, and \Omega_{Test} is the set of time stamps used for testing. For RMSE and RRSE, the lower value is better, while, for CORR, the higher value is better for evaluation.

# 4.4. Walk-Forward Validation

In the test set, the Walk-Forward Validation method is adopted, but the model is not updated. In this case, a model is needed to predict a period of time, and then the actual data of the current period is provided to the model, so that it can be used as the basis for the prediction of subsequent periods. This is not only applicable to the way the model is used in practice, but also conducive to the model using the best available data.

In the experiment, the output length is set to 24. For multi-step prediction problems, we evaluate each prediction time step separately. Table 3 summarizes the actual value and predicted value. Models can be trained and evaluated as follows.

+   Step 1: Starting at the beginning of the test set, the last set of observations in the training set is used as input of the model to predict the next set of data (the first set of true values in the validation set).
Step 2: The model makes a prediction for the next time step.
Step 3: Get real observation and add to history for predicting the next time.
Step 4: The prediction is stored and evaluated against the real observation.
Step 5: Go to step 1.

Table 3. Dataset Statistics, where h is hour, d is day.

| Input (Actual Value) | Output (Predicted Value) |
|---|---|
| Current 24 h | Next, 24 h |
| 1d 1 h-1 d 24 h | 2 d 1 h-2 d 24 h |
| 2d 1 h-1 d 24 h | 3 d 1 h-2 d 24 h |
| ... | ... |

# 4.5. Experimental Details

To be more specific, most models chose input length from {24,72,168}, and the batch size is set to 100. The mean squared error is the default loss function for forecasting tasks. Adam [35] is adopted as optimization strategy, with an initial learning rate set to 0.001. In addition, the learning rate is reduced