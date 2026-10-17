
其中，`$t$` 是时间变量，`$u, v$` 和 `$w$` 是浅壳中间参考面上沿 `$x, y, z$` 轴的位移分，`$U, V$` 和 `$W$` 是壳上任意点的位移分，`varphi_x$` 和 `$\varphi_y$` 分别是中面的旋转变量。壳上任意点的应变可以表示为：

$\begin{matrix} \varepsilon_x & \gamma_{xy}^0 & \gamma_{xz}^0 \\ \gamma_{xy}^0 & \varepsilon_y & \gamma_{yz}^0 \\ \gamma_{xz}^0 & \gamma_{yz}^0 & \varepsilon_z \end{matrix} + z \begin{matrix} \kappa_{xx}^0 & \kappa_{xy}^0 & \kappa_{xz}^0 \\ \kappa_{xy}^0 & \kappa_{yy}^0 & \kappa_{yz}^0 \\ \kappa_{xz}^0 & \kappa_{yz}^0 & \kappa_{zz}^0 \end{matrix} \quad (5.6)$

其中 $(\varepsilon_x, \varepsilon_y)$ 和 $\gamma_{xy}$ 分别是壳上任意点的正应变和切应变。$\gamma_{xz}$ 和 $\gamma_{yz}$ 是横向剪应变。

表面，扭转变化（$\kappa_s$）和曲率变化（$\kappa_s$ 和 $\kappa_t$）。这些变量可以表示为：

$\left\{\kappa_{sx}^0, \kappa_{sy}^0, \kappa_{sz}^0, \kappa_{xy}^0, \kappa_{xz}^0, \kappa_{yz}^0 \right\T = \begin{bmatrix} \frac{\partial \kappa_{sx}}{\partial x} & \frac{\partial \kappa_{sy}}{\partial y} & \frac{\partial \kappa_{sz}}{\partial z} & 0 & 0 & 0 \\ \frac{\partial \kappa_{xy}}{\partial x} & 0 & \frac{\partial \kappa_{yz}}{\partial y} & R_1 & 0 & 0 \\ 0 & \frac{\partial \kappa_{xz}}{\partial y} & 0 & \frac{\partial \kappa_{yz}}{\partial z} & R_2 & 0 \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix} \begin{bmatrix} \varphi_{sx} \\ \varphi_{sy} \\ \varphi_{sz} \\ \varphi_{xy} \\ \varphi_{xz} \\ \varphi_{yz} \end{bmatrix}$ （等待，图像中的公式与 OCR 生成的略有不同，根据视觉结构重新评估） (5.7)

根据广义胡克定律，梯度材料（FG）结构的应力-应变关系可以表示为：

$\begin{bmatrix} \sigma_x \\ \sigma_y \\ \tau_{xy} \\ \tau_{xz} \\ \tau_{yz} \end{bmatrix} = \begin{bmatrix} Q_{11}(z) & Q_{12}(z) & 0 & 0 & 0 \\ Q_{12}(z) & Q_{11}(z) & 0 & 0 & 0 \\ 0 & 0 & Q_{66}(z) & 0 & 0 \\ 0 & 0 & 0 & Q_{66}(z) & 0 \\ 0 & 0 & 0 & 0 & Q_{66}(z) \end{bmatrix} \begin{bmatrix} \varepsilon_x \\ \varepsilon_y \\ \gamma_{xy} \\ \gamma_{xz} \\ \gamma_{yz} \end{bmatrix}$ (5.8)

其中 $\sigma_x, \sigma_y$ 用于表示法应力，$\tau_{xy}, \tau_{xz}, \tau_{yz}$ 表示剪应力。$Q_{ij}$ 是减面材料刚度，相关的表达式如下：

$Q_{11}, Q_{12}, Q_{66} = \begin{bmatrix} E(z) & \mu(z)E(z) \\ \mu(z)E(z) & (1-\mu^2(z))\frac{E(z)}{2} \end{bmatrix}$ (5.9)

基于上述方程并沿厚度方向对应力进行积分，可以得到 FG 浅壳的力合力和力矩合：

