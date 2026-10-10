
# Choosing kernel
我们有许多参数用于许多 ML 模型。最重要的是我们需要关注的参数是 kernel。kernel 是你使用 linear SVR 还是 polynomial SVR 或 Gaussian SVR。`'linear'`、`'poly'`、`'rbf'`、`'sigmoid'`、`'precomputed'` 作为最常见的 kernel。

# The one we want to use is the 'rbf' kernel
为什么不使用它？因为我们的问题是非线性的。`linear` kernel 会使一个线性机器模型，这对于非线性问题是不合适的。

# And then we have the choice 'poly' and 'rbf'
这两个 kernel 都可以用于我们的问题。我们将选择最常见的 Gaussian kernel 因此这里是 `'rbf'`。

# Prediction without scaling
在 `y_pred` 中，我们使用 `[[6.5]]`。因为 Parameter 必须是 2-D array

```python
y_pred = regressor.predict([[6.5]]) # [[6.5]], since Parameter must be 2-D array
print(y_pred)
```

# Before scaling is applied

```python
from sklearn.svm import SVR
regressor = SVR(kernel='rbf')
regressor.fit(X, y)
```

```python
# Visualising the SVR results
plt.scatter(X, color='red')
plt.plot(X, predict(X), color='blue')
```

```python
# prediction
在这里我们将预测等级 6.5 的输出
因为该候选人拥有 4 年以上的区域经理经验，
所以他的水平一定在 7 和 6 之间。
y_prd = regressor.predict([[6.5]]) # [[6.5]], 参数必须是 2 维数组
print(y_prd)
# python prct_svr.py
```

**需要的特征：** `SVR` 不像简单和多元线性模型那样自动应用特征缩放（Feature-Scaling）。`SVR` 不像 `Linearregression` 那样常见的类。

