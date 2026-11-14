
$$
\frac{\partial\mathbf{C}}{\partial\widehat{\mathbf{y}}} = \frac{\partial}{\partial\widehat{\mathbf{y}}}\frac{1}{\mathbf{n}}\sum\limits_{\mathbf{i} = 1}^{\mathbf{n}}\left( \mathbf{y}_{\mathbf{i}} - {\widehat{\mathbf{y}}}_{\mathbf{i}} \right)^{2} = 2 \ast \frac{1}{\mathbf{n}}\sum\limits_{\mathbf{i} = 1}^{\mathbf{n}}\left( \mathbf{y}_{\mathbf{i}} - {\widehat{\mathbf{y}}}_{\mathbf{i}} \right)
$$

设 `y` = [`y`₁, `y`₂, … `y`[`n`]] 和 `ŷ` = [`ŷ`₁, `ŷ`₂, … `ŷ`[`n`]] 分别为实际值和预测值的行向量。因此上式简化如下（公式 15.25）：

**公式 (15.25)**

$$
\frac{\partial\mathbf{C}}{\partial\widehat{\mathbf{y}}} = \frac{2}{\mathbf{n}}\sum\left( \mathbf{y} - \widehat{\mathbf{y}} \right)
$$

现在让我们求 `predicted value`（预测值）关于 `z` 的梯度（公式 15.26）。这会稍微长一点。

**公式 (15.26)**

$$
\begin{array}{ll} \frac{\partial\widehat{\mathbf{y}}}{\partial\mathbf{z}} & {= \frac{\partial}{\partial\mathbf{z}}\sigma\left( \mathbf{z} \right)} \\ & {= \frac{\partial}{\partial\mathbf{z}}\left( \frac{1}{1 + \mathbf{e}^{- \mathbf{z}}} \right)} \\ & {= \frac{\mathbf{e}^{- \mathbf{z}}}{\left( 1 + \mathbf{e}^{- \mathbf{z}} \right)^{2}}} \\ & {= \frac{1}{\left( 1 + \mathbf{e}^{- \mathbf{z}} \right)}^{\ast}\frac{\mathbf{e}^{- \mathbf{z}}}{\left( 1 - \mathbf{e}^{- \mathbf{z}} \right)}} \\ & {= \frac{1}{\left( 1 + \mathbf{e}^{- \mathbf{z}} \right)}^{\ast}\left( 1 - \frac{1}{\left( 1 + \mathbf{e}^{- \mathbf{z}} \right)} \right)} \\ & {= \sigma\left( \mathbf{z} \right) \ast \left( 1 - \sigma\left( \mathbf{z} \right) \right)} \\ \end{array}
$$

`z` 关于权重 `wᵢ` 的梯度见公式 (15.27)。

**公式 (15.27)**

$$
\begin{array}{ll} \frac{\partial\mathbf{z}}{\partial\mathbf{w}_{\mathbf{i}}} & {= \frac{\partial}{\partial\mathbf{w}_{\mathbf{i}}}\left( \mathbf{z} \right)} \\ & {= \frac{\partial}{\partial\mathbf{w}_{\mathbf{i}}}\left( \sum\limits_{\mathbf{i} = 1}^{\mathbf{n}}\mathbf{x}_{\mathbf{i}}\mathbf{w}_{\mathbf{i}} + \mathbf{b} \right)} \\ & {= \mathbf{x}_{\mathbf{i}}} \\ \end{array}
$$

因此我们得到公式 (15.28)，

**公式 (15.28)**

$$
\frac{\partial\mathbf{C}}{\partial\mathbf{w}_{\mathbf{i}}} = \frac{2}{\mathbf{n}}\sum\left( \mathbf{y} - \widehat{\mathbf{y}} \right) \ast \sigma\left( \mathbf{z} \right) \ast \left( 1 - \sigma\left( \mathbf{z} \right) \right) \ast \mathbf{x}_{\mathbf{i}}
$$

