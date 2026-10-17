
其中使用了 `$N_L + N_R = N_P$`。纯度完全取决于子节点中最大类别的数量。尽管这个数字在不同的划分中可以保持不变，但子节点的纯度会有很大不同。Breiman 等人（1984）给出了一个数值示例：假设有两个类别，且父节点具有相同的奇性，$N_{P1} = N_{P2} = 400$。一种可能的划分是 $N_{L1} = 100, N_{L2} = 200, N_{R1} = 200, N_{R2} = 100$。两种划分均导致 $\Delta I = (600-400)/800 = 1/4$。然而，第二次划分是更优的，因为它沿着水平方向划分，从而产生了一个叶子节点。对于第一次划分，子节点是不纯的，需要再次划分。

图 5.10 显示了我们之前的示例，即由决策树分类的区域。图 5.11 显示了相应的决策树。每个节点代表一个区域的划分。第一个节点沿 2.5 处的垂直线对整个区域进行划分。在这个例子中，这是有利的，因为一个类别完全位于其他类别的左侧，导致沿垂直线划分时得到一个纯节点。该线右侧的区域沿水平线进行划分。最后一个节点将该线下方且第一条线右侧的区域在 4.95 处进行垂直划分。可以看出，可以通过将水平划分稍微调低到 1.65 处来改进该决策树。这将导致一个被误分类的 `virginica` 样本被正确分类。

决策树的深度由三个参数控制：

- 允许的分支节点数量。
- 划分节点中所需的最小样本数。
- 每个叶子节点的最小样本数。

在图 5.10 的示例中，叶子节点中的最小样本数设置为 2。将其设置为 1 会导致进一步的划分。事实上，最后一个区域在 1.65 处进行水平划分，导致被误分类的 `virginica` 样本被正确分类。这增加了决策树的深度。如果决策树的深度不受控制，它对未见数据的泛化能力就会变差，因为它与训练数据拟合得过于紧密。

列表 5.4 为数据交织的更具挑战性的情况生长决策树。该区域根据决策树进行分类。图 5.11a 显示了当最小样本数为...

```python
import numpy as np

import matplotlib.pyplot as plt

from sklearn import datasets

from sklearn.tree import DecisionTreeClassifier

from sklearn.inspection import DecisionBoundaryDisplay

d = datasets.load()

# Iris setosa 存储在前 50 个条目中。

# Iris versicolor 存储在接下来的 50 个条目中。

# Iris virginia 存储在接下来的 50 个条目中。
```

```python
# 创建一个 SVM 的分类实例
t = DecisionTreeClassifier(criterion='gini', Impurity measure.
min_samples_split=5, Minimum to split.
min_samples_leaf=2 Minimum in leaf.)
```

```python
# 我们考虑长度和宽度，即第一和第二个特征。
# 我们考虑花瓣长度和宽度，即第三和第四特征。
# 我们在整个数据上进行训练。
# 样本数量，因此物种。
# 三：150
n = 150
X = d.data[0, 0:2] # 特征 1 和 2。
y = d.target[0:n]

# 拟合模型。
t.fit(X, y)
```

```python
colors = np.repeat(['r'],50)
colors = np.append(colors, np.repeat(['g'],50))
colors = np.append(colors, np.repeat(['b'],50))

# 绘制决策边界
display = DecisionBoundaryDisplay.from_estimator(
t, X, grid_resolution=1000,
response_method='predict',
plot_method='contour',
xlabel=d.feature_names[0], ylabel=d.feature_names[1],
cmap = 'Greys',
alpha =0.5)
```

```python
# 显示数据。
disp.ax.scatter(X[:,0], X[:,1], facecolors='none',
edgecolors = colors[0:n])
plt.show()
```

```python
# 显示树。
tree.plot_tree(t)
plt.show()
```

列表 5.4：在 Python 中生长树。非线性 https://github.com/Non-Linear-Matlab.

![](img/c6c76bf52016db7e78a5e30d4766ef81_155_0.png)

(a) 纯度量。

![](img/c6c76bf52016db7e78a5e30d4766ef81_155_1.png)

(b) 决策树分类。

图 5.10：决策树分类。

图 5.9 以图的形式说明了这一点。通过比较 GDI、离度和节点误差的图表，类别具有相似奇性的节点在 GDI 和 离度下被认为比节点误差下更不纯。这产生的效果是节点误差不会导致创建更纯的子节点的倾向。为了观察这一点，

