
每季的成本以及每季度的收入。
列表 3.7 的输出如下：

整个数据集：

| | 成本 | 季度 | 收入 |
|---|---|---|---|
| 0 | 23500 | Q1 | 40000 |
| 1 | 34000 | Q2 | 60000 |
| 2 | 57000 | Q3 | 50000 |
| 3 | 32000 | Q4 | 30000 |

```python
Quarter:
0 Q1
1 Q2
2 Q3
3 Q4
Name: Quarter, dtype: object
Cost:
0 23500
1 34000
2 57000
3 32000
Name: Cost, dtype: int64
Revenue:
0 40000
1 60000
2 50000
3 30000
Name: Revenue, dtype: int64
```

## 使用 PANDAS DATAFRAM 进行数据操作 (2)

在本节中，让我们假设有一家两人的公司，按季度跟踪收支，我们想要计算每个季度的利润/亏损，以及整体的利润/亏损。

列表 3.8 显示了 `pandas-quarterly-df1.py` 的内容，展示了如何定义一个包含收入相关值的 Pandas DataFrame。

### 列表 3.8：pandas-quarterly-df2.py

```python
import pandas as pd

summary = {
    'Quarter': ['Q1', 'Q2', 'Q3', 'Q4'],
    'Cost': [-23500, -34000, -57000, -32000],
    'Revenue': [40000, 40000, 40000, 40000]
}

df = pd.DataFrame(summary)
print("First Dataset:\n",df)

df['Total'] = df.sum(axis=1)
print("Second Dataset:\n",df)
```

列表 3.8 定义了变量 `summary`，它包含了我们这家两人的公司成本和收入的季度信息。变量 `df` 是基于 `summary` 变量中数据的 Pandas DataFrame。三个 `print` 语句显示了季度、每季成本和每季收入。
列表 3.8 的输出为：

第一个数集:
| | 成本 | 季度 | 收入 |
|---|---|---|---|
| 0 | -23500 | Q1 | 40000 |
| 1 | -34000 | Q2 | 60000 |
| 2 | -57000 | Q3 | 50000 |
| 3 | -32000 | Q4 | 30000 |

第二个数据集:
| | 成本 | 季度 | 收入 |

## 使用 PANDAS DATAFRAM 进行数据操作 (3)

让我们从与上一节相同的假设开始：我们有一家两人的公司，按季度跟踪收支，我们想要计算每个季度的利润/亏损，以及整体的利润/亏损。此外，我们还想计算列总和行行总。

列表 3.9 显示了 `pandas-quarterly-df1.py` 的内容，展示了如何定义一个包含收入相关值的 Pandas DataFrame。

### 列表 3.9：pandas-quarterly-df3.py

```python
import pandas as pd
summary = {
    'Quarter': ['Q1', 'Q2', 'Q3', 'Q4'],
    'Cost': [-23500, -34000, -57000, -32000],
    'Revenue': [40000, 40000, 40000, 40000]
}

df = pd.DataFrame(summary)
print("First Dataset:\n",df)

df['Total'] = df.sum(axis=1)
df.loc['Sum'] = df.sum()
print("Second Dataset:\n",df)

# or df.loc['avg'] / 3
df.loc['avg'] = df[:3].mean()
```

```python
#print("Third Dataset:\n",df)
```

列表 3.9 定义了变量 `summary`，它包含了我们这家两人的公司成本和收入的季度信息。变量 `df` 是基于 `summary` 变量中数据的 Pandas DataFrame。三个 `print` 语句显示了季度、每季成本和每季收入。列表 3.9 的输出如下：

#### 第一个数据集：

| | 成本 | 季度 | 收入 |
|---|---|---|---|
| 0 | -23500 | Q1 | 40000 |
| 1 | -34000 | Q2 | 60000 |
| 2 | -57000 | Q3 | 50000 |
| 3 | -32000 | Q4 | 30000 |

#### 第二个数据集：

| | 成本 | 季度 | 收入 | 总计 |
|---|---|---|---|---|
| 0 | -23500 | Q1 | 40000 | 16500 |
| 1 | -34000 | Q2 | 60000 | 26000 |
| 2 | -57000 | Q3 | 50000 | -7000 |
| 3 | -32000 | Q4 | 30000 | -2000 |
| Sum | -146500 | Q1Q2Q3Q4 | 180000 | 33500 |

## PANDAS DATAFRAMES 与 CSV 文件

