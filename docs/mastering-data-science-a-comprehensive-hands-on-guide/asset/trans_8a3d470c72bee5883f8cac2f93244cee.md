
## 多索引
### 创建和使用多索引
`MultiIndexing` 启用分层索引，允许用户处理具有多个索引级别的数据集。这对于分组、透视和汇总复杂数据集特别有用。

示例:
```
arrays = [
    ['A', 'A', 'B', 'B'],
    [1, 2, 1, 2]
]
index = pd.MultiIndex.from_arrays(arrays, names=('Group', 'Subgroup'))
df = pd.DataFrame({'Value': [10, 20, 30, 40]}, index=index)
print(df)
```
输出:
```
Value
Group Subgroup
A 1 10
2 20
B 1 30
2 40
```

### 处理分层数据
在 `MultiIndex` 中访问数据使用 `.loc[]` 很简单。聚合和分组在分层结构中更容易。

示例:
```
df.loc['A']  # Access all subgroups under Group 'A'
df.groupby('Group').sum()  # Summarize by Group level
```

## 窗口函数
### 滚动操作
对滑动窗口中的数据执行计算，例如移动平均或滚动求和。

示例:
```
df['rolling_mean'] = df['Value'].rolling(window=2).mean()
```

### 扩展操作
扩展计算每个观测值之前所有数据点的指标。

示例:
```
df['expanding_sum'] = df['Value'].expanding().sum()
```

### EWM（指数加权均值）
`EWM` 给近期观测值赋予更大权重，有助于平滑时间序列数据。

示例:
```
df['ewm_mean'] = df['Value'].ewm(span=2).mean()
```

## 性能优化
### 使用向量化操作
Pandas 针对向量化操作进行了优化，其速度明显快于循环。向量化操作是指在一个操作中对整个数组或数据集执行计算，而不是遍历单个元素。

示例数据 `performance-optimization-data.csv`:
```
Value,category_col
10,A
20,B
30,A
40,C
50,B
60,A
70,C
80,B
90,A
100,C
```

示例:
```
import pandas as pd
# Load the data
df = pd.read_csv('performance-optimization-data.csv')
# Vectorized operation: square the 'Value' column
df['squared'] = df['Value'] ** 2
print(df)
```

### 使用 Pandas 避免循环
循环会减慢大型数据集的计算速度。相反，使用内置函数或 `apply()`。

```
df['new_col'] = df['Value'].apply(lambda x: x * 2)
print(df)
```

### 使用数据类型减少内存占用
将列转换为适当的数据类型以节省内存。

示例:
```
df['Value'] = df['Value'].astype('float32')
df['category_col'] = df['category_col'].astype('category')
print(df.info())
```

关键要点:
- 避免循环：使用类似 `df['column'] ** 2` 的向量化操作以加快计算速度。
- `apply()` 用法：使用 `apply()` 在不使用显式循环的情况下进行行/元素级转换。
- 内存优化：将数值列转换为较小的数据类型，例如 `float32` 或 `int8`，并将分类列转换为 `category` 类型以节省内存。

总之，像 `MultiIndexing` 和窗口函数这样的高级功能扩展了 Pandas 处理分层数据以及执行滚动或扩展操作的能力。

# 6.11 Pandas 用于数据科学工作流
Pandas 是许多数据科学工作流的核心，提供大量工具来简化 ETL 操作、探索性数据分析和数据转换流程。

## ETL（提取、转换、加载）操作
### 读取数据
Pandas 支持从各种文件格式读取数据，例如 CSV、Excel、JSON、SQL 数据库和 API。

示例数据 `ETL-Operations-Data.csv`:
```
Product,Price,Quantity
Laptop,1000,5
Phone,500,10
Tablet,300,7
Monitor,150,12
Headphones,50,20
Keyboard,25,15
Mouse,20,
```

示例:
```
import pandas as pd
df = pd.read_csv("ETL-Operations-Data.csv")
print(df)
```

### 转换数据
转换涉及清理、过滤、聚合和重构数据。

示例:
```
df['Revenue'] = df['Price'] * df['Quantity']
df = df.dropna()
print(df)
```

### 写回数据
处理后，Pandas 可以将数据导出到各种格式。

示例:
```
df.to_csv("processed_data.csv", index=False)  # Save to a CSV file
```
`df.to_csv()` 方法中的参数 `index=False` 用于排除 DataFrame 的索引不写入 CSV 文件。

流程摘要:
- 提取：数据从 `data.csv` 加载。
- 转换：通过将 `Price` 和 `Quantity` 相乘添加新的列 `Revenue`。删除 `Quantity` 列中存在缺失值的行。
- 加载：清理和转换后的数据保存到 `processed_data.csv`。

## 使用 Pandas 进行探索性数据分析（EDA）
EDA 是数据科学过程中的关键阶段，Pandas 在此阶段大放异彩，使用户能够汇总和可视化数据集。

### 生成描述性统计
`describe()` 等函数提供数据集的快速统计摘要。

示例数据 `EDA-sales-data.csv`:
```
Date,Month,Product,Revenue
2023-01-05,January,Laptop,5000
2023-01-12,January,Phone,3000
2023-01-18,January,Tablet,2000
2023-02-03,February,Laptop,4500
2023-02-14,February,Phone,3200
2023-02-28,February,Tablet,2500
2023-03-10,March,Laptop,6000
2023-03-15,March,Phone,4000
2023-03-20,March,Tablet,3000
```

示例:
```
import pandas as pd
df = pd.read_csv("EDA-sales-data.csv")
print(df.describe())
```
