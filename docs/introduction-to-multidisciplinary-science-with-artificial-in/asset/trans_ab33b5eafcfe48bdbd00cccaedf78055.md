

**测验：旋转条件下的金斯不稳定性。** 为了推导更实际的不稳定性判据，必须考虑旋转。在旋转参考系中，需要在流体动力学方程组 (6.150)-(6.153) 中加入科里奥利加速度和离心加速度。我们可以将离心力与引力合并，用 Ψ 表示由旋转通过离心力引起的引力势扰动。科里奥利加速度可以作为附加源项加入动量方程。假设扰动仅沿 z 轴变化，在没有磁效应的情况下，在时-空域和频率-波数域中重写旋转云团的方程组 (6.150)-(6.153)。(2) 推导当扰动传播方向与旋转轴夹角为 90 度时的金斯波长。

## 6.4.3. 开尔文-亥姆霍兹不稳定性与瑞利-泰勒不稳定性

瑞利-泰勒（RT）不稳定性与开尔文-亥姆霍兹（KH）不稳定性是自然界中观测到的典型流体和等离子体动力学现象，包括云层、行星大气和超新星等。它们发生在分隔两种不同性质的流体或等离子体的界面处。这两种不稳定性通常同时出现。此外，两者的数学推导过程相同。我们在此推导这些界面不稳定性的条件。

考虑两个不可压缩、均匀的平面等离子体层，其中嵌有恒定磁场 $\boldsymbol{B}_1$ 和 $\boldsymbol{B}_2$、恒定速度场 $\boldsymbol{v}_1$ 和 $\boldsymbol{v}_2$ 以及恒定密度 $\rho_1$ 和 $\rho_2$，如图 6.41 所示。我们保持垂直重力场 $g = -g\hat{\boldsymbol{i}}_z$。整个结构由以下两个区域组成：

$\rho_0 = \begin{cases} \rho_1, & z < 0 \\ \rho_2, & z > 0 \end{cases} \quad , \quad \boldsymbol{v} = \begin{cases} \boldsymbol{v}_1, & z < 0 \\ \boldsymbol{v}_2, & z > 0 \end{cases} \quad , \quad \boldsymbol{B}_0 = \begin{cases} \boldsymbol{B}_1, & z < 0 \\ \boldsymbol{B}_2, & z > 0 \end{cases} \quad . \quad (6.208)$

两个区域中的磁场均假定为平行于 $x$-$y$ 平面。我们处理的是定常等离子体而非静态等离子体，如图 6.41 所示。正是两个等离子体界面处速度、磁场和密度的跃变，使等离子体在某些条件下变得不稳定。

因此，这两个等离子体具有不同的速度和密度，并受到如下不同磁场的作用（另见图 6.41）：

- 上层（$0 < z \le a$）：$\rho_1 = \text{const.}$，$\boldsymbol{v}_1 = [v_{x1}, v_{y1}, 0]^T = \text{const.}$，$\boldsymbol{B}_1 = [B_{x1}, B_{y1}, 0]^T = \text{const.}$，且 $p_1 = p_0 - \rho_1 g z$，其中 $p_0 > \rho g a$。根据 (6.177)，我们有

$\frac{d^2 \xi^{(1)}}{dz^2} - k_0^2 \xi^{(1)} = 0$, with $\xi^{(1)}(a) = 0 \implies \xi^{(1)} = C_1 \frac{\sinh[k_0(a - z)]}{\sinh(k_0 a)}$,

其中 $C_1$ 为积分常数，$\xi^{(1)}$ 是拉格朗日位移矢量 $\boldsymbol{\xi}$ 的垂直分量。同样，$\boldsymbol{\xi}$ 描述了不稳定性使流体元在初始流 $(\boldsymbol{v} = \boldsymbol{v}_0 = \mathbf{0})$ 与扰动流 $(\boldsymbol{v} = \boldsymbol{v}_0 + \delta \boldsymbol{v} = \delta \boldsymbol{v} = \partial \boldsymbol{\xi}/\partial t)$ 之间发生位移的方式。

![](img/f5b5b8709fc3a81631262f22d3552c5e_696_0.png)

