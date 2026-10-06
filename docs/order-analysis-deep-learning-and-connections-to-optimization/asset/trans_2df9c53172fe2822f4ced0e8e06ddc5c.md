

## 6.6 梯度方法

![](img/e4a2e491dbba0d9f71abf293f149cd5b_119_0.png)

**图 6.9** Rosenbrock 函数 $f: \mathbb{R}^2 \to \mathbb{R}$ 的等高线，对于所有 $(x_1, x_2) \in \mathbb{R}^2$，$f(x_1, x_2) := 100(x_2 - x_1^2)^2 + (1 - x_1)^2$。

(b) 梯度下降法基本上是确定目标函数梯度的零点。$\nabla f(x)=0$ 是全局或局部极小点的必要条件。由于该方法属于下降类（即迭代点的函数值逐步减小，见引 6.1），梯度下降法会运行到起始位置的局部极小点。为了找到（全局）最小值，建议从不同的起点重复执行该过程，并在所有近似解中选择目标值最小的一个。一个例子是 Himmelblau 函数 [60]，$f: \mathbb{R}^2 \to \mathbb{R}$
$f(x_1, x_2) := (x_1^2 + x_2 - 1)^2 + (x_1 + x_2 - 7)^2$，对于所有 $(x_1, x_2) \in \mathbb{R}^2$。

Himmelblau 函数由图 6.10 中的等高线所示。它有四个（全局）最小值（位于 $(3.58, -1.85)$、$(-3.78, -3.28)$、$(-2.81, 3.13)$ 和 $(3, 2)$）、一个局部极大值点（位于 $(-0.27, -0.92)$）以及四个鞍点（位于 $(3.39, 0.07)$、$(-3.07, -0.08)$、$(-0.09, 2.88)$ 和 $(-0.13, -1.95)$），在这些点 $\nabla f$ 也为零。

![](img/e4a2e491dbba0d9f71ab293f14cd5b_120.png)

**图 6.10** Himmelblau 函数 $f: \mathbb{R}^2 \to \mathbb{R}$ 的等高线，$f(x_1, x_2) := (x_1^2 + x_2 - 1)^2 + (x_1 + x_2 - 7)^2$，对于所有 $(x_1, x_2) \in \mathbb{R}^2$。四个黑点表示（全局）最小值的位置。

在算法 6.1 中确定最优步长通常需要巨大的计算量，因此使用了简单的方法。我们现在考虑步长 $\lambda_i$ 可以在某个范围内任意选择的可能性。在适当的假设下，我们可以证明改进后的算法 6.1 的线性收敛性。为此我们需要两个引理：

**引理 6.2**（变分不等式 [42]）*对于某些 $\mu > 0$，令函数 $f : \mathbb{R}^n \to \mathbb{R}$ 是 $\mu$-强凸且可微的。那么有*
$\nabla f(x)^T(y-x) \geq f(x) - f(y) + \frac{\mu}{2} \|x-y\|_2^2$，对于所有 $x, y \in \mathbb{R}^n$。

**证明** 根据命题 1.12，得到
$f(y) \geq f(x) + \nabla f(x)^T(y-x) + \frac{\mu}{2} \|y-x\|_2^2$，对于所有 $x, y \in \mathbb{R}^n$，
这意味着：
$\nabla f(x)^T(x-y) \geq f(x) - f(y) + \frac{\mu}{2}\|x-y\|_2^2$，对于所有 $x, y \in \mathbb{R}^n$。

**引理 6.3（Lipschitz 连续性 [42, 2.28]）** 令函数 $f:\mathbb{R}^n \to \mathbb{R}$ 可微，梯度 $\nabla f$ 是 Lipschitz 连续的，Lipschitz 常数为 $L > 0$，且 $\tilde{x} \in \mathbb{R}^n$ 是 $f$ 的极点。那么有
$\|\nabla f(x)\|^2 \leq 2L(f(x)-f(\tilde{x}))$，对于所有 $x \in \mathbb{R}^n$。

**证明** 根据 Garrigos 和 [42, 2.25]，不等式
$f(y) \leq f(x) + \nabla f(x)^T(y-x) + \frac{L}{2}\|y-x\|_2^2$，对于所有 $x, y \in \mathbb{R}^n$
有效。因此，对于 $y := x-\frac{1}{L}\nabla f(x)$
$f(x-\frac{1}{L}\nabla f(x)) \leq f(x)-\frac{1}{L}\nabla f(x)^T\nabla f(x) + \frac{L}{2}\|-\frac{1}{L}\nabla f(x)\|_2^2 = f(x)-\frac{1}{L}\|\nabla f(x)\|_2^2+\frac{1}{2L}\|\nabla f(x)\|_2^2 = f(x)-\frac{1}{2L}\|\nabla f(x)\|_2^2$，对于所有 $x \in \mathbb{R}^n$。

因此，我们得到
$\|\nabla f(x)\|^2 \leq 2L(f(x)-f(x-\frac{1}{L}\nabla f(x))) \geq 2L(f(x)-f(\tilde{x}))$，对于所有 $x \in \mathbb{R}^n$，这需要证明。