在之前的几个节中的代码示例在 Python 脚本中包含了硬编码的数据。然而，从 CSV 文件读取数据也是非常常见的。你可以使用 Python 的 `CSV.reader()` 函数、`NumPy.loadtxt()` 函数或 Pandas 的 `read_csv()` 函数（本节所示）来读取 CSV 文件的内容。

列表 3.10 显示了 `weather-data.py` 的内容，展示了如何读取 CSV 文件、使用该 CSV 文件的内容初始化 Pandas DataFrame，并显示 Pandas DataFrame 中的各种子集。

### 列表 3.10：weather-data.py

```python
import pandas as pd

df = pd.read_csv("weather_data.csv")

print(df)
print(df.shape)  # 行，列
print(df.head()) # df(3)
print(df.tail())
print(df[1:3])
print(df.columns)
print(type(df))
print(df[['day', 'temperature']])
print(df['temperature'].max())
```

列表 3.10 调用 Pandas 的 `read_csv()` 函数读取 `weather_data.csv` 文件的内容，随后用一组 `print()` 语句显示文件的不同部分。列表 3.10 的输出如下：

```
day, temperature, windspeed
7/1/2018, 42, Rain
7/2/2018, 45, Sunny
7/3/2018, 78, Snow
7/4/2018, 74, Snow
7/5/2018, 42, Rain
7/6/2018, 51, Sunny
```

在某些情况下，你可能需要根据应用于列值的条件的布尔逻辑来“过滤出”某些行数据。

列表 3.11 显示了 `people.csv` 文件的内容，列表 3.12 显示了 `people-pandas.py` 的内容，展示了如何定义一个读取 CSV 文件并处理数据的 Pandas DataFrame。

### 列表 3.11：people.csv

```
fname, age, country
john, smith, 30, usa
jane, smith, 31, france
jack, jones, 32, france
dave, stone, 33, france
sara, stein, 34, france
ed, bower, 35, france
```

### 列表 3.12：people-pandas.py

```python
import pandas as pd
df = pd.read_csv('people.csv')
df.info()
print('fname:')
print(df['fname'])
print('----------------------')
print('age:')
print(df['age'] > 33)
print('----------------------')
print('age over 33:')
myfilter = df['age'] > 33
print(df[myfilter])
```

列表 3.12 用 `people.csv` 的内容填充 Pandas `df`。列表 3.12 的后续部分显示了 `df` 的结构，然后是所有人的名字。后续部分显示了包含 True 或 False 的行列表，取决于人员是否大于 33 或最多 33。列表 3.12 的最后部分显示了所有超过 33 岁的人的列表。列表 3.12 的输出为：

```python
myfilter = df['age'] > 33
<class 'pandas.core.frame.DataFrame'>
Index: 6 entries, 0 to 5
Data columns (5):
fname     6 non-null object
age      6 non-null int64
gender   6 non-null object
country  6 non-null object
dtypes: object
memory usage: 320.0+ bytes

fname:
0 john
1 jane
2 jack
3 dave
4 sara
5 eddy
Name: fname, dtype: object
age over 33:
0 False
1 False
2 False
3 False
4 True
5 True
Name: age, dtype: bool
```

age over 33:

| | fname | age | country |
|---|---|---|---|
| 4 | sara stein | 34 | france |
| 5 | eddy bower | 35 | france |

## PANDAS DATAFRAMES 与 Excel 表格 (1)

列表 3.13 显示了 `people-xlsx.py` 的内容，展示了如何从 Excel 表格读取数据并使用这些数据创建 Pandas DataFrame。

### 列表 3.13：people-xlsx.py

```python
import pandas as pd

df = pd.read_excel("people.xlsx")
print("Contents of Excel spreadsheet:")
print(df)
```

列表 3.13 非常简单：通过 Pandas 的 `read_excel()` 函数使用 `people.xlsx` 表格（内容与 `people.csv` 相同）初始化 Pandas dataframe。列表 3.13 的输出为：

| | fname | age | country |
|---|---|---|---|
| 0 | john smith | 30 | usa |
| 1 | jane smith | 31 | france |
| 2 | jack jones | 32 | france |
| 3 | dave stone | 33 | france |
| 4 | sara stein | 34 | france |
| 5 | eddy bower | 35 | france |

## PANDAS DATAFRAMES 与 Excel 表格 (2)

列表 3.14 显示了 `employees-xlsx.py` 的内容，展示了如何从 Excel 表格读取数据并使用这些数据创建 Pandas DataFrame。

### 列表 3.14：employees-xlsx.py

```python
import pandas as pd

df = pd.read_excel("employees.xlsx")
print("Contents of Excel spreadsheet:")
print(df)
```

