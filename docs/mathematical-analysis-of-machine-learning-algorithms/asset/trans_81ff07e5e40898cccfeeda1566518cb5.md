
### 例 9.23

对于 $y \in \{\pm1\}$ 的二分类问题，我们可以考虑由实值函数 $f(x)$ 诱导的分类器，使得当 $f(x)\geq 0$ 时预测 $y=1$，否则预测 $y=-1$。如果 $f(x)$ 取自 RKHS，则有以下 margin 界。概率为 $1-\delta$，对所有满足 $\|f\|_{\mathcal H}\leq A$ 的 $f\in\mathcal H$，

$$\mathbb E_D\mathbb 1(f(X)Y\leq 0)\leq \frac{1}{n}\sum_{i=1}^{n}\mathbb 1(f(X_i)Y_i\leq\gamma)+\frac{2A}{\gamma}\sqrt{\frac{\mathbb E_D k(X,X)}{n}}+\sqrt{\frac{\ln(1/\delta)}{2n}}.$$

它表明如果我们能找到一个 margin 误差很小的分类器，则可以实现良好的测试分类误差。与第 4 章中的 VC 分析不同，该界不依赖于特征向量 $\psi(x)$ 的维数，而是依赖于分类器的 RKHS 范数 $A$ 和 margin 条件。

该界可以直接由推论 9.22 得到，使用损失函数 $L(p,y)=\min(1,\max(0,1-py/\gamma))$，它是 $\gamma^{-1}$ Lipschitz 的。在这种情况下，$\mathbb 1(f(x)y\leq 0)\leq L(f(x),y)\leq\mathbb 1(f(x)y\leq\gamma)$。

我们注意到 Rademacher 复杂度分析仅导致 $O(1/\sqrt n)$ 的收敛速率。然而，与 VC 分析类似，当 margin 误差为零时，可以得到 $O(\ln n/n)$ 的 margin 界。这需要定理 4.21 中陈述的不同分析，以及定理 5.20 的经验 $L_\infty$ covering 数。我们将其留给练习 9.5。

### 例 9.24

对于 SVM 损失，$\gamma=1$。在硬正则化下，我们可以取 $M=(1+AB)$，其中假设 $k(x,x)\leq B^2$。考虑求解 (9.9) 达到精度 $\epsilon' > 0$ 的 $\hat f$。由推论 9.22 可得，概率至少为 $1-\delta$，

$$\mathbb E_D L(\hat f(X),Y)\leq \inf_{\|f\|_{\mathcal H}\leq A}\mathbb E_D L(f(X),Y)+\epsilon'+\frac{2AB}{\sqrt n}+(1+AB)\sqrt{\frac{2\ln(2/\delta)}{n}}.$$

给定任意竞争者 $f\in\mathcal H$，$A$ 的最优值将为 $A=\|f\|_{\mathcal H}$。然而，这需要我们知道 $\|f\|_{\mathcal H}$ 的值，这在实际中不可行。实践中，使用软正则化版本 (9.10) 更方便，其中 $\lambda$ 的选择比 $A$ 更不敏感，并且可以独立于 $\|f\|_{\mathcal H}$ 设置。以下结果是推论 9.21 和定理 6.14 的直接推论。

### 推论 9.25
如果 $L(p,y)$ 关于 $p$ 是 $\gamma$-Lipschitz，则对 (9.10) 有以下期望 oracle 不等式：

$$\mathbb E_{S_n}L(\hat f,\mathcal D)\leq\inf_{f\in\mathcal H}\left[L(f,\mathcal D)+\frac{\lambda}{2}\|f\|_{\mathcal H}^{2}\right]+\frac{2\gamma^{2}\mathbb E_D k(X,X)}{\lambda n}.$$

请注意，在推论 9.25 中，期望 oracle 不等式不依赖于 $L(\cdot,\cdot)$ 的有界性。也可以通过采用第 8 章的技术以及对适当定义的嵌套函数类序列进行 union bound 来得到高概率不等式。