**定理 6.3（梯度方法的收敛性 [42, 3]）** 对于 $\mu > 0$，令函数 $f:\mathbb{R}^n \to \mathbb{R}$ 是 $\mu$-强凸且可微的，梯度 $\nabla f$ 是 Lipschitz 连续的，常数为 $L$，且 $\tilde{x} \in \mathbb{R}^n$ 是 $f$ 的极点。如果算法 6.1 任意选择 $\lambda_i \in (0, \lambda_{max}]$（其中 $0 < \lambda_i \leq \min\{\frac{1}{L}, \frac{1}{\mu}\}$，而不是算法 6.1 第 7 行的最优步长）生成序列 $(x^i)_{i\in\mathbb{N}}$，则
$\|x^{i+1}-\tilde{x}\|_2^2 \leq (1-\lambda_i\mu)\|x^i-\tilde{x}\|_2^2$，对于所有 $i \in \mathbb{N}$
且 $\|x^t-\tilde{x}\|_2^2 \leq (1-\lambda_i\mu)^t \|x^0-\tilde{x}\|_2^2$，对于所有 $t \in \mathbb{N}$，其中 $1-\lambda_i\mu \in (0, 1)$。

**证明** 根据引 1.1，函数 $f$ 有唯一的极点 $\tilde{x}$，因为 $f$ 是 $\mu$-强凸且连续的。对于任意 $i \in \mathbb{N}\cup\{0\}$，我们得到
$\|x^{t+1}-\tilde{x}\|_2^2 = \|x^t-\tilde{x}-\lambda_i\nabla f(x^t)\|_2^2$
$= (x^t-\tilde{x}-\lambda_i\nabla f(x^t))^T(x^t-\tilde{x}) + \lambda_i^2\|\nabla f(x^t)\|_2^2$
$= \|x^t-\tilde{x}\|_2^2 - 2\lambda_i\nabla f(x^t)^T(x^t-\tilde{x}) + \lambda_i^2\|\nabla f(x^t)\|_2^2$
$\geq \|x^t-\tilde{x}\|_2^2 - 2\lambda_i(f(x^t)-f(\tilde{x}) + \frac{\mu}{2}\|x^t-\tilde{x}\|_2^2) + \lambda_i^2\|\nabla f(x^t)\|_2^2$（由引 6.2）
$\leq (1-\lambda_i\mu)\|x^t-\tilde{x}\|_2^2 - 2\lambda_i(f(x^t)-f(\tilde{x})) + \lambda_i^2\|\nabla f(x^t)\|_2^2$（由引 6.3）
$\leq (1-\lambda_i\mu)\|x^t-\tilde{x}\|_2^2 - 2\lambda_i \frac{(1-\lambda_i L)}{L} (f(x^t)-f(\tilde{x}))$
$\geq 0$（因为 $\lambda_i < \frac{1}{L}$）
$\leq (1-\lambda_i\mu)\|x^t-\tilde{x}\|_2^2$，这证明了不等式 (6.7)。不等式 (6.8) 是不等式 (6.7) 的直接结果。结合 $\lambda > 0$ 和 $\mu < \frac{1}{L}$，结论 (6.9) 立即成立。

**推论 6.1（梯度方法的线性收敛性）** 满足定理假设。那么序列 $(x^t)^{t \in \mathbb{N}}$ 收敛于 $f$ 的唯一极点 $\tilde{x}$。

**证明** 从不等式 (6.8) 和条件 (6.9) 显看出，序列 $(x^t)^{t \in \mathbb{N}}$ 收敛于 $f$ 的唯一极点 $\tilde{x}$。不等式 (6.7) 结合条件 (6.9) 意味着序列 $(x^t)^{t \in \mathbb{N}}$ 是线性收敛的。

现在，我们关注概念算法 6.1 更实用的变体。在实践中，使用算法 6.1 第 6 和 7 行的最优步长意义不大。因此，使用了近似方法，例如非线性优化中 Armijo、Goldstein 或 Powell 给出的方法（见 [46, 第 2 章）。但在深度学习中，我们需要以低计算开销为特征的变体。为此，Barzilai 和 Borwein [12] 的近似被证明是有效的。该变体在以下程序中：

```
**算法 6.2** (梯度下降法—实用形式)
1 输入: $f: \mathbb{R}^n \to \mathbb{R}$，起始向量 $x^0 \in \mathbb{R}^n$，停止准则 $\epsilon > 0$。
2 $i := 0$ % 初始化
3 while $\|\nabla f(x^i)\|_2 > \epsilon$ do % 迭代
4 $d^i := -\nabla f(x^i)$
5 if $i = 0$ then
6 $\lambda_0 := 1$
7 else
8 $\lambda_i := \frac{(x^i - x^{i-1})^T(x^i - x^{i-1})}{(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))}$ % Barzilai-Borwein 步长
9 end if
10 $x^{i+1} := x^i + \lambda_i d^i$
11 $i := i + 1$
12 end while
13 输出: $x^1, x^2, \dots$
```

