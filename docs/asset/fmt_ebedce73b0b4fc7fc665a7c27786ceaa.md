
- `Dtype`：代表数组内元素的数据类型：

`>>> n_array.dtype.name`

`Int64`

## 数学运算

当你有一有一个数据数组时，你可能想对其进行特定的数学运算。本节将探索其中几个关键操作。

### 数组减法

此命令从 `b` 数组中减去一个数组以得到结果 `c` 数组。减法是逐元素进行的。请注意，当你减去两个数组时，它们的维度必须相等。

### 数组平方

此命令将每个元素提升 2 次方以得到以下结果：

```python
>>> b**2
[1 4 9 16]
```

### 在数组上执行三角函数

此命令将余弦函数应用于 `b` 数组中的每个值以得到以下结果：

```python
>>> np.cos(b)
[ 0.54030231 -0.41614684 -0.9899925 -0.65364362]
```

### 条件运算

条件命令对 `b` 数组的每个元素应用条件操作以生成所需的布尔值：

```python
>>> b<2
[True False False False]
```

### 矩阵乘法

两个矩阵可以逐元素相乘，也可以使用点积。下方的命令将求值逐元素乘法：

```python
>>> A1 = np.array([[1, 1]],
[0, 1]])
>>> A2 = np.array([[2, 0]],
[3, 4]])
>>> A1 * A2
[[2 0]
[0 4]]
```

点积可以使用以下命令计算：

```python
>>> np.dot(A1, A2)
[[5 4]
[3 4]]
```

### 索引与切片

如果你想选择数组的给定元素，可以使用索引来完成：

```python
>>> n_array[1, 2]
```

这将选择第二个数组的第三个值。如果某行中需要突出一个范围的值，可以写以下命令：

```python
>>> n_array[0:3]
[0 1 2]
```

`0:3` 值代表第一行的前三个值。可以使用以下命令突出整行：

```python
>>> n_array[0, :]
[0 1 2]
```

通过这种方法，可以选取整列值：

```python
>>> n_array[:, 1]
[1 5 9]
```

### 形状修改

当数组创建时，它的形状也可以改变。以下命令将数组展平：

```python
>>> n_array.ravel()
[0 1 2 3 4 5 6 7 8 9 10 11]
```

上述命令将数组的形状改为六行两列。此外，在重塑时，新形状的元素数量应与初始相同：

```python
>>> n_array.shape = (6,2)
>>> n_array
[[0 1]
[4 5]
[6 7]
[8 9]
[10 11]]
```

上述数组可以转置为：

```python
>>> n_array.transpose()
[[0 2 4 6 8 10]
[1 3 5 7 9 11]]
```

## 使用 Pandas 进行数据分析

`Pandas` 是一个开源库。该库专门为数据分析设计。`Pandas` 构建在 `NumPy` 之上，因此易于使用。`pandas` 库包含高效处理数据结构，完成快速连接并从不同源读取数据。

### Pandas 的数据结构

`pandas` 库基本上有三种数据结构：

1. `Panel`
2. `Series`
3. `DataFrame`

### Series

`Series` 是单维数组，可以存储任何类型的数据，如浮点数、字符串、整数以及 Python 对象。可以通过编写以下函数生成系列：

```python
>>> import pandas as pd
>>> pd.Series(np.random.randn(5))
0    0.733810
1   -1.274658
2   -1.602298
3   -0.460944
4   -0.632756
dtype: float64
```

可以通过调用以下函数自定义系列的索引：

```python
>>> pd.Series(np.random.randn(5), index=['a', 'b', 'c', 'd', 'e'])
a - 0.929494
b - 0.571423
c - -1.197866
d - 0.081107
e - -0.035091
type: float64
Series 也可以从 Python 字典生成：
>>> d = {'A': 10, 'B': 20, 'C': 30}
>>> pd.Series(d)
A    10
B    20
C    30
dtype: int64
```

## DataFrame

`DataFrame` 指的是一种包含不同数据类型的列的 2D 数据结构。它可以被视为一个表格。可以从上述数据结构生成 `DataFrame`：

- `NumPy` 数组
- 二维 `NumPy` 数组
- 字典 `Dicts`
- 列表 `Lists`

当你编写以下命令时，可以从序列的字典生成 `DataFrame`：

```python
>>> d = {'c1': pd.Series(['A', 'B', 'C']),
      'c2': pd.Series([1, 2., 3., 4.])}
>>> df = pd.DataFrame(d)
>>> df
  c1  c2
0  A  1
1  B  2
2  C  3
3 NaN  4
```

## Panel

`Panel` 指的是一种处理 3D 数据的数据结构。命令

```python
>>> d = {'Item1': pd.DataFrame(np.random.randn(4, 3)),
       'Item2': pd.DataFrame(np.random.randn(4, 2))}
>>> pd.Panel(d)
class pandas.core.panel.Panel
Dimensions: 2 (items) x 4 (major_axis) x 3 (minor_axis)
Items axis: Item1 to Item2
Major_axis axis: 0 to 3
Minor_axis axis: 0 to 2
```

