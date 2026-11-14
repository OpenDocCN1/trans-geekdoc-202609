
自2007年推出以来，Scikit-Learn已成为 Python 最著名的开源机器学习库之一。但直到2010年，Scikit-Learn才面向公众发布。Scikit-Learn是一个开源的、基于BSD许可的数据挖掘和数据分析工具，用于在Python上开发监督和非监督机器学习算法。Scikit-learn提供多种机器学习算法，包括“分类”、“回归”、“降维”和“聚类”。它还提供用于特征提取、数据处理和模型评估的模块。

作为“SciPy”库的扩展而设计，Scikit-Learn基于最流行的Python库“NumPy”和“matplotlib”。NumPy扩展了Python，以支持对大型数组和多维矩阵进行高效操作。Matplotlib提供可视化工具，而SciPy提供科学计算模块。对于学术研究，Scikit-Learn很受欢迎，因为它拥有文档齐全、易于使用且灵活的API。开发人员只需修改几行代码，即可利用Scikit-Learn对各种算法进行实验。Scikit-Learn还提供多种训练数据集，使开发人员能够专注于算法，而不是数据收集和清洗。Scikit-Learn的许多算法速度快，可扩展到除超大型数据集外的几乎所有数据集。Scikit-learn以其可靠性而闻名，且该库的大部分提供自动化测试。Scikit-learn在机器学习初学者中非常流行，可用于开始实现简单算法。

## Scikit-Learn库应用的先决条件

Scikit-Learn库基于SciPy（科学Python），在使用Scikit-Learn之前需要先安装它。该技术栈包括以下内容：

## NumPy（基础n维数组包）

NumPy是Python用于科学计算的基础包。它包括（但不限于）：“功能强大的N维数组对象；复杂的（广播）函数；用于集成C/C++和Fortran代码的工具；有用的线性代数、傅里叶变换和随机数功能”。

除了明显的科学用途外，NumPy还被广泛用作通用数据的高效多维容器。可以定义任意数据类型。这使得NumPy能够与各种数据库无缝且快速地集成。NumPy的主要目标是多维数组的同质性。它由一个元素表（通常是数字）组成，所有元素都是同一种类型，并由非负整数元组表示。NumPy的维度称为“轴”，数组类称为“ndarray”。

## SciPy（科学计算的基础库）

SciPy是“基于Python NumPy扩展构建的数学算法和便捷函数集合”。它通过为用户提供高级数据操作和可视化命令与课程，增强了交互式Python会话的影响力。带有SciPy的交互式Python会话成为一个环境，可与“MATLAB、IDL、Octave、R-Lab和SciLab”等系统的数据处理和系统原型设计技术相抗衡。

将SciPy基于Python的额外好处在于，这也使得一种强大的编程语言可用于开发高级程序和特定应用。使用SciPy的科学应用受益于全球开发人员在无数软件领域细分市场中开发额外模块。所生成的一切都已提供给Python程序员，从并行编程到Web和数据库子程序及类。这些强大工具除了SciPy提供的数学库之外还可用。

## IPython（增强型交互式控制台）

IPython（交互式Python）是一种用于多种编程语言进行交互式计算的接口或命令行外壳。它最初是为Python编程语言创建的，支持内省、丰富媒体、shell语法、制表符补全和历史记录。IPython提供的一些功能包括：“交互式外壳（终端和基于Qt的）；带有代码、文本、数学、内联图表和其他媒体支持的基于浏览器的笔记本接口；支持交互式数据可视化和使用GUI工具包；可嵌入到您自己的项目中加载的灵活解释器；用于并行计算的工具”。

## SymPy（符号数学）

由Ondřej Čertík和Aaron Meurer开发，SymPy是“用于符号计算的开源Python库”。它向其他应用提供代数计算功能，既可以作为独立应用程序，也可以作为库，甚至可以作为带有“SymPy Live”或“SymPy Gamma”的在线应用程序。由于SymPy完全使用Python开发，依赖项有限，因此安装和检查都很容易。SymPy涵盖从微积分、代数、离散数学和量子物理到基础符号算术的各种特性。计算结果可以格式化为“LaTeX”代码。

结合一种众所周知语言中简单且可扩展的代码库，SymPy提供的易于访问的特性使其成为一个入门门槛相对较低的计算机代数系统。

## Seaborn（数据可视化）

Seaborn源自Matplotlib库，是一个非常流行的可视化库。它是一个高级库，可以生成特定类型的图表，包括热图、时间序列和小提琴图。

