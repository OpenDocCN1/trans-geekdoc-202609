
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_321_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_321_1.png)

图 10.7：二维输入的三分类逻辑回归示例。(a) 原始特征。(b) 二次特征。由 logreg_multiclass_demo.py 生成。

一种创建非线性边界的方法。例如，假设我们用以下方式替换 $\mathbf{x} = (x_1, x_2)$ by

$$\phi(\mathbf{x}) = [1, x_1, x_2, x_1^2, x_2^2, x_1 x_2] \quad (10.54)$$

这使我们能够创建二次决策边界，如图 10.7(b) 所示。

## 10.3.2 最大似然估计

在本节中，我们讨论如何通过最小化负对数似然（NLL）来计算最大似然估计（MLE）。

### 10.3.2.1 目标

NLL 由下式给出

$$\mathrm{NLL}(\boldsymbol{\theta}) = -\log \prod_{n=1}^{N} \prod_{c=1}^{C} \mu_{nc}^{y_{nc}} = -\sum_{n=1}^{N} \sum_{c=1}^{C} y_{nc} \log \mu_{nc} = \sum_{n=1}^{N} \mathbb{H}(\mathbf{y}_n, \boldsymbol{\mu}_n) \quad (10.55)$$

其中 $\mu_{nc} = p(y_n = c|\mathbf{x}_n, \boldsymbol{\theta}) = \mathcal{S}(f(\mathbf{x}_n; \boldsymbol{\theta}))_c$, $y_{nc} = \mathbb{I}(y_n = c)$ 是 $y_n$ 的独热编码，且 $\mathbb{H}(\mathbf{y}_n, \boldsymbol{\mu}_n)$ 是交叉熵：

$$\mathbb{H}(\mathbf{p}, \mathbf{q}) = - \sum_{c=1}^{C} p_c \log q_c \quad (10.56)$$

### 10.3.2.2 优化目标

要找到最优解，我们需要求解 $\nabla_{\mathbf{w}} \mathrm{NLL}(\mathbf{w}) = \mathbf{0}$，其中 $\mathbf{w}$ 是权重矩阵 $\mathbf{W}$ 的向量化版本，且为书写简便我们忽略了偏置项。我们可以使用任何基于梯度的优化器找到这样的驻点；下面给出一些示例。但首先我们推导梯度和 Hessian，然后证明目标是凸的。

### 10.3.2.3 推导梯度

要推导 NLL 的梯度，我们需要使用 softmax 函数的雅可比矩阵，如下所示（参见练习 10.1 的证明）：

$$\frac{\partial \mu_c}{\partial a_j} = \mu_c(\delta_{cj} - \mu_j) \quad (10.57)$$

其中 $\delta_{cj} = \mathbb{I}(c = j)$。例如，如果我们有 3 个类别，雅可比矩阵由下式给出

$$\left[\frac{\partial \mu_c}{\partial a_j}\right]_{cj} = \begin{pmatrix} \mu_1(1-\mu_1) & -\mu_1\mu_2 & -\mu_1\mu_3 \\ -\mu_2\mu_1 & \mu_2(1-\mu_2) & -\mu_2\mu_3 \\ -\mu_3\mu_1 & -\mu_3\mu_2 & \mu_3(1-\mu_3) \end{pmatrix} \quad (10.58)$$

在矩阵形式中，这可以写成

$$\frac{\partial \boldsymbol{\mu}}{\partial \mathbf{a}} = (\boldsymbol{\mu}\mathbf{1}^\top) \odot (\mathbf{I} - \mathbf{1}\boldsymbol{\mu}^\top) \quad (10.59)$$

其中 $\odot$ 是逐元素乘积，$\boldsymbol{\mu}\mathbf{1}^\top$ 将 $\boldsymbol{\mu}$ 跨各列复制，$\mathbf{1}\boldsymbol{\mu}^\top$ 将 $\boldsymbol{\mu}$ 跨各行复制。

