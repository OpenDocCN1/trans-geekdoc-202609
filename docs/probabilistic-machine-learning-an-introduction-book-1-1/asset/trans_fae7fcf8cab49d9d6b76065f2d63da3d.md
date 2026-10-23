
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_145_0.png)

图 5.7：Nesterov 更新的示意图。改编自 [Gér19] 的图 11.6。

为了更深入地理解该方法，假设梯度在每次迭代中都是常数，记为 **g**。由于我们将动量初始化为零，**m**₀ = **0**，各步的动量如下：

**m**₁ = −η**g**  (5.23)
**m**₂ = β**m**₁ − η**g** = −β η**g** − η**g** = −(β + 1)η**g**  (5.24)
**m**₃ = β**m**₂ − η**g** = −β² η**g** − β η**g** − η**g** = −(β² + β¹ + β⁰)η**g**  (5.25)

依此类推。缩放因子是一个等比数列，其无穷和为

1 + β + β² + ⋯ = Σᵢ₌₀^∞ βⁱ = 1 / (1 − β)  (5.26)

因此在极限情况下，我们将步长乘以 1/(1 − β)。例如，若设 β = 0.9，则最终 η 会增大 10 倍。这有助于防止 GD 卡在平坦的“山谷底部”。然而，它也可能导致 overshooting，如我们在第 5.2.4.2 节中讨论的。

## 5.2.4.2 Nesterov momentum

标准动量方法的一个问题是，在山谷底部可能减速不足，导致振荡。[Nes04] 中的 Nesterov 加速梯度方法则对梯度下降进行了修改，加入了外推步骤，如下所示：

˜θₜ₊₁ = θₜ + βₜ(θₜ − θₜ₋₁)  (5.27)
θₜ₊₁ = ˜θₜ₊₁ − ηₜ ∇ℒ(˜θₜ₊₁)  (5.28)

这本质上是一种一步“向前看”的形式，可以减少振荡量，如图 5.7 所示。

Nesterov 加速梯度也可以改写为与标准动量相同的格式。在这种情况下，动量项使用预测的新位置处的梯度进行更新，

$$\mathbf{m}_{t+1}= \beta\mathbf{m}_t - \eta_t \nabla\mathcal{L}(\boldsymbol{\theta}_t + \beta\mathbf{m}_t)\tag{5.29}$$
$$\boldsymbol{\theta}_{t+1}= \boldsymbol{\theta}_t + \mathbf{m}_{t+1}\tag{5.30}$$

这解释了为什么 Nesterov 加速梯度方法有时被称为 Nesterov momentum。它还显示了该方法为何可能比标准动量更快：动量向量已经大致指向正确方向，因此在新位置 $\boldsymbol{\theta}_t + \beta\mathbf{m}_t$ 而非当前位置 $\boldsymbol{\theta}_t$ 处测量梯度会更准确。

当 $\beta$ 和 $\eta_t$ 选择合适时，Nesterov 加速梯度方法已被证明比凸函数上的最速下降更快。它被称为“加速”，是因为这种改进的收敛速率，对于仅使用一阶信息的梯度方法而言是最佳的，前提是目标函数为凸且具有 Lipschitz 连续梯度。然而在实践中，使用 Nesterov momentum 可能比最速下降更慢，并且如果 $\beta$ 或 $\eta_t$ 指定不当，甚至会变得不稳定。

## 5.3 Second-order methods

仅使用梯度的优化算法称为 **first-order** 方法。它们的优点是梯度计算和存储成本低，但它们不建模空间的曲率，因此收敛可能很慢，如我们在图 5.5 中所见。**Second-order** 优化方法以各种方式结合曲率（如通过 Hessian），可能带来更快的收敛。我们将在下面讨论其中一些方法。

### 5.3.1 Newton’s method

经典的二阶方法是 **Newton’s method**。这由以下形式的更新组成

$$\boldsymbol{\theta}_{t+1}= \boldsymbol{\theta}_t - \eta_t\mathbf{H}_t^{-1}\mathbf{g}_t\tag{5.31}$$

其中
$$\mathbf{H}_t \triangleq \nabla^2\mathcal{L}(\boldsymbol{\theta})|_{\boldsymbol{\theta}_t}= \nabla^2\mathcal{L}(\boldsymbol{\theta}_t)= \mathbf{H}(\boldsymbol{\theta}_t)\tag{5.32}$$

