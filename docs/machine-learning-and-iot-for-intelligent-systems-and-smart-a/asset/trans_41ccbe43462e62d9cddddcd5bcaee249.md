

![](img/93c6e2919cb9917d1bdd8f6271e04df4_52_0.png)

**图 3.1 所提系统的框图。**

![](img/93c6e2919cb9917d1bdd8f6271e04df4_52_1.png)

**图 3.2 两级单相并网逆变器。**

该逆变器作为 DC-DC 转换器运行，具有门极关断和门极导通功能。M3 和 M4 的门极脉冲相位相差 180°，而 M1 和 M2 的门极脉冲同相。开关 M5-M8 作为逆变器运行，输出端连接至 LCL-T 滤波器。

### 3.3.1 工作模式 1：(t0-t1)

在时间区间 (t0-t1) 内，开关 M1、M2、M5 和 M6 导通，PV 电源 V1 的功率施加到逆变器电路和 LCL-T 谐振滤波器上。电容 Cp 被充电；给定电感 Ls1，第一级导致流过电感的电流为零。在 t0 时刻，谐振电流变为零，电容 Cp 处于负值状态。

### 3.3.2 工作模式 2：(t1-t2)

在 t1 时刻，Cp 两端的电压变为正值。在 t2 时刻，开关 M1 和 M2 不导通，电感电流流过二极管 D1 和 D2。二极管开始导通。电容 $C_{P}$ 被放电。变压器的电压被检测为正值。

### 3.3.3 工作模式 3：($t_{2}$-$t_{3}$)

在时间区间 ($t_{2}$-$t_{3}$) 内，开关 $M_{3}$、$M_{4}$、$M_{7}$ 和 $M_{8}$ 导通，在此期间二极管 $D_{1}$ 和 $D_{4}$ 截止，功率从基础 PV 电压源 $V_{i}$ 提供至电网。谐振滤波器由负电压使能。

### 3.3.4 工作模式 4：($t_{3}$-$t_{4}$)

第四级的工作模式中，开关 $M_{3}$、$M_{4}$、$M_{7}$ 和 $M_{8}$ 工作在非导通模式。二极管 $D_{2}$ 和 $D_{3}$ 导通，从 $LS_{1}$ 侧对电容进行放电。在 $t_{4}$ 区间期间，CP 处的电压在负侧达到零。

### 3.3.5 工作模式 5：($t_{4}$-$t_{5}$)

第五级的过程与第一级的过程相似。由于电流 $i_{5}$ 产生电流方向的变化，二极管 $D_{2}$ 和 $D_{3}$ 截止。逆变器电流达到零，新的周期开始。

## 3.4 状态空间建模与 LCL-T 滤波器设计

LCL-T 滤波器的等效模型如图 3.3 所示。逆变器侧电感为 $L_{1}$，电网侧电感为 $L_{G}$，$C_{F}$ 是输出电容，$V_{1}$ 是给定的来自光伏组件的输入，其中 $V_{G}$ 是电网电压。

为了简化基础 LCL-T 逆变器的分析，考虑以下假设：

- i. 开关、二极管、电感和电容均为理想元件。
- ii. 忽略缓冲电容效应。
- iii. 忽略谐振回路损耗。
- iv. 采用直流供电。
- v. 使用波形的主要分量进行分析。
- vi. 对于理想变压器，匝数比 h = 1。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_53_0.png)

**图 3.3 LCL-T 滤波器的等效电路模型。**

LCL-T 逆变器的等效电路如图 3.3 所示。

状态空间模型是状态变量的数学模型，其中输出和输入通过微分方程相关联。状态、输出、输入的数量，向量变量、代数方程和微分方程以矩阵方程形式写出。时域方法（也称为“状态空间表示”）考察具有多个输入和输出的系统。电路包含一定数量的电感和电容。状态变量分别表示电感和电容的磁场和电场。状态方程提供系统行为。状态模型给出状态变量的时间历史。

$$\dot{X} = Ax + Bu \tag{3.1}$$

其中

