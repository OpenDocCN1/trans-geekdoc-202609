
因此，通过应用鲁斯-胡尔维茨条件，它是局部渐近稳定的。

### 定理 2
如果基本再生数 $R_0 < 1$，则 COVID-19 无病平衡是全局渐近稳定的。

证明：考虑 Thieme Horst 和 Lyapunov (2011) 公式 7.18：

$M = \mu E + (d_1 + \mu) I$
$\Rightarrow \frac{dM}{dt} = \frac{\mu dE}{dt} + \frac{(d_1 + \mu) dI}{dt} \tag{7.18}$
$\Rightarrow \frac{dM}{dt} = (d_1 + \mu)(d_1 + d_2 + \alpha)(R_0 - 1) I$

如果 $R_0 < 1$，则 $\frac{dM}{dt} < 0$ 且 $\frac{dM}{dt} = 0$ 仅当 $I = 0$ 或 $R_0 = 1$ 时成立。因此，根据 LaSalle 不变性原理，该集合在区域 $\Omega_0$ 中全局渐近稳定。

## 7.5.2 地方性平衡的稳定性分析
对地方性平衡 $\Omega^* (S^*, E^*, I^*, Q^*, R^*)$ 的稳定性分析，我们求解公式 7.19 的联立系统：

$S^* = \frac{1}{R_0}$

$E^* = \frac{A}{(d_1 + \mu)} \left(1 - \frac{1}{R_0}\right)$

$I^* = \frac{\mu (R_0 - 1)}{\beta} \tag{7.19}$

$Q^* = \frac{\alpha d_1 (R_0 - 1) \beta}{(d_1 + d_2 + \delta) \beta}$

$R^* = \frac{\alpha \delta (R_0 - 1)}{(d_1 + d_2 + \delta)}$

### 定理 3
如果 $R_0 > 1$，则系统 (2) 具有唯一的地方性平衡 $\Omega^* (S^*, E^*, I^*, Q^*)$，它是局部渐近稳定的。

证明：在公式 7.20 的线性化中，矩阵的雅可比矩阵为

$\Omega^* = \begin{pmatrix} -d_1 - \beta I^* & 0 & -\beta S^* & 0 \\ \beta I^* & -(d_1 + \mu) & \beta S^* & 0 \\ 0 & \mu & -(d_1 + d_2 + \alpha) & 0 \\ 0 & 0 & \alpha & -(d_1 + d_2 + \delta) \end{pmatrix} \tag{7.20}$

特征值为 $\lambda = -(d_1 + d_2 + \delta)$。

求解三次方程时另外三个特征值为 $\lambda^3 + A\lambda^2 + B\lambda + C = 0$，其中

$A = \beta I^* + 3d_1 + d_2 + \alpha + \mu$
$B = 3d_1^2 + 2d_1\mu + 2d_1d_2 + 2d_1\alpha + 2d_1\beta I^* + \mu\beta I^* + d_2\beta I^* + \alpha\beta I^* + \mu d_2 + \alpha\mu - \alpha\beta S^*$
$C = d_1^3 + d_1^2 d_2 + \alpha d_1^2 + \mu d_1^2 + \mu d_1 d_2 + d_1\alpha\mu + d_1^2\beta I^* + d_1 d_2\beta I^* + d_1\alpha\beta I^* + \mu d_1\beta I^* + \mu d_2\beta I^* + \mu\alpha\beta I^* + \mu\beta S^* d_1 + 2\mu\beta^2 I^* S^*$ (7.21)

由于 $A > 0$、$B > 0$ 且 $C > 0$，则 $AB > C$。

因此，通过应用鲁斯-胡尔维茨条件，地方性平衡是局部渐近稳定的。

## 7.5.3 地方性平衡的全局稳定性
本节使用几何方法讨论地方性平衡的全局稳定性。平衡点全局稳定性的充分条件由 Bendixson 条件给出。

