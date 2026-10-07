

![](img/0684d2da98e09085c0a622d4fd69aaad_86_0.png)

图 2-13. 加利福尼亚房价

这张图片告诉我们，房价与位置（例如，靠近海洋）以及人口密度非常相关，这你可能已经意识到了。使用聚类算法来检测主要的聚类，并添加衡量与聚类中心距离程度的新特征，可能会很有用。海洋临近性也可能很有用，尽管在加利福尼亚北部，沿海地区的房价并不太高，所以这并不是一个简单的规则。

## 寻找相关性

由于数据集并不大，你可以使用 `corr()` 方法轻松地计算每对属性之间的标准相关系数（也称为皮尔逊相关系数）：

```
corr_matrix = housing.corr()
```

现在让我们看看每个属性与房屋中位数价值的相关性有多大：

```
>>> corr_matrix["median_house_value"].sort_values(ascending=False)
median_house_value      1.000000
median_Income         0.687121
total_rooms            0.135231
h_median_age             0.114220
households             0.064702
total_bedrooms        0.047865
population             -0.026699
longitude              -0.047279
latitude               -0.142826
```

相关系数的范围从 -1 到 1。当它接近 1 时，意味着存在强烈的正相关性；例如，当中位数收入增加时，房屋中位数价值往往倾向于上升。当系数接近 -1 时，意味着存在强负相关；你可以看到纬度与房屋中位数价值之间存在微小的负相关（即当你向北移动时，价格有轻微下降的趋势）。最后，接近零的系数意味着没有线性相关性。图 2-14 显示了散点图以及横轴和纵轴之间的相关系数。

![](img/0684d2da98e09085c0a622d4fd69aaad_88_0.png)

检查属性之间相关性的另一种方法是使用 Pandas 的 `scatter_matrix` 函数，它会将每个数值属性与其他每个数值属性进行绘图。由于现在有 11 个数值属性，我们得到了 $11^2 = 121$ 张图，这无法放在一页上，所以让我们只关注与中位数相关性最最有前景的属性（图 2-15）：

```python
from pandas.plotting import scatter_matrix

attributes = ["median_house_value", "median_income", "total_rooms", "housing_median_age"]
scatter_matrix(housing[attributes], figsize=(12, 8))
```

![](img/0684d2da98e09085c0a622d4fd69aaad_89_0.png)

图 2-15. 散点矩阵

如果 Pandas 将每个变量与其自身进行绘图，主对角线（左上角到右下角）将充满直线，这并没有什么用。相反，Pandas 显示每个属性的直方图（可以使用其他选项；更多细节请参阅 Pandas 文档）。预测房屋中位数价值最有前景的属性是中位数收入，所以让我们放大它们的相关性图（图 2-16）：

```python
housing.plot(kind='scatter', x='median_income', y='median_house_value', alpha=0.1)
```

这幅图首先揭示了相关性确实非常强；你可以清楚地看到上升趋势，且点分布得不那么分散。其次，我们之前注意到的价格在 $500,000 处作为一条水平线清晰可见。但这张图还揭示了其他不那么明显的直线：一条在 $450,000 左右的线，另一条在 $350,000 左右，可能还有一条在 $280,000 左右，以及在它下面的方的几个。你可能想尝试删除相应的地区，以防止你的算法学习这些特殊特征。

![](img/0684d2da98e09085c0a622d4fd69aaad_90_0.png)

## 属性组合的实验

希望前面的章节能让你了解一些探索数据并获取见解的方法。你识别了一些数据中的异常情况，在将数据输入机器学习算法之前可能想要清理它们，并且你发现了属性与目标属性之间存在有趣的相关性。你还注意到某些属性具有尾部分布，因此你可能想对它们进行转换（例如，计算它们的对数）。当然，每个项目的实际操作会有很大不同，但总体思路是相似的。

在为机器学习算法准备数据之前，你可能还想做的最后一件事是尝试各种组合。例如，如果你不知道一个地区有多少户家庭，那么该地区的卧室总数就没什么用。你真正想要的是每户家庭的房间数。同样，卧室总数本身也是没用的：你可能想将其与房间数进行比较。每户人口似乎也是一个值得关注的有趣组合。让我们创建这些新属性：

```python
housing["rooms_per_household"] = housing["total_rooms"] / housing["households"]
housing["bedrooms_per_room"] = housing["total_bedrooms"] / housing["total_rooms"]
housing["population_per_household"] = housing["population"] / housing["households"]
```

现在让我们看看相关性矩阵：

```python
corr_matrix = housing.corr()
>>> corr_matrix["median_house_value"].sort_values(ascending=False)
median_house_value      1.000000
median_Income         0.687121
total_rooms            0.135231
h_median_age             0.114220
households             0.064702
total_bedrooms        0.047865
population             -0.026699
longitude              -0.047279
latitude               -0.142826
```

