
## Survey Data Analysis

In social sciences, particularly in survey data analysis, ridge regression can be beneficial when dealing with correlated survey responses, helping to identify significant predictors without overemphasizing any single variable.

## High-Dimensional Data

In Machine Learning applications with high-dimensional data, ridge regression is frequently used to prevent overfitting and stabilize the training of models, especially when the number of features is close to or exceeds the number of samples.

## Image Processing

In remote sensing applications, ridge regression can be applied to image processing tasks where pixels might exhibit correlation. It helps improve the accuracy of image analysis models.

## Lasso Regression

A regularization term is included in the objective function of Lasso regression, which is short for least absolute shrinkage and selection operator. The L1 norm of the coefficients, which represents the regularization term, promotes sparsity by precisely decreasing some coefficients to zero. For feature selection, lasso regression is advantageous because of this characteristic. The objective function of Lasso regression is given as follows:

![](images/eq-5.jpg)

Where:

*   `m` is the number of samples.
*   `n` is the number of features.
*   `θ` is the vector of coefficients (including the intercept term).
*   `xi` is the feature vector for the `i`th sample.
*   `yi` is the target variable for the `i`th sample.
*   `α` is the regularization parameter (hyperparameter).

[Code 3.5](#ch03.xhtml#cd3-5) explains lasso regression along with a Python code example using the `scikit-learn` library.

### Code 3.5: Python code for lasso regression

```python
import numpy as np
from sklearn.linear_model import Lasso
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt

# Generate sample data
np.random.seed(42)
X = 2 * np.random.rand(100, 1)
y = 4 + 3 * X + 1.5 * np.random.randn(100, 1)

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Lasso regression with different alpha values
alphas = [0, 0.1, 1, 10]
plt.figure(figsize=(12, 8))

for alpha in alphas:
    lasso_reg = Lasso(alpha=alpha)
    lasso_reg.fit(X_train, y_train)

    # Make predictions on the test set
    y_pred = lasso_reg.predict(X_test)

    # Plot the results
    plt.scatter(X_test, y_test, label='Actual Data')
    plt.plot(X_test, y_pred, label=f'Lasso Regression (alpha={alpha})')
    plt.xlabel('X-axis')
    plt.ylabel('y-axis')

    # Print the mean squared error
    mse = mean_squared_error(y_test, y_pred)
    print(f'Lasso Regression (alpha={alpha}) - Mean Squared Error: {mse:.2f}')

plt.legend()
plt.show()
```

Refer to [Figure 3.8](#ch03.xhtml#fig3-8) for the output of the code:

![](images/3.8.png)

**Figure 3.8: Output of Code 3.5**

In this code, we generate synthetic data with a linear relationship and add some noise. The data is split into training and testing sets. Lasso regression is applied with different values of the regularization parameter. The results, including mean squared error, are printed and plotted for visualization. You can adjust the `alpha` values and other parameters based on your specific use case. Lasso regression can effectively shrink coefficients to zero, aiding in feature selection and creating simpler models. It proves valuable when handling high-dimensional data containing potentially irrelevant features.

Lasso regression, with its ability to introduce sparsity by shrinking some coefficients exactly to zero, finds applications in various fields. Some common applications of Lasso regression are mentioned below:

*   **Genomics**: In genomics research, lasso regression is used to select relevant genes from a large set of genetic markers, aiding in identifying potential biomarkers for diseases.
*   **Variable selection in economic models**: Lasso is applied in economic studies to select relevant economic indicators or variables while handling multicollinearity.
*   **Risk management**: Lasso regression is used in finance for risk management and portfolio optimization by selecting relevant financial features and constructing more robust models.
*   **Drug discovery**: In drug discovery, lasso regression helps identify important features in large datasets related to drug responses and treatment outcomes.
*   **Environmental modelling**: Lasso is applied in environmental sciences to identify key factors influencing environmental outcomes, such as pollution levels or climate change impacts.
*   **Customer segmentation**: Lasso regression is used in marketing to select relevant customer segmentation features, aiding in targeted marketing strategies.
*   **Sparse signal reconstruction**: Lasso is applied in signal processing for sparse signal reconstruction, where it helps recover a sparse representation of a signal from noisy measurements.
*   **Sparse data representation**: Lasso regression is employed in Machine Learning for sparse data representation and feature selection, enhancing model interpretability and generalization.
*   **Clinical trials**: In clinical trials, lasso regression is used to select relevant features for predicting patient outcomes, contributing to personalized medicine.
*   **Medical imaging**: Lasso is applied in medical image processing for feature selection in tasks such as tumor detection and image classification.
*   **Brain imaging**: Lasso regression is used in neuroscience for analyzing brain imaging data and identifying relevant brain regions associated with specific conditions or tasks.
*   **Survey data analysis**: Lasso regression aids in social sciences by selecting important features in survey data, helping researchers understand relationships between variables.
*   **Energy consumption prediction**: Lasso regression is applied in energy forecasting to select relevant features for predicting energy consumption, contributing to efficient energy management.

## Performance Evaluation of Regression Models

Evaluating the performance of regression models is crucial to determine how well a model fits the data and makes accurate predictions. Several evaluation metrics can be used to assess the performance of regression models. Some common methods and metrics for evaluating regression models are mentioned below:

### Mean Absolute Error (MAE)

It quantifies the average absolute disparity between predicted values and actual values. It exhibits lower sensitivity to outliers in contrast to the MSE. Mathematically it is represented as follows:

![](images/eq-6.jpg)

Where:

*   `n` is the number of samples in the dataset.
*   `Yi` represents the true target values or observations.
*   `Ŷi` represents the predicted values from a model.
*   `|Yi - Ŷi|` calculates the absolute difference between the true value `Yi` and the predicted value `Ŷi` for each sample.
*   `∑|Yi - Ŷi|` calculates the sum of all absolute differences across all samples.

### Mean Squared Error (MSE)

It calculates the average squared deviation between predicted and actual values, assigning greater importance to larger errors. Mathematically it is represented as follows and all variables are explained as above:

![](images/eq-7.jpg)

### Root Mean Squared Error (RMSE)

It is derived from the square root of the MSE, offering an understandable metric for assessing the average prediction error. Mathematically it is represented as follows:

![](images/eq-8.png)

### R-squared (R²) Score

R-squared evaluates the fraction of the variance in the dependent variable accounted for by the independent variables. A greater R-squared value signifies a stronger alignment of the model with the dataset. Mathematically it is represented as follows:

![](images/eq-9.jpg)

Where:

*   **SSR**: Sum of Squares of Residuals
*   `R2 = MSE * n`
