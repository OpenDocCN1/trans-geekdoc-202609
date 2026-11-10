
# 8.5 数据分布（正态，偏态）

数据分布是指数据集中的数据值是如何分布或排列的。理解分布类型对于统计分析至关重要，有助于确定适当的统计检验和模型。

## 8.5.1 正态分布

正态分布，也称为高斯分布，是统计学中最常用的数据分布。它是对称的并遵循钟形曲线。

### 关键特征

• 对称性：分布围绕均值完全对称。
• `Mean = Median = Mode`：三个集中趋势度量相等且位于分布中心。
• 形状：钟形曲线，尾部向两个方向无限延伸。
• 经验法则（68-95-99.7 法则）：
  * 68% 的数据落在均值的 1 个标准差范围内。
  * 95% 的数据落在 2 个标准差范围内。
  * 99.7% 的数据落在 3 个标准差范围内。

### 示例

• 人口中成人的身高。
• 标准化考试的考试成绩（例如，SAT、智商测试）。

### 可视化表示
对称曲线，其中最高点对应均值，随着远离均值概率递减。

## 8.5.2 偏态分布

偏态分布是不对称的，数据值更集中在均值的一侧。偏度表示不对称的方向和程度。

### 偏态分布的类型

#### 正偏态（右偏态）

• 右侧尾部：右侧尾部（较大值）比左侧尾部更长。
• `Mean > Median > Mode`：均值被拉向较大值。
• 示例：收入分布（大多数人收入低于均值，少数人收入高得多）。
• 可视化表示：左侧峰值，右侧延伸出长尾的曲线。

#### 负偏态（左偏态）

• 左侧尾部：左侧尾部（较小值）比右侧尾部更长。
• `Mean < Median < Mode`：均值被拉向较小值。
• 示例：退休年龄（大多数人退休年龄较大，少数人提前退休）。
• 可视化表示：右侧峰值，左侧延伸出长尾的曲线。

## 8.5.3 正态分布与偏态分布的比较

| 方面 || 正态分布 || 偏态分布 |
| --- | --- | --- |
| 对称性 || 完全对称 || 非对称 |
| 均值、中位数、众数 || 全部相等 || 均值、中位数和众数不同 |
| 尾部 || 两侧相等 || 一侧尾部更长 |
| 示例 || 身高、考试成绩 || 收入（正偏）、退休年龄（负偏） |

## 8.5.4 何时使用正态或偏态分布

**正态分布：**
• 适用于许多自然现象（例如，身高、体重）。
• 常用于假设检验、置信区间和回归分析。

**偏态分布：**
• 表示存在异常值或数据分布不均匀。
• 需要转换（例如，对数）以用于假设正态性的统计检验。

总之，了解数据集是否遵循正态或偏态分布对于选择适当的统计方法至关重要。正态分布由于其成熟的特性简化了许多分析，而偏态分布则提供了有关数据不对称性和潜在异常值的有价值见解，有助于更深入地理解数据集。

# 8.6 实战：使用 Python（pandas、NumPy）进行描述性统计

描述性统计总结并描述数据集的主要特征。它们包括均值、中位数、标准差等度量，以及直方图和箱线图等可视化工具。Python 库如 `pandas` 和 `NumPy` 对于执行描述性统计分析至关重要。以下是实战细节。

## 导入所需库

首先导入数据操作和计算所需的库。

```python
import pandas as pd
import numpy as np
```

## 创建和加载数据

示例数据集：您可以为练习创建小型数据集或从文件加载数据。

```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eve'],
    'Age': [25, 30, 35, 40, 28],
    'Salary': [50000, 60000, 75000, 80000, 58000],
    'Department': ['HR', 'IT', 'Finance', 'IT', 'HR']
}
df = pd.DataFrame(data)
print(df)
```

