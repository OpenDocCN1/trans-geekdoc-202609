
```python
from sklearn.preprocessing import LabelEncoder, StandardScaler

# Load dataset
data = pd.read_csv('customer_churn.csv')

# Feature engineering
data['TotalCharges'] = pd.to_numeric(data['TotalCharges'], errors='coerce')
data['MonthlyCharges_Per_Tenure'] = data['MonthlyCharges'] / (data['tenure'] + 1)

# Encoding categorical features
encoder = LabelEncoder()
data['Gender'] = encoder.fit_transform(data['Gender'])

# Standardize numerical features
scaler = StandardScaler()
data[['MonthlyCharges', 'TotalCharges', 'MonthlyCharges_Per_Tenure']] = scaler.fit_transform(data[['MonthlyCharges', 'TotalCharges', 'MonthlyCharges_Per_Tenure']])

print(data.head())
```

## 4. 特征工程的最佳实践

### 4.1. 了解您的数据

在创建或转换特征之前，花时间了解您的数据。这包括：
- 探索分布：查看各个特征的分布情况。
- 识别相关性：识别特征之间的关系。

### 4.2. 迭代过程

特征工程是一个迭代过程。尝试不同的特征和转换，看看哪些效果最好。

### 4.3. 领域知识

利用领域知识创建有意义的特征，以捕捉数据中的潜在模式。

### 4.4. 避免过拟合

创建过多特征或过于复杂的转换时要谨慎，因为这可能导致过拟合。使用交叉验证来验证您的方法。

### 4.5. 自动化

使用管道和函数自动化重复性任务，以简化特征工程流程。

## 5. 结论

在本教程中，我们探讨了特征工程的关键概念和技术，这是为机器学习准备数据的关键步骤。以下是我们所涵盖内容的总结：

| 主题 | 描述 | 示例代码和函数 |
|---|---|---|
| 介绍 | 特征工程的重要性 | 技术概述 |
| 处理分类特征 | 一热编码和标签编码 | `pd.get_dummies()`, `LabelEncoder` |
| 处理数值特征 | 归一化和标准化 | `MinMaxScaler`, `StandardScaler` |
| 创建新特征 | 多项式、交互和时间特征 | `PolynomialFeatures`, 日期分量提取 |
| 聚合和分组 | 对数据进行分组并聚合值 | `groupby()`, `agg()` |
| 实际示例 | 在不同数据集上进行特征工程的真实世界示例 | 组合技术 |
| 最佳实践 | 了解数据、迭代过程、利用领域知识 | 交叉验证、自动化 |

通过遵循这些技术和最佳实践，您可以增强机器学习模型并获得更好的性能。特征工程是一种强大的工具，当有效使用时，可以释放数据的全部潜力。

祝特征工程愉快！

# 特征缩放和归一化

特征缩放和归一化是机器学习数据预处理管道中的重要步骤。它们确保特征处于可比较的尺度上，这有助于提高许多机器学习算法的性能和收敛速度。在本教程中，我们将探讨特征缩放和归一化的概念、它们之间的差异、各种技术以及使用 Python 的实际示例。

## 1. 特征缩放和归一化的介绍

### 1.1. 什么是特征缩放？

特征缩放涉及调整特征的范围，使其处于相似的尺度。这很重要，因为许多机器学习算法，如基于梯度下降的方法和 k 近邻，对输入特征的尺度很敏感。

### 1.2. 什么是归一化？

归一化是指将特征转换以具有特定范围或分布的过程。它是一种特征缩放，通常涉及将值调整到 0 到 1 的范围内。

### 1.3. 为什么特征缩放和归一化很重要？

特征缩放和归一化很重要，因为：
- 提高模型性能：k 近邻和支持向量机等算法在缩放特征下表现更好。
- 收敛更快：当特征处于相似尺度时，基于梯度下降的算法收敛更快。
- 防止主导：确保没有单个特征因其更大的范围而主导模型。

## 2. 特征缩放和归一化的技术

### 2.1. Min-Max 缩放

Min-max 缩放，也称为归一化，将特征缩放到固定范围，通常为 0 到 1。

#### 2.1.1. 公式

x′=x−xmin⁡xmax⁡−xmin⁡x' = \frac{x - x_{\min}}{x_{\max} - x_{\min}}x′=xmax​−xmin​x−xmin​​

#### 2.1.2. 实现

```python
from sklearn.preprocessing import MinMaxScaler
import pandas as pd

# Example data
data = pd.DataFrame({'Age': [25, 30, 35, 40, 45]})

# Min-max scaling
scaler = MinMaxScaler()
data['Age_Scaled'] = scaler.fit_transform(data[['Age']])
print(data)
```

### 2.2. 标准化

标准化将特征缩放到均值为 0，标准差为 1。

#### 2.2.1. 公式

x′=x−μσx' = \frac{x - \mu}{\sigma}x′=σx−μ​

#### 2.2.2. 实现

```python
from sklearn.preprocessing import StandardScaler

# Example data
data = pd.DataFrame({'Salary': [50000, 60000, 70000, 80000, 90000]})

# Standardization
scaler = StandardScaler()
data['Salary_Standardized'] = scaler.fit_transform(data[['Salary']])
print(data)
```

### 2.3. 稳健缩放

稳健缩放使用中位数和四分位距（IQR）来缩放特征，使其对异常值具有鲁棒性。

#### 2.3.1. 公式

x′=x−medianIQRx' = \frac{x - \text{median}}{\text{IQR}}x′=IQRx−median​

#### 2.3.2. 实现

```python
from sklearn.preprocessing import RobustScaler

# Example data
data = pd.DataFrame({'Income': [45000, 50000, 55000, 60000, 65000]})

# Robust scaling
scaler = RobustScaler()
data['Income_RobustScaled'] = scaler.fit_transform(data[['Income']])
print(data)
```

### 2.4. MaxAbs 缩放

MaxAbs 缩放通过其最大绝对值缩放每个特征，结果值在 -1 到 1 之间。

#### 2.4.1. 实现

```python
from sklearn.preprocessing import MaxAbsScaler

# Example data
data = pd.DataFrame({'Balance': [200, -300, 400, -500, 600]})

# MaxAbs scaling
scaler = MaxAbsScaler()
data['Balance_MaxAbsScaled'] = scaler.fit_transform(data[['Balance']])
print(data)
```

### 2.5. 对数转换

对数转换对数据应用自然对数，这对于处理偏斜分布很有用。

#### 2.5.1. 公式

x′=log⁡(x+1)x' = \log(x + 1)x′=log(x+1)

#### 2.5.2. 实现

```python
import numpy as np

# Example data
data = pd.DataFrame({'Value': [1, 10, 100, 1000, 10000]})

# Log transformation
data['Value_LogTransformed'] = np.log1p(data['Value'])
print(data)
```

### 2.6. 幂转换

幂转换稳定方差并使数据更接近高斯分布。

#### 2.6.1. 实现

```python
from sklearn.preprocessing import PowerTransformer

# Example data
data = pd.DataFrame({'Measurement': [2, 5, 8, 11, 14]})

# Power transformation
scaler = PowerTransformer()
data['Measurement_PowerTransformed'] = scaler.fit_transform(data[['Measurement']])
print(data)
```

## 3. 特征缩放和归一化的实际示例

### 3.1. 示例：在房屋数据集中缩放特征

让我们对房屋数据集应用特征缩放，看看它如何提高模型性能。

示例代码：

```python
import pandas as pd
```
