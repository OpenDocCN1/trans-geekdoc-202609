
在上述代码中，特征 1 被添加到输入数据 `X` 的每个数据特征 `X[i]` 中。因此，调用此函数时，只需传递输入数据本身的特征即可。以下代码测试梯度下降法的向量版本，以拟合上述平面数据：

```
learning_rate = 0.02
num_iters = 100
X = np.hstack((xs[:, None], ys[:, None]))
history = gradient_descent_vec(X, y, learning_rate, num_iters)
print("w:", history[-1])
```

```
w: [5.2574307 3.00002524 1.99999406]
```

根据 `history` 中记录的迭代过程中的模型参数，计算每次迭代过程中模型参数对应的假设函数在训练数据集上的平均损失：

```
def compute_loss_history(X, y, w_history):
    loss_history = []
    for w in w_history:
        errors = X @ w[1:] + w[0] - y
        loss_history.append((errors ** 2).mean() / 2)
    return loss_history
```

```
loss_history = compute_loss_history(X, y, history)
print(loss_history[:-1:10])
plt.plot(loss_history, linewidth=2)
plt.title("Gradient descent with learning rate = " + str(learning_rate), fontsize=16)
plt.xlabel("number of iterations", fontsize=14)
plt.ylabel("cost", fontsize=14)
plt.grid()
plt.show()
```

```
[50.488263686179806, 4.228316318122407, 0.25447029668776583, 0.013353012122347907, 0.005607394691562173, 0.0004965791382370437, 5.787738027991273e-05, 7.432016613222019e-06, 6.995869865807676e-07, 1.9291969094070538e-08]
```

![](EPUB/media/file49.png)

**图 3-13 损失曲线**

可以看到，获得了相同的良好拟合结果。

#### 3. 温度与压力问题

让我们看一个简单的温度与压力问题。大气中的压力和温度（在气体中）是相关的。如果给定一组（温度、压力）数据，能否用模型从温度预测压力（反之亦然）？

如果温度和压力数据放在 CSV 格式文件 `data.csv` 中，可以使用 pandas 包的 `read_csv()` 从文件读取数据：

```
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

data = pd.read_csv('data.csv', delimiter=',')  # delimiter 表示分隔符是什么
data
```

![](EPUB/media/file50.png)

```
X = data.values[:, 1:2]
y = data.values[:, 2]
print(X)
print(y)
```

```
[[ 0.]
 [20.]
 [ 40.]
 [60.]
 [ 80.]
 [100.]]
[2.0e-04 1.2e-03 6.0e-03 3.0e-02 9.0e-02 2.7e-01]
```

调用 `gradient_descent_vec()` 进行线性回归：

```
history = gradient_descent_vec(X, y, 0.00005, 50)
w = history[-1]
print("w:", w)
```

```
w: [-0.00016333 0.00165672]
```

绘制代价曲线和测试的预测值：

```
def plot_history_predict(X, y, w, loss_history, fig_size=(12, 4)):
    fig = plt.gcf()
    fig.set_size_inches(fig_size[0], fig_size[1], forward=True)

    plt.subplot(1, 2, 1)
    plt.plot(loss_history)

    X = np.hstack((np.ones((X.shape[0], 1), dtype=X.dtype), X))  # 添加一列特征 1
    x = X[:, 1]

    predicts = X @ w
    plt.subplot(1, 2, 2)
    plt.scatter(x, predicts)  # , marker="x", c="red"

    indices = x.argsort()
    sorted_x = x[indices[::-1]]
    sorted_predicts = predicts[indices[::-1]]

    plt.plot(sorted_x, sorted_predicts, color='red')
    # plt.plot(x, predicts, color='red')

    plt.scatter(x, y)  # , marker="x", c="red"
    plt.show()
```

绘制损失函数曲线和训练样本的预测值：

```
loss_history = compute_loss_history(X, y, history)
plot_history_predict(X, y, w, loss_history)
```

![](EPUB/media/file51.png)

**图 3-14 损失曲线和拟合直线**

虽然获得了拟合温度与压力关系的最佳线性模型，但从图中可以看出，压力和温度并非线性关系，线性假设函数不是最佳选择。它们之间应存在非线性关系。很自然地，会想到使用多项式函数（如 3 次多项式）来表示压力 `y` 与温度 `x` 之间的这种非线性关系。

