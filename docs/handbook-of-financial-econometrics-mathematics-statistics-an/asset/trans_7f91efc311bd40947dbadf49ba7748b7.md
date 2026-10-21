
最大似然估计程序。假定一期短期利率 $r_t$ 是上述所有因子的仿射函数，

$r_t = \delta_0 + \delta_1^T x_t.$
(61.8)

在我们的估计中，我们将 $\delta_0$ 固定为三个月国库券利率的无条件均值。关于 $\delta_1$，我们通过将三个月利率对宏观因子进行线性回归得到对应宏观因子的系数 $\delta_{11}$，并将对应潜在因子的 $\delta_{12}$ 留待在最大似然估计程序中估计。最后，市场风险价格通过以下标准关系进行估计，

$\lambda_t = \lambda_0 + \lambda_1 x_t.$
(61.9)

在这种情况下，$\lambda_0$ 是一个 27 维向量，$\lambda_1$ 是一个 $27 \times 27$ 矩阵，其中与滞后宏观因子对应的相关参数被设为零。这使我们能够大幅简化估计程序，同时仍确保宏观和潜在因子的风险得到定价。这意味着 $\lambda_0$ 的上部 $2 \times 1$ 行（对应当前宏观因子）和下部 $3 \times 1$ 行（对应潜在因子）是自由参数。$\lambda_1$ 的左上 $2 \times 2$ 角、右上 $2 \times 3$ 角、左下 $3 \times 2$ 角以及右下 $3 \times 3$ 角也都是自由参数。上述步骤刻画了模型中因子随时间演化的时间序列动态。

关于我们最大似然估计程序的横截面部分，我们首先假设 $P_{t,n} = \exp (\bar{A}_n + \bar{B}_n^T x_t)$（例如参见 Duffie and Kan, 1996）。为了推导用于计算递归债券价格的系数，我们首先注意到对于一个 $n$ 期债券，

$P_{t,n+1} = E_t[\xi_{t+1} P_{t+1,n}]$
$= E_t\left[ \exp\left\{ -r_t - \frac{1}{2} \lambda_t^T \lambda_t - \lambda_t^T \varepsilon_{t+1} + \bar{A}_n + \bar{B}_n^T x_{t+1} \right\} \right].$
(61.10a)

由于期望是在时间 $t$ 取的，信息在时间 $t$ 已知，且该表达式可在无不确定性的情况下求值。因此，我们将这些已知量从期望中提出，如方程 (61.10b) 所示，并在后续步骤中，

$= \exp\left\{ -r_t - \frac{1}{2} \lambda_t^T \lambda_t + \bar{A}_n \right\} E_t[\exp\{-\lambda_t^T \varepsilon_{t+1} + \bar{B}_n^T x_{t+1}\}].$
(61.10b)

然后，我们在假设状态变量 $x_{t+1} = \mu + \phi x_t + \Sigma \varepsilon_{t+1}$ 的以下动态下继续推导，并用一阶向量自回归动态描述上述表达式中的状态变量

$=\exp\left\{-r_t - \frac{1}{2}\lambda_t^T\lambda_t + \bar A_n\right\} E_t\left[\exp\left\{-\lambda_t^T\varepsilon_{t+1} + \bar B_n^T(\mu + \phi x_t + \Sigma\varepsilon_{t+1})\right\}\right].$

(61.10c)

在下面的步骤中，我们简化方程 (61.10c)，然后收集并匹配系数，以展示作者如何得出论文第 760 页上给出的状态因子系数（Ang and Piazzesi, 2003），

$=\exp\left\{-r_t - \frac{1}{2}\lambda_t^T\lambda_t + \bar A_n + \bar B_n^T\mu + \bar B_n^T\phi x_t\right\} E_t\left[\exp\left\{-\lambda_t^T\varepsilon_{t+1} + \bar B_n^T\Sigma\varepsilon_{t+1}\right\}\right]$
$=\exp\left\{-\delta_0 - \delta_1^T x_t - \frac{1}{2}\lambda_t^T\lambda_t + \bar A_n + \bar B_n^T\mu + \bar B_n^T\phi x_t\right\} E_t\left[\exp\left\{-\lambda_t^T\varepsilon_{t+1} + \bar B_n^T\Sigma\varepsilon_{t+1}\right\}\right]$
$=\exp\left\{-\delta_0 + \bar A_n + \bar B_n^T\mu + (\bar B_n^T\phi - \delta_1^T) x_t - \frac{1}{2}\lambda_t^T\lambda_t\right\} E_t\left[\exp\left\{-\lambda_t^T\varepsilon_{t+1} + \bar B_n^T\Sigma\varepsilon_{t+1}\right\}\right].$

