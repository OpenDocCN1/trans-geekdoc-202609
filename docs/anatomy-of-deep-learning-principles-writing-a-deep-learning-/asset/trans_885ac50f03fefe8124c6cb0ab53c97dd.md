
`TwoLayerNN` 的构造函数 `__init__()` 接受输入层、隐藏层和输出层的神经元数量作为参数，并初始化 2 层神经网络的模型参数。`train()` 用于训练神经网络模型，即根据训练样本，使用梯度下降算法计算最佳模型参数，使这些训练样本的交叉熵损失最小。`train()` 的参数包括一组训练样本 (`X`, `y`)、正则化参数 `reg` 以及梯度下降法的相关超参数（如 `iterations`、学习率 `learning_rate` 和收敛误差）。在梯度下降法的每一步迭代中，`train()` 函数首先前向计算样本的输出值及其中间变量 (`Z1`, `A1`, `Z2`)，使用 softmax 将得分转换为概率值并计算多分类交叉熵损失 (`data_loss`)，然后计算交叉熵损失 (`data_loss`) 关于输出层输出的梯度 `dZ2`，并反向传播以求得关于中间变量和模型参数的梯度（模型参数的梯度包含正则项关于模型参数的梯度 `2 * reg * W2`、`2 * reg * W1`）。

模型的预测函数 `predict()` 根据训练好的神经网络模型预测输入数据 `X` 的目标值，这是一个前向传播计算过程。

第 2.7 节中螺旋数据集的数据特征和目标值可以用上述 2 层神经网络建模。首先生成数据集：

```python
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import data_set as ds

np.random.seed(89)
X, y = ds.gen_spiral_dataset()

# lets visualize the data:
# plt.scatter(X[:, 0], X[:, 1], c=y, s=20, cmap=plt.cm.spring)
# plt.show()
```

![](EPUB/media/file95.png "fig:")

定义一个 `TwoLayerNN` 类对象，将训练集传递给该类对象的构造函数，然后调用其 `train()` 方法进行模型训练：

```python
nn = TwoLayerNN(2, 100, 3)
W1, b1, W2, b2 = nn.train(X, y)
```

```
iteration 0: loss 1.098627
    iteration 1000: loss 0.115216
    iteration 2000: loss 0.053218
    iteration 3000: loss 0.038299
    iteration 4000: loss 0.031767
    iteration 5000: loss 0.028016
    iteration 6000: loss 0.025411
    iteration 7000: loss 0.023476
    iteration 8000: loss 0.022009
    iteration 9000: loss 0.020872
```

使用以下代码输出训练模型的准确率：

```python
# evaluate training set accuracy
# A1 = np.maximum(0, np.dot(X, W1) + b1)
# Z2 = np.dot(A1, W2) + b2
Z2 = nn.predict(X)
predicted_class = np.argmax(Z2, axis=1)
print('training accuracy: %.2f' % (np.mean(predicted_class == y)))
```

```
training accuracy: 0.99
```

可以看出，使用解析导数进行梯度计算训练的模型更准确，达到 99%。以下代码还可视化了比使用数值梯度训练的模型更好的决策边界：

```python
# plot the resulting classifier
h = 0.02
x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                     np.arange(y_min, y_max, h))
XX = np.c_[xx.ravel(), yy.ravel()]
Z = nn.predict(XX)
Z = np.argmax(Z, axis=1)
Z = Z.reshape(xx.shape)
fig = plt.figure()
plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)
plt.scatter(X[:, 0], X[:, 1], c=y, s=20, cmap=plt.cm.spring)
plt.xlim(xx.min(), xx.max())
plt.ylim(yy.min(), yy.max())
# fig.savefig('spiral_net.png')
```

```
(-1.9124776305480737, 1.9275223694519297)
```

![](EPUB/media/file96.png)

图 4-27 螺旋数据点集的分类决策区域

### 4.2.6 任意层神经网络反向传播的推导

