
行列式仅对方阵有定义，并且等于将矩阵所表示的变换应用于单位（超）立方体后所产生的平行六面体的有符号体积。在二维情况下，这只是将矩阵所表示的变换应用于单位正方形后所产生的平行四边形的有符号面积。

计算 `n` 维矩阵行列式的通用公式运行时间为 `O(n³)`。对于我们的示例，我们只需要二维的公式，如下所示：

$$
\det\begin{pmatrix} a & b \\ c & d \end{pmatrix} = ad - bc
$$

因此，对于我们的示例，雅可比行列式为 1/3 × 1/2 − 0 × 0 = 1/6。这就是我们需要确保变换后概率分布仍积分到 1 的 1/6 缩放因子！

![](img/f0f0f5d89818fdddf117bbe758ac8143_199_0.png)

根据定义，行列式是有符号的——也就是说，它可以为负。因此我们需要取雅可比行列式的绝对值以获得体积的相对变化。

## The Change of Variables Equation

现在我们可以写下一个描述 `X` 和 `Z` 之间变量变换过程的单一方程。这被称为变量变换方程（方程 6-1）。

方程 6-1。变量变换方程

$$
p_X(x) = p_Z(z) |\det(\partial z / \partial x)|
$$

这如何帮助我们构建生成模型？关键在于理解，如果 `p_Z(z)` 是一个可以轻松采样的简单分布（例如高斯分布），那么理论上我们需要做的就是找到一个合适的可逆函数 `f(x)`，它可以将数据 `X` 映射到 `Z`，以及对应的逆函数 `g(z)`，该函数可用于将采样的 `z` 映射回原始域中的点 `x`。我们可以使用前面涉及雅可比行列式的方程来找到数据分布 `p(x)` 的精确、可处理公式。

然而，在实际应用中存在两个主要问题，我们首先需要解决！

首先，计算高维矩阵的行列式在计算上极其昂贵——具体来说，它是 `O(n³)`。这在实践中完全不切实际，因为即使是小的 32 × 32 像素灰度图像也有 1,024 个维度。

其次，如何计算可逆函数 `f(x)` 并非显而易见。我们可以使用神经网络来找到某个函数 `f(x)`，但不一定能反转该网络——神经网络只在一个方向上工作！

为了解决这两个问题，我们需要使用一种特殊的神经网络架构，确保变量变换函数 `f` 是可逆的，并且其行列式易于计算。

我们将在下一节中看到如何使用一种称为 real-valued non-volume preserving (`RealNVP`) 变换的技术来实现这一点。

## RealNVP

`RealNVP` 最早由 Dinh et al. 在 2017 年提出。¹ 在该论文中，作者展示了如何构建一个神经网络，将复杂的数据分布转换为简单的高斯分布，同时具有可逆性和雅可比矩阵易于计算的期望特性。

![](img/f0f0f5d89818fdddf117bbe758ac8143_200_0.png)

### Running the Code for This Example

本示例的代码可以在书籍仓库中的 Jupyter notebook `notebooks/06_normflow/01_realnvp/realnvp.ipynb` 中找到。

该代码改编自 Mandolini Giorgio Maria 等人创建的优秀 `RealNVP` 教程，该教程可在 Keras 网站上获得。

## The Two Moons Dataset

我们将在本示例中使用的

![](img/f0f0f5d89818fdddf117bbe758ac8143_201_0.png)

图 6-4. 二维中的双月数据集

创建此数据集的代码在示例 6-1 中给出。

#### 示例 6-1. 创建 moons 数据集

```
data = datasets.make_moons(3000, noise=0.05)[0].astype("float32")
norm = layers.Normalization()
norm.adapt(data)
normalized_data = norm(data)
```

- ① 创建一个包含 3,000 个点的带噪声、未归一化的 moons 数据集。
- ② 将数据集归一化，使均值为 0，标准差为 1。

我们将构建一个 `RealNVP` 模型，该模型能够生成在 2D 中遵循与双月数据集相似分布的点。虽然这是一个非常简单的示例，但它将帮助我们深入细致地理解归一化流模型在实践中的工作原理。

