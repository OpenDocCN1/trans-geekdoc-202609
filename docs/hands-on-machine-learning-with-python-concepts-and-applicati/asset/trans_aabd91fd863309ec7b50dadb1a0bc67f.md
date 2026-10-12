
训练好的逻辑回归模型在测试集上达到了 72% 的准确率。

# 广义线性模型

广义线性模型是线性模型的一种扩展，其中因变量不属于正态分布或高斯分布。广义线性模型能够建模自变量和因变量之间更复杂的关系。GLM 通常可以对各种概率分布进行建模，例如泊松分布、二项分布、多项分布等。逻辑回归就是广义线性模型的一个例子，其中因变量使用二项分布进行建模。这使其能够创建从输入到输出的映射，且输出本质上是二元的。

泊松回归是一种广义线性模型，用于建模计数数据。计数数据是只能为正的整数值。泊松回归假设因变量 `y` 服从泊松分布，这是一种指数概率分布。泊松回归与线性回归的主要区别在于：线性回归假设输出来自正态分布，而泊松回归假设 `y` 来自泊松分布。泊松回归中的输出建模如下所示。

```
![](images/00065.gif)
```

广义线性模型由三个部分组成：随机成分（即输出的概率分布）、系统成分（描述解释变量 `X` 或预测变量）以及连接函数（指定解释变量与随机成分之间的关系）。

由于泊松回归的超参数（权重）不能取负值，因此它们通过自然对数进行变换以确保始终为正。泊松分布的均值在数学上表述为：

```
![](images/00066.gif)
```

用于训练模型以发现可学习参数的目标函数或损失函数如下所示：

```
![](images/00067.gif)
```

在我们的实操示例中，我们将使用 `statsmodels` 包，它提供了各种用于统计建模、统计数据探索等的函数和类。我们将使用 `statsmodels` 自带的数据集——苏格兰投票数据集，该数据集包含 1997 年关于授予苏格兰议会征税权的投票记录。该数据集包含 8 个解释变量（预测变量）和 32 个观测值，每个地区一个。

首先我们按如下方式导入 `Statsmodels` 包。

```
import statsmodels.api as sm
```

接下来我们加载数据集并提取解释变量 (`X`)。

```
data = sm.datasets.scotland.load()

# data.exog 是自变量 X
data.exog = sm.add_constant(data.exog)
```

类似于 Scikit-Learn，我们导入合适的模型并实例化一个对象。在这种情况下，我们指定一个广义线性模型并将分布族设置为泊松分布。

```
# 使用默认连接函数实例化一个泊松族模型。
poisson_model = sm.GLM(data.endog, data.exog, family=sm.families.Poisson())
```

然后我们在数据上拟合模型。

```
poisson_results = poisson_model.fit()
```

我们现在可以打印结果摘要，以更好地了解训练好的模型。

```
print(poisson_results.summary())
```

```
![](images/00068.jpeg)
```

摘要包含自变量的系数或权重、标准误和 z 分数等值。

# 回归示例：预测波士顿房价

为了更好地理解迄今为止讨论的概念，我们将引入一个贯穿始终的示例，其中我们面临一个回归问题：给定波士顿郊区房屋的特征信息，预测其价格。

我们将使用的数据集可以在以下链接找到：[https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv](https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv)

## 执行分析的步骤

为了执行分析并构建模型，我们首先需要明确问题，执行探索性数据分析以更好地了解数据内容，选择机器学习算法，训练模型，最后评估其性能。以下步骤将以实操方式进行，建议读者跟随操作。

### 导入库：

```
import numpy as np

import pandas as pd

import matplotlib.pyplot as plt
```

Numpy 是一个流行的 Python 数值计算库，支持计算的向量化实现，并显著加快计算速度。Pandas 是一个用于在数据框中操作数据的库，而 Matplotlib 用于绘制图表和数据可视化。

让我们使用 Pandas 库的 `read_csv` 方法并传入数据位置来加载数据。

```
dataset = pd.read_csv('Boston.csv')
```

下一步是查看数据包含的内容

```
dataset.head(5)
```

```
![](images/00069.jpeg)
```

这将显示单个观测值作为行。一行代表一个数据点，而列代表特征。共有 13 个特征，因为最后一列 `medv` 是我们要预测的回归值（自住房中位数价格，单位：千美元），`Unnamed:0` 列是一种标识符，无信息量。每个特征代表一部分信息，例如 `crim` 表示城镇人均犯罪率，`rm` 表示每户平均房间数。

接下来我们运行

```
dataset.shape
```

这给出了数据集的形状，包含 506 个观测值。我们首先需要将列分离为自变量和因变量

```
X = dataset.drop(['Unnamed: 0', 'medv'], axis=1)

y = dataset['medv']
```

我们需要将数据集拆分为训练集和测试集，因为我们想在训练集上训练模型，然后在测试集上评估其性能。

```
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test = train_test_split(X, y, test_size=0.3)
```

`x_train`、`x_test` 包含我们的特征，而 `y_train`、`y_test` 分别是训练集和测试集的预测目标。`test_size=0.3` 意味着我们希望 70% 的数据用于训练，30% 用于测试阶段。

下一步是从 Scikit-Learn 库导入线性回归模型。Scikit-Learn 是 Python 中事实上的标准机器学习库，开箱即用地包含了许多机器学习模型和工具。

线性回归使用直线方程来拟合参数。

```
# 导入模型
from sklearn.linear_model import LinearRegression

regressor = LinearRegression()
```

上述代码导入线性回归模型并实例化一个对象。

```
regressor.fit(x_train,y_train)
```

这行代码使用 `fit` 方法拟合数据。这意味着它找到解释数据的自变量的适当值。

### 如何预测

为了评估我们的模型，我们使用测试集来了解模型是否能很好地泛化到未训练过的数据。

```
y_pred = regressor.predict(x_test,y_test)

from sklearn.metrics import mean_squared_error

mse = mean_squared_error(y_test, y_pred)
```

在 `regressor` 对象上调用的 `predict` 方法返回预测值，我们用它来评估模型的误差。我们使用均方误差作为度量标准。均方误差 (MSE) 衡量预测值偏离真实（实际）值的程度。该模型获得的 MSE 为 20.584。

最后，我们绘制输出图以了解分布情况。

```
plt.scatter(y_test, y_pred)

plt.xlabel("Prices: $Y_i$")

plt.ylabel("Predicted prices: $\hat{Y}_i$")

plt.title("Prices vs Predicted prices: $Y_i$ vs $\hat{Y}_i$")
```

```
![](images/00070.jpeg)
```

从上述散点图可以看出，我们模型的预测值接近实际房价，因此点集中分布。
