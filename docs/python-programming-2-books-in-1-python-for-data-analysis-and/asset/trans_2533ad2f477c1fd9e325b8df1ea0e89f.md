
ax.legend()

![](img/fe3427740784586362e0a35d3200b425_218_0.png)

## 直方图

“hist” 方法可用于在 matplotlib 中生成直方图。下面的示例代码允许传递类别数据，例如“酒评”数据集中的 points 列，以自动计算每个类别的出现次数。

```
# creation of figure and axis
fig, ax = plt.subplots()
# plotting histogram
ax.hist(wine_reviews['points'])
# setting title and labels
ax.set_title('Wine Review Scores')
ax.set_xlabel('Points')
ax.set_ylabel('Frequency')
```

![](img/fe3427740784586362e0a35d3200b425_219_0.png)

## 柱状图

“bar” 方法可用于在 matplotlib 中生成柱状图。这些图表无法自动计算每个类别的出现次数，因此需要使用 Pandas 库的“value_counts” 函数。任何类别种类不多的类别数据都可以轻松使用柱状图绘制。但是，包含超过 30 个类别的数据集过于复杂，无法生成易于理解的柱状图。下面的示例代码将使用“value_counts” 函数从“酒评”数据集中创建柱状图。

```
# creation of figure and axis
fig, ax = plt.subplots()
# counting the occurrence of each class
data = wine_reviews['points'].value_counts()
# getting x and y data
points = data.index
frequency = data.values
# creation of bar chart
ax.bar(points, frequency)
# setting title and labels
ax.set_title('Wine Review Scores')
ax.set_xlabel('Points')
ax.set_ylabel('Frequency')
```

![](img/fe3427740784586362e0a35d3200b425_220_0.png)

## Pandas

Pandas 提供直观且用户友好的高级数据结构。“Pandas” 在机器学习算法开发者社区中广受欢迎，内置了数据聚合、分组和过滤技术，以及时间序列分析结果。Pandas 库有两种主要结构：一维“Series” 和二维“DataFrame”。

“Pandas” 提供的部分关键特性如下：

- 一个带有内嵌索引的快速高效的“DataFrame 对象”，用于数据操作活动。
- 用于在内存数据结构与多种文件格式之间读写数据的工具，例如“CSV”和文本、“Microsoft Excel”、“SQL 数据库”以及快速的“HDF5 格式”。
- 通过实现自动标签驱动的计算对齐，实现智能数据对齐和不完整数据的集成管理，并能轻松将无序数据整理成有序形式。
- 数据集的灵活重构和透视。
- 对大型数据集进行基于标签的智能切片和索引，以及创建数据子集。
- 可以向数据结构添加或删除列，以实现所需的数据库大小。
- 使用先进的“Group By” 系统对数据进行聚合或转换，使数据上的“split-apply-combine” 技术得以执行。
- 数据集的高效合并和连接函数。
- “层级轴索引” 提供了一种在低维数据结构中处理高维数据的简单方法。
- 时间序列功能，包括“日期范围生成和频率转换、移动窗口统计、移动窗口线性回归、日期移位和滞后”。还可创建“领域特定时间偏移”，并能无数据损失地连接时间序列。
- 由于大部分底层代码使用“Cython” 或“C”，Pandas 拥有高性能和高效率。
- Python 与 Pandas 结合，广泛应用于多个学术和工业领域，包括金融服务、统计学、神经生物学、经济学、市场营销与广告、在线数据分析等。

Pandas 提供的两种数据结构是：“Pandas DataFrame” 和 “Pandas Series”。

## Pandas DataFrame

它被定义为“带有可能不同类型列的二维标记数据结构”。它与 Excel 电子表格高度相似，如下图所示，具有多个相似功能，用于从数据中进行分析、修改和提取有价值的见解。您可以通过输入来自“Excel”、“CSV”、“MySQL 数据库”等的数据集来创建“Pandas DataFrame”。

| | NAME | AGE | DESIGNATION |
|---|---|---|---|
| 1 | a | 20 | VP |
| 2 | b | 27 | CEO |
| 3 | c | 35 | CFO |
| 4 | d | 55 | VP |
| 5 | e | 18 | VP |
| 6 | f | 21 | CEO |
| 7 | g | 35 | MD |

例如，在上图中，假设“Keys”由列名表示，“Values”由该列中的项目列表表示，可以使用“Python 字典”来表示，如下面的代码所示：

```
my_dict = {
    'name': ["a", "b", "c", "d", "e", "f", "g"],
    'age': [20, 27, 35, 55, 18, 21, 35],
    'designation': ["VP", "CEO", "CFO", "VP", "VP", "CEO", "MD"]
}
```

可以使用下面的代码从这个字典创建“Pandas DataFrame”：

```
import pandas as pd
df = pd.DataFrame(my_dict)
```

生成的“DataFrame”如下图所示，类似于 Excel 电子表格：

|   | age | designation | name |
|---|---|---|---|
| 0 | 20 | VP | a |
| 1 | 27 | CEO | b |
| 2 | 35 | CFO | c |
| 3 | 55 | VP | d |
| 4 | 18 | VP | e |
| 5 | 21 | CEO | f |
| 6 | 35 | MD | g |

如果您想为行定义索引值，则需要像下面这样在“DataFrame ()” 子句中添加“index” 参数：

```
df = pd.DataFrame(my_dict, index=[1, 2, 3, 4, 5, 6, 7])
```

要获取“字符串”索引而不是数字索引，请使用下面的代码：

```
df = pd.DataFrame(
    my_dict,
    index=["First", "Second", "Third", "Fourth", "Fifth", "Sixth",
           "Seventh"]
)
```

现在，由于这些索引值是统一的，您可以执行下面的代码来使用“NumPy 数组”作为索引值：

```
np_arr = np.array([10, 20, 30, 40, 50, 60, 70])
df = pd.DataFrame(my_dict, index=np_arr)
```

类似于“NumPy”，“DataFrame” 的列也是同质的。
您可以使用类似字典的语法，或在“DataFrame”中添加列名，来查看列的数据类型，如下面的代码所示：

```
df['age'].dtype  # Dict Like Syntax
df.age.dtype  # DataFrame.ColumnName
df.name.dtype  # DataFrame.ColumnName
```

您可以使用下面的代码，使用“head ( )” 函数查看前五行，使用“tail ( )” 函数查看后五行，从而有选择地查看“Pandas DataFrame” 中可用的记录或行。例如，使用下面的代码查看数据的前 3 行：

```
df.head(3)  # Display first 3 Rows
```

## Pandas Series

它可以定义为“一种一维标记数组，能够存储任何类型的数据（整数、字符串、浮点数、Python 对象）”。简单来说，它就像 Excel 电子表格中的一列。要从数组生成“Pandas Series”，必须导入“NumPy” 模块，并与“array ()” 函数一起使用，如下面的代码所示：

```
import pandas as pd
import numpy as np

# simple array
data = np.array(['m', 'a', 'c', 'h', 'T', 'n', 'e'])
ser = pd.Series(data)
print(ser)
```

## 使用散点图进行数据可视化

散点图可以定义为“一种二维数据可视化，使用点来表示两个不同变量获得的值——一个沿 x 轴绘制，另一个沿 y 轴绘制”。它也被称为“散点图”或“散点图表”。例如，下图中看到的“散点图”描绘了一组儿童身高和体重的虚构测量值。图中的每个“点”都用于表示一个人，其身高沿“x 轴” 测量，体重沿“y 轴” 测量。

![](img/fe3427740784586362e0a35d3200b425_225_0.png)