$$f(x) = w[3]x^3 + w[2]x^2 + w[1]x + w[0] = (1, x, x^2, x^3)(w[0], w[1], w[2], w[3])^T$$

从原始特征 `x` 出发，人为构造新特征 `x²`、`x³`，并将 1 也作为一个特征，因此 `x` 可视为由 4 个特征组成的数据特征向量 `x = (1, x, x², x³)`。

$$f(x; w) = (1, x, x^2, x^3)(w[0], w[1], w[2], w[3])^T = x w$$

其中，`w` 是模型参数。

首先生成包含 4 个特征（包括 1）的数据：

```
X2 = np.hstack((X, X**2, X**3))
print(X2)
```

```
[[0.00e+00 0.00e+00 0.00e+00]
 [2.00e+01 4.00e+02 8.00e+03]
 [4.00e+01 1.60e+03 6.40e+04]
 [6.00e+01 3.60e+03 2.16e+05]
 [8.00e+01 6.40e+03 5.12e+05]
 [1.00e+02 1.00e+04 1.00e+06]]
```

随后实施梯度下降法，但发现损失函数持续快速增加直至无穷大，并未收敛。

```
history = gradient_descent_vec(X2, y, 0.00005, 50)
print("w:", history[-1])
```

```
w: [nan nan nan nan]

D:\Programs\Anaconda3\lib\site-packages\ipykernel_launcher.py:8: RuntimeWarning: overflow encountered in matmul
D:\Programs\Anaconda3\lib\site-packages\ipykernel_launcher.py:10: RuntimeWarning: overflow encountered in matmul
D:\Programs\Anaconda3\lib\site-packages\ipykernel_launcher.py:8: RuntimeWarning: invalid value encountered in matmul
```

这是因为数据的特征值均为较大数值，导致梯度过大，必须使用极小学习率，但过小的学习率会使算法收敛极其缓慢。解决此问题的方法是对数据特征进行归一化，使数据特征值落入较小的取值范围（如 `[0,1]` 或 `[-1,1]`）。

### 3.1.10 数据归一化

特征的归一化过程非常简单：首先计算所有样本关于该特征的平均值，然后计算所有样本该特征围绕平均值的离散程度（即标准差），最后将所有样本的该特征减去其均值并除以标准差。

$$x \leftarrow \frac{x - \text{mean}(x)}{\text{stddev}(x)}$$

其中 `x` 是一组数字，`mean(x)` 是 `x` 中数字的平均值，`stddev(x)` 是 `x` 中数字的标准差（均方差）。例如，有一组特征值：{-5, 6, 9, 2, 4}，其平均值为：

```
mean = (-5 + 6 + 9 + 2 + 4) / 5 = 3.2
```

从所有特征值中减去该平均值得到偏差，并计算这些偏差的平方：

$$
\begin{matrix}
(-5 - 3.2)^2 = 67.24 \\
(6 - 3.2)^2 = 7.84 \\
(9 - 3.2)^2 = 33.64 \\
(2 - 3.2)^2 = 1.44 \\
(4 - 3.2)^2 = 0.64
\end{matrix}
$$

然后，计算标准差 `stddev`：

$$\text{stddev} = \sqrt{(67.24 + 7.84 + 33.64 + 1.44 + 0.64)/5} = 4.71$$

对于之前的 `X2`，可以使用以下代码计算每个特征的均值（`mean`）和均方差（`stddev`）：

```
mean = np.mean(X2, axis=0)
stddev = np.std(X2, axis=0)
print(mean)
print(stddev)
X2 = (X2 - mean) / stddev
print(X2)
```

```
[5.00000000e+01 3.66666667e+03 3.00000000e+05]
[3.41565026e+01 3.55840164e+03 3.58924319e+05]
[[-1.46385011 -1.03042518 -0.8358308 ]
 [-0.87831007 -0.91801516 -0.81354198]
 [-0.29277002 -0.5807851  -0.65752023]
 [ 0.29277002 -0.018735   -0.23403262]
 [ 0.87831007  0.76813514  0.59065376]
 [ 1.46385011  1.77982532  1.95027186]]
```
