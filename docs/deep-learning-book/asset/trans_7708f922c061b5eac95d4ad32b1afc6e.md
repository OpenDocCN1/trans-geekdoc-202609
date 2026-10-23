
将表达式写成迹运算符（trace operator）的形式，为我们利用许多有用的恒等式来操纵该表达式提供了机会。例如，迹运算符对转置运算符是不变的：

$$\operatorname{Tr}(A)=\operatorname{Tr}(A^\mathsf{T}). \tag{2.50}$$

由多个因子组成的方阵的迹，也允许将最后一个因子移动到第一个位置而不改变其值，前提是对应矩阵的形状允许定义结果乘积：

$$\operatorname{Tr}(ABC)=\operatorname{Tr}(CAB)=\operatorname{Tr}(BCA). \tag{2.51}$$

或者更一般地，

$$\operatorname{Tr}\left(\prod_{i=1}^{n}F^{(i)}\right)=\operatorname{Tr}\left(F^{(n)}\prod_{i=1}^{n-1}F^{(i)}\right). \tag{2.52}$$

即使结果乘积具有不同的形状，这种对循环置换的不变性也成立。例如，对于 $A \in \mathbb{R}^{m\times n}$ 和 $B \in \mathbb{R}^{n\times m}$，我们有

$$\operatorname{Tr}(AB)=\operatorname{Tr}(BA). \tag{2.53}$$

尽管 $AB \in \mathbb{R}^{m\times m}$ 且 $BA \in \mathbb{R}^{n\times n}$。

另一个值得牢记的有用事实是，标量就是其自身的迹：$a=\operatorname{Tr}(a)$。

## 2.11 行列式

方阵的行列式，记作 $\det(A)$，是一个将矩阵映射为实数标量的函数。行列式等于矩阵所有特征值的乘积。行列式的绝对值可以被视为矩阵乘法扩展或收缩空间程度的度量。如果行列式为 0，则空间在至少一个维度上完全收缩，导致其失去所有体积。如果行列式为 1，则该变换保持体积不变。

## 2.12 示例：主成分分析

一种简单的机器学习算法，**主成分分析（PCA）**，可以仅利用基本的线性代数知识推导得出。

假设我们有一个包含 $m$ 个点 $\{\boldsymbol{x}^{(1)}, \dots, \boldsymbol{x}^{(m)}\}$ 的集合，它们位于 $\mathbb{R}^{n}$ 中，并且我们希望对这些点进行有损压缩。有损压缩意味着以占用更少内存但可能损失部分精度的方式存储点。我们希望尽可能少地损失精度。

编码这些点的一种方法是表示它们的低维版本。对于每个点 $\boldsymbol{x}^{(i)} \in \mathbb{R}^{n}$，我们将找到一个对应的码字向量 $\boldsymbol{c}^{(i)} \in \mathbb{R}^{l}$。如果 $l$ 小于 $n$，那么存储码字点所占用的内存将少于存储原始数据。我们将寻找一种编码函数来为输入生成码字，$f(\boldsymbol{x}) = \boldsymbol{c}$，以及一种解码函数，根据码字生成重建的输入，$\boldsymbol{x} \approx g(f(\boldsymbol{x}))$。

PCA 由我们对解码函数的选择来定义。具体来说，为了使解码器非常简单，我们选择使用矩阵乘法将码字映射回 $\mathbb{R}^{n}$。设 $g(\boldsymbol{c}) = \boldsymbol{D}\boldsymbol{c}$，其中 $\boldsymbol{D} \in \mathbb{R}^{n \times l}$ 是定义解码的矩阵。

计算该解码器的最优码字可能是一个困难的问题。为了使编码问题保持简单，PCA 约束 $\boldsymbol{D}$ 的列彼此正交。（请注意，除非 $l = n$，否则 $\boldsymbol{D}$ 在技术上仍然不是“正交矩阵”。）

根据迄今为止描述的问题，许多解都是可能的，因为如果我们按所有点的比例减小 $c_{i}$，我们可以增加 $\boldsymbol{D}_{:i}$ 的尺度。为了使问题具有唯一解，我们约束 $\boldsymbol{D}$ 的所有列具有单位范数。

