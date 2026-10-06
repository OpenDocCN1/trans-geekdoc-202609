
功能梯度多孔圆柱壳的自由与自由振动

应变向量 $\varepsilon$ 表示为：

$$\varepsilon = [\varepsilon_x, \varepsilon_{\theta}, \varepsilon_{x\theta}, \kappa_x, \kappa_{\theta}, \kappa_{x\theta}]^T \quad (4.9)$$

其中 $\varepsilon_x, \varepsilon_{\theta}$ 表示中面应变，$\kappa_x, \kappa_{\theta}$ 表示中面曲率。根据 Sanders 理论，中面的应变-位移关系和曲率变化可以表示为：

$$\varepsilon_x = \frac{\dot{u}}{L\eta}$$
$$\varepsilon_{\theta} = \frac{1}{R}\frac{dw}{d\theta} - \frac{w}{R}$$
$$\varepsilon_{x\theta} = \frac{1}{R}\frac{du}{d\theta} + \frac{\dot{v}}{L\eta} \quad (4.10)$$

$$\kappa_x = -\frac{\ddot{w}}{L^2\eta^2}$$
$$\kappa_{\theta} = -\frac{1}{R^2}\frac{\partial^2w}{d\theta^2} - \frac{1}{R}\frac{\dot{w}}{R}$$
$$\kappa_{x\theta} = -\frac{1}{R^2}\frac{\partial^2u}{d\theta^2} + \frac{2}{RL}\frac{\partial v}{d\theta} - \frac{2}{RL}\frac{\dot{\eta}}{R\eta} \quad (4.11)$$

等式 (4.8) 中的应力矩阵 $S$ 给出：

$$\begin{bmatrix} A_{11} & A_{12} & 0 & B_{11} & B_{12} & 0 \\ A_{12} & A_{22} & 0 & B_{12} & B_{22} & 0 \\ 0 & 0 & A_{66} & 0 & 0 & B_{66} \\ B_{11} & B_{12} & 0 & D_{11} & D_{12} & 0 \\ B_{12} & B_{22} & 0 & D_{12} & D_{22} & 0 \\ 0 & 0 & 0 & D_{66} & 0 & D_{66} \end{bmatrix} \quad (4.12)$$

其中 $A_{ij}, B_{ij}$ 和 $D_{ij}$ ($i, j=1, 2, 6$) 分别表示拉伸矩阵、拉伸-耦合矩阵和弯曲矩阵的元素。它们的定义为：

$$A_{ij} = \int_{-h/2}^{h/2} Q_{ij}dz, B_{ij} = \int_{-h/2}^{h/2} zQ_{ij}dz, D_{ij} = \int_{-h/2}^{h/2} z^2Q_{ij}dz \quad (4.13)$$

等式 (4.13) 中的 $Q_{ij}$ 是应力-应变矩阵元素，可以通过以下方式确定：

$$Q_{11} = Q_{22} = \frac{E(z)}{1-\mu(z)^2}, Q_{12} = \frac{\mu(z)E(z)}{1-\mu(z)^2}, Q_{66} = \frac{E(z)}{2(1+\mu(z))} \quad (4.14)$$

在壳两端实现的人工弹簧用于模拟任意边界条件。边界人工弹簧的势能表示为：

$$U_b = \frac{1}{2}\int_{0}^{2\pi} \left\{ k_u^2[u(0, \theta, t)]^2 + k_v^2[v(0, \theta, t)]^2 + k_w^2[w(0, \theta, t)]^2 + k_{\rho}^2\left[\frac{\Delta w(0,t)}{L_z}\right]^2 \right\} d\theta$$
+ \frac{1}{2}\int_{0}^{2\pi} \left\{ k_{\theta}^2[u(1, \theta, t)]^2 + k_{\phi}^2[v(1, \theta, t)]^2 + k_w^2[w(1, \theta, t)]^2 + k_{\rho}^2\left[\frac{\Delta w(1,t)}{L_z}\right]^2 \right\} d\theta \quad (4.15)$$

## 4.2.2 求解步骤

FG 圆柱壳在周向方向的模式定义为谐函数，轴向模式选择为多项式。则位移函数可以表示为：

$$u(\eta, \theta, t) = \cos(n\theta+\omega t)U(\eta)$$
$$v(\eta, \theta, t) = \sin(n\theta+\omega t)V(\eta)$$
$$w(\eta, \theta, t) = \cos(n\theta+\omega t)W(\eta) \quad (4.16)$$

