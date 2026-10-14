
其中，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>y</mi></math>![y](images/c004_dequ8.png) 是实际观测输出，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><msub><mi>&#946;</mi><mn>0</mn></msub></math>![beta subscript 0](images/c004_dequ9.png) 是截距，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><msub><mi>&#946;</mi><mn>1</mn></msub><mo>,</mo><msub><mi>&#946;</mi><mn>2</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>&#946;</mi><mi>n</mi></msub></math>![beta sub 1, beta sub 2, dot dot dot, beta sub n](images/c004_dequ10.png) 是特征 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><msub><mi>x</mi><mn>2</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub></math>![Subscript x1 , Subscript x2 , ... , Subscript x n](images/c004_dequ11.png) 的系数（或权重），而 <math class="a" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>&#949;</mi></math>![epsilon](images/MathcabEQ_0010.png) 代表误差，也称为 `residual`（残差，即实际值与预测值之间的差异）。

你的目标是预测模型将学习的系数 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><msub><mi>&#946;</mi><mi mathvariant="normal">I</mi></msub></math>![beta subscript upper I](images/c004_dequ13.png)，以使整个数据集上的误差 <math class="a" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>&#949;</mi></math>![epsilon](images/MathcabEQ_0011.png) 最小化。

在评估模型时，我们通过查看残差来了解模型的表现如何。在线性回归中，模型旨在找到使均方误差（MSE）最小化的线性函数。MSE 的公式如下：

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><mtext>MSE</mtext><mo>=</mo><mstyle displaystyle="true"><mfrac><mn>1</mn><mi>n</mi></mfrac></mstyle><munderover><mo movablelimits="false">&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></munderover><msup><mrow><mo>(</mo><msub><mi>y</mi><mrow><mi>i</mi></mrow></msub><mo>&#8722;</mo><mrow><mover><msub><mi>y</mi><mrow><mi>i</mi></mrow></msub><mo>^</mo></mover></mrow><mo>)</mo></mrow><mrow><mn>2</mn></mrow></msup></math>![Mean Squared Error equals 1 over n, sum from i equals 1 to n, of left parenthesis, y sub i minus y sub i hat right parenthesis, squared.](images/c004_dequ15.png)

其中，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mtext>&#160;</mtext><mi>n</mi></math>![n](images/c004_dequ16.png) 表示数据集中的观测值数量，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><msub><mi>y</mi><mi>i</mi></msub></math>![y sub i](images/c004_dequ17.png) 表示观测值 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>i</mi></math>![i](images/c004_dequ18.png) 的实际值，而 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mover accent="true"><mrow><msub><mi>y</mi><mi>i</mi></msub></mrow><mo>^</mo></mover></math>![y subscript i with circumflex accent](images/c004_dequ19.png) 表示观测值 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>i</mi></math>![i](images/c004_dequ20.png) 的预测值。

最小化 MSE 有助于确保预测值尽可能接近实际值，从而有效降低整体误差。

你可以使用 `sklearn.linear_model` 模块中的 `LinearRegression` 类从数据集构建线性回归模型，如以下代码片段所示：

```
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# Generate some sample data
np.random.seed(0)
X = 2 * np.random.rand(100, 1)
y = 4 + 3 * X + np.random.randn(100, 1)

# Fit a linear regression model
model = LinearRegression()
model.fit(X, y)
y_pred = model.predict(X)

# Plot the data points
plt.scatter(X, y, color='blue', label='Data Points')

# Plot the regression line
plt.plot(X, y_pred, color='red', label='Regression Line')

# Plot the residuals
for i in range(len(X)):
    plt.plot([X[i], X[i]], [y[i], y_pred[i]], color='green', linestyle='--')

plt.xlabel('X')
plt.ylabel('y')
plt.title('Linear Regression with Residuals')
plt.legend()
plt.show()

# Print Mean Squared Error
mse = np.mean((y - y_pred) ** 2)
print(f"Mean Squared Error: {mse}")
```

让我们看看该程序是如何工作的：

*   **数据生成** 我们生成一个包含 100 行（样本）和 1 列（特征）的矩阵 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>X</mi></math>![X](images/c004_dequ21.png)。每一行代表单个特征的值（观测值或样本），该值是在 0 和 2 之间均匀分布的随机数。然后我们定义一个线性关系 <math class="a" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>y</mi><mo>=</mo><mn>4</mn><mo>+</mo><mn>3</mn><mi>X</mi><mo>+</mo><mi>&#949;</mi></math>![y equals sum with 3 summands four plus three times cap x plus epsilon](images/MathcabEQ_0012.png)，并加入一些残差。在程序中，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>y</mi></math>![y](images/c004_dequ23.png) 代表与每个样本对应的目标变量向量。

*   **模型拟合** 我们使用 `scikit-learn` 中的 `LinearRegression` 创建并拟合线性回归模型。

*   **可视化** 如 [图 4.9](#c004.xhtml#c04-fig-9) 所示，我们绘制数据点的散点图，并绘制回归线。最后，我们绘制虚线以显示每个数据点（共 100 个）的残差（实际值与预测值之间的差异）。

    ![图 4.9 线性回归。](images/c04f009.png)

    [图 4.9](#c004.xhtml#rc04-fig-9) 线性回归。

*   **MSE** 我们计算并打印 MSE 以量化模型的性能。

### 逻辑回归

尽管名为“回归”，但逻辑回归是一种分类算法，它允许你使用输入特征的线性组合来建模正确类别预测的概率。当因变量是二元时，即只能取两种可能的结果：正确类别预测或错误类别预测，该算法特别有用。

逻辑回归通过将 `logistic function`（逻辑函数）应用于输入特征的线性组合来工作，这会将输出转换为落在 0 和 1 之间的范围内。然后可以将此输出解释为事件发生的概率，并使用阈值（通常为 0.5）将事件分类为两个可能的类别之一。

逻辑函数，也称为 `sigmoid function`（Sigmoid 函数），是逻辑回归的关键，定义如下：

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><mi mathvariant="normal">&#963;</mi><mfenced close=")" open="("><mrow><mi>z</mi></mrow></mfenced><mo>=</mo><mstyle displaystyle="true"><mfrac><mrow><mn>1</mn></mrow><mrow><mn>1</mn><mo>+</mo><msup><mi>e</mi><mrow><mo>-</mo><mi>z</mi></mrow></msup></mrow></mfrac></mstyle></math>![Sigma of z equals 1 over 1 plus e to the power of negative z.](images/c004_dequ24.png)

在该公式中，<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>z</mi></math>![z](images/c004_dequ25.png) 是输入特征及其对应系数的线性组合：
