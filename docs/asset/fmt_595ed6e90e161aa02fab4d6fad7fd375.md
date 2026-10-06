
可用的方法有 `Pearson`、`Kendall` 和 `spearman`。默认情况下，函数应用 `spearman`。

```python
df9 = pd.DataFrame(np.arange(8).reshape(4,2), columns=['a', 'b'])
df8.corr(df9)
```

### 功能性统计

库支持的统计方法在数据分析中非常重要。为了获取大数据对象内部的信息，我们需要如 `mean`、`sum` 等信息。Pandas 支持大量方法来计算它们。让我们考虑 `df5` 的和示例，这是一个 `DataFrame` 对象：

```python
df5.sum()
9    12
dtype: int64
```

当我们不指定 `axis` 时，默认函数将在 `axis` 上计算：

- `Series`: 不需要 `axis`。
- `DataFrame`: 列 (`axis=1`)。默认设置为 `axis=0`。

然而，我们有 `skip` 参数，允许我们排除数据。默认情况下，它是 `True`：

```python
df7.sum(skip=False)
13    18
23
dtype: float64
```

我们想要考虑的另一个函数是 `describe()`。它总结了数据结构最有信息的信息，也包括 `Series` 和 `DataFrame`：

```python
df5.describe()
count    3.000000
mean    2.000000
std     0.577350
25%    1.500000
50%    2.000000
75%    2.500000
max     3.000000
```

我们可以使用 `percentiles` 参数在输出中包含或排除百分分位数；例如，考虑：

```python
df5.describe(percentiles=[0.5, 0.8])
count    3.000000
mean    2.000000
std     0.577350
25%    1.500000
50%    2.000000
80%    2.600000
max     3.000000
```

## 函数应用

Pandas 支持函数 `apply`，允许我们把其他包（如 NumPy）支持的一些函数或我们自己的函数应用于数据结构上。在这里，我们将说明这些情况的两个示例；首先，使用 `apply` 执行 `std()` 函数，这是 NumPy 包的标准差计算函数：

```python
df5.apply(np.std, axis=1)
# default: axis=0
0    0.816497
1    0.816497
2    0.816497
dtype: float64
```

其次，如果想对 `DataFrame` 应用公式，可以遵循以下步骤：

1. 在对象上定义你想要的公式。
2. 调用定义的公式。

```python
f = lambda x: x.max() - x.min() # 步骤 1
df5.apply(f, axis=1)           # 步骤 2
0    2
1    2
2    2
dtype: int64
```

```python
def sigmoid(x):
    return 1/(1 + np.exp(x))
df5.apply(sigmoid)
0    0.500000
1    0.268941
2    0.179886
3    0.06693
```

### 排序

我们感兴趣的两种排序方法：按行或列索引排序，以及按值排序。首先，考虑按行和列排序。在这种情况下，我们有 `sort_index()` 函数。我们还有一个 `axis` 参数来设置按行还是列。`ascending` 选项 `True` 或 `False` 允许按升序或降序排序数据。默认设置为 `True`：

```python
df7 = pd.DataFrame(np.range(12).shape(3,4), columns=['b', 'd', 'c'], index=['x', 'y', 'z'])
df7
   b  d  c
x  0  1  2
y  3  4  5
z  6  7  8
df7.sort_index(axis=1)
   b  c  d
x  0  2  1
y  3  5  4
z  6  8  7
```

`Series` 有一个按值排序的 `order` 方法。对于对象中的 `NaN` 值，我们还可以通过 `na_position` 选项进行特殊处理：

```python
s4.order(na_position='first')
024    NaN
065    NaN
002    May
001    Nam
```

基于此，`Series` 也有按值排序的 `sort()`。然而，该函数不会返回排序后数据的副本：

```python
s4.sort(na_position='first')
```

### 处理缺失数据

在本部分，我们将讨论 Pandas 数据结构中的缺失值、`NaN` 或空值。对象中存在缺失数据是非常常见的情况。一种创建缺失数据的情况是重索引：