其中 $\omega$ 是圆频率，$n$ 是周向波数。用切比夫多项式表示的轴向模式函数 $U(\eta), V(\eta)$ 和 $W(\eta)$ 可以写为：

$$U(\eta) = \sum_{g=0}^{NT} a_g \varphi_g(\eta)$$
$$V(\eta) = \sum_{g=0}^{NT} b_g \varphi_g(\eta)$$
$$W(\eta) = \sum_{g=0}^{NT} c_g \varphi_g(\eta) \quad (4.17)$$

其中 $NT$ 是截断阶；$a_g, b_g$ 和 $c_g$ 是未知系数；$\varphi_g(\eta), \varphi_g(\eta)$, 和 $\varphi_g(\eta)$ 是第一类切比夫多项式，其递推关系为：

$$\varphi_0(\eta) = 1, \varphi_1(\eta) = \eta, \varphi_{g+1}(\eta) = 2\eta\varphi_g(\eta) - \varphi_{g-1}(\eta), g \ge 1 \quad (4.18)$$

坐标从 $\eta$ 到 $2\eta-1$ 的变换对于应用切比夫多项式是必要的，因为切比夫多项式定义在区间 $[-1, 1]$ 之间。一旦获得了能量表达式和许函数，便采用 Ritz 方法推导出 FG 多孔壳的特征值方程。

将等式 (4.16) 代入等式 (7)，FG 多孔壳的动能 $T$ 可以表示为：

$$T = \frac{\pi LR}{2} \rho_0^2 \int_{0}^{L} (U^2 + V^2 + W^2) d\eta \quad (19)$$
其中
$$\rho_0^2 = \int_{-L}^{L} \rho(z) dz \quad (20)$$

同样，将等式 (4.16) 代入等式 (8)，FG 多孔壳的应变能通过：

$$U_\epsilon = \frac{\pi L}{2} \int_{-L}^{L} \left( n^2 A_{66} U^2 + \frac{R^2 A_{11}}{L^2} V^2 + 2n \left(\frac{RA_{12}}{L} + \frac{B_{12}}{L}\right) U' V' - 2n \left(\frac{RA_{66}}{L} + \frac{B_{06}}{L}\right) U' V' + 2n \left(\frac{n^2 B_{12}}{L} + \frac{RA_{12}}{L}\right) U' W' + \frac{4n^2 B_{66}}{L} UW' - \frac{R^2 B_{66}}{L^3} U' V' + n^2 \left(\frac{A_{22}}{R} + \frac{D_{22}}{R^2}\right) V^2 + \left(\frac{D_{66}}{L} + \frac{2RB_{66}}{L^2}\right) V' W' + 4n \left(\frac{RB_{66}}{L^2} + \frac{B_{06}}{L}\right) V' W'' - 2n \left(\frac{n^2 B_{12}}{L^2} + \frac{RB_{12}}{L}\right) V' W'' + 2n \left(\frac{n^2 B_{22}}{R} + \frac{D_{22}}{R^2}\right) W' W'' + A_{22} \frac{2n^2 B_{22}}{R} + \frac{n^2 D_{06}}{R^2} W^2 + 4n^2 \frac{D_{06}}{L^2} W^2 - \frac{R^2 D_{11}}{L^4} W'' - 2n \left(\frac{n^2 B_{12}}{L^2} + \frac{RB_{12}}{L}\right) WW'' \right) d\eta \quad (21)$$

然后，将等式 (4.16) 代入等式 (15)，边界势能可以写为：

$$U_b = \frac{\pi R}{2} \left\{ k_u^2[U(0)]^2 + k_v^2[V(0)]^2 + k_w^2[W(0)]^2 + k_{\theta}^2\left[\frac{W(0)}{L_{\eta}}\right]^2 \right\} + \frac{\pi R}{2} \left\{ k_u^2[U(1)]^2 + k_v^2[V(1)]^2 + k_w^2[W(1)]^2 + k_{\theta}^2\left[\frac{W(1)}{L_{\eta}}\right]^2 \right\} \quad (22)$$

具有任意条件的 FG 多孔圆柱壳的拉朗日函数定义为：

$$\Pi = T - U_c - U_s \quad (23)$$

应用标准 Ritz 程序对未知系数最小化 $\Pi$，可以得到表达式 (24)：

