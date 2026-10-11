

## 4.1.2 激活函数

### tanh 函数

```python
def grad_tanh(x):
    a = np.tanh(x)
    return 1 - a**2
```

```python
x = np.arange(-5.0, 5.0, 0.1)
plt.plot(x, np.tanh(x), label="tanh")
plt.plot(x, grad_tanh(x), label="derivative")
plt.legend(loc="upper right", frameon=False)
plt.show()
```

![](EPUB/media/file88.png)

**图 4-13** `tanh(x)` 函数及其导函数 `tanh'(x)` 的图像

### ReLU 函数

当 `x` 大于 0 时，ReLU 函数 `f(x)` 直接输出 `x`，否则输出 0：

$$
Relu(x) = \begin{cases} x & (x > 0) \\ 0 & (x \leq 0) \end{cases}
$$

其导数：

$$
Relu'(x) = \begin{cases} 1 & (x > 0) \\ 0 & (x \leq 0) \end{cases}
$$

以下代码计算 `Relu(x)`、`Relu'(x)`，并绘制 `Relu(x)`、`Relu'(x)` 的函数曲线：

```python
def relu(x):
    return np.maximum(0, x)

def grad_relu(x):
    return 1. * (x > 0)

x = np.arange(-5.0, 5.0, 0.1)
plt.plot(x, relu(x), label="relu")
plt.plot(x, grad_relu(x), label="derivative")
plt.legend(loc="upper right", frameon=False)
plt.show()
```

![](EPUB/media/file89.png)

**图 4-14** `relu(x)` 函数及其导函数 `relu'(x)` 的图像

ReLU 函数还有一些变体，例如 LeakyReLU 函数：

$$
LeakRelu(x) = \begin{cases} x & (x > 0) \\ kx & (x \leq 0) \end{cases}
$$

其导数：

$$
LeakRelu'(x) = \begin{cases} 1 & (x > 0) \\ k & (x \leq 0) \end{cases}
$$

以下代码计算 `LeakRelu(x)`、`LeakRelu'(x)`，并绘制 `LeakRelu(x)`、`LeakRelu'(x)` 的函数曲线：

```python
import numpy as np

def leakRelu(x, k=0.2):
    y = np.copy(x)
    y[y < 0] *= k
    return y

def grad_leakRelu(x, k=0.2):
    return np.clip(x > 0, k, 1.0)
    grad = np.ones_like(x)
    grad[x < 0] = alpha
    return grad

x = np.arange(-5.0, 5.0, 0.1)
plt.plot(x, leakRelu(x), label="leakrelu")
plt.plot(x, grad_leakRelu(x), label="derivative")
plt.legend(loc="upper right", frameon=False)
plt.show()
```

![](EPUB/media/file90.png)

**图 4-15** `leakrelu(x)` 函数及其导函数 `leakrelu'(x)` 的图像

## 4.1.3 神经网络与深度学习

1943 年，心理学家 McCulloch 和数学家 Pitts 参考生物神经元的结构，发表了抽象神经元模型 MP。1949 年，心理学家 Hebb 提出了 Hebb 学习率，认为人脑神经细胞的突触（即连接）强度是可以改变的。1957 年，计算科学家 Frank Rosenblatt 将人工神经元称为“感知机”，并提出了由两层感知机组成的多层感知机（MLP, Multilayer Perceptron）。在现代机器学习中，感知机更常被称为**神经元**，多层感知机也称为人工神经网络（ANN, Artificial Neural Network），简称**神经网络**。

神经网络由许多简单的“神经元”组成，用于表示一个复杂函数。Softmax 函数是一个多元向量值函数，它接受多个输入值并输出多个输出值，或者说该函数的输入和输出都是一个向量。例如，输入向量 $\mathbf{z} = (z_1, z_2, z_3)$ 和输出向量 $\mathbf{f} = \text{softmax}(\mathbf{z})$ 有 3 个输入值和 3 个输出值 $= (f_1, f_2, f_3)$，该函数可以看作由 3 个神经元组成（如图 4-16 所示）。

**图 4-16** Softmax 函数可以看作由 3 个特殊神经元组成的神经网络（图中右侧列的 3 个圆圈）

这 3 个神经元都接受输入向量 $\mathbf{z} = (z_1, z_2, z_3)$ 并分别生成一个输出 $f_1, f_2, f_3$，即：

$$
f_1 = \frac{e^{z_1}}{e^{z_1} + e^{z_2} + e^{z_3}}
$$

$$
f_2 = \frac{e^{z_2}}{e^{z_1} + e^{z_2} + e^{z_3}}
$$

$$
f_3 = \frac{e^{z_3}}{e^{z_1} + e^{z_2} + e^{z_3}}
$$

这 3 个神经元不同于一般神经元；它们不对输入向量 $\mathbf{z} = (z_1, z_2, z_3)$ 进行加权求和，而是根据上述公式直接输出一个结果值 $f_i$。

对于第 2.6 节螺旋数据集（图 2-6）的二维数据点，进行 3 类别的 softmax 回归，首先用 3 个神经元计算输入向量 $\mathbf{x} = (x_1, x_2)$ 的加权和 $\mathbf{z} = (z_1, z_2, z_3)$，然后将这些神经元输出的加权和 $\mathbf{z} = (z_1, z_2, z_3)$ 输入到 softmax 函数的 3 个神经元中，得到最终输出 $\mathbf{f} = (f_1, f_2, f_3)$。该 softmax 回归的假设函数可以看作由以下神经元组成。

**图 4-17** Softmax 回归的假设函数可以看作中间列的三个加权求和神经元，再结合 softmax 函数的三个神经元

在上述神经网络中，最左列的圆圈代表输入的多个特征。对于二维平面坐标点，一个样本只有 2 个特征，即其横纵坐标值 $\mathbf{x} = (x_1, x_2)$。中间列的神经元是输入数据多个特征的加权和 $z_i$，这些加权和 $\mathbf{z} = (z_1, z_2, z_3)$ 直接输出到最右列，即 softmax 函数的 3 个神经元，每个神经元产生一个输出值 $f_i$，构成了 softmax 回归的最终输出 $\mathbf{f} = (f_1, f_2, f_3)$。可以看出，数据从左侧输入，从右侧输出。左列神经元的输出是右侧神经元的输入。同一列神经元之间没有连接，右侧神经元也不会向左侧神经元输出。也就是说，这是一个数据沿“从左到右”方向推进而不回头的计算过程。这样的神经网络称为**前馈神经网络**（Feedforward Neural Network）。

前馈神经网络中每一列的所有神经元称为神经网络的一层，输入数据的特征通常称为**输入层**，产生最终输出的最后一列神经元称为**输出层**，中间每一列神经元称为**隐藏层**。在前馈神经网络中，数据从输入层开始，依次经过每个隐藏层，最后通过输出层输出神经网络函数的最终输出值。在某些书籍中，包含输入层在内的层数称为神经网络的层数。例如，上述神经网络称为 3 层神经网络；而在某些书籍中，上述神经网络称为 2 层神经网络，即不包含输入层。

如图 4-18 所示，softmax 函数可以看作一个产生多个输出的神经元，而不是看作多个神经元。

**图 4-18** 将 softmax 函数视为一个产生多个输出的单个神经元

