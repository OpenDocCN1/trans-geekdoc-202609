

假设我们有如下一个 DataFrame

```python
[In 27]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit','Cookies'],
    'Sales':[227,158]}, index = [1,2])

sr
```

| | Product | Sales |
|---|---|---|
| 1 | Biscuit | 227 |
| 2 | Cookies | 158 |

我们只需要 Sales 列，因此使用 `DataFrame[column_label]` 语法

```python
[In 32]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit','Cookies'],
    'Sales':[227,158]}, index = [1,2])
sr['Sales']

Out[32]: 
1    227
2    158
Name: Sales, dtype: int64
```

或者只获取第二行，因此使用 `DataFrame.loc[row_index]` 语法

```python
[In 33]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit','Cookies'],
    'Sales':[227,158]}, index = [1,2])
sr.loc[2] #你也可以使用 sr.iloc[1]

Out[33]: 
Product  Cookies
Sales      158
Name: Sales, dtype: object
```

或者只获取 cookies 的销售额，因此使用 `DataFrame.values[index]` 语法

```python
[In 37]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit','Cookies'],
    'Sales':[227,158]}, index = [1,2])
sr.values[1,1]

Out[37]: 158
```

值是以 ndarrays 形式存储的，这就是为什么我们使用了类似于二维 ndarrays 的切片方法

# 我们可以从 DataFrame 中删除一整列

```python
In [41]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit', 'Cookies'],
    'Sales':[227,158]}, index = [1,2])
```

| | Product | Sales |
|---|---|---|
| 1 | Biscuit | 227 |
| 2 | Cookies | 158 |

```python
In [45]: del sr['Sales']
sr
```

| | Product |
|---|---|
| 1 | Biscuit |
| 2 | Cookies |

# 但我们不能删除一个值

```python
In [47]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit', 'Cookies'],
    'Sales':[227,158]}, index = [1,2])
sr.values=[1,1]
```

> ValueError Traceback (most recent call last)
<ipython-input-4422e071c59> in module
3 sr = pd.DataFrame({'Product':['Biscuit', 'Cookies'],
    'Sales':[227,158]}, index = [1,2])
---> 4 del sr.values=[1,1]

ValueError: cannot delete array

# 不能修改值

```python
In [48]: import pandas as pd
sr = pd.DataFrame({'Product':['Biscuit', 'Cookies'],
    'Sales':[227,158]}, index = [1,2])
```

| | Product | Sales |
|---|---|---|
| 1 | Biscuit | 227 |
| 2 | Cookies | 158 |

```python
In [51]: sr.values[1,1] = 1

In [51]: 158
```

# 更多关于 ndarrays

我们可以使用 `array[::-1]` 语法反转 ndarray

```python
In [56]: import numpy as np
ar = np.array([1, 2, 3, 4])
Out[56]: array([1 2 3 4])
In [55]: ar = ar[::-1]
Out[55]: array([4 3 2 1])
```

不需要这种方法就可以广播整个 ndarray

```python
In [56]: import numpy as np
ar = np.array([1, 2, 3, 4])
Out[56]: array([1 2 3 4])
In [62]: # 这种方法 - ar + [1,1,1,1]
ar = ar + 1
Out[62]: array([2 3 4 5])
```

我们可以用 `sort` 函数排序数组

```python
In [63]: import numpy as np
ar = np.array([5, 1, 3, 9])
Out[63]: array([5 1 3 9])
In [64]: ar.sort()
Out[64]: array([1 3 5 9])
```

有很多内置的 ndarray 方法现在不会讨论，但在各种步骤中使用，你可以查看文档查找所有函数及其作用，杂杂函数在书中书中被讨论

# 数据清洗

让我们考虑下面的情况

```python
In [71]: import pandas as pd
import numpy as np
ar = np.array([[1,2,3],[6,7,2],[4,9,1]])
df = pd.DataFrame(data = ar, index = ['a','c','e'], columns = ['C1','C2','C3'])

Out[71]:
      C1  C2  C3
a     4   7   2
c     9   1
In [72]: df = df.reindex(['a','b','c','e'])
df
```

| | C1 | C2 | C3 |
|---|---|---|---|
| a | 1.0 | 2.0 | 3.0 |
| b | NaN | NaN | NaN |
| c | 4.0 | 7.0 | 2.0 |
| d | NaN | NaN | NaN |
| e | 4.0 | 9.0 | 1.0 |

重索引后的 DataFrame 在 b 行 NaN NaN。这是因为 b 行没有数据。使用重索引我们创建了一个带有缺失值的 DataFrame。在输出中，NaN 表示非数字。为了更容易检测缺失值（跨不同类型），Pandas 提供了 `isnull()` 和 `isna()` 函数，它们也是 Series 和 DataFrame 对象上的方法

```python
In [73]: df['C1'].isnull()

Out[73]:
a    False
b     True
c    False
d     True
e    False
Name: C1, dtype: bool
```

Pandas 提供了各种清理缺失值的方法。`fillna` 可以用几种方式用非空数据填充 NaN 值，例如用 0 替换值

```python
In [74]: df.fillna(0)
Out[74]:
      C1  C2  C3
a  1.0 2.0 3.0
b  0.0 0.0 0.0
c  4.0 7.0 2.0
d  0.0 0.0 0.0
e  4.0 9.0 1.0
```

