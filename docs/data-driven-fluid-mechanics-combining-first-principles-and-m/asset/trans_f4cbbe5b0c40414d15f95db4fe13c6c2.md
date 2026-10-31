
大多数计算软件使得 T_u 的列具有单位范数。然后两个 Gram 矩阵都被对角化，但不一定相等：

T_u^{-1} W_c T_u^* = Σ_c. (12.20a)
T_u^* W_o T_u = Σ_o. (12.20b)

精确平衡这些 Gram 矩阵的缩放随后由 Σ_s = Σ_c^{1/4} Σ_o^{-1/4} 给出。因此，精确的平衡变换为

T = T_u Σ_s. (12.21)

可以直接验证该变换使 Gram 矩阵平衡：

(T_u Σ_s)^{-1} W_c (T_u Σ_s)^{-*} = Σ_s^{-1} T_u^{-1} W_c T_u^{*-1} Σ_s^{-1} = Σ_s^{-1} Σ_c Σ_s^{-1} = Σ_c^{1/2} Σ_o^{1/2}, (12.22a)
(T_u Σ_s)^* W_o (T_u Σ_s) = Σ_s T_u^* W_o T_u Σ_s = Σ_s Σ_o Σ_s = Σ_c^{1/2} Σ_o^{1/2}. (12.22b)

这些运算依赖于对角矩阵可交换这一事实，因此 Σ_c Σ_o = Σ_o Σ_c 等等。

## 平衡变换和 Gram 矩阵的示例

在面对准确高效计算平衡变换相关的实际挑战之前，考虑一个说明性示例是有帮助的。

以下示例说明了二维系统的平衡实现。首先，我们生成一个系统并计算其平衡实现，以及每个系统的 Gram 矩阵。接下来，我们在图 12.2 中可视化非平衡和平衡系统的 Gram 矩阵。

为了在图 12.2 中可视化 Gram 矩阵，我们首先回忆，系统在方向 x 上在单位激励输入下所能达到的距离由 x^* W_c x 给出。因此，可控性 Gram 矩阵可通过对 ||x|| = 1 的球面上 x 绘制 W_c^{1/2} x 来可视化。可观测性 Gram 矩阵可类似地可视化。

## 12.1.4 平衡截断

我们现在已表明，可以定义一种坐标变换，使得可控性和可观测性 Gram 矩阵相等且为对角。此外，这些新坐标可以根据其联合可控性

![](img/ddadb1d3eaa6f9576eea68f95d453bca_259_0.png)

图 12.2 平衡变换对 Gram 矩阵的示意。单位控制输入下的可达集合以红色显示，由 ||x|| = 1 时的 W_c^{1/2} x 给出。相应的可观测集合以蓝色显示。在平衡变换 T 下，Gram 矩阵相等，以紫色显示。摘自 Brunton and Kutz (2019)，经 Licensor 通过 PLSclear 许可转载。

以及可观测性进行层次化排序。可以截断这些坐标并仅保留最可控/可观测的方向，从而得到一个忠实捕捉输入-输出动态的 ROM。

给定新的坐标 z = T^{-1} x ∈ R^n，可以将降阶状态 \tilde{x} ∈ R^r 定义为

```
z = [ z1 : z_r z_{r+1} : z_n ] } \tilde{x}  (12.23)
```

以最可控和最可观测的前 r 个方向表示。如果我们将平衡变换 T 和逆变换 S = T^{-1} 分区为要保留的前 r 个模态和要截断的后 n − r 个模态，

```
T = [Ψ  T_t],  S = [Φ* S_t],  (12.24)
```

则可以重写 (12.7) 中的变换动力学为

$$\frac{d}{dt}\begin{bmatrix}\tilde{\mathbf{x}}\\ \mathbf{z}_t\end{bmatrix}=\begin{bmatrix}\mathbf{\Phi}^*\mathbf{A}\mathbf{\Psi}&\mathbf{\Phi}^*\mathbf{A}\mathbf{T}_t\\ \mathbf{S}_t\mathbf{A}\mathbf{\Psi}&\mathbf{S}_t\mathbf{A}\mathbf{T}_t\end{bmatrix}\begin{bmatrix}\tilde{\mathbf{x}}\\ \mathbf{z}_t\end{bmatrix}+\begin{bmatrix}\mathbf{\Phi}^*\mathbf{B}\\ \mathbf{S}_t\mathbf{B}\end{bmatrix}\mathbf{u},\qquad(12.25a)$$

$$\mathbf{y}=\begin{bmatrix}\mathbf{C}\mathbf{\Psi}&\mathbf{C}\mathbf{T}_t\end{bmatrix}\begin{bmatrix}\tilde{\mathbf{x}}\\ \mathbf{z}_t\end{bmatrix}+\mathbf{D}\mathbf{u}.\qquad(12.25b)$$

在平衡截断中，状态 $\mathbf{z}_t$  simply 被截断（即丢弃并设为零），仅保留 $\tilde{\mathbf{x}}$ 方程：

$$\frac{d}{dt}\tilde{\mathbf{x}}=\mathbf{\Phi}^*\mathbf{A}\mathbf{\Psi}\tilde{\mathbf{x}}+\mathbf{\Phi}^*\mathbf{B}\mathbf{u},\qquad(12.26a)$$ $$\mathbf{y}=\mathbf{C}\mathbf{\Psi}\tilde{\mathbf{x}}+\mathbf{D}\mathbf{u}.\qquad(12.26b)$$

