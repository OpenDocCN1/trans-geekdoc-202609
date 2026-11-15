

其中 f(z) 是激活函数。简单网络中激活函数的典型选择包括 logistic 函数（更常被称为 sigmoid 函数）和 tanh 函数（可以被视为 logistic 函数的重新缩放版本）：

```math
sigmoid(z) = \frac{1}{1 + e^{-z}}

tanh(z) = \frac{e^{-z} - e^{z}}{e^{z} + e^{-z}} = \frac{2}{1 + e^{-2z}} - 1
```

这两个函数的图像如下：

![](img/da8fb67f2acf661518076e08b6ffd9b9_36_0.png)

目前我们在单层网络中将使用 logistic 函数。

对于 K 个可能类别的情况，连接隐藏层到输出层的权重矩阵 \( w^{(2)} \) 的大小为 H 乘以 K。每一列 \( w_k^{(2)} \) 表示与类别 k 相关的系数。输出层的输入是隐藏层的输出 \( a^{(2)} = \{a_1^{(2)}, a_2^{(2)}, \dots, a_l^{(2)}\} \)，x 属于类别 k 的概率可以用数学表达式表示（为保持一致性，我们将其表示为 \( a_k^{(3)} \)）：

```math
a_k^{(3)} = f(z^{(3)}) = softmax_k(W^{(2)}a^{(2)})
```

同样，给定 m 个训练样本，为了训练神经网络，我们使用梯度下降法学习所有权重 \( w = \{w^{(1)}, w^{(2)}\} \)，目标是最小化均方误差代价 J(w)。

梯度 \(\Delta w\) 的计算可以通过 **反向传播算法** 实现。
反向传播算法的思路如下：我们首先遍历网络，计算所有隐藏层和输出层的输出；然后从最后一层开始向后移动，计算每个节点对最终输出误差的贡献程度，并将其向后传播到之前的层。在我们的单层网络中，详细步骤如下：

