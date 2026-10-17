
maximize with respect to `λ` `Σ_{n=1}^N λ_n y_n - 1/(4C) Σ_{n=1}^N Σ_{m=1}^N λ_n λ_m κ(x_n, x_m) - 1/4 Σ_{n=1}^N λ_n²`,

![Equation](img/si311.png)(11.55)

其中我们根据核技巧，已用核运算替换了 `x_n^T x_m`。通过简单的代数运算即可得到（参见 [98] 和问题 11.9）

```
λ = 2C (K + C I)^(-1) y,
```

![Equation](img/si313.png)(11.56)

将其与公式 (11.53) 结合并涉及核技巧，我们得到核岭回归的预测规则，即

```
ŷ(x) = y^T (K + C I)^(-1) κ(x),
```

![Equation](img/si314.png)(11.57)

这与公式 (11.27) 相同；然而，通过这条路径不需要假设 `K` 的可逆性。求解核岭回归的高效方案已在文献 [117,118] 中提出。

### 目标函数与损失函数

$$J(f) = \sum_{n = 1}^{N}\mathcal{L}\left( y_{n},f(\mathbf{x}_{n}) \right)$$

![Equation](img/si315.png)

其中

$$y_{n} = \begin{cases} + 1, & \quad\text{if}\quad\mathbf{x}_{n} \in \omega_{1}, \\ - 1, & \quad\text{if}\quad\mathbf{x}_{n} \in \omega_{2}. \end{cases}$$

![Equation](img/si316.png)

对于二分类任务，首先想到的损失函数是

$$\mathcal{L}\left( y,f(\mathbf{x}) \right) = \begin{cases} 1, & \quad\text{if}\quad yf(\mathbf{x}) \leqslant 0, \\ 0, & \quad\text{otherwise}, \end{cases}$$

![Equation](img/si317.png)(11.58)

这也被称为 **(0, 1)-损失函数**。然而，这是一个不连续函数，其优化是一项艰巨的任务。为此，采用了许多替代损失函数来近似 **(0, 1)-损失函数**。回顾一下，平方误差损失也可以使用，但正如第 3 章和第 7 章已经指出的那样，这不太适合分类任务，且与 **(0, 1)-损失函数** 差异很大。在本节中，我们将关注所谓的 *hinge*（合页）损失函数，其定义如下（第 8 章）：

$$\mathcal{L}_{\rho}(y,f(\mathbf{x})) = \max \{0,\rho - y f(\mathbf{x})\}.$$

![Equation](img/si319.png)(11.59)

换句话说，如果真实标签 (`y`) 与判别函数值 (`f(\mathbf{x})`) 预测值的乘积为正且大于阈值/边界值 `\rho \ge 0`（用户定义），则损失为零。否则，损失呈线性增长。如果 `y f(\mathbf{x})` 无法达到至少 `\rho` 的值，我们称犯了一个边界错误。*Hinge* 损失函数如 图 11.13 所示，图中还展示了 **(0, 1)-损失函数** 和平方误差损失函数。

![图 11.13 (0,1)-损失（红色虚线）、合页损失（红色实线）和平方误差（黑色虚线）函数，经过调整均通过 (0,1) 点以便比较。对于合页损失，选取了值 `ρ` = 1。此外，对于合页损失和 (0,1)-损失函数 `τ` = `yf(x)`，而对于平方误差函数，`τ` = `y` − `f(x)`。](img/gr013.jpg)

**图 11.13** (0,1)-损失（红色虚线）、合页损失（红色实线）和平方误差（黑色虚线）函数，经过调整均通过 (0,1) 点以便比较。对于合页损失，选取了值 `ρ` = 1。此外，对于合页损失和 (0,1)-损失函数 `τ` = `yf(x)`，而对于平方误差函数，`τ` = `y` − `f(x)`。

我们将局限于位于某个 RKHS 中的线性判别函数，其形式为

```
f(x) = θ₀ + ⟨θ, ϕ(x)⟩
```