上述 2 层神经网络的反向传播推导过程可以扩展到任意深度（层数）神经网络的反向传播推导。即对于任意层 `l`，其加权和 $z^{[l]} = a^{[l-1]}W^{[l]} + b^{[l]}$ 通过激活函数 $g$ 产生输出 $a^{[l]} = g(z^{[l]})$。如果已知损失函数关于 $\frac{\partial\mathcal{L}}{\partial a^{[l]}}$ 的梯度，可求得 $\frac{\partial\mathcal{L}}{\partial z^{[l]}} = \frac{\partial\mathcal{L}}{\partial a^{[l]}}g'(z^{[l]})$。通过 $\frac{\partial\mathcal{L}}{\partial z^{[l]}}$，可获得该层损失函数关于参数 $W^{[l]}$、$b^{[l]}$ 和 $a^{[l-1]}$ 的梯度：

$$\frac{\partial\mathcal{L}}{\partial W^{[l]}} = {a^{[l - 1]}}^{T}\frac{\partial\mathcal{L}}{\partial z^{[l]}}\quad\quad\frac{\partial\mathcal{L}}{\partial b^{[l]}} = np.sum(\frac{\partial\mathcal{L}}{\partial z^{[l]}}, axis = 0, keepdims = True)\quad\quad\frac{\partial\mathcal{L}}{\partial a^{[l - 1]}} = \frac{\partial\mathcal{L}}{\partial z^{[l]}}{W^{[l]}}^{T}$$

对于多样本的向量形式，公式如下：

$$\frac{\partial\mathcal{L}}{\partial Z^{[l]}} = \frac{\partial\mathcal{L}}{\partial A^{[l]}}g'(Z^{[l]})$$

$$\frac{\partial\mathcal{L}}{\partial W^{[l]}} = {A^{[l - 1]}}^{T}\frac{\partial\mathcal{L}}{\partial Z^{[l]}}$$

$$\frac{\partial\mathcal{L}}{\partial b^{[l]}} = np.sum(\frac{\partial\mathcal{L}}{\partial Z^{[l]}}, axis = 0, keepdims = True)$$

$$\frac{\partial\mathcal{L}}{\partial A^{[l - 1]}} = \frac{\partial\mathcal{L}}{\partial Z^{[l]}}{W^{[l]}}^{T}$$

上述公式假设输入 $x = a^{[0]}$ 和中间变量 $z^{[l-1]}$、$a^{[l-1]}$ 均采取行向量形式。

下面将以列向量形式推导损失函数关于中间变量和模型参数的梯度，即假设输入数据 $x = a^{[0]}$、中间变量 $z^{[l-1]}$、$a^{[l-1]}$ 及其梯度均用列向量表示。采用列向量表示时，第 `l` 层的加权和 $z^{[l]}$ 表示为：

$z^{[l]} = W^{[l]}a^{[l-1]} + b^{[l]}$

此时，权重矩阵的每一行（而非每一列）代表一个神经元的权重参数。当然，加权和 $z^{[l]}$ 通过激活函数 $g$ 后也是列向量 $a^{[l]} = g(z^{[l]})$。

如果该层有 `m` 个神经元，输入 $a^{[l-1]}$ 有 `n` 个值，展开加权和的向量形式：

$$
\begin{matrix}
{z^{[l]} = \begin{bmatrix} z_{1}^{[l]} \\ z_{2}^{[l]} \\ \vdots \\ z_{m}^{[l]} \\ \end{bmatrix} = \begin{bmatrix} {\sum\limits_{k = 1}^{n}W_{1k}^{[l]}a_{k}^{[l - 1]} + b_{1}^{[l]}} \\ {\sum\limits_{k = 1}^{n}W_{2k}^{[l]}a_{k}^{[l - 1]} + b_{2}^{[l]}} \\ \vdots \\ {\sum\limits_{k = 1}^{n}W_{mk}^{[l]}a_{k}^{[l - 1]} + b_{m}^{[l]}} \\ \end{bmatrix}} \\
\end{matrix}
$$
