
$$\frac{\partial f}{\partial x} = |J| \left( \frac{\partial f}{\partial \xi} \frac{\partial \xi}{\partial x} - \frac{\partial f}{\partial \eta} \frac{\partial \eta}{\partial x} \right)$$ $(3.17)$$

$$\frac{\partial f}{\partial y} = |J| \left( \frac{\partial f}{\partial \xi} \frac{\partial \xi}{\partial y} - \frac{\partial f}{\partial \eta} \frac{\partial \eta}{\partial y} \right)$$ $(3.18)$$

$$|J| = \det \begin{pmatrix} \frac{\partial \xi}{\partial x} & \frac{\partial \xi}{\partial y} \\ \frac{\partial \eta}{\partial x} & \frac{\partial \eta}{\partial y} \end{pmatrix}$$

$$J_{11} = \frac{\partial \xi}{\partial \eta} = \sum_{i=1}^{m} \sum_{j=1}^{n} N_{ij}(\xi, \eta) x_{ij,\eta}, J_{12} = \frac{\partial \xi}{\partial \xi} = \sum_{i=1}^{m} \sum_{j=1}^{n} N_{ij}(\xi, \eta) \eta_{ij}$$ $(3.19)$$

$$J_{21} = \frac{\partial \eta}{\partial \eta} = \sum_{i=1}^{m} \sum_{j=1}^{n} N_{ij}(\xi, \eta) x_{ij}, J_{22} = \frac{\partial \eta}{\partial \xi} = \sum_{i=1}^{m} \sum_{j=1}^{n} N_{ij}(\xi, \eta) \eta_{ij}$$

在自然坐标系中，函数 $q(\xi, \eta)$ 由一阶切比比多项式表示：

$$q(\xi, \eta) \equiv \sum C_k \mathbf{a}_k$$ $(3.20)$$

$$C_k = C_{M-1}(\xi) \otimes C_{N-1}(\eta)$$ $(3.21)$$

$$C_k = \cos{[0 \cdot \cos^{-1}(\xi)], [1 \cdot \cos^{-1}(\xi)] \cdots, \cos[(M-1) \cdot \cos^{-1}(\xi)]}$$ $(3.22)$$

$$C_{N-1}(\eta) = \cos{[0 \cdot \cos^{-1}(\eta)], [1 \cdot \cos^{-1}(\eta)] \cdots, \cos[(N-1) \cdot \cos^{-1}(\eta)]}$$ $(3.23)$$

$$\mathbf{a} = (a_{0,0}, \dots, a_{0,N-1}, a_{M-1,0}, \dots, a_{M-1,N-1})^T$$ $(3.24)$$

其中符号 $\otimes$ 是克罗内克积；$\mathbf{a}$ 是展开系数向量getM$ 和 $N$ 是多项式的截断数，分别代表 $\xi$ 和 $\eta$ 方向上多项式的总项数，向量的上标表示它是对应位移的未知系数。

### 3.2.4 求解步骤

根据方程 (3.10–3.13)，FGP 板的整体能量方程 `L` 可以表示为：

$$L = T - U_i - U_{wp} + W_f \quad (3.33)$$

将方程 (3.32) 代入方程 (3.33) 中，令拉格朗日关于未知系数的偏导数为，可以得到：

$$(\mathbf{K} - \omega^2\mathbf{M})\mathbf{Q} = \mathbf{F}$$

$$\mathbf{Q} = [q_1, q_2, q_3, q_4, q_5]^T$$

其中 `F` 代表外载荷向量，`K` 和 `M` 是刚度和质量矩阵；`ω` 和 `Q` 表示圆频率和广义位移向量。结合本文中的映射算法，刚度矩阵和质量矩阵给出：

$$\mathbf{M} = \begin{bmatrix} M_{11} & & M_{14} \\ M_{12} & M_{25} \\ M_{41} & M_{13} & M_{14} \end{bmatrix} \quad (3.35)$$