根据定义，

```
ϕ(x) := κ(⋅, x)
```

为特征映射。然而，基于第 11.8.1 节中讨论的相同原因，我们将在输入空间 `ℝˡ` 中将该任务表述为线性任务，并在最后阶段使用核技巧将核信息“植入”进去。

设计线性分类器的目标现在等价于最小化代价

```
J(θ, θ₀) = ½‖θ‖² + C ∑ₙ₌₁ᴺ Lᵨ(yₙ, θᵀxₙ + θ₀)
```

(11.60)

或者，采用松弛变量，并遵循第 11.8.1 节中类似的推理，最小化公式 (11.60) 等价于

```
关于 θ, θ₀, ξ 最小化  J(θ, ξ) = ½‖θ‖² + C ∑ₙ₌₁ᴺ ξₙ
```

(11.61)

约束条件为 `yₙ(θᵀxₙ + θ₀) ≥ ρ − ξₙ`

(11.62)

`ξ[n] \ge 0, n = 1, 2, \dots, N`.

![Equation](img/si328.png)(11.63)

从现在开始，我们将采用 `\rho = 1` 的值，这不失一般性。如果 `yₙ(θᵀxₙ + θ₀) < 1`，则会犯边界错误，这对应于 `ξ[n] > 0`，否则 (11.62) 中的不等式不成立。为了使后者在边界错误的情况下成立，必须有 `ξ[n] > 0`，这会对公式 (11.61) 中的代价产生贡献。另一方面，如果 `ξ[n] = 0`，则 `yₙ(θᵀxₙ + θ₀) \ge 1`，且在代价函数中没有贡献。请注意，`yₙ(θᵀxₙ + θ₀)` 的值相对于边界 `\rho = 1` 越小，为满足不等式，相应的 `ξ[n]` 就应该越大，因此公式 (11.61) 中的代价贡献也就越大。因此，优化任务的目标是尽可能多地将 `ξ[n]` 驱动为零。(11.61)–(11.63) 中的优化任务具有有趣且重要的几何解释。

#### 11.10.1 线性可分类别：最大边界分类器

假设类别是线性可分的，存在无限多个线性分类器能够精确解决分类任务，在训练集上不犯错误（参见 图 11.14）。很容易看出，而且马上就会变得显而易见，从这解决任务的无限多个超平面中，我们总能识别出一个子集，使得

`yₙ(θᵀxₙ + θ₀) \ge 1, n = 1, 2, \dots, N`,

![Equation](img/si334.png)

这保证了在 (11.61)–(11.63) 中 `ξ[n] = 0, n = 1, 2, \dots, N`。因此，对于线性可分类别，前述优化任务等价于

##### 优化问题

$$

\text{minimize with respect to } \mathbf{\theta} \quad \frac{1}{2}\|\mathbf{\theta}\|²,

$$

subject to

$$

y_n(\mathbf{\theta}^T\mathbf{x}_n + \theta_0) \ge 1, \quad n = 1, 2, \dots, N.

$$

换句话说，从这无限多个能够解决任务并正确分类所有训练模式的线性分类器中，我们的优化任务选择了范数最小的那个。正如下文所述，范数 `\|\mathbf{\theta}\|` 与相应分类器形成的间隔直接相关。

![Figure 11.14 There is an infinite number of linear classifiers that can classify correctly all the patterns in a linearly separable class task.](img/gr014.jpg)

**Figure 11.14** 存在无限多个线性分类器，它们能够正确分类线性可分类任务中的所有模式。

空间中的每个超平面由以下方程描述：

$$

f(\mathbf{x}) = \mathbf{\theta}^T\mathbf{x} + \theta_0 = 0.

$$

