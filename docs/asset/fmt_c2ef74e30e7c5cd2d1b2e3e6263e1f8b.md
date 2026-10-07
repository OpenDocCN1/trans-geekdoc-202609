
$K_{cb}(p, q) = \frac{L}{R_0} \left[ \frac{2nRB_{66}}{L^2} + \frac{3nD_{66}}{L}\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) - (\frac{nRB_{12}}{L^2} + \frac{nD_{12}}{L^2})\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) + nA_{22} + \frac{n^2B_{22}}{R} + \frac{n^2D_{22}}{R^2}\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) \right] d\eta \quad (4.38)$

$K_{cc}(p, q) = \frac{L}{R_0} \left[ \frac{A_{22}}{R} + \frac{2n^2B_{22}}{R} + \frac{n^2D_{22}}{R^2}\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) + \frac{4n^2D_{66}}{L^2}\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) - \frac{R^2D_{11}}{L^4}\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) - (\frac{nD_{12}}{L^2} + \frac{RB_{12}}{L^2})\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) - \frac{n^2D_{12}}{L^2} + \frac{RB_{12}}{L^2}\psi_p^{(w)}(\eta)\psi_q^{(w)}(\eta) \right] d\eta \quad (4.39)$

弹刚度矩阵 $\mathbf{K}_s$ 的表达式：

```
$$\mathbf{K}_s = \begin{bmatrix} k_{bb} & & \ & k_{bc} & \ & & k_{cc} \end{bmatrix} \quad \quad (4.40)$$
```

其中：

$k_{bb}^{(w)}(p, q) = RK_0\psi_p^{(w)}(0)\psi_q^{(w)}(0) \quad (4.41)$

$k_{bc}^{(w)}(p, q) = RK_0\psi_p^{(w)}(0)\psi_q^{(w)}(0) \quad (4.42)$

$k_{cc}^{(w)}(p, q) = R(k_0\psi_p^{(w)}(0)\psi_q^{(w)}(0) + k_0^2[\psi_p^{(w)}(0)]^2)/L^2 \quad (4.43)$

$k_{cb}^{(w)}(p, q) = RK_0\psi_p^{(w)}(1) \quad (4.44)$

功能梯度多孔圆柱壳的自由振动与迫振动

**表 4.2** 均匀圆柱壳 (S-S) 频率频率 $\omega/2\pi$ 的比较。

| 模态数 | 自然频率 (Hz) | | |
|---|---|---|---|
| m | n | Pellicano [31] | 本文 |
| 1 | 7 | 484.6 | 484.6 |
| 1 | 8 | 489.6 | 489.6 |
| 1 | 9 | 546.2 | 546.2 |
| 1 | 6 | 553.3 | 553.3 |
| 1 | 10 | 636.8 | 636.8 |
| 1 | 5 | 722.1 | 722.1 |
| 1 | 11 | 750.7 | 750.7 |
| 2 | 12 | 882.2 | 882.2 |
| 2 | 10 | 968.1 | 968.1 |
| 2 | 11 | 983.4 | 983.4 |

```
$k_{re}(p,q) = Rk_{\mu}^p(1)\omega_{\mu}^q(1)$
```

```
$k_{gj}(p,q) = R(k_{\mu}^p(1)\omega_{\mu}^q(1) + k_g_{\mu}^p(1)[\nu_{\mu}^q(1)]/L^2$
```

然后推导出具有任意边界条件的 FG 多孔圆柱壳的特征值问题：

```
$|\omega^2 M - K - K| =0$
```

### 4.2.3 结果与讨论

首先进行了一项研究。均匀圆柱壳的自然频率结果见表 4.2。圆柱壳的几何尺寸和材料属性如下：$L=0.2$ m，$R=0.1$ m，$h=0.247\times10^{-3}$ m，$E=71.02$ GPa，$\rho=2796$ kg/m³，$\mu=0.3$。根据文献 [30],$k_h=k_p=0, k_t=10^{2}$ 和 $k_u=k_g=10^{2}$ (N/m) 分别选择为简支 (S) 和固定 (C) 边界。目前的结果与文献 [31] 给出的结果一致良好。本节 FG 多孔壳的几何和材料参数为：

```
$L=5$ m，$R=1$ m，$h=0.002$ m，$E_m=2.04\times10^{9}$ Pa，$\rho_m=7850$ kg/m³，$\nu_m=0.3$。
```