然而，首先，我们需要介绍一种新型层，称为耦合层。

## 耦合层

耦合层为其输入的每个元素生成缩放因子和转换因子。换句话说，它生成两个与输入大小完全相同的张量，一个用于缩放因子，一个用于转换因子，如图 6-5 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_201_1.png)

图 6-5. 耦合层输出与输入形状相同的两个张量：缩放因子 (`s`) 和转换因子 (`t`)

为了构建我们简单示例的自定义 `Coupling` 层，我们可以堆叠 `Dense` 层来创建缩放输出，并使用另一组 `Dense` 层来创建转换输出，如示例 6-2 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_202_0.png)

对于图像，耦合层块使用 `Conv2D` 层而不是 `Dense` 层。

#### 示例 6-2. Keras 中的耦合层

```
def Coupling():
    input_layer = layers.Input(shape=2) ①

    s_layer_1 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(input_layer) ②
    s_layer_2 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_1)
    s_layer_3 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_2)
    s_layer_4 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_3)
    s_layer_5 = layers.Dense(
        2, activation="tanh", kernel_regularizer=regularizers.l2(0.01)
    )(s_layer_4) ③

    t_layer_1 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(input_layer) ④
    t_layer_2 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_1)
    t_layer_3 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_2)
    t_layer_4 = layers.Dense(
        256, activation="relu", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_3)
    t_layer_5 = layers.Dense(
        2, activation="linear", kernel_regularizer=regularizers.l2(0.01)
    )(t_layer_4) ⑤

    return models.Model(inputs=input_layer, outputs=[s_layer_5, t_layer_5]) ⑥
```

- ① 我们示例中耦合层块的输入有两个维度。
- ② 缩放流是大小为 256 的 `Dense` 层堆叠。
- ③ 最终的缩放层大小为 2 且具有 `tanh` 激活。
- ④ 转换流是大小为 256 的 `Dense` 层堆叠。
- ⑤ 最终的转换层大小为 2 且具有线性激活。
- ⑥ 耦合层被构造为具有两个输出（缩放因子和转换因子）的 Keras 模型。

注意通道数如何暂时增加，以便学习更复杂的表示，然后再压缩回与输入相同的通道数。在原始论文中，作者还在每个层上使用正则化器来惩罚较大的权重。

## 将数据通过耦合层传递

耦合层的架构并不特别有趣——使其独特的是输入数据在通过该层时被掩码和转换的方式，如图 6-6 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_203_0.png)

图 6-6. 输入 `x` 通过耦合层的转换过程

注意只有数据的最初 `d` 个维度被送入第一个耦合层——剩余的 `D − d` 个维度完全被掩码（即设为零）。在我们 `D = 2` 的简单示例中，选择 `d = 1` 意味着耦合层看到的不是两个值 `(x₁, x₂)`，而是 `(x₁, 0)`。

层的输出是缩放因子和转换因子。这些再次被掩码，但这次使用的是与之前*相反*的掩码，因此只有后半部分被放行——即在我们的示例中，我们得到 `(0, s₂)` 和 `(0, t₂)`。然后它们按元素应用于输入的后半部分 `x₂`，而输入的前半部分 `x₁` 则直接原样通过，完全不被更新。综上所述，对于维度为 `D` 且 `d < D` 的向量，更新方程如下：

$$
z_{1:d} = x_{1:d}
$$

$$
z_{d+1:D} = x_{d+1:D} \odot \exp(s(x_{1:d})) + t(x_{1:d})
$$

你可能想知道为什么我们要费心构建一个掩码如此多信息的层。如果我们研究该函数的雅可比矩阵的结构，答案就很清楚了：

$$
\frac{\partial z}{\partial x} = \begin{bmatrix} \mathbf{I} & 0 \\ \frac{\partial z_{d+1:D}}{\partial x_{1:d}} & \text{diag}(\exp[s(x_{1:d})]) \end{bmatrix}
$$

左上角的 `d × d` 子矩阵只是单位矩阵，因为 `z_{1:d} = x_{1:d}`。这些元素直接原样通过而不被更新。因此右上角的子矩阵为 0，因为 `z_{1:d}` 不依赖于 `x_{d+1:D}`。

