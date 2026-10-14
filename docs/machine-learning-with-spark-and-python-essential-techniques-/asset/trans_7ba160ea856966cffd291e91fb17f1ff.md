

> ```
> __author__ = 'mike_bowles'
> 
> #read rocks versus mines data into pandas data frame
> rocksVMines = pd_read_rvm()
> 
> #print head and tail of data frame
> print(rocksVMines.head())
> print(rocksVMines.tail())
> 
> #print summary of data frame
> summary = rocksVMines.describe()
> print(summary)
> ```

读取文件后，程序的第一部分会打印出数据集的前几行和后几行。请注意，所有前几行的示例都带有 R 标签，而后几行的示例带有 M 标签。在这个数据集中，所有的 R 都排在前面，所有的 M 都排在后面。在检查数据时要注意这类情况。你将在后续章节看到，确定模型质量需要对数据进行采样。数据存储方式中的结构可能需要纳入你后续采样方法的考量中。代码片段的最后一部分打印出了数据集中实值列的摘要统计。

Pandas 使得自动计算均值、方差和分位数成为可能。请注意，`describe` 函数生成的摘要本身就是一个数据帧，因此你可以自动化筛选包含异常值属性的过程。为此，你可以比较不同分位数之间的差异，如果某属性的任意差异与该属性的其他差异相比超出了比例尺度，则标记该属性。输出中显示的属性表明，其中几个存在异常值。值得进一步查看涉及异常值的行数。它们可能都来自少数几个示例。这可以指出需要更仔细检查的数据。

## 可视化岩石与地雷数据集的属性

可视化有时能让你洞察到在数字表格中难以发现的数据规律。本节介绍几种你可能会觉得有用的可视化方法。其中一些可视化在分类问题和回归问题中略有不同。你将在介绍鲍鱼数据集和红酒质量数据集的章节中看到这些方法的回归变体。

### 使用平行坐标图进行可视化

一种适用于属性数量超过几个的问题的可视化方法称为*平行坐标图*。[图 2.2](#c02.xhtml#c02-fig-0002) 展示了平行坐标图的构建过程。图右侧的数字向量代表机器学习数据集中一行属性数据。该数字向量的平行坐标图显示在[图 2.2](#c02.xhtml#c02-fig-0002)的折线图中。折线图绘制了每个属性的值与其索引的关系。整个数据集的平行坐标图为数据集中每一行属性绘制一条线。基于标签的颜色编码可以帮助你看清属性值与标签之间某些类型的系统性关系。将一行的实值属性绘制在其属性索引上。（搜索“parallel coordinates”并查看维基百科页面以获取更多示例。）

![Figure 2.2: Constructing a parallel coordinates plot](images/c02f002.png)

[**图 2.2**](#c02.xhtml#R_c02-fig-0002)：构建平行坐标图

[清单 2-6](#c02.xhtml#c02-fea-0007) 展示了该过程在岩石与地雷数据集上的应用。[图 2.3](#c02.xhtml#c02-fig-0003) 显示了生成的折线图。线条根据其标签进行颜色编码：R（岩石）为蓝色，M（地雷）为红色。有时这种类型的图会显示出类别之间清晰的分离区域。著名的“Iris 数据（鸢尾花数据）”显示出非常清晰的分离，机器学习算法将利用这一点进行分类。对于岩石与地雷数据集，折线图中没有明显的极度清晰的分离，但存在一些蓝色和红色分离的区域。在图表底部，蓝色略微突出，在属性索引 30 到 40 的范围内，蓝色比红色稍高一些。这类洞察有助于解释和验证训练模型做出的预测。

#### [清单 2-6](#c02.xhtml#R_c02-fea-0007)：用于实值属性可视化的平行坐标图 — linePlots.py

> ```
> __author__ = 'mike_bowles'
> 
> #read rocks versus mines data into pandas data frame
> rocksVMines = pd_read_rvm()
> 
> for i in range(208):
>     #assign color based on color based on "M" or "R" labels
>     if rocksVMines.iat[i,60] == "M":
>         pcolor = "red"
>     else:
>         pcolor = "blue"
> 
>     #plot rows of data as if they were series data
>     dataRow = rocksVMines.iloc[i,0:60]
>     dataRow.plot(color=pcolor, alpha=0.5)
>   
> plt.xlabel("Attribute Index")
> plt.ylabel(("Attribute Values"))
> plt.show() 
> ```

![Figure 2.3: Parallel coordinates graph of rocks versus mines attributes](images/c02f003.png)

[**图 2.3**](#c02.xhtml#R_c02-fig-0003)：岩石与地雷属性的平行坐标图

### 可视化属性与标签之间的相互关系

