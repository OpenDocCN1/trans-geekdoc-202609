
让我们进行实验，在数据中引入不同的离群值，并观察皮尔逊相关和斯尔曼相关是如何受影响的。

![](img/43582740ac1227a817786ef73e0f772_215_0)

从之前的图中，你可以清楚地定义离群值。让我们考虑皮尔逊相关和斯尔曼相关是如何受影响的。以下命令代表皮尔逊相关：

```python
>>> stats.pearson(mpg, hp)
(0.4741530489143548, 0.00461221679473484862)
```

以下是斯尔曼相关：

```python
>>> stats.spearman(mpg, hp)
(-0.89466464574996252, 5.08596943092453e-12)
```

你现在可以看到皮尔逊相关明显受到了离群值的影响，相关性从0.89降到了0.47。斯尔曼相关没有受影响，尽管它是基于数据中的顺序而非实际值。

# Z检验 vs T检验

在验证假设假设之前，你已经进行了几次Z检验。

![](img/43582740ac1227a817786ef73e0f772_216_0.png)

T分布类似于Z分布。

当样本较小时使用T检验。

Z检验用于比较总体均值。

# F分布

这种分布也被称为Snedecor F。

统计量由以下公式提供：

$$f = \frac{s_1^2/n_1}{s_2^2/n_2}$$

在以下案例中，s1是指具有n1的样本1的标准差，s2是样本的标准差。d1和d2代表此图中的自由度：

![](img/43582740ac1227a817786ef73e0f772_217_0.png)

# 卡方分布

这种分布使用以下公式定义：

$\chi^2 = (n-1)s^2/\sigma^2$

在以下案例中，n是指样本大小，s代表样本的标准差，$\sigma$是总体的标准差。

如果你反复抽取样本并定义卡方统计量，那么你可以创建一个卡方分布，它由以下概率函数描述：

$Y = Y_0 X^{(v/2-1)} e^{-X/2}$

# 卡方拟合优检验

卡方检验可以测试观测数据是否与期望数据有显著差异。例如，骰子掷了36次，每个面朝上的概率为1/6。因此，期望分布如下：

| 期望频率 | 结果 |
| :--- | :--- |
| 6 | 1 |
| 6 | 2 |
| 6 | 3 |
| 6 | 4 |
| 6 | 5 |
| 6 | 6 |

观测分布包含以下：

| 观测频率 | 结果 |
| :--- | :--- |
| 7 | 1 |
| 5 | 2 |
| 3 | 3 |
| 9 | 4 |
| 6 | 5 |
| 6 | 6 |

卡方检验中的零假设是观测值与期望值相似。

卡方可以使用SciPy包中的`chisquare`函数进行：

```python
>>> stats.chisquare(observed,expected)
(3.3333333333333335, 0.64874235866759344)
```

第一个值是卡方值，第二个值是p值，它非常高。换句话说，原假设是有效的，观测值与期望值相似。

## 第 5 章：Python 库-Pygal

### 为什么要使用 Pygal？

在 Python 开发中，有很多用于图图的库（Matplotlib 和 plotly 只是其中几个例子），并且为其中许多库都创建了不同的资源。由于这是一本关于数据图表的介绍，你需要一个易于使用的库，让 Python 图表初级开发者能够遵循提供的代码。

Pygal 是一个由 Kozea 开发的基于 Python 的 SVG 图表创建器。这是一个致力于构建高质量开源库的社区，主要基于 Python。

Pygal 库提供了标准图表定义之外的多种图表选项：折线图、饼图和柱状图。它还包含了世界地图、雷达图、箱线图和漏斗图。它还带有预置的主题和样式，如果不强制要求，你不需要自定义。此外，由于图表库的输出是 SVG，这使其成为 HTML5 甚至打印媒体的灵活输出格式。Python 语言图表库的一个问题是输出默认为特定图像大小的 PNG 格式。由于 SVG 是矢量图形，可以根据任何需要进行缩放和调整大小，而不损坏质量。

