

## 假设

多元线性回归假设因变量与自变量之间的关系是线性的，且误差项（ε）服从方差恒定的正态分布。它还假设自变量之间不存在完全相关性。系数的解释如下：

*   截距项（`β0`）表示当所有自变量均为 0 时 `Y` 的预测值。
*   每个系数（`β1`、`β2` 等）表示在保持所有其他变量不变的情况下，相应自变量每变化一个单位，`Y` 发生的变化量。

## 模型复杂度

多元线性回归通过考虑多个自变量对因变量的联合影响，允许对更复杂的关系进行建模。这使其适用于多种因素共同影响结果的广泛应用场景。

## 评估

多元线性回归模型可以使用 R 平方（`R²`）、调整后 R 平方、均方误差（`MSE`）等指标进行评估，以判断模型对数据的拟合程度。

## 应用

多元线性回归应用于经济学、金融学、社会科学、流行病学和环境科学等领域，这些领域中多种因素共同作用于结果。它在进行预测、理解变量关系以及假设检验方面非常有价值。

## 在 Python 中执行多元线性回归

借助 NumPy 和 sci-kit-learn 等库，在 Python 中执行多元线性回归非常简单。[代码 3.2](#ch03.xhtml#cd3-2) 展示了如何使用 sci-kit-learn 创建并拟合多元线性回归模型的示例：

### 代码 3.2：多元线性回归的 Python 代码

```python
import numpy as np

from sklearn.linear_model import LinearRegression

from sklearn.model_selection import train_test_split

from sklearn.metrics import mean_squared_error

import matplotlib.pyplot as plt

from mpl_toolkits.mplot3d import Axes3D

# Sample data with multiple independent variables (X1, X2, X3) and a dependent variable (Y)
X = np.array([[1, 2, 3], [2, 3, 4], [3, 4, 5], [4, 5, 6], [5, 6, 7]])
Y = np.array([5, 8, 11, 14, 17])

# Split the data into training and testing sets
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.2, random_state=42)

# Create a linear regression model
model = LinearRegression()

# Fit the model to the training data
model.fit(X_train, Y_train)

# Make predictions using the trained model
Y_pred = model.predict(X_test)

# Calculate the mean squared error (MSE) to evaluate the model's performance
mse = mean_squared_error(Y_test, Y_pred)

# Get the regression coefficients (intercept and slopes)
intercept = model.intercept_
coefficients = model.coef_

print("Intercept (β0):", intercept)
print("Coefficients (β1, β2, β3):", coefficients)
print("Mean Squared Error (MSE):", mse)

# Plot the original data points and the regression plane
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.scatter(X_test[:, 0], X_test[:, 1], Y_test, color='blue', label='Actual Data Points')
ax.scatter(X_test[:, 0], X_test[:, 1], Y_pred, color='red', label='Predicted Data Points')
ax.set_xlabel('X1-axis')
ax.set_ylabel('X2-axis')
ax.set_zlabel('Y-axis')
ax.legend()
ax.set_title('Linear Regression Plane')
plt.show()
```

请参考 [图 3.4](#ch03.xhtml#fig3-4) 查看代码输出：

![](images/3.4.png)

**图 3.4：代码 3.2 的输出**

在该代码中，我们导入了必要的库，包括用于数值运算的 NumPy 和用于创建及训练线性回归模型的 scikit-learn。我们定义了包含三个自变量（`X1`、`X2`、`X3`）和一个因变量（`Y`）的样本数据。我们使用 `train_test_split()` 将数据划分为训练集和测试集，以评估模型性能。然后，我们使用 scikit-learn 中的 `LinearRegression()` 建立多元线性回归模型。

我们使用 `fit()` 方法在训练数据上拟合模型。我们使用训练好的模型对测试数据进行预测。我们计算 `MSE` 以评估模型性能。最后，我们打印回归系数（截距和斜率）以及 `MSE` 作为模型质量的度量。由于实际数据点和预测数据点相同，因此它们在图中重叠显示。

> **注意：** 您可以用自己的数据集替换样本数据进行分析。

## 多项式回归

[多项式回归](#contents.xhtml#sc2_72a)

多项式回归是一种回归分析技术，它通过多项式函数来刻画因变量（`Y`）与一个或多个自变量（`X`）之间的关系。

与假设变量间存在线性关系的简单线性回归不同，多项式回归能够捕捉更复杂的非线性关系。

[图 3.5](#ch03.xhtml#fig3-5) 有助于直观展示多项式方程如何用于建模因变量（`Y`）与自变量（`X`）之间的关系。下图展示了二次多项式回归的基本示意图：

![](images/3.5.png)

**图 3.5：多项式回归**

图示说明如下：

*   纵轴代表因变量 `Y`。
*   横轴代表自变量 `X`。
*   曲线代表捕捉 `X` 与 `Y` 关系的二次回归曲线。

在多项式回归中，回归模型表示为指定次数（如二次、三次或更高）的多项式方程。含一个自变量的多项式回归通式为：

![](images/eq-3.jpg)

其中：

*   `Y` 是因变量。
*   `X` 是自变量。
*   `β0`、`β1`、`β2`、...、`βn` 是决定多项式函数形状和次数的系数。
*   `ε` 是误差项，代表未被解释的变异性。

关于多项式回归的关键点如下：

*   **多项式的次数：** 次数（`n`）决定了多项式方程的复杂程度。一次多项式代表线性关系，而高次多项式能捕捉数据中更复杂的非线性模式。
*   **过拟合：** 使用高次多项式可能导致过拟合，即模型对训练数据拟合得非常紧密，但可能无法很好地泛化到新的、未见过的数据。选择合适的多项式次数对于平衡模型复杂度和泛化能力至关重要。
*   **可解释性：** 虽然多项式回归能捕捉复杂关系，但随着多项式次数的增加，系数的解释变得更具挑战性。
*   **应用：** 多项式回归用于数据关系呈现曲线或非线性模式的各个领域。例如物理学、经济学、生物学和工程学。
*   **可视化：** 绘图时多项式回归通常呈现曲线，使其在视觉上适合建模具有非线性趋势的数据。
*   **正则化：** 在某些情况下，可以结合岭回归和 Lasso 回归等正则化技术与多项式回归一起使用，以防止过拟合。

