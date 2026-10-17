
$(E_{min}, G_{min})$ 出现在中表面。孔隙率分布类型 2 表现出的材料属性变化是从顶表面到底面的连续下降。类型 1 和类型 2 的材料属性变化过程可以用公式 (2.2) 和 (2.3) 的数学形式表示，这些公式可以从文献 [8,30] 中。

$$E(z) = E_{max} \left[1 - e_{0E}\cos\left(\frac{\pi z}{h}\right)\right] \quad (2.2a)$$

$$G(z) = G_{max} \left[1 - e_{0G}\cos\left(\frac{\pi z}{h}\right)\right] \quad (2.2b)$$

$$\rho(z) = \rho_{max} \left[1 - e_{m\rho}\cos\left(\frac{\pi z}{2h} + \frac{\pi}{4}\right)\right] \quad (2.2c)$$

$$E(z) = E_{max} \left[1 - e_{mE}\cos\left(\frac{\pi z}{2h} + \frac{\pi}{4}\right)\right] \quad (2.3a)$$

$$G(z) = G_{max} \left[1 - e_{mG}\cos\left(\frac{\pi z}{2h} + \frac{\pi}{4}\right)\right] \quad (2.3b)$$

$$\rho(z) = \rho_{max} \left[1 - e_{m\rho}\cos\left(\frac{\pi z}{2h} + \frac{\pi}{4}\right)\right] \quad (2.3c)$$

其中 $e_{0} < 1$ 且 $e_{m} < 1$。

## 2.2.2 功能梯度多孔梁的能量表述

FGP 梁的相应表述可以使用 Timoshenko 梁理论确定：

$$\begin{pmatrix} U \\ W \end{pmatrix} = u(\varphi,t) + z\phi(\varphi,t) \quad (2.5)$$

其中 $U$ 和 $W$ 是任意点的位移，$\phi$ 代表法向和剪切应变的中面分量。

法向和剪切应变用符号 $\varepsilon_{\varphi}$ 和 $\gamma_{\varphi z}$ 表示。基于小变形应变-位移关系：

$$\begin{pmatrix} \varepsilon_{\varphi} \\ \gamma_{\varphi z} \end{pmatrix} = \frac{1}{R_{\varphi}} \kappa_{\varphi} \quad (2.6)$$

其中上标 $0$ 表示变量 $\kappa_{\varphi}$ 代表曲率，可以表示为：

$$\varepsilon_{\varphi}^0 = \frac{1}{R_{\varphi}} \frac{\partial u}{\partial \varphi} + w, \quad \gamma_{\varphi z}^0 = \frac{1}{R_{\varphi}} (\frac{\partial w}{\partial \varphi} - u) \quad (2.7)$$

应用广义胡克定律得到的应力-应变本构关系可以表示为：

$$\begin{pmatrix} \sigma_{\varphi} \\ \tau_{\varphi z} \end{pmatrix} = \begin{pmatrix} Q_{11} & 0 \\ 0 & Q_{55} \end{pmatrix} \begin{pmatrix} \varepsilon_{\varphi} \\ \gamma_{\varphi z} \end{pmatrix} \quad (2.8)$$

其中 $\sigma_{\varphi}$ 和 $\tau_{\varphi z}$ 分别代表法向应力和剪切应力。$Q_{11}$ 和 $Q_{55}$ 是 FGP 材料的弹性刚度，其表达式可以写为：

$$Q_{11} = \frac{E(z)}{1-\nu^2} = G(z) \quad (2.9)$$

其中符号 $\nu$ 表示泊松比。积分方程 (2.8) 得到轴力 $N_{\varphi}$、剪力 $Q_{\varphi}$ 和弯矩 $M_{\varphi}$：

$$\begin{pmatrix} N_{\varphi} \\ Q_{\varphi} \end{pmatrix} = b \int_{-h/2}^{h/2} \begin{pmatrix} \sigma_{\varphi} \\ \tau_{\varphi z} \end{pmatrix} dz \quad (2.10)$$

$M_{v} = \dot{b} \int_{-b/2}^{b/2} \sigma_{v} dz \quad (2.10b)$

将等式 (2.6) 代入等式 (2.10)，进一步表达式可以重写为依赖于应变的形式：

```
$$\begin{cases} N_{\zeta} \\ M_{\zeta} \\ Q_{\zeta} \end{cases} = \begin{cases} A_{11} & B_{11} & 0 \\ B_{11} & D_{11} & 0 \\ 0 & 0 & A_{55} \end{cases} \begin{cases} \varepsilon_{\zeta} \\ k_{\zeta} \\ \gamma_{\zeta} \end{cases} \quad (2.11)$$
```

