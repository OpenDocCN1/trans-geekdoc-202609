
如何分类：无论如何，你可能会说：我不想要概率。我想要一个预测。我想要 y 值的预测。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_84_0.png)

- 我们只能得到一个预测值 $\hat{y}$。因此，$\hat{y}$ 代表因变量的预测值。你是如何获得 $\hat{y}$ 的？这种方法非常任意。你必须选择一条线。在这种情况下，我们将检查 50%。你可以选择任何地方，但选择 50% 是因为它位于中间且具有对称性。这条线以下的任何部分（以及 s 曲线的底部）都将向下投影到零线上。同样，上半部分，它将投影到 $y = 1$ 上。

- 也就是说，如果你接受此提议的预测概率小于 50%，那么你就会落入 $y = 0$，即你不会接受该提议。因此，我们偏向“是”或“否”（0 或 1）（而不是连续的 [0,1] 区间）。

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_84_1.png)

# 3.1-4 逻辑回归：Python 中的实现

我们将看到逻辑回归如何成功地分离类别并预测二元结果。为了理解逻辑回归的 Python 中的实现，我们将使用以下示例：

> 示例：有一个数据集，包含了从社交网络网站获取的用户信息。这是一家汽车制造公司，最近推出了一款新的 SUV 汽车。因此，公司想跟踪数据中有多少用户想要购买汽车。

对于这个问题，我们将使用逻辑回归算法构建一个机器学习模型。详情见下图。在这个问题中，我们将使用年龄（Age）和薪水（salary）作为独立变量来预测购买变量（purchased）。

| User ID | Gender | Age | EstimatedSalary | Purchased |
|---|---|---|---|---|
| 15624510 | Male | 19 | 29000 | 0 |
| 15610944 | Male | 35 | 20000 | 0 |
| 15649875 | Female | 28 | 42000 | 0 |
| 15600326 | Male | 27 | 57000 | 0 |
| 15604002 | Male | 19 | 76000 | 0 |
| 15728733 | Male | 27 | 68000 | 0 |
| 15595554 | Female | 24 | 84000 | 0 |
| 15649829 | Female | 32 | 150000 | 1 |
| 15600575 | Male | 25 | 39000 | 0 |
| 15570769 | Female | 35 | 65000 | 0 |
| 15606274 | Female | 26 | 52000 | 0 |
| 15539333 | Male | 35 | 36000 | 0 |
| 15704887 | Male | 32 | 18000 | 0 |
| 15628972 | Male | 18 | 62000 | 0 |
| 15731995 | Female | 29 | 78000 | 0 |
| 15733883 | Male | 47 | 25000 | 1 |
| 15617282 | Male | 46 | 28600 | 1 |
| 15621083 | Female | 48 | 29000 | 1 |
| 15649487 | Male | 45 | 22000 | 1 |
| 15735760 | Female | 47 | 49000 | 1 |

# 逻辑回归的步骤：为了使用 Python 实现逻辑回归，我们将使用与之前回归主题中相同的步骤。以下是具体步骤：

- i. 数据预处理
- ii. 在训练集上拟合逻辑回归
- iii. 预测测试结果
- iv. 混淆矩阵（Confusion matrix）结果的测试准确率
- v. 可视化测试集结果

缩放 & 缩放：分割前和分割后的缩放（分割后的结果将不同，因为标准差会不同）

# 分割后缩放

```python
# 数据划分：此示例不需要这个
from sklearn.model_selection import train_test_split
# 0.25 测试大小意味着总观测值的“1/4”
x_train, X_test, y_train, y_test = train_test_split(
(X, y, test_size=0.25, random_state=0)

# 特征缩放
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
x_scaled = sc.fit_transform(X_train)
st_ = StandardScaler()
x_test_scaled = st_.transform(X_test)
```

# 分割前缩放

```python
# 特征缩放
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
x_scaled = sc.fit_transform(X)

# 数据划分
from sklearn.model_selection import train_test_split
# 0.25 测试大小意味着总观测值的“1/4”
x_train, X_test, y_train, y_test = train_test_split(
(x_scaled, y, test_size=0.25, random_state=0)
```

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_85_0.png)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_85_1.png)