构造 $\mathbf{\Psi}$ 和 $\mathbf{\Phi}$ 仅需要 $\mathbf{T}$ 的前 $r$ 列和 $\mathbf{S}^*=\mathbf{T}^{-*}$，因此计算整个平衡变换 $\mathbf{T}$ 是不必要的。将在后续章节讨论不通过 $\mathbf{T}$ 计算 $\mathbf{\Psi}$ 和 $\mathbf{\Phi}$。平衡截断的一个关键优点是给定阶截断误差存在上界和下界：

**上界：** $||\mathbf{G}-\mathbf{G}_r||_{\infty}\le 2\sum_{j=r+1}^{n}\sigma_j,\qquad(12.27a)$

**下界：** $||\mathbf{G}-\mathbf{G}_r||_{\infty}>\sigma_{r+1},\qquad(12.27b)$

其中 $\sigma_j$ 是平衡 Gram 矩阵的第 $j$ 个对角元。$\mathbf{\Sigma}$ 的对角元也称为 *汉克尔奇异值*。

## 12.1.5 计算平衡实现

在上一节中，我们证明了获得平衡可控性和可观测性 Gram 矩阵的坐标变换的可行性。然而，该平衡变换的计算并非微不足道，自 Moore (1981) 起，Lall et al. (2002)、Willcox and Peraire (2002) 和 Rowley (2005) 等人已投入大量工作以获得准确高效的方法。关于平衡实现和模型降阶的优秀且完整的论述，参见 Antoulas (2005)。

在实践中，计算 Gram 矩阵 $\mathbf{W}_c$ 和 $\mathbf{W}_o$ 以及 (12.16) 中乘积 $\mathbf{W}_c\mathbf{W}_o$ 的特征分解对于高维系统可能代价过高。相反，平衡变换可以从脉冲响应数据中近似，利用奇异值分解（SVD）高效提取最相关的子空间。

我们首先将展示 Gram 矩阵如何通过来自脉冲响应实验/仿真的快照矩阵近似。然后，我们将展示如何从该数据获得平衡变换。

### 经验 Gram 矩阵

在实践中，通过 Lyapunov 方程计算 Gram 矩阵计算成本高，计算复杂度为 $O(n^3)$。相反，Gram 矩阵可通过离散时间直接系统和伴随系统的全状态测量近似：

*直接：* $\boldsymbol{x}_{k+1} = \mathbf{A}_d \boldsymbol{x}_k + \mathbf{B}_d \boldsymbol{u}_k$,  (12.28a)
*伴随：* $\boldsymbol{x}_{k+1} = \mathbf{A}_d^* \boldsymbol{x}_k + \mathbf{C}_d^* \boldsymbol{y}_k$.  (12.28b)

式 (12.28a) 是离散时间动态更新方程，(12.28b) 是伴随方程。矩阵 $\mathbf{A}_d$、$\mathbf{B}_d$ 和 $\mathbf{C}_d$ 是离散时间系统矩阵。注意伴随方程通常是非物理的，必须进行仿真；因此这里的方法适用于解析方程和仿真，但不适用于实验数据。一种不依赖伴随数据、从而推广到实验的替代公式将在第 12.2 节中给出。

计算直接系统和伴随系统的脉冲响应得到以下离散时间快照矩阵：

$\mathbf{C}_d = \begin{bmatrix} \mathbf{B}_d & \mathbf{A}_d \mathbf{B}_d & \cdots & \mathbf{A}_d^{m_c-1} \mathbf{B}_d \end{bmatrix}$
$\mathbf{O}_d = \begin{bmatrix} \mathbf{C}_d \\ \mathbf{C}_d \mathbf{A}_d \\ \vdots \\ \mathbf{C}_d \mathbf{A}_d^{m_o-1} \end{bmatrix}$ .  (12.29)

注意当 $m_c = n$ 时，$\mathbf{C}_d$ 是离散时间可控性矩阵，当 $m_o = n$ 时，$\mathbf{O}_d$ 是离散时间可观测性矩阵；然而我们通常考虑 $m_c, m_o \ll n$。这些矩阵也可以通过以规则间隔 $\Delta t$ 采样连续时间直接系统和伴随系统获得。

现在可以计算 *经验* Gram 矩阵，用以在不求解 Lyapunov 方程的情况下近似真实 Gram 矩阵：

$\mathbf{W}_c \approx \mathbf{W}_c^e = \mathbf{C}_d \mathbf{C}_d^*$,  (12.30a)
$\mathbf{W}_o \approx \mathbf{W}_o^e = \mathbf{O}_d^* \mathbf{O}_d$.  (12.30b)

经验 Gram 矩阵本质上是连续时间 Gram 矩阵中积分的黎曼和近似，当离散时间系统的步长变得任意小且脉冲响应的持续时间变得任意大时变得精确。在实践中，应在轻阻尼瞬态衰减后收集脉冲响应快照。经验 Gram 矩阵方法非常高效，已被广泛使用（Moore 1981, Lall et al. 1999, Lall et al. 2002, Willcox & Peraire 2002, Rowley 2005）。注意需要 $p$ 个伴随脉冲响应，其中 $p$ 为输出数。当输出数量很大时（例如全状态测量），这变得不可行，从而促使下面的输出投影。