假定为正定以确保更新是良定义的。Newton 方法的伪代码见算法 1。为什么它比梯度下降更快的原因在于矩阵逆 $\mathbf{H}^{-1}$ “抵消”了局部曲率中的任何偏斜，将类似图 5.5a 的拓扑转换为类似图 5.5b 的拓扑。

该算法可如下推导。考虑对 $\mathcal{L}(\boldsymbol{\theta})$ 在 $\boldsymbol{\theta}_t$ 附近做二阶泰勒级数近似：
$$\mathcal{L}_{\text{quad}}(\boldsymbol{\theta}) = \mathcal{L}(\boldsymbol{\theta}_t) + \mathbf{g}_t^{\top}(\boldsymbol{\theta} - \boldsymbol{\theta}_t) + \frac{1}{2}(\boldsymbol{\theta} - \boldsymbol{\theta}_t)^{\top}\mathbf{H}_t(\boldsymbol{\theta} - \boldsymbol{\theta}_t)\tag{5.33}$$

$\mathcal{L}_{\text{quad}}$ 的最小值在
$$\boldsymbol{\theta}= \boldsymbol{\theta}_t - \mathbf{H}_t^{-1}\mathbf{g}_t\tag{5.34}$$

#### Algorithm 1: Newton's method for minimizing a function

- 1 初始化 $\boldsymbol{\theta}_0$；
- 2 对于 $t = 1,2,...$ 直到收敛 do
- 3 计算 $\mathbf{g}_t = \nabla \mathcal{L}(\boldsymbol{\theta}_t)$；
- 4 计算 $\mathbf{H}_t = \nabla^2 \mathcal{L}(\boldsymbol{\theta}_t)$；
- 5 求解 $\mathbf{H}_t \mathbf{d}_t = -\mathbf{g}_t$ 得到 $\mathbf{d}_t$；
- 6 使用线搜索沿 $\mathbf{d}_t$ 找到步长 $\eta_t$；
- 7 $\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t + \eta_t \mathbf{d}_t$；

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_147_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_147_1.png)

图 5.8：最小化一维函数时 Newton 方法的示意图。(a) 实曲线是函数 $\mathcal{L}(x)$。点线 $\mathcal{L}_{quad}(\theta)$ 是其在 $\theta_t$ 处的二阶近似。Newton 步 $d_t$ 是必须加到 $\theta_t$ 上以得到 $\mathcal{L}_{quad}(\theta)$ 最小值的量。改编自 [Van06] 的图 13.4。由 newtonsMethodMinQuad.m 生成。(b) Newton 方法应用于非凸函数的示意图。我们在当前点 $\theta_t$ 周围拟合一个二次函数并移动到其驻点，$\theta_{t+1} = \theta_t + d_t$。不幸的是，这会使我们接近 f 的局部最大值，而不是最小值。这意味着我们需要谨慎对待二次近似的范围。改编自 [Van06] 的图 13.11。由 newtonsMethodNonConvex.m 生成。

如果二次近似是好的，我们应该选择 $\mathbf{d}_t = -\mathbf{H}_t^{-1}\mathbf{g}_t$ 作为下降方向。参见图 5.8(a) 的示意图。请注意，在“纯” Newton 方法中，我们使用 $\eta_t = 1$ 作为步长。然而，我们也可以使用线搜索找到最佳步长；这往往更稳健，因为使用 $\eta_t = 1$ 可能并不总是全局收敛。

如果我们将该方法应用于线性回归，我们一步即可达到最优，因为（如我们在第 11.2.2.1 节所示）我们有 $\mathbf{H} = \mathbf{X}^\top \mathbf{X}$ 且 $\mathbf{g} = \mathbf{X}^\top \mathbf{X}\mathbf{w} - \mathbf{X}^\top \mathbf{y}$，因此 Newton 更新变为

