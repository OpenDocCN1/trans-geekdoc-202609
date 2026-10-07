

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
mydf = pd.DataFrame(myarray, index=rownames,
columns=colnames)
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
# 标准化数据（均值0，标准差1）
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

# 总结转换后的数据
numpy.set_printoptions(precision=3)
print(rescaledX[0:5, :])
```