根据经典几何（另见习题 5.11），我们知道其在空间中的方向由 `\mathbf{\theta}` 控制（垂直于超平面），其位置由 `\theta_0` 控制（参见 Figure 11.15）。从所有能精确解决任务且具有特定方向（即共享同一个 `\mathbf{\theta}`）的超平面集合中，我们选择 `\theta_0` 以将超平面置于两个类别之间，使其到每个类别最近点的距离相同。Figure 11.16 展示了两个不同方向（灰色和红色实线）的线性分类器（超平面）。它们都被放置为到两个类别中最近点的距离相同。此外，请注意与“灰色”分类器相关的距离 `z_1` 小于与“红色”分类器相关的距离 `z_2`。

![Figure 11.15 The direction of the hyperplane θTx + θ0 = 0 is determined by θ and its position in space by θ0. Note that θ has been shifted away from the origin, since here we are only interested to indicate its direction, which is perpendicular to the straight line.](img/gr015.jpg)

**Figure 11.15** 超平面 `\mathbf{\theta}^T\mathbf{x} + \theta_0 = 0` 的方向由 `\mathbf{\theta}` 决定，其在空间中的位置由 `\theta_0` 决定。请注意，`\mathbf{\theta}` 已从原点平移开，因为这里我们只关心指示其方向，该方向垂直于直线。

![Figure 11.16 For each direction θ, “red” and “gray,” the (linear) hyperplane classifier, θTx + θ0 = 0 (full lines), is placed in between the two classes and normalized so that the nearest points from each class have a distance equal to one. The dotted lines, θTx + θ0 = ±1, which pass through the nearest points, are parallel to the respective classifier and define the margin. The width of the margin is determined by the direction of the corresponding classifier in space and is equal to \frac{2}{||\mathbf{\theta}||}Equation.](img/gr016.jpg)

**Figure 11.16** 对于每个方向 `\mathbf{\theta}`，“红色”和“灰色”，(线性)超平面分类器 `\mathbf{\theta}^T\mathbf{x} + \theta_0 = 0`（实线）被置于两个类别之间并进行归一化，使得来自每个类别的最近点距离等于 1。虚线 `\mathbf{\theta}^T\mathbf{x} + \theta_0 = \pm 1` 穿过最近点，分别与对应的分类器平行并定义了间隔。间隔的宽度由空间中相应分类器的方向决定，等于 `\frac{2}{\|\mathbf{\theta}\|}`。

根据基础几何知识，我们知道点 `\mathbf{x}` 到超平面的距离（参见 Figure 11.15）由下式给出：

`z = \frac{|\mathbf{\theta}^{T}\mathbf{x} + \theta_{0}|}{\|\mathbf{\theta}\|}`

![Equation](img/si342.png)

如果该点位于超平面上，该值显然为零。此外，我们总可以用一个常数因子，比如说 `a`，同时缩放 `\theta` 和 `\theta[0]`，而不影响超平面的几何形状，正如公式 (11.66) 所述。经过适当的缩放后，我们总能使两个类别中最近的点到超平面的距离等于 `z = \frac{1}{\|\mathbf{\theta}\|}`；等价地说，这种缩放保证了如果 `x` 是距离超平面最近的点，则 `f(x) = ± 1`，符号取决于该点属于 `\omega[1] (+ 1)` 还是 `\omega[2] (− 1)`。由 `f(x) = ± 1` 定义的这两个超平面，在 图 11.16 中显示为虚线，适用于“灰色”和“红色”两个方向。这一对超平面定义了每个方向对应的间隔，其宽度等于 `\frac{2}{\|\mathbf{\theta}\|}`.

![Equation](img/si347.png)

因此，如前所述构建的、且能解决该任务的任何分类器都具有以下两个性质：

*   它具有*间隔*，宽度等于 `\frac{1}{\|\mathbf{\theta}\|} + \frac{1}{\|\mathbf{\theta}\|}`；
*   它满足以下两组约束条件，

```
θ^(T)x[n] + θ[0] ≥ + 1,  x[n] ∈ ω[1],
θ^(T)x[n] + θ[0] ≤ − 1,  x[n] ∈ ω[2].
```

