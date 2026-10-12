
```python
df.columns = ['Head_size', 'Brain_weight']
model = smf.ols(formula='Head_size ~ Brain_weight', data=df).fit()
```

### 步骤 5：模型摘要

线性回归模型的所有摘要统计量由 `model.summary()` 方法返回。通过此方法可知 p 值和许多其他值/统计量。通过 `model.summary()` 方法可得出关于数据的预测。

```python
print(model.summary())
```

### 代码实现

```python
###### 导入包
import numpy as np
import pandas as pd
import statsmodels.formula.api as smf

###### 加载 csv 文件
df = pd.read_csv('headbrain1.csv')
print(df.head())

###### 拟合模型
df.columns = ['Head_size', 'Brain_weight']
model = smf.ols(formula='Head_size ~ Brain_weight', data=df).fit()

###### 模型摘要
print(model.summary())
```

**输出：**

![模型摘要输出](img/image_rsrc9WR.jpg)

### 表中部分术语的说明

*   **R-squared 值：** R-squared 值范围在 0 和 1 之间。R-squared 为 100% 表示因变量的所有变化完全由自变量的变化解释。如果 R-squared 值为 1，意味着完美拟合。在我们的例子中，R-squared 值为 0.638。

*   **F-statistic：** F 统计量简单地比较所有变量的综合效应。简单来说，如果你的显著性水平大于 p 值，则拒绝原假设。

*   **coef：** 回归方程中自变量的系数。

### 我们的预测

如果我们将显著性水平 (alpha) 设为 0.05，由于 p < 0.05，我们拒绝原假设并接受备择假设。因此，我们可以得出结论：头围大小与脑重量之间存在关系。

## 5.14 使用 Matplotlib 和 Seaborn 进行 Python 数据可视化

### 数据可视化

有时似乎浏览一组数据点并从中构建洞察会更容易，但通常这个过程可能无法产生良好的结果。由于这一过程，可能会有很多事情未被发现。此外，现实生活中使用的大多数数据集太大，无法进行人工分析。这正是数据可视化发挥作用的地方。

数据可视化是展示数据的一种更简单的方式，无论数据多么复杂，都能借助图形表示来分析变量之间的趋势和关系。

### 数据可视化的优势

*   更容易展示复杂数据
*   突显表现好和表现差的领域
*   探索数据点之间的关系
*   即使对于较大的数据点也能识别数据模式

### 构建可视化的最佳实践

在构建可视化时，始终牢记以下几点是一种良好的实践：

*   确保在构建可视化时适当使用形状、颜色和大小
*   使用坐标系的图表/图形更加突出
*   了解适合数据类型的合适图表类型，能让信息更加清晰
*   使用标签、标题、图例和指示器，能向更广泛的受众无缝传递信息

### Python 库

有许多 Python 库可用于构建可视化，如 `matplotlib`、`vispy`、`bokeh`、`seaborn`、`pygal`、`folium`、`plotly`、`cufflinks` 和 `networkx`。其中，`matplotlib` 和 `seaborn` 似乎被广泛用于基础到中级水平的可视化。

#### Matplotlib

它是一个用于数组 2D 绘图的 Python 可视化库，功能非常强大。它是一个建立在 `NumPy` 数组之上的多平台数据可视化库，旨在与更广泛的 `SciPy` 技术栈协同工作。它由 John Hunter 于 2002 年推出。让我们尝试了解 `matplotlib` 的一些优势和特性：

*   它速度快、效率高，因为它基于 numpy，而且构建起来也更容易
*   自诞生以来经历了开源社区的大量改进，因此是一个拥有高级功能的更好的库
*   维护良好的可视化输出和高质量的图形吸引了大量用户
*   基础和高级图表都可以非常容易地构建
*   从用户/开发者的角度来看，由于它拥有庞大的社区支持，解决问题和调试变得容易得多

#### Seaborn

该库最初在斯坦福大学构思并构建，建立在 `matplotlib` 之上。从某种意义上说，它具有 `matplotlib` 的一些特性，但从可视化的角度来看，它比 `matplotlib` 好得多，并且拥有额外的功能。以下是它的优势：

*   内置主题有助于更好的可视化
*   统计函数有助于获得更好的数据洞察
*   更美观的外观和内置图表
*   具有有效示例的实用文档

### 可视化的性质

根据用于绘制可视化的变量数量和变量类型，我们可以使用不同类型的图表来理解关系。根据变量的数量，我们可以有：

*   **单变量图**（仅涉及一个变量）
*   **双变量图**（需要不止一个变量）

**单变量**图可以用于连续变量，以了解变量的分布和散布情况；而对于离散变量，它可以告诉我们计数。

