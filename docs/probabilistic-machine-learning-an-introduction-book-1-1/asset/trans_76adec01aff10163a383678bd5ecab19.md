
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_788_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_788_1.png)

例如，考虑绝对值函数 f(x) = |x|。其次微分由下式给出

∂f(x) = \begin{cases} \{-1\} & \text{if } x < 0 \\\ [-1,1] & \text{if } x = 0 \\\ \{+1\} & \text{if } x > 0 \end{cases}

(B.63)

其中记号 [-1, 1] 表示 -1 到 1 之间（含端点）的任意值。参见图 B.11 作图示。

## B.4.5 泰勒级数近似

在许多情况下，函数并非凸函数，但在某点附近可能是局部凸的。特别地，我们可能能够在某个邻域内计算线性或二次近似。这称为（一阶或二阶）泰勒级数展开。

更详细地说，设 f : \mathbb{R}^n \to \mathbb{R} 为二阶可微函数。我们可以在点 a \in \mathbb{R}^n 附近计算线性近似，使用

\hat f(x) = f(a) + \nabla f(a)^\top (x - a)

(B.64)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_789_0.png)

图 B.12：布雷格曼散度的示意图。

其中 ∇ 为梯度。若 f 为凸函数，则 f̂ 是线性下界（参见图 B.12）。

我们可以在点 a ∈ ℝⁿ 附近计算二次近似，使用

f̂(x) = f(a) + ∇f(a)ᵀ (x − a) + ½ (x − a)ᵀ ∇²f(a) (x − a)  (B.65)

其中 ∇² 为海森矩阵。

## B.4.6 布雷格曼散度

设 f : Ω → ℝ 为定义在闭凸集 Ω 上的连续可微、严格凸函数。我们按如下方式定义与 f 相关的布雷格曼散度 [Brc67]：

D_f(w, v) = f(w) − f(v) − (w − v)ᵀ ∇f(v)  (B.66)

为理解此式，令

f̂_v(w) = f(v) + (w − v)ᵀ ∇f(v)  (B.67)

为以 v 为中心的 f 的一阶泰勒级数近似。则布雷格曼散度为与该线性近似的差：

D_f(w, v) = f(w) − f̂_v(w)  (B.68)

参见图 B.12 作图示。由于 f 为凸函数，我们有 D_f(w, v) ≥ 0，因为 f̂_v 是 f 的线性下界（另见图 B.7b）。

下面我们提及布雷格曼散度的一些重要特例。

- 若 f(w) = ||w||²，则 D_f(w, v) = ||w − v||² 为平方欧几里得距离。
- 若 f(w) = wᵀ Q w，则 D_f(w, v) 为平方马哈拉诺比斯距离（第 3.5.2 节）。
- 若 w 为指数族分布的自然参数，且 f(w) = log Z(w) 为对数归一化因子，则布雷格曼散度与库尔贝克-莱布勒散度相同（第 6.2 节）。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_790_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_790_1.png)

图 B.13：共轭函数的示意图。红色线为原函数 f(x)，蓝色线为线性下界 λx。为使界紧，我们找到 ∇f(x) 与 λ 平行的 x，并将直线向上滑动使其在该处相切；向上滑动的量由 f*(λ) 给出。改编自 [Bis06] 的图 10.11。由 conjugateFunction.m 生成。

## B.4.7 共轭对偶

本节简要讨论共轭对偶，这是一种构造非凸函数的线性下界的有用方法，然后我们可以轻松地最大化它。我们遵循 [Bis06, 第 10.5 节] 的表述。

### B.4.7.1 引言

考虑任意连续函数 f(x)，并假设我们为其构造形如

$$\mathcal{L}(\mathbf{x}, \lambda) \triangleq \lambda^{\top} \mathbf{x} - f^{*}(\lambda) \le f(\mathbf{x}) \tag{B.69}$$

的线性下界，其中 λ 为我们选择的斜率，f*(λ) 为截距，我们将在下面求解。参见图 B.13(a) 作图示。

对于固定的 λ，我们可以通过“向上滑动”直线直到它在 x_λ 处与曲线相切，如图 B.13(b) 所示，来找到下界紧的点 x_λ。在 x_λ 处，我们最小化函数与下界之间的距离：

$$\mathbf{x}_{\lambda} \triangleq \arg\min_{\mathbf{x}} f(x) - \mathcal{L}(\mathbf{x}, \lambda) = \arg\min_{\mathbf{x}} f(\mathbf{x}) - \lambda^{\top} \mathbf{x} \tag{B.70}$$

（我们假设该最小值存在且唯一。）由于在此点下界是紧的，我们有

$$f(\mathbf{x}_{\lambda}) = \mathcal{L}(\mathbf{x}_{\lambda}, \lambda) = \lambda^{\top} \mathbf{x}_{\lambda} - f^{*}(\lambda) \tag{B.71}$$

且因此

