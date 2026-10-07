

![](img/55c2af1cab44d6186a8b2008b93f459f_208_0.png)

**图 4.22** 线性回归。

## SKLEARN 中的线性回归 (2)

列表 4.25 向你展示了如何执行线性回归，以便找到平面上点集集合最佳拟合线。列表 4.24 扩展了列表 4.23，使用线性方程而不是一组硬编码的点集，然后绘制了这些点和最佳拟合线。

列表 4.25 显示了 sklearn-linreg.py 的内容，展示了如何在 Sklearn 中使用一组随机点集执行线性回归。

## **列表 4.25:** sklearn-linreg.py

```
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt
import numpy as np
```

```
x = np.random.randn(10,1)
y = 2*x + 3 + 0.1*np.random.randn(10,1)

model = LinearRegression()
model.fit(x,y)
```

```
print('slope:',model.coef_)
print('inter:',model.intercept_)
print('predict:',model.predict(20))
```

```
x_test = np.linspace(-3,3,3)
y_pred = model.predict(x_test[:None])
```

```
plt.scatter(x,y)
plt.plot(x_test,y_pred,'r')
plt.legend(['Predicted line','Observed data'])
plt.show()
```

列表 4.25 包含一个新的导入语句，它使我们能够使用 Sklearn 中的 `LinearRegression` 类。接下来，使用 NumPy 变量 `x` 初始化一组随机数字，随后是 NumPy 变量 `y`，其值基于变量 `x`。注意 `y` 中的每个值都带有一个小的随机数偏移，这样我们就得到了对直线的“模糊”近似（你已经在其他代码示例中见过这种技术）。

接下来，变量 `model` 被实例化为 `LinearRegression` 的实例，然后调用 `fit()` 方法来训练该模型。NumPy 变量 `x_test` 通过 NumPy `linspace()` API 初始化，NumPy 变量 `y_pred` 则通过 `predict()` API 计算出的预测值初始化。

列表 4.25 的最后一个代码块显示了由 `x` 和 `y` 派生的点散点图，随后是一个带有图例的线性图。图 4.23 显示了基于列表 4.25 生成输出的图像。

![](img/55c2af1cab44d6186a8b2008b93f459f_210_0.png)

**图 4.23** 散点图和最佳拟合线。

## SKLEARN 中的线性回归与正则化

附录讨论了过拟合（overfitting），过拟合发生在训练模型时，此外还讨论了正则化技术，这些技术通过对最小二法解施加“惩罚”来减少模型中的过拟合。两种著名的技术是 L1 和 L2 正则化。

Sklearn 支持岭回归（Ridge regression，本质与 L2 回归）来解决模型的过拟合问题，你可以在相应的 API 中轻松地指定它。

列表 4.26 显示了 sklearn-ridgelinreg.py 的内容，展示了如何在 Sklearn 中使用随机点集执行线性回归的同时，将岭回归包含在线性模型。

**列表 4.26** sklearn-ridge-linreg.py

```
from sklearn.linear_model import LinearRegression
import warnings
warnings.filterwarnings(action="ignore",
module="scipy", message="^internal gelsd")
```

```
from sklearn import linear_model
```

# previous: reg = linear_model.LinearRegression()
**reg = linear_model.Ridge (alpha = .5)**
reg.fit([[0, 0], [0, 0], [1, 1]], [0, .1, 1])

```

```
print("Coefficients:", reg.coef_)
print("Intercept:", reg.intercept_)
```

列表 4.26 显示了 Python 脚本 `sklearn-simple-lr.py` 中的一段注释代码片段，随后是提供岭相关功能的新代码片段（加粗显示）。列表 4.26 的输出如下：

```
Coefficients: [0.34545455 0.34545455]
Intercept: 0.1363636363636368
```

除了支持线性回归和 L2 正则化外，Sklearn 的另一个优秀特性是它支持逻辑回归（logistic regression），这是本章后面一个章节的主题。

## 什么是逻辑回归？

逻辑回归本质上是对线性回归应用 sigmoid 激活函数，以执行二分类。逻辑回归在许多不相关的领域都很有用。这些领域包括机器学习、各种医学领域和社会科学。逻辑回归可以根据患者的各种观测特征预测患某种特定疾病的风险。其他使用逻辑回归的领域包括工程、营销和经济学。

逻辑回归可以是二项的（因变量只有两个结果）、多项的（因变量有三个或更多结果）或序数的（因变量是有顺序的）。

例如，假设一个数据集由属于类 A 或类 B 的数据组成。逻辑回归可以预测一个数据点属于类 A 还是类 B。尽管名字带有回归，它是一种分类技术。

## SKLEARN 与逻辑回归

正如你可能已经料到的，逻辑回归支持线性回归和逻辑回归。列表 4.27 显示了 logistic-regression.py 的内容，展示了如何在数据集上使用 Sklearn 和逻辑回归。

## 列表 4.27: logistic-regression.py

```
from sklearn import datasets
from sklearn import metrics
from sklearn.linear_model import LogisticRegression
```

```
# 加载数据集
dataset = datasets.load_iris()
```

```
# 对数据拟合逻辑回归模型
model = LogisticRegression()
model.fit(dataset.data, dataset.target)
```

```
# 预测
```

```
expected = dataset.target
predicted = model.predict(dataset.data)

# 总结拟合情况
print("classification report")
print(metrics.classification_report(expected, predicted))
print("confusion matrix")
print(metrics.confusion_matrix(expected, predicted))
```

