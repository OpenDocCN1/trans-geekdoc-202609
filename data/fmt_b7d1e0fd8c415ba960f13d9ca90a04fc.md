
处理新数据集的第一件事是确定其大小和形状。清单 2-1 展示了用于确定 UC Irvine 数据存储库中“Rocks versus Mines”数据集（即岩石与水雷数据）大小和形状的代码。本章稍后你将了解更多关于该数据集的信息，并且全书将在介绍算法时使用它作为示例。在这种情况下，确定行数和列数的过程非常简单。该文件以逗号分隔，一个实验的数据占据一行文本。这使得读取一行、按逗号分隔符拆分、并将生成的列表堆叠成一个包含整个数据集的外层列表变得非常容易。

#### 清单 2-1：评估新数据集规模 — rockVmineSummaries.py

```python
__author__ = 'mike_bowles'

#read data from uci data repository
xList = list_read_rvm()
  
print('Number of Rows of Data = ' + str(len(xList)))
print('Number of Columns of Data = ' + str(len(xList[1])))

Printed Output:
Number of Rows of Data = 208
Number of Columns of Data = 61 
```

正如示例输出所示，该数据集有 208 行（行数）和 61 列（每行字段数）。这有什么区别？行数和列数对后续步骤有多方面影响。首先，整体规模能让你大致了解训练时间会有多长。对于像岩石与水雷数据这样小的数据集，训练时间将少于一分钟，这将便于你迭代训练和调整的过程。如果数据集增长到 1,000 x 1,000，惩罚线性回归的训练时间将增长到几分之一分钟，而集成方法则需要几分钟。当数据集达到数万行和列时，惩罚线性回归的训练时间将扩展到 3 或 4 小时，集成方法则为 12 到 24 小时。较大的训练时间会影响你的开发时间，因为你需要迭代多次。

关于行数和列数的第二个重要观察是，如果数据集的列数远多于行数，你可能更有可能通过惩罚线性回归获得最佳预测，反之亦然。第 3 章 “预测模型构建：平衡性能、复杂性与大数据” 以及稍后你将运行的示例将让你更好地理解为什么会这样。

检查清单的下一步是确定有多少列数据是数值型与分类型。清单 2-2 展示了针对岩石与水雷数据集实现此目的的代码。该代码遍历每一列，统计数值型条目（`int` 或 `float`）、非空字符串条目以及空条目的数量。结果显示前 60 列全为数值，最后一列全为字符串。这些字符串值即为标签。通常，分类变量以字符串形式呈现，如此例所示。在某些情况下，二值分类变量会呈现为 0、1 数值变量。

#### 清单 2-2：确定属性性质 — rockVmineContents.py

### 岩石与地雷数据集的统计摘要

在确定哪些属性是分类属性、哪些是数值属性之后，你需要获取数值变量的描述性统计信息，以及每个分类属性中唯一类别的计数。清单 2-3 给出了这两个过程的一些示例。

#### 清单 2-3：数值与分类属性的汇总统计 — rVMSummaryStats.py

```python
__author__ = 'mike_bowles'
import numpy as np

#read data from uci data repository
xList = list_read_rvm()
 
nrow = len(xList)
ncol = len(xList[1])

type = [0]*3
colCounts = []

#generate summary statistics for column 3 (e.g.)
col = 3
colData = []
for row in xList:
    colData.append(float(row[col]))

colArray = np.array(colData)
colMean = np.mean(colArray)
colsd = np.std(colArray)
print("Mean = " + '\t' + str(colMean) + '\t\t' +
            "Standard Deviation = " + '\t ' + str(colsd))


#calculate quantile boundaries
ntiles = 4

percentBdry = []

for i in range(ntiles+1):
    percentBdry.append(np.percentile(colArray, i*(100)/ntiles))

print("\nBoundaries for 4 Equal Percentiles")
print(percentBdry)
print(" \n")
```

**打印输出：**

