
```python
for idx, row in df.iterrows():
    folium.CircleMarker(
        location=[row['latitude'], row['longitude']],
        radius=5,
        popup=f"Price: ${row['price']:,.0f}, Sq Ft: {row['sq_ft']}",
        color='red',
        fill=True,
        fillColor='red'
    ).add_to(m)
```
# Save the map
```python
m.save("house_prices_map.html")
```

### 3.5 Dimensionality Reduction

Dimensionality reduction techniques are used to reduce the number of features in a dataset while retaining as much information as possible. This is useful for visualization, noise reduction, and improving model performance.

#### 3.5.1 Principal Component Analysis (PCA)

`PCA` is a technique that transforms the data into a new coordinate system where the new axes (principal components) are ordered by the amount of variance they explain in the data.

Example: Applying PCA to house features

```python
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler

# Select numerical features
numerical_features = ['sq_ft', 'bedrooms', 'bathrooms', 'year_built']

# Standardize the features
scaler = StandardScaler()
X_scaled = scaler.fit_transform(df[numerical_features])

# Apply PCA
pca = PCA()
X_pca = pca.fit_transform(X_scaled)

# Plot explained variance ratio
plt.figure(figsize=(10, 6))
plt.plot(range(1, len(pca.explained_variance_ratio_) + 1), np.cumsum(pca.explained_variance_ratio_))
plt.xlabel('Number of Components')
plt.ylabel('Cumulative Explained Variance Ratio')
plt.title('Explained Variance Ratio by PCA Components')
plt.show()
```

#### 3.5.2 t-SNE (t-Distributed Stochastic Neighbour Embedding)

`t-SNE` is a nonlinear dimensionality reduction technique particularly well suited for visualizing high-dimensional data.

Example: Visualizing house data using t-SNE

```python
from sklearn.manifold import TSNE

# Apply t-SNE
tsne = TSNE(n_components=2, random_state=42)
X_tsne = tsne.fit_transform(X_scaled)

# Visualize the result
plt.figure(figsize=(12, 8))
scatter = plt.scatter(X_tsne[:, 0], X_tsne[:, 1], c=df['price'], cmap='viridis')
plt.colorbar(scatter)
plt.title('t-SNE Visualization of House Data')
plt.xlabel('t-SNE Feature 1')
plt.ylabel('t-SNE Feature 2')
plt.show()
```

This comprehensive overview of data pre-processing and exploration covers the essential steps needed to prepare and understand your data before building machine learning models. These techniques are crucial for ensuring the quality of your data and gaining insights that can inform your modelling approach.

# Chapter 4: Supervised Learning: Regression

Regression is a type of supervised learning where the goal is to predict a continuous outcome variable based on one or more input features. In this chapter, we'll explore various regression techniques, their mathematical foundations, implementation, and applications.

### 4.1 Linear Regression

Linear regression is the simplest and most widely used regression technique. It models the relationship between the dependent variable and one or more independent variables using a linear equation.

#### 4.1.1 Simple Linear Regression

Simple linear regression involves one independent variable and one dependent variable.

Mathematical representation: `y = β₀ + β₁x + ε`

Where:

* `y` is the dependent variable
* `x` is the independent variable
* `β₀` is the y-intercept
* `β₁` is the slope
* `ε` is the error term

Example: Predicting house prices based on square footage

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Load the data
df = pd.read_csv('house_data.csv')

# Prepare the data
X = df['sqft_living'].values.reshape(-1, 1)
y = df['price'].values

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and train the model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Visualize the results
plt.scatter(X_test, y_test, color='blue', alpha=0.5)
plt.plot(X_test, y_pred, color='red', linewidth=2)
plt.xlabel('Square Footage')
plt.ylabel('Price')
plt.title('Simple Linear Regression: House Price vs Square Footage')
plt.show()
```

#### 4.1.2 Multiple Linear Regression

Multiple linear regression involves two or more independent variables.

Mathematical representation: `y = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ + ε`

Example: Predicting house prices based on multiple features

```python
# Prepare the data
X = df[['sqft_living', 'bedrooms', 'bathrooms', 'floors']]
y = df['price']

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and train the model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Print coefficients
for feature, coef in zip(X.columns, model.coef_):
    print(f"{feature}: {coef}")
```

#### 4.1.3 Assumptions of Linear Regression

1. Linearity: The relationship between X and Y is linear.
2. Independence: Observations are independent of each other.
3. Homoscedasticity: The variance of residual is the same for any value of X.
4. Normality: For any fixed value of X, Y is normally distributed.

#### 4.1.4 Evaluation Metrics for Regression

1. Mean Squared Error (MSE): Average of the squared differences between predicted and actual values.
2. Root Mean Squared Error (RMSE): Square root of MSE, in the same units as the target variable.
3. Mean Absolute Error (MAE): Average of the absolute differences between predicted and actual values.
4. R-squared (R²): Proportion of the variance in the dependent variable that is predictable from the independent variable(s).

### 4.2 Polynomial Regression

Polynomial regression is used when the relationship between the independent variable and the dependent variable is nonlinear.

Mathematical representation: `y = β₀ + β₁x + β₂x² + ... + βₙxⁿ + ε`

Example: Predicting house prices with polynomial features

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline

# Prepare the data
X = df['sqft_living'].values.reshape(-1, 1)
y = df['price'].values

# Split the data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Create and train the model
degree = 2
model = make_pipeline(PolynomialFeatures(degree), LinearRegression())
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Evaluate the model
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
print(f"R-squared: {r2}")

# Visualize the results
X_plot = np.linspace(X.min(), X.max(), 100).reshape(-1, 1)
y_plot = model.predict(X_plot)
plt.scatter(X_test, y_test, color='blue', alpha=0.5)
plt.plot(X_plot, y_plot, color='red', linewidth=2)
plt.xlabel('Square Footage')
plt.ylabel('Price')
plt.title(f'Polynomial Regression (degree={degree}): House Price vs Square Footage')
plt.show()
```

### 4.3 Regularization Techniques

Regularization is used to prevent overfitting by adding a penalty term to the loss function.

#### 4.3.1 Ridge Regression (L2 Regularization)

Ridge regression adds a penalty term proportional to the square of the magnitude of coefficients.

Mathematical representation: `Loss = MSE + α * Σ(β²)`