左下角子矩阵很复杂，我们不寻求简化它。右下角子矩阵只是一个对角矩阵，填充了 `exp(s(x_{1:d}))` 的元素，因为 `z_{d+1:D}` 在线性上依赖于 `x_{d+1:D}`，而梯度仅依赖于缩放因子（不依赖于转换因子）。图 6-7 显示了这种矩阵形式的示意图，其中只有非零元素用颜色填充。

注意对角线上方没有非零元素——因此这种矩阵形式被称为*下三角*。现在我们看到了这样结构化矩阵的好处——下三角矩阵的行列式就等于对角线元素的乘积。换句话说，行列式不依赖于左下角子矩阵中的任何复杂导数！

$$
J = \partial z / \partial x =
$$

![](img/f0f0f5d89818fdddf117bbe758ac8143_205_0.png)

图 6-7. 变换的雅可比矩阵——一个下三角矩阵，其行列式等于对角线上元素的乘积

因此，我们可以按如下方式写出该矩阵的行列式：

$$
\det(J) = \exp[\sum_j s(x_{1:d})_j]
$$

这很容易计算，这也是构建归一化流模型的两个原始目标之一。

另一个目标是该函数必须易于求逆。我们可以看到这是正确的，因为我们只需重新排列前向方程即可写出可逆函数，如下所示：

$$
x_{1:d} = z_{1:d}
$$

$$
x_{d+1:D} = (z_{d+1:D} - t(x_{1:d})) \odot \exp(-s(x_{1:d}))
$$

等价的示意图显示在图 6-8 中。

![](img/f0f0f5d89818fdddf117bbe758ac8143_206_0.png)

图 6-8. 逆函数 `x = g(z)`

我们现在几乎拥有构建 `RealNVP` 模型所需的一切。然而，仍有一个问题未解决——我们应如何更新输入的最初 `d` 个元素？目前它们完全未被模型更改！

## 堆叠耦合层

为了解决这个问题，我们可以使用一个非常简单的技巧。如果我们将耦合层堆叠在一起但交替掩码模式，则被一层未更改的层将在下一层中被更新。这种架构还有额外的好处，即能够学习数据的更复杂表示，因为它是一个更深的神经网络。

该组合耦合层的雅可比矩阵仍然易于计算，因为线性代数告诉我们矩阵乘积的行列式是行列式的乘积。同样，两个函数组合的逆只是逆的组合，如以下方程所示：

$$
\det(A \cdot B) = \det(A)\det(B)
$$

$$
(f_b \circ f_a)^{-1} = f_a^{-1} \circ f_b^{-1}
$$

因此，如果我们堆叠耦合层，每次翻转掩码，我们就可以构建一个神经网络，能够转换整个输入张量，同时保留具有简单雅可比行列式和可逆性的基本特性。图 6-9 显示了整体结构。

![](img/f0f0f5d89818fdddf117bbe758ac8143_207_0.png)

Figure 6-9. 堆叠耦合层，并在每层交替掩码

## 训练 RealNVP 模型

现在我们已经构建了 `RealNVP` 模型，可以训练它来学习双月数据集的复杂分布。记住，我们希望最小化模型下数据的负对数似然 `– log p_X(x)`。使用公式 6-1，我们可以将其写为如下形式：

$$
- \log p_X(x) = - \log p_Z(z) - \log |\det(\partial z / \partial x)|
$$

我们选择前向过程 `f` 的目标输出分布 `p_Z(z)` 为标准高斯分布，因为我们可以轻松地从该分布中采样。然后，我们可以通过应用逆过程 `g`，将从高斯分布中采样的点转换回原始图像域，如图 6-10 所示。

![](img/f0f0f5d89818fdddf117bbe758ac8143_207_1.png)

Figure 6-10. 在 1D（中间行）和 2D（底部行）中在复杂分布 `p_X(x)` 与简单高斯分布 `p_Z(z)` 之间进行转换

#### 示例 6-3. 在 Keras 中构建 RealNVP 模型