```python
df8 = pd.DataFrame(np.range(12).shape(4,3), columns=['a', 'b', 'c'])
df9 = df8.index(columns=['a', 'b', 'd'])
df9
   a  b  c  d
0  0  1  2  NaN
1  3  4  5  NaN
2  6  7  8  NaN
3  9 10 11 NaN
```

为了处理缺失值，我们使用 `isnull()` 或 `null()` 来检测 `Series` 以及 `DataFrame` 中的缺失值：

```python
df10.isnull()
a    False
b    False
c    False
:
dtype: bool
```

在 `Series` 上，我们可以使用 `dropna` 函数丢弃所有空数据和索引值：

```python
s4 = pd.Series({'001': 'nam', '002': 'May', '003': 'ter'}, index=['002', '001', '024', '065'])
s4.dropna()
```

对于 `DataFrame` 对象，比 `Series` 稍微复杂。我们可以告诉我们要删除哪些行或列，以及所有条目必须为空，或者一个空值就足够。默认情况下，函数将删除任何包含缺失值的行：

```python
df9.dropna() # 删除所有行
df9.dropna(axis=1) # 删除列
```

控制缺失值的另一种方法是使用我们在上一节介绍的函数参数。它们对于解决这个问题非常有用。根据我们的经验，在创建数据对象时，在缺失情况下应该分配一个固定值：

```python
df7 = df5.add(fill_value=0)
```

### 索引和标签

对于 `DataFrame` 行的标签索引，我们使用 `ix` 函数。它允许我们选择一组行和列。有两个参数我们需要指定：我们想要获取的行和列标签。默认情况下，如果我们不指定选定的列名，函数将返回对象中所有列的行：

```python
df5.ix[0]
a    0
b    1
c    2
Name: 0, dtype: int64
df5.ix[0, 1:3]
b    1
c    2
Name: 0, dtype: int64
```

如果数据对象是 `DataFrame`，我们也可以以类似的方式进行：

```python
df5[['b', 'c']]
   b  c
0  1  2
1  4  5
2  7  8
```

## 计算工具

从两个数据对象之间的相关性和协方差开始。`Series` 和 `DataFrame` 都有 `cov` 方法。在 `DataFrame` 对象上，此方法将计算对象内部 `Series` 之间的协方差：

```python
s1 = pd.Series(np.random.rand(3))
s1
0    0.460324
1    0.993279
2    0.032957
dtype: float64
s2 = pd.Series(np.random.rand(3))
s2
0    0.777509
1    0.573716
2    0.664212
dtype: float64
s1.cov(s2)
-0.0245136015904524
```

```python
df8 = pd.DataFrame(np.random.rand(12).shape(4,3), columns=['a', 'b', 'c'])
df8
         a        b        c
0  0.200049 0.070034 0.978615
1  0.293063 0.609812 0.78873
2  0.853431 0.243656 0.978057
3  0.500765 0.48180
```

### 相关方法的使用

`corr` 方法类似于 `cov`。它计算数据对象内部 `Series` 之间的相关性，如果数据对象是 `DataFrame`。然而，我们需要指定使用哪种方法进行相关：

```python
df8.corr(method='spearman')
```

可用的方法有 `Pearson`、`Kendall` 和 `spearman`。默认情况下，函数应用 `spearman`。

```python
df9 = pd.DataFrame(np.arange(8).reshape(4,2), columns=['a', 'b'])
df8.corr(df9)
```

### 功能性统计

库支持的统计方法在数据分析中非常重要。为了获取大数据对象内部的信息，我们需要如 `mean`、`sum` 等信息。Pandas 支持大量方法来计算它们。让我们考虑 `df5` 的和示例，这是一个 `DataFrame` 对象：

```python
df5.sum()
9    12
dtype: int64
```

当我们不指定 `axis` 时，默认函数将在 `axis` 上计算：

- `Series`: 不需要 `axis`。
- `DataFrame`: 列 (`axis=1`)。默认设置为 `axis=0`。

