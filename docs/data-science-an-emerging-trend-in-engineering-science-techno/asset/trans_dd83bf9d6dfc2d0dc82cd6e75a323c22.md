

# 误差棒与统计可视化

正如你所知，任何统计数据不可避免地都包含误差。统计学中的误差简单来说就是测量值与实际值之间的差异。在图表上绘制误差是一种传达更多信息的方式。测量中误差或不确定性的图形表示称为**误差棒**。它是从数据点引出的一条线（有时是一条带帽线）。线的长度显示了测量的精确程度。较短的误差棒意味着数值集中，数据可靠。较长的误差棒表明数值分散，数据很可能包含误差。

幸运的是，`matplotlib` 允许我们向各种图表添加误差棒。它们可应用于：

*   折线图
*   面积图
*   直方图
*   柱状图
*   散点图
*   点图

## 密度图

![density plot](image_rsrc9VX.jpg)
![density plot](image_rsrc9VX.jpg)
![density plot](image_rsrc9VX.jpg)
![](image_rsrc9VY.jpg)

**图 5.4 (a) 密度图**

### 描述

也称为**核密度图**或**密度轨迹图**。

密度图可视化数据在连续区间或时间段内的分布。该图表是[直方图](https://datavizcatalogue.com/methods/histogram.html)的一种变体，它使用[核平滑](https://en.wikipedia.org/wiki/Kernel_smoother)来绘制数值，通过平滑噪声从而得到更平滑的分布。密度图的峰值有助于显示数值在区间内集中的位置。

密度图优于直方图的一个优势是，它们更擅长确定[分布形状](https://en.wikipedia.org/wiki/Shape_of_the_distribution)，因为它们不受所用箱数（典型直方图中使用的每个柱子）的影响。仅包含 4 个箱的直方图无法像 20 个箱的直方图那样产生足够可辨别的分布形状。然而，使用密度图则不存在这个问题。

### 结构

![](image_rsrc9VZ.jpg)

**图 5.4(b) 直方图形式的密度图**

## 5.5 使用 Matplotlib 绘制等高线图 – Python

等高线图，也称为水平面图，是一种用于进行多元分析并在二维空间中可视化三维图表的工具。如果我们将 X 和 Y 视为要绘制的变量，那么响应 Z 将作为切片绘制在 X-Y 平面上，因此等高线有时被称为**Z 切片**或**等响应线**。

等高线图广泛用于可视化密度、海拔或山脉高度，以及在气象部门。由于这种广泛的用途，`matplotlib.pyplot` 提供了 `contour` 方法，使我们能够轻松绘制等高线图。

### `matplotlib.pyplot.contour`

当 `Z = f(X, Y)` 即 Z 随输入 X 和 Y 的函数而变化时，`matplotlib.pyplot.contour()` 通常很有用。`contourf()` 也可用，它允许我们绘制填充等高线。

**语法：** `matplotlib.pyplot.contour([X, Y,] Z, [levels], **kwargs)`

**参数：**

*   **X, Y：** 与 Z 形状相同的二维 numpy 数组，或一维数组，使得 `len(X)==M` 且 `len(Y)==N`（其中 M 和 N 是 Z 的行数和列数）
*   **Z：** 绘制等高线所依据的高度值。形状为 (M, N)
*   **levels：** 决定等高线/区域的数量和位置。

以下示例演示了 matplotlib.pyplot 中 `matplotlib.pyplot.contour()` 函数的用法：

#### 示例 #1：使用 `contour()` 绘制等高线，仅绘制等高线。

```
# matplotlib 函数的实现
import matplotlib.pyplot as plt
import numpy as np

feature_x = np.arange(0, 50, 2)
feature_y = np.arange(0, 50, 3)

# 创建特征的二维网格
[X, Y] = np.meshgrid(feature_x, feature_y)

fig, ax = plt.subplots(1, 1)
Z = np.cos(X / 2) + np.sin(Y / 4)

# 绘制等高线
ax.contour(X, Y, Z)
ax.set_title('Contour Plot')
ax.set_xlabel('feature_x')
ax.set_ylabel('feature_y')
plt.show()
```

**输出：**

![Example 1](image_rsrc9W0.jpg)

**图 5.5(a) 等高线图**

#### 示例 #2：使用 `contourf()` 绘制等高线，绘制填充等高线。

```
# matplotlib 函数的实现
import matplotlib.pyplot as plt
import numpy as np

feature_x = np.linspace(-5.0, 3.0, 70)
feature_y = np.linspace(-5.0, 3.0, 70)

# 创建特征的二维网格
[X, Y] = np.meshgrid(feature_x, feature_y)

fig, ax = plt.subplots(1, 1)
Z = X ** 2 + Y ** 2

# 绘制填充等高线图
ax.contourf(X, Y, Z)
ax.set_title('Filled Contour Plot')
ax.set_xlabel('feature_x')
ax.set_ylabel('feature_y')
plt.show()
```

**输出：**

![Example 2](image_rsrc9W1.jpg)

**图 5.5 (b) 填充等高线图**

## 5.6 直方图、分箱与密度

简单的直方图可以成为理解数据集的绝佳第一步。在完成常规的样板导入后，Matplotlib 的直方图函数可在一行代码中创建基本直方图：

```
%matplotlib inline
import numpy as np
import matplotlib.pyplot as plt

plt.style.use('seaborn-white')
data = np.random.randn(1000)
```

![](image_rsrc9W2.jpg)

**图 5.6(a) 自定义直方图**

`hist()` 函数有许多选项可调整计算和显示；下面是一个更定制化的直方图示例：

```
plt.hist(data, bins=30, normed=True, alpha=0.5,
         histtype='stepfilled', color='steelblue',
         edgecolor='none');
```

![](image_rsrc9W3.jpg)

**图 5.6 (b) 阶梯填充直方图**

`plt.hist` 的文档字符串中有关于其他可用定制选项的更多信息。我发现 `histtype='stepfilled'` 结合一定的透明度 `alpha` 在比较多个分布的直方图时非常有用：

```
x1 = np.random.normal(0, 0.8, 1000)
x2 = np.random.normal(-2, 1, 1000)
x3 = np.random.normal(3, 2, 1000)

kwargs = dict(histtype='stepfilled', alpha=0.3, normed=True, bins=40)

plt.hist(x1, **kwargs)
plt.hist(x2, **kwargs)
plt.hist(x3, **kwargs);
```

![](image_rsrc9W4.jpg)

**图 5.6(c) 随机直方图**

如果你只是想计算直方图（即计算给定箱内的点数）而不显示它，可以使用 `np.histogram()` 函数：

```
counts, bin_edges = np.histogram(data, bins=5)
print(counts)
# [ 12 190 468 301  29]
```

### 二维直方图与分箱

正如我们通过将数轴分成箱来创建一维直方图一样，我们也可以通过将点分配到二维箱中来创建二维直方图。我们将简要介绍几种实现方法。首先定义一些数据——从多元高斯分布中抽取的 x 和 y 数组：

```
mean = [0, 0]
cov = [[1, 1], [1, 2]]
x, y = np.random.multivariate_normal(mean, cov, 10000).T
```

#### `plt.hist2d`：二维直方图

绘制二维直方图的一个直接方法是使用 Matplotlib 的 `plt.hist2d` 函数：

```
plt.hist2d(x, y, bins=30, cmap='Blues')
counts, xedges, yedges = np.histogram2d(x, y, bins=30)
cb = plt.colorbar()
cb.set_label('counts in bin')
```

![](image_rsrc9W5.jpg)

**图 5.6(d) 二维直方图**

正如 `plt.hist` 一样，`plt.hist2d` 也有许多额外选项来微调绘图和分箱，这些在函数文档字符串中都有很好的说明。此外，正如 `plt.hist` 在 `np.histogram` 中有对应函数一样，`plt.hist2d` 在 `np.histogram2d` 中也有对应函数，用法如下：

```
counts, xedges, yedges = np.histogram2d(x, y, bins=30)
```

关于二维以上维度的直方图分箱泛化，请参阅 `np.histogramdd` 函数。

#### `plt.hexbin`：六边形分箱

二维直方图在坐标轴上创建了方形的镶嵌。另一种天然适合这种镶嵌的形状是正六边形。为此，Matplotlib 提供了 `plt.hexbin` 例程，它将在六边形网格中对二维数据集进行分箱表示：

```
plt.hexbin(x, y, gridsize=30, cmap='Blues')
cb = plt.colorbar(label='count in bin')
```

![](image_rsrc9W6.jpg)

