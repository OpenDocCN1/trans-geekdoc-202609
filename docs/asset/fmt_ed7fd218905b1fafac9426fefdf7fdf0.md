
$K_{33} = \frac{L}{R} \int_0^{2\pi} \left( A_{22}\mathbf{W}\mathbf{W}^T + \frac{D_{22}}{R^2}\frac{\partial W}{\partial\theta} + \frac{R^2 A_{11}}{L^5}\frac{\partial W}{\partial\theta} + \frac{4D_{60}}{L^2}\frac{\partial W}{\partial\theta} \right) d\theta\eta \quad (4.69)$

# 功能梯度孔隙圆柱壳的自由与受迫振动

弹簧刚度矩阵 $\mathbf{K}_s$ 表示为：

$\mathbf{K}_s = \begin{bmatrix} \mathbf{K}_{s11} & 0 & 0 \\ 0 & \mathbf{K}_{s22} & 0 \\ 0 & 0 & \mathbf{K}_{s33} \end{bmatrix} \quad (4.70)$

其中

$\mathbf{K}_{s11} = \int_{0}^{2\pi} (k_1^0 U(0)T(0) + k_1^1 U(1)T(1))R d\theta \quad (4.71)$

$\mathbf{K}_{s22} = \int_{0}^{2\pi} (k_2^0 V(0)V^T(0) + k_2^1 V(1)V^T(1))R d\theta \quad (4.72)$

$\mathbf{K}_{s33} = \int_{0}^{2\pi} [k_3^0 W(0)W^T(0) + k_3^1 W(1)W^T(1) + \frac{k_3^0}{L_2^2}\frac{\partial W(0)}{\partial\eta}\frac{\partial W(0)}{\partial\eta} + \frac{k_3^1}{L_2^2}\frac{\partial W(1)}{\partial\eta}\frac{\partial W(1)}{\partial\eta}] R d\theta \quad (4.73)$

$\mathbf{C} = \alpha\mathbf{M} + \beta\mathbf{K} \quad (4.74)$

其中 $\alpha$ 和 $\beta$ 代表阻尼系数，由给出：

$\alpha = 2 \left( \frac{\xi_u}{\omega_u} - \frac{\xi_v}{\omega_v} \right) \left( \frac{1}{\omega_u^2} - \frac{1}{\omega_v^2} \right) \quad (4.75)$

$\beta = 2 \left( \frac{\xi_u}{\omega_u} - \frac{\xi_v}{\omega_v} \right) \left( \frac{1}{\omega_u^2} - \frac{1}{\omega_v^2} \right)$

其中 $\omega_u, \omega_v$ 是阶频率，$\xi_u, \xi_v$ 是阻尼比。单点激励作用于 $(\eta, \theta_0)$ 可以表示为：

$F(t) = [f_u, f_v, f_w]^T \quad (4.76)$

其中 $f_{ex}$ 是激励幅度。

通过等式 (4.57) 得到稳态响应，功能梯度孔隙圆柱壳的瞬态响应会衰减，由于阻尼的存在，稳态分析更为重要。在本节中，

## 4.3.2 求解步骤

功能梯度圆柱壳的频率响应由下给出：

$\mathbf{H} = (\mathbf{K} + \mathbf{C}/\mathbf{M})^{-1} \quad (4.77)$

根据模态的正交性，等式 (4.78) 可以得到：

$\mathbf{Q}^T\mathbf{M} = \mathbf{I} \quad (4.78)$

$\mathbf{Q}^T(\mathbf{K} + \mathbf{C}/\mathbf{M}) = \text{diag}(\omega_1^2, \dots, \omega_n^2) \quad (4.79)$

其中 $\mathbf{I}$ 是单位矩阵，$\omega_n$ 是频率。频率响应矩阵表示为：

$H_{ij}(\omega) = \sum_{n=1}^{NT} \frac{q_{in}q_{jn}}{\omega_n^2 - \omega^2 + i\dots} \quad (4.80)$

