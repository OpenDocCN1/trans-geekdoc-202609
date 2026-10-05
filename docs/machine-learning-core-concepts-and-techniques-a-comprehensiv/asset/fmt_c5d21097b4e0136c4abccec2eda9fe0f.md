
# Example: Ridge regression for house price prediction

```python
from sklearn.linear_model import Ridge
from sklearn.preprocessing import StandardScaler

# Prepare the data
X = df[['sqft_living', 'bedrooms', 'bathrooms', 'floors']]
y = df['price']

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Scale the features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Create and train the model
alpha = 1.0
model = Ridge(alpha=alpha)
model.fit(X_train_scaled, y_train)

# Make predictions
y_pred = model.predict(X_test_scaled)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Print coefficients
for feature, coef in zip(X.columns, model.coef_):
    print(f"{feature}: {coef}")
```

## 4.3.2 Lasso Regression (L1 Regularization)

Lasso regression adds a penalty term proportional to the absolute value of the magnitude of coefficients.

Mathematical representation: Loss = MSE + α * Σ|β|

### Example: Lasso regression for house price prediction

```python
from sklearn.linear_model import Lasso

# Create and train the model
alpha = 1.0
model = Lasso(alpha=alpha)
model.fit(X_train_scaled, y_train)

# Make predictions
y_pred = model.predict(X_test_scaled)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Print coefficients
for feature, coef in zip(X.columns, model.coef_):
    print(f"{feature}: {coef}")
```

## 4.3.3 Elastic Net

Elastic Net combines both L1 and L2 regularization.

Mathematical representation: Loss = MSE + α * (ρ * Σ|β| + (1-ρ)/2 * Σ(β²))

### Example: Elastic Net regression for house price prediction

```python
from sklearn.linear_model import ElasticNet

# Create and train the model
alpha = 1.0
l1_ratio = 0.5
model = ElasticNet(alpha=alpha, l1_ratio=l1_ratio)
model.fit(X_train_scaled, y_train)

# Make predictions
y_pred = model.predict(X_test_scaled)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Print coefficients
for feature, coef in zip(X.columns, model.coef_):
    print(f"{feature}: {coef}")
```

### 4.4 Non-linear Regression Techniques

## 4.4.1 Decision Tree Regression

Decision trees can be used for regression tasks by predicting the mean value of the samples in each leaf.

### Example: Decision Tree regression for house price prediction

```python
from sklearn.tree import DecisionTreeRegressor

# Create and train the model
model = DecisionTreeRegressor(max_depth=5, random_state=42)
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Visualize the tree (requires graphviz)
from sklearn.tree import plot_tree
plt.figure(figsize=(20,10))
plot_tree(model, feature_names=X.columns, filled=True, rounded=True)
plt.show()
```

## 4.4.2 Random Forest Regression

Random Forest is an ensemble learning method that constructs multiple decision trees and outputs the mean prediction of the individual trees.

### Example: Random Forest regression for house price prediction

```python
from sklearn.ensemble import RandomForestRegressor

# Create and train the model
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Feature importance
importances = model.feature_importances_
for feature, importance in zip(X.columns, importances):
    print(f"{feature}: {importance}")
```

## 4.4.3 Support Vector Regression (SVR)

SVR uses the same principles as SVM for classification, but for regression tasks.

### Example: SVR for house price prediction

```python
from sklearn.svm import SVR
from sklearn.preprocessing import StandardScaler

# Scale the features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Create and train the model
model = SVR(kernel='rbf', C=100, epsilon=0.1)
model.fit(X_train_scaled, y_train)

# Make predictions
y_pred = model.predict(X_test_scaled)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")
```

### 4.5 Time Series Regression

Time series regression involves predicting future values based on previously observed values.

## 4.5.1 Autoregressive Integrated Moving Average (ARIMA)

ARIMA is a popular model for time series forecasting that explicitly models the autocorrelation in the data.

### Example: ARIMA for monthly house price prediction

```python
import pandas as pd
import numpy as np
from statsmodels.tsa.arima.model import ARIMA
import matplotlib.pyplot as plt

# Load time series data
df = pd.read_csv('monthly_house_prices.csv', parse_dates=['date'], index_col='date')

# Fit ARIMA model
model = ARIMA(df['price'], order=(1, 1, 1))
results = model.fit()

# Forecast future values
forecast = results.forecast(steps=12)

# Plot the results
plt.figure(figsize=(12, 6))
plt.plot(df.index, df['price'], label='Observed')
plt.plot(pd.date_range(start=df.index[-1], periods=13, freq='M')[1:], forecast, label='Forecast')
plt.xlabel('Date')
plt.ylabel('House Price')
plt.title('ARIMA Time Series Forecast of House Prices')
plt.legend()
plt.show()

print(results.summary())
```

This comprehensive overview of regression techniques covers the fundamental concepts, implementation, and evaluation of various regression models. These techniques form the backbone of many predictive modeling tasks in machine learning and data science.

# Chapter 5: Supervised Learning: Classification

Classification is a type of supervised learning where the goal is to predict a categorical outcome variable based on one or more input features. In this chapter, we'll explore various classification techniques, their mathematical foundations, implementation, and applications.

### 5.1 Logistic Regression

Despite its name, logistic regression is a classification algorithm, not a regression algorithm. It's used for binary classification problems.

## 5.1.1 Binary Logistic Regression

Binary logistic regression models the probability that an instance belongs to a particular class.

Mathematical representation: P(Y=1|X) = 1 / (1 + e^(-z)) where z = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ

### Example: Predicting whether a customer will churn or not

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix, classification_report
from sklearn.preprocessing import StandardScaler

# Load the data
df = pd.read_csv('customer_churn.csv')

# Prepare the data
X = df[['tenure', 'monthly_charges', 'total_charges']]
y = df['churn'].map({'Yes': 1, 'No': 0})

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Scale the features
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# Create and train the model
model = LogisticRegression()
model.fit(X_train_scaled, y_train)

# Make predictions
```