```
$$\Delta I = (1 - \max p_{PK}) \frac{N_L}{N_P} - (1 - \max p_{Lk}) \frac{N_{Lk}}{N_L} - (1 - \max p_{Rk}) \frac{N_R}{N_P} - (1 - \max p_{Rk}) \frac{N_{Rk}}{N_R})$$\n$= 1 - \max \frac{N_{Pk}}{N_P} - \max \frac{N_{Lk}}{N_P} + \max \frac{N_{Lk}}{N_L} - \max \frac{N_R}{N_P} - \max \frac{N_{Rk}}{N_R}$$\n$= \frac{1}{N_P}(\max N_{Lk} + N_{Rk} - \max N_{Pk})$$
```

其中使用了 `$N_L + N_R = N_P$`。纯度完全取决于子节点中最大类别的数量。尽管这个数字在不同的划分中可以保持不变，但子节点的纯度会有很大不同。Breiman 等人（1984）给出了一个数值示例：假设有两个类别，且父节点具有相同的奇性，$N_{P1} = N_{P2} = 400$。一种可能的划分是 $N_{L1} = 100, N_{L2} = 200, N_{R1} = 200, N_{R2} = 100$。两种划分均导致 $\Delta I = (600-400)/800 = 1/4$。然而，第二次划分是更优的，因为它沿着水平方向划分，从而产生了一个叶子节点。对于第一次划分，子节点是不纯的，需要再次划分。

图 5.10 显示了我们之前的示例，即由决策树分类的区域。图 5.11 显示了相应的决策树。每个节点代表一个区域的划分。第一个节点沿 2.5 处的垂直线对整个区域进行划分。在这个例子中，这是有利的，因为一个类别完全位于其他类别的左侧，导致沿垂直线划分时得到一个纯节点。该线右侧的区域沿水平线进行划分。最后一个节点将该线下方且第一条线右侧的区域在 4.95 处进行垂直划分。可以看出，可以通过将水平划分稍微调低到 1.65 处来改进该决策树。这将导致一个被误分类的 `virginica` 样本被正确分类。

决策树的深度由三个参数控制：

- 允许的分支节点数量。
- 划分节点中所需的最小样本数。
- 每个叶子节点的最小样本数。

在图 5.10 的示例中，叶子节点中的最小样本数设置为 2。将其设置为 1 会导致进一步的划分。事实上，最后一个区域在 1.65 处进行水平划分，导致被误分类的 `virginica` 样本被正确分类。这增加了决策树的深度。如果决策树的深度不受控制，它对未见数据的泛化能力就会变差，因为它与训练数据拟合得过于紧密。

列表 5.4 为数据交织的更具挑战性的情况生长决策树。该区域根据决策树进行分类。图 5.11a 显示了当最小样本数为...

![](img/c6c76bf52016db7e78a5e30d4766ef81_163_0.png)

来自属于负类的点 `(0,0)`, `(0,1)` 和 `(1,0)`。图 5.14 中的任何一条红线都可以由 `$w_1v_1 + w_2v_2 - b = 0$` 描述。对于任何一条线，右侧的点应该输出为 1，而左侧的点应该输出为 0。

Heaviside 阶跃函数定义为：

```
$H(x) = \begin{cases} 0 & x \leq 0 \\ 1 & x > 0 \end{cases}$
```

也被称为硬限幅传输函数。使用此作为激活函数，生成的神经网络可能是：

![](img/c6c76bf52016db7e78a5e30d4766ef81_163_1.png)

学习过程可能对 `$w_1, w_2$` 和 `$b$` 产生了不同的选择。同样，逻辑或（OR）：

| $v_1$ | $v_2$ | OR |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

可以如图 5.15 所示实现。再次使用 Heaviside 阶跃

![](img/c6c76bf52016db7e78a5e30d4766ef81_164_0.png)

函数，结果神经网络的一种可能性是

![](img/c6c76bf52016db7e78a5e30d4766ef81_164_1.png)

继续这个主题，可以实现逻辑与非（NAND），例如：

| v1 | v2 | NAND |
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

![](img/c6c76bf52016db7e78a5e30d4766ef81_164_2.png)

列表 5.5a 实现了一个简单的双层神经网络类。它在列表 5.5b 中用于学习逻辑运算符 AND、OR 和 NAND。

然而，简单的神经网络无法实现异或（XOR，二选一，但不同兼者）。

