
![](img/c2ad4b400bf63af9804b2d44510f76a6_46_0.png)

图 4.1：来源： http://www.scipy-lectures.org

```
[20 21 22]
[30 31 32]]
```

## 示例

操作数 A、B 和结果的形状：

```
A      (2d array):  5 x 4
B      (1d array):     1
Result (2d array):  5 x 4

A      (2d array):  5 x 4
B      (1d array):     4
Result (2d array):  5 x 4

A      (3d array): 15 x 3 x 5
B      (3d array): 15 x 1 x 5
Result (3d array): 15 x 3 x 5

A      (3d array): 15 x 3 x 5
B      (2d array):     3 x 5
Result (3d array): 15 x 3 x 5

A      (3d array): 15 x 3 x 5
B      (2d array):     3 x 1
Result (3d array): 15 x 3 x 5
```

## 4.8 练习

给定数组：

```
X = np.random.randn(4, 2) # random normals in 4x2 array
```

- 对于每一列，找到最小值的行索引。
- 编写一个函数 standardize(X)，使其返回列居中并缩放（按标准差）的数组。

脚本总运行时间：( 0 分钟 0.008 秒)

注意：点击此处下载完整示例代码

## PANDAS：数据操作

常说数据分析的 80% 时间花在清理上，以及使用 Pandas 进行数据操作和清理这一虽小但重要的方面。

## 来源：

- Kevin Markham: https://github.com/justmarkham
- Pandas 文档: http://pandas.pydata.org/pandas-docs/stable/index.html

## 数据结构

- **Series** 是一个一维的带标签数组，能够容纳任何数据类型（整数、字符串、浮点数、Python 对象等）。轴标签统称为索引。创建 Series 的基本方法是调用 *pd.Series([1,3,5,np.nan,6,8])*
- **DataFrame** 是一个二维的带标签数据结构，其列可能具有不同的类型。你可以把它想象成电子表格或 SQL 表，或 Series 对象的字典。它源自 R 的 *data.frame()* 对象。

```
from __future__ import print_function

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

## 5.1 创建 DataFrame

```
columns = ['name', 'age', 'gender', 'job']

user1 = pd.DataFrame([['alice', 19, "F", "student"],
    ['john', 26, "M", "student"]],
    columns=columns)

user2 = pd.DataFrame([['eric', 22, "M", "student"],
    ['paul', 58, "F", "manager"]],
    columns=columns)

user3 = pd.DataFrame(dict(name=['peter', 'julie'],
    age=[33, 44], gender=['M', 'F'],
    job=['engineer', 'scientist']))

print(user3)
```

输出：

|   | 名称 | 年龄 | 性别 | 工作 |
|---|---|---|---|---|
| 0 | peter | 33 | M | engineer |
| 1 | julie | 44 | F | scientist |

## 5.2 合并 DataFrames

## 5.2.1 拼接 DataFrame

```
```python
user1.append(user2)
users = pd.concat([user1, user2, user3])
print(users)
```
```

输出：

|   | 名称 | 年龄 | 性别 | 工作 |
|---|---|---|---|---|
| 0 | alice | 19 | F | student |
| 1 | john | 26 | M | student |
| 0 | eric | 22 | M | student |
| 1 | paul | 58 | F | manager |
| 0 | peter | 33 | M | engineer |
| 1 | julie | 44 | F | scientist |

## 5.2.2 连接 DataFrame

```
```python
user4 = pd.DataFrame(dict(name=['alice', 'john', 'eric', 'julie'],
                         height=[165, 180, 175, 171]))
print(user4)
```
```

输出：

|   | 名称 | 身高 |
|---|---|---|
| 0 | alice | 165 |
| 1 | john | 180 |
| 2 | eric | 175 |
| 3 | julie | 171 |

使用两个数据帧键的交集

```
```python
merge_inter = pd.merge(users, user4, on="name")
print(merge_inter)
```
```

输出：

|   | 名称 | 年龄 | 性别 | 工作 | 身高 |
|---|---|---|---|---|---|
| 0 | alice | 19 | F | student | 165 |
| 1 | john | 26 | M | student | 180 |
| 2 | eric | 22 | M | student | 175 |
| 3 | julie | 44 | F | scientist | 171 |

使用两个数据帧键的并集

```
users = pd.merge(users, user4, on="name", how='outer')
print(users)
```

输出：

| 名称 | 年龄 | 性别 | 工作 | 身高 |
|---|---|---|---|---|
| alice | 19 | F | student | 165.0 |
| john | 26 | M | student | 180.0 |
| eric | 22 | M | student | 175.0 |
| paul | 58 | F | manager | NaN |
| peter | 33 | M | engineer | NaN |
| julie | 44 | F | scientist | 171.0 |

## 5.2.3 通过透视重塑

“取消透视”将 DataFrame 从宽格式重塑为长（堆叠）格式，

```
staked = pd.melt(users, id_vars="name", var_name="variable", value_name="value")
print(staked)
```

输出：

| 名称 | 变量 | 值 |
|---|---|---|
| alice | age | 19 |
| john | age | 26 |
| eric | age | 22 |
| paul | age | 58 |
| peter | age | 33 |
| julie | age | 44 |
| alice | gender | F |
| john | gender | M |
| eric | gender | M |
| paul | gender | F |
| peter | gender | M |
| julie | gender | F |
| alice | job | student |
| john | job | student |
| eric | job | student |
| paul | job | manager |
| peter | job | engineer |
| julie | job | scientist |
| alice | height | 165 |
| john | height | 180 |
| eric | height | 175 |
| paul | height | NaN |
| peter | height | NaN |
| julie | height | 171 |

“透视”将 DataFrame 从长（堆叠）格式重塑为宽格式，

```
print(staked.pivot(index='name', columns='variable', values='value'))
```

输出：

| 名称 | 年龄 | 性别 | 身高 | 工作 |
|---|---|---|---|---|
| alice | 19 | F | 165 | student |
| eric | 22 | M | 175 | student |
| john | 26 | M | 180 | student |
| julie | 44 | F | 171 | scientist |
| paul | 58 | F | NaN | manager |
| peter | 33 | M | NaN | engineer |

## 5.3 汇总

```
```python
# examine the users data

users                 # print the first 30 and last 30 rows
type(users)           # DataFrame
users.head()          # print the first 5 rows
users.tail()          # print the last 5 rows

users.index           # "the index" (aka "the labels")
users.columns         # column names (which is "an index")
users.dtypes          # data types of each column
users.shape           # number of rows and columns
users.values          # underlying numpy array
users.info()          # concise summary (includes memory usage as of pandas 0.15.0)
```
```

输出：

```
```
<class 'pandas.core.frame.DataFrame'>
Int64Index: 6 entries, 0 to 5
Data columns (total 5 columns):
name      6 non-null object
age       6 non-null int64
gender    6 non-null object
job       6 non-null object
height    4 non-null float64
dtypes: float64(1), int64(1), object(3)
memory usage: 288.0+ bytes
```
```

## 5.4 列选择

```
```python
users['gender']            # select one column
type(users['gender'])      # Series
users.gender               # select one column using the DataFrame

# select multiple columns
users[['age', 'gender']]   # select two columns
my_cols = ['age', 'gender'] # or, create a list...
users[my_cols]             # ...and use that list to select columns
type(users[my_cols])       # DataFrame
```
```

## 5.5 行选择（基础）

iloc 严格基于整数位置

```
df = users.copy()
df.iloc[0]      # first row
df.iloc[0, 0] # first item of first row
df.iloc[0, 0] = 55