为了将这个基本想法变成我们可以实施的算法，我们需要做的第一件事是弄清楚如何为每个输入点 $\boldsymbol{x}$ 生成最优码字点 $\boldsymbol{c}^{*}$。做到这一点的一种方法是最小化输入点 $\boldsymbol{x}$ 与其重建 $g(\boldsymbol{c}^{*})$ 之间的距离。我们可以使用范数来衡量这个距离。在主成分算法中，我们使用 $L^{2}$ 范数：

$$\boldsymbol{c}^{*} = \arg\min_{\boldsymbol{c}} \| \boldsymbol{x} - g(\boldsymbol{c}) \|_{2}. \tag{2.54}$$

我们可以改用平方 $L^{2}$ 范数而不是 $L^{2}$ 范数本身，因为两者都由 $\boldsymbol{c}$ 的同一个值最小化。由于 $L^{2}$ 范数是非负的，且平方运算对非负参数是单调递增的，因此两者都由 $\boldsymbol{c}$ 的同一个值最小化。

$$\boldsymbol{c}^{*} = \arg\min_{\boldsymbol{c}} \| \boldsymbol{x} - g(\boldsymbol{c}) \|_{2}^{2}. \tag{2.55}$$

被最小化的函数简化为

$$(\boldsymbol{x} - g(\boldsymbol{c}))^{\top}(\boldsymbol{x} - g(\boldsymbol{c})) \tag{2.56}$$

（根据 $L^2$ 范数的定义，公式 2.30）

$$= \boldsymbol{x}^{\top} \boldsymbol{x} - \boldsymbol{x}^{\top} g(\boldsymbol{c}) - g(\boldsymbol{c})^{\top} \boldsymbol{x} + g(\boldsymbol{c})^{\top} g(\boldsymbol{c}) \tag{2.57}$$

（根据分配律）

$$= \boldsymbol{x}^{\top} \boldsymbol{x} - 2\boldsymbol{x}^{\top} g(\boldsymbol{c}) + g(\boldsymbol{c})^{\top} g(\boldsymbol{c}) \tag{2.58}$$

（因为标量 $g(\boldsymbol{c})^{\top} \boldsymbol{x}$ 等于其自身的转置）。

我们现在可以再次更改被最小化的函数，省略第一项，因为这一项不依赖于 $\boldsymbol{c}$：

$$\boldsymbol{c}^* = \arg\min_{\boldsymbol{c}} -2\boldsymbol{x}^{\top} g(\boldsymbol{c}) + g(\boldsymbol{c})^{\top} g(\boldsymbol{c}) \tag{2.59}$$

为了进一步取得进展，我们必须代入 $g(\boldsymbol{c})$ 的定义：

$$\boldsymbol{c}^* = \arg\min_{\boldsymbol{c}} -2\boldsymbol{x}^{\top} \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^{\top} \boldsymbol{D}^{\top} \boldsymbol{D}\boldsymbol{c} \tag{2.60}$$

$$= \arg\min_{\boldsymbol{c}} -2\boldsymbol{x}^{\top} \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^{\top} \boldsymbol{I}_l \boldsymbol{c} \tag{2.61}$$

（根据 $\boldsymbol{D}$ 的正交性和单位范数约束）

$$= \arg\min_{\boldsymbol{c}} -2\boldsymbol{x}^{\top} \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^{\top} \boldsymbol{c} \tag{2.62}$$

我们可以使用向量微积分来解决这个优化问题（如果你不知道如何做，请参见第 4.3 节）：

$$\nabla \left(-2\boldsymbol{x}^{\top} \boldsymbol{D}\boldsymbol{c} + \boldsymbol{c}^{\top} \boldsymbol{c}\right) = \boldsymbol{0} \tag{2.63}$$

$$-2\boldsymbol{D}^{\top} \boldsymbol{x} + 2\boldsymbol{c} = \boldsymbol{0} \tag{2.64}$$

$$\boldsymbol{c} = \boldsymbol{D}^{\top} \boldsymbol{x} \tag{2.65}$$

这使得算法高效：我们可以仅使用一个矩阵-向量操作来最优地编码 $\boldsymbol{x}$。要编码一个向量，我们应用编码函数

