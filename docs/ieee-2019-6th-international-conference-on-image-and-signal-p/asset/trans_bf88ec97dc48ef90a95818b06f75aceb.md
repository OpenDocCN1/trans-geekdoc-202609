

# IEEE Access F. Muhammad - 带有干扰管理的解耦 DL-UL 覆盖分析

表 1. 符号汇总。

| 参数 | 语义 |
| :--- | :--- |
| $\Theta_M, \Theta_S, \Theta_U$ | 分别为 MBS、SBS 和用户位置的泊松点过程 (PPPs) |
| $\sigma$ | 接收端的噪声功率 |
| $P_{TM}, P_{SU}, P_{UL}$ | 分别为服务性 MBS、SBS 和用户的发射功率 |
| $\lambda_M, \lambda_S, \lambda_U$ | 分别为 MBS、SBS 和用户的空间密度 |
| $P_{DL}$ | 分别为服务性 MBS 和 SBS 接收到的 DL 功率 |
| $P_{UL}$ | 分别为从用户处服务性 MBS 和 SBS 接收到的 UL 功率 |
| $\alpha_M, \alpha_S, \alpha_U$ | 分别为 MBS 和 SBS 的路损，其中 $\alpha_M = \alpha_S > \alpha_U$ |
| $\beta_M, \beta_S$ | 分别为 MBS 和 SBS 的信噪比 (SINR) |
| $R^{(in)}, R^{(out)}$ | 分别为小区内和小区外区域 |
| $Y_M, Y_S$ | 分别为到服务性 MBS 或服务性 SBS 的统计距离 |
| $T_{UE}$ | 分别为 TUE 中的时间 |
| $M_{BS}$ | 分别为 MBS 和 SBS 的关联偏置 |
| $P_{v,u}^{(j)}, P_{v,decouple}^{(j)}$ | 分别为目标信号和干扰信道的衰落方差 |
| $C_v^{(j)}$ | 分别为关联到 $v$ 个解耦接入 SBS 的第 $j$ 个小区 TUE 的覆盖概率 |

![](img/50c5c77000cc0e118c831908687e75a5_2_0.png)

比 $R^{(out)}$ 高。所提出的两级集在 $R^{(in)}$ 和 $R^{(out)}$ 中的频谱划分如图 1 所示。

![](img/50c5c77000cc0e118c831908687e75a5_2_1.png)

图 1. $R^{(in)}$ 和 $R^{(out)}$ 中带有 DL 和 UL 子载波的 RFA 方案频谱划分。

然而，$R^{(out)}$ 被视为小区边缘，其中 MBS 对其关联用户的覆盖较差。同样，总频谱被分为两个子载波，$i.BW_1$ 和 $BW_2$，其中 $BW_1 = BW_{1,DL} + BW_{1,UL}$ 分别分配给 $R^{(in)}$ 和 $R^{(out)}$ 中的 MBS 带宽。$BW_2$ 和 $BW_3$，其中 $BW_2 = BW_{2,DL} + BW_{2,UL}$ 分别是 $R^{(in)}$ 和 $R^{(out)}$ 中的 MBS 载波。$BW_1$ 和 $BW_2$ 中的 MBS 子频谱被用作 SBS 子频谱 $BW'_1$ 和 $BW'_2$，其中 $BW'_j = BW_{j,UL}$。而 $R^{(in)}$ 和 $R^{(out)}$ 的 UL 和 DL 子载波表示为 $BW_1 = BW_{2,UL} + BW_{2,DL}$。SBS 以反方向使用 $R^{(in)}$ 中的 UL 和 DL 子载波。

图 2. 带有 Co-DU 和 De-DU 的网络布局。

所提出的带有 Co-DU 和 De-DU 的两级网络设置的频谱划分如图 2 所示。$R^{(in)}$ 和 $R^{(out)}$ 区域分别为 $0 \leq D \leq d_1$ 和 $d_1 \leq d_2$。显示了 TUE 与 $v$ 个 SBS（$v=\{M, S\}$）之间的各种 DL、UL（实线）以及干扰信道（虚线）。根据 MPR 策略，$R^{(in)}$ 中的用户在 UL 和 DL 方向上都关联到 SBS-2。对于 DL 传输，它接收来自同一区域内 SBS-1 的 DL 干扰（记为 $IdL_1$），以及来自位于 $R^{(out)}$ 中的 SBS-1 的 UL 干扰（记为 $IUL_1$）。

