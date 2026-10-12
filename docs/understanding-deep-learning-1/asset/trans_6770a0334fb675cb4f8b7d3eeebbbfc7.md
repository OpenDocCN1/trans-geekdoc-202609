
生成式方法的缺点在于它不能直接预测 `y`。要进行推理，我们必须将生成式方程反转为 `y = g*^−*¹[x, *ϕ*]`，这可能很困难。然而，生成式模型的优势在于我们可以将关于数据如何生成的先验知识构建到模型中。例如，如果我们想预测图像 `x` 中汽车的三维位置和朝向 `y`，那么我们可以将关于汽车形状、三维几何和光传输的知识构建到函数 `x = g[y, *ϕ*]` 中。

这听起来是个好主意，但实际上，判别式模型主导着现代机器学习；从生成式模型利用先验知识中获得的优势，通常会被利用大量训练数据学习非常灵活的判别式模型所超越。

## 习题

**习题 2.1** 要在损失函数（方程 2.5）上“向下”行走，我们测量其关于参数 `ϕ[0]` 和 `ϕ[1]` 的梯度。计算斜率 `∂L/∂ϕ[0]` 和 `∂L/∂ϕ[1]` 的表达式。

**习题 2.2** 证明我们可以通过将习题 2.1 中导数的表达式设为零并求解 `ϕ[0]` 和 `ϕ[1]`，以闭式找到损失函数的最小值。注意这适用于线性回归，但不适用于更复杂的模型；这就是为什么我们使用迭代模型拟合方法，如梯度下降（图 2.4）。

**习题 2.3\*** 考虑将线性回归重新表述为生成式模型，因此我们有 `x = g[y, *ϕ*] = ϕ[0] + ϕ[1]y`。新的损失函数是什么？求用于执行推理的反函数 `y = g*^−*¹[x, *ϕ*]` 的表达式。对于给定的训练数据集 `{x[i], y[i]}`，该模型的预测结果会与判别式版本相同吗？验证这一点的一种方法是编写代码，分别使用这两种方法为三个数据点拟合一条线，看结果是否相同。

# 第 3 章

浅层神经网络

第 2 章介绍了使用一维线性回归的监督学习。然而，该模型只能将输入/输出关系描述为一条直线。本章介绍浅层神经网络。它们描述分段线性函数，表达能力足以近似多维输入和输出之间任意复杂的关系。

## 3.1 神经网络示例

浅层神经网络是具有参数 `*ϕ*` 的函数 `y = f[x, *ϕ*]`，将多变量输入 `x` 映射到多变量输出 `y`。我们将完整定义推迟到第 3.4 节，并通过一个示例网络 `f[x, *ϕ*]` 来介绍主要思想，该网络将标量输入 `x` 映射到标量输出 `y`，并具有十个参数 `*ϕ* = {ϕ[0], ϕ[1], ϕ[2], ϕ[3], θ[10], θ[11], θ[20], θ[21], θ[30], θ[31]}`：

![c3-fig-5001.jpg](images/c3-fig-5001.jpg)

(3.1)

我们可以将此计算分解为三部分：首先，我们计算输入数据的三个线性函数（`θ[10] + θ[11]x`、`θ[20] + θ[21]x` 和 `θ[30] + θ[31]x`）。其次，我们将这三个结果通过一个*激活函数* `a[•]`。最后，我们用 `ϕ[1]、ϕ[2] 和 ϕ[3]` 对生成的三个激活值进行加权，求和，并加上偏移 `ϕ[0]`。

为了完善描述，我们必须定义激活函数 `a[•]`。有很多选择，但最常用的是*线性修正单元*或*ReLU*：

![c3-fig-5002.jpg](images/c3-fig-5002.jpg)

(3.2)

当输入为正时返回输入，否则返回零（图 3.1）。

![Figure 3.1 Rectified linear unit (ReLU). This activation function returns zero if the input is less than zero and returns the input unchanged otherwise. In other words, it clips negative values to zero. Note that there are many other possible choices for the activation function (see figure 3.13), but the ReLU is the most commonly used and the easiest to understand.](images/c3-fig-0001.jpg)

图 3.1 线性修正单元 (ReLU)。如果输入小于零，该激活函数返回零；否则返回未改变的输入。换句话说，它将负值截断为零。注意，激活函数还有许多其他可能的选择（见图 3.13），但 ReLU 是最常用且最容易理解的。

方程 3.1 表示哪一族输入/输出关系可能并不显而易见。尽管如此，前一章的思想都适用。方程 3.1 表示一族函数，该族的特定成员取决于 `*ϕ*` 中的十个参数。如果我们知道这些参数，就可以通过为给定输入 `x` 求解方程来执行推理（预测 `y`）。给定训练数据集 ![c3-fig-5003.jpg](images/c3-fig-5003.jpg)，我们可以定义最小二乘损失函数 `L[*ϕ*]`，并用它来衡量模型对于任意给定参数值 `*ϕ*` 描述该数据集的效果。为了训练模型，我们寻找使该损失最小化的值 ![c3-fig-5004.jpg](images/c3-fig-5004.jpg)。

### 3.1.1 神经网络直觉

事实上，方程 3.1 表示一族连续分段线性函数（图 3.2），最多包含四个线性区域。我们现在分解方程 3.1 并展示它*为什么*描述这一族函数。为了便于理解，我们将函数分为两部分。首先，我们引入中间量：

![c3-fig-5005.jpg](images/c3-fig-5005.jpg)

(3.3)

![Figure 3.2 Family of functions defined by equation 3.1. a–c) Functions for three different choices of the ten parameters ϕ. In each case, the input/output relation is piecewise linear. However, the positions of the joints, the slopes of the linear regions between them, and the overall height vary.](images/c3-fig-0002.jpg)

图 3.2 方程 3.1 定义的函数族。a–c) 十个参数 `*ϕ*` 的三种不同选择对应的函数。在每种情况下，输入/输出关系都是分段线性的。然而，节点的位置、它们之间线性区域的斜率以及整体高度各不相同。

其中我们将 `h[1]、h[2] 和 h[3]` 称为*隐藏单元*。其次，我们通过用线性函数组合这些隐藏单元来计算输出：[¹](#c003.xhtml#c3-fn-0001)

`y = ϕ[0] + ϕ[1]h[1] + ϕ[2]h[2] + ϕ[3]h[3].`

(3.4)

图 3.3 展示了创建图 3.2a 中函数的计算流程。每个隐藏单元包含输入的一个线性函数 `θ[•0] + θ[•1]x`，该直线被 ReLU 函数 `a[•]` 在零以下截断。三条直线穿过零点的位置成为最终输出中的三个“节点”。然后，三条截断后的直线分别由 `ϕ[1]、ϕ[2] 和 ϕ[3]` 加权。最后，加上控制最终函数整体高度的偏移 `ϕ[0]`。

* * *

习题 3.1–3.8

* * *

![Figure 3.3 Computation for function in figure 3.2a. a–c) The input x is passed through three linear functions, each with a different y-intercept θ•0 and slope θ•1. d–f) Each line is passed through the ReLU activation function, which clips negative values to zero. g–i) The three clipped lines are then weighted (scaled) by ϕ1, ϕ2, and ϕ3, respectively. j) Finally, the clipped and weighted functions are summed, and an offset ϕ0 that controls the height is added. Each of the four linear regions corresponds to a different activation pattern in the hidden units. In the shaded region, h2 is inactive (clipped), but h1 and h3 are both active.](images/c3-fig-0003.jpg)