$\{N_x, N_y, N_{xy}\} = \int_{-h/2}^{h/2}\{\sigma_x, \tau_{xy}\}dz$

$\{M_x, M_y, M_{xy}\} = \int_{-h/2}^{h/2}\{\sigma_y, \tau_{xy}\}dz$

$\{Q_x, Q_y\} = \int_{-h/2}^{h/2}\{\tau_{xz}, \tau_{yz}\}dz$ (5.10)

## 弹性基础上梯度材料多孔壳的自由和受迫振动

将方程 (5.6) 和 (5.8) 代入方程 (5.10)，可以得到：

$\begin{aligned} N_x &= A_{11}z_s^0 + A_{12}z_s^2 + B_{11}\kappa_x + B_{12}\kappa_y \\ N_y &= A_{21}z_s^0 + A_{22}z_s^2 + B_{21}\kappa_x + B_{22}\kappa_y \\ N_{xy} &= A_{66} + B_{66}\kappa_{xy} \\ M_{xy} &= D_{66}\kappa_{xy} + D_{66}\gamma^0 \\ M_x &= B_{11}z_s^0 + B_{12}z_s^2 + D_{11}\kappa_x + D_{12}\kappa_y \\ M_y &= B_{21}z_s^0 + B_{22}z_s^2 + D_{21}\kappa_x + D_{22}\kappa_y \\ Q_s &= C_{66}\gamma_s, Q_z &= C_{66}\gamma^0 \end{aligned}$ (5.11)

其中 $\kappa$ 是剪切修正系数，其值为 5/6。$A_{ij}, D_{ij}$ ($i,j=1, 2$) 是拉伸和拉伸-弯曲系数，其值可以通过以下表达式计算：

$A_{ij} = \int_{-h/2}^{h/2} Q_{ij}dz, D_{ij} = \int_{-h/2}^{h/2} z^2 Q_{ij}dz$ (5.12)

FG 浅壳的应变能能 $U_s$ 可以表述为：

$U_s = \frac{1}{2} \int_0^h \left( N_x\varepsilon_x + N_y\varepsilon_y + N_{xy}\varepsilon_{xy} + M_x\kappa_x + M_y\kappa_y + M_{xy}\kappa_{xy} + Q_s\gamma_s + Q_z\gamma^0 \right) dz$ (5.13)

FG 浅壳的动能 $T$ 可以表示为：

$T = \frac{1}{2} \int_0^h \left( \left(\frac{\partial\dot{w}}{\partial z}\right)^2 + \left(\frac{\partial\dot{\varphi}_x}{\partial z}\right)^2 + \left(\frac{\partial\dot{\varphi}_y}{\partial z}\right)^2 \right) + 2I_1 \left( \dot{w}\left(\frac{\partial\dot{\varphi}_x}{\partial z}\right) + \dot{\varphi}_x\frac{\partial\dot{w}}{\partial z} + \dot{\varphi}_y\left(\frac{\partial\dot{w}}{\partial z}\right) \right) dz$ (14)

其中惯性项为：

$I_0 = \int_{-h/2}^{h/2} \rho dz, I_1 = \int_{-h/2}^{h/2} \rho z^2 dz$ (15)

为了满足任何边界条件，本章引入了虚拟位移，通过三组线性弹簧和一组转动弹簧来模拟边界：

FG 复合结构

![](img/90ed16a3f9a7f082ec43da791c25f182)

**图 5.3** 所示，(A) 边界条件 (B) 弹性基础。因此，梯度材料（FG）壳的势能给出：

$U_p = \frac{1}{2} \int_{-h/2}^{h/2} \dots$ （省略部分公式） (16)

在本章中，不仅对 FG 壳进行了自由振动分析，还对外力 $W_j$ 功进行了分析：

$W_j = \dots$ （省略部分公式） (17)

对于弹性基础的势能 $U_g$ 可以写为：

18

对于 FG 壳，

梯度材料复合壳的应变能

### 5.2.4 切比方法