## Matplotlib（全面的2D/3D绘图）

“Matplotlib”是一个来自Python的2D绘图库，可在多种打印格式和交互环境中生成出版质量的图表。“Python脚本”、“Python”和“IPython shell”、“Jupyter笔记本”、Web应用程序服务器以及四种用户界面工具包均可与matplotlib一起使用。Matplotlib致力于进一步简化简单任务并使困难任务可行。只需几行代码，您就可以生成曲线、直方图、功率谱、柱状图、误差图、散点图等。Pyplot模块提供类似MATLAB的接口，以便轻松绘图，尤其是与IPython配合使用时。作为高级用户，您可以通过面向对象的接口或通过类似于提供给MATLAB用户的功能集合来控制整个线条样式、字体属性和坐标轴属性。

要安装Matplotlib，请使用下面列出的pip或conda命令之一：

```
pip install matplotlib
```

```
conda install matplotlib
```

使用Matplotlib可以轻松创建基本图表，如折线图、柱状图和直方图。必须首先导入以下文件：

```
import matplotlib.pyplot as plt
```

下面使用matplotlib创建的图表中使用的“iris”和“wine review”数据集，可以使用pandas的“read_csv”方法导入，如下所示：

```python
import pandas as pd
iris = pd.read_csv('iris.csv', names=['sepal_length', 'sepal_width',
'petal_length', 'petal_width', 'class'])
print(iris.head())
```

| | 萼片长度 | 萼片宽度 | 花瓣长度 | 花瓣宽度 | 类别 |
|---|---|---|---|---|---|
| 0 | 5.1 | 3.5 | 1.4 | 0.2 | iris-setosa |
| 1 | 4.9 | 3.0 | 1.4 | 0.2 | iris-setosa |
| 2 | 4.7 | 3.2 | 1.3 | 0.2 | iris-setosa |
| 3 | 4.6 | 3.1 | 1.5 | 0.2 | iris-setosa |
| 4 | 5.0 | 3.6 | 1.4 | 0.2 | iris-setosa |

```python
wine_reviews = pd.read_csv('winemag-data-130k-v2.csv', index_col=0)
wine_reviews.head()
```

| 国家 | 描述 | 称号 | 评分 | 价格 | 省份 | 产区_1 | 产区_2 | 品酒师姓名 | 品酒师推特账号 | 标题 | 品种 | 酒庄 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Italy | Aromas include tropical fruit, broom, brimstone... | Vulka Blanco | 87 | NaN | Sicily & Sardinia | Etna | NaN | Kerin O'Keefe | @kerinokeefe | Nicosia 2013 Vulka Blanco (Etna) | White Blend | Nicosia |
| Portugal | This is ripe and fruity, a wine that is smooth... | Avidagos | 87 | 15.0 | Douro | NaN | NaN | Roger Voss | @vossroger | Quinta dos Avidagos 2011 Avidagos Red (Douro) | Portuguese Red | Quinta dos Avidagos |
| US | Tart and snappy, the flavors of lime flesh and... | NaN | 87 | 14.0 | Oregon | Willamette Valley | Willamette Valley | Paul Gregutt | @paulgwine | Rainstorm 2013 Pinot Gris (Willamette Valley) | Pinot Gris | Rainstorm |
| US | Pineapple rind, lemon pith and orange blossom ... | Reserve Late Harvest | 87 | 13.0 | Michigan | Lake Michigan Shore | NaN | Alexander Peartree | NaN | St. Julian 2013 Reserve Late Harvest Riesling ... | Riesling | St. Julian |
| US | Much like the regular bottling from 2012, this... | Vinther's Reserve Wild Child Block | 87 | 65.0 | Oregon | Willamette Valley | Willamette Valley | Paul Gregutt | @paulgwine | Sweet Cheeks 2012 Vinther's Reserve Wild Child... | Pinot Noir | Sweet Cheeks |

## 折线图

可以使用“plot”方法在matplotlib中生成折线图。您可以通过循环处理所需的列并将它们全部绘制在同一坐标轴上，在单个图表中绘制多个列。以下是GitHub上可用的“iris”数据集的示例代码及其生成的图表，供您参考。

```python
# getting columns to plot
columns = iris.columns.drop(['class'])
# creation of x data
x_data = range(0, iris.shape[0])
# creation of figure and axis
fig, ax = plt.subplots()
# plotting each column
for column in columns:
    ax.plot(x_data, iris[column], label=column)
# setting title and legend
ax.set_title('Iris Dataset')
```