我们现在可以使用链式法则推导 NLL 的（批量）梯度，如下所示：

$$\nabla_{\mathbf{w}_j}\text{NLL} = \sum_n \sum_c \frac{\partial \text{NLL}}{\partial \mu_{nc}} \frac{\partial \mu_{nc}}{\partial a_{nj}} \frac{\partial a_{nj}}{\partial \mathbf{w}_j} \quad (10.60)$$

$$= -\sum_n \sum_c \frac{y_{nc}}{\mu_{nc}} \mu_{nc}(\delta_{jc} - \mu_{nj})\mathbf{x}_n \quad (10.61)$$

$$= \sum_n \sum_c y_{nc}(\mu_{nj} - \delta_{jc})\mathbf{x}_n \quad (10.62)$$

$$= \sum_n \left(\sum_c y_{nc}\right)\mu_{nj}\mathbf{x}_n - \sum_n y_{nj}\mathbf{x}_n \quad (10.63)$$

$$= \sum_n (\mu_{nj} - y_{nj})\mathbf{x}_n \quad (10.64)$$

在矩阵记号中，我们有

$$\mathbf{g}(\mathbf{W}) = \sum_{n=1}^{N} \mathbf{x}_n (\boldsymbol{\mu}_n - \mathbf{y}_n)^\top \quad (10.65)$$

这与二元逻辑回归情形的形式相同，即误差项乘以输入 $\mathbf{x}_n$，对 $N$ 求和。

### 10.3.2.4 推导 Hessian

练习 10.1 要求你证明多项逻辑回归的 NLL 的 Hessian 由下式给出

$$\mathbf{H}(\mathbf{W}) = \sum_{n=1}^{N} \bigl(\text{diag}(\boldsymbol{\mu}_n) - \boldsymbol{\mu}_n \boldsymbol{\mu}_n^\top\bigr) \otimes (\mathbf{x}_n \mathbf{x}_n^\top) \quad (10.66)$$

其中 $\mathbf{A} \otimes \mathbf{B}$ 是 Kronecker 积（Sec. C.2.5）。换句话说，块 $c, c'$ 子矩阵由下式给出