# 混淆矩阵

```python
# 将数据集拟合到逻辑回归
from sklearn.linear_model import LogisticRegression
# 使用 "classifier" 而不是 "regression"
classifier = LogisticRegression(random_state=0) # 创建对象
classifier.fit(X_train, y_train)

# 预测
y_pred = classifier.predict(X_test)
```
为什么是线性？因为逻辑回归是一个线性分类器，两个维度上的用户类别通过直线分开。

混淆矩阵：使用混淆矩阵评估性能，它包含了模型在集合上做的正确和错误预测：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_85_2.png)

| | 0 | 1 |
|---|---|---|
| 0 | 65 | 3 |
| 1 | 8 | 24 |

结果的测试准确率：通过解释混淆矩阵可以找到结果的准确率。根据上述输出，我们可以解释为65+24=90（正确输出），8+3=11（错误输出）。

可视化训练集：最后我们将可视化训练集。为了可视化，我们将使用 matplotlib 的 Colormap。我们将区域划分为 0.01 的像素。

```python
# 可视化训练结果
from matplotlib import Colormap
import matplotlib.pyplot as plt
import numpy as np

X1, X2 = np.meshgrid(np.arange(X_set[:,0].min() - 1, X_set[:,0].max() + 1, 0.01), 
                     np.arange(X_set[:,1].min() - 1, X_set[:,1].max() + 1, 0.01))
plt.contourf(X1, X2, classifier.predict(np.array([X1.ravel(), X2.ravel()]).T).reshape(X1.shape), cmap=Colormap('red','green'))
plt.xlim(X1.min(), X1.max())
plt.ylim(X2.min(), X2.max())
for i, j in enumerate(np.unique(y_set)):
    plt.scatter(X_set[y_set == j,0], X_set[y_set == j,1], c=Colormap('yellow','blue')[i], label=j)
plt.title('Logistic Regression Training')
plt.xlabel('Age')
plt.ylabel('Estimated Salary')
plt.legend()
plt.show()
```

在代码中，我们使用了 Colormap matplotlib 库的颜色映射来可视化结果。

- 我们创建了两个变量 x_set 和 y_set 来对应 x_train 和 y_train。

之后，我们使用 np.meshgrid 命令创建一个矩形网格，其范围从 -1（最小）到 1（最大）。我们取的像素点是 0.01。

为了创建填充等高线（Filled Contour），我们使用了 plt.contour，它将创建指定的区域（黄色和蓝色）。在这个函数中，我们传递了 classifier.predict 来显示分类器预测的数据点。

输出：通过检查结果，我们将得到：

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_86_0.png)

- 在下图，我们看到绿色区域有一些蓝色点，红色区域有一些黄色点。
- 所有数据都是训练集的观测点，显示了购买变量的结果。
- 该图使用两个独立变量制作，即 x 轴上的年龄和 y 轴上的估计薪水。
- 黄色点观测值的购买（因变量）可能为 1，意味着购买了 SUV 汽车的用户。
- 蓝色点观测值的购买（因变量）可能为 1，意味着购买了 SUV 汽车的用户。
- 我们也可以从图中估计，薪水较低的年轻用户没有购买汽车，而研究显示高薪水者购买了汽车。
但在绿色区域（不买汽车）中有黄色点，红色区域中有一些蓝色点（买汽车）。因此，高估计薪水的年轻用户购买了汽车，而低薪水的老年用户没有购买。

分类器的目标：我们成功地可视化了逻辑回归的训练集，我们这次分类的目标是划分购买了 SUV 汽车和没有购买汽车的用户（作为预测区域）。从输出中，我们可以清楚地看到两个区域（红色和绿色）以及观测值。

线性分类器：从图中看到，分类器是直线或本质上线性的，我们在逻辑回归中使用线性模型。在后续的主题中，我们将学习非线性分类器。这条线被称为“预测边界”。

