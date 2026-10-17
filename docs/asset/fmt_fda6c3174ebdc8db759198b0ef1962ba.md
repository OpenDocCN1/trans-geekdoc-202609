
`Listing F.11` 定义了数组 `x`，其中包含一个硬编码的值集合。Pyplot API `plot()` 使用变量 `x` 来显示一组连续的线段。`Figure F.11` 显示了运行第 F.11 部分代码后的结果。

![Figure F.11. ¶ A Set of Connected Line Segments.](img/figF.11.jpg)

Figure F.11. ¶ A Set of Connected Line Segments.

## Plotting Multiple Lines in Matplotlib

`Listing F.12` 显示了 `plt_array2.py` 的内容，该文件说明了在 Matplotlib 中绘制多条线的简便方法。

# LISTING F.12: plt_array2.py

```python
import matplotlib.pyplot as plt
x = [7,11,13,15,17,19,23,29,31,37]
data = [[8, 4, 1], [5, 3, 3], [6, 0, 2], [1, 7, 9]]
plt.plot(data, 'd-')
plt.show()
```

Listing F.12 定义了一个包含硬编码值的数组数据。Pyplot API 的 `plot()` 使用变量 `data` 来显示一条线段。`Figure F.12` 根据 `Listing F.12` 中的代码显示多条线。

![Figure F.12. ¶ Multiple Lines in Matplotlib.](img/figF.12.jpg)

Figure F.12. ¶ Multiple Lines in Matplotlib.

## Trigonometric Functions in Matplotlib

如果你在想，你可以像渲染“普通”图表一样轻松使用 Matplotlib 显示三角函数的图表。`Listing F.13` 展示了 `sincos.py` 的内容，演示如何在 Matplotlib 中绘制正弦函数和余弦函数。

# LISTING F.13: sincos.py

```python
import numpy as np
import math
x = np.linspace(0, 2*math.pi, 101)
s = np.sin(x)
c = np.cos(x)
import matplotlib.pyplot as plt
plt.plot(s)
plt.plot(c)
plt.show()
```

`Listing F.13` 使用 NumPy API 的 `linspace()`、`sin()`、`cos()` 分别初始化变量 `x`、`s`、`c`。随后，Pyplot API 的 `plot()` 使用这些变量绘制正弦函数和余弦函数。

`Figure F.13` 根据 `Listing F.13` 中的代码绘制了两条三角函数的图表。

![Figure F.13 ¶ Sine and Cosine Trigonometric Functions.](img/figF.13.jpg)

Figure F.13 ¶ Sine and Cosine Trigonometric Functions.

现在让我们来看一个由离散数据点组成的简单数据集，这将是下一节的主题。

## 在 Matplotlib 中绘制智商分数 (IQ Scores)

`Listing F.14` 展示了 `iq_scores.py` 的内容，演示如何绘制一个直方图来显示基于正态分布的 IQ 分数。

# LISTING F.14: iq_scores.py

```python
import numpy as np
import matplotlib.pyplot as plt
mu, sigma = 100, 15
x = mu + sigma * np.random.randn(10000)
# the histogram of the data
n, bins, patches = plt.hist(x, 50, normed=1, facecolor='g', alpha=0.75)
plt.xlabel('Intelligence')
plt.ylabel('Probability')
plt.title('Histogram of IQ')
plt.text(60, .025, r'$\mu=100,\\ \sigma=15$')
plt.axis([40, 160, 0, 0.03])
plt.grid(True)
plt.show()
```

`Listing F.14` 定义了标量变量 `mu` 和 `sigma`，随后使用 NumPy 变量 `x` 存储一个随机生成的点集合。接着，通过 `hist()` API 初始化 `n`、`bins`、`patches`，最后使用 `plot()` API 绘制直方图。

`Figure F.14` 根据 `Listing F.14` 中的代码绘制出一个直方图。

![Figure F.14. ¶ A Histogram to Display IQ Scores.](img/figF.14.jpg)

Figure F.14. ¶ A Histogram to Display IQ Scores.

## 在 Matplotlib 中绘制最佳拟合直线

`Listing F.15` 展示了 `plot_best_fit2.py` 的内容，演示如何在 Matplotlib 中绘制最佳拟合直线。

# LISTING F.15: plot-best-fit2.py

```python
import numpy as np
xs = np.array([1,2,3,4,5], dtype=np.float64)
ys = np.array([1,2,3,4,5], dtype=np.float64)
def best_fit_slope(xs,ys):
    m = (((np.mean(xs)*np.mean(ys))-np.mean(xs*ys)) / ((np.mean(xs)**2) - np.mean(xs**2))
    b = np.mean(ys) - m * np.mean(xs)
    return m, b
m,b = best_fit_slope(xs,ys)
print('m:',m,'b:',b)
regression_line = [(m*x)+b for x in xs]
import matplotlib.pyplot as plt
from matplotlib import style
style.use('ggplot')
plt.scatter(xs,ys,color='#0000FF')
plt.plot(xs, regression_line)
plt.show()
```

`Listing F.15` 定义了变量 `xs` 和 `ys`，并将它们传入 `best_fit_slope()` 函数，计算最佳拟合直线的斜率 `m` 和截距 `b`。随后，Pyplot API 的 `scatter()` 显示散点图，`plot()` 显示最佳拟合直线。`Figure F.15` 根据 `Listing F.15` 绘制出一个简单的 2D 数据集的最佳拟合直线。

