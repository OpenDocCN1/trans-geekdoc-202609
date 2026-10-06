
```python
data3 = pd.concat([data1.reset_index(drop=True), data2], axis=1)
```

```python
display(data3.head)
```

我们创建一个名为 `data1` 的新 DataFrame，其中只包含花瓣宽度列：`data1 = data[["Petal_Width"]]`。我们使用 `display()` 函数显示 `data1` 的前五行。类似地，我们创建另一个名为 `data2` 的 DataFrame，其中只包含类列：`data2 = data[["Class"]]`。我们也显示 `data2` 的前五行。最后，我们沿水平轴 (`axis=1`) 拼接 `data1` 和 `data2`，创建一个名为 `data3` 的新 DataFrame。我们使用 `reset_index` 函数删除 `data1` 的原始索引并分配新的索引。我们显示 `data3` 的前五行，其中显示每朵花的花瓣宽度和类别。

Output:

| | Petal_Width | | Class | | Petal_Width | Class |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | 0.2 | 0 | Iris-setosa | 0 | 0.2 | Iris-setosa |
| 1 | 0.2 | 1 | Iris-setosa | 1 | 0.2 | Iris-setosa |
| 2 | 0.2 | 2 | Iris-setosa | 2 | 0.2 | Iris-setosa |
| 3 | 0.2 | 3 | Iris-setosa | 3 | 0.2 | Iris-setosa |
| … | … | … | … | … | … | … |
| 146 | 2.0 | 146 | Iris-virginica | 146 | 2.0 | Iris-virginica |
| 147 | 2.3 | 147 | Iris-virginica | 147 | 2.3 | Iris-virginica |
| 148 | 1.8 | 148 | Iris-virginica | 148 | 1.8 | Iris-virginica |

### 13.5.18 Displaying DataFrame Information

```python
# This line imports the pandas library and gives it the alias pd
import pandas as pd

# This line reads a CSV file named iris.csv and stores it in a variable called data
data = pd.read_csv("iris.csv")

# This line assigns new names to the columns of the data
data.columns = ['Sepal_Length','Sepal_Width','Petal_Length','Petal_Width','Class']

# displays the summary information of the data using the data.info method
display(data.info)
```

Output:

| | Sepal_Length | Sepal_Width | Petal_Length | Petal_Width | Class |
| --- | --- | --- | --- | --- | --- |
| 0 | 4.9 | 3.0 | 1.4 | 0.2 | Iris-setosa |
| 1 | 4.7 | 3.2 | 1.3 | 0.2 | Iris-setosa |
| 2 | 4.6 | 3.1 | 1.5 | 0.2 | Iris-setosa |
| 3 | 5.0 | 3.6 | 1.4 | 0.2 | Iris-setosa |
| 4 | 5.4 | 3.9 | 1.7 | 0.4 | Iris-setosa |
| ………………………. | | | | | |
| 144 | 6.7 | 3.0 | 5.2 | 2.3 | Iris-virginica |
| 145 | 6.3 | 2.5 | 5.0 | 1.9 | Iris-virginica |
| 146 | 6.5 | 3.0 | 5.2 | 2.0 | Iris-virginica |
| 147 | 6.2 | 3.4 | 5.4 | 2.3 | Iris-virginica |
| 148 | 5.9 | 3.0 | 5.1 | 1.8 | Iris-virginica |

### 13.5.19 Finding the Mean and Median of a Column

```python
# This line imports the pandas library and gives it the alias pd
import pandas as pd

# This line reads a CSV file named iris.csv and stores it in a variable called data
data = pd.read_csv("iris.csv")

# This line assigns new names to the columns of the data
data.columns = ['Sepal_Length','Sepal_Width','Petal_Length','Petal_Width','Class']

# Use the median function from numpy to calculate the median value of the petal length column
display(np.median(data[["Petal_Length"]]))

# Use the mean function from numpy to calculate the mean value of the petal length column
display(np.mean(data[["Petal_Length"]]))

# Use the axis parameter to specify that we want to calculate the variance
# Variance is calculated along the rows (axis=0) rather than along the columns (axis=1)
display(np.var(data[["Petal_Length"]], axis=0))
```

我们使用 `display()` 函数以格式化的方式打印以下表达式的输出。我们使用 NumPy 中的 `median()` 函数来计算 `Petal_Length` 列的中位数。中位数是有序数字列表的中间值，如果列表元素个数为偶数，则为中间两个值的平均值：`display(np.median(data[["Petal_Length"]]))`。

我们使用 NumPy 中的 `mean()` 函数来计算 `Petal_Length` 列的平均值。平均值是所有值的总和除以值的数量：`display(np.mean(data[["Petal_Length"]]))`。

我们使用 NumPy 中的 `var` 函数来计算 `Petal_Length` 列的方差。方差是衡量值与均值偏离程度的指标。它是通过取每个值与均值之差的平方的平均值来计算的。我们使用 `axis` 参数指定我们希望沿行 (`axis=0`) 而非沿列 (`axis=1`) 计算方差：`display(np.var(data[["Petal_Length"]], axis=0))`。

Output:

```
4.4
3.774496644295302
Petal_Length 3.075591
dtype: float64
```

### 13.5.20 Displaying Boxplot using Matplotlib

```python
# This line imports the pandas and matplot library
import pandas as pd
import matplotlib.pyplot as plt

# This line reads a CSV file named iris.csv and stores it in a variable called data
data = pd.read_csv("iris.csv")

# This line assigns new names to the columns of the data
data.columns = ['Sepal_Length','Sepal_Width','Petal_Length','Petal_Width','Class']

boxplot = data.boxplot(figsize=(5,5))
```