$$f^{*}(\lambda) = \lambda^{\top} \mathbf{x}_{\lambda} - f(\mathbf{x}_{\lambda}) = \max_{\mathbf{x}} \lambda^{\top} \mathbf{x} - f(\mathbf{x}) \tag{B.72}$$

函数 f* 称为 f 的共轭，也称为 f 的芬切尔变换。对于可微 f 的特殊情况，f* 称为 f 的勒让德变换。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_791_0.png)

图 B.14：红色曲线为 f(x)= e^{-x}，彩色直线为线性下界。斜率为 λ 的每个下界在点 x_λ = −log(−λ) 处与曲线相切，其中 f(x_λ)= e^{log(−λ)} = −λ。对于蓝色曲线，这发生在 x_λ = ξ 处。改编自 [Bis06] 的图 10.10。由 optLowerbound.m 生成。

共轭函数有用的一个原因是它们可用于为非凸函数创建凸下界。即我们有 L(x, λ) ≤ f(x)，当 x = x_λ 时取等号，对任意函数 f : ℝ^D → ℝ 成立。对于任意给定的 x，我们可以对 λ 进行优化以使界尽可能紧，从而得到固定函数 L(x)；这称为变分近似。然后我们可以尝试最大化关于 x 的该下界，而不是最大化 f(x)。该方法在近似贝叶斯推断中被广泛使用，如我们在第 7.7.3 节中所讨论的。

### B.4.7.2 示例：指数函数

让我们考虑一个例子。假设 f(x)= e^{-x}，它为凸函数。考虑形如

L(x, λ) = λx − f*(λ) (B.73)

的线性下界，其中共轭函数由下式给出

f*(λ) = max_x λx − f(x) = −λ log(−λ) + λ (B.74)

如图 B.14 所示。

### B.4.7.3 共轭的共轭

如果我们取共轭的共轭，会发生什么是有趣的：

$f^{**}(\mathbf{x}) = \max_{\boldsymbol{\lambda}} \boldsymbol{\lambda}^{\top} \mathbf{x} - f^{*}(\boldsymbol{\lambda})$  (B.79)

若 $f$ 为凸函数，则 $f^{**} = f$，因此 $f$ 和 $f^{*}$ 称为 **共轭对偶**。为了解释原因，注意到

$f^{**}(\mathbf{x}) = \max_{\boldsymbol{\lambda}} \mathcal{L}(\mathbf{x}, \boldsymbol{\lambda}) \le f(\mathbf{x})$  (B.80)

由于我们可以针对每个 $\mathbf{x}$ 自由修改 $\boldsymbol{\lambda}$，因此可以在每个 $\mathbf{x}$ 处使下界紧。于是 $f^{**}=f$。这完全刻画了 $f$，因为凸函数的上图是线性下界所定义的半平面的交集，如图 B.7b 所示。

让我们用第 B.4.7.2 节的例子来演示。我们有

$f^{**}(x) = \max_{\lambda} \lambda x - f^{*}(\lambda) = \max_{\lambda} \lambda x + \lambda \log(-\lambda) - \lambda$  (B.81)

定义

$J^{*}(x, \lambda) = \lambda x - f^{*}(\lambda) = \lambda x + \lambda \log(-\lambda) - \lambda$  (B.82)

我们有

$\frac{\partial}{\partial \lambda} J^{*}(x, \lambda) = x + \log(-\lambda) + \lambda \left(\frac{-1}{-\lambda}\right) - 1 = 0$  (B.83)
$x = -\log(-\lambda)$  (B.84)
$\lambda_{x} = -e^{-x}$  (B.85)

代回可得

$f^{**}(x) = J^{*}(x, \lambda_{x}) = (-e^{-x})x + (-e^{-x})(-x) - (-e^{-x})$  (B.86)
$= e^{-x} = f(x)$  (B.87)

## C 线性代数¹

### C.1 引言

线性代数是矩阵和向量的研究。本章总结了整本书中所需用到的关键材料。更多信息可在其他来源中找到，例如 [Str09; Kle13; Mol04; TB97; AxI15; Tho17; Agg20]。

### C.1.1 记号

本节定义一些记号。

### C.1.1.1 向量

向量 $\mathbf{x} \in \mathbb{R}^n$ 是 $n$ 个数的列表，通常写成列向量

$\mathbf{x} = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}.$ (C.1)

全为 1 的向量记为 $\mathbf{1}$。全为 0 的向量记为 $\mathbf{0}$。单位向量 $\mathbf{e}_i$ 是一个全为 0 的向量，除第 $i$ 个分量外，其值为 1：

$\mathbf{e}_i = (0, \dots, 0, 1, 0, \dots, 0)$ (C.2)

这也称为 one-hot 向量。

### C.1.1.2 矩阵

具有 $m$ 行 $n$ 列的矩阵 $\mathbf{A} \in \mathbb{R}^{m \times n}$ 是一个二维数字数组，按如下方式排列：

$\mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}.$ (C.3)