### 推论 9.26
假设 $L(p, y) \geq 0$ 关于 $p$ 是 $\gamma$ Lipschitz，且 $\sup_y L(0, y) \leq M₀$。令 $B² = \sup_x k(x, x)$，则概率至少为 $1 − δ$，对所有 $f ∈ H$，

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ (1/√n)(4M₀ + 4γB‖f‖_H) + (3M₀ + 2γB‖f‖_H) √[ ln(2(2 + log₂(1 + γB‖f‖_H/M₀))²/δ) / (2n) ].

证明 令 $Aθ = 2^{θ} A₀$，其中 $A₀ > 0$ 稍后确定，$q(θ) = 1/(θ + 1)²$ 对 $θ = 1, 2, …$。考虑 $Bθ = \{f ∈ H: ‖f‖_H ≤ Aθ\}$。我们知道 $L(p, y) ≤ L(0, y) + γ|p| ≤ M₀ + γAθB$。令 $Mθ = M₀ + γAθB$。则推论 9.22 表明概率至少为 $1 − q(θ)δ$，对所有满足 $‖f‖_H ≤ Aθ$ 的 $f ∈ H$，

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ 2γAθB/√n + Mθ √[ ln(2/(q(θ)δ)) / (2n) ].

取 union bound，我们有概率 $1 − δ$，对所有 $f ∈ H$ 和所有满足 $‖f‖_H ≤ Aθ$ 的 $θ ≥ 1$，

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ 2γAθB/√n + Mθ √[ ln(2/(q(θ)δ)) / (2n) ].

我们令 $θ(f) ≥ 1$ 为满足 $‖f‖_H ≤ Aθ$ 的最小指标。则 $Aθ(f) ≤ 2(A₀ + ‖f‖_H)$，从而 $θ(f) ≤ log₂(2 + 2‖f‖_H/A₀)$。我们可以取 $A₀ = M₀/(γB)$。这就得到了期望的界。□

我们也可以得到如下的 oracle 不等式。

### 推论 9.27
假设 $L(p, y) ≥ 0$ 关于 $p$ 是 $\gamma$-Lipschitz，$\sup_y L(0, y) ∈ [0, M₀]$，且 $\sup_x k(X, X) ≤ B²$。则概率为 $1 − δ$，对 (9.10) 有以下 oracle 不等式：

L(f̂, D) ≤ inf_{f∈H} [ L(f, D) + (λ/2)‖f‖²_H + ε_B‖f‖_H ] + 2ε_M + ε_B²/(2λ),

其中 $θ₀ = 1 + log₂(1 + γB √(2/(λM₀)))$，且

ε_M = 4M₀/√n + 3M₀ √[ ln(2(1 + θ₀)²/δ) / (2n) ],

ε_B = 4γB/√n + 2γB √[ ln(2(1 + θ₀)²/δ) / (2n) ].

证明 我们注意到 $‖f‖²_H ≤ 2M₀/λ$。因此推论 9.26 表明概率至少为 $1 − δ$，对所有 $f ∈ H$，

| E_D L(f(X), Y) − (1/n) ∑ᵢ₌₁ⁿ L(f(Xᵢ), Yᵢ) | ≤ ε_M + ε_B‖f‖_H.  (9.13)

这意味着

L(\hat{f}, \mathcal{D}) \le \frac{1}{n} \sum_{i=1}^{n} L(\hat{f}(X_i), Y_i) + \frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} \underbrace{-\frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} + \epsilon_M + \epsilon_B \|\hat{f}\|_{\mathcal{H}}}_{V}
\le \frac{1}{n} \sum_{i=1}^{n} L(\hat{f}(X_i), Y_i) + \frac{\lambda}{2} \|\hat{f}\|_{\mathcal{H}}^{2} + \epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}
\le \frac{1}{n} \sum_{i=1}^{n} L(f(X_i), Y_i) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^{2} + \epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}
\le L(f, \mathcal{D}) + \frac{\lambda}{2} \|f\|_{\mathcal{H}}^{2} + \epsilon_B \|f\|_{\mathcal{H}} + 2\epsilon_M + \frac{\epsilon_B^{2}}{2\lambda}.