$$\dot{X} = \begin{bmatrix} \frac{di_{Ll}}{dt} \\ \frac{dV_{C_F}}{dt} \\ \frac{di_{L_G}}{dt} \end{bmatrix} x = \begin{bmatrix} i_{Ll} \\ V_{C_F} \\ i_{L_G} \end{bmatrix} u = \begin{bmatrix} V_i \\ V_G \end{bmatrix}$$

LCL-T 滤波器的状态空间数学模型由图 3.3 得出，负载侧方程见方程 (3.2)–(3.4)

$$\frac{d}{dt} i_{Ll} = V_i \frac{1}{L_l} - V_{C_F} \frac{1}{L_F} \tag{3.2}$$

$$\frac{d}{dt} V_{C_F} = \frac{1}{C_F} (i_{Ll} - i_{L_G}) \tag{3.3}$$

$$\frac{d}{dt} i_{L_G} = -V_G \frac{1}{L_G} + V_{C_F} \frac{1}{L_G} \tag{3.4}$$

由方程 (3.2)、(3.3) 和 (3.4)，我们得到表示为连续状态空间模型的模型，由下式给出：

$$\begin{bmatrix} \frac{di_{Li}}{dt} \\ \frac{dV_{CF}}{dt} \\ \frac{di_{LG}}{dt} \end{bmatrix} = \begin{bmatrix} 0 & \frac{1}{L_i} & 0 \\ \frac{1}{C_F} & 0 & \frac{1}{C_F} \\ 0 & \frac{1}{L_G} & 0 \end{bmatrix} \begin{bmatrix} i_{Li}(t) \\ V_{CF}(t) \\ i_{LG}(t) \end{bmatrix} + \begin{bmatrix} \frac{1}{L_i} & 0 \\ 0 & 0 \\ 0 & \frac{1}{L_G} \end{bmatrix} \begin{bmatrix} V_i \\ V_G \end{bmatrix}$$ (3.5)

然后考虑 A、B 和 u 写作

$$A = \begin{bmatrix} 0 & \frac{1}{L_i} & 0 \\ \frac{1}{C_F} & 0 & \frac{1}{C_F} \\ 0 & \frac{1}{L_G} & 0 \end{bmatrix} \quad B = \begin{bmatrix} \frac{1}{L_i} & 0 \\ 0 & 0 \\ 0 & \frac{1}{L_G} \end{bmatrix} \quad u = \begin{bmatrix} V_i \\ V_G \end{bmatrix}$$

LCL-T 滤波器的零输入响应与零状态响应的和由下式给出：

$$\dot{X}(t) = \varnothing(t)A(x(s)) + L^{-1}(\varnothing(t)B(u(s)))$$ (3.6)

方程 (3.5) 和 (3.6) 可以针对电流求解，电压分量可以写为

$$\begin{bmatrix} i_{Li} \\ V_{CF} \\ i_{LG} \end{bmatrix} = \begin{bmatrix} \cos \theta + \frac{1}{C_F L_G \alpha^2}[\cos \theta + 1] & \frac{1}{L_i \alpha} \sin \theta & \frac{1}{C_F L_i \alpha^2}[\cos \theta + 1] \\ -\frac{1}{C_F \alpha}[\sin \theta] & \cos \theta & -\frac{1}{C_F \alpha} \sin \theta \\ \frac{1}{C_F L_G \alpha^2}[\cos \theta + 1] & \frac{1}{L_G \alpha} \sin \theta & \frac{1}{C_F L_G \alpha^2}[\cos \theta + 1] + \cos \theta \end{bmatrix}$$

$$\begin{bmatrix} i_{Li}(t) \\ V_{CF}(t) \\ i_{LG}(t) \end{bmatrix} + \begin{bmatrix} \frac{1}{L_i}[\frac{1}{\alpha} \sin \theta + \frac{1}{C_F L_G \alpha^2}(t + \frac{1}{\alpha} \sin \theta) + V_i \frac{1}{C_F L_i^2}(t + \frac{1}{\alpha} \sin \theta)] \\ -\frac{1}{\alpha C_F} \sin \theta - V_G \frac{1}{\alpha L_G \alpha} \sin \theta \\ V_i \frac{1}{\alpha^2 L_i C_F L_G}[(1 + \frac{\sin \theta}{\alpha})] - V_G \frac{1}{L_G}[\frac{\sin \theta}{\alpha} + \frac{1}{\alpha^2}(t + \frac{\sin \theta}{\alpha})] \end{bmatrix}$$ (3.7)