之前的命令表示由两个项目代表 2 个 `DataFrame`。由四个主轴 `major_axis` 表示四行，由三个次轴 `minor_axis` 表示三列。

### 插入和导出数据

数据以不同的形式存储，例如数据库、`CSV`、`tsv` 等。`pandas` 库使得从这些格式中读取数据并导出到以下格式变得有用。你将使用一个包含美国学校体重统计数据的数据集。

你将使用结构如下的文件：

| 列名 | 说明 |
| --- | --- |
| LOCATION CODE | 唯一位置代码 |
| COUNTY | 学校所属的国家/县 |
| AREA NAME | 学校所属的地区/区 |
| REGION | 学校所属的区域/大区 |
| SCHOOL YEARS | 数据涉及的学年 |
| NO. OVERWEIGHT | 超重学生人数 |
| PCT OVERWEIGHT | 超重学生的百分比 |
| NO. OBESE | 肥胖学生人数 |
| NO. OVERWEIGHT OR OBESE | 超重或肥胖的学生人数 |
| PCT OVERWEIGHT OR OBESE | 超重或肥胖学生的百分比 |
| GRADE LEVEL | 是否属于小学或高中 |
| AREA TYPE | 区域类型 |
| STREET ADDRESS | 学校地址 |
| CITY | 学校所属的城市 |
| STATE | 学校所属的州 |
| ZIP CODE | 学校的邮政编码 |
| Location 1 | 带有纬度的地址 |

要从 `.csv` 文件读取数据，输入以下 `read_csv` 函数：

```python
>>> d = pd.read_csv('Data/Student_Weight_Status_Category_Reporting_Results__Beginning_2010.csv')
>>> d[:5]['AREA NAME']
```

`read_csv` 函数接受 `.csv` 文件的路径来输入数据。

此命令后的指令将打印数据中 `Location` 列的前五行。

要写入 `.csv` 文件，你可以使用 `to_csv` 函数。

```python
>>> d = {'c1': pd.Series(['A', 'B', 'C']),
      'c2': pd.Series([1, 2., 3., 4.])}
>>> df = pd.DataFrame(d)
>>> df.to_csv('sample_data.csv')
```

通过应用 `to_csv` 方法并将 `DataFrame` 写入 `.csv` 文件，并应指定需要构建文件的文件名。

## XLS

除了 `pandas` 包之外，还需要安装 `xlrd` 包，`pandas` 才能从 Excel 文件中读取数据。

前面的函数类似于 `CSV` 读取命令。要写入 Excel 文件，应该安装 `xlswt` 包。

## JSON

要从 `JSON` 文件读取数据，可以使用 Python 的标准 `JSON` 包。以下命令在读取文件时很有用。

```python
>>> import json
>>> json_data = open('Data/Student_Weight_Status_Category_Reporting_Results__Beginning_2010.json')
>>> data = json.load(json_data)
>>> json_data.close()
```

在之前的命令中，`open()` 函数启动与文件的连接。

`json.load` 将数据加载到 Python。`json_data.close()` 函数关闭与文件的连接。

`pandas` 库也生成了一个读取 `JSON` 文件的函数，你可以使用 `pd.read_json()` 进行访问。

## 数据库

要从数据库读取数据，使用以下函数：

```python
>>> pd.read_sql(table_name, con)
```

之前的命令创建一个 `DataFrame`。假设提供表名和一个 `SQLAlchemy` 引擎，它们返回一个 `DataFrame`。此函数支持 `DBAPI` 连接。

- `Table_name`: 指数据库中的表名。
- `Con`: 指 `SQLAlchemy` 引擎。

下面的命令读取 SQL 查询到 `DataFrame`：

```python
>>> pd.read_sql(sql, con)
```

参数描述如下：

- `Sql`: 指要执行的 SQL 查询。
- `Con`: 指 `SQLAlchemy` 引擎。

## 数据清洗

在行形式上，数据需要一些清洗。许多因素可能导致数据出现问题。例如，零售系统可能输入带有缺失值的数据。此部分将教你如何处理此类数据。

### 缺失数据

通常情况下，大多数数据会有缺失值。这可能是由于不同的原因。一旦加载了数据，搜索数据中的缺失值很重要。这可以通过删除行或替换缺失值来处理。

在验证 `Location` 列是否有缺失值的情况下，可以使用以下命令：

```python
>>> d['Location 1'].isnull()
```

`isnull()` 函数将每行显示为 `True` 或 `False`。如果是 `True`，则存在缺失值。此数据可以统计缺失值的数量：

```python
>>> d['Location 1'].isnull().value_counts()
```

之前的命令说明 `Location 1` 列包含 24 个缺失值。这些缺失值可以通过删除行或替换值来处理。运行以下命令：

```python
>>> d['Location 1'].dropna()
```