其中，扩展刚度系数 $A_{11}$、扩展系数 $B_{11}$、弯曲耦合刚度 $D_{11}$ 以及剪切刚度 $A_{55}$ 可以表示为：

```
$A_{11} = \tilde{A}_{11} - \frac{1}{R_{\zeta}}\tilde{B}_{11} \quad (2.12a)$
```

```
$B_{11} = \tilde{B}_{11} - \frac{1}{R_{\zeta}}\tilde{D}_{11} \quad (2.12b)$
```

```
$D_{11} = \tilde{D}_{11} - \frac{1}{R_{\zeta}}\hat{C}_{11} \quad (2.12c)$
```

```
$A_{55} = \kappa\tilde{A}_{55} - \frac{1}{R_{\zeta}}\tilde{B}_{55} \quad (2.12d)$
```

其中

```
$$\hat{\mathbf{Q}} = \mathbf{A} - \mathbf{BC}^{-1}\mathbf{B}^{T} \quad (2.13a)$$
```

```
$$\bar{\mathbf{Q}} = \begin{pmatrix} \tilde{A}_{11} & \tilde{B}_{11} \\ \tilde{B}_{11} & \tilde{D}_{11} \end{pmatrix} \quad (2.13b)$$
```

```
$$\mathbf{A} = \begin{pmatrix} \tilde{A}_{11} & \tilde{B}_{11} \\ \tilde{B}_{11} & \tilde{D}_{11} \end{pmatrix}, \mathbf{B} = \begin{pmatrix} A_{12} & 0 & B_{12} & 0 \\ B_{12} & 0 & D_{12} & 0 \end{pmatrix}, \mathbf{C} = \begin{pmatrix} \hat{A}_{11} & 0 & 0 \\ \hat{A}_{55} & 0 & 0 \\ 0 & 0 & \hat{D}_{11} \\ 0 & 0 & \hat{D}_{55} \end{pmatrix} \quad (2.13c)$$
```

```
$(\hat{A}_{ij\zeta}, \hat{B}_{ij\zeta}, \hat{D}_{ij\zeta}, \hat{C}_{ij\zeta}) = \int_{-b/2}^{b/2} Q_{0}(z)(1, z, z^{2}, z^{3}) dz \quad (2.13d)$
```

```
$Q_{12}(z) = vQ_{11}(z) \quad (2.13e)$
```

其中 $\kappa$ 是剪切修正因子，之后取值为 5/6。

根据本构关系表达式和应变能公式，功能梯度材料（FGP）弯梁的应变能 $U_f$ 可以给出：

```
$U_f = \frac{1}{2} \int_{\varphi_1}^{\varphi_2} \left[ \left( \frac{A_{11}}{R_{\varphi}^2} + w \frac{\partial w}{\partial t} \right)^2 + 2B_{11} \frac{1}{R_{\varphi}^2} \frac{\partial \varphi}{\partial t} \left( \frac{\partial u}{\partial \varphi} + w \right) + \left( \frac{D_{11}}{R_{\varphi}^2} \frac{\partial \varphi}{\partial t} + A_{55} \frac{1}{R_{\varphi}} \left( \frac{\partial u}{\partial t} - u + \phi \right) \right)^2 \right] R_{\varphi} d\varphi \quad (2.14)$
```

动能 $T$ 为：

```
$T = \frac{1}{2} \int_{\varphi_1}^{\varphi_2} \left[ I_0 \left( \frac{\partial w}{\partial t} \right)^2 + 2I_{01} \frac{\partial w}{\partial t} \frac{\partial \varphi}{\partial t} + I_0 \left( \frac{\partial \varphi}{\partial t} \right)^2 + I_2 \left( \frac{\partial \phi}{\partial t} \right)^2 \right] R_{\varphi} d\varphi \quad (2.15)$
```

其中惯性量项 $I_0, I_1$ 和 $I_2$ 如下：

```
$(I_0, I_1, I_2) = \int_{-h/2}^{h/2} p(z) \left( 1 + \frac{z}{R_{\varphi}} \right)^2 (1, z, z^2) dz \quad (2.16)$
```

FGP 弯梁的边界条件通过在梁两端选择合适的弹簧来实现，其势能可以给出：

```
$U_b = \frac{1}{2} \int_{\varphi_1}^{\varphi_2} \left[ (k_w^2 w^2 + k_{\theta}^2 \theta^2) + (k_u^2 u^2 + k_{\phi}^2 \phi^2) \right] d\varphi \quad (2.17)$
```

此外，为了便于验证，作用于 FGP 弯梁的激励 $F_f$ 平于 z 轴。因此，固定点负载做的功 $W_f$ 给出：

