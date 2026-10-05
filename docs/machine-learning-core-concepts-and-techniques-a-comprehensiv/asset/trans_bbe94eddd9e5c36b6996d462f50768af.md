

### 相关性和协方差：衡量变量之间的关系
示例：在特征选择中，我们可能会移除高度相关的特征以减少冗余。

## 2.2.3 推断统计

1. 抽样和样本统计量
示例：在自助法中，我们从数据集中创建多个样本来估计统计量的分布。

2. 假设检验：
* 零假设和备择假设
* p值和显著性水平
示例：我们可能会使用假设检验来确定两个机器学习模型之间性能差异是否具有统计显著性。

3. 置信区间：很可能包含真实总体参数的值范围
示例：我们可以计算模型性能指标的置信区间以评估其可靠性。

4. 最大似然估计（`MLE`）：一种估计统计模型参数的方法
示例：在逻辑回归中，`MLE`常用于寻找最优系数。

### 2.3 机器学习的编程基础（以 Python 为主）

虽然机器学习概念与语言无关，但由于其简洁性和丰富的库生态系统，Python 已成为机器学习的事实标准语言。

#### 2.3.1 Python 基础

1. 数据类型：`int`, `float`, `str`, `bool`, `list`, `tuple`, `dict`
示例：
```python
# Feature vector for a house
house = [1500, 3, 2, 250000]

# Dictionary representing a data point
house_dict = {
    'sqft': 1500,
    'bedrooms': 3,
    'bathrooms': 2,
    'price': 250000
}
```

2. 控制结构：`if-else`, `for` 循环，`while` 循环
示例：
```python
# Simple decision tree logic
def classify_fruit(color, diameter):
    if color == 'red':
        if diameter < 7:
            return 'cherry'
        else:
            return 'apple'
    elif color == 'yellow':
        return 'banana'
```

3. 函数和模块
示例：
```python
def calculate_mse(y_true, y_pred):
    """Calculate Mean Squared Error"""
    return np.mean((y_true - y_pred) ** 2)
```

#### 2.3.2 NumPy

`NumPy` 是 Python 中数值计算的基础。

1. 数组和数组操作
示例：
```python
import numpy as np

# Create a feature matrix
X = np.array([[1500, 3, 2],
              [1200, 2, 1],
              [1800, 4, 3]])

# Calculate mean of each feature
feature_means = np.mean(X, axis=0)
```

2. 广播
示例：
```python
# Standardize features
X_standardized = (X - feature_means) / np.std(X, axis=0)
```

3. 线性代数运算
示例：
```python
# Matrix multiplication for linear regression
weights = np.linalg.inv(X.T @ X) @ X.T @ y
```

#### 2.3.3 Pandas

`Pandas` 对于数据处理和分析至关重要。

1. DataFrames 和 Series
示例：
```python
import pandas as pd

# Create a DataFrame from a dictionary
df = pd.DataFrame({
    'sqft': [1500, 1200, 1800],
    'bedrooms': [3, 2, 4],
    'bathrooms': [2, 1, 3],
    'price': [250000, 200000, 300000]
})
```

2. 数据加载和保存
示例：
```python
# Load data from a CSV file
df = pd.read_csv('house_data.csv')

# Save processed data
df.to_csv('processed_house_data.csv', index=False)
```

3. 数据操作：过滤、分组、合并
示例：
```python
# Filter houses with more than 2 bedrooms
large_houses = df[df['bedrooms'] > 2]

# Calculate average price per square foot by number of bedrooms
price_per_sqft = df.groupby('bedrooms')['price'].mean() / df.groupby('bedrooms')['sqft'].mean()
```

#### 2.3.4 Matplotlib 和 Seaborn

这些库用于数据可视化，这对于探索性数据分析和呈现结果至关重要。

1. 基础图表：线图、散点图、直方图
示例：
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Scatter plot of house prices vs. square footage
plt.figure(figsize=(10, 6))
plt.scatter(df['sqft'], df['price'])
plt.xlabel('Square Footage')
plt.ylabel('Price')
plt.title('House Prices vs. Square Footage')
plt.show()
```

2. 统计可视化：箱线图、小提琴图
示例：
```python
# Box plot of prices by number of bedrooms
plt.figure(figsize=(10, 6))
sns.boxplot(x='bedrooms', y='price', data=df)
plt.xlabel('Number of Bedrooms')
plt.ylabel('Price')
plt.title('House Prices by Number of Bedrooms')
plt.show()
```

#### 2.3.5 Scikit-learn

`Scikit-learn` 为许多机器学习算法和工具提供了统一的接口。

1. 数据预处理
示例：
```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_scaled = scaler.fit_transform(df[['sqft', 'bedrooms', 'bathrooms']])
```

2. 模型训练和评估
示例：
```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Split data in to training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X_scaled, df['price'], test_size=0.2, random_state=42)

# Train a linear regression model
model = LinearRegression()
model.fit(X_train, y_train)

# Make predictions and evaluate the model
y_pred = model.predict(X_test)
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse}")
```

3. 交叉验证
示例：
```python
from sklearn.model_selection import cross_val_score

# Perform 5-fold cross-validation
cv_scores = cross_val_score(model, X_scaled, df['price'], cv=5, scoring='neg_mean_squared_error')
print(f"Cross-validation MSE scores: {-cv_scores}")
print(f"Average MSE: {-cv_scores.mean()}")
```

这份机器学习基础的全面概述涵盖了理解和实现机器学习算法所需的核心数学、统计和编程概念。这些概念将在后续章节中得到应用和扩展，我们将深入探讨具体的机器学习技术和应用。

# 第 3 章：数据预处理和探索

### 3.1 数据收集和清洗

数据收集和清洗是任何机器学习项目中的基本步骤。数据的质量直接影响模型的性能。

#### 3.1.1 数据收集

1. 数据来源：
* 数据库（例如，SQL，NoSQL）
* API
* 网络爬取
* 调查和表单
* 传感器和物联网设备

示例：收集房屋价格数据
```python
import pandas as pd
import requests

# Collecting data from an API
api_url = "https://api.example.com/house_prices"
response = requests.get(api_url)
data = response.json()

# Convert to DataFrame
df = pd.DataFrame(data)

# Save to CSV
df.to_csv("house_prices.csv", index=False)
```

2. 数据抽样：
* 随机抽样
* 分层抽样
* 整群抽样

示例：分层抽样以确保不同房屋类型的代表性
```python
from sklearn.model_selection import train_test_split

# Stratified split based on house type
train_data, test_data = train_test_split(df, test_size=0.2, stratify=df['house_type'])
```

#### 3.1.2 数据清洗

1. 处理缺失值：
* 删除（列删除或成对删除）
* 插补（均值、中位数、众数或预测值）

示例：处理房屋价格数据中的缺失值
```python
# Check for missing values
print(df.isnull().sum())

# Fill missing numerical values with median
df['sq_ft'].fillna(df['sq_ft'].median(), inplace=True)

# Fill missing categorical values with mode
df['house_type'].fillna(df['house_type'].mode()[0], inplace=True)
```

2. 处理异常值：
* 识别（Z-score，IQR 方法）
* 处理（移除、截断、转换）

示例：识别并截断异常值
```python
import numpy as np

def cap_outliers(s):
    q1, q3 = s.quantile([0.25, 0.75])
    iqr = q3 - q1
```