图 4.3 显示了不同孔隙率下自然频率与周向波数的关系。此外，不同的边界条件：

![](img/90ed165a39fa708ec48fc7931c25_111_0.png)

![](img/90ed165a39fa708ec48fc7931c25_111_1.png)

![](img/90ed165a39fa708ec48fc7931c25_111_2.png)

![](img/90ed165a39fa708ec48fc7931c25_111_3.png)

![](img/90ed165a39fa708ec48fc7931c25_111_4.png)

![](img/90ed165a39fa708ec48fc7931c25_111_5.png)

**图 4** 不同孔隙率下的自然频率周向波数：(A) C-C；(B) S-S；(C) $k_t=10^{10}$ (N/m or Nrad)；(D) $k_l=10^{9}$ (N/m or Nrad)；(E) $k_t=10^{9}$ (N/m or Nrad)；(F) $k_l=10^{8}$ (N/m or Nrad)。对于较强的边界，如图 4.3A–C 所示，自然频率随着孔隙率的增加而降低。但频率降低与周向波数有关。对于较弱边界，上述现象不再适用。如图 4.3D–F 所示，随着边界刚度的降低，孔隙率对自然频率的影响逐渐收敛。当周向波数较小时，自然频率甚至随孔隙率的增加而增加（见图 4.3E 和 F）。同时，对于大波数，孔隙率对自然频率的影响也微乎其微。

图 4 展示了边界条件对频率随孔隙率变化的影响。在 C-C、C-S、$k_c=10^{10}$ 和 $k_s=10^{8}$ 边界条件下，但在 C-F 和 S-F 边界条件下，自然频率变化很小。这表明由于孔隙率导致的自然频率降低与边界条件密切相关。表 4.3 给出了不同孔隙分布下 FG 多孔圆柱壳的自然频率。这里采用 $k_s=10^{10}$ 作为 E-E 边界

![](img/90ed165a39fa708ec48fc7931c25_112_0.png)

图 4.4 不同边界条件下自然频率随孔隙率的变化 (PD-A)。

**表 4.3** 不同边界条件和孔隙分布下功能梯度多孔圆柱壳的最低自然频率 (Hz) ($e_1=0.2$)。

| | C-C | | E-E | | C-F | | |
|---|---|---|---|---|---|---|---|
| | PD-A | PD-B | PD-A | PD-B | PD-A | PD-B |
| 1 | 963.1 | 963.1 | 248.8 | 248.8 | 248.8 | 453.4 | 453.1 |
| 2 | 628.5 | 628.5 | 227.8 | 235.0 | 235.1 | 229.2 |
| 3 | 446.8 | 454.0 | 245.6 | 221.8 | 228.7 | 147.4 |
| 4 | 359.6 | 353.0 | 232.1 | 228.9 | 166.9 | 162.3 |
| 5 | 351.8 | 332.6 | 282.3 | 275.7 | 264.8 | 241.1 |
| 6 | 410.2 | 383.2 | 370.6 | 372.2 | 362.0 | 344.4 |
| 7 | 514.8 | 475.6 | 500.2 | 491.4 | 477.1 | 452.7 |

功能梯度圆柱壳的迫振

## 4.3 线性迫振

### 4.3.1 控制方程

对于多孔圆柱壳，振动响应由多个模态的叠加组成。考虑到计算效率和收敛速度，这里使用了切比多项式。那么圆柱壳的选取函数可以表示为：

```
$$\begin{aligned} u(\eta, \theta, t) &= \sum_{n=1}^{N} \sum_{m=-G}^{G} a_{nm}T_m(\eta)\cos(n\theta)e^{i\omega t} = \mathbf{V}_u^T\mathbf{q}_w \\ v(\eta, \theta, t) &= \sum_{n=1}^{N} \sum_{m=-G}^{G} b_{nm}T_m(\eta)\sin(n\theta)e^{i\omega t} = \mathbf{V}_v^T\mathbf{q}_w \\ w(\eta, \theta, t) &= \sum_{n=1}^{N} \sum_{m=-G}^{G} c_{nm}T_m(\eta)\cos(n\theta)e^{i\omega t} = \mathbf{V}_w^T\mathbf{q}_w \end{aligned}$$
```

FG 多孔

复合结构

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