在自然坐标系中，FG 壳的未知函数 $p(x, y)$ 可以转换为第一类切比多项式：

$x = \frac{a}{2}\xi + \frac{a}{2}, y = \frac{b}{2}\eta + \frac{b}{2}, \xi \in[-1, 1], \eta \in[-1, 1]$ (19)

$q(\xi, \eta) \equiv C_{q}a$ (20a)

$C_{q} = C_{M-1}(\xi) \otimes C_{N-1}(\eta)$ (20b)

$C_{M-1}(\xi) = \{\cos(0 \cdot \xi), \cos(1 \cdot \xi), \dots, \cos((M-1) \cdot \xi)\}$ (20c)

$C_{N-1}(\eta) = \{\cos(0 \cdot \eta), \cos(1 \cdot \eta), \dots, \cos((N-1) \cdot \eta)\}$ (20d)

$a = (a_{0,0}, \dots, a_{0,N-1}, a_{1,0}, \dots, a_{1,N-1}, \dots, a_{M-1,N-1})^T$ (20e)

其中 $a$ 是展开系数向量，$M$ 和 $N$ 是多项式的总数，也称为截断数。使用 Gauss-Lobatto 点对自然坐标系下的矩形区域进行离散采样：

$\xi_i = -\cos\left(\frac{\pi i}{M-1}\right), i=0, 1, \dots, M-1$ (21)

$\eta_j = -\cos\left(\frac{\pi j}{N-1}\right), j=0, 1, \dots, N-1$ (21)

那么函数值向量与展开系数之间的关系写如下：

$q = C_{q}a, \quad a = C_{q}^{-1}q$ (22)

其中

$q = (q_{0,0}, \dots, q_{0,N-1}, \dots, q_{M-1,0}, \dots, q_{M-1,N-1})^T$ (23a)

$C = C_{M-1}(\xi) \otimes C_{N-1}(\eta)$ (23b)

### 5.2.5 求解步骤

一般边界条件下的拉格朗日函数可以表示为：

```
$L = U_s + U_{ip} + U_g - T - W_f \quad (5.30)$
```

将方程 (5.13),(5.14) 和 (5.16)–(5.18) 代入方程 (5.30)，并对未知系数进行变分运算，可以得到一个线性方程组，通过排序和矩阵化可以获得系统的振动特性，即：

```
$(\mathbf{K} - \omega^2\mathbf{M})mathbf{Q} = F \quad (5.31)$
```

其中 **M** 代表 FGP 浅壳矩阵，**K** 是刚度矩阵，**F** 代表作用在浅壳上的外部激励力矢量。**Q** 代表广义坐标矢量。当浅壳未施加外力时（即方程 (5.31) 中的力矢量设为零向量），即可得到自由振动分析所需的广义特征值方程 (5.30)。相关的动力方程可以表示为：

```
$(\mathbf{K} - \omega^2\mathbf{M})mathbf{Q} = 0 \quad (5.32)$
```

在本研究中，受迫振动分析主要考虑包括矩形、三角形、半弦波和指数脉冲在内的四种载荷，其数学定义可采用 [47]：

```
$Rectangular: F_r(t) = \begin{cases} f_r & 0 \le t \le \tau \\ 0 & t > \tau \end{cases}$
```

```
$Triangular: F_t(t) = \begin{cases} \frac{2t}{\tau}f_t & 0 \le t \le \frac{\tau}{2} \\ -2(\frac{t}{\tau} - 1)f_t & \frac{\tau}{2} \le t \le \tau \\ 0 & t \ge \tau \end{cases}$
```

```
$Half-sine: F_s(t) = f_s\sin(\frac{\pi t}{\tau}) \begin{cases} & 0 \le t \le \tau \\ 0 & t > \tau \end{cases}$
```

```
$Exponential: F_e(t) = \begin{cases} f_ee^{-\frac{t}{\tau}} & 0 \le t \le \tau \\ 0 & t > \tau \end{cases} \quad (5.33)$
```

