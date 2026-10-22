
具有正的 \(N_B^2\)。我们将在后面关于对流不稳定性的讨论中再次回到这个频率。当磁场非零时，(6.169) 变为

```
\frac{d}{dz}\left[(\gamma\rho_0+B_0^2)\rho_0(\omega^2-\omega_A^2)(\omega^2-\frac{\gamma\rho_0\omega_A^2}{\gamma\rho_0+B_0^2}\omega^2)\frac{d\hat{\xi}}{dz}\right]/\left[\rho_0\omega^4-k_0^2(\gamma\rho_0+B_0^2)(\omega^2-\frac{\gamma\rho_0\omega_A^2}{\gamma\rho_0+B_0^2}\omega^2)\frac{d\hat{\xi}}{dz}\right]+\left[\rho_0(\omega^2-\omega_A^2)-\frac{k_0^2\rho_0^2g^2(\omega^2-\omega_A^2)}{\rho_0\omega^4-k_0^2(\gamma\rho_0+B_0^2)(\omega^2-\frac{\gamma\rho_0\omega_A^2}{\gamma\rho_0+B_0^2}\omega^2)}\right]\hat{\xi}+\frac{d}{dz}\left\{\rho_0g-\frac{\rho_0^2g\omega^2(\omega^2-\omega_A^2)}{\rho_0\omega^4-k_0^2(\gamma\rho_0+B_0^2)(\omega^2-\frac{\gamma\rho_0\omega_A^2}{\gamma\rho_0+B_0^2}\omega^2)}\right\}\hat{\xi}=0
```

其中 \( \omega_A = \mathbf{k} \cdot \mathbf{B}_0 / \sqrt{\rho_0 \mu_0} \) 为阿尔芬角频率。我们可以通过令 \( B_0 = 0 \) 来验证，这意味着 \( \omega_A = 0 \)，我们将回到 (6.172)。对于不可压缩等离子体（即 \( \gamma \to \infty \)），我们可以假设 \( \rho_0 |\omega|^2 \ll k_0^2 (\gamma \rho_0 + B_0^2) \)。可以验证 (6.172) 化简为

```
\frac{d}{dz}\left[\rho_0(\omega^2-\omega_A^2)\frac{d\hat{\xi}}{dz}\right]-k_0^2\left[\rho_0(\omega^2-\omega_A^2)-\frac{\rho_0^2g^2}{\gamma\rho_0+B_0^2}-\frac{d\rho_0}{dz}g\right]\hat{\xi}=0
```

```
\frac{d}{dz}\left[\rho_0(\omega^2-\omega_A^2)\frac{d\hat{\xi}}{dz}\right]-k_0\rho_0\left[(\omega^2-\omega_A^2)-N_M^2\right]\hat{\xi}=0
```

```
N_M^2=-\frac{1}{\rho_0}\left(\frac{\rho_0^2g^2}{\gamma\rho_0+B_0^2}+\frac{d\rho_0}{dz}g\right)
```

是磁修正的布伦特-瓦伊萨拉频率，因为它现在包含了磁贡献。

## 示例：笛卡尔坐标系中分层静止等离子体的 MHD。

由于平衡条件与静态和静止等离子体相同，这意味着在用 \( \tilde{\omega}(z) \) 替换 \( \omega \) 后，(6.169) 至 (6.176) 中的方程对静止等离子体仍然有效。

对于不可压缩磁化等离子体（即 \( \gamma \to \infty \)），例如，(6.176) 变为

```
\frac{d}{dz}\left[\rho_0(\tilde{\omega}^2-\omega_A^2)\frac{d\hat{\xi}}{dz}\right]-k_0^2\left[\rho_0(\tilde{\omega}^2-\omega_A^2)+\frac{\rho_0^2g^2}{\gamma\rho_0+B_0^2}+\frac{d\rho_0}{dz}g\right]\hat{\xi}=0
```

```
\Pi=\frac{\rho_0}{k_0^2}(\tilde{\omega}^2-\omega_A^2)\frac{d\hat{\xi}}{dz}
```

其中 \tilde{\omega}(z) = \omega - \Omega_0(z), \Omega_0(z) = \boldsymbol{k}_0 \cdot \boldsymbol{v}(z), \boldsymbol{k}_0 = [k_x, k_y, 0]^T 为水平波矢，阿尔芬角频率为 \omega_A = \boldsymbol{k}_0 \cdot \boldsymbol{B}_0 / \sqrt{\rho_0 \mu_0}。这为新的流动驱动（开尔文-亥姆霍兹）不稳定性提供了可能性，我们将在后面讨论。当密度恒定且 \rho_0^2 g_0^2 \ll k_0^2(\gamma p_0 + B_0^2) 时，(6.176) 进一步化简为

$$\frac{d^2 \hat{\xi}}{dz^2} - k_0^2 \hat{\xi} = 0 \ .$$
(6.178)

对于两个半空间的情况，上半空间表示区间 [0, +\infty]，下半空间表示区间 (-\infty,0]，在 z = 0 处有描述法向速度连续性和压力平衡的两个边界条件；即，

$$\left[ \boldsymbol{n} \cdot \hat{\boldsymbol{\xi}} \right]_1^2 = 0 \quad \text{and} \quad \left[ \Pi + \boldsymbol{n} \cdot \boldsymbol{\xi} \, \boldsymbol{n} \cdot \nabla \left( p + \frac{B^2}{2\mu_0} \right) \right]_1^2 = 0 \ ,$$
(6.179)

其中 \boldsymbol{n} 表示半空间界面上的法向量。注意天体通常处于流体静力平衡，这意味着剖面：p(z)、B_x(z) 和 B_y(z) 满足如下关系：