图 6.41. 考虑两个等离子体。上层（z > 0）和下层（z < 0）流体具有不同的密度 ρ₁ 和 ρ₂。对两个等离子体施加了两个不同的磁场。等离子体界面处的扰动为垂直位移 z = ξ(x, y, t)；即界面在 ξ(x, y, t) 处的扰动位置。

- 下层（$-b < z \le 0$）：ρ = const.，v₂ = [vₓ₂, vᵧ₂, 0]ᵀ = const.，B₂ = [Bₓ₂, Bᵧ₂, 0]ᵀ = const.，且 p₂ = p₀ - ρ₂ g z。根据 (6.177)，我们有

$d²ξ⁽²⁾/dz² - k₀² ξ⁽²⁾ = 0 , with ξ⁽²⁾(-b) = 0 ⟹ ξ⁽²⁾ = C₂ sinh[k₀(z + b)] / sinh(k₀ b) ,$

其中 C₂ 是积分常数。

- 第一个边界条件是运动学边界条件，表述界面处等离子体位移（或法向速度）的法向分量连续；即

$\xi^{(1)}(0) = \xi^{(2)}(0) \implies C_1 = C_2 .$

- 第二个边界条件是动力学边界条件，表述界面 z = 0 处总压力（压力平衡）连续；即

$[Π - ρ g ξ]_1^2 = 0 \implies [ (ρ/k₀²)(~ω² - ω_A²) (1/ξ) dξ/dz - ρ g ]_1^2 = 0 , \quad (6.209)$

其中 Π 是在 (6.177) 中针对随深度变化的不可压缩等离子体（即 γ ⟶ ∞）定义的总压力（动力学压力加磁压力），这意味着 ∇·ξ = 0。

分析不稳定性的标准方法是求出其色散关系。将 ξ₁ 和 ξ₂ 的解代入 (6.209) 得到色散方程：

-ρ₁ [ (ω - Ω₀₁)² - ω_A₁² ] coth(k₀ a) - k₀ ρ₁ g
= -ρ₂ [ (ω - Ω₀₂)² - ω_A₂² ] coth(k₀ b) - k₀ ρ₂ g.   (6.210)

对于短波长（即壁面实际上 $a \longrightarrow \infty$ 和 $b \longrightarrow -\infty$），我们有 $k_0 x \gg 1$，因此 $\coth(k_0 x) \approx 1$。上述解简化为

$$\omega = \omega^{(r)} + i\omega^{(i)} = \frac{\rho_1\Omega_{01} + \rho_2\Omega_{02}}{\rho_1 + \rho_2} \pm \left[ -\frac{\rho_1\rho_2 (\Omega_{01} - \Omega_{02})^2}{(\rho_1 + \rho_2)^2} + \frac{\rho_1\omega_{A1}^2 + \rho_2\omega_{A2}^2}{\rho_1 + \rho_2} - \frac{k_0 (\rho_1 - \rho_2) g}{\rho_1 + \rho_2} \right]^{1/2}, \tag{6.211}$$

其中 $\Omega_{01} = \boldsymbol{k}_0 \cdot \boldsymbol{v}_1$，$\Omega_{02} = \boldsymbol{k}_0 \cdot \boldsymbol{v}_2$，$\omega_{A1} = \boldsymbol{k}_0 \cdot \boldsymbol{B}_1 / \sqrt{\mu_0\rho_1}$，$\omega_{A2} = \boldsymbol{k}_0 \cdot \boldsymbol{B}_2 / \sqrt{\mu_0\rho_2}$，$\boldsymbol{k}_0 = [k_x, k_y]^T$，且 $k_0^2 = \boldsymbol{k}_0 \cdot \boldsymbol{k}_0$。波动方程的解 $\xi$ 表示两支波（当 $\omega$ 为实数（或 $\omega^2 > 0$）时）或具有复频率的两个模（即不稳定性）——也就是说，它们取决于 (6.211) 中平方根下表达式的符号。我们可以看到，当 $\omega^{(i)} = 0$ 时 $\omega$ 是实数；更一般地，当该表达式为负时，也就是说：

