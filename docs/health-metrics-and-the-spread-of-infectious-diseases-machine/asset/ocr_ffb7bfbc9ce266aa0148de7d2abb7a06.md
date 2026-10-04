92 Introduction to Machine Learning

precise values are crucial and the data range is wide, MSE might be appropriate. Conversely, for models where the prediction scale is logarithmic or the data contains many outliers, MSLE or MAE could be more effective.

The choice of a loss function is not merely a technical decision but a strategic one, affecting how a model learns and performs on unseen data. Each function has its strengths and trade-offs, making it vital for practitioners to understand their implications thoroughly. Understanding these measures and how they influence model training and predictions can greatly enhance the effectiveness of machine learning applications.

# 6.4.2 Evaluation Metrics

While losses are used during the training process to guide the optimization of the model parameters, evaluation metrics measure how well the model's predictions align with the actual outcomes, providing a signal to adjust the model.

# 6.4.2.1 Regression Evaluation Metrics

For regression tasks, the following metrics are commonly used to assess the model's predictive performance:

+   Root Mean Squared Error (RMSE): A measure of the average deviation between predicted and actual values, calculated as the square root of the squared differences between predicted and actual values. It is commonly used in regression tasks to assess the model's predictive accuracy.

> $RMSE = \sqrt{rac{1}{n}\sum_{i=1}^{n}(Y_i - \hat{Y}_i)^2} \quad (6.21)$

+   R-squared (R2): A statistical measure of how well the model fits the data, indicating the proportion of variance in the dependent variable is explained by the independent variables. It ranges from 0 to 1, with higher values indicating a better fit.

> $R^2 = 1 - \frac{SS_{residual}}{SS_{total}} \quad (6.22)$

+   Adjusted R-squared: A modified version of R-squared that adjusts for the number of predictors in the model, providing a more accurate measure of the model's goodness of fit. It penalises the addition of unnecessary predictors that do not improve the model's performance.

> $AdjustedR^2 = 1 - \frac{(1-R^2)(n-1)}{n-k-1} \quad (6.23)$

# 6.4.2.2 Classification Evaluation Metrics

For classification tasks, the following metrics are commonly used to evaluate the model's performance:

+   Accuracy: The proportion of correctly classified instances out of the total instances in the dataset. It is a simple and intuitive measure of a model's performance, but it may not be suitable for imbalanced datasets.

> $Accuracy = \frac{TP + TN}{TP + TN + FP + FN} \quad (6.24)$