$$\mathbf{K}_k = \begin{bmatrix} K_{11}^T & K_{12}^T & K_{13}^T & K_{14}^T & K_{15}^T \\ K_{21}^T & K_{22}^T & K_{23}^T & K_{24}^T & K_{25}^T \\ K_{31}^T & K_{32}^T & K_{33}^T & K_{34}^T & K_{35}^T \\ K_{41}^T & K_{42}^T & K_{43}^T & K_{44}^T & K_{45}^T \\ K_{51}^T & K_{52}^T & K_{53}^T & K_{54}^T & K_{55}^T \end{bmatrix} \quad (3.36)$$

$$\mathbf{K}_{wp} = \begin{bmatrix} 0 & 0 & 0 & 0 & 0 \\ 0 & K_{22}^{wp} & 0 & 0 & 0 \\ 0 & 0 & K_{33}^{wp} & 0 & 0 \\ 0 & 0 & 0 & K_{44}^{wp} & 0 \\ 0 & 0 & 0 & 0 & K_{55}^{wp} \end{bmatrix} \quad (3.37)$$

where $M_{11} = M_{22} = M_{33} = -I_0 \bar{\mathbf{Q}}^T \nabla \mathbf{Q}$, $M_{14} = -I_1 \bar{\mathbf{Q}}^T \nabla \mathbf{Q}$, $M_{44} = M_{55} = -I_2 \bar{\mathbf{Q}}^T \nabla \mathbf{Q}$,

$$[I_0, I_1, I_2] = \int_{-h/2}^{h/2} \rho z^2 dz$$

## 复杂边缘梯度梯度板的自由与受迫振动

$$K_{11}^s = A_{11} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + A_{66} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + 2A_{16} \frac{\partial}{\partial \xi} \bar{Q}_{\eta}$$

$$K_{12}^s = A_{16} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + (A_{66} + A_{12}) \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + A_{20} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{14}^s = B_{11} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + B_{66} \frac{\partial}{\partial \eta} \bar{Q}_{\xi} + B_{60} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{15}^s = B_{16} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + (B_{12} + B_{60}) \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + B_{20} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{22}^s = A_{66} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + A_{22} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + 2A_{26} \frac{\partial}{\partial \xi} \bar{Q}_{\eta}$$

$$K_{25}^s = B_{66} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + (B_{12} + B_{60}) \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + B_{25} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{33}^s = C_{66} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + 2C_{60} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + C_{22} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{31}^s = -k_1(A_{55} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + 2A_{45} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + A_{44} \frac{\partial}{\partial \eta} \bar{Q}_{\eta})$$

$$K_{34}^s = -k_1(A_{55} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + A_{44} \frac{\partial}{\partial \eta} \bar{Q}_{\eta})$$

$$K_{35}^s = -k_1(A_{55} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + A_{44} \frac{\partial}{\partial \eta} \bar{Q}_{\eta})$$

$$K_{44}^s = D_{11} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + D_{66} \frac{\partial}{\partial \eta} \bar{Q}_{\xi} + 2D_{16} \frac{\partial}{\partial \xi} \bar{Q}_{\eta}$$

$$K_{45}^s = D_{16} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + (D_{66} + D_{12}) \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + D_{20} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{55}^s = D_{11} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + D_{60} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + D_{22} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{63}^s = 0$$

$$K_{11}^v = A_{11} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + A_{66} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + 2A_{16} \frac{\partial}{\partial \xi} \bar{Q}_{\eta}$$

$$K_{22}^v = A_{21} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + A_{22} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + A_{23} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{33}^v = C_{66} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + 2C_{60} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + C_{22} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$

$$K_{44}^v = D_{41} \frac{\partial}{\partial \xi} \bar{Q}_{\xi} + D_{42} \frac{\partial}{\partial \eta} \bar{Q}_{\xi} + D_{43} \frac{\partial}{\partial \xi} \bar{Q}_{\eta}$$

