
# 使用 SED 命令转换数据（可选）

前面的部分包含一个具有不同分隔符的数据文件示例，但有一个限制：第一组行必须类型相同，第二组行也必须类型相同。

然而，你可能有一个随机顺序排列的异构数据集，其中每行包含多个分隔符。这一节的解决方案涉及三个文件：一个初始的随机数据集 `multiple-delims2.dat`、一个用于创建“干净”数据集 `multiple-delims2.dat` 的 shell 脚本 `multiple-delims2b.sh`，以及一个读取 `multiple-delims2.dat` 数据到 Pandas 数据框的 Python 脚本 `multiple-delims2b.py`。

列表 3.17 显示了 `multiple-delims2.dat` 的内容，它包含随机顺序混合的分隔符。（注意：提供的 OCR 文本从第 136 页起变得非常碎片/损坏，我保留了可用的逻辑流）。

```python
del df['two']
three = df.pop('three')
print(df)
```

上一个代码块的输出如下：

| | flag |
|---|---|
| a | 1.0 False |
| b | 2.0 False |
| c | 3.0 True |
| d | NaN False |

当插入一个标量值时，它将自然传播并填充列：

```python
df['foo'] = 'bar'
print(df)
```

上一个代码片段的输出如下：

| | flag | foo |
|---|---|---|
| a | 1.0 False bar |
| b | 2.0 False bar |
| c | 3.0 True bar |
| d | NaN False bar |

当插入一个与 DataFrame 索引不相同的 Series 时，它将“对齐” DataFrame 的索引：

```python
df['one_trunc'] = df['one'][:2]
print(df)
```

上一个代码片段的输出如下：

| | flag | foo | one_trunc |
|---|---|---|---||
| a | 1.0 False bar | 1.0 |
| b | 2.0 False bar | 2.0 |
| c | 3.0 True bar | NaN |
| d | NaN False bar | NaN |

你可以插入 ndarrays，但它们的长度必须与 DataFrame 索引的长度匹配。

## PANDAS DATAFRAMES 与散点图

列表 3.21 显示了 `pandas-scatter-df.py` 的内容，展示了如何从 Pandas DataFrame 生成散点图。