其中 $f_t$ 和 $\tau$ 分别是作用在浅壳上的载荷幅和脉冲宽度，$t$ 代表时间变量。$\xi$ 表示常数。在上述推导的基础上，可以进一步对浅壳进行瞬态动力分析。基本运动方程可以表示为：

## $\mathbf{M}\ddot{\mathbf{u}} + \mathbf{C}_u\dot{\mathbf{u}} + \mathbf{K}\mathbf{u} = \mathbf{F}$

其中 $\mathbf{M}$、$\mathbf{K}$ 和 $\mathbf{F}$ 与之前一致，$\ddot{\mathbf{u}}$、$\dot{\mathbf{u}}$ 和 $\mathbf{u}$ 分别代表加速度矢量、速度矢量和位移矢量，$\mathbf{C}_R$ 是结构的阻尼矩阵，其定义见 [15]。

## $\mathbf{C}_R = \beta_1\mathbf{M} + \beta_2\mathbf{K}$

$\beta_1$ 和 $\beta_2$ 代表瑞利阻尼系数。对于目前的研究，不考虑阻尼，即 $\mathbf{C}_R=0$。

为了获得 FGP 浅壳的响应，采用 Newmark-$\beta$ 方法求解瞬态动力方程。根据 Newmark-$\beta$，可以获得 FGP 浅壳响应的位移 $\mathbf{u}_i$ 与速度 $\dot{\mathbf{u}}_i$ 的递归关系，并计算任意时刻的瞬态响应。

```
$$\mathbf{u}_{i+\Delta t} = \mathbf{u}_i + (1-\delta)\dot{\mathbf{u}}_i\Delta t + \frac{\delta}{2}\ddot{\mathbf{u}}_{i+\Delta t}\Delta t^2$$
$$\dot{\mathbf{u}}_{i+\Delta t} = \dot{\mathbf{u}}_i + \ddot{\mathbf{u}}_i\Delta t + (\frac{1}{2}-\alpha)(\ddot{\mathbf{u}}_i + \ddot{\mathbf{u}}_{i+\Delta t})\Delta t^2$$
```

从方程 (5.37) 可以推导出 $t_{i+1}$ 刻的加速度和速度计算公式如下：

```
$$\ddot{\mathbf{u}}_{i+1} = a_0(\dot{\mathbf{u}}_{i+1} - \dot{\mathbf{u}}_i) + a_2(\mathbf{u}_{i+1} - \mathbf{u}_i)$$
$$\dot{\mathbf{u}}_{i+1} = a_1(\dot{\mathbf{u}}_{i+1} - \dot{\mathbf{u}}_i) + a_4(\mathbf{u}_{i+1} - \mathbf{u}_i)$$
```

其中

```
$a_0 = \frac{1}{\alpha\Delta t^2}, a_1 = \frac{\delta}{\alpha\Delta t}, a_2 = \frac{-1}{\alpha}, a_3 = \frac{1}{2\alpha}, a_4 = \frac{-1}{2}, a_5 = \frac{\Delta t}{2}(\frac{1}{\alpha}-1)$
```

其中 $\alpha=\frac{1}{2}$ 且 $\delta=\frac{1}{2}$。根据方程 (5.34)，可以得到 $t_{i+1}$ 处的运动方程：

```
$$\mathbf{M}\ddot{\mathbf{u}}_{i+1} + \mathbf{C}_R\dot{\mathbf{u}}_{i+1} + \mathbf{K}\mathbf{u}_{i+1} = \mathbf{F}_{i+1}$$
```

弹性基上功能梯度壳的自由和受迫振动 5.3 分析与讨论

基于上述模型，本节目的是进行弹性基上功能梯度壳的自由和受迫振动，主要包括以下方面：

- (1) 收敛性分析；
- (2) 验证，与文献结果进行对比；
- (3) FGP 浅壳的自由振动分析；
- (4) 受迫振动，分析边界条件、载荷类型、材料参数 $\rho_1=2702\text{ kg/m}^3$、$E_1=70\text{ GPa}$、$\nu=0.3$ 以及无量纲频率 $\omega = \sqrt{\rho_1/E_1}$。

### 5.3.1 收敛