同样，**双变量**图对于连续变量可以显示相关性等基本统计量；对于连续变量与离散变量的组合，可以得出非常重要的结论，如理解分类变量不同水平下的数据分布。两个离散变量之间也可以绘制**双变量**图。

#### 箱线图

箱线图，也称为箱须图，下图中清晰地展示了箱体和须线。在衡量数据分布方面，它是一种非常好的可视化表示。清晰地绘制了中位数、异常值和四分位数。理解数据分布是另一个有助于构建更好模型的重要因素。如果数据有异常值，箱线图是识别它们并采取必要措施的推荐方法。

##### 语法

```
seaborn.boxplot(x=None, y=None, hue=None, data=None, order=None, hue_order=None, orient=None, color=None, palette=None, saturation=0.75, width=0.8, dodge=True, fliersize=5, linewidth=None, whis=1.5, ax=None, **kwargs)
```

##### 参数

*   `x`, `y`, `hue`：用于绘制长格式数据的输入。
*   `data`：用于绘图的数据集。如果 `x` 和 `y` 缺失，则将其解释为宽格式。
*   `color`：所有元素的颜色。

##### 返回值

它返回绘制了图表的 Axes 对象。

箱须图显示了数据是如何分散的。图表中通常包含五条信息：

1.  最小值显示在图表的最左侧，左侧“须线”的末端
2.  第一四分位数 Q1 是箱体的最左侧（左须线）
3.  中位数显示为箱体中心的一条线
4.  第三四分位数 Q3 显示在箱体的最右侧（右须线）
5.  最大值在箱体的最右侧

正如下面的表示和图表所示，箱线图可以针对一个或多个变量绘制，为我们的数据提供非常好的洞察。

##### 箱线图的表示

![表示多变量分类变量的箱线图](img/image_rsrc9WS.jpg)

*图 5.14 (a) 表示多变量分类变量的箱线图*

![表示多变量分类变量的箱线图](img/image_rsrc9WT.jpg)

*图 5.14 (b) 表示多变量分类变量的箱线图*

```python
######## import required modules
import matplotlib as plt
import seaborn as sns

####### Box plot and violin plot for Outcome vs BloodPressure
_, axes = plt.subplots(1, 2, sharey=True, figsize=(10, 4))

####### box plot illustration
sns.boxplot(x='Outcome', y='BloodPressure', data=diabetes, ax=axes[0])

####### violin plot illustration
sns.violinplot(x='Outcome', y='BloodPressure', data=diabetes, ax=axes[1])
```

![箱线图和小提琴图的输出](img/image_rsrc9WU.jpg)

*图 5.14(c) 箱线图和小提琴图的输出*

```python
####### Box plot for all the numerical variables
sns.set(rc={'figure.figsize': (16, 5)})

####### multiple box plot illustration
sns.boxplot(data=diabetes.select_dtypes(include='number'))
```

![多重箱线图输出](img/image_rsrc9WV.jpg)

*图 14 (d) 多重箱线图输出*

#### 散点图

散点图或散点图是**双变量**图，在构建方式上与折线图有很大相似性。折线图使用 X-Y 轴上的线来绘制连续函数，而散点图依靠点来代表单个数据片段。这些图表非常有利于查看两个变量是否相关。散点图可以是二维的，也可以是三维的。

##### 语法

```
seaborn.scatterplot(x=None, y=None, hue=None, style=None, size=None, data=None, palette=None, hue_order=None, hue_norm=None, sizes=None, size_order=None, size_norm=None, markers=True, style_order=None, x_bins=None, y_bins=None, units=None, estimator=None, ci=95, n_boot=1000, alpha='auto', x_jitter=None, y_jitter=None, legend='brief', ax=None, **kwargs)
```

##### 参数

*   `x`, `y`：输入数据变量，应为数值型。
*   `data`：DataFrame，每列是一个变量，每行是一个观测值。
*   `size`：分组变量，将生成具有不同大小的点。
*   `style`：分组变量，将生成具有不同标记的点。
*   `palette`：分组变量，将生成具有不同标记的点。
*   `markers`：确定如何为不同层级绘制标记的对象。
*   `alpha`：点的比例不透明度。

##### 返回值

此方法返回绘制了图表的 Axes 对象。

##### 散点图的优势

*   显示变量之间的相关性
*   适合大型数据集
*   更容易发现数据聚类
*   更好地代表每个数据点

```python
####### import module
import matplotlib.pyplot as plt

####### scatter plot illustration
plt.scatter(diabetes['DiabetesPedigreeFunction'], diabetes['BMI'])
```

### 数据可视化示例

#### 散点图

##### 2D 散点图

![](img/image_rsrc9WW.jpg)

Fig. 5.14(e) Output 2D Scattered Plot