然而，我们有 `skip` 参数，允许我们排除数据。默认情况下，它是 `True`：

```python
df7.sum(skip=False)
13    18
23
dtype: float64
```

我们想要考虑的另一个函数是 `describe()`。它总结了数据结构最有信息的信息，也包括 `Series` 和 `DataFrame`：

```python
df5.describe()
count    3.000000
mean    2.000000
std     0.577350
25%    1.500000
50%    2.000000
75%    2.500000
max     3.000000
```

我们可以使用 `percentiles` 参数在输出中包含或排除百分分位数；例如，考虑：

```python
df5.describe(percentiles=[0.5, 0.8])
count    3.000000
mean    2.000000
std     0.577350
25%    1.500000
50%    2.000000
80%    2.600000
max     3.000000
```

## 函数应用

Pandas 支持函数 `apply`，允许我们把其他包（如 NumPy）支持的一些函数或我们自己的函数应用于数据结构上。在这里，我们将说明这些情况的两个示例；首先，使用 `apply` 执行 `std()` 函数，这是 NumPy 包的标准差计算函数：

```python
df5.apply(np.std, axis=1)
# default: axis=0
0    0.816497
1    0.816497
2    0.816497
dtype: float64
```

其次，如果想对 `DataFrame` 应用公式，可以遵循以下步骤：

1. 在对象上定义你想要的公式。
2. 调用定义的公式。

```python
f = lambda x: x.max() - x.min() # 步骤 1
df5.apply(f, axis=1)           # 步骤 2
0    2
1    2
2    2
dtype: int64
```

```python
def sigmoid(x):
    return 1/(1 + np.exp(x))
df5.apply(sigmoid)
0    0.500000
1    0.268941
2    0.179886
3    0.06693
```

### 排序

我们感兴趣的两种排序方法：按行或列索引排序，以及按值排序。首先，考虑按行和列排序。在这种情况下，我们有 `sort_index()` 函数。我们还有一个 `axis` 参数来设置按行还是列。`ascending` 选项 `True` 或 `False` 允许按升序或降序排序数据。默认设置为 `True`：

```python
df7 = pd.DataFrame(np.range(12).shape(3,4), columns=['b', 'd', 'c'], index=['x', 'y', 'z'])
df7
   b  d  c
x  0  1  2
y  3  4  5
z  6  7  8
df7.sort_index(axis=1)
   b  c  d
x  0  2  1
y  3  5  4
z  6  8  7
```

`Series` 有一个按值排序的 `order` 方法。对于对象中的 `NaN` 值，我们还可以通过 `na_position` 选项进行特殊处理：

```python
s4.order(na_position='first')
024    NaN
065    NaN
002    May
001    Nam
```

基于此，`Series` 也有按值排序的 `sort()`。然而，该函数不会返回排序后数据的副本：

```python
s4.sort(na_position='first')
```

### 处理缺失数据

在本部分，我们将讨论 Pandas 数据结构中的缺失值、`NaN` 或空值。对象中存在缺失数据是非常常见的情况。一种创建缺失数据的情况是重索引：

```python
df8 = pd.DataFrame(np.range(12).shape(4,3), columns=['a', 'b', 'c'])
df9 = df8.index(columns=['a', 'b', 'd'])
df9
   a  b  c  d
0  0  1  2  NaN
1  3  4  5  NaN
2  6  7  8  NaN
3  9 10 11 NaN
```

为了处理缺失值，我们使用 `isnull()` 或 `null()` 来检测 `Series` 以及 `DataFrame` 中的缺失值：

```python
df10.isnull()
a    False
b    False
c    False
:
dtype: bool
```

在 `Series` 上，我们可以使用 `dropna` 函数丢弃所有空数据和索引值：

```python
s4 = pd.Series({'001': 'nam', '002': 'May', '003': 'ter'}, index=['002', '001', '024', '065'])
s4.dropna()
```

对于 `DataFrame` 对象，比 `Series` 稍微复杂。我们可以告诉我们要删除哪些行或列，以及所有条目必须为空，或者一个空值就足够。默认情况下，函数将删除任何包含缺失值的行：