对于 $R_0 > 1$，我们推断方程组的均匀持续性，这意味着存在一个正常数 $C$，使得初始条件 $(S(0),E(0),I(0),Q(0))$ 位于区域 $\Omega$ 的内部。

满足 $\min\{\liminf_{t\to\infty} S(t),\liminf_{t\to\infty} E(t),\liminf_{t\to\infty} I(t),\liminf_{t\to\infty} Q(t)\} > C$ 的任意解 $(S(t),E(t),I(t),Q(t))$

上述条件连同区域 $\Omega$ 的有界性验证了地方性平衡点位于 $\Omega$ 内部。

### 定理 4
如果 $R_0 > 1$，则唯一的地方性平衡 $\Omega^*$ 在 $\Omega$ 内部是全局渐近稳定的。

证明：系统的一般解如公式 7.22 所示。
$J = \begin{pmatrix} -d_1 - \beta I & 0 & -\beta S & 0 \\ \beta I & -(d_1 + \mu) & \beta S & 0 \\ 0 & \mu & -(d_1 + d_2 + \alpha) & 0 \\ 0 & 0 & \alpha & -(d_1 + d_2 + \delta) \end{pmatrix}$ (7.22)

二阶复合矩阵由公式 7.23 给出：

J^{[2]} = \begin{pmatrix} -2d_{1} - \beta I - \mu & \beta S & 0 & 0 & 0 & 0 \\ \mu & -2d_{1} - d_{2} - \alpha - \beta I & 0 & 0 & 0 & 0 \\ 0 & \alpha & -2d_{1} - d_{2} - \delta - \beta I & 0 & 0 & -\beta S \\ 0 & \beta I & 0 & -(2d_{1} + d_{2} + \mu + \alpha) & 0 & 0 \\ 0 & 0 & \beta I & \alpha & -(2d_{1} + \mu + d_{2} + \delta) & \beta S \\ 0 & 0 & 0 & 0 & \mu & -(2d_{1} + 2d_{2} + \alpha + \delta) \end{pmatrix} \tag{7.23}

为了在 Bendixson 矩阵条件下得到矩阵 B，我们将对角矩阵 M 定义为公式 7.24：

M = \operatorname{diag}\left(1, \frac{E}{I}, \frac{E}{I}, \frac{E}{I}, \frac{E}{I}, \frac{E}{I}\right) \tag{7.24}

我们可以定义系统的向量场，然后是公式 7.25 和 7.26：

M_{f} M^{-1} = \operatorname{diag}\left(0, \frac{E'}{E} - \frac{I'}{I}, \frac{E'}{E} - \frac{I'}{I}, \frac{E'}{E} - \frac{I'}{I}, \frac{E'}{E} - \frac{I'}{I}, \frac{E'}{E} - \frac{I'}{I}\right) \tag{7.25}

B = M_{f} M^{-1} + M J^{[2]} M^{-1} = \begin{pmatrix} -2d_{1} - \beta I - \mu & \frac{\beta S I}{E} & 0 & \frac{\beta S I}{E} & 0 & 0 \\ \frac{E \mu}{I} & -2d_{1} - d_{2} - \alpha - \beta I + \frac{E'}{E} - \frac{I'}{I} & 0 & 0 & 0 & 0 \\ 0 & \alpha & \frac{E'}{E} - \frac{I'}{I} -2d_{1} - d_{2} - \delta - \beta I & 0 & 0 & -\beta S \\ 0 & \beta I & 0 & \frac{E'}{E} - \frac{I'}{I} - (2d_{1} + d_{2} + \mu + \alpha) & 0 & 0 \\ 0 & 0 & \beta I & \alpha & \frac{E'}{E} - \frac{I'}{I} - (2d_{1} + \mu + d_{2} + \delta) & \beta S \\ 0 & 0 & 0 & 0 & \mu & \frac{E'}{E} - \frac{I'}{I} - (2d_{1} + 2d_{2} + \alpha + \delta) \end{pmatrix} \tag{7.26}