- 1. 计算隐藏层的 \(a^{(2)}\) 并将它们馈送到输出层以计算输出 \(a^{(3)}\)
- 2. 对于输出层，计算单个样本的代价函数关于每个单元的导数 \(\delta_k^{(3)} = \frac{\partial}{\partial z_k^{(3)}} J(W) = -(y_k - a_k^{(3)}) \cdot f'(z_k^{(3)})\)，\(\delta^{(3)} = -(y - a^{(3)}) \cdot f'(z^{(3)})\)，重写为整个层
- 3. 对于隐藏层，我们根据 \(\delta^{(3)}\) 的加权平均计算误差项 \(\delta^{(2)} : \delta^{(2)} = ((W^{(2)})^T \delta^{(3)}) \cdot f'(z^{(2)})\)
- 4. 应用链式法则计算梯度：

```math
\triangle W^{(2)} = \frac{\partial J(W)}{\partial z_k^{(3)}} \frac{\partial z_k^{(3)}}{\partial W^{(2)}} = \delta^{(3)} (a^{(2)})^T
```

```math
\triangle W^{(1)} = \frac{\partial J(W)}{\partial z_k^{(2)}} \frac{\partial z_k^{(2)}}{\partial W^{(1)}} = \delta^{(2)} (x)^T
```

我们通过执行这些步骤反复更新所有权重，直到代价函数收敛。

简要回顾单层网络后，我们可以将其作为数字分类项目的第二个解决方案。

再次，我们使用 `nnet` 包来实现我们的单层网络：

```r
> model_nn <- nnet(label ~ ., data=data_train, size=50, maxit=300,
MaxNWts=100000, decay=1e-4)
# weights: 39760
initial value 108597.598656
iter 10 value 27708.286001
iter 20 value 16027.005297
iter 30 value 14058.141050
iter 40 value 12615.442747
iter 50 value 11793.700937
iter 60 value 11026.672273
iter 70 value 10654.855058
iter 80 value 10193.580947
iter 90 value 9854.836168
iter 100 value 9544.973159
iter 110 value 9307.192737
iter 120 value 9043.028253
iter 130 value 8845.069307
iter 140 value 8686.707561
iter 150 value 8525.104362
iter 160 value 8281.609223
iter 170 value 8140.051273
iter 180 value 7998.721024
iter 190 value 7854.388240
iter 200 value 7712.459027
iter 210 value 7636.945553
iter 220 value 7557.675909
iter 230 value 7449.854506
iter 240 value 7355.021651
iter 250 value 7259.186906
iter 260 value 7192.798089
iter 270 value 7055.027833
iter 280 value 6957.926522
iter 290 value 6866.641511
iter 300 value 6778.342997
final value 6778.342997
stopped after 300 iterations
```

我们使用包括以下参数拟合模型：

- size=50：隐藏层中有 50 个隐藏单元。
- MaxNWts=100000：它最多允许 100,000 个权重。在我们的例子中，权重矩阵 w<sup>(1)</sup> 中有 (784 个输入维度 + 1 个偏置) * 50 个隐藏单元 = 39,250 个元素，权重矩阵 w<sup>(2)</sup> 中有 (50 个隐藏单元 + 1 个偏置) * 10 个输出单元 = 510 个元素。因此总共有 39,760 个权重。
- decay=1e-4：正则化强度，权重衰减为 0.0001。
- maxit=300：最大迭代次数设置为 300。

我们在测试集上应用训练好的网络模型：

```r
> prediction_nn <- predict(model_nn, data_test, type = "class")
> cm_nn = table(data_test$label, prediction_nn)
> cm_nn
```

| True \ Predicted | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 987 | 0 | 3 | 3 | 2 | 11 | 10 | 7 | 5 | 5 |
| 1 | 0 | 1134 | 9 | 6 | 0 | 2 | 0 | 5 | 11 | 4 |
| 2 | 14 | 9 | 918 | 31 | 11 | 11 | 7 | 15 | 22 | 6 |
| 3 | 3 | 1 | 17 | 966 | 0 | 41 | 3 | 14 | 24 | 18 |
| 4 | 4 | 3 | 8 | 2 | 929 | 4 | 11 | 11 | 5 | 41 |
| 5 | 12 | 2 | 6 | 17 | 5 | 851 | 15 | 9 | 26 | 5 |
| 6 | 10 | 1 | 14 | 0 | 9 | 14 | 970 | 0 | 15 | 1 |
| 7 | 4 | 4 | 23 | 6 | 5 | 2 | 0 | 1010 | 7 | 39 |
| 8 | 5 | 15 | 9 | 18 | 5 | 31 | 9 | 4 | 912 | 7 |
| 9 | 11 | 2 | 1 | 20 | 52 | 4 | 0 | 36 | 8 | 913 |

```r
> accuracy_nn = mean(prediction_nn == data_test$label)
> accuracy_nn
[1] 0.9135944
```

比我们的第一次尝试更好！我们可以使用深度学习模型，比如说更多的隐藏层，做得更好吗？当然可以。

## 向网络中添加更多隐藏层

我们刚刚使用单层神经网络模型达到了 91.3% 的准确率。理论上，我们可以使用多个隐藏层获得更好的模型。作为示例，我们提供一个具有两个隐藏层的深度神经网络模型的解决方案：

![](img/da8fb67f2acf661518076e08b6ffd9b9_39_0.png)

前馈深度神经网络中的权重优化也是通过反向传播算法实现的，这与单层网络相同。但是，层数越多，计算复杂度越高，模型收敛越慢。加速权重优化的一种方法是使用计算效率更高的激活函数。近年来最流行的是整流线性单元（ReLU）：

```math
relu(z) = z^+ = \max(0, z)
```

![](img/da8fb67f2acf661518076e08b6ffd9b9_40_0.png)

```math
relu'(z) = \begin{cases} 0, z < 0 \\ 1, z \ge 0 \end{cases}
```

得益于其导数的特性，与 sigmoid 相比，使用 ReLU 激活函数有两个主要优势：

- 学习更快，因为 \( relu'(z) \) 是常数，而 logistic 函数 \( sigmoid'(z) = sigmoid(z) * (1 - sigmoid(z)) \) 不是。
- 不太可能出现梯度消失问题，即梯度的指数级下降，这可能出现在多层堆叠的 sigmoid 层网络中。由于我们在计算每个层的误差 \(\delta\) 时要乘以激活函数的导数，而 \( sigmoid'(z) \) 的最大值为 ¼，随着我们堆叠越来越多的 sigmoid 层，梯度会呈指数级下降。

我们在前面章节中使用的 `nnet` 包目前只能建模单层网络。在本章中，我们使用 `MXNet` 包来实现具有多个隐藏层的深度神经网络。`MXNet (`https://mxnet.incubator.apache.org/`)` 是一个支持包括 R、Scala、Python、Julia、C++ 和 Perl 在内的编程语言的深度学习框架。它由 `DMLC (`http://dmlc.ml/`)` 团队开发，这是一个专家团队，致力于开源机器学习项目的协作。它是可移植的，可以扩展到多个 CPU、多个 GPU 和多个机器，例如在云中。最重要的是，它允许我们灵活且高效地构建最先进的深度学习模型，包括深度神经网络、CNN 和 RNN。

让我们先安装 MXNet：

```r
> cran <- getOption("repos")
> cran["dmlc"] <- "https://s3-us-west-2.amazonaws.com/apache-mxnet/R/CRAN/"
> options(repos = cran)
> if (!require("mxnet"))
install.packages("mxnet")
```

现在我们可以导入 MXNet 并将数据转换为 MXNet 中神经网络模型偏好的格式：

```r
> require(mxnet)
> data.train <- data.matrix(data_train)
> data.train.x <- data_train[,-1]
> data.train.x <- t(data.train.x/255)
> data.train.y <- data_train[,1]
```

注意，我们通过除以最大可能值 255 将输入特征缩放到 0 到 1 的范围。否则，深度神经网络可能会偏向某些特征，这种偏差会随着层数累积。

现在训练数据集已准备就绪，我们可以通过定义其架构来开始构建网络，如下所示：

```r
> data <- mx.symbol.Variable("data")
> fc1 <- mx.symbol.FullyConnected(data, name="fc1", num_hidden=128)
> act1 <- mx.symbol.Activation(fc1, name="relu1", act_type="relu")
> fc2 <- mx.symbol.FullyConnected(act1, name="fc2", num_hidden=64)
> act2 <- mx.symbol.Activation(fc2, name="relu2", act_type="relu")
> fc3 <- mx.symbol.FullyConnected(act2, name="fc3", num_hidden=10)
> softmax <- mx.symbol.SoftmaxOutput(fc3, name="sm")
```

在 MXNet 的 Symbol API 中，我们使用 symbol 数据类型表示网络。我们从输入层数据开始，即输入数据，然后是第一个隐藏层 fc1，包含 128 个节点，它与输入层完全连接。然后我们将 ReLU 函数附加到 fc1，并输出该层的激活值 act1。同样，我们链接另一个隐藏层 fc2，这次有 64 个节点，并输出基于 ReLU 的激活值 act2。最后，我们使用 softmax 函数结束输出层，生成对应 10 个类别的 10 个概率。整体结构如下：

