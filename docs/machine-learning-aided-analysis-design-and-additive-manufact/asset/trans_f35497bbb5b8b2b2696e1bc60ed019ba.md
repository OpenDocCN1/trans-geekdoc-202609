

![](img/90ed165a39fa708ec438fcda79319c25_114_0.png)

图 4.5 不同边界条件下模态形状随周向波数的变化：(A) C-C; (B) E-E; (C) C-F。

![](img/90ed165a39fa708ec438fcda79319c25_115_0.png)

![](img/90ed165a39fa708ec438fcda79319c25_115_1.png)

**4.6** 不同孔隙率分布下的阶频率孔隙系数：(A) C-C; (B) S-S; (C) E-E。

其中 $n$ 是周向数，$\omega$ 是圆振动频率，$N$ 和 $G$ 分截断的周波数和多项式项；$a_{ng}, b_{ng}, c_{ng}$ 是未知系数；$i = \sqrt{-1}$；$q_w, q_v, q_u$ 是广义坐标，$U, V, W$ 是模态向量。$T_n(\eta)$ 是第一类切比多项式，它具有以下递归表达式：

> $T_0(\eta)=1, T_1(\eta)=\eta, T_n(\eta)=2\eta T_{n-1}(\eta)-T_{n-2}(\eta), g \ge 1$

广义坐标和模态向量的表达式为：

> $q_w = [a_{10}, a_{11}, ..., a_{1G}, a_{N0}, a_{N1}, ..., a_{NG1}]^T \times e^{i\omega_wt}$

> $q_v = [b_{10}, b_{11}, ..., b_{1G}, b_{N0}, b_{N1}, ..., b_{NG1}]^T \times e^{i\omega_vt}$

> $q_u = [c_{10}, c_{11}, ..., c_{1G}, c_{N0}, c_{N1}, ..., c_{NG1}]^T \times e^{i\omega_ut}$

> $U = [T_0(\eta)\cos(\theta), ..., T_G(\eta)\cos(\theta), T_1(\eta)\cos(\theta), ..., T_G(\eta)\cos(\theta)]^T$

功能梯度孔隙圆柱壳的自由与受迫振动

$V = [T_0(\eta)\sin(\theta)]$

$W = [T_0(\eta)\cos(\theta), \dots, T_G(\eta)\cos(\theta), \dots, T_1(\eta)\cos(N), \dots, T_G(\eta)\cos(N)]^T \quad (4.55)$

$J = N(G+1)$.
功能梯度孔隙圆柱壳的拉格朗日方程可以表示为：

$\frac{d}{dr}\frac{\partial \tilde{T}}{\partial \tilde{q}_u} +\frac{\partial (U_z + U_n)}{\partial \tilde{q}_u}}=f_u$

$\frac{d}{dr}\frac{\partial \tilde{T}}{\partial \tilde{q}_v} +\frac{\partial (U_z + U_n)}{\partial \tilde{q}_v}}=f_v \quad (4.56)$

$\frac{d}{dr}\frac{\partial \tilde{T}}{\partial \tilde{q}_w} +\frac{\partial (U_z + U_n)}{\partial \tilde{q}_w}}=f_w$

$f_u, f_v$ 和 $f_w$ 分别是轴向、周向和径向方向的外力矢量。
将等式 (4.7) 和 (4.15) 代入等式 (4.56)，可以导出功能梯度孔隙圆柱壳的控制方程：

$M\dot{q} + C\dot{q} + (K+K_s)q=F(t) \quad (4.57)$

其中

$q = [q_u, q_v, q_w]^T \quad (4.58)$

其中 $M, C, K$, 和 $K_s$ 分别是质量矩阵、阻尼矩阵、结构刚度矩阵和弹簧刚度矩阵。
质量矩阵 $M$ 表示为：

$M = \begin{bmatrix} M_1 & 0 & 0 \\ 0 & M_2 & 0 \\ 0 & 0 & M_3 \end{bmatrix} \quad (4.59)$

其中

$M_1 = \rho_z^2 LR \int_0^{2\pi} UU^T d\eta \quad (4.60)$

$M_2 = \rho^b_{LR} \int_0^{2\pi} \mathbf{VV}^T d\theta\eta \quad (4.61)$

$M_3 = \rho^b_{LR} \int_0^{2\pi} \mathbf{WW}^T d\theta\eta \quad (4.62)$

刚度矩阵 $K$ 表示为：

$K = \begin{bmatrix} \frac{1}{2}K_{11} & \frac{1}{2}K_{12} & \frac{1}{2}K_{13} \\ \frac{1}{2}K_{21} & \frac{1}{2}K_{22} & \frac{1}{2}K_{23} \\ \frac{1}{2}K_{31} & \frac{1}{2}K_{32} & \frac{1}{2}K_{33} \end{bmatrix} \quad (4.63)$
其中

$K_{11} = \frac{L}{R} \int_0^{2\pi} \left( \frac{L}{A_{66}}\frac{\partial U}{\partial\theta} + \frac{R^2 A_{11}}{L^2}\frac{\partial U}{\partial\theta} + \frac{D_{66}}{R^2}\frac{\partial U}{\partial\theta} \right) d\theta\eta \quad (4.64)$

$K_{12} = \frac{L}{R} \int_0^{2\pi} \left( \frac{2RA_{12}}{L}\frac{\partial U}{\partial\theta} + \frac{2RA_{66}}{L}\frac{\partial U}{\partial\theta} - \frac{3D_{66}}{2R}\frac{\partial U}{\partial\theta} \right) d\theta\eta \quad (4.65)$

$K_{13} = \frac{L}{R} \int_0^{2\pi} \left( \frac{2RA_{12}}{L}\frac{\partial U}{\partial\theta} + \frac{2D_{66}}{LR}\frac{\partial U}{\partial\theta} \right) d\theta\eta \quad (4.66)$

$K_{22} = \frac{L}{R} \int_0^{2\pi} \left( A_{22} + \frac{D_{22}}{R^2}\frac{\partial W}{\partial\theta} + \frac{R^2 A_{66}}{L^2}\frac{\partial W}{\partial\theta} + \frac{D_{66}}{4L^2}\frac{\partial W}{\partial\theta} \right) d\theta\eta \quad (4.67)$

$K_{23} = \frac{L}{R} \int_0^{2\pi} \left( \frac{2A_{22}}{L}\frac{\partial V}{\partial\theta} - \frac{2D_{22}}{R^2}\frac{\partial W}{\partial\theta} + \frac{6D_{66}}{L^2}\frac{\partial W}{\partial\theta} - \frac{2D_{12}}{L^2}\frac{\partial V}{\partial\theta} \right) d\theta\eta \quad (4.68)$

$K_{33} = \frac{L}{R} \int_0^{2\pi} \left( A_{22}\mathbf{W}\mathbf{W}^T + \frac{D_{22}}{R^2}\frac{\partial W}{\partial\theta} + \frac{R^2 A_{11}}{L^5}\frac{\partial W}{\partial\theta} + \frac{4D_{60}}{L^2}\frac{\partial W}{\partial\theta} \right) d\theta\eta \quad (4.69)$

功能梯度孔隙圆柱壳的自由与受迫振动

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

### 4.3.2 求解步骤

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