在 $R^{(out)}$ 中，根据路损 (PL) 关联策略，它在同一区域的 UL 方向关联到 SBS-2，在 DL 方向关联到 $R^{(in)}$ 中的 MBS-1。对于传输，它接收来自 $R^{(out)}$ 中关联到 SBS 的所有其他用户的 DL 干扰（记为 $I_{ij}$）以及来自 $R^{(in)}$ 中 MBS-1 的干扰。通过 MCI减轻，由于不需要额外的 SBS 频谱，Rafa 方案提高了频谱效率。

# III. 解耦关联的统计

在本节中，我们分析了 SINR 分布并定义了基于上行的关联规则。分析了所提模型的性能。

## A. 解耦关联的干扰

给定 $R^{(0)}$, $\tau \in \{in, out\}$：

+ 1) 解耦关联的干扰 $I_{R^{(0)}},dec}$（见 1）：当 $R^{(0)}$ 中的 UE 在 DL 和 UL 方向都关联到 vBS 时，它会受到位于 $R^{(0)}$ 中的 vBS 的 DL 干扰以及关联到 vBS 的用户的干扰，$v, \tau \in \{M, S\}$。

+ 2) 解耦关联的干扰 $I_{R^{(0)}}\tau,dec}$（见 2）：如果 $R^{(0)}$ 中的 UE 在 DL 方向和 UL 方向都关联到 vBS，它会接收来自 $R^{(0)}$ 中所有 vBS（除服务性 vBS 外）的 DL 干扰以及来自 $R^{(0)}$ 中用户的干扰。然而，在 UL 中，UE 接收来自 $R^{(0)}$ 中所有用户的干扰，$v, \in \{M, S\}$。

## B. 耦合/解耦关联的信干扰比分析

根据页面顶部的 (1) 和 (2)，对所提模型分析 Co-DU 和 De-DU 的 SINR 分布，给定 UE 位于 $R^{(0)}$。

+ 1) 耦合关联的 SINR 分析 $S_{R^{(0)}}$（见 3）：当 $R^{(0)}$ 中的 UE 在 DL 和 UL 方向都关联到 vBS 且 SBS 建模时（如顶部所示），其中 $\sigma^2$ 代表接收到的功率。在 DL 传输中，来自 $R^{(0)}$ 中 vBS 的 DL 干扰表示为 $\sum_{\tau \in \{in, out\}} P_{\tau,R^{(0)}} |H_{R^{(0)}}}^{(\tau)}|^2$，来自 $R^{(0)}$ 中用户的 UL 干扰表示为 $\sum_{\tau \in \{in, out\}} P_{\tau,R^{(0)}} |H_{R^{(0)}}}^{(\tau)}|^2$。在 UL 传输中，来自 $R^{(0)}$ 中 vBS 的 DL 干扰表示为 $\sum_{\tau \in \{in, out\}} P_{\tau,R^{(0)}} |H_{R^{(0)}}}^{(\tau)}|^2, H_{R^{(0)}}^{UL}$。

+ 2) 解耦关联的 SINR 分析（见 4）：当 $R^{(0)}$ 中的 UE 在 DL 和 UL 方向都关联到 vBS 时，对解耦接入建模 SINR 分布（如页页所示）。在 DL 传输中，来自 $R^{(0)}$ 中 vBS 的 DL 干扰表示为 $\sum_{\tau \in \{in, out\}} P_{\tau,R^{(0)}} |H_{R^{(0)}}}^{(\tau)}|^2, H_{R^{(0)}}^{UL}$，来自 $R^{(0)}$ 中用户的 UL 干扰可以表示为 $\sum_{\tau \in \{in, out\}} P_{\tau,R^{(0)}} |H_{R^{(0)}}}^{(\tau)}|^2$。在 UL 传输中，来自 $R^{(0)}$ 中 vBS 的 DL 干扰建模为 $\sum_{\tau \in \{in, out\}} P_{\tau,R^{(0)}} |H_{R^{(0)}}}^{(\tau)}|^2, H_{R^{(0)}}^{UL}$。