Ang and Piazzesi (2003) 进一步假设 $\varepsilon_{t+1} \sim N(0, I)$，因此，关于第二项及其期望的计算

$E_t\left[\exp\left\{-\lambda_t^T\varepsilon_{t+1} + \bar B_n^T\Sigma\varepsilon_{t+1}\right\}\right]$
$= E_t\left[\exp\left\{(\bar B_n^T\Sigma - \lambda_t^T)\varepsilon_{t+1}\right\}\right]$
$= \exp\left\{\frac{(\bar B_n^T\Sigma - \lambda_t^T)(\bar B_n^T\Sigma - \lambda_t^T)^T}{2}\right\}$
$= \exp\left\{\frac{(\bar B_n^T\Sigma - \lambda_t^T)(\Sigma^T\bar B_n - \lambda_t)}{2}\right\}$
$= \exp\left\{\frac{(\bar B_n^T\Sigma\Sigma^T\bar B_n - \bar B_n^T\Sigma\lambda_t - \lambda_t^T\Sigma^T\bar B_n + \lambda_t^T\lambda_t)}{2}\right\}$
$= \exp\left\{\frac{(\bar B_n^T\Sigma\Sigma^T\bar B_n - 2\bar B_n^T\Sigma\lambda_t + \lambda_t^T\lambda_t)}{2}\right\}$
$= \exp\left\{\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2} - \bar B_n^T\Sigma\lambda_t + \frac{\lambda_t^T\lambda_t}{2}\right\}$
$= \exp\left\{\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2} - \bar B_n^T\Sigma(\lambda_0 + \lambda_1 x_t) + \frac{\lambda_t^T\lambda_t}{2}\right\}$
$= \exp\left\{\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2} - \bar B_n^T\Sigma\lambda_0 + \bar B_n^T\Sigma\lambda_1 x_t + \frac{\lambda_t^T\lambda_t}{2}\right\}.$

最后，将所有这些信息代回定价方程并简化，

$P_{t,n+1}=\exp\left\{-\delta_0+\bar A_n+\bar B_n^T\mu+(\bar B_n^T\phi-\delta_1^T)x_t-\frac12\lambda_t^T\lambda_t\right\}\exp\left\{\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}-\bar B_n^T\Sigma\lambda_0+\bar B_n^T\Sigma\lambda_1x_t+\frac{\lambda_t^T\lambda_t}{2}\right\},\tag{61.11}$

$P_{t,n+1}=\exp\left\{-\delta_0+\bar A_n+\bar B_n^T\mu+(\bar B_n^T\phi-\delta_1^T)x_t-\frac12\lambda_t^T\lambda_t+\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}-\bar B_n^T\Sigma\lambda_0+\bar B_n^T\Sigma\lambda_1x_t+\frac{\lambda_t^T\lambda_t}{2}\right\},$

$P_{t,n+1}=\exp\left\{-\delta_0+\bar A_n+\bar B_n^T\mu+(\bar B_n^T\phi-\delta_1^T)x_t+\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}-\bar B_n^T\Sigma\lambda_0+\bar B_n^T\Sigma\lambda_1x_t\right\},$

$P_{t,n+1}=\exp\left\{-\delta_0+\bar A_n+\bar B_n^T(\mu-\Sigma\lambda_0)+(\bar B_n^T\phi-\delta_1^T)x_t+\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}+\bar B_n^T\Sigma\lambda_1x_t\right\},$

$P_{t,n+1}=\exp\left\{-\delta_0+\bar A_n+\bar B_n^T(\mu-\Sigma\lambda_0)+(\bar B_n^T\phi-\bar B_n^T\Sigma\lambda_1)x_t+\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}-\delta_1^Tx_t\right\},$

