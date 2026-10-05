
`lower_bound = q1 - (1.5 * iqr)`

`upper_bound = q3 + (1.5 * iqr)`

`return s.clip(lower_bound, upper_bound)`

`df['price'] = cap_outliers(df['price'])`

### 3. Handling Inconsistent Data

* Standardizing formats (e.g., dates, currencies)
* Correcting typographical errors
* Resolving conflicting information

Example: Standardizing date formats

```python
df['sale_date'] = pd.to_datetime(df['sale_date'], format='%m/%d/%Y')
```

### 4. Handling Duplicate Data

* Identification
* Removal or merging

Example: Removing duplicate entries

```python
# Check for duplicates
print(df.duplicated().sum())

# Remove duplicates
df.drop_duplicates(inplace=True)
```

## 3.2 Feature Engineering and Selection

Feature engineering is the process of creating new features or transforming existing ones to improve model performance. Feature selection involves choosing the most relevant features for your model.

### 3.2.1 Feature Engineering

1. Creating Interaction Features: Combining two or more features to create a new feature that captures their interaction.

Example: Creating an interaction feature for price per square foot

```python
df['price_per_sqft'] = df['price'] / df['sq_ft']
```

2. Binning: Converting continuous variables into categorical ones.

Example: Binning house prices into categories

```python
df['price_category'] = pd.cut(df['price'], bins=[0, 200000, 500000, 1000000, float('inf')],
                              labels=['Budget', 'Mid-range', 'High-end', 'Luxury'])
```

3. One-Hot Encoding: Converting categorical variables into binary vectors.

Example: One-hot encoding for house type

```python
df_encoded = pd.get_dummies(df, columns=['house_type'], prefix='type')
```

4. Feature Scaling: Normalizing the range of features to a common scale.

Example: Standardizing numerical features

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df[['sq_ft', 'price']] = scaler.fit_transform(df[['sq_ft', 'price']])
```

5. Text Feature Engineering: Creating numerical features from text data.

Example: Extracting features from property descriptions

```python
from sklearn.feature_extraction.text import CountVectorizer

vectorizer = CountVectorizer(stop_words='english')
description_features = vectorizer.fit_transform(df['description'])
```

### 3.2.2 Feature Selection

1. Filter Methods: Selecting features based on statistical measures.

Example: Correlation-based feature selection

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Compute correlation matrix
corr_matrix = df.corr()

# Plot heatmap
plt.figure(figsize=(12, 10))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Feature Correlation Heatmap')
plt.show()

# Select features with correlation to target above a threshold
target_corr = corr_matrix['price'].abs().sort_values(ascending=False)
selected_features = target_corr[target_corr > 0.5].index.tolist()
```

2. Wrapper Methods: Using a model to evaluate feature subsets.

Example: Recursive Feature Elimination

```python
from sklearn.feature_selection import RFE
from sklearn.linear_model import LinearRegression

model = LinearRegression()
rfe = RFE(estimator=model, n_features_to_select=5)
rfe = rfe.fit(X, y)
selected_features = X.columns[rfe.support_]
```

3. Embedded Methods: Feature selection as part of the model training process.

Example: Lasso Regression for feature selection

```python
from sklearn.linear_model import Lasso

lasso = Lasso(alpha=0.1)
lasso.fit(X, y)
selected_features = X.columns[lasso.coef_ != 0]
```

## 3.3 Exploratory Data Analysis

Exploratory Data Analysis (EDA) is the process of analysing and visualizing data to understand its main characteristics, often using statistical graphics and other data visualization methods.

### 3.3.1 Univariate Analysis

Examining the distribution and statistics of individual variables.

Example: Analyzing the distribution of house prices

```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
sns.histplot(df['price'], kde=True)
plt.title('Distribution of House Prices')
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.show()

print(df['price'].describe())
```

### 3.3.2 Bivariate Analysis

Examining the relationship between pairs of variables.

Example: Analysing the relationship between house size and price

```python
plt.figure(figsize=(10, 6))
sns.scatterplot(x='sq_ft', y='price', data=df)
plt.title('House Price vs. Size')
plt.xlabel('Square Footage')
plt.ylabel('Price')
plt.show()

print(f"Correlation coefficient: {df['sq_ft'].corr(df['price']):.2f}")
```

### 3.3.3 Multivariate Analysis

Examining relationships between three or more variables simultaneously.

Example: Analysing house price, size, and number of bedrooms

```python
plt.figure(figsize=(12, 8))
sns.scatterplot(x='sq_ft', y='price', hue='bedrooms', size='bedrooms', data=df)
plt.title('House Price vs. Size, colored by Number of Bedrooms')
plt.xlabel('Square Footage')
plt.ylabel('Price')
plt.show()
```

## 3.4 Data Visualization Techniques

Data visualization is crucial for understanding patterns, trends, and relationships in your data. It's an essential part of both exploratory data analysis and communicating results.

### 3.4.1 Basic Plots

1. Line Plots: Useful for showing trends over time or other continuous variables.

Example: Trend of average house prices over time

```python
df['year'] = df['sale_date'].dt.year
yearly_avg_price = df.groupby('year')['price'].mean().reset_index()

plt.figure(figsize=(12, 6))
plt.plot(yearly_avg_price['year'], yearly_avg_price['price'])
plt.title('Average House Price Trend')
plt.xlabel('Year')
plt.ylabel('Average Price')
plt.show()
```

2. Bar Plots: Useful for comparing quantities across different categories.

Example: Average house price by number of bedrooms

```python
plt.figure(figsize=(10, 6))
sns.barplot(x='bedrooms', y='price', data=df)
plt.title('Average House Price by Number of Bedrooms')
plt.xlabel('Number of Bedrooms')
plt.ylabel('Average Price')
plt.show()
```

3. Scatter Plots: Useful for showing the relationship between two continuous variables.

Example: Relationship between house size and price

```python
plt.figure(figsize=(10, 6))
sns.scatterplot(x='sq_ft', y='price', data=df)
plt.title('House Price vs. Size')
plt.xlabel('Square Footage')
plt.ylabel('Price')
plt.show()
```

### 3.4.2 Advanced Plots

1. Box Plots: Useful for showing the distribution of a variable across different categories.

Example: Distribution of house prices by house type

```python
plt.figure(figsize=(12, 6))
sns.boxplot(x='house_type', y='price', data=df)
plt.title('House Price Distribution by House Type')
plt.xlabel('House Type')
plt.ylabel('Price')
plt.xticks(rotation=45)
plt.show()
```

2. Heatmaps: Useful for visualizing correlation matrices or other 2D data.

Example: Correlation heatmap of numerical features

```python
plt.figure(figsize=(10, 8))
sns.heatmap(df.select_dtypes(include=[np.number]).corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap of Numerical Features')
plt.show()
```

3. Pair Plots: Useful for visualizing pairwise relationships in a dataset.

Example: Pair plot of key house features

```python
sns.pairplot(df[['price', 'sq_ft', 'bedrooms', 'bathrooms']])
plt.suptitle('Pair Plot of Key House Features', y=1.02)
plt.show()
```

### 3.4.3 Geospatial Visualization

For datasets with geographical information, geospatial visualization can be very insightful.

Example: Visualizing house prices on a map

```python
import folium

# Create a map centered on the mean latitude and longitude
m = folium.Map(location=[df['latitude'].mean(), df['longitude'].mean()], zoom_start=12)

# Add markers for each house
```