## C. 解耦/解耦关联的 SBS 基关联方案

Co-DU 中的用户关联（UE 在 DL 和 UL 关联到特定的 BS）基于偏置 MPR 关联方案 [7], [8]。该 BS（UE 关联的 BS）的位置表示为
$\omega = \arg \max_{v \in \{M,S\}} T_v \|Y_v\|^{-\alpha}$。

# IEEE Access F. Muhammad 等：带有干扰管理的解耦 DL-UL 覆盖分析

$I_{v,coup}^{R^{(i)}} = \begin{cases} \sum_{j \in \Xi(i) \setminus \{v\}} T_v P_{H_j}^{R^{(i)}} \|x_j\|^{-\alpha} + \sum_{j \in \Upsilon(i) \setminus \{v\}} P_{H_j}^{R^{(i)}} \|y_j\|^{-\alpha} & \text{对于 DL, \\ \sum_{j \in \Upsilon(i) \setminus \{v\}} P_{H_j}^{R^{(i)}} \|y_j\|^{-\alpha} + \sum_{j \in \Xi(i) \setminus \{v\}} T_v P_{H_j}^{R^{(i)}} \|x_j\|^{-\alpha} & \text{对于 UL.} \end{cases} \quad (1)$

$I_{v,t,dec}^{R^{(i)}} = \begin{cases} \sum_{j \in \Xi(i) \setminus \{v\}} T_v P_{H_j}^{R^{(i)}} \|x_j\|^{-\alpha} + \sum_{j \in \Upsilon(i) \setminus \{v\}} P_{H_j}^{R^{(i)}} \|y_j\|^{-\alpha} & \text{对于 DL, \\ \sum_{j \in \Upsilon(i) \setminus \{v\}} P_{H_j}^{R^{(i)}} \|y_j\|^{-\alpha} + \sum_{j \in \Xi(i) \setminus \{v\}} T_v P_{H_j}^{R^{(i)}} \|x_j\|^{-\alpha} & \text{对于 UL.} \end{cases} \quad (2)$

$SINR_{v,coup}^{R^{(i)}} \geq SINR_{v,t,dec}^{R^{(i)}} = \begin{cases} \sigma^2 + \sum_{j \in \Xi(i) \setminus \{v\}} T_v P_{H_j}^{R^{(i)}} \|x_j\|^{-\alpha} + \sum_{j \in \Upsilon(i) \setminus \{v\}} P_{H_j}^{R^{(i)}} \|y_j\|^{-\alpha} & \text{对于 DL, \\ \sum_{j \in \Upsilon(i) \setminus \{v\}} P_{H_j}^{R^{(i)}} \|y_j\|^{-\alpha} + \sum_{j \in \Xi(i) \setminus \{v\}} T_v P_{H_j}^{R^{(i)}} \|x_j\|^{-\alpha} & \text{对于 UL.} \end{cases} \quad (3)$

# IV. 用户关联概率

在本节中，我们描述关联概率定义为 UE 被特定层级服务的概率。为了推导关联概率，我们首先测量 UE 与服务 BS 之间的距离分布 $y_v$，即用户关联到 $v$。考虑 $Y_v$ 为表示到最近 BS 统计距离的随机变量。由于 BS 部署通过泊松点过程 [20]，利用 $Y_v$ 的概率密度函数 (PDF) 可得：

$f_v(y_v) = \lambda_v e^{-\lambda_v y_v^{\alpha_v}}, \forall v \in \{M, S\}. \quad (7)$

我们在多区域环境中使用 RFA 方案来减少区域干扰。此外，我们将可用区域分为两个区域，$R^{(1)}$ 和 $R^{(2)}$。关联概率的：

+   位于 $R^{(i)}$ 的 UE 与服务 $v$ BS 之间的距离 $y_v$ 分布为

$f_{y_v|TUE \in R^{(i)}}(y_v) = \frac{2\lambda_v e^{-\lambda_v y_v^{\alpha_v}}}{1 - e^{-\lambda_v d_i^{\alpha_v}}}, \forall v \in \{M, S\}. \quad (8)$

6254

VOLUME 4, 2016