```python
######## import required modules
from mpl_toolkits.mplot3d import Axes3D
######## assign axis values
x = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
y = [5, 6, 2, 3, 13, 4, 1, 2, 4, 8]
z = [2, 3, 3, 3, 5, 7, 9, 11, 9, 10]
######## adjust size of plot
sns.set(rc={'figure.figsize': (8, 5)})
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.scatter(x, y, z, c='r', marker='o')
######## assign labels
ax.set_xlabel('X Label'), ax.set_ylabel('Y Label'), ax.set_zlabel('Z Label')
######## display illustration
plt.show()
```

##### 3D 散点图

![](img/image_rsrc9WX.jpg)

Fig. 5.14 (f) 3D Scattered Plot

#### 直方图

直方图显示数据的计数，因此类似于条形图。直方图还可以告诉我们数据分布与正态曲线的接近程度。在统计方法中，拥有正态分布或接近正态分布的数据非常重要。然而，直方图本质上是**单变量**的，而条形图是**双变量**的。

条形图将实际计数与类别对应绘制（例如，条形的高度表示该类别中的项目数量），而直方图则在**分箱**中显示相同的分类变量。

分箱是构建直方图的组成部分，它们控制落在某个范围内的数据点。作为一个广泛接受的选择，我们通常将分箱数量限制在 5-20 个，但这完全取决于现有的数据点。

```python
####### illustrate histogram
features = ['BloodPressure', 'SkinThickness']
diabetes[features].hist(figsize=(10, 4))
```

![](img/image_rsrc9WY.jpg)

Fig. 5.14 (g) Output Histogram

#### 计数图

计数图是分类变量与连续变量之间的绘图。这里的连续变量是分类变量出现的次数，即频率。从某种意义上说，计数图可被视为与直方图或条形图密切相关。

##### 语法

```python
seaborn.countplot(x=None, y=None, hue=None, data=None, order=None, hue_order=None, orient=None, color=None, palette=None, saturation=0.75, dodge=True, ax=None, **kwargs)
```

##### 参数

*   `x`, `y`：变量名（在 `data` 中）或向量数据，可选。用于绘制长格式数据的输入。
*   `hue`：可选，用于颜色编码的列名。
*   `data`：可选，`DataFrame`、数组或数组列表。绘图数据集。如果 `x` 和 `y` 缺失，则解释为宽格式；否则预期为长格式。
*   `order`, `hue_order`：可选，字符串列表。绘制分类水平的顺序，否则从数据对象推断。
*   `orient`：可选，"v" | "h"。绘图方向（垂直或水平）。通常从输入变量的数据类型推断，但可用于在“分类”变量为数值型或绘制宽格式数据时指定。
*   `color`：可选，`matplotlib` 颜色。所有元素的颜色，或渐变调色板的种子。
*   `palette`：可选，调色板名称、列表或字典。用于 `hue` 变量不同水平的颜色。应为可被 `color_palette()` 解释的对象，或将 `hue` 水平映射到 `matplotlib` 颜色的字典。
*   `saturation`：可选，浮点值。绘制颜色时原始饱和度的比例。大色块使用稍微降低饱和度的颜色通常效果更好，但如果希望绘图颜色完美匹配输入颜色规范，则设为 1。
*   `dodge`：可选，布尔值。当使用 `hue` 嵌套时，元素是否应沿分类轴移动。
*   `ax`：可选，`matplotlib Axes`。绘图的坐标轴对象，否则使用当前坐标轴。
*   `kwargs`：键值映射。其他关键字参数传递给 `matplotlib.axes.Axes.bar()`。

##### 返回值

返回绘制了图形的 `Axes` 对象。

它仅基于特定类别显示项目的出现次数。在 Python 中，我们可以使用 `seaborn` 库创建计数图。`Seaborn` 是建立在 `matplotlib` 之上的 Python 模块，用于绘制美观的统计图表。

```python
####### import required module
import seaborn as sns
######## assign required values
_, axes = plt.subplots(nrows=1, ncols=2, figsize=(12, 4))
######## illustrate count plots
sns.countplot(x='Outcome', data=diabetes, ax=axes[0])
sns.countplot(x='BloodPressure', data=diabetes, ax=axes[1])
```

![](img/image_rsrc9WZ.jpg)

Fig. 5.14(h) Output Countplot

#### 相关性图

相关性图是一种多变量分析，对于查看数据点间的关系非常方便。散点图有助于理解一个变量对另一个变量的影响。相关性可定义为一个变量对另一个变量的影响。

相关性可以在两个变量之间计算，也可以是一对多相关性，如下图所示。相关性可以是正相关、负相关或无相关，数学范围是从 -1 到 1。理解相关性对模型构建阶段和理解模型输出有非常显著的影响。