$$\frac{\partial \Pi}{\partial a_g}=0, \frac{\partial \Pi}{\partial b_g}=0, \frac{\partial \Pi}{\partial c_g}=0, \dots, NT \quad (24)$$

因此产生了特征值方程：

$$\omega^2 \mathbf{M} \mathbf{q} - \mathbf{K} \mathbf{q} = \mathbf{K}_s \quad (25)$$

其中 $\mathbf{q} = [\mathbf{a}_g, \mathbf{b}_g, \mathbf{c}_g]^T$ 是 Ritz 向量，$\mathbf{a}_g = [a_1, a_2, \dots, a_{NT}]$, $\mathbf{b}_g = [b_1, b_2, \dots, b_{NT}]$, 以及 $\mathbf{c}_g = [c_1, c_2, \dots, c_{NT}]$。

质量矩阵 $\mathbf{M}$ 的表达式为：

$$\mathbf{M} = \begin{bmatrix} M_{aa} & M_{ab} \\ M_{ac} & M_{bc} \end{bmatrix} \quad (26)$$

其中
$$M_{aa}(p, q) = \rho_L^{LR} \int_{0}^{1} \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (27)$$
$$M_{ab}(p, q) = \rho_L^{LR} \int_{0}^{1} \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (28)$$
$$M_{bc}(p, q) = \rho_L^{LR} \int_{0}^{1} \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (29)$$

刚度矩阵 $\mathbf{K}$ 的表达式为：

$$\mathbf{K} = \begin{bmatrix} K_{aa} & K_{ab} & K_{ac} \\ K_{ba} & K_{bb} & K_{bc} \\ K_{ca} & K_{cb} & K_{cc} \end{bmatrix} \quad (4.30)$$

其中
$$K_{aa}(p, q) = \frac{L}{R} \int_{0}^{L} \left[ n^2 A_{66} - \frac{n^2 B_{66}}{R} + \frac{n^2 D_{66}}{4R^2} \right] \varphi_p(\eta)\varphi_q(\eta) + \frac{R^2 A_{11}}{L^2} \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (31)$$
$$K_{ab}(p, q) = \frac{L}{R} \int_{0}^{L} \left( \frac{n^2 B_{12}}{L} - \frac{RA_{12}}{L} \right) \varphi_p(\eta)\varphi_q(\eta) + \frac{3nD_{66}}{L} \left( \frac{RA_{66}}{L} - \frac{B_{66}}{L} \right) \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (32)$$
$$K_{ac}(p, q) = \frac{L}{R} \int_{0}^{L} \left[ \left( \frac{RA_{12}}{L} + \frac{B_{12}}{L} \right) \varphi_p(\eta)\varphi_q(\eta) + \left( \frac{n^2 D_{66}}{L} - \frac{2n^2 B_{66}}{L} \right) \varphi_p(\eta)\varphi_q(\eta) \right] - \frac{R^2 B_{11}}{L^3} \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (33)$$
$$K_{ba}(p, q) = \frac{L}{R} \int_{0}^{L} \left[ \left( \frac{RA_{12}}{L} + \frac{B_{12}}{L} \right) \varphi_p(\eta)\varphi_q(\eta) + \frac{3nD_{66}}{4L} \left( \frac{RA_{66}}{L} - \frac{B_{66}}{L} \right) \varphi_p(\eta)\varphi_q(\eta) \right] d\eta \quad (34)$$
$$K_{bb}(p, q) = \frac{L}{R} \int_{0}^{L} \left[ n^2 A_{22} - \frac{2n^2 B_{22}}{R} + \frac{n^2 D_{22}}{R^2} \right] \varphi_p(\eta)\varphi_q(\eta) + \frac{R^2 A_{66}}{L^2} + \frac{3RB_{66}}{L} + \frac{9D_{66}}{4L^2} \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (35)$$
$$K_{bc}(p, q) = \frac{L}{R} \int_{0}^{L} \left[ \left( \frac{2nRB_{66}}{L^2} + \frac{3nD_{66}}{L^2} \right) \varphi_p(\eta)\varphi_q(\eta) - \left( \frac{nRB_{12}}{L^2} + \frac{nD_{12}}{L^2} \right) \varphi_p(\eta)\varphi_q(\eta) \right] + \left( nA_{22} + \frac{n^2 B_{22}}{R} + \frac{n^2 D_{22}}{R^2} \right) \varphi_p(\eta)\varphi_q(\eta) d\eta \quad (36)$$