$P_{t,n+1}=\exp\left\{-\delta_0+\bar A_n+\bar B_n^T(\mu-\Sigma\lambda_0)+\bar B_n^T(\phi-\Sigma\lambda_1)x_t+\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}-\delta_1^Tx_t\right\}.$

因此，将上述方程中的系数与下面的方程 $P_{t,n+1}=\exp(\bar A_n+\bar B_n^T x_t)$ 进行匹配，我们发现

$\bar A_{n+1}=-\delta_0+\bar A_n+\bar B_n^T(\mu-\Sigma\lambda_0)+\frac{\bar B_n^T\Sigma\Sigma^T\bar B_n}{2}\tag{61.12}$

和

$\bar B_{n+1}=-\delta_1^T+\bar B_n^T(\phi-\Sigma\lambda_1).\tag{61.13}$

这些递归差分方程以初始条件 $\bar{A}_1 = -\delta_0$ 和 $\bar{B}_1 = -\delta_1$ 求解，并在其论文的方程 (61.17) 中给出。$n$ 期零息债券的连续复利零息收益率 $y_t^n$ 由下式给出

$$y_t^n = -\frac{\log p_t^n}{n} = A_n + B_n^T x_t.\tag{61.14}$$

最后，$A_n = -\frac{\bar{A}_n}{n}$ 且 $B_n = -\frac{\bar{B}_n}{n}$。如果我们假设可用的债券数量与潜在因子相同，估计中为三个。然后，遵循大量文献（例如 Pearson and Sun (1994)），我们可以将六个月、两年和十年零息债券收益率视为无误差测量，并利用这些收益率“反演”模型以得到潜在因子。这意味着我们可以将三个收益率的方程堆叠为 $Y_t = (y_t^{6\text{mo}}, y_t^{2\text{yr}}, y_t^{10\text{yr}})^T$。然后，$Y_t = A + B x_t$，其中 A 是一个 $3 \times 1$ 向量，B 是 $3 \times 27$。如果我们将 B 分区为 $B = [B^o B^u]$，其中 $B^o$ 是与可观测因子相关的 $3 \times 24$ 矩阵，$B^u$ 是与潜在变量相连的 $3 \times 3$ 矩阵，那么我们可以使用以下关系计算潜在因子，$Y_t = A + B^o x_t^o + B^u x_t^u$。因此，对于如上所述无误差测量的三个收益率，我们有 $x_t^u = B^u^{-1}(Y_t - A + B^o x_t^o)$。剩余的四个收益率将被假设为存在测量误差，因此我们首先定义 $B^m$ 为 $7 \times 4$ 的测量误差项矩阵，$u_t^m$ 是一个包含测量误差的 4 维高斯白噪声向量。基于这些假设，对于剩余的四个收益率 $(y_t^{1\text{yr}}, y_t^{3\text{yr}}, y_t^{5\text{yr}}, y_t^{7\text{yr}})$，我们可以写出，

$$Y_t = A + B^o x_t^o + B^u x_t^u + B^m u_t^m.\tag{61.15}$$

因此，无误差测量的收益率用于如上所述求解 $x_t^u$，而假设存在测量误差的收益率则用于类似的计算中求解 $u_t^m$，

$$u_t^m = (B^m)^{-1}(Y_t - A + B^o x_t^o + B^u x_t^u).\tag{61.16}$$

因此，本质上，我们已将模型从包含收益率和可观测量的系统转换为了包含可观测变量和不可观测变量的系统。收益率以状态变量的闭式表达，因此可用于从收益率中获得不可观测因子。我们将 $(Y_t, x_t^o)$ 转换 为 $(x_t^o, x_t^u)$，因此需要以下雅可比矩阵来促进此转换

$$J = \begin{bmatrix} \frac{\partial x_t^o}{\partial x_t^o} & \frac{\partial x_t^o}{\partial x_t^u} & \frac{\partial x_t^o}{\partial u_t^m} \\ \frac{\partial Y_t}{\partial x_t^o} & \frac{\partial Y_t}{\partial x_t^u} & \frac{\partial Y_t}{\partial u_t^m} \end{bmatrix} = \begin{bmatrix} I_{(24\times24)} & 0_{(24\times3)} & 0_{(24\times4)} \\ B^o_{(7\times24)} & B^u_{(7\times3)} & B^m_{(7\times4)} \end{bmatrix}_{(31\times31)}.$$