输出：
Name  Age  Salary Department
0    Alice   25   50000        HR
1      Bob   30   60000        IT
2  Charlie   35   75000    Finance
3    David   40   80000        IT
4      Eve   28   58000        HR

## 基本描述性统计

### 使用 pandas

汇总统计：

```python
print(df.describe())
```

输出：
Age        Salary
count   5.000000     5.000000
mean   31.600000  64600.000000
std     6.579049  11662.277660
min    25.000000  50000.000000
25%    28.000000  58000.000000
50%    30.000000  60000.000000
75%    35.000000  75000.000000
max    40.000000  80000.000000

具体度量：
均值：
```python
print(df['Salary'].mean())  # Output: 64600.0
```
中位数：
```python
print(df['Salary'].median())  # Output: 60000.0
```
标准差：
```python
print(df['Salary'].std())  # Output: 11662.27766016838
```
众数：
```python
print(df['Department'].mode())  # Output: IT
```

### 使用 NumPy

对于数值计算，`NumPy` 提供高效的方法：

```python
salaries = df['Salary'].values
# Mean
print(np.mean(salaries))  # Output: 64600.0
# Median
print(np.median(salaries))  # Output: 60000.0
# Standard Deviation
print(np.std(salaries))  # Output: 11016.68311293057
```

## 百分位数和四分位数

百分位数和四分位数将数据集划分为若干部分以更好地理解数据分布。

使用 `NumPy`：

```python
# 25th and 75th Percentiles
print(np.percentile(salaries, 25))  # Output: 58000.0
print(np.percentile(salaries, 75))  # Output: 75000.0
# Interquartile Range (IQR)
iqr = np.percentile(salaries, 75) - np.percentile(salaries, 25)
print(iqr)  # Output: 17000.0
```

## 分组描述性统计

使用 pandas `GroupBy`：

```python
grouped = df.groupby('Department')['Salary'].mean()
print(grouped)
```

输出：
Department
Finance    75000.0
HR         54000.0
IT         70000.0
Name: Salary, dtype: float64

多个聚合：

```python
agg_stats = df.groupby('Department').agg({
    'Salary': ['mean', 'median', 'std']
})
print(agg_stats)
```

输出：
Salary
mean   median           std
Department
Finance  75000.0  75000.0           NaN
HR       54000.0  54000.0   5656.854249
IT       70000.0  70000.0  14142.135624

## 可视化描述性统计

### 直方图

```python
import matplotlib.pyplot as plt
df['Salary'].plot(kind='hist', bins=5, title='Salary Distribution')
plt.xlabel('Salary')
plt.show()
```

![薪资分布图 AI 生成内容可能不正确。](image_rsrcF18.jpg)

### 箱线图

```python
df.boxplot(column='Salary', by='Department')
plt.title('Salary by Department')
plt.suptitle('')  # Removes default title
plt.xlabel('Department')
plt.ylabel('Salary')
plt.show()
```

![带线条和点的图表 AI 生成内容可能不正确。](image_rsrcF19.jpg)

## 处理缺失值

真实数据集通常包含缺失值。您可以使用 `pandas` 管理它们。

### 示例数据（`data.csv`）

```
Name,Age,Department,Salary
Alice,25,IT,50000
Bob,30,HR,45000
Charlie,,Finance,60000
David,35,IT,
Eve,40,Finance,70000
Frank,,HR,55000
Grace,28,IT,48000
```

### 加载数据

```python
import pandas as pd
# Load the sample data
df = pd.read_csv('data.csv')
print("Original Data:")
print(df)
```

输出：
Name Age Department Salary
Alice 25.0 IT 50000.0
Bob 30.0 HR 45000.0
Charlie NaN Finance 60000.0
David 35.0 IT NaN
Eve 40.0 Finance 70000.0
Frank NaN HR 55000.0
Grace 28.0 IT 48000.0

### 检查缺失值

```python
# Check for missing values
print("\nMissing Values Count:")
print(df.isnull().sum())
```

输出：