![Equation](img/si349.png)

因此，(11.64)–(11.65) 中的优化任务计算的是在约束条件下*最大化间隔*的线性分类器。

正则化项 `\|\mathbf{\theta}\|²` 的间隔解释，将设计最大化间隔分类器的任务，与统计学习理论以及 Vapnik–Chervonenkis 的开创性工作巧妙地联系在了一起，后者建立了此类分类器泛化性能的优雅界限（参见例如 [28,123,127,128]）。

###### 解

遵循与支持向量回归情况类似的步骤，解可表示为训练样本子集的线性组合，即

$$

\widehat{\mathbf{\theta}} = \sum\limits_{n = 1}^{N_{s}}\lambda_{n}y_{n}\mathbf{x}_{n},

$$

其中 `N_{s}` 是非零拉格朗日乘子的数量。结果表明，只有与最靠近分类器的点相关联的拉格朗日乘子，即那些满足等式约束的点（`y_{n}(\mathbf{\theta}^{T}\mathbf{x}_{n} + \theta_{0}) = 1`），才是非零的。这些被称为*支持向量*。与较远点（`y_{n}(\mathbf{\theta}^{T}\mathbf{x}_{n} + \theta_{0}) > 1`）对应的拉格朗日乘子为零。偏置项的估计值 `\hat{\theta}_{0}`，是通过选择所有 `\lambda_{n} \neq 0` 的约束来获得的，这些约束对应于

$$

y_{n}({\widehat{\mathbf{\theta}}}^{T}\mathbf{x}_{n} + {\widehat{\theta}}_{0}) - 1 = 0,\quad n = 1,2,\ldots,N_{s},

$$

求解 `\hat{\theta}_{0}` 并取平均值。

对于更一般的 RKHS 情况，解是一个由下式给出的函数

$$

\widehat{\theta}( \cdot ) = \sum\limits_{n = 1}^{N_{s}}\lambda_{n}y_{n}\kappa( \cdot ,\mathbf{x}_{n}),

$$

这导致了以下预测规则。给定一个未知的 `\mathbf{x}`，其类别标签根据以下公式的符号进行预测

`ŷ(\mathbf{x}) = ⟨\hat{\theta}, \kappa(\cdot,\mathbf{x})⟩ + \hat{\theta}[0]`

![Equation](img/si358.png)

或

![Equation](img/fx011.jpg)(11.68)

与线性情况类似，我们选择所有与 `\lambda[n] \neq 0` 相关的约束，即

```
y_n ( ∑_{m=1}^{N_s} λ_m y_m κ(x_m, x_n) + θ̂_0 ) - 1 = 0, n = 1,2,...,N_s,
```

![Equation](img/si360.png)

而 `\hat{\theta}[0]` 则计算为从这些约束中每一个获得的值的平均值。尽管解是唯一的，但对应的拉格朗日乘子可能不唯一（例如，参见 [123]）。

最后，必须强调的是，支持向量的数量与分类器的泛化性能有关。*支持向量的数量越少，预期的泛化能力越好* [28,123]。

###### 优化任务

此部分在初次阅读时也可以跳过。

(11.64)–(11.65) 中的任务是一个二次规划任务，可以遵循类似于 SVR 任务所采用的步骤来求解。

相关的拉格朗日函数由下式给出

```
L(θ, θ_0, λ) = 1/2 ||θ||² - ∑_{n=1}^N λ_n ( y_n ( θ^T x_n + θ_0 ) - 1 ),
```

![Equation](img/si361.png)(11.69)

而 KKT 条件（附录 C）变为

$$

\frac{\partial}{\partial\mathbf{\theta}}L(\mathbf{\theta},\theta_{0},\mathbf{\lambda}) = 0 \longrightarrow \widehat{\mathbf{\theta}} = \sum\limits_{n = 1}^{N}\lambda_{n}y_{n}\mathbf{x}_{n},

$$

![Equation](img/si362.png)(11.70)

$$
