
作为统计摘要列表的替代方案，[清单 2-11](#c02.xhtml#c02-fea-0012) 为每个实数型数据列生成了箱线图。其中第一个如[图 2.9](#c02.xhtml#c02-fig-0009)所示。在[图 2.9](#c02.xhtml#c02-fig-0009)中，统计摘要以箱线图表示，也称为*箱须图*。这些图显示了一个中间穿过一条红线的小矩形。红线标记了该数据列的中位数（或第 50 百分位数）。矩形的顶部和底部分别标记了第 25 百分位数和第 75 百分位数。你可以将打印摘要中的数字与箱线图中的水平线进行比较以确认这一点。在箱体上方和下方，你会看到小的水平刻度，即所谓的须线。这些线绘制在箱体上方和下方 1.4 倍四分位距的位置。四分位距是第 75 百分位数与第 25 百分位数之间的差值。换句话说，箱体顶部到上须线的距离是箱体高度的 1.4 倍。须线的 1.4 倍间距是可调的；请参阅箱线图文档。你会注意到在某些情况下，须线比 1.4 倍间距更近。在这些情况下，数据值并未延伸至计算出的须线位置。在这些情况下，须线放置在最极端的数据点处。在其他情况下，数据延伸至计算出的须线位置相当远的距离之外。这些点可被视为异常值。

![图 2.9：鲍鱼数据集实数型属性的箱线图](images/c02f009.png)

[**图 2.9**](#c02.xhtml#R_c02-fig-0009)：鲍鱼数据集实数型属性的箱线图

[图 2.9](#c02.xhtml#c02-fig-0009)中的箱线图比打印数据更快、更直观地识别异常值，但 rings 属性（最右侧的箱线图）上的刻度导致其他属性被压缩（使其难以看清）。解决此问题的一种方法是直接移除较大刻度的属性。结果如[图 2.10](#c02.xhtml#c02-fig-0010)所示。但这种方法并不令人满意，因为它无法很好地实现自动化或扩展。

![图 2.10：鲍鱼数据集实数型属性的箱线图](images/c02f010.png)

[**图 2.10**](#c02.xhtml#R_c02-fig-0010)：鲍鱼数据集实数型属性的箱线图

[清单 2-11](#c02.xhtml#c02-fea-0012) 代码的最后一部分在绘制箱线图前对所有数据列进行了归一化。这里的*归一化*是指将每一列进行中心化和缩放，使得属性 1 的一个单位意味着与属性 2 的一个单位相同的含义。数据科学中的许多算法和操作都需要这种类型的归一化。例如，K 均值聚类基于数据行之间的向量距离来构建簇。距离是通过将一个点减去另一个点并求平方来测量的。如果单位不同，数值距离也会不同。去杂货店的距离如果用英里衡量可以是 1，如果用英尺衡量则是 5,280。[清单 2-11](#c02.xhtml#c02-fea-0012) 中所示的归一化将变量调整为均值为 0、标准差为 1。这是一种非常常见的归一化。归一化的计算利用了 `summary()` 函数生成的数字。结果绘制在[图 2.11](#c02.xhtml#c02-fig-0011)中。

![图 2.11：归一化后的鲍鱼属性箱线图](images/c02f011.png)

[**图 2.11**](#c02.xhtml#R_c02-fig-0011)：归一化后的鲍鱼属性箱线图

请注意，归一化为标准差 1.0 并不意味着所有数据都落在 -1.0 和 +1.0 之间。它或多或少地将箱体的下边缘和上边缘分别置于 -1.0 和 +1.0 处，但大部分数据位于这些边界之外。

### 回归问题的平行坐标图——可视化鲍鱼问题的变量关系

下一步是了解属性之间以及属性与标签之间的关系。对于岩石与矿石数据，颜色编码的平行坐标图以图形方式描绘了这些关系。该方法需要一些修改才能适用于鲍鱼问题。岩石与矿石是一个分类问题。该问题的平行坐标图根据数据行的真实分类对代表数据行的线条进行颜色编码。这有助于可视化预测目标与预测变量之间的关系。鲍鱼问题是一个回归问题，因此此示例中的颜色编码需要是对应于较高或较低目标值的色调。要为真实值分配色调，真实值需要被压缩到区间 \[0.0, 1.0\] 内。[清单 2-12](#c02.xhtml#c02-fea-0013) 使用 pandas `summary()` 函数生成的最小值和最大值来实现这一点。[图 2.12](#c02.xhtml#c02-fig-0012) 显示了结果。

#### [清单 2-12](#c02.xhtml#R_c02-fea-0013)：鲍鱼数据的平行坐标图 — abaloneParallelPlot.py

```
__author__ = 'mike_bowles'

from math import exp
from Read_Fcns import pd_read_abalone

abalone = pd_read_abalone()

#get summary to use for scaling
summary = abalone.describe()
min_rings = summary.iloc[3,7]
max_rings = summary.iloc[7,7]
nrows = len(abalone.index)

for i in range(nrows):
    #plot rows of data as if they were series data
    data_row = abalone.iloc[i,1:8]
    label_color = (abalone.iloc[i,8] - min_rings) / (max_rings - \
        min_rings)
    data_row.plot(color=plt.cm.RdYlBu(label_color), alpha=0.5)

plt.xlabel("Attribute Index")
plt.ylabel(("Attribute Values"))
plt.show()

#renormalize using mean and standard variation, then compress
# with logit function

mean_rings = summary.iloc[1,7]
sd_rings = summary.iloc[2,7]

for i in range(nrows):
    #plot rows of data as if they were series data
    data_row = abalone.iloc[i,1:8]
    norm_target = (abalone.iloc[i,8] - mean_rings)/sd_rings
    label_color = 1.0/(1.0 + exp(-norm_target))
    data_row.plot(color=plt.cm.RdYlBu(label_color), alpha=0.5) 

plt.xlabel("Attribute Index")
plt.ylabel(("Attribute Values"))
plt.show() 
```

![图 2.12：鲍鱼数据的颜色编码平行坐标图](images/c02f012.png)

[**图 2.12**](#c02.xhtml#R_c02-fig-0012)：鲍鱼数据的颜色编码平行坐标图

[图 2.12](#c02.xhtml#c02-fig-0012) 中的平行坐标图展示了鲍鱼年龄（贝壳环数）与用于预测年龄的可用属性之间的直接关系。生成此图所用的颜色刻度范围从非常深的红褐色，经过较浅的色调、黄色、浅蓝色，到非常深的蓝色。[图 2.11](#c02.xhtml#c02-fig-0011) 中的箱线图显示，最大值和最小值与大部分数据相距甚远。这产生了压缩刻度的效果，使大部分数据在颜色刻度上处于中间范围。尽管如此，[图 2.12](#c02.xhtml#c02-fig-0012) 表明每个属性与每个样本测得的环数之间存在显著相关性。相似的色调在多个属性的相似值处聚集在一起。这种相关性表明你将能够构建一个准确的预测模型。与属性和目标之间总体有利的相关性相反，一些淡蓝色的线条混杂在图表较深橙色区域中，表明存在一些难以正确预测的样本。