```
Mean =      0.053892307692307684             
Standard Deviation =       0.04641598322260027 

Boundaries for 4 Equal Percentiles
[0.0058, 0.024375, 0.04405, 0.0645, 0.4264]
 
 
Boundaries for 10 Equal Percentiles 

[0.0058, 0.0141, 0.022740000000000003, 0.027869999999999995, 0.03622, 
0.04405, 0.050719999999999, 0.0599599999999999, 0.07794000000000001, 
0.10836, 0.4264]
 
 
Unique Label Values
{'M', 'R'}

Counts for Each Value of Categorical Label
['M', 'R']
[111, 97] 
```

代码的第一部分选取一列数值数据，然后为其生成一些统计信息。第一步是计算所选属性的`均值`和`标准差`。了解这些将为你在开发模型时建立直觉提供基础。

代码的下一部分用于寻找`离群值`。其工作原理如下。假设你试图判断以下数字列表中是否存在离群值：`[0.1, 0.15, 0.2, 0.25, 0.3, 0.35, 0.4, 4]`。此示例特意构造了一个离群值。最后一个数字（`4`）与其他数字相比显然超出了量级。

揭示此类不匹配的一种方法是将一组数字划分为百分位数。例如，第 25 百分位包含最小的 25% 的数据。第 50 百分位包含最小的 50% 的数据。可视化这些分组形成过程的最简单方法是想象数据已按数值顺序排序。前面列表中的数字已按数值顺序排列。这使得很容易看出百分位边界的位置。一些常用的百分位数有特殊的名称。将集合划分为相等的四分之一、五分之一和十分之一所定义的百分位数分别称为`四分位数`、`五分位数`和`十分位数`。

对于前面的列表，因为列表已排序且包含八个元素，所以很容易定义四分位数。第一四分位数包含 `0.1` 和 `0.15`，以此类推。请注意这些四分位数的宽度。第一四分位数的范围是 `0.5`（`0.15–0.1`）。第二四分位数大致相同。然而，最后一个四分位数的范围是 `4.6`，这是其他四分位数范围的 100 倍。

你可以在清单 2-3 中计算出的四分位边界中看到类似的行为。首先程序计算四分位数。这显示出上四分位数比其他四分位数宽得多。为了更确定，还计算了十分位边界，同样表明上十分位异常宽。由于分布在尾部通常会变稀疏，因此一定程度的变宽是正常的。

#### 使用分位数-分位数图可视化离群值

更详细地研究离群值的一种方法是，将相关数据的分布与某些合理的分布进行绘图对比，以查看相对数值是否匹配。清单 2-4 展示了如何使用 Python 函数 `probplot` 来帮助确定数据集是否存在离群值。生成的图表显示了数据中经验百分位数相关的边界与高斯分布相同百分位数的边界之间的比较。如果被分析的数据来自高斯分布，绘制的点将落在一条直线上。图 2.1 显示，岩石与地雷数据第 4 列的几个点距离该直线非常远。这意味着岩石与地雷数据的尾部包含的样本比高斯密度的尾部更多。

#### 清单 2-4：岩石与地雷数据第 4 个属性的分位数-分位数图 — qqplotAttribute.py

```python
__author__ = 'mike_bowles'
import numpy as np

import scipy.stats as stats

#read rocks v mines data
xList = list_read_rvm()
nrow = len(xList)
ncol = len(xList[1])

type = [0]*3
colCounts = []

#generate summary statistics for column 3 (e.g.)
col = 3
colData = []
for row in xList:
    colData.append(float(row[col]))


stats.probplot(colData, dist="norm", plot=plt)
plt.show() 
```

![Figure 2.1: Quantile-quantile plot of attribute 4 from rocks versus mines data](img/c02f001.png)

**Figure 2.1**：岩石与矿山数据中属性 4 的分位数-分位数图