\mathbf{w}_1 = \mathbf{w}_0 - \mathbf{H}^{-1}\mathbf{g} = \mathbf{w}_0 - (\mathbf{X}^\top\mathbf{X})^{-1}(\mathbf{X}^\top\mathbf{X}\mathbf{w}_0 - \mathbf{X}^\top\mathbf{y}) = \mathbf{w}_0 - \mathbf{w}_0 + (\mathbf{X}^\top\mathbf{X})^{-1}\mathbf{X}^\top\mathbf{y} \tag{5.35}

这就是 OLS 估计。然而，当我们将该方法应用于逻辑回归时，可能需要多次迭代才能收敛到全局最优，如我们在第 10.2.6 节中讨论的。

### 5.3.2 BFGS and other quasi-Newton methods

拟牛顿方法，有时称为变度量方法，通过利用每次迭代的梯度向量信息逐步构建 Hessian 的近似。

最常见的方法称为 **BFGS**（以其同时发明者 Broyden、Fletcher、Goldfarb 和 Shanno 命名），它按如下方式更新 Hessian 的近似 **B**_t ≈ **H**_t：

**B**_{t+1} = **B**_t + ( **y**_t **y**_t^⊤ ) / ( **y**_t^⊤ **s**_t ) - ( **B**_t **s**_t )( **B**_t **s**_t )^⊤ / ( **s**_t^⊤ **B**_t **s**_t )  (5.36)

**s**_t = **θ**_t - **θ**_{t-1}  (5.37)

**y**_t = **g**_t - **g**_{t-1}  (5.38)

这是对矩阵的秩二更新。如果 **B**_0 为正定，且步长 η 通过线搜索选择，满足 Eq. (5.18) 中的 Armijo 条件以及以下曲率条件

∇ℒ(**θ**_t + η**d**_t) ≥ c_2 η **d**_t^⊤ ∇ℒ(**θ**_t)  (5.39)

则 **B**_{t+1} 将保持正定。常数 c_2 在 (c,1) 中选择，其中 c 是 Eq. (5.18) 中的可调参数。这两个步长条件合称为 **Wolfe conditions**。我们通常从对角近似开始，**B**_0 = **I**。因此 BFGS 可以被视为 Hessian 的“对角加低秩”近似。

另外，BFGS 可以迭代地更新逆 Hessian 的近似 **C**_t ≈ **H**_t^{-1}，如下所示：

**C**_{t+1} = ( **I** - **s**_t **y**_t^⊤ / ( **y**_t^⊤ **s**_t ) ) **C**_t ( **I** - **y**_t **s**_t^⊤ / ( **y**_t^⊤ **s**_t ) ) + **s**_t **s**_t^⊤ / ( **y**_t^⊤ **s**_t )  (5.40)

由于存储 Hessian 近似仍需要 O(D²) 空间，对于非常大的问题，可以使用 **limited memory BFGS**，或 **L-BFGS**，其中我们通过仅使用最近的 M 个 (**s**_t, **y**_t) 对而忽略旧信息来控制近似的秩。不是显式存储 **B**_t，我们只需将这些向量存储在内存中，然后通过与存储的 **s**_t 和 **y**_t 向量进行一系列内积来近似 **H**_t^{-1} **g**_t。因此存储需求为 O(M D)。通常选择 M 在 5-20 之间足以获得良好的性能 [NW06, p177]。

请注意，sklearn 使用 LBFGS 作为逻辑回归的默认求解器。

### 5.3.3 Trust region methods

如果目标函数是非凸的，则 Hessian **H**_t 可能不是正定的，因此 **d**_t = -**H**_t^{-1} **g**_t 可能不是下降方向。这在图 5.8(b) 的一维情况下有所说明，其中显示 Newton 方法可能最终落入局部最大值而非局部最小值。

一般来说，只要 Newton 方法所做的二次近似失效，我们就会遇到麻烦。然而，通常在当前迭代点周围存在一个局部区域，在该区域内我们可以安全地用二次函数近似目标。让我们称该区域为 ℛ_t，并称 M(δ) 为目标的模型（或近似），其中 δ = θ - θ_t。然后在每一步我们可以求解

**δ*** = argmin_{δ ∈ ℛ_t} M_t(δ)  (5.41)

这称为 **trust-region optimization**。（这可以看作是线搜索的“相反”，因为我们先选择想要行进的距离，由 ℛ_t 决定，然后求解最优方向，而不是先选择方向再求解最优距离。）