你可以访问 `http://pygal.org/` 网站。

Pygal 网站由美观且易读的文档组成。第三方 Python 库的一个明显特征是，文档可以是记录良好的、在线可搜索的 wiki，也可以是只揭示如何安装库的 readme.txt 文件。此外，Pygal 库不需要过多的依赖项，这对于一本介绍性书籍来说很重要。

许多 Python 框架选择挑剔的依赖项，你可能在项目可能需要它们，但它们可能与你的系统兼容或兼容。

`lxml` 库是 pygal 唯一需要的库，但取决于你执行 Python 代码的操作系统，它会有一些问题。在直接开始安装 pygal 之前，花时间重新阅读关于 `lxml` 的说明是非常重要的。

### 使用 Pip 安装 Pygal

首先，如果你还没有安装 `lxml`，且你正在 Windows 上工作，你可能需要安装 `lxml` 安装程序。否则，这些命令将帮助你安装 `lxml`。接下来，你需要使用以下命令针对 Mac 和 Windows 系统应用 pip 并安装 pygal。

如果你使用的是 Windows 笔记本电脑，输入以下命令：

`pip install pygal`

如果你在 Ubuntu 上工作，输入以下命令：

`sudo pip install pygal`

接下来，打开带有 PyDev 的 Eclipse 并启动一个新的 Python 项目。一旦创建了项目，创建一个新文件，将其命名为 `importtest.py`，并输入以下命令：

`import pygal`

完成后，你应该按下 `CTRL + Space` 并看到 PyDev 的代码补全。此截图说明了 pygal 在系统中的排列情况：

![](img/43582740ac1227a817786ef73e0f3772_220_0.png)

### 使用 Visual Studio 的 Python 工具安装 Pygal

如果你计划使用 Visual Studio，这里有一个关于安装的说明。首先，如果你还没有安装 `lxml`，请在“安装 Python 包”窗口中通过你的 Python 环境运行 `easy_install`，如下截图所示：

![](img/43582740ac1227a817786ef73e0f3772_221_0.png)

如果成功，则安装 pygal 库。你可以在环境内部右键点击并选择“安装 Python 包”，这次使用 `pygal`，如截图所示：

![](img/43582740ac1227a817786ef73e0f3772_221_1.png)

### 创建折线图

通常情况下，折线图表示给定数据在不同时间间隔内的变化情况。在制作图表时，这是你创建的最简单的图表。它由 x 轴和 y 轴组成，图表上的每个轴表示时间、取值或不同的参数。

让我们创建一个关于网站在过去两年内点击次数的简单图表。看看这段代码的第一行。那是 Python 解释器的一条声明式语句，用于描述到文件的字符串编码。此外，你会发现 `online.x_labels` 你应用了一个名为 `range()` 的内联函数。这允许你构建一个数字数组，从最低数字到最高数字。在这种情况下，2012 和 2014 将以数组形式输出 2012, 2013, 2014。现在，将此代码复制到你项目的主 Python 文件中：

```python
# -*- coding: utf-8 -*-
import pygal
#创建一个新的折线图。
line = pygal.Line()
line.title = 'Website hits in the past 2 years' #设置图表标题
line.x_labels = map(str, range(2012, 2014)) #设置x 轴标签
line.add('Page views', [None, 0, 12, 32, 72, 148]) #设置值。
line.render_to_file('linechart.svg') #设置文件名。
```

截图展示了一个基础的 pygal 折线图输出：

![](img/43582740ac1227a817786ef73e0f3772_222_0.png)

你会发现 `online.x_labels` 你应用了一个名为 `range()` 的内联函数。这允许你构建一个数字数组，从最低数字到最高数字。在这种情况下，2012 和 2014 将以数组形式输出 2012, 2013, 2014。

---

### 堆叠折线图（Stacked Line Charts）