要移除所有包含缺失值的行，以下命令很有用：

```python
>>> d = d.dropna(how='any')
```

## 完善缺失数据

定义一些 `DataFrame`：

```python
>>> df = pd.DataFrame(np.random.randn(5, 3), index=['a0', 'a10', 'a20', 'a30', 'a40'], columns=['X', 'Y', 'Z'])
>>> df
      X         Y         Z
a0  -0.854269  0.117540  1.515373
a10 -0.483923 -0.379934  0.484155
a20 -0.038317  0.196770 -0.564157
a30  0.752686  0.632661 -1.274481
a40 -1.383379 -0.564157  1.375555
```

接下来，添加一些额外的索引，将在 `DataFrame` 中生成空值：

```python
>>> df2 = df.reindex(['a0', 'a1', 'a10', 'a20', 'a30', 'a40'])
>>> df2
      X         Y         Z
a0  -0.854269  0.117540  1.515373
a1      NaN       NaN       NaN
a10 -0.483923 -0.379934  0.484155
a20 -0.038317  0.196770 -0.564157
a30  0.752686  0.632661 -1.274481
a40 -1.383379 -0.564157  1.375555
```

如果你想将 `df2` 中的空值替换为 0，请运行以下命令：

```python
>>> df2.fillna(0)
      X         Y         Z
a0  -0.854269  0.117540  1.515373
a1      0.0       0.0      0.0
a10 -0.483923 -0.379934  0.484155
a20 -0.038317  0.196770 -0.564157
a30  0.752686  0.632661 -1.274481
a40 -1.383379 -0.564157  1.375555
```

## 字符串操作

有时你可能想要更改数据中的字符串字段列。

这里有一种描述了一些字符串操作的技术：

- 子字符串：让我们从选择数据中 `AREA NAME` 列的前五行作为编辑的示例开始。

要从 `Area Name` 列中提取第一个单词，你需要应用下方命令所示的 `extract` 函数：

```
>>> df['AREA NAME'][0:5].str.extract('(\w+)')
```

在上述命令中，使用了 series 的 `str` 特性。`str` 类拥有一个 `extract` 方法，可以传入一个正则表达式来提取数据，这非常强大。也可以将 `AREA NAME` 中的第二个单词作为单独的一列提取：

```python
>>> df['AREA NAME'][0:5].str.extract('(\w+) (\w+)')
```

要从不同的列中挖掘数据，所需的正则表达式应该包含在独立的括号中。

- 过滤：如果你想根据 `ELEMENTARY`（小学）学校的数据来过滤行，可以使用下面的命令：

```python
>>> df[df['GRADE LEVEL'] == 'ELEMENTARY']
```

- 大写：若要将区域名称转换为大写，你需要输入以下命令：

```python
>>> df['AREA NAME'][0:5].str.upper()
```

由于数据字符串已经是大写了，因此不会有任何可见的变化。

- 小写：若要将区域名称转换为小写，你需要应用以下命令：

```python
>>> df['AREA NAME'][0:5].str.lower()
```

- 长度：要确定 `Area Name` 列中每个元素的长度，你需要应用以下命令：

```python
>>> df['AREA NAME'][0:5].str.len()
0 47
1 47
2 47
3 27
4 27
Name: AREA NAME, dtype: int64
```

- 分割：若要根据空格分割 `Area Name`，你需要应用以下命令：

```python
>>> df['AREA NAME'][0:5].str.split(' ')
```

- 替换：如果你想将所有以 `DISTRICT` 结尾的区域名称替换为 `DIST`，可以使用以下命令：

```python
>>> df['AREA NAME'][0:5].str.replace('DISTRICT$', 'DIST')
```

替换方法中的第一个参数表示用于高亮显示待替换字符串部分的正则表达式。第二个参数表示要替换后的值。

## 合并数据

为了聚合数据集，可以使用 `pandas` 的 `concat` 函数。考虑包含前五个 `Area Name` 和 `Country` 的列：

```python
>>> d[['AREA NAME', 'COUNTY']][0:5]
```

仍然，你可以对数据进行分割，如下：

```python
>>> p1 = d[['AREA NAME', 'COUNTY']][0:2]
>>> p2 = d[['AREA NAME', 'COUNTY']][2:5]
```

数据的前两行在 `p1` 中，最后三行在 `p2` 中。这些部分可以使用 `concat()` 函数组合。例如：

```python
>>> pd.concat([p1,p2])
```

可以通过分配键 `key` 来识别组合后的部分：

```python
>>> concatenated = pd.concat([p1,p2], keys=['p1','p2'])
>>> concatenated
```

通过应用键，可以从合并的数据中提取回片段。例如：

```python
>>> concatenated.ix['p1']
```

## 数据操作

一旦处理缺失数据，就可以对数据进行不同的操作。

### 聚合操作

有不同的聚合操作，如求和、平均值等，你想在数值字段上进行这些操作。以下是用于评估这些的方法：