其中 $NT$ 是实际计算中的截断模数。

事实上，模态 $q_i$ 是位移函数的未知系数，表示为：

$\mathbf{q}_i = \begin{bmatrix} a_{10} & a_{11} & \dots & a_{1G} & a_{N0} & a_{N1} & \dots & a_{NG1} \\ b_{10} & b_{11} & \dots & b_{1G} & b_{N0} & b_{N1} & \dots & b_{NG1} \\ c_{10} & c_{11} & \dots & c_{1G} & c_{N0} & c_{N1} & \dots & c_{NG1} \end{bmatrix}^T \quad (4.81)$

值得注意的是，任意点 $p$ 与响应点 $q$ 之间的频率响应。通常，功能梯度圆柱壳的径向响应与其他方向受到关注。构造激励点和响应点的模态基于径向位移函数，其表示如下：

$\q_i^a = \sum_{e=0}^G T_{ie}^a(r_p)\cos(\theta_e), \sum_{e=0}^G T_{ie}^a(r_p)\cos(2\theta_e), \dots, \sum_{e=0}^G T_{ie}^a(r_p)\cos(G\theta_e)$

$\q_i^b = \sum_{e=0}^G T_{ie}^b(r_p)\cos(\theta_e), \sum_{e=0}^G T_{ie}^b(r_p)\cos(2\theta_e), \dots, \sum_{e=0}^G T_{ie}^b(r_p)\cos(G\theta_e) \quad (4.82)$

功能梯度多孔圆柱壳的自由振动与受迫振动

其中 $\eta_p$，$\theta_p$ 代表与激励点相关的坐标值，$\eta_q$，$\theta_q$ 代表与响应点相关的坐标值。因此，可以得到 FG 多孔圆柱壳相应激励点与响应点之间的频率响应：

```
$H_p^q(\omega) = \sum_{i=1}^{NT} \frac{-\omega^2 q_i^T}{\omega_i^2 + (\alpha\beta\omega_i)^2 - \omega^2} \quad (4.83)$
```

需要注意的是，由公式(4.83)得到的频率响应是一个复函数。FG 多孔圆柱壳在任何激励函数下的响应值通过取其绝对值得到。

## 4.3.3 结果与讨论

本节中 FG 多孔圆柱壳的几何和材料参数与第 4.2 节相同。首先

![](img/90ed165a39fa708ec438fcda79319c25_120_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_121_0.png)

**图 4.8** 具有 C-C 边界条件的圆柱壳有限元模型。

![](img/90ed165a39fa708ec438fcda79319c25_121_1.png)

**图 4.9** 与 FEM 频率响应的对比。

在固定边界条件下，齐质圆柱壳方法（FEM）的频率响应与使用 ANSYS 软件的有限元法的对比如图 4.8 所示，其中采用了 SHELL 281 单元。单元数量为 900，节点数为 2820。模态阻尼比 $\zeta_i$ 和 $\zeta_n$ 设置为 0.02。节点在左右边缘受到连续约束以模拟固定条件。频率响应的对比如图 4.9 所示。可以观察到本文方法得到的频率响应与 FEM 良好一致，验证了本文方法的准确性。

# 功能梯度多孔圆柱壳的自由振动与受迫振动

![](img/90ed165a39fa708ec438fcda79319c25_122_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_122_1.png)

![](img/90ed165a39fa708ec438fcda79319c25_122_2.png)

**图 4.10** 不同阻尼比（$\epsilon_i=0.2$）下功能梯度多孔壳跨跨 ($\eta=1/2$，$\theta=0$)的频率响应：(A) C-C；(B) S-S；(C) E-E。

阻尼对 FG 多孔壳在径向谐波激励下振动响应的影响如图*图 4.10*所示。考虑了包括 C-S、S-E 和 E-E 在内的不同边界条件，在本讨论中采用 $k_s=10^3$ 作为 E-E 边界条件。如图 4.10 所示，由于阻尼衰减的存在，共振幅值降低。阻尼增加一倍并不能导致幅衰衰一倍。也就是说，随着阻尼值的增加，阻尼对共振响应的影响降低。另一个观察结果是阻尼对非共振区域的响应没有影响。