如何利用这些信息？异常值可能会给模型构建或预测带来麻烦。在该数据集上训练好模型后，你可以检查模型产生的误差，看这些误差是否与这些异常值相关。如果相关，则可以采取措施进行修正。例如，你可以复制表现不佳的样本，迫使它们得到更充分的代表。你可以将它们隔离出来，作为一个单独的类别进行训练。如果它们代表的是一种异常情况，且在模型部署后将要面对的数据中不会出现，你也可以将它们从数据中剔除。一个合理的流程可能是在探索阶段生成四分位数边界，并标记潜在的异常值，以了解问题可能有多严重（或者根本不严重）。然后在评估性能数据时，使用分位数-分位数（Q-Q）图来确定哪些点应被称为异常值，以便用于误差分析。

### 分类属性的统计特征描述

上述过程适用于数值属性。但分类属性怎么办？你需要检查它们有多少个类别，以及每个类别有多少个样本。了解这些有几个原因。性别属性只有两个可能值（男性和女性），但如果该属性是美国的州，就会有 50 个可能的类别。随着属性数量的增加，处理它们的复杂性也会增加。大多数二叉树算法（集成方法的基础）都限制了能处理的类别数量。由 Breiman 和 Cutler（该算法的发明者）编写的流行 Random Forests 包将类别数量限制在 32 个。如果某个属性有超过 32 个类别，你就需要对它们进行聚合。

稍后你会看到，训练涉及随机抽取数据子集并在其上训练一系列模型。例如，假设类别是美国的州，而爱达荷州只有两个样本。随机抽取训练样本可能一个爱达荷州的样本也抽不到。你需要在问题发生前就发现这类问题，以便加以解决。对于爱达荷州的这两个样本，你可以将它们与蒙大拿州或怀俄明州合并，可以复制它们，或者可以管理随机抽取过程，以确保抽到爱达荷州的样本（这一过程称为`分层抽样`）。

### 如何使用 Python Pandas 对岩石与矿山数据集进行汇总

Python 包 pandas 可以帮助自动化数据检查和处理过程。它在数据检查和预处理的早期阶段特别有用。pandas 包使得将数据读入一种称为`数据框`的专用数据结构成为可能。数据框是仿照 CRAN-R 中同名数据结构建模的。

你可以把数据框想象成 **Table 2.1** 所示的表格或矩阵状结构。数据框的行代表单个案例（实验、样本、测量），列代表特定属性。该结构类似矩阵，但不是矩阵，因为不同列中的元素可能属于不同类型。从形式上讲，矩阵定义在一个域上（如实数、二进制数、复数），矩阵中的所有条目都是该域的元素。对于统计问题，矩阵过于局限，因为统计样本通常包含混合的不同类型。

**Table 2.1** 中的简单示例在 Attribute 1 列中有实数值，在 Attribute 2 列中有分类变量，在 Attribute 3 列中有整数变量。在同一列内，条目类型相同，但不同列之间类型不同。数据框结构支持通过索引访问单个元素，这大致类似于访问 Python `numpy` 数组或列表的列表中的条目。同样，索引切片可用于访问数组中的整行或整列。此外，pandas 数据框还支持通过名称访问行和列。这非常方便，特别是在列数较少到中等的情况下。（搜索“pandas introduction”将提供许多链接，指导你了解 pandas 的基本用法。）

**Listing 2-5** 展示了如何简单地从 UC Irvine 数据存储库网站读取岩石与矿山 CSV 文件。清单中显示的输出是从实际输出中截取的。你可以通过自行运行代码获得完整版本。

#### Listing 2-5: 使用 Python pandas 读取和汇总数据 — pandasReadSummarize.py

```python
__author__ = 'mike_bowles'

#read rocks versus mines data into pandas data frame
rocksVMines = pd_read_rvm()

#print head and tail of data frame
print(rocksVMines.head())
print(rocksVMines.tail())

#print summary of data frame
summary = rocksVMines.describe()
print(summary)
```

