

下面的屏幕截图显示了一个垂直柱状图，它汇总了 600 次掷骰子中每个面出现的频率及其所占百分比。Seaborn 将这种图表称为条形图：

## 掷六面骰子 600 次

![](img/34b7fc2f1ee27beb73bca14927d42340_211_0.png)

这里我们期望每个骰子面出现约 100 次。然而，在掷骰子次数如此少的情况下，没有任何频率正好是 100（尽管有几个很接近），且大多数百分比也不接近 16.667%（约为 1/6）。当我们运行 60,000 次掷骰子的模拟时，柱子的大小会变得非常接近。在 6,000,000 次掷骰子时，它们看起来将大小完全相同。这就是“大数定律”在起作用。下一章将展示柱长度的动态变化。

我们将讨论如何控制图表的外观和内容，包括：

- 窗口内的图表标题（掷六面骰子 600 次），
- x 轴的描述性标签“骰子面值”和 y 轴的描述性标签“频率”，
- 每个柱子上方显示的文本，表示频率和总掷骰次数的百分比，以及
- 柱子的颜色。

我们将使用各种 Seaborn 默认选项。例如，Seaborn 根据骰子面值 1–6 确定 x 轴上的文本标签，并根据实际的骰子频率确定 y 轴上的文本标签。在幕后，Matplotlib 根据窗口大小和柱子所表示数值的大小来确定柱子的位置和大小。它还根据柱子所表示的实际骰子频率来定位 **频率** 轴的数值标签。还有更多可自定义的功能。你应根据个人偏好调整这些属性。

下面的第一个屏幕截图显示了 60,000 次掷骰子的结果——想象一下亲手做这件事有多困难。在这种情况下，我们期望每个面出现约 10,000 次。下面的第二个屏幕截图显示了 6,000,000 次掷骰子的结果——这肯定是你绝不会亲手去做的事情！在这种情况下，我们期望每个面出现约 1,000,000 次，且频率柱看起来长度相同（它们很接近，但并不完全相同）。请注意，掷骰子次数越多，频率百分比就越接近预期的 16.667%。

![](img/34b7fc2f1ee27beb73bca14927d42340_212_0.png)

## 5.17.2 可视化掷骰子频率和百分比

在本节中，你将交互式地开发前一节中显示的条形图。

### 启动 IPython 以进行交互式 Matplotlib 开发

IPython 内置支持交互式开发 Matplotlib 图表，开发 Seaborn 图表也需要它。只需使用以下命令启动 IPython：

```
ipython --matplotlib
```

### 导入库

首先，让我们导入将要使用的库：

- 1. **matplotlib.pyplot** 模块包含我们使用的 Matplotlib 库的绘图功能。该模块通常以名称 `plt` 导入。
- 2. NumPy（Numerical Python）库包含我们将用于汇总掷骰子结果的 `unique` 函数。**numpy** 模块通常作为 `np` 导入。
- 3. `random` 模块包含 Python 的随机数生成功能。
- 4. **seaborn** 模块包含我们使用的 Seaborn 库的绘图功能。该模块通常以名称 `sns` 导入。搜索一下为何选择这个古怪的缩写。

点击此处查看代码图片

```python
In [1]: import matplotlib.pyplot as plt
In [2]: import numpy as np
In [3]: import random
In [4]: import seaborn as sns
```

### 掷骰子并计算骰子频率

接下来，让我们使用 *列表推导式* 创建一个包含 600 个随机骰子值的列表，然后使用 NumPy 的 `unique` 函数来确定唯一的掷骰子值（最可能是所有六个可能的面值）及其频率：

点击此处查看代码图片

```python
In [5]: rolls = [random.randrange(1, 7) for i in range(600)]
In [6]: values, frequencies = np.unique(rolls, return_counts=True)
```

NumPy 库提供了高性能的 **ndarray** 集合，其速度通常远快于列表。1 虽然我们在这里不直接使用 ndarray，但 NumPy 的 `unique` 函数期望一个 ndarray 参数并返回一个 ndarray。如果你传递一个列表（如 `rolls`），NumPy 会将其转换为 ndarray 以获得更好的性能。`unique` 返回的 ndarray 我们将简单地赋值给一个变量，供 Seaborn 绘图函数使用。