$$\underbrace{\frac{(\boldsymbol{k}_0 \cdot \boldsymbol{B}_1)^2 + (\boldsymbol{k}_0 \cdot \boldsymbol{B}_2)^2}{\mu_0}}_{\text{磁剪切}} < \underbrace{\frac{\rho_1\rho_2}{\rho_1 + \rho_2} [\boldsymbol{k}_0 \cdot (\boldsymbol{v}_{01} - \boldsymbol{v}_{02})]^2}_{\text{KH 驱动}} + \underbrace{k_0 (\rho_1 - \rho_2) g}_{\text{RT 驱动}}, \tag{6.212}$$

则系统是不稳定的。KH 驱动和 RT 驱动这两个术语表征了两种不同的不稳定性，我们将在接下来的段落中描述。三个项之间存在真正的竞争，因此稳定性取决于所有这些参数的精确选择。所以，这种界面不稳定性的关键原因是 $\Omega_{01} \neq \Omega_{02}$、$\omega_{A1} \neq 0$、$\omega_{A2} \neq 0$ 和/或 $\rho_1 < \rho_2$。注意，上述推导仅限于 $\boldsymbol{k}_0 \parallel \boldsymbol{B}_0$ 的情形。实际上，即使当 $\boldsymbol{k}_0 \perp \boldsymbol{B}_0$ 时它们也成立，这等价于令 $\omega_{A2} = \boldsymbol{k}_0 \cdot \boldsymbol{B}_2 / \sqrt{\mu_0\rho_2} = 0$ 和 $\omega_{A1} = \boldsymbol{k}_0 \cdot \boldsymbol{B}_1 / \sqrt{\mu_0\rho_1} = 0$。换言之，$\boldsymbol{k}_0 \perp \boldsymbol{B}_0$ 消除了磁场对界面不稳定性的影响，从而产生流体动力学不稳定性。

### 开尔文-亥姆霍兹（KH）不稳定性

开尔文-亥姆霍兹（KH）不稳定性是一种界面不稳定性，当两种密度不同的流体在其界面上存在速度差时产生。假设没有重力，即 (6.211) 变为

$$\omega_{\text{KH}} = \frac{\rho_1\Omega_{01} + \rho_2\Omega_{02}}{\rho_1 + \rho_2} \pm \left[ -\frac{\rho_1\rho_2 (\Omega_{01} - \Omega_{02})^2}{(\rho_1 + \rho_2)^2} + \frac{\rho_1\omega_{A1}^2 + \rho_2\omega_{A2}^2}{\rho_1 + \rho_2} \right]^{1/2} \tag{6.213}$$

并且在此条件下，$\omega_{\text{KH}}$ 变为复值频率：

$$\frac{(\boldsymbol{k}_0 \cdot \boldsymbol{B}_1)^2 + (\boldsymbol{k}_0 \cdot \boldsymbol{B}_2)^2}{\mu_0} < \frac{\rho_1\rho_2}{\rho_1 + \rho_2} [\boldsymbol{k}_0 \cdot (\boldsymbol{v}_{01} - \boldsymbol{v}_{02})]^2. \tag{6.214}$$

这种不稳定性由开尔文勋爵（以温度单位著称）于 1871 年提出，并由赫尔曼·冯·亥姆霍兹（以亥姆霍兹方程著称）于 1868 年提出，如今被称为开尔文-亥姆霍兹不稳定性（KHI）。考虑特殊情况：$\boldsymbol{v}_1 = [v_{1x}, 0, 0]^T$，$\boldsymbol{v}_2 = [0, 0, 0]^T$（即静止），$\boldsymbol{B}_1 = \boldsymbol{B}_2 = \boldsymbol{B}_0$，且 $\boldsymbol{k}_0 = [k_x, k_y]^T$。则 (6.213) 中的不稳定性判据简化为

$$\underbrace{\frac{2(\boldsymbol{k}_0 \cdot \boldsymbol{B}_0)^2}{\mu_0 \bar{\rho}}}_{\text{磁张力}} < \underbrace{\boldsymbol{k}_0 \cdot \boldsymbol{v}_{01}}_{\text{速度剪切}}. \tag{6.215}$$