$$f(\boldsymbol{x}) = \boldsymbol{D}^{\top} \boldsymbol{x} \tag{2.66}$$

使用进一步的矩阵乘法，我们还可以定义 PCA 重建操作：

$$r(\boldsymbol{x}) = g\left(f(\boldsymbol{x})\right) = \boldsymbol{D}\boldsymbol{D}^{\top} \boldsymbol{x} \tag{2.67}$$

接下来，我们需要选择编码矩阵 $\boldsymbol{D}$。为此，我们重新审视最小化输入和重建之间 $L^2$ 距离的想法。由于我们将使用同一个矩阵 $\boldsymbol{D}$ 来解码所有的点，我们不能再孤立地考虑这些点。相反，我们必须最小化在所有维度和所有点上计算出的误差矩阵的 Frobenius 范数：

$$\boldsymbol{D}^* = \arg\min_{\boldsymbol{D}} \sqrt{\sum_{i,j} \left(x_j^{(i)} - r(\boldsymbol{x}^{(i)})_j\right)^2} \text{ subject to } \boldsymbol{D}^{\top} \boldsymbol{D} = \boldsymbol{I}_l. \tag{2.68}$$

为了推导寻找 $\boldsymbol{D}^*$ 的算法，我们先考虑 $l = 1$ 的情况。在这种情况下，$\boldsymbol{D}$ 只是一个单个向量 $\boldsymbol{d}$。将公式 2.67 代入公式 2.68 并将 $\boldsymbol{D}$ 简化为 $\boldsymbol{d}$，问题归结为

$$\boldsymbol{d}^* = \arg\min_{\boldsymbol{d}} \sum_i \|\boldsymbol{x}^{(i)} - \boldsymbol{d}\boldsymbol{d}^{\top} \boldsymbol{x}^{(i)}\|_2^2 \text{ subject to } \|\boldsymbol{d}\|_2 = 1. \tag{2.69}$$

上述表述是执行替换最直接的方式，但不是书写公式最美观的方式。它将标量值 $\boldsymbol{d}^{\top} \boldsymbol{x}^{(i)}$ 放在向量 $\boldsymbol{d}$ 的右侧。标量系数通常写在它们作用的向量左侧。因此，我们通常将这样的公式写为

$$\boldsymbol{d}^* = \arg\min_{\boldsymbol{d}} \sum_i \|\boldsymbol{x}^{(i)} - \boldsymbol{d}^{\top} \boldsymbol{x}^{(i)}\boldsymbol{d}\|_2^2 \text{ subject to } \|\boldsymbol{d}\|_2 = 1, \tag{2.70}$$

或者，利用标量是其自身转置的事实，写为

$$\boldsymbol{d}^* = \arg\min_{\boldsymbol{d}} \sum_i \|\boldsymbol{x}^{(i)} - \boldsymbol{x}^{(i)\top} \boldsymbol{d}\boldsymbol{d}\|_2^2 \text{ subject to } \|\boldsymbol{d}\|_2 = 1. \tag{2.71}$$

读者应努力熟悉这类外观上的重新排列。

此时，将问题改写为单个示例设计矩阵的形式，而不是作为对单独示例向量的求和，可能很有帮助。这将使我们能够使用更紧凑的符号。设 $\boldsymbol{X} \in \mathbb{R}^{m\times n}$ 为通过堆叠描述点的所有向量定义的矩阵，使得 $\boldsymbol{X}_{i,:} = \boldsymbol{x}^{(i)}$。我们现在可以将问题重写为

$$\boldsymbol{d}^* = \arg\min_{\boldsymbol{d}} \|\boldsymbol{X} - \boldsymbol{X}\boldsymbol{d}\boldsymbol{d}^{\top}\|_F^2 \text{ subject to } \boldsymbol{d}^{\top} \boldsymbol{d} = 1. \tag{2.72}$$

暂时忽略约束条件，我们可以将 Frobenius 范数部分简化如下：

$$\arg\min_{\boldsymbol{d}} \|\boldsymbol{X} - \boldsymbol{X}\boldsymbol{d}\boldsymbol{d}^{\top}\|_F^2 \tag{2.73}$$

