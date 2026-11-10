
In our corn and fertilizer example, this means finding the line that best predicts corn yield for different fertilizer levels.

This "best fit" line is the most reliable for understanding the relationship and making predictions.

By applying `OLS`, we ensure the model is both mathematically sound and practically useful for analyzing relationships in data. This explanation keeps the fertilizer and corn yield context, ensuring the concept is relatable and grounded in a real-world example.

# 17.3 Multiple Linear Regression

Multiple Linear Regression is a statistical technique used to model the relationship between one dependent variable and two or more independent variables. It extends simple linear regression by incorporating multiple predictors, enabling a deeper understanding of how various factors contribute to the outcome. The goal is to determine the linear equation that best fits the data, represented as ![](image_rsrcF2U.jpg) = `b0 + b1X1 + b2X2 + … + bnXn`

where ![](image_rsrcF2U.jpg) is the dependent variable, `b0` is the y-intercept, `b1`, `b2`, … , `bn` are coefficients for the independent variables `X1`, `X2`, ... , `Xn` respectively. Multiple Linear Regression is widely used in fields such as economics, biology, marketing, and engineering to predict outcomes and analyze the influence of various factors.

The equation for multiple linear regression: ![](image_rsrcF2U.jpg) = `b0 + b1X1 + b2X2 + … + bnXn`

As you can see, it’s quite similar to the equation for simple linear regression. In this case, we still have the dependent variable (the outcome we want to predict), the y-intercept (or constant), and a slope coefficient paired with an independent variable. The difference is that with multiple linear regression, we can include several independent variables, each with its own slope coefficient.

![A diagram of multiple linear regression equation AI-generated content may be incorrect.](image_rsrcF2Y.jpg)

In essence, the number of slope coefficients corresponds to the number of independent variables we include in the model.

![A diagram of a corn plant AI-generated content may be incorrect.](image_rsrcF2Z.jpg)

Now, let’s move on to an example using corn harvesting. Imagine you want to predict how much corn you can harvest (in tons) based on the amount of nitrogen fertilizer you use (in kilograms), the average temperature during the growing season (in degrees Celsius), and the total rainfall (in millimeters). In this case, the dependent variable is the yield of corn (in tons), and the independent variables are fertilizer usage, average temperature, and rainfall.

A possible equation for this scenario might look something like this:

`Corn Yield (tons) = 5 + 4.5 × Fertilizer (kg) − 0.3 × Temperature (°C) + 0.06 × Rainfall (mm)`

Here’s what the terms mean:

`5` (y-intercept): Even if no fertilizer is used, the baseline yield might be 5 tons due to natural soil fertility and growing conditions.

`4.5` (coefficient for fertilizer): For every kilogram of nitrogen fertilizer used, the corn yield increases by 4.5 tons. This reflects the significant impact fertilizer has on yield.

`-0.3` (coefficient for temperature): As the average temperature increases by one degree Celsius, the yield decreases by 0.3 tons. This suggests that higher temperatures slightly hinder corn growth.

`0.06` (coefficient for rainfall): For every millimeter of rainfall, the yield increases by 0.06 tons, indicating that rainfall positively contributes to crop yield.

(Note: this is just for an example to understand multiple linear regression – not a real-life example.)

# 17.4 Evaluating Regression Models (MAE, MSE, R²)

Evaluating the performance of regression models is essential to understanding how effectively the model fits the data and predicts outcomes. Three widely used metrics for regression evaluation are `MAE`, `MSE`, and `R² Score`. Each of these metrics offers unique insights into the model's accuracy and its ability to generalize to unseen data.

### Mean Absolute Error (MAE)

`MAE` measures the average magnitude of errors in a set of predictions, without considering their direction. It represents the average absolute difference between predicted values (`y_pred`) and actual values (`y_true`).

Formula:

![](image_rsrcF30.jpg)

Characteristics: Easy to interpret since it measures error in the same units as the target variable. Treats all errors equally, regardless of their magnitude.

Example:

If a house price prediction model has `MAE` = 10,000, it means, on average, the model's predictions are off by $10,000.

### Mean Squared Error (MSE)

`MSE` measures the average squared difference between predicted and actual values. By squaring the errors, it penalizes larger errors more heavily, making it sensitive to outliers.

Formula:

![](image_rsrcF31.jpg)

Characteristics:
- More sensitive to outliers compared to `MAE` because of the squaring effect.
- Provides an overall measure of error in squared units of the target variable.

Example:

If `MSE` = 1,000,000, the model's predictions deviate from the actual values by about the square root of 1,000,000, or $1,000, on average.

### R² Score (Coefficient of Determination)

`R²` measures the proportion of the variance in the dependent variable (`y`) that is predictable from the independent variables (`X`). It quantifies how well the regression model explains the variation in the data.

![A black and white image of a mathematical equation AI-generated content may be incorrect.](image_rsrcF32.jpg)

Characteristics:
- `R²` ranges from 0 to 1:
  - `R² = 1`: Perfect fit.
  - `R² = 0`: The model does not explain any variance.
  - Negative values indicate the model performs worse than a horizontal line (mean of `y`).

Example:

An `R²` value of 0.85 means 85% of the variance in the target variable is explained by the model, while 15% remains unexplained.

### Comparison of Metrics

| Metric | Sensitivity to Outliers | Units | Interpretability |
| --- | --- | --- | --- |
| `MAE` | Low | Same as target variable | Easy to understand and interpret |
| `MSE` | High | Squared units of target | Highlights large errors |
| `R² Score` | N/A | Unitless (0 to 1 scale) | Measures explained variance |
|  |  |  |  |

### Python Example

Here's how to calculate these metrics using `scikit-learn`:

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

# True and predicted values
y_true = [300000, 400000, 500000, 600000]
y_pred = [310000, 390000, 490000, 610000]

# Calculate metrics
mae = mean_absolute_error(y_true, y_pred)
mse = mean_squared_error(y_true, y_pred)
r2 = r2_score(y_true, y_pred)

print(f"Mean Absolute Error (MAE): {mae}")
print(f"Mean Squared Error (MSE): {mse}")
print(f"R² Score: {r2}")
```

Output:

Mean Absolute Error (MAE): 10000.0

Mean Squared Error (MSE): 100000000.0

R² Score: 0.99

### Conclusion

- `MAE` is useful for understanding the average error in real-world terms.
- `MSE` emphasizes larger errors, making it ideal for models where avoiding significant deviations is important.
- `R² Score` provides an overall sense of how well the model fits the data.

Choosing the right metric depends on the specific problem and the importance of handling outliers in your data.

# 17.5 Hands-On: Building and Evaluating Regression Models

In this hands-on tutorial, we will walk through the process of building and evaluating a regression model using Python. The example will focus on predicting house prices based on features like area and the number of bedrooms. We will use the `scikit-learn` library to build the model and evaluate it with metrics like `MAE`, `MSE`, and `R² Score`.

### Importing Necessary Libraries

First, import the required Python libraries:

```python
import numpy as np
import pandas as pd
```