堆叠折线图的操作方式与折线图相似，不同之处在于它将许多数据堆叠在一起。将以下代码添加到你的函数中：

```python
# -*- coding: utf-8 -*-
import pygal
#创建一个新的堆叠折线图。
line = pygal.StackedLine(fill=True)
line.title = 'Website hits in the past 2 years' #设置图表标题
line.x_labels = map(str, range(2012, 2014)) #设置x 轴标签
line.add('Site A', [None, 0, 12, 32, 72, 148]) #设置值。
line.add('Site B', [2, 16, 12, 87, 91, 342]) #设置值。
line.add('Site C', [42, 55, 84, 88, 90, 171]) #设置值。
line.render_to_file('linechart.svg') #设置文件名。
```

![](img/43582740ac1227a817786ef73e0f3772_224_0.png)

部署后，你的堆叠图将像之前的截图所示。打开你的项目目录确定 `linechart.svg` 文件。

### 简单柱状图（Simple Bar Charts）

简单柱状图的应用类似于折线图。此外，它向信息类别展示了值。使用以下代码创建一个简单的柱状图：

```python
# -*- coding: utf-8 -*-
import pygal
#创建一个简单的柱状图。
bar = pygal.Bar()
bar.title = 'Searches for term: sleep'
bar.x_labels = map(str, range(2011, 2015))
bar.add('Searches', [81, 88, 88, 100])
bar.render_to_file('bar_chart.svg')
```

浏览器。请记住代码并没有很大变化。下面的截图展示了术语：“sleep”的结果。

![](img/43582740ac1227a817786ef73e0f3772_225_0.png)

### 堆叠柱状图

与折线图一样，堆叠柱状图按数据顺序将不同的柱形层叠在一起。请在你的 python 脚本文件中添加以下代码。

```python
# -*- - coding: utf-8 -
import pygal

# 创建一个新的堆叠柱状图。
bar = pygal.StackedBar()
bar.title = 'Searches for term: sleep''
bar.x_labels = map(str, range(2011, 2015))
bar.add('Men', [81, 88, 88, 100])
bar.add('Women', [78, 84, 69, 92])
bar.render_to_file('bar_chart.svg')
```

这是运行上述脚本的结果：

![](img/43582740ac1227a817786ef73e0f3772_226_0.png)

由于这是一个堆叠值，你有两组数据。在下面的例子中，是男性和女性的搜索。之前的截图是一个完整的图表，展示了带有术语“sleep”总搜索次数的各种分段值的组合数据集。

### 水平柱状图

这是 pygal 提供的最后一种柱状图，你将应用水平图表并复用你来自简单柱状图中的数据。水平柱状图用于展示某一时间点的数据。因此，你将移除 `x_labels` 属性，因为你只想显示一个月份。现在，添加以下代码并执行你的脚本：

```python
# coding: utf-8 -*
import pygal
# 创建一个新的柱状图。
bar = pygal.HorizontalBar()
bar.title = 'Searches for term: sleep in April'
bar.add('Searches', [81, 88, 88, 100])
bar.render_to_file('bar_chart.svg')
```

打开 `bar_chart.svg` 文件，结果在下方的截图所示：

![](img/43582740ac1227a817786ef73e0f3772_227_0.png)

### XY 图表

XY 图在科学数据中非常流行，用于表示不同时期的众多值。它们也可以显示负值。这些图表可以输出各种集合以增加可读性。现在，使用下面提供的代码创建一个包含两个点的简单 XY 图。

```python
# -*- coding: utf-8 -*
import pygal
xy_chart = pygal.XY()
xy_chart.add('Value 1', [[(-50, -30), (100, 45)])
xy_chart.render_to_file("xy_chart.svg")
```

打开 `xy_chart.svg` 文件。结果如下方的截图所示：

![](img/43582740ac1227a817786ef73e0f3772_228_0.png)