前述矩阵可表示为公式 7.27 中的分块矩阵：

$$B = \begin{pmatrix} B_{11} & B_{12} \\ B_{21} & B_{22} \end{pmatrix}\tag{7.27}$$

其中公式 7.28

$$B_{11}=(-2d_1 - \beta I - \mu)$$

$$B_{12}=\begin{pmatrix} \frac{\beta S I}{E} & 0 & \frac{\beta S I}{E} & 0 & 0 \end{pmatrix}$$

$$B_{21}=\begin{pmatrix} \frac{E'\mu}{I} \\ 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$$

$$B_{22}=\begin{pmatrix} -2d_1 - d_2 - \alpha - \beta I + \frac{E'}{E} - \frac{I'}{I} & 0 & 0 \\ \alpha & \frac{E'}{E} - \frac{I'}{I} -2d_1 - d_2 - \delta - \beta I & 0 \\ \beta I & 0 & \frac{E'}{E} - \frac{I'}{I} -(2d_1 + d_2 + \mu + \alpha) \\ 0 & \beta I & \alpha \\ 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & -\beta S & 0 \\ 0 & 0 & 0 \\ \frac{E'}{E} - \frac{I'}{I} -(2d_1 + \mu + d_2 + \delta) & \beta S & 0 \\ \mu & \frac{E'}{E} - \frac{I'}{I} -(2d_1 + 2d_2 + \alpha + \delta) \end{pmatrix}\tag{7.28}$$

矩阵的 Lozinskii 测度可计算为 $\mu(B) \le \sup\{g_1, g_2\}$，其中

$$g_1 = \mu(B_{11}) + |B_{12}| = -2d_1 - \beta I - \mu + \frac{\beta S I}{E}$$

$$g_2 = |B_{21}| + \mu(B_{22}) = -2d_1 + \mu + \frac{E'}{E} - \frac{I'}{I}\tag{7.29}$$

该 Lozinskii 测度 (2023) 相对于分块矩阵 B12 和 B21 的范数是 mieux，其中它们是算子范数。

因此，$g_1$ 和 $g_2$ 化简为公式 7.30：

$$\begin{aligned}
g_1 &= -d_1 - \beta I + \frac{E'}{E} \\
g_2 &= -d_1 + \alpha + d_2 + \frac{E'}{E}
\end{aligned} \tag{7.30}$$

因此

$$\mu(B) \leq \sup\{g_1,g_2\} \leq \frac{E'}{E} - d_1 + \sup\{-\beta I, d_2+\alpha\}$$

因此，$\mu(B) \leq \frac{E'}{E} - d_1$；于是

$$\int_0^t \mu(B)\,dt \leq \left(\log E(t)-d_1t\right)$$

因此，最后如公式 7.31 所示

$$\bar{q}_2 = \frac{\int_0^t \mu(B)\,dt}{t} < \frac{\log E(t)}{t} - d_1 < \frac{d_1}{2} - d_1 < 0 \tag{7.31}$$

因此，准则 $\bar{q}_2 < 0$ 得到满足。因此，系统的流行病平衡是全局稳定的。

## 7.6 结果与讨论
分析结果若无数值模拟则无法证明。这些图解释了 COVID-19 期间模型在不同人群中的行为。

这些图显示了参数随时间变化的人群偏差。人工智能技术正在被开发用于检测 COVID-19 并确定疾病的稳定性。主要目标是通过可视化来控制 COVID-19 引起的感染。

基于 COVID-19 期间的不同情况，我们在人工智能技术的帮助下使用了不同的参数。COVID-19 无病平衡点在 $R_0 < 1$ 时是稳定的（图 7.3）。

隔离和暴露的综合效应的最佳用途在图中显示。结果，使用人工智能后暴露人群的隔离/住院率下降，如图 7.4 所示。

该图表明，如果暴露人群出现某些疾病症状，他们会迅速存活并进入隔离，如图 7.5 所示。