该程序导入了两个模块：`matplotlib.pyplot` 和 `pandas`。这些模块是分别提供绘图函数和操作 DataFrame 函数的库。它使用 pandas 函数 `read_csv` 将 `iris.csv` 文件加载到名为 `data` 的 DataFrame 对象中。`iris.csv` 文件包含来自三种不同物种的 150 朵鸢尾花的萼片长度、萼片宽度、花瓣长度、花瓣宽度和类别的数据：setosa、versicolor 和 virginica。它使用 `data.columns` 属性为 DataFrame 的列分配新名称。新的名称为 `Sepal_Length`、`Sepal_Width`、`Petal_Length`、`Petal_Width` 和 `Class`。它使用 `data.boxplot` 方法创建四个数值变量的箱线图：萼片长度、萼片宽度、花瓣长度和花瓣宽度。箱线图是变量分布的图形表示，显示最小值、最大值、中位数、第一四分位数和第三四分位数的值，以及任何异常值。`boxplot()` 方法接受一个参数 `figsize`，指定以英寸为单位的图形大小。它使用 `matplotlib.pyplot` 中的 `plt.show` 函数在屏幕上显示箱线图。

Output:

![](img/685-1.jpg)

### 13.5.21 Displaying Histogram using Matplotlib

```python
# This line imports the pandas and matplot library
import pandas as pd
import matplotlib.pyplot as plt

# This line reads a CSV file named iris.csv and stores it in a variable called data
data = pd.read_csv("iris.csv")

# This line assigns new names to the columns of the data
data.columns = ['Sepal_Length','Sepal_Width','Petal_Length','Petal_Width','Class']

# It uses the data['Sepal_Length'].plot() method to create a plot object of the sepal length column of the data frame.
# It specifies the kind argument as 'hist' to make it a histogram.
data['Sepal_Length'].plot(kind='hist')
```

它将 `matplotlib.pyplot` 模块导入为 `plt`，这是一个用于在 Python 中创建各种类型绘图和图形的库。它将 `pandas` 模块导入为 `pd`，这是一个用于 Python 中数据分析和操作的库。它使用 `data['Sepal_Length'].plot()` 方法创建 DataFrame 的 `Sepal_Length` 列的绘图对象，并指定 `kind` 参数为 `hist` 以使其成为直方图。它使用 `plt.show()` 函数在屏幕上显示直方图。

Output:

![](img/686-1.jpg)

### 13.5.22 Displaying Scatter Diagrams

```python
# This line imports the pandas and matplot library
import pandas as pd
import matplotlib.pyplot as plt

# This line reads a CSV file named iris.csv and stores it in a variable called data
data = pd.read_csv("iris.csv")

import numpy as np

# This line assigns new names to the columns of the data
data.columns = ['Sepal_Length','Sepal_Width','Petal_Length','Petal_Width','Class']

# Generate random X and Y values
x = np.random.randn(1000)
y = np.random.randn(1000)

# Create customized scatter plot
plt.scatter(data[["Petal_Width"]], data[["Petal_Length"]], c='r', marker='x')
plt.xlabel('Petal Width')
plt.ylabel('Petal Length')
plt.title('Scatter Plot')
plt.show()
```

以上程序详细解释了如何使用 Matplotlib、pandas 和 NumPy 模块创建鸢尾花数据集的自定义散点图。它首先导入必要的模块并从 csv 文件读取数据。然后它重命名数据列以匹配鸢尾花数据集的属性。接下来，它生成两个随机数数组用作虚拟数据。最后，它创建鸢尾花数据集的花瓣宽度和花瓣长度的散点图，并相应地标注和标题化该图。

Output:

![](img/687-1.jpg)

### 13.6 Finding Outliers

```python
def find_outlier(ds, col):
    quart1 = ds[col].quantile(0.25)
    quart3 = ds[col].quantile(0.75)
    IQR = quart3 - quart1  # Inter-quartile range
    low_val = quart1 - 1.5 * IQR
    high_val = quart3 + 1.5 * IQR
    ds = ds.loc[(ds[col] < low_val) | (ds[col] > high_val)]
    return ds
```

我们想要编写一个函数来查找数据集中的异常值：`def find_outlier(ds, col)`。该函数将数据集 (`ds`) 和列名 (`col`) 作为输入参数。它返回数据集的一个子集，其中仅包含给定列中的异常值。异常值定义为与第一或第三四分位数相距超过 1.5 倍四分位距 (`IQR`) 的值。`IQR` 是列值的第 75 百分位数 (`quart3`) 与第 25 百分位数 (`quart1`) 之间的差值。第一四分位数是通过在列上调用 `quantile()` 方法并将 0.25 作为参数来计算的。第三四分位数是通过在列上调用 `quantile()` 方法并将 0.75 作为参数来计算的。异常值的下界 (`low_val`) 是通过从第一四分位数减去 1.5 倍 `IQR` 计算得出的。异常值的上界 (`high_val`) 是通过向第三四分位数加上 1.5 倍 `IQR` 计算得出的。`loc()` 方法用于通过选择列值小于 `low_val` 或大于 `high_val` 的行来过滤数据集。过滤后的数据集作为函数的输出返回。

### 13.7 Removing Outliers

```python
def remove_outlier(ds, col):
    quart1 = ds[col].quantile(0.25)
    quart3 = ds[col].quantile(0.75)
    IQR = quart3 - quart1  # Inter-quartile range
    low_val = quart1 - 1.5 * IQR
    high_val = quart3 + 1.5 * IQR
    df_out = ds.loc[(ds[col] > low_val) & (ds[col] < high_val)]
    df_out.dropna(axis=0, how='any')
    return df_out
```

该程序是一个函数，接受两个参数：数据集 (`ds`) 和列名 (`col`)。该函数旨在使用四分位距 (`IQR`) 方法从数据集的给定列中移除异常值。函数执行以下步骤。