读取文件后，程序的第一部分会打印出数据集的前几行和后几行。请注意，所有前几行的示例都带有 R 标签，而后几行的示例带有 M 标签。在这个数据集中，所有的 R 都排在前面，所有的 M 都排在后面。在检查数据时要注意这类情况。你将在后续章节看到，确定模型质量需要对数据进行采样。数据存储方式中的结构可能需要纳入你后续采样方法的考量中。代码片段的最后一部分打印出了数据集中实值列的摘要统计。

Pandas 使得自动计算均值、方差和分位数成为可能。请注意，`describe` 函数生成的摘要本身就是一个数据帧，因此你可以自动化筛选包含异常值属性的过程。为此，你可以比较不同分位数之间的差异，如果某属性的任意差异与该属性的其他差异相比超出了比例尺度，则标记该属性。输出中显示的属性表明，其中几个存在异常值。值得进一步查看涉及异常值的行数。它们可能都来自少数几个示例。这可以指出需要更仔细检查的数据。

## 可视化岩石与地雷数据集的属性

可视化有时能让你洞察到在数字表格中难以发现的数据规律。本节介绍几种你可能会觉得有用的可视化方法。其中一些可视化在分类问题和回归问题中略有不同。你将在介绍鲍鱼数据集和红酒质量数据集的章节中看到这些方法的回归变体。

### 使用平行坐标图进行可视化

一种适用于属性数量超过几个的问题的可视化方法称为`平行坐标图`。图 2.2 展示了平行坐标图的构建过程。图右侧的数字向量代表机器学习数据集中一行属性数据。该数字向量的平行坐标图显示在图 2.2 的折线图中。折线图绘制了每个属性的值与其索引的关系。整个数据集的平行坐标图为数据集中每一行属性绘制一条线。基于标签的颜色编码可以帮助你看清属性值与标签之间某些类型的系统性关系。将一行的实值属性绘制在其属性索引上。（搜索“parallel coordinates”并查看维基百科页面以获取更多示例。）

![Figure 2.2: Constructing a parallel coordinates plot](img/c02f002.png)

**图 2.2**：构建平行坐标图

清单 2-6 展示了该过程在岩石与地雷数据集上的应用。图 2.3 显示了生成的折线图。线条根据其标签进行颜色编码：R（岩石）为蓝色，M（地雷）为红色。有时这种类型的图会显示出类别之间清晰的分离区域。著名的“Iris 数据（鸢尾花数据）”显示出非常清晰的分离，机器学习算法将利用这一点进行分类。对于岩石与地雷数据集，折线图中没有明显的极度清晰的分离，但存在一些蓝色和红色分离的区域。在图表底部，蓝色略微突出，在属性索引 30 到 40 的范围内，蓝色比红色稍高一些。这类洞察有助于解释和验证训练模型做出的预测。

#### 清单 2-6：用于实值属性可视化的平行坐标图 — linePlots.py

```python
__author__ = 'mike_bowles'

#read rocks versus mines data into pandas data frame
rocksVMines = pd_read_rvm()

for i in range(208):
    #assign color based on color based on "M" or "R" labels
    if rocksVMines.iat[i,60] == "M":
        pcolor = "red"
    else:
        pcolor = "blue"

    #plot rows of data as if they were series data
    dataRow = rocksVMines.iloc[i,0:60]
    dataRow.plot(color=pcolor, alpha=0.5)
   
plt.xlabel("Attribute Index")
plt.ylabel(("Attribute Values"))
plt.show() 
```

![Figure 2.3: Parallel coordinates graph of rocks versus mines attributes](img/c02f003.png)

**图 2.3**：岩石与地雷属性的平行坐标图

### 可视化属性与标签之间的相互关系

你可能想问数据的另一个问题是各个属性之间是如何相互关联的。快速了解成对关系的一种方法是将带标签的属性进行交叉绘图。清单 2-7 展示了为几对代表性属性生成交叉图所需的内容。这些交叉图（也称为散点图）能让你看出成对变量之间的关联程度。

#### 清单 2-7：属性成对交叉绘图 — corrPlot.py