我们可以使用 `fillna` 参数中的 `pad` 或 `bfill` 复制该数据上方或下方的值

```python
In [75]: df.fillna(method='pad')
Out[75]:
      C1  C2  C3
a  1.0 2.0 3.0
b  1.0 2.0 3.0
c  4.0 7.0 2.0
d  4.0 7.0 2.0
e  4.0 9.0 1.0
```

我们可以用 `dropna` 丢弃带有缺失值的行

```python
In [76]: df.dropna()
Out[76]:
      C1  C2  C3
a  1.0 2.0 3.0
c  4.0 7.0 2.0
e  4.0 9.0 1.0
```

如果想更改 DataFrame 中的某个单元值，可以使用 `replace` 函数

```python
In [78]: import pandas as pd
import numpy as np
ar = np.array([[1,2,3],[4,7,2],[4,9,1]])
df = pd.DataFrame(data = ar, index = ['a','c','e'], columns = ['C1','C2','C3'])

df.replace({3:1})

Out[78]:
  C1 C2 C3
a  1  2  1
c  4  7  2
e  4  9  1
```

# 数据分析 & 处理

- 数据分析
- 属性之间的相关性
- 偏度

作为机器学习课程，我们需要大量的分析来了解更多数据信息。我们已经知道了集中趋势，例如平均值、中位数和众数是我们的基本统计数据。同样，我们不需要手动计算它们，在不同的库中有许多函数用于分析。

# 数据分析

在训练任何模型之前，我们需要检查数据。我们将使用 `trees.csv` 作为你的数据。在进行进一步操作之前，让我们看看原始数据

```python
In [2]: import pandas as pd
dt = pd.read_csv('trees.csv')
dt
```

| | "Girth (in)" | "Height (ft)" | "Volume(ft3)" |
|---|---|---|---|
| count | 31.00 | 31.00 | 31.00 |
| mean | 16.00 | 13.25 | 76.00 |
| std | 9.09 | 3.14 | 6.37 |
| min | 1.00 | 8.30 | 63.00 |
| 25% | 8.50 | 11.05 | 72.00 |
| 50% | 16.00 | 12.90 | 76.00 |
| 75% | 23.50 | 15.25 | 80.00 |
| max | 31.00 | 20.60 | 87.00 |

第一步分析是了解数据的形状或者有多少行和多少列。我们可以通过使用 dataframe 对象的 `shape` 属性来实现

```python
In [4]: import pandas as pd
dt = pd.read_csv('trees.csv')
dt.shape

Out[4]: (31, 4)
```

我们的数据有 31 行 4 列，总共 124 个值。如果我们想检查前 10 个值，可以使用 `head()` 函数并传递 10 作为参数

```python
In [5]: import pandas as pd
dt = pd.read_csv('trees.csv')
dt.head(10)
```

| Index | Girth (in) | Height (ft) | Volume(ft3) |
|---|---|---|---|
| 0 | 8.3 | 70 | 10.3 |
| 1 | 8.6 | 65 | 10.3 |
| 2 | 8.8 | 63 | 10.2 |
| 3 | 10.5 | 72 | 16.4 |
| 4 | 10.7 | 81 | 18.8 |
| 5 | 10.8 | 83 | 19.7 |
| 6 | 11.0 | 66 | 15.6 |
| 7 | 11.0 | 75 | 18.2 |
| 8 | 11.1 | 80 | 22.6 |
| 9 | 11.2 | 75 | 19.9 |

为了获取整个数据的统计概述，我们可以使用 `describe()` 函数，它提供了计数、平均值、标准差、25%、50%（中位数）、75%、最小值和最大值

```python
In [6]: import pandas as pd
dt = pd.read_csv('trees.csv')
dt.describe()
```

| | "Girth (in)" | "Height (ft)" | "Volume(ft3)" |
|---|---|---|---|
| count | 31.00 | 31.00 | 31.00 |
| mean | 16.00 | 13.25 | 76.00 |
| std | 9.09 | 3.14 | 6.37 |
| min | 1.00 | 8.30 | 63.00 |
| 25% | 8.50 | 11.05 | 72.00 |
| 50% | 16.00 | 12.90 | 76.00 |
| 75% | 23.50 | 15.25 | 80.00 |
| max | 31.00 | 20.60 | 87.00 |

如果你想将值保留到（ 2 位）小数位数，可以使用 pandas 的 `set_option()` 函数并将精度指定为 2。我们可以通过这个函数指定许多选项

```python
In [7]: import pandas as pd
dt = pd.read_csv('trees.csv')
pd.set_option('precision',2)
dt.describe()
```

| | "Girth (in)" | "Height (ft)" | "Volume(ft3)" |
|---|---|---|---|
| count | 31.00 | 31.00 | 31.00 |
| mean | 16.00 | 13.25 | 76.00 |
| std | 9.09 | 3.14 | 6.37 |
| min | 1.00 | 8.30 | 63.00 |
| 25% | 8.50 | 11.05 | 72.00 |
| 50% | 16.00 | 12.90 | 76.00 |
| 75% | 23.50 | 15.25 | 80.00 |
| max | 31.00 | 20.60 | 87.00 |

