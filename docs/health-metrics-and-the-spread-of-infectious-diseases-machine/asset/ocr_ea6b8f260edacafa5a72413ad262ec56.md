# Measures of Machine Learning Models

The accuracy of predictive models is checked with loss functions, which measure the discrepancy between the predicted outcomes and the actual values. This adjustment of the model learning process is performed through iterative adjustments of the model parameters with the objective to improve the model's performance.

Models are trained to a specific loss function that guides the optimization process and quantifies the model performance.

# 6.4.1.1 Regression Loss Functions

Regression loss functions are for regression tasks where the prediction involves continuous numbers, and include:

+   - Mean Squared Error (MSE): MSE calculates the average of the squares of the errors, i.e., the average squared between the estimated values and the actual value. Its loss function is sensitive to outliers as it weights errors before averaging.

```
MSE = \frac{1}{n} \sum_{i=1}^{n}(\hat{Y}_i - Y_i)^2
```

+   - Mean Absolute Error (MAE): MAE measures the average magnitude of the errors in a set of predictions, without considering their direction (i.e., it averages the differences between predictions and actual outcomes). Unlike MSE, MAE is not overly sensitive to outliers, making it suitable for datasets with anomalies.

```
MAE = \frac{1}{n} \sum_{i=1}^{n} |\hat{Y}_i - Y_i|
```

+   - Mean Squared Logarithmic Error (MSLE): MSLE is used when targeting a regression model to exponential growth. By logging the predictions and actual values, MSLE transforms the target variable to reduce the skew of the distribution, which can lead to more stable predictions across a range of values.

```
MSLE = \frac{1}{n} \sum_{i=1}^{n}(log(\hat{Y}_i + 1) - log(Y_i + 1))
```

# 6.4.1.2 Classification Loss Functions

Classification loss functions are for classification tasks, where the output is categorical, typical loss functions include:

+   - Binary Cross-Entropy: Also known as log, this function measures the performance of a classification model whose output is a probability value between 0 and 1. It is particularly useful for binary classification tasks.

```
L = \frac{1}{m} \sum_{i=1}^{m}(y_i log(\hat{y}_i) + (1-y_i)log(1-\\hat{y}_i))
```

+   - Hinge Loss: Often used with Support Vector Machines (SVMs), hinge evaluates the margin of classification errors, providing a penalty for misclassified points to improve model accuracy.

```
L = max(0, 1 - y * f(x))
```

Choosing the right loss function: The selection of a suitable loss function depends on the specific characteristics of the data and the model application. For instance, predicting