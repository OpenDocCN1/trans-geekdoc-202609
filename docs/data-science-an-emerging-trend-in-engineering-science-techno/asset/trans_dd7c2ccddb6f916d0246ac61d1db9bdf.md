

# 直方图

直方图用于可视化连续数据的分布。直方图是使用 Plotly Express 中的 `histogram()` 函数绘制的。直方图的 `barmode` 参数可以是 “stack”（堆叠）、“group”（分组）或 “relative”（相对）。

根据上述数据，让我们找出每种产品线在各付款方式下的总销售额。请看下面的语法：

```python
fig = px.histogram(sales, x="Product line", y="Total", color='Payment', barmode='group')
fig.show()  # 显示图表
```

这段代码生成如下图表：

![](image_rsrc9X7.jpg)

**图 5.15(a) 各产品线在各付款方式下的总金额**

从上图 5.15(a) 可以看出，家居与生活类产品主要通过电子钱包购买。您可以进一步添加颜色、坐标轴名称、标题等新特性。

![](image_rsrc9X8.jpg)

**图 5.14(b) 展示了 “stack” 与 “group” 两种 barmode 的对比**

![](image_rsrc9X9.jpg)![](image_rsrc9XA.jpg)

**图 5.14(b) — 直方图函数中的柱状模式**

# 柱状图

柱状图的绘制方式与直方图相同，但使用的是 `bar()` 函数。在这里，我们将添加动画帧和更多样式。

![](image_rsrc9XB.jpg)

**图 5.15(c) 柱状图**

点击三角形图标播放动画。

# 饼图

让我们用饼图来查看各产品线的单价。

在此图表中，我使用了 Plotly Express 的颜色序列和标记来使图表边缘变粗。

```python
piec = px.pie(sales, names="Product line", values="Unit price", color_discrete_sequence=px.colors.sequential.Viridis)
piec.update_traces(marker=dict(line=dict(color='#000000', width=2)))
piec.show()
```

上述代码生成如下图表：

![](image_rsrc9XC.jpg)

**图 5.15(d) 饼图**

Plotly 饼图的另一个绝妙功能是，您可以使用 Plotly Graph Objects “拉出” 一个切片。请看下面的示例：

```python
go_fig = go.Figure()
go_fig.add_trace(go.Pie(labels=labels, values=values, pull=[0.2]))
go_fig.update_layout(title_text='Total per Branch')
```

请注意，在下图 5.15(d) 中，分支 A 被拉了出来。

![](image_rsrc9XD.jpg)

**图 5.15(e) — 拉出式饼图**

# 环形图

绘制环形图的语法与饼图相同，但需要添加中间孔洞尺寸作为属性。我们将绘制上述相同的图表并包含 `hole` 参数。

![](image_rsrc9XE.jpg)![](image_rsrc9XF.jpg)

**图 5.15(f) — 环形图**

# 箱线图

箱线图使用 `box()` 函数绘制。在这里，我们将查看各分支的毛收入。下面的代码将显示一个标准箱线图，但您可以通过……更改形状。

```python
fig = px.box(sales, x="Branch", y="gross income", color="Branch", title="Gross income made by branches")
fig.show()
```

![](image_rsrc9XG.jpg)

**图 5.15(g) — 箱线图**

# 5.16 使用 Bokeh 进行 Python 交互式数据可视化：从数据到可视化

使用 Bokeh 构建可视化涉及以下步骤：

*   准备数据
*   确定可视化的渲染位置
*   设置图表
*   连接并绘制数据
*   组织布局
*   预览并保存您精美的数据创作

## 准备数据

任何优秀的数据可视化都始于——您猜对了——数据。如果您需要快速复习 Python 中的数据处理，一定要查看 [Real Python 上不断增加的优秀数据科学教程](https://realpython.com/tutorials/data-science/)。

此步骤通常涉及 [Pandas](https://pandas.pydata.org/) 和 [Numpy](http://www.numpy.org/) 等数据处理库，核心在于采取必要步骤将数据转换为最适合您预期可视化的形式。

## 确定可视化的渲染位置

在此步骤中，您将决定如何生成并最终查看您的可视化。在本教程中，您将了解 Bokeh 提供的两种常用选项：生成静态 HTML 文件和在 [Jupyter Notebook](http://jupyter.org/) 中内联渲染可视化。

## 设置图表

从这里开始，您将组装您的图表，为可视化准备画布。在此步骤中，您可以自定义从标题到刻度标记的所有内容。您还可以设置一套工具，以启用与可视化的各种用户交互。

## 连接并绘制数据

接下来，您将使用 Bokeh 的多种渲染器为数据赋予形状。在这里，您可以灵活地使用众多可用的标记和形状选项从头绘制数据，所有这些都易于自定义。此功能赋予了您在数据表现方面难以置信的创作自由。

此外，Bokeh 还内置了一些功能用于构建诸如 [堆叠柱状图](https://bokeh.pydata.org/en/latest/docs/user_guide/categorical.html#stacked) 之类的图表，并提供了大量示例用于创建更高级的可视化，如 [网络图](https://bokeh.pydata.org/en/latest/docs/user_guide/graph.html) 和 [地图](https://bokeh.pydata.org/en/latest/docs/user_guide/geo.html)。

## 组织布局

如果您需要不止一个图表来表达数据，Bokeh 完全能满足。Bokeh 不仅提供标准的网格布局选项，还允许您仅用几行代码就轻松地将可视化组织成选项卡式布局。

此外，您的图表可以快速链接在一起，因此在一个图表上的选择将反映在其他任意组合的图表上。

## 预览并保存您精美的数据创作

最后，是时候看看您创建了什么了。

无论您是在浏览器还是笔记本中查看可视化，您都能探索可视化、检查自定义设置，并体验添加的任何交互功能。

如果您喜欢所见，可以将可视化保存为图像文件。否则，您可以根据需要重温上述步骤，将您的数据愿景变为现实。

就这些！这六个步骤是整洁、灵活模板的基础模块，可用于将您的数据从表格呈现到大屏幕：

```python
"""Bokeh 可视化模板

此模板是使用 Bokeh 将数据转化为可视化的通用大纲。
"""

# 数据处理
import pandas as pd
import numpy as np

# Bokeh 库
from bokeh.io import output_file, output_notebook
from bokeh.plotting import figure, show
from bokeh.models import ColumnDataSource
from bokeh.layouts import row, column, gridplot
from bokeh.models.widgets import Tabs, Panel

# 准备数据

# 确定可视化的渲染位置
output_file('filename.html')  # 渲染为静态 HTML，或
output_notebook()  # 在 Jupyter Notebook 中内联渲染

# 设置图表
fig = figure()  # 实例化一个 figure() 对象

# 连接并绘制数据

# 组织布局

# 预览并保存
show(fig)  # 看看我做了什么，喜欢的话就保存
```

# 第 6 章

## 6.1 什么是神经网络？

神经网络是人工智能中的一种方法，它教会计算机以一种受人脑启发的方式处理数据。它是一种机器学习过程，称为深度学习，使用分层结构中相互连接的节点或神经元，这种结构类似于人脑。

人工神经网络通常被称为神经网络（NN）。

神经网络实际上是多层感知机。

感知机定义了进入多层神经网络的第一步。

神经网络是深度学习的核心。

神经网络是历史上最重要的发现之一。

### 神经网络模型

输入数据（黄色）针对隐藏层（蓝色）进行处理，并针对另一个隐藏层（绿色）进行修改，以产生最终输出（红色）。

![神经网络](image_rsrc9XH.jpg)

**图 6.1 神经网络模型**

## 6.2 神经网络中的感知机：