# 应用特征缩放：

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
# 导入数据集，预览“欺诈检测”问题
dataSet = pd.read_csv('Position_Salaries.csv')
X = dataSet.iloc[:, 1:2]
y = dataSet.iloc[:, 2].values
```

```python
# 将数据集分为训练集和测试集：这里不需要
```

```python
# 特征缩放
from sklearn.preprocessing import StandardScaler
sc_x = StandardScaler()
sc_y = StandardScaler()
X_scaled = sc_x.fit_transform(X.reshape(-1, 1))
y_scaled = sc_y.fit_transform(y)
```

**新的预测：** 我们不使用 `fit_transform()` 因为模型已经拟合过了。我们只使用 `transform()`

```python
sc_X.transform(np.array([[6.5]]))
```

**将 6.5 转换为数组：** 期望 2 维数组，我们需要将 6.5 作为数组传递。结果 `y_prd` 也是缩放后的输出。

**反向缩放（逆转换）：** 因为应用了缩放且我们以缩放数组的形式传递了 6.5。结果 `y_prd` 也是缩放后的输出。

```python
y_prd = regressor.predict(sc_X.transform(np.array([[6.5]]))
print('prediction under scaled data : ', y_prd)
y_inv_sc = sc_y.inverse_transform(y_prd)
print('Reverse prediction :', y_inv_sc)
```

注意在“可视化 SVR 结果”中，所有缩放后的数据都用于绘制模型。

`SVR` 拟合在观测值出现最多的地方。

# 练习版本

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt preprocessing

# -------------------------------------------------
# 导入数据集，之前的“欺诈检测”问题
dataSet = pd.read_csv("Position_Salaries.csv")
y = dataSet.iloc[:,2].values
X = dataSet.iloc[:,:-2].values

# 将数据集分为训练集和测试集：不需要表头

# 特征缩放
from sklearn.preprocessing import StandardScaler
sc_x = StandardScaler()
sc_y = StandardScaler()
X_scaled = sc_x.fit_transform(X)
y_scaled = sc_y.fit_transform(y.reshape(-1, 1))

# 对数据拟合 SVR
from sklearn.svm import SVR
regressor = SVR(kernel='rbf')
regressor.fit(X_scaled, y_scaled)
regressor.fit(X_scaled, y_scaled)

# 可视化结果
# 需要特征缩放
plt.scatter(X_scaled, y, color='red')
plt.plot(X_scaled, regressor.predict(X_scaled), color='blue')
plt.scatter(X, y, color="red")
plt.title("Truth or Bluff (SVR)")
plt.xlabel("Position level")
plt.ylabel("Salary")
plt.show()

# 可视化 SVR 结果（为了更高的分辨率和更平滑的曲线）
X_grid = np.arange(min(X_scaled), max(X_scaled), 0.1)
X_grid = X_grid.reshape(len(X_grid), 1)
plt.scatter(X_scaled, y_scaled, color="red")
plt.plot(X_grid, regressor.predict(X_grid), color="blue")
plt.title("Truth on Bluff (SVR)")
plt.xlabel("Position level")
plt.ylabel("Salary")
plt.show()

# prediction

在这里我们将预测等级 6.5 的输出
因为该候选人拥有 4 年以上的区域经理经验，
所以他的水平一定在等级 7 和 6 之间。

y_prd = regressor.predict([[6.5]]) # 因为，参数必须是 2 维数组

# 我们需要在缩放中转换 6.5
ny_prd = regressor.predict(sc_x.transform([[6.5]])) # 替代方案
y_prd = sc_y.inverse_transform(np.array([[ny_prd]]
print("Prediction under scale 6.5: ", y_prd))
y_inv_sc = sc_y.inverse_transform(y_prd)
print("Reverse scaled prediction: ", y_inv_sc)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_60_0.png)

# 教师版本：6.5 未经过转换

```python
# 支持向量回归 (SVR)
# 导入库
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# 导入数据集
dataset = pd.read_csv('Position_Salaries.csv')
X = dataset.iloc[:, 1:-1].values
y = dataset.iloc[:, -1].values

# 特征缩放
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
sc_y = sc.fit_transform(y)

# 在整个数据集上训练 SVR 模型
from sklearn.svm import SVR
regressor = SVR(kernel='rbf')
regressor.fit(X, sc_y)

# 预测结果
y_pred = regressor.predict([[6.5]])
y_pred = sc_y.inverse_transform(y_pred)

# 可视化结果
plt.scatter(X, y, color='red')
plt.plot(regressor.predict(X), color='blue')
plt.title('Truth or Bluff (SVR)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()

# 可视化结果（为了更高的分辨率和更平滑的曲线）
X_grid = np.arange(min(X), max(X), 0.01)
X_grid = X_grid.reshape(-1, 1)
plt.scatter(X, y, color='red')
plt.plot(X_grid, regressor.predict(X_grid), color='blue')
plt.title('Truth or Bluff (SVR)')
plt.xlabel('Position level')
plt.ylabel('Salary')
plt.show()
```

## 4.2 什么时候使用 SVR？

如果线性回归等线性模型不能很好地拟合你的数据，你应该使用 `SVR`。你面对的是非线性问题，你的数据不是线性可分的。在这种情况下，`SVR` 可能是一个更好的解决方案。

`SVR` 是一个非常抽象的模型，并不为人所知。你必须理解 `SVM` 模型，你将在第三章：分类中看到它。一旦理解了 `SVM` 模型，你就能更好地掌握它。

## 2.4.4 为什么我们需要 inverse_transform？

因为应用了缩放且我们以缩放数组的形式传递了 6.5。结果 `y_prd` 也是缩放后的输出。

## 2.4.5 为什么我们需要 p 值？

`SVR` 拟合在观测值出现最多的地方。

## 2.4.6 特征的输出是什么？

注意在“可视化 SVR 结果”中，所有缩放后的数据都用于绘制模型。

## 2.5.1 决策树

- 分类与回归树：决策树
- 当响应变量是数值或连续的时，需要回归树。
- 分类树如其名义，响应变量是分类的。

决策树：现在我们将逐一个创建这些拆分，同时我们也将开始绘制我们的决策树。

## 分割数据集

## 决策树

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_1.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_2.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_3.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_4.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_5.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_6.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_63_7.png)

现在这就是我们的决策树。

如何预测：接下来我们确定 `$y$`，该值通过取终端叶子节点（最后一次迭代）中的平均值来确定，即只需取叶子节点所有点 `$y$` 的平均值，该值将分配给任何落在该区域的新点。这项练习的整个意义在于向我们的图表和系统中添加更多信息，以便更好地预测。我们的机器学习算法只需对所有点取平均值，无论你的新数据元素落在何处，它都会在该处添加数据集。

因此，我们将图表划分为终端叶子节点，机器学习算法已将信息培养到了我们的系统中。这样我们就可以更准确地预测值或为新元素分配值。以下是我们完成的决策树。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_64_0.png)

## 2.5.2 使用 Python 练习决策树回归模型

# 练习版本

```python
# 库
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# 数据提取
dataset = pd.read_csv("Position_Salaries.csv") 
X = dataset.iloc[:, 1:2].values
y = dataset.iloc[:, 2].values

# 特征缩放
from sklearn.preprocessing import StandardScaler
sc_x = StandardScaler()
sc_y = StandardScaler()
X_scaled = sc_x.fit_transform(X)
y_scaled = sc_y.fit_transform(y.reshape(-1, 1))

# 数据分割：此示例不需要
# 将数据集拟合到模型
from sklearn.tree import DecisionTreeRegressor
regressor = DecisionTreeRegressor(random_state=0)
regressor.fit(X_scaled, y_scaled)

# 预测
```

```python
y_pred = regressor.predict([[6.5]])
print("The predicted value for 6.5 is: ", y_pred)
```

```python
# 绘制模型
plt.scatter(X, y, color="red")
plt.plot(X, regressor.predict(X), color="green")
plt.title("Truth or Bluff (Decision Tree Regression)")
plt.xlabel("Position level")
plt.ylabel("Salary")
```

预测：我们的预测通过以下方式计算：

```python
y_pred = regressor.predict([[6.5]])
```

结果为 150,000。这个预测低于 160,000（新员工询问的数值）。这并不是一个良好的预测，实际上它是根据平均值计算得的。

**新陷阱：** 我们得到了如下所示：在决策树回归算法中，通过将自变量拆分为几个区间，熵会增加。在我们的直觉中，我们有两个自变量 `$X_1$` 和 `$X_2$`。在这个例子中，我们**只有一个自变量**。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_65_0.png)

因此根据算法，它在每个区间内取平均值。由于存在无限个区间，使得上面的图表是平滑的，或者我们的 `matplotlib` 设置有问题。课程**决策树算法**并没有考虑无限区间，所以这是我们绘图的问题。

在我们之前的模板中，它只绘制了 10 个位置的薪资预测值，并用直线连接它们，因为在这里在区间内没有自由度。

**非线性且非连续的回归模型：** 我们面临了一种新的回归模型。是非线性且非连续的回归模型。

尽管所有的回归模型都是线性的，但这里的决策树是非连续的，这是我们遇到的第一个非连续模型。

**可视化非连续回归模型：** 当我们以更高的分辨率进行平滑处理可视化时，我们可以观察到平均值和非连续回归模型。遵循一维的**决策树算法**。