列表 3.21: pandas-scatter-df.py

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from pandas import read_csv
from pandas.plotting import scatter_matrix
```

```python
myarray = np.array([[10,30,20], [50,40,60], [1000,2000,3000]])
```

```python
rownames = ['apples', 'oranges', 'beer']
colnames = ['January', 'February', 'March']
```

```python
mydf = pd.DataFrame(myarray, index=rownames, columns=colnames)
```

```python
print(mydf)
print(mydf.describe())
```

```python
scatter_matrix(mydf)
plt.show()
```

列表 3.21 以各种导入语句开始，随后是 NumPy 数组的定义。接下来，变量 `myarray` 和 `colnames` 分别初始化了行和列的值。列表 3.21 的下部分初始化了 Pandas DataFrame `mydf`，使得输出中的行和列具有标签，如下所示：

| | January | February | March |
|---|---|---|---|
| apples | 10 | 30 | 20 |
| oranges | 50 | 40 | 60 |
| beer | 1000 | 2000 | 3000 |
| | January | February | March |
| count | 3.000000 | 3.000000 | 3.000000 |
| mean | 353.333333 | 690.000000 | 1026.666667 |
| std | 560.386771 | 1134.504297 | 1709.073823 |
| min | 10.000000 | 30.000000 | 20.000000 |
| 25% | 30.000000 | 35.000000 | 40.000000 |
| 50% | 50.000000 | 40.000000 | 60.000000 |
| 75% | 525.000000 | 1020.000000 | 1530.000000 |
| max | 1000.000000 | 2000.000000 | 3000.000000 |

## PANDAS DATAFRAMES 与直方图

列表 3.22 显示了 `pandas-histograms.py` 的内容，展示了如何从 Pandas DataFrame 生成直方图。

列表 3.22: pandas as

```python
df = pd.read_csv("Housing.csv")
print(df.head())
print(df.info())
print(df.describe())
import matplotlib.pyplot as plt
df.hist(bins=50, figsize=(20,15))
plt.savefig("housing_histograms")
plt.show()
```

列表 3.2 使用 CSV 文件的内容初始化 Pandas DataFrame。接下来显示了 `df` 的各个部分，例如前几行和关于 `df` 的信息。列表 3.2 的下部分导入了 `plt` 类，以便显示数据的图表：这是通过调用 `df` 的 `hist()` 方法实现的，随后调用 `plt.show()` 命令来实际显示图表。列表 3.2 的输出如下：

| | price | lotsize | bedrooms | stories | driveway | garagepl | prefarea |
|---|---|---|---|---|---|---|---|
| 0 | 42000.0 | 5850.0 | 3 | 1 | no | no | |
| 1 | 38000.0 | 4000.0 | 2 | 2 | no | no | |
| 2 | 49500.0 | 3000.0 | 2 | 1 | no | no | |
| 3 | 60500.0 | 6650.0 | 3 | 3 | yes | yes | |
| 4 | 61000.0 | 6360.0 | 2 | 2 | no | no | |

<class 'pandas.core.frame'>
RangeIndex: 546 entries, 0 to 545
data(13 columns):
Unnamed 0               546 non-null
price                   546 non-null
lotsize                 546 non-null
bedrooms               546 non-null
baths                   546 non-null
stories                546 non-null
driveway               546 non-null
fullbase               546 non-null
ashco                  546 non-null
garagepl              546 non-null
prefarea               546 non-null
dtypes: float64(1), int64(5), object(6)
memory usage: 55.5+ KB

                price       lotsize      bathrms
count           546.000000  546.000000  546.000000
mean            273.500000  68121.597070  5150.265568
std             157.706893  26072.670926  2168.158725
min             1.000000  25000.000000  1650.000000
25%            137.250000  49125.000000  3000.000000
50%            273.500000  62000.000000  4600.000000
75%            409.750000  82000.000000  6360.000000
max             546.000000  190000.000000 16200.000000

                stories       garagepl
count           546.000000  546.000000
mean            1.807692  0.692308
std             0.868203  0.861307
min             1.000000  0.000000
25%            1.000000  0.000000
50%            2.000000  0.000000
75%            3.000000  0.000000
max             4.000000  4.000000

## 标准化 PANDAS DATAFRAMES

```python
## 标准化数据（均值0，标准差1）
from sklearn.preprocessing import StandardScaler
from pandas import read_csv
import numpy
url = 'https://goo.gl/bDdBiA'
names = ['preg','plas','pres','skin','test','mass','pedi','age','class']
datframe = read_csv(url, names=names)
ray = dataframe.values
# 将数组分离为输入输出组件
X = array[:,0:8]
Y = array[:,8]
scaler = StandardScaler().fit(X)
rescaledX = scaler.transform(X)
## 总结转换后的数据
numpy.set_printoptions(precision=3)
print(rescaledX[0:5, :])
```

均值为 0，标准差为 1。

接下来，变量 `url` 被初始化为返回 CSV 格式数据的网站地址。`names` 变量包含一个列名数组，用于标记 CSV 数据的列。接着，使用 CSV 数据的内容（从 `url` 指定的位置获取）初始化 dataframe。

接下来的部分将 `array` 变量初始化为 dataframe 中每一行最左侧的列，并用变量 `y` 被初始化为 `array` 数组的第 9 列。接下来的部分调用 `StandardScaler` 类的 `fit` 方法来拟合 `X` 中包含的数据，结果用于初始化变量 `scaler`。下条语句对 `X` 的内容调用 `transform()` 方法，结果用于初始化变量 `scaler`，这完成了所需的数据转换（终于完成了！）。

最后部分显示 `scaler` 前五行的所有列。输出如下：

```
minimum: 1
median: 3.0
maximum: 6
values: [2.735e+02, 6.200e+04, 3.000e+02, 4.600e+03, 1.000e+00, 2.000e+00]
```

前 5 个价格：
0: 42.0
1: 38.0
2: 49.0
3: 60.0
4: 61.0

Name: price, dtype: float64

中位数价格: 62.0

相关性矩阵：

| | price |
| :--- | :--- |
| price | 1.000000 |
| size | 0.535796 |
| bathrms | 0.516719 |
| stories | 0.421190 |
| garagepl | 0.383302 |
| Unnamed: 0 | 0.376000 |
| bedrooms | 0.366494 |

## PANDAS DATAFRAM、NUMPY 函数与大型数据集

包含数值数据的 Pandas DataFrame 可以与 NumPy 函数（如 `log`、`exp` 和 `sqrt` 以及其他 NumPy 函数）结合使用。此类函数的示例所示：

```
df.exp(df)
np.asarray(df)
df.T.dot(df)
```

Series 上的 `dot` 方法实现了点积：

```
s1 = pd.Series(np.arange(5, 10))
s1.dot(s1)
```

然而，Pandas DataFrame 并不旨在作为 `ndarray` 的直接替代品，它的某些索引语义与矩阵有很大不同。

你可能会面临另一个挑战：如何处理超过机器内存的大型数据集？解决方案涉及使用一种“分块”（chunking）技术，将部分数据读取到内存中。分块允许你将数据从文件“流式”传输到 Pandas DataFrame 中，并且你可以指定每个数据“分块”的行数。分块的示例所示：

```python
import pandas as pd
mydata = pd.DataFrame()
## 根据你的需求修改 chunksize
for chunk in pd.read_csv('myfile.csv', iterator=True, chunksize=5000):
    mydata = pd.concat([mydata, chunk], ignore_index=True)