| v1 | v2 | XOR |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

## 非线性分类

```python
# 简单的双层神经网络类。
class NeuralNetworks:
    def __init__(self,
                 output,
                 hidden,
                 tol,
                 epoch):
        # 输入神经元的数量
        # 输出神经元的数量
        # 隐藏神经元的数量
        # 容差
        # 迭代次数
        # 学习率
        self.in_size = input
        self.nout = output
        self.hidden = hidden
        self.tol = tol
        self.epoch = epoch
        self.learning_rate = rate
        self.weights_in = np.random.randn(self.in_size, hidden)

        self.weights_out = np.random.randn(hidden, self.nout)

    def forward(self, X):
        # 添加偏置并与权重相乘
        self.weights_in += np.random.randn(*self.weights_in.shape)
        # 激活函数
        Y = np.tanh(np.dot(X, self.weights_in))
        # 添加偏置并与权重相乘
        self.weights_out += np.random.randn(*self.weights_out.shape)
        # 激活函数
        Y = np.sigmoid(np.dot(Y, self.weights_out))
        return Y

    def train(self, X, target):
        # 传播训练数据
        perm = np.random.permutation(X.shape[0])
        X = X[perm]
        target = target[perm]
        Z = np.dot(X, self.weights_in)
        Y = np.tanh(Z)
        # 激活函数
        Y = np.dot(Y, self.weights_out)
        # 所有训练样本的误差
        errors = Y - target
        cost = 0.5 * np.sum(errors**2)
        epoch = 0
        while epoch < self.epoch and cost < self.tol:
            # 传播误差
            # 用于矩阵乘法组件
            # 使用 sigmoid 导数的属性
            delta = errors * Y * (1 - Y)
            # 更新层中的权重
            self.weights_out -= np.dot(Y.T, delta) * self.learning_rate
            # 更新层中的权重
            delta = np.dot(delta, self.weights_out.T) * (1 - Y**2)
            self.weights_in -= np.dot(X.T, delta) * rate
            # 打乱数据
            perm = np.random.permutation(X.shape[0])
            X = X[perm]
            target = target[perm]
            # 添加偏置，与权重相乘
            Z = np.dot(X, self.weights_in)
            Y = np.tanh(Z)
            Y = np.dot(Y, self.weights_out)
            # 所有训练样本的误差
            errors = Y - target
            cost = 0.5 * np.sum(errors**2)
            epoch += 1
        return epoch
```

图 5.a：简单网络类。

```python
import numpy as np
import pandas
import matplotlib.pyplot as plt

# 定义逻辑运算符
def OR(v1,v2):
    if not (v1.all() in (0,1) and v2.all() in (0,1)):
        raise ValueError("输入为0 或 1")
    return v1 | v2

def AND(v1,v2):
    if not (v1.all() in (0,1) and v2.all() in (0,1)):
        raise ValueError("输入为0 或 1")
    return v1 & v2

def XOR(v1,v2):
    if not (v1.all() in (0,1) and v2.all() in (0,1)):
        raise ValueError("输入为0 或 1")
    return OR(v1,v2) ^ AND(v1,v2)

# 显示为 dataframe
# 每行是一个样本，每列是一个特征
v1 = np.array([[0,0],[1,1]]).astype(int).reshape(-1,1)
v2 = np.array([[0,1],[1,0]]).astype(int).reshape(-1,1)
data = np.hstack((v1, v2, OR(v1,v2), AND(v1,v2)))
df = pandas.DataFrame(data)
df.columns = ['v1', 'v2', 'OR', 'AND']
df.index = ['*', '*']
print(df)

# 定义逻辑 sigmoid 作为激活函数。它对
负 值不敏感，零附近是过渡区
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def sigmoid_derivative(y):
    return y * (1 - y)

# 学习逻辑运算符
X = data[:,2]
target = data[:,3:]
NN = NeuralNetwork(min=2, out=1, hidden=2, tol=0.1, epoch=100, rate=0.1)
print("训练前的迭代次数：")
print(NN.predict(X))
print("收敛的迭代次数：")
NN.train(X,target)
print("训练后四舍五入到整数：")
print(np.round(NN.predict(X)).astype(int))
```

列表 5.5：Python 中的神经网络逻辑运算符。

图 5.16 显示真区域需要与两个侧的假区域分开。一种可能的解决方案是具有两个阶梯的激活函数，例如：