for i in range(users.shape[0]):
    row = df.iloc[i]
    row.age *= 100 # setting a copy, and not the original frame data.

print(df)  # df is not modified
```

输出：

| 名称 | 年龄 | 性别 | 工作 | 身高 |
|---|---|---|---|---|
| 55 | 19 | F | student | 165.0 |
| john | 26 | M | student | 180.0 |
| eric | 22 | M | student | 175.0 |
| paul | 58 | F | manager | NaN |
| peter | 33 | M | engineer | NaN |
| julie | 44 | F | scientist | 171.0 |

ix 支持混合整数和标签访问。

```
df = users.copy()
df.ix[0]            # first row
df.ix[0, "age"] # first item of first row
df.ix[0, "age"] = 55

for i in range(df.shape[0]):
    df.ix[i, "age"] *= 10

print(df)  # df is modified
```

输出：

| 名称 | 年龄 | 性别 | 工作 | 身高 |
|---|---|---|---|---|
| alice | 550 | F | student | 165.0 |
| john | 260 | M | student | 180.0 |
| eric | 220 | M | student | 175.0 |
| paul | 580 | F | manager | NaN |
| peter | 330 | M | engineer | NaN |
| julie | 440 | F | scientist | 171.0 |

## 5.6 行选择（过滤）

简单逻辑过滤

```
users[users.age < 20]      # only show users with age < 20
young_bool = users.age < 20  # or, create a Series of booleans...
young = users[young_bool]           # ...and use that Series to filter rows
```

75%    41.250000  176.250000
max    58.000000  180.000000

## 汇总所有列

```
print(df.describe(include='all'))
print(df.describe(include=['object']))  # limit to one (or more) types
```

输出：

```
name    age gender    job    height
count    6  6.000000    6      6  4.000000
unique   6  NaN        2      4  NaN
top      peter NaN    M student NaN
freq     1  NaN        3      3  NaN
mean     NaN 33.666667 NaN    NaN 172.750000
std      NaN 14.895189 NaN    NaN 6.344289
min      NaN 19.000000 NaN    NaN 165.000000
25%      NaN 23.000000 NaN    NaN 169.500000
50%      NaN 29.500000 NaN    NaN 173.000000
75%      NaN 41.250000 NaN    NaN 176.250000
max      NaN 58.000000 NaN    NaN 180.000000
        name gender    job
count    6    6      6
unique   6    2      4
top      peter M      student
freq     1    3      3
```

## 按组统计（groupby）

```
print(df.groupby("job").mean())
print(df.groupby("job")["age"].mean())
print(df.groupby("job").describe(include='all'))
```

输出：

age    height
job
engineer 33.000000 NaN
manager 58.000000 NaN
scientist 44.000000 171.000000
student 22.333333 173.333333
job
engineer 33.000000
manager 58.000000
scientist 44.000000
student 22.333333
Name: age, dtype: float64
        name    age
→ ... gender    height
        count unique top freq mean std min 25% 50% 75% max count unique top
→freq ... 25% 50% 75% max count unique top freq mean std min
→25% 50% 75% max
job
→ ...