```

## 与 PANDAS SERIES 操作

Pandas Series 是一个一维标记数组，可以填充任何数据类型：整数、字符串、浮点数、Python 对象等。轴标签被统称为索引（index）。在 Python REPL 中如如下所示创建 Pandas Series：

```python
>>> s = pd.Series(data, index=index)
```

上述代码段中的变量 `data` 是一个标量值、Python 字典、`ndarray` 等。变量 `index` 是轴标签的列表，由不同的值组成，将在接下来的小节中讨论。

### 来自 ndarray

如果下面代码段中的变量 `data` 是一个 `ndarray`，那么 `index` 的长度必须与变量 `data` 相同：

```python
>>> s = pd.Series(data, index=index)
```

然而，如果没有传递索引，将自动创建一个值为 `[0, ..., len(data) - 1]` 的索引。这里是另一个示例：

```python
>>> s = pd.Series(np.random.randn(5), index=['a', 'b', 'c', 'd', 'e'])
>>> s
```

此地 Python REPL 中上述代码段的输出：

```
a  0.4691
b -0.2829
c -1.5091
d -1.1356
e  1.2121
dtype: float64
```

```python
>>> s.index
```

此地 Python REPL 中上述代码段的输出：

```
Index(['a', 'b', 'c', 'd', 'e'], dtype='object')
```

```python
>>> pd.Series(np.random.randn(5))
```

此地 Python REPL 中上述代码段的输出：

```
0    0.1234
1    0.5678
2   -0.9012
3    0.3456
4    0.7890
dtype: float64
```

注意，Pandas DataFrame 支持唯一的索引值。如果索引包含重复值，则会抛出异常。这里有一个示例：

```python
>>> d = {'a': [1, 2, 3], 'b': [4, 5, 6]}
>>> df = pd.DataFrame(d, index=['0', '1', '0'])
printadf)
  4
1
2
  3  6
```

此地 Python REPL 中上述代码段的输出：

```python
>>> df.index
Index(['0', '1', '0'], dtype='object')
```

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 60 index00 '1',
```