为了说明孔隙率系数对频率响应的影响

FG 复合结构

![](img/90ed165a39fa708ec438fcda79319c25_123_0.png)

**图 4.11** 不同孔隙率系数（C-C）下功能梯度多孔壳跨跨 ($\eta = 1/2$， $\theta = 0$)的频率响应：(A) PD-A；(B) PD-B；(C) PD-U。

## 4.4 非线性振动

### 4.4.1 控制方程

根据 Don 壳理论，FG 圆壳的应变分量形式如下：

```
$\varepsilon_{xx} = \varepsilon_{xx}^0 + z\varepsilon_{xx}^1$
$\varepsilon_{00} = \varepsilon_{00}^0 + z\varepsilon_{00}^1$
$\gamma_{x0} = \gamma_{x0}^0 + z\gamma_{x0}^1$
```

其中 $\varepsilon_{xx}^0, \varepsilon_{00}^0, \gamma_{x0}^0$ 是中面应变；$\varepsilon_{xx}^1, \varepsilon_{00}^1, \gamma_{x0}^1$ 是中面曲率。它们的表达式如下：

功能梯度多孔壳的自由振动

![](img/90ed165a39fa708ec438fcda79319c25)

**图 4.12** 不同边界条件（(A) PD-A；(B) PD-B；(C) PD-U）下跨跨 ($\eta = 1/2$, $\theta = 0$) 功能梯度多孔壳的频率。

![](img/90ed165a39fa708ec438fcda79319c25)

```
$H_p^q(\omega) = \sum_{i=1}^{NT} \frac{-\omega^2 q_i^T}{\omega_i^2 + (\alpha\beta\omega_i)^2 - \omega^2} \quad (4.83)$
```

功能梯度多孔壳的受迫振动

```
$\begin{aligned}
\varepsilon_{xx} = \varepsilon_{xx}^0 + z\varepsilon_{xx}^1 \\
\varepsilon_{00} = \varepsilon_{00}^0 + z\varepsilon_{00}^1 \\
\gamma_{x0} = \gamma_{x0}^0 + z\gamma_{x0}^1
\end{aligned}
```

其中 $\varepsilon_{xx}^0, \varepsilon_{00}^0, \gamma_{x0}^0$ 是中面应变；$\varepsilon_{xx}^1, \varepsilon_{00}^1, \gamma_{x0}^1$ 是中面曲率。它们的表达式为：

```
$\begin{aligned}
\varepsilon_{xx} &= \varepsilon_{xx}^0 + z\varepsilon_{xx}^1 \\
\varepsilon_{00} &= \varepsilon_{00}^0 + z\varepsilon_{00}^1 \\
\gamma_{x0} &= \gamma_{x0}^0 + z\gamma_{x0}^1
\end{aligned}
```

应力-应变关系为：

```
$\begin{aligned}
\sigma_{xx} &= Q_{11}\varepsilon_{xx} + Q_{12}\varepsilon_{00} + Q_{16}\gamma_{x0} \\
\sigma_{\theta} &= Q_{12}\varepsilon_{xx} + Q_{22}\varepsilon_{00} + Q_{26}\gamma_{x0} \\
\tau_{x\theta} &= Q_{16}\varepsilon_{xx} + Q_{26}\varepsilon_{00} + Q_{66}\gamma_{x0}
\end{aligned}
```

内力和矩为：

```
$\begin{aligned}
N_{xx} &= \int_{-z_0}^{z_0} \sigma_{xx} dz \\
N_{\theta} &= \int_{-z_0}^{z_0} \sigma_{\theta} dz \\
N_{x\theta} &= \int_{-z_0}^{z_0} \tau_{x\theta} dz \\
M_{xx} &= \int_{-z_0}^{z_0} z\sigma_{xx} dz \\
M_{\theta} &= \int_{-z_0}^{z_0} z\sigma_{\theta} dz \\
M_{x\theta} &= \int_{-z_0}^{z_0} z\tau_{x\theta} dz
\end{aligned}
```