设

$$t_1 = \frac{1}{L_i}[\frac{1}{\alpha} \sin \theta + \frac{1}{C_F L_G \alpha^2}(t + \frac{1}{\alpha} \sin \theta) + V_i \frac{1}{C_F L_i^2}(t \frac{1}{\alpha} \sin \theta)]$$ (3.8)

$$t_2 = -\frac{1}{\alpha C_F} \sin \theta - V_G \frac{1}{\alpha L_G \alpha} \sin \theta$$ (3.9)

$t_3 = V_f\frac{1}{\alpha^2 L_f C_f L_G}\left[\left(1 + \frac{\sin\theta}{\alpha}\right)\right] - V_G\frac{1}{L_G}\left[\frac{\sin\theta}{\alpha} + \frac{1}{\alpha^2}\left(t + \frac{\sin\theta}{\alpha}\right)\right] (3.10)$

且 $\theta_{p-1}$ 和 $\theta_p$ 是连续导通模式下的开始和结束时间。
解方程 (3.5)、(3.6) 和 (3.7)，我们得到

$i_{L_f}(t) = i_{L_f}(\theta - \theta_{t-1})[\cos(\theta - \theta_{t-1}) + \frac{1}{C_f L_G \alpha^2}[1 + \cos(\theta - \theta_{t-1})]f_1$
$+ [\frac{1}{L_f\alpha}\sin\theta](V_{C_f}(\theta - \theta_{t-1}))f_2$
$+ \frac{1}{C_f L_f \alpha^2}[1 + \cos(\theta - \theta_{t-1})]i_{L_G}(\theta - \theta_{t-1})f_3$ (3.11)

$V_{C_f}(t) = i_{L_f}(\theta - \theta_{t-1})[\frac{1}{C_f\alpha}\sin(\theta - \theta_{t-1})f_1 + V_{C_f}(\theta - \theta_{t-1})\cos\theta]f_2$
$+ i_{L_G}(\theta - \theta_{t-1})[\frac{-1}{C_f\alpha}\sin(\theta - \theta_{t-1})]f_3$ (3.12)

$i_{L_G}(t) = i_{L_f}(\theta - \theta_{t-1})[\frac{1}{C_f L_G \alpha^2}(1 + \cos(\theta - \theta_{t-1}))]f_1$
$+ V_{C_f}(\theta - \theta_{t-1})[\frac{1}{L_G\alpha}\sin(\theta - \theta_{t-1})]f_2 + i_{L_f}(\theta - \theta_{t-1})[\cos(\theta - \theta_{t-1})]$
$+ \frac{1}{C_f L_f \alpha^2}(1 + \cos(\theta - \theta_{t-1}))f_3$ (3.13)

所提系统的输出电流、电压和稳定性可以通过方程 (3.5)、(3.11)、(3.12) 和 (3.13) 来估算。基于上述方程，计算 C$_f$、L$_f$ 和 L$_G$ 的值。

### 3.4.1 稳定性分析

该框图表示来自状态空间方程 (3.5) 的 LCL-T 逆变器。$-1 + j0$ 指向时间方向。因此，如果网络包络值零，则开环在 s 平面的右半部分没有极点。LCT-T 逆变器的奈奎斯特图如图 3.4 所示。

LCL-T 逆变器电路被证明是稳定的。LCL-T 逆变器的频率响应如图 3.5 所示。LCL-T 逆变器在 35° 相位裕度和 17 dB 增益裕度下是稳定的。

图 3.6 显示了变换器增益 (M) 与频率比 ($\omega_s/\omega_i$) 之间的关系，其中 $\delta=1$ (L$_f$/L$_G$)，曲线显示了裕度值。

### 3.4.2 FANN 控制器设计

FANN 控制器可以减少稳态、动态和瞬态性能偏差。所提 FANN 控制器的性能随神经元数量减少而得到改善