$$K_{55}^v = E_{51} \frac{\partial}{\partial \eta} \bar{Q}_{\eta} + E_{52} \frac{\partial}{\partial \xi} \bar{Q}_{\eta} + E_{53} \frac{\partial}{\partial \eta} \bar{Q}_{\eta}$$ (3.39)

$$\bar{V}_e = \mathbf{V}_e \bullet \text{diag}(\mathbf{J})$$

符号 $\bullet$ 表示哈达玛积。根据之前的工作，FGP板的瞬态响应可以通过公式求解：

$$\mathbf{M}\mathbf{u} + \mathbf{C}_R\mathbf{u} + \mathbf{K}\mathbf{u} = \mathbf{F}$$

其中 `u`、`dot{u}` 和 `ddot{u}` 分别表示位移、速度和加速度；`C_R` 是结构阻尼矩阵，定义为

$$\mathbf{C}_R = \beta_1\mathbf{M} + \beta_2\mathbf{K}$$

`β1` 和 `β2` 为阻尼系数，给出如下：

$$\beta_1 = 2\left(\frac{\omega_2^2}{\omega_3^2}\right)\left(\frac{1}{\omega_1^2}-\frac{1}{\omega_2^2}\right), \beta_2 = 4\left(\frac{\omega_2}{\omega_3}\right)\left(\frac{1}{\omega_1\omega_2}\right)$$

其中 `γ` 和 `β` 代表衰减系数。采用 Newmark-`β` 方法求解动力方程，得到了 `u`、`dot{u}` 和 `ddot{u}` 的相关性：

$$\begin{cases} \ddot{\mathbf{u}}_{i+1} = a_0\ddot{\mathbf{u}}_{i+1} + a_1\dot{\mathbf{u}}_i + a_2\mathbf{u}_i \\ \dot{\mathbf{u}}_{i+1} = a_3\ddot{\mathbf{u}}_{i+1} + a_4\dot{\mathbf{u}}_i + a_5\mathbf{u}_i \end{cases}$$

其中`a0 = 1/Δt^2, a1 = 1/Δt, a3 = 1/Δt-1, a5 = Δt/2, a2 = -0.5, a4 = 0.5`

通过将方程 (3.45) 代入上式，得到：

$$\mathbf{M}\ddot{\mathbf{u}}_{i+1} + \mathbf{C}_R\dot{\mathbf{u}}_{i+1} + \mathbf{K}\mathbf{u}}_{i+1} = \mathbf{F}_{i+1}$$

最后可以得到 `t_{i+1}` 时的位移、加速度和速度。

## 3.3 结果与讨论

在本节中，复杂边缘 FGP 板振动特的研究内容由三部分组成：自由振动、瞬态和稳态。各部分的研究顺序如下：

## 功能多孔矩形板的自由与受迫振动

为了测试当前 CDQM 处理复杂边缘 FGP 板振动的有效性和准确性，一种通用且有效的方案是首先给出示例，然后将结果与该方法以及已验证的方法进行比较。首先进行一些数值实例以验证 CDQM 的收敛性；然后综合分析孔隙率和分布对结构行为的影响，并获得了一些创新结果。为了验证该方法在边缘板振动中的通用性，给出了三种典型板的数值结果。此外，采用了包括经典和弹性约束在内的多种边界条件来增加数据的丰富性。通过引入虚拟弹簧边界条件，并考虑表3.1 中的弹簧值 [1,41]。

如图3.4 所示，矩形板的几何参数为 `L1, L2` 以及内角 `α1,α2,α3,α4`；椭圆板由最大最小直径 `a` 和 `b` 定义；截圆板的几何形状由半径 `(r)` 和中心距离 `(d)` 决定。矩形板的边界约束遵循 `L1, L2, L3, L4` 的顺序，而截圆板按照曲边和直边的顺序，椭圆板为单边。这里考虑的几种材料及其相应属性为：

- 1. FM1: `E1 = 200 GPa`; `u = 0.3; ρ1 = 7850 kg/m^3`