将公式(4.84–4.86)代入公式(4.87)，得到：

```
$\begin{aligned}
N_{xx} &= A_{11}\varepsilon_{xx} + A_{12}\varepsilon_{00} + A_{16}\gamma_{x0} \\
N_{\theta} &= A_{12}\varepsilon_{xx} + A_{22}\varepsilon_{00} + A_{26}\gamma_{x0} \\
N_{x\theta} &= A_{16}\varepsilon_{xx} + A_{26}\varepsilon_{00} + A_{66}\gamma_{x0} \\
M_{xx} &= B_{11}\varepsilon_{xx} + B_{12}\varepsilon_{00} + B_{16}\gamma_{x0} \\
M_{\theta} &= B_{12}\varepsilon_{xx} + B_{22}\varepsilon_{00} + B_{26}\gamma_{x0} \\
M_{x\theta} &= B_{16}\varepsilon_{xx} + B_{26}\varepsilon_{00} + B_{66}\gamma_{x0}
\end{aligned}
```

FG 多孔壳的应变能 $U_r$ 和动能 $T$ 为：

```
$U_r = \int_{-z_0}^{z_0} \frac{1}{2} [Q_{11}\varepsilon_{xx}^2 + Q_{22}\varepsilon_{\theta\theta}^2 + 2Q_{12}\varepsilon_{xx}\varepsilon_{\theta\theta} + Q_{66}\gamma_{x\theta}^2] dz \quad (4.90)$
```

```
$T = \int_{-z_0}^{z_0} \frac{1}{2} \rho (\dot{U}^2 + \dot{V}^2 + \dot{W}^2) dz \quad (4.91)$
```

$$k_{31} = \frac{(B_{12}+2B_{60})L^2mn\pi^2+A_{12}m^2\piR+B_{11}m^3\pi^2}{L^3\rho^2} \quad (4.104)$$

$$k_{32} = \frac{B_{11}L^2n^3+A_{11}L^2n^2+(B_{12}+2B_{60})mn^2\pi^2}{L^3\rho^2} \quad (4.105)$$

$$k_{33} = \frac{L^2[2B_{21}L^2n^5+A_{11}L^2n^2+2m\pi^2(D_{12}n^2+D_{60}n^2+B_{12}R)] + \frac{D_{11}(L^2n^4+m^4\pi^4)}{L^4R^4\rho^2} \quad (4.106)$$

$$k_{34} = \frac{9A_{11}(L^2n^4+m^4\pi^4)+(A_{12}+4A_{60})L^2mn^2\pi^2}{32L^4\rho^2} \quad (4.107)$$

忽略在横向振动中微不足道的惯性项 $\rho\ddot{u}$ 和 $\rho\ddot{v}$，我们可以通过结合方程 (4.95) 和方程 (4.96) 来求解 $u_i$ 和 $v_i$。将结果代入方程 (4.97)，得到：

$$\frac{\ddot{w}_i}{t^2} + a_1w_i + a_3w_i^3 = 0 \quad (4.108)$$

其中

$$a_1 = \frac{k_{13}k_{22}k_{31}}{k_{12}k_{21}-k_{11}k_{22}} - \frac{k_{12}k_{23}k_{31}}{k_{12}k_{21}-k_{11}k_{22}} - \frac{k_{13}k_{21}k_{32}}{k_{12}k_{21}-k_{11}k_{22}} + \frac{k_{12}k_{23}k_{32}}{k_{12}k_{21}-k_{11}k_{22}} - k_{33} \quad (4.109)$$

$$a_3 = k_{34} \quad (4.110)$$

### 4.4.2 求解步骤

线性惯性得为：

$$\omega = \sqrt{a_1} \quad (4.111)$$

初始条件定义为：