第一个不等式使用了 (9.13)。第二个不等式可以通过对 $\|\hat{f}\|_{\mathcal{H}}$ 最大化 $V$ 得到。第三个不等式使用了 $\hat{f}$ 是 (9.10) 的解这一事实。最后一个不等式再次使用了 (9.13)。

### 例 9.28
考虑 (9.10) 中的软正则化 SVM。我们可以令 $\gamma = 1$ 且 $M₀ = 1/B$。由此可知，如果取 $\lambda = O(1/\sqrt{n})$，则由推论 9.27 得到收敛速率为 $O(\sqrt{\ln \ln n / n})$ 的 oracle 不等式。

## 9.4 向量值函数

我们现在考虑使用核的向量值函数。在这种情况下，我们有 $f(x): 𝒳 → ℝ^q$，其中 $q > 1$。令 $f(x) = [f₁(x),...,f_q(x)]$。如果考虑特征空间表示，则有两种可能性。一种是将这些函数视为共享相同的特征向量，但 $w$ 不同：

f_ℓ(x) = ⟨w_ℓ, ψ(x)⟩      (ℓ = 1,...,q).

另一种观点是考虑相同的 $w$，但对不同维度使用不同的特征：

f_ℓ(x) = ⟨w, ψ(x,ℓ)⟩. (9.14)

第二种观点更一般，因为我们可以将第一种观点写成如下形式。我们通过令 $w = [w₁,...,w_q]$ 且 $\psi(x,ℓ) = [0,...,0,ψ(x),0,...,0]$ 来拼接特征表示，其中只有第 $ℓ$ 个拼接分量为 $\psi(x)$，其他分量为零。利用此表示，$\langle w, ψ(x,ℓ) \rangle = \langle w_ℓ, ψ(x) \rangle$。在以下讨论中，我们关注 (9.14)。

类似于 (9.2)，我们在特征表示中有以下公式：

ĥw = arg min_{w∈ℋ} [ 1/n ∑_{i=1}^{n} L(⟨w, ψ(X_i,·)⟩, Y_i) + λ/2 ‖w‖² ], (9.15)

### 定理 9.29

考虑 $q$ 维向量值函数 $f(x)$。令 $\hat f(x)= \langle \hat w, \psi(x,\cdot)\rangle$，其中 $\hat w$ 为 (9.15) 的解。则

$$\hat f(x)=\sum_{i=1}^{n}\mathbf{k}(x,X_i)\hat\alpha_i,$$

其中

$$\langle \hat w, \hat w\rangle = \sum_{i=1}^{n}\sum_{j=1}^{n}\hat\alpha_i^{\top}\mathbf{k}(X_i,X_j)\hat\alpha_j,$$

其中每个 $\hat\alpha_i \in \mathbb{R}^q$，且

$$\mathbf{k}(x,x')=\begin{bmatrix}k_{1,1}(x,x') & \cdots & k_{1,q}(x,x')\\ \vdots & & \vdots\\ k_{q,1}(x,x') & \cdots & k_{q,q}(x,x')\end{bmatrix},$$

且

$$k_{i,j}(x,x')=\langle\psi(x,i),\psi(x',j)\rangle \qquad (i,j=1,\dots,q).$$

因此 (9.15) 的解等价于

$$\hat\alpha=\arg\min_{\alpha\in\mathbb{R}^{q\times n}}\left[\frac{1}{n}\sum_{i=1}^{n}L\left(\sum_{j=1}^{n}\mathbf{k}(X_i,X_j)\alpha_j,Y_i\right) +\frac{\lambda}{2}\sum_{i=1}^{n}\sum_{j=1}^{n}\alpha_i^{\top}\mathbf{k}(X_i,X_j)\alpha_j\right].\tag{9.16}$$

证明 证明类似于定理 9.2 的证明，我们将 (9.15) 中的目标定义为 $Q1(w)$。 (9.16) 中的目标记为 $Q2(α)$。 (9.15) 的解满足以下一阶最优性条件：