$$\frac{d}{dz} \left[ p(z) + \frac{B^2(z)}{2\mu_0} \right] = -\rho g \ .$$
(6.180)

## 示例：圆柱坐标系中的分层 MHD。

让我们考虑圆柱坐标 \boldsymbol{r} = [r, \theta, z]^T 中的 Frieman-Rotenberg 形式主义，在一维圆柱平衡中，由密度 \rho(r)、压力 p(r)、磁场分量 B_\theta(r) 和 B_z(r) 或 \boldsymbol{B} = [0, B_\theta(r), B_z(r)]^T 以及速度分量 v_\theta(r) 和 v_z(r) 或 \boldsymbol{v} = [0, v_\theta(r), v_z(r)]^T 描述。平衡仅受径向坐标 r 上一个微分方程的限制。引力势 \Psi(r) 被认为是由位于轴 r = 0 上的致密天体产生的。由于圆柱对称性，我们考虑如下形式的法向模的傅里叶分量

$$\boldsymbol{\xi}(r, \theta, z) = [\xi_r(r), \xi_\theta(r), \xi_z(r)]^T \exp[ i (m\theta + kz - \omega t)] \ .$$
(6.181)

圆柱等离子体的谱方程为（例如，Bondeson et al., 1987）

$$\boldsymbol{F}(\boldsymbol{\xi}) - \underbrace{\left[ \left( \frac{\rho_0 v_\theta^2}{r} \right) \nabla \cdot \boldsymbol{\xi} + r \frac{d}{dr} \left( \frac{\rho_0 v_\theta^2}{r^2} \right) \xi_r \right] \boldsymbol{i}_r}_{\sim \text{centrifugal force}} + 2 i \rho \tilde{\omega} \left( \frac{v_\theta}{r} \right) \boldsymbol{i}_z \times \boldsymbol{\xi} + \rho \tilde{\omega}^2 \boldsymbol{\xi} = \boldsymbol{0},$$
(6.182)

其中

$$\tilde{\omega} = \omega - \Omega_0 = \omega - \underbrace{\frac{m v_\theta}{r}}_{\text{Coriolis}} - k v_z \ .$$
(6.183)

注意在圆柱坐标中，谱方程变得更加复杂，因为 $\mathbf{v}\cdot\nabla\mathbf{v}$ in (6.160) 现在产生离心加速度，而算子 $\mathbf{v}\cdot\nabla$ 在 (6.166) 中给频率带来额外的科里奥利贡献。还要注意在没有旋转的情况下，$v_\theta = 0$，简单的“准静态”形式 $\mathbf{F}(\boldsymbol{\xi}) = -\rho\tilde{\omega}^2\boldsymbol{\xi}$ 再次得到。

假设等离子体不可压缩，$\nabla\cdot\boldsymbol{\xi}=0$，位移局限于盘面，$v_z = 0$（即纯方位角速度场），且垂直磁场为零，$B_\theta = 0$。此外，我们仅将分析限制在垂直波数 $k$ 上；即 $m = 0$。这些假设适用于吸积盘，我们将在后面讨论。谱问题随后简化为求解

$$r\frac{d}{dr}\left(\frac{1}{r}\frac{d\chi}{dr}\right)-k^2\left[1-\frac{\kappa^2(r)}{\omega^2-\omega_A^2}-\frac{4\omega_A^2\Omega^2(r)}{(\omega^2-\omega_A^2)^2}\right]\chi=0\tag{6.184}$$

其中

$$\chi = r\xi\;,\quad \Omega = \frac{v_\theta}{r}\;,\text{ and }\kappa^2 = \frac{1}{r^3}\frac{d\left(r^4\Omega^2\right)}{dr}=2r\Omega\frac{d\Omega}{dr}+4\Omega^2\;,\tag{6.185}$$

在边界条件 $\xi(r_1)=\xi(r_2)=0$ 下。注意天体通常处于流体静力平衡。圆柱坐标平衡意味着剖面：$p(r)$、$B_\theta$ 和 $B_z(r)$ 满足如下关系：

$$\frac{d}{dr}\left[p(r)+\frac{B^2(r)}{2\mu_0}\right]+\frac{B_\theta^2(r)}{r}=\rho\frac{v_\theta^2(r)}{r}-\rho g\;.\tag{6.186}$$

因此，$\rho(r)$、$p(r)$、$v_\theta(r)$、$B_\theta$ 和 $B_z(r)$ 彼此相关。仅分量 $v_z(r)$ 可以任意选取。注意分层等离子体的线性化 MHD 方程在 1D 情况下，无论坐标系如何，都可以写成如下形式的常微分方程（ODEs）：

$$\frac{d}{d\alpha}\left[P(\alpha;\omega^2)\frac{d\xi}{d\alpha}\right]+Q(\alpha;\omega^2)\xi=0\;,\tag{6.187}$$

其中 $\alpha$ 可以是 $z$、$y$、$x$ 和 $r$。存在非常高效的数值程序来积分 n 个非线性一阶微分方程组。因此，将上述二阶 ODE 转化为两个一阶（线性）ODE 系统的学习练习是有用的。

## 6.4.2. 引力坍缩

星系包含巨分子云（GMCs）。这些云的稳定性由自引力将物质拉入与内部云压将物质推出的平衡来保证。当云压超过引力时，会发生振荡（声波）。当引力克服云压时，云坍缩。例如，云中的微小扰动可能导致其指数增长并变得不稳定。这导致云的坍缩，从而产生恒星形成。Jeans 不稳定性描述了自引力云中的引力不稳定性。我们此处的目标是推导这种不稳定性。其他
