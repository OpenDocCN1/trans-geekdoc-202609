

## 数学推导版本

我们现在给出同一论证的数学版本。考虑相邻预激活值 **f** 和 **f′** 之间的计算，它们的维度分别为 `D[h]` 和 `D[h′]`：

![c7-fig-5029.jpg](images/c7-fig-5029.jpg)

 (7.27)

其中 **f** 代表预激活值，**Ω** 和 **β** 代表权重和偏置，**a**[•] 是激活函数。

假设输入层 **f** 中的预激活值 `f[j]` 具有方差 ![c7-fig-5030.jpg](images/c7-fig-5030.jpg)。考虑将偏置 `β[i]` 初始化为零，权重 `Ω[ij]` 初始化为均值为零、方差为 ![c7-fig-5031.jpg](images/c7-fig-5031.jpg) 的正态分布。现在我们推导后续层预激活值 **f′** 的均值和方差表达式。

中间值 `f[i]` 的期望（均值）`𝔼[f[i]]` 为：

---

### 附录 C.2 期望

---

![c7-fig-5032.jpg](images/c7-fig-5032.jpg)

 (7.28)

其中 `D[h]` 是输入层 **h** 的维度。我们使用了期望操作规则，并假设隐藏单元 `h[j]` 和网络权重 `Ω[ij]` 的分布在第二行和第三行之间是独立的。

---

### 附录 C.2.1 期望规则

---

利用这个结果，我们看到预激活值 ![c7-fig-5033.jpg](images/c7-fig-5033.jpg) 的方差 ![c7-fig-5030.jpg](images/c7-fig-5030.jpg) 为：

![c7-fig-5034.jpg](images/c7-fig-5034.jpg)

 (7.29)

其中我们使用了方差恒等式 `σ² = 𝔼[(z − 𝔼[z])²] = 𝔼[z²] − 𝔼[z]²`。我们再次假设权重 `Ω[ij]` 和隐藏单元 `h[j]` 的分布在第三行和第四行之间是独立的。

---

### 附录 C.2.3 方差恒等式

---

假设预激活值 `f[j]` 的输入分布关于零对称，其中一半将被 ReLU 函数截断，`h[j]` 的二阶矩 `𝔼[h[j]]²` 将是 `f[j]` 方差 ![c7-fig-5030.jpg](images/c7-fig-5030.jpg) 的一半（见问题 7.14）：

![c7-fig-5035.jpg](images/c7-fig-5035.jpg)

 (7.30)

---

### 问题 7.14

---

这反过来意味着，如果我们希望后续预激活值 **f′** 的方差 ![c7-fig-5036.jpg](images/c7-fig-5036.jpg) 在前向传播期间与原始预激活值 **f** 的方差 ![c7-fig-5030.jpg](images/c7-fig-5030.jpg) 相同，我们应该设置：

![c7-fig-5037.jpg](images/c7-fig-5037.jpg)

 (7.31)

其中 `D[h]` 是应用权重的原始层的维度。这被称为 **He 初始化**。

### 7.5.2 反向传播的初始化

类似的论证确立了梯度 `∂l/∂f[k]` 的方差在反向传播期间如何变化。在反向传播期间，我们乘以权重矩阵的转置 **Ω^T**（公式 7.24），因此等效表达式变为：

![c7-fig-5038.jpg](images/c7-fig-5038.jpg)

 (7.32)

其中 `D[h′]` 是权重连接到的层的维度。

### 7.5.3 前向和反向传播的初始化

如果权重矩阵 **Ω** 不是方阵（即两个相邻层中的隐藏单元数量不同，所以 `D[h]` 和 `D[h′]` 不同），则无法选择方差以同时满足公式 7.31 和 7.32。一种可能的折中方案是使用平均值 `(D[h] + D[h′])/2` 作为项数的代理，这给出：

![c7-fig-5039.jpg](images/c7-fig-5039.jpg)

 (7.33)

[图 7.7](#c007.xhtml#c7-fig-0007) 实证表明，当参数适当初始化时，前向传播中隐藏单元的方差和反向传播中梯度的方差都保持稳定。

---

### 问题 7.15

---

---

### Notebook 7.3 初始化

---

![Figure 7.7 Weight initialization. Consider a deep network with 50 hidden layers and Dh = 100 hidden units per layer. The network has a 100-dimensional input x initialized from a standard normal distribution, a single fixed target y = 0, and a least squares loss function. The bias vectors βk are initialized to zero, and the weight matrices Ωk are initialized with a normal distribution with mean zero and five different variances c7-fig-5031.jpg. a) Variance of hidden unit activations computed in forward pass as a function of the network layer. For He initialization (c7-fig-5031.jpg = 2/Dh = 0.02), the variance is stable. However, for larger values, it increases rapidly, and for smaller values, it decreases rapidly (note log scale). b) The variance of the gradients in the backward pass (solid lines) continues this trend; if we initialize with a value larger than 0.02, the magnitude of the gradients increases rapidly as we pass back through the network. If we initialize with a value smaller, then the magnitude decreases. These are known as the exploding gradient and vanishing gradient problems, respectively.](images/c7-fig-0007.jpg)

[图 7.7](#c007.xhtml#c7-fig-0007a) 权重初始化。考虑一个具有 50 个隐藏层、每层 `D[h]` = 100 个隐藏单元的深层网络。该网络具有 100 维输入 **x**（从标准正态分布初始化）、单一固定目标 `y` = 0 和最小二乘损失函数。偏置向量 `β[k]` 初始化为零，权重矩阵 `Ω[k]` 初始化为均值为零、具有五种不同方差 ![c7-fig-5031.jpg](images/c7-fig-5031.jpg) 的正态分布。a) 前向传播中计算的隐藏单元激活值方差随网络层变化的函数。对于 He 初始化（![c7-fig-5031.jpg](images/c7-fig-5031.jpg) = 2/`D[h]` = 0.02），方差是稳定的。然而，对于较大的值，它迅速增加，对于较小的值，它迅速减少（注意对数刻度）。b) 反向传播中梯度的方差（实线）延续了这一趋势；如果我们用大于 0.02 的值初始化，梯度的幅度在反向通过网络时迅速增加。如果我们用较小的值初始化，则幅度减小。这些分别被称为 **梯度爆炸** 和 **梯度消失** 问题。

## 7.6 示例训练代码

本书的主要关注点是科学性的；这不是实现深度学习模型的指南。尽管如此，在 [图 7.8](#c007.xhtml#c7-fig-0008) 中，我们展示了实现本书迄今探讨思想的 PyTorch 代码。该代码定义了一个神经网络并初始化权重。它创建随机输入和输出数据集并定义最小二乘损失函数。模型使用批量大小为 10 的 SGD with momentum 在 100 个 epoch 上从数据中训练。学习率从 0.01 开始，每 10 个 epoch 减半。

---

### 问题 7.16–7.17

---

![Figure 7.8 Sample code for training two-layer network on random data.](images/c7-fig-0008.jpg)

[图 7.8](#c007.xhtml#c7-fig-0008a) 在随机数据上训练两层网络的示例代码。

要点是，虽然深度学习的底层思想相当复杂，但实现相对简单。例如，反向传播的所有细节都隐藏在单行代码中：`loss.backward()`。

## 7.7 总结

上一章介绍了随机梯度下降（SGD），一种旨在寻找函数最小值的迭代优化算法。在神经网络的背景下，该算法寻找最小化损失函数的参数。SGD 依赖于损失函数相对于参数的梯度，这些参数必须在优化前初始化。本章解决了深度神经网络的这两个问题。