$$\mathbf{H}_{c,c'}(\mathbf{W}) = \sum_{n} \mu_{nc}(\delta_{c,c'} - \mu_{n,c'})\mathbf{x}_{n}\mathbf{x}_{n}^{\top}\quad (10.67)$$

例如，如果我们有 3 个特征和 2 个类别，则变为

$$\mathbf{H}(\mathbf{W}) = \sum_{n} \begin{pmatrix} \mu_{n1} - \mu_{n1}^2 & -\mu_{n1}\mu_{n2} \\ -\mu_{n1}\mu_{n2} & \mu_{n2} - \mu_{n2}^2 \end{pmatrix} \otimes \begin{pmatrix} x_{n1}x_{n1} & x_{n1}x_{n2} & x_{n1}x_{n3} \\ x_{n2}x_{n1} & x_{n2}x_{n2} & x_{n2}x_{n3} \\ x_{n3}x_{n1} & x_{n3}x_{n2} & x_{n3}x_{n3} \end{pmatrix}\quad (10.68)$$

$$= \sum_{n} \begin{pmatrix} (\mu_{n1} - \mu_{n1}^2)\mathbf{X}_{n} & -\mu_{n1}\mu_{n2}\mathbf{X}_{n} \\ -\mu_{n1}\mu_{n2}\mathbf{X}_{n} & (\mu_{n2} - \mu_{n2}^2)\mathbf{X}_{n} \end{pmatrix}\quad (10.69)$$

其中 $\mathbf{X}_{n} = \mathbf{x}_{n}\mathbf{x}_{n}^{\top}$。练习 10.1 还要求你证明这是一个正定矩阵，因此目标是凸的。

## 10.3.3 基于梯度的优化

使用第 10.3.2.3 节中的梯度推导 SGD 算法是直接的。类似地，我们可以使用第 10.3.2.4 节中的 Hessian 推导二阶优化方法。然而，计算 Hessian 可能很昂贵，因此通常使用拟牛顿方法对其进行近似，例如有限内存 BFGS。（BFGS 代表 Broyden, Fletcher, Goldfarb 和 Shanno。）参见第 5.3.2 节了解详情。另一种与 IRLS 类似的方法在第 10.3.4 节中描述。

所有这些方法都依赖于计算对数似然的梯度，而这又需要计算归一化概率，该概率可从 logits 向量 $\mathbf{a} = \mathbf{W}\mathbf{x}$ 使用下式计算

$$p(y = c|\mathbf{x}) = \exp(a_{c} - \mathrm{lse}(\mathbf{a}))\quad (10.70)$$

其中 lse 是第 3.2.4 节中定义的 log-sum-exp 函数。因此，许多软件库定义了接受未归一化 logits 作为输入的交叉熵损失版本。

## 10.3.4 边界优化

在本节中，我们考虑一种使用我们将在第 5.7 节中描述的称为边界优化的一类算法来拟合逻辑回归的方法。基本思想是迭代地构造你要最大化的函数的下界，然后更新该界，使其“推高”真实函数。优化边界通常比直接更新函数更容易。

如果 $L(\boldsymbol{\theta})$ 是一个我们想要最大化的凹函数，那么获得有效下界的一种方法是使用其 Hessian 的界，即找到一个负定矩阵 $\mathbf{B}$ 使得 $\mathbf{H}(\boldsymbol{\theta}) \succeq \mathbf{B}$。在这种情况下，可以证明

$$L(\boldsymbol{\theta}) \ge L(\boldsymbol{\theta}^{t}) + (\boldsymbol{\theta} - \boldsymbol{\theta}^{t})^{\top} \mathbf{g}(\boldsymbol{\theta}^{t}) + \frac{1}{2}(\boldsymbol{\theta} - \boldsymbol{\theta}^{t})^{\top} \mathbf{B}(\boldsymbol{\theta} - \boldsymbol{\theta}^{t})\quad (10.71)$$

其中 $\mathbf{g}(\boldsymbol{\theta}^{t}) = \nabla L(\boldsymbol{\theta}^{t})$。将 $Q(\boldsymbol{\theta}, \boldsymbol{\theta}^{t})$ 定义为式 (10.71) 的右端，则更新变为

$$\boldsymbol{\theta}^{t+1} = \boldsymbol{\theta}^{t} - \mathbf{B}^{-1} \mathbf{g}(\boldsymbol{\theta}^{t})\quad (10.72)$$

这与牛顿更新类似，只是我们使用的是固定矩阵 $\mathbf{B}$，而不是每次迭代都变化的 $\mathbf{H}(\boldsymbol{\theta}^t)$。这可以在较低的计算成本下提供二阶方法的一些优点。

现在让我们按照 [Kri+05] 将其应用于逻辑回归。令 $\boldsymbol{\mu}_n(\mathbf{w}) = [p(y_n = 1 \mid \mathbf{x}_n, \mathbf{w}), \ldots, p(y_n = C \mid \mathbf{x}_n, \mathbf{w})]$ 且 $\mathbf{y}_n = [\mathbb{I}(y_n = 1), \ldots, \mathbb{I}(y_n = C)]$。我们想要 *最大化* 对数似然，如下所示：

$$L(\mathbf{w}) = \sum_{n=1}^{N} \left[\sum_{c=1}^{C} y_{nc}\mathbf{w}_c^\top \mathbf{x}_n - \log \sum_{c=1}^{C} \exp(\mathbf{w}_c^\top \mathbf{x}_n)\right] \quad (10.73)$$

梯度由下式给出（参见第 10.3.2.3 节了解推导详情）：

$$\mathbf{g}(\mathbf{w}) = \sum_{n=1}^{N}(\mathbf{y}_n - \boldsymbol{\mu}_n(\mathbf{w})) \otimes \mathbf{x}_n \quad (10.74)$$

其中 $\otimes$ 表示 kronecker 积（在这种情况下，只是两个向量的外积）。Hessian 由下式给出（参见第 10.3.2.4 节了解推导详情）：

$$\mathbf{H}(\mathbf{w}) = -\sum_{n=1}^{N}\left(\operatorname{diag}(\boldsymbol{\mu}_n(\mathbf{w})) - \boldsymbol{\mu}_n(\mathbf{w})\boldsymbol{\mu}_n(\mathbf{w})^\top\right) \otimes (\mathbf{x}_n\mathbf{x}_n^\top) \quad (10.75)$$

我们可以构造 Hessian 的下界，如 [Boh92] 中所示：

$$\mathbf{H}(\mathbf{w}) \succeq -\frac{1}{2}\left[\mathbf{I} - \frac{1\,1^\top}{C}\right] \otimes \left(\sum_{n=1}^{N}\mathbf{x}_n\mathbf{x}_n^\top\right) \triangleq \mathbf{B} \quad (10.76)$$

其中 $\mathbf{I}$ 是 $C$ 维单位矩阵，$\mathbf{1}$ 是全为 1 的 $C$ 维向量。[^1] 在二元情况下，这变为

$$\mathbf{H}(\mathbf{w}) \succeq -\frac{1}{2}\left(1-\frac{1}{2}\right)\left(\sum_{n=1}^{N}\mathbf{x}_n\mathbf{x}_n^\top\right) = -\frac{1}{4}\mathbf{X}^\top\mathbf{X} \quad (10.77)$$

这是因为 $\mu_n \leq 0.5$，所以 $-(\mu_n - \mu_n^2) \geq -0.25$。

我们可以使用此下界构造 MM 算法来找到 MLE。更新变为

$$\mathbf{w}^{t+1} = \mathbf{w}^{t} - \mathbf{B}^{-1}\mathbf{g}(\mathbf{w}^{t}) \quad (10.78)$$

此迭代比 IRLS（第 10.2.6 节）更快，因为我们可以在与 $N$ 无关的时间内预先计算 $\mathbf{B}^{-1}$，而不是在每次迭代中反转 Hessian。例如，让我们考虑二元情况，则 $\mathbf{g}^{t} = \nabla L(\mathbf{w}^{t}) = \mathbf{X}^\top(\mathbf{y} - \boldsymbol{\mu}^{t})$，其中 $\boldsymbol{\mu}^{t} = [p_n(\mathbf{w}^{t}), (1-p_n(\mathbf{w}^{t}))]_{n=1}^{N}$。更新变为

$$\mathbf{w}^{t+1} = \mathbf{w}^{t} - 4(\mathbf{X}^\top\mathbf{X})^{-1}\mathbf{g}^{t} \quad (10.79)$$

将其与式 (10.37) 进行比较，其形式如下：

$$\mathbf{w}^{t+1} = \mathbf{w}^{t} - \mathbf{H}^{-1}\mathbf{g}(\mathbf{w}^{t}) = \mathbf{w}^{t} - (\mathbf{X}^\top\mathbf{S}^{t}\mathbf{X})^{-1}\mathbf{g}^{t} \quad (10.80)$$

其中 $\mathbf{S}^{t} = \operatorname{diag}(\boldsymbol{\mu}^{t} \odot (1-\boldsymbol{\mu}^{t}))$。我们看到式 (10.79) 计算更快，因为我们可以预先计算常数矩阵 $(\mathbf{X}^\top\mathbf{X})^{-1}$。

[^1]: 如果我们强制 $w_C = 0$，我们可以使用 $C-1$ 维来表示这些向量 / 矩阵。