偏置项呢？理论上偏置被视为具有常数值 1 的输入。因此（公式 15.29），

**公式 (15.29)**

$$
\frac{\partial C}{\partial b} = \frac{2}{n}\sum\left( y - \widehat{y} \right) \ast \sigma\left( z \right) \ast \left( 1 - \sigma\left( z \right) \right)
$$

## 15.7 多层感知机

`Multilayered Perceptron (MLP)`（多层感知机）是深度学习领域中最常用的神经网络模型之一。它常被称为 `Vanilla Neural Network`（原始神经网络/普通神经网络），比当今复杂的模型更简单。然而，它引入的技术为更先进的神经网络铺平了道路。

`MLP` 用于各种任务，例如股票分析、图像识别、垃圾邮件检测和选举投票预测。

### 15.7.1 基本结构

多层感知机由相互连接、相互传递信息的神经元组成，非常类似于人脑。每个神经元被分配一个值。网络可分为三个主要层，如 [图 15.10](#ch15.xhtml#fig15_10) 所示。

![图 15.10 多层感知机。](images/fig15_10_B.jpg)

*   **输入层**：这是网络的初始层，接收用于产生输出的输入。
*   **隐藏层**：网络至少需要一个隐藏层。隐藏层对输入数据执行计算和操作以产生有意义的结果。
*   **输出层**：该层的神经元显示有意义的输出。
*   **连接**

*   `MLP` 是一种 `Feed Forward Neural Network`（前馈神经网络），这意味着数据从输入层向输出层单向传输。
*   层间连接被赋予 `Weights`（权重），如 [图 15.11](#ch15.xhtml#fig15_11) 所示。连接的权重指定其重要性。这一概念是 `MLP` 学习过程的核心。

    ![图 15.11 带权重的 MLP 架构。](images/fig15_11_B.jpg)

*   虽然输入从环境中获取值，但所有其他神经元的值都是通过涉及前一层权重和值的数学函数计算得出的。
*   例如，[图 15.11](#ch15.xhtml#fig15_11) 中 `h5` 节点的值可能是（公式 15.30），

    **公式 (15.30)**

    ```
    h[5] = h[1] * w[8] + h[2] * w[9] * h[5]
    ```

### 15.7.2 反向传播

`Backpropagation`（反向传播）是一种利用输出作为输入来优化 `MLP` 权重的技术。

在传统的 `MLP` 中，随机权重被分配给所有连接，如 [图 15.12](#ch15.xhtml#fig15_12) 所示。这些随机权重将值传播通过网络以产生实际输出（[图 15.13](#ch15.xhtml#fig15_13)）。自然地，该输出会与预期输出不同。这两个值之间的差异称为 `Error`（误差）。

![图 15.12 用于预测下一个二进制数的简单模型。](images/fig15_12_B.jpg)

![图 15.13 第 1 次迭代——使用训练集的第一个输入进行训练。](images/fig15_13_B.jpg)

`Backpropagation` 指将此误差反向传送通过网络（[图 15.14](#ch15.xhtml#fig15_14)，[图 15.15](#ch15.xhtml#fig15_15)）的过程，自动重新调整权重，使得实际输出与预期输出之间的误差最终最小化（[图 15.16](#ch15.xhtml#fig15_16)）。

![图 15.14 反向传播——从输出层向隐藏层调整权重。](images/fig15_14_B.jpg)

![图 15.15 反向传播——从隐藏层向输入层调整权重。](images/fig15_15_B.jpg)

![图 15.16 特定输入的训练。](images/fig15_16_B.jpg)

这样，当前迭代的输出成为输入并影响下一次输出。这会重复进行，直到产生正确的输出。过程结束时的权重将是神经网络正常工作所依赖的权重（[图 15.16](#ch15.xhtml#fig15_16)，[图 15.17](#ch15.xhtml#fig15_17)）。

![图 15.17 最终模型的生成。](images/fig15_17_B.jpg)

## 15.8 卷积神经网络