![Figure F.15. ¶ A Best-Fitting Line for a 2D Dataset.](img/figF.15.jpg)

Figure F.15. ¶ A Best-Fitting Line for a 2D Dataset.

这部分关于 NumPy 和 Matplotlib 的章节至此结束。

下一节将介绍 Sklearn，这是一个基于 Python 的强大机器学习库，支持众多机器学习算法。阅读简短介绍后，后续章节将包含结合 Pandas、Matplotlib 和 Sklearn 内置数据集的 Python 代码示例。

## Introduction to Sklearn (scikit-learn)

Sklearn（安装为 Sklearn）是 Python 最高级的通用机器学习库，其主页位于：

[`scikit-learn.org/stable`](https://scikit-learn.org/stable)

在讨论任何代码示例之前，请记住 Sklearn 是一个极其有用的 Python 库，支持大量机器学习算法。特别是，Sklearn 支持许多分类算法，如逻辑回归、朴素贝叶斯、决策树、随机森林和支持向量机器（SVM）。第 8 章节对大多数分类算法提供了高层次描述。虽然有专门的书籍致力于 Sklearn，但本附录仅包含几页关于 Sklearn 的材料。

如果你想获得关于 Sklearn 的深度知识，请访问包含详细文档的 Web 页面。此外，如果你有关于 Sklearn 的“如何操作”问题，基本上可以在 `stackoverflow.com` 上找到合适的答案。

Sklearn 适用于分类、回归和聚类任务，并提供丰富的机器学习算法，包括线性回归、逻辑回归、kNN（“k 最近邻”）、kMeans、决策树、随机森林、多层感知器（MLP）以及支持向量机器（SVM）。

此外，Sklearn 支持维度降低技术，如主成分分析（PCA）、超参数调优、数据标准化方法，以及适用于数据预处理、交叉验证等操作。

机器学习代码示例通常会结合 Sklearn、NumPy、Pandas 和 Matplotlib。Sklearn 还提供多种内置数据集，可供可视化展示。本附录的下一节将提供几个结合 Pandas、Matplotlib 和 Sklearn 内置 Digits 数据集的 Python 代码示例。

## The Digits Dataset in Sklearn

Sklearn 的 Digits 数据集包含 1,797 张 8×8 的小型手写数字图像，和 MNIST 数据集同样是手写数字。`Listing F.16` 展示了 `load_digits1.py` 的内容，演示如何绘制 Digits 数据集。

# LISTING F.16: load_digits1.py

```python
from sklearn import datasets
# Load in the 'digits' data
digits = datasets.load_digits()
# Print the 'digits' data
print(digits)
```

`Listing F.16` 很简单：导入 `datasets` 模块后，变量 `digits` 初始化为 Digits 数据集的内容。`print()` 语句显示 `digits` 变量的内容，如下所示：

`Listing F.17` 显示了 `load_digits2.py` 的内容，说明如何绘制数字数据集（您可以修改以显示不同的数字）。

# LISTING F.17: load_digits2.py

```python
from sklearn.datasets import load_digits
from matplotlib import pyplot as plt
digits = load_digits()  # set interpolation='none'
fig = plt.figure(figsize=(3, 3))
plt.imshow(digits['images'][66], cmap="gray", interpolation='none')
plt.show()
```

`Listing F.17` 导入 Sklearn 中的 `load_digits` 类，以初始化变量 `digits`，其中包含 Sklearn 自带的数字数据集。随后，该列表初始化变量 `fig`，并调用 `plt` 类的 `imshow()` 方法，用于显示数字数据集中的一个数字。

`Figure F.16` 根据 `Listing F.17` 中的代码，显示了数字数据集中的一个数字的绘图。

- [IRIS 特征名称](https://wiki.example.org/iris_feature_names): `sepal length (cm)` `sepal width (cm)` `petal length (cm)` `petal width (cm)` => 行数: `150` => 列数: `4` => 行和列数: `\(150, 4\)` => 元素数: `600` => IRIS 详情: `<class 'pandas.core.frame.DataFrame'> RangeIndex: 150 entries, 0 to 149 Data columns (total 4 columns): sepal length (cm) 150 non-null float64 sepal width (cm) 150 non-null float64 petal length (cm) 150 non-null float64 petal width (cm) 150 non-null float64 dtypes: float64(4) memory usage: 4.8 KB None` => 前五行: `sepal length (cm)` `sepal width (cm)` `petal length (cm)` `petal width (cm)` 0 5.1 3.5 1.4 0.2 1 4.9 3.0 1.4 0.2 2 4.7 3.2 1.3 0.2 3 4.6 3.1 1.5 0.2 4 5.0 3.6 1.4 0.2 => 类标签: `[0 1 2]`

## The Iris Dataset in Sklearn (Optional)

The Iris dataset in Sklearn consists of the lengths of three different types of Iris‑based petals and sepals: Setosa, Versicolour, and Virginica. These numeric values are stored in a 150x4 NumPy.ndarray.

Note that the rows in the Iris dataset are the sample images, and the columns consist of the values for the Sepal Length, Sepal Width, Petal Length, and Petal Width of each image. `Listing F.21` displays the contents of `sklearn_iris.py` that illustrates how to display detailed information about the Iris dataset.

# LISTING F.21: sklearn_iris.py
