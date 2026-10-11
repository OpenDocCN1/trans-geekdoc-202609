
图 3-49 训练损失曲线

```
loss_history_valid = compute_loss_history(w_history, test_X[0:1000,:], test_y[0:1000], reg)

plt.plot(loss_history, color='r')
plt.plot(loss_history_valid, color='b') 
plt.ylim(0, 5)
plt.xlabel('iterations')
plt.ylabel('loss')
plt.title('iterative learning curve')
plt.legend(['train', 'valid'])
plt.ylim(-0.2, 3)
plt.show()  
```

![](EPUB/media/file86.png)

图 3-50 验证损失曲线

```
print("Accuracy of training set:", getAccuracy(w, train_X, train_y))
print("Accuracy of test set:", getAccuracy(w, test_X, test_y))
```

```
Accuracy on training set: 0.8293
    Accuracy on test set: 0.8171
```

### 3.7.4 随机梯度下降

批量梯度下降每次迭代仅使用一小批样本，而随机梯度下降则更为极端，每次迭代仅使用一个样本。因此，要执行随机梯度下降，只需在调用上述代码中的批量梯度下降方法之前，将批量大小 `batchsize` 修改为 1，即每次仅使用一个样本来更新模型参数。为了节省训练时间，将 epochs 改为 2 次：

```
batchsize = 1
epochs = 2
w = np.zeros([train_X.shape[1] + 1, len(np.unique(train_y))])   
w_history = batch_gradient_descent_softmax(w, train_X, train_y, epochs, batchsize, shuffle, reg, alpha, gamma)
w = w_history[-1]
print("w: ", w)
```

计算模型在训练集和测试集上的准确率：

```
print("Accuracy of training set:", getAccuracy(w, train_X, train_y))
print("The accuracy of the test set:", getAccuracy(w, test_X, y_test))
```

```
Accuracy on training set: 0.81425
    Accuracy on test set: 0.7988
```

#### 总结

线性回归、逻辑回归和 Softmax 回归本质上都是线性分类器。线性回归是输入的线性加权，其回归函数是线性函数（直线）。逻辑回归本质上与线性回归相同，只是将这种线性加权求和的值从区间 (−∞, ∞) 压缩到了区间 (0, 1)，使得输出值具有概率意义，其针对二分类问题的决策曲线仍然是一条直线。Softmax 回归仅将多个线性加权求和视为各类别的得分，然后将它们的值转换为样本属于多个类别的概率值。当它用于多分类问题时，其决策曲线无非就是多条直线罢了。

![](EPUB/media/file233.png)![](EPUB/media/file234.png)![](EPUB/media/file235.png)![](EPUB/media/file236.png)

![](EPUB/media/file237.png)

## 4.1 神经网络

前面学习的线性回归使用数据特征的线性函数来表示特征与目标值之间的函数关系。线性函数过于简单，对于许多机器学习问题，特征与目标值之间的函数关系往往是非线性的。逻辑回归在线性函数的基础上进一步使用非线性函数 sigmoid 函数 `σ(z)` 将线性函数的结果转换为 [0, 1] 之间的概率值，从而使特征与目标值之间存在非线性关系，但仅将线性加权求和转换为概率，也难以表示复杂函数。

如何表示复杂函数？

复杂函数通常可以分解为简单函数，或通过简单的四则运算或函数组合由简单函数构成。例如，逻辑回归的假设函数 `σ(xw + b)` 就是由函数 `z = xw + b` 和 `σ(z)` 组合而成，而函数 `xw + b` 则是由 `x`、`w`、`b` 通过乘法和加法组成的。

非常复杂的函数可以通过简单运算和函数组合来表示。**神经网络** 就是以这种方式将许多简单的 **神经元** 函数组合成一个复杂函数。神经元就是一个逻辑回归函数，即神经元函数对输入进行线性加权，然后使用非线性函数对加权求和进行非线性变换。当然，神经元函数中对加权求和执行非线性变换的函数也可能是其他类似于 sigmoid 函数的简单函数。神经网络由多个神经元（函数）组成，一个神经元的输出作为另一个神经元的输入，一个神经元接受其他神经元的输入，并将简单的加权求和和简单的（非线性）函数变换输出传递给其他神经元。神经元通过相互的输入输出连接形成网络，因此这个复杂函数被称为神经网络。

### 4.1.1 感知机与神经元

#### 1. 感知机

**感知机** 是一个具有二分类功能的简单函数。逻辑回归函数使用 sigmoid 函数将输入的线性加权求和转换为概率 `σ(xxww)`，而感知机则使用阈值函数将输入的线性加权求和转换为 0 和 1：`sign[b](xxww)`。其中 `sign[b](z)` 是一个阶跃函数，根据 z 值是否大于阈值 `b` 输出 1 和 0：

$$
\begin{matrix} 
{sign\_b(z) = \left\{ \begin{matrix} 
1 & {\text{if } z >= b} \\ 
0 & \text{else} \\ 
\end{matrix} \right.} 
\end{matrix}
$$

感知机通过权重向量 `ww` 计算输入 `xx` 的加权求和 `xxww`，然后根据加权求和是否超过某个阈值 `b` 输出 1 或 0 的值。例如，一个具有 3 个输入值的感知机计算如下：

$$f\_{ww,b}(xx) = sign\_b(\sum\limits\_{j = 1}^{3} w\_j x\_j)$$

感知机可以用一个简单的圆圈来可视化。图 4-1 中的感知机接受 3 个输入值并产生一个输出值 `f`：

图 4-1 感知机接受 3 个输入值并产生输出值 `f`

感知机也被称为 "**人工神经元**", 简称 "**神经元**"。它试图模拟人脑中的神经元。神经科学揭示，人脑由许多简单的神经元组成，如图 3-2 所示。

图 4-2 大脑神经元的结构

一个神经元通常有多个树突，主要用于接收传入的信息，而只有一个轴突，轴突末端有许多轴突末梢，可将信息传递给其他神经元，轴突末梢与其他神经元的树突建立连接以传递信号，该连接位置在生物学中称为“突触”。

每个神经元接受多个输入信号，每个输入信号对神经元的权重也不同。如果所有输入信号的加权求和超过神经元内部的“阈值”，则会产生一个输出信号。

用 `f[ww](xx)` 表示感知机函数，即 `f[ww](xx) = sign[b](xxww)`，其中 `xx` 是输入，`ww` 是权重向量，即：

$$
\begin{matrix} 
{f\_{ww}(xx) = \left\{ \begin{matrix} 
1 & {\text{if } \sum\limits\_{j} w\_j x\_j >= b} \\ 
0 & {else} \\ 
\end{matrix} \right.} 
\end{matrix}
$$

上述公式可以转换为：

$$
\begin{matrix} 
{f\_{ww}(xx) = \left\{ \begin{matrix} 
1 & {\text{if } \sum\limits\_{j} w\_j x\_j - b >= 0} \\ 
0 & {otherwise} \\ 
\end{matrix} \right.} 
\end{matrix}
$$

`b` 可以是正数或负数，用 `b` 表示 −`b`，上述公式可以写为：

$$
\begin{matrix} 
{f\_{ww}(xx) = \left\{ \begin{matrix} 
1 & {\text{if } \sum\limits\_{j} w\_j x\_j + b >= 0} \\ 
0 & {else} \\ 
\end{matrix} \right.} 
\end{matrix}
$$