```
$W_f = \dots$
```

## 2.2.3 离散化与求解

基于有限切比多项式的一维无限可微函数 $f(\varphi)$ 的近似表达式为：

```
$f(\varphi) \cong \sum_{n=0}^{N-1} a_n C_n(\varphi) \quad (19a)$
```

```
$C_{N-1}(\varphi) = [\cos(0 \cdot \cos^{-1}(\varphi)), \cos(1 \cdot \cos^{-1}(\varphi)), \dots, \cos((N-1) \cdot \cos^{-1}(\varphi))] \quad (19b)$
```

```
$\mathbf{a} = (a_0, a_1, \dots, a_{N-1})^T \quad (19c)$
```

其中 $N$ 是切比多项式的阶，$\mathbf{a}$ 代表系数向量。将 Gauss-Lobatto 点应用于一维弯梁：

```
$\varphi_i = -\cos\left(\frac{i\pi}{N-1}\right), \quad i=0, 1, \dots, N-1 \quad (220)$
```

离散点的函数值 $f(\varphi)$ 可以得到：

```
$\mathbf{f} = \mathbf{C}\mathbf{a} \quad (221)$
```

其中

```
$\mathbf{f} = [f(\varphi_0), f(\varphi_1), \dots, f(\varphi_{N-1})]^T \quad (222a)$
```

```
$\mathbf{C} = [C_{N-1}(\varphi_0), C_{N-1}(\varphi_1), \dots, C_{N-1}(\varphi_{N-1})]^T \quad (222b)$
```

通过等式 (221) 求导，可以得到表达式：

```
$\mathbf{f}^{(\theta)} = \mathbf{C}\mathbf{D}\mathbf{a} = \mathbf{Q}_{\theta}\mathbf{a} \quad (223)$
```

其中 $\mathbf{D}$ 和 $\mathbf{Q}_{\theta}$ 分别代表切比多项式的阶数阶矩阵。经过低阶切比多项式的递归后，每个切比多项式的导数可以给出：

```
$\mathbf{D}^{(p)} = \left(\frac{1}{s}\mathbf{D}\right)^p \begin{cases} D_{ij} = j-1, & j \text{ even} \\ D_{ij} = 2(j-i), & i>1, i+j \text{ is odd} \\ D_{ij} = 0, & \text{otherwise} \end{cases} \quad (24b)$
```

其中 $s = (\varphi_1-\varphi_0)/2$ 是尺度因子$f(\varphi)$ 的积分表达式写为：

```
$\int_{-1}^1 f(\varphi)d\varphi = \mathbf{v}\mathbf{a} \quad (225)$
```

功能梯度直梁和弯梁的自由与受迫振动，切比多项式的整数向量 $\mathbf{v}$ 可以表示为：

```
$v_k = \begin{cases} \frac{2s}{1-k^2}, & k \text{ even} \\ 0, & k \text{ odd} \end{cases}$
```

乘积积分以矩阵形式表示：

```
$\int_{-1}^1 [f(\varphi)] R_{\theta}(\varphi) d\varphi = \mathbf{f}^T \mathbf{V}_{R_{\theta}} \mathbf{f}$
```

其中

```
$\mathbf{V}_{R_{\theta}} = \text{diag}(\mathbf{R}_{\theta})$
```

$R_{\theta}$ 是 Gauss–Lobatto 离散点的 $R_{\theta}(\varphi)$ 向量。根据通过谱切比方法得到的公式，等式 (2.5) 中的平移和旋转位移函数重写为：

```
$\begin{bmatrix} u \\ v \\ \theta \end{bmatrix} = e^{-j\varphi} \mathbf{C} \begin{bmatrix} c \\ d \\ e \end{bmatrix} = e^{-j\varphi} \mathbf{q}$
```

其中系数 $c, d, e$ 分别是三个方向坐标，$q$ 表示广义坐标。同样，应变、动能、边界弹簧和负载表达式可以重构成矩阵形式。

受到外部负载的 FGP 弯梁能量方程可以表示为：

```
$L = T - (U_e + U_{\theta}) + W_f$
```

将此能量方程代入拉格朗日方程，可以得到矩阵形式的表达式：

```
$(\mathbf{M}\omega^2 - \mathbf{K} - \mathbf{K}_s)\mathbf{q} = \mathbf{F}$
```

其中 $\mathbf{M}$ 和 $\mathbf{K}$ 是系统的质量矩阵和刚度矩阵，$\mathbf{K}_s$ 是刚度矩阵，$\mathbf{F}$ 代表力向量，$\omega$ 表示角频率。具体的向量和矩阵可以表示为：