```python
df9.dropna() # 删除所有行
df9.dropna(axis=1) # 删除列
```

控制缺失值的另一种方法是使用我们在上一节介绍的函数参数。它们对于解决这个问题非常有用。根据我们的经验，在创建数据对象时，在缺失情况下应该分配一个固定值：

```python
df7 = df5.add(fill_value=0)
```

### 索引和标签

对于 `DataFrame` 行的标签索引，我们使用 `ix` 函数。它允许我们选择一组行和列。有两个参数我们需要指定：我们想要获取的行和列标签。默认情况下，如果我们不指定选定的列名，函数将返回对象中所有列的行：

```python
df5.ix[0]
a    0
b    1
c    2
Name: 0, dtype: int64
df5.ix[0, 1:3]
b    1
c    2
Name: 0, dtype: int64
```

如果数据对象是 `DataFrame`，我们也可以以类似的方式进行：

```python
df5[['b', 'c']]
   b  c
0  1  2
1  4  5
2  7  8
```

# 数据可视化

数据可视化关注于以图像或图表形式呈现数据。它是数据分析中最重要的任务之一，因为我们可以让我们能够看到分析结果、检测离群值并为模型构建做出决策。有很多 Python 可视化库，其中 `Matplotlib`、`seaborn`、`bokeh` 和 `plotly` 是最流行的。然而，在本章中，我们主要关注在许多不同场景下被广泛使用的 `Matplotlib` 库。

![数据可视化的图像结果](img/image3860.jpg)

Matplotlib 能够生成多种格式的出版级图表，以及跨 Python 平台的交互式环境。另一个优势是 Pandas 配备了对几个 Matplotlib 绘图程序的实用封装器，允许快速方便地对 `Series` 和 `DataFrame` 对象进行绘图。

IPython 包最初是标准交互式 Python Shell 的替代品，但从以后已变为数据探索、可视化和快速原型设计不可或缺的工具。可以通过各种选项从 `IPython` 中使用 `matplotlib` 提供的图形功能，其中最容易上手的方法是内联标记：`python --inline`。该标记将重新加载 `matplotlib` 和 `NumPy` 以供默认 `matplotlib` 后端交互式使用。IPython 可以在各种环境中运行：终端、Qt 应用程序或浏览器内部。这些选项值得探索，因为 `IPython` 已用于许多用例，例如原型设计、更具吸引力的会议演讲或课程的交互式幻灯片，以及共享研究的工具。

## Matplotlib API 入门

使用 `matplotlib` 开始绘图的最简单方法是通过该包支持的 MATLAB API：

```python
import matplotlib.pyplot as plt
from numpy import *
x = linspace(0, 3, 6)
x = array([0., 0.6, 1.2, 1.8, 2.4, 3.])
y = power(x, 2)
y = array([0., 0.36, 1.24, 5.76, 9.])
figure()
plt(x, y, 'r')
plt.xlabel('x')
plt.ylabel('y')
title('Data visualization in MATLAB-like')
plt.show()
```

然而，不应使用 `import *` 是有充分理由的。在 `matplotlib` 的情况下，我们可以使用以下导入：

```python
import matplotlib.pyplot as plt
plt.plot(x, y)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Data visualization using Plot')
plt.show()
```

如果我们只给 `plot` 函数提供一个参数，它将自动将其用作 y 值，并从 0 到 `N-1` 生成 x 值，其中 `N` 是值的数量：

```python
plt.plot(y)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Plot y without x values')
plt.show()
```

默认情况下，轴的范围受输入的 x 和 y 数据的限制。如果我们想指定轴的视图，可以使用 `axes()` 方法设置范围。例如，在之前的可视化中，我们可以通过编写以下命令将 x 轴范围从 `[0, 5]` 增加到 `[0, 6]`，并将 y 轴范围从 `[0, 9]` 增加到 `[0, 10]`：

```python
plt.axes([0, 6, 0, 10])
```

### 线条属性