指定关键字参数 **return_counts=True** 会告诉 `unique` 统计每个唯一值出现的次数。在这种情况下，`unique` 返回一个包含两个一维 `ndarrays` 的元组，分别包含排序后的唯一值和相应的频率。我们将元组的 `ndarrays` 解包到变量 `values` 和 `frequencies` 中。如果 `return_counts` 为 `False`，则仅返回唯一值列表。

### 创建初始条形图

让我们创建条形图的标题，设置其样式，然后绘制骰子面值和频率：

点击此处查看代码图片

```python
In [7]: title = f'Rolling a Six-Sided Die {len(rolls):,} Times'

In [8]: sns.set_style('whitegrid')

In [9]: axes = sns.barplot(x=values, y=frequencies,      palette='bright')
```

片段 [7] 的 f-string 在条形图的标题中包含掷骰子的次数。下面代码中逗号（,）格式说明符

```
{len(rolls):,}
```

会使用 *千位分隔符* 显示数字——因此，60000 将显示为 60,000。

默认情况下，Seaborn 在纯白色背景上绘制图表，但它提供了多种样式可供选择（'darkgrid'、'whitegrid'、'dark'、'white' 和 'ticks'）。片段 [8] 指定了 'whitegrid' 样式，该样式在垂直条形图中显示浅灰色水平线。这些线条有助于你更轻松地了解每个条形的高度如何对应条形图左侧的数值频率标签。

片段 [9] 使用 Seaborn 的 `barplot` 函数绘制骰子频率。当你执行此片段时，将出现以下窗口（因为你使用 `--matplotlib` 选项启动了 IPython）：

![](img/34b7fc2f1ee27beb73bca14927d42340_215_0.png)

Seaborn 通过创建 Matplotlib Axes 对象来与 Matplotlib 交互以显示条形，该对象管理窗口中出现的内容。在幕后，Seaborn 使用 Matplotlib Figure 对象来管理 Axes 将出现的窗口。barplot 函数的前两个参数分别是包含 x 轴和 y 轴值的 ndarray。我们使用了可选的 palette 关键字参数来选择 Seaborn 预定义的颜色调色板 'bright'。你可以在以下网址查看调色板选项：

https://seaborn.pydata.org/tutorial/color_palettes.html

barplot 函数返回它配置的 Axes 对象。我们将其赋值给变量 axes，以便可以用它来配置最终图表的其他方面。在此点之后对条形图所做的任何更改，在执行相应片段时都会立即显示。

### 设置窗口标题并为 x 轴和 y 轴添加标签

接下来的两个片段为条形图添加了一些描述性文本：

点击此处查看代码图片

```python
In [10]: axes.set_title(title)
Out[10]: Text(0.5,1,'Rolling a Six-Sided Die 600 Times')
```

```python
In [11]: axes.set(xlabel='Die Value', ylabel='Frequency')
Out[11]: [Text(92.6667, 0.5, 'Frequency'), Text(0.5, 58.7667, 'Die Value')]
```

片段 [10] 使用 axes 对象的 set_title 方法在图表上方居中显示标题字符串。该方法返回一个包含标题及其在窗口中位置的 Text 对象，IPython 仅将其显示为输出以供确认。你可以忽略上面片段中的 Out[]。

片段 [11] 为每个轴添加标签。set 方法接收用于设置 Axes 对象属性的关键字参数。该方法沿 x 轴显示 xlabel 文本，沿 y 轴显示 ylabel 文本，并返回一个包含标签及其位置的 Text 对象列表。条形图现在如下所示：

![](img/34b7fc2f1ee27beb73bca14927d42340_216_0.png)

### 完成条形图

接下来的两个片段通过为每个柱子上方的文本腾出空间，然后显示它来完成图表：

点击此处查看代码图片

```python
In [12]: axes.set_ylim(top=max(frequencies) * 1.10)
```

