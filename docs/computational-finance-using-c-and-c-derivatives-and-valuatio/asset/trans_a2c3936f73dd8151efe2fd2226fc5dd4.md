

## 7.4.3 总收益互换 (Total Swap)

总收益互换（Total Return Swap, TRS）是对参考资产（债券）$B$ 收益的合成复制。TRS 的接收方在互换存续内接收参考资产的利息支付，作为是按照无风险利率加上约定的利差进行定期的利息支付。在发生违约时，接收方需向支付方支付一笔违约金，金额等于参考资产的约定价格减去违约时的价格，随后交易终止。如果没有发生违约，初始资产（债券）价格 $B_0$ 与到期价格 $B(t_m)$ 之间的差额由支付方和接收方结算，如果（债券）在到期时的价值较低（或更高），则由接收方支付（或收取）。参考资产（债券）的存期限可能长于到期期限 $t_m$。

对于参考资产利息的接收方，TRS 的价值为 $TRS$，其公式为：

$TRS = $ 债券总收益 – 互换的总浮动利息支付
债券总收益 = TRS 存续期间的债券固定利息总和 + TRS 到期时债券价值的增加 – 如果债券在 TRS 存续期间违约的违约金。
在时间 $t$ 的 $TRS_t$ 价值为：

$TRS_{(t)} =$

$= \hat{C} \sum_{t_j=t_1}^{t_m} DF(t,t_j) \quad \text{固定参考债券支付}$
$+ P \left\{ \frac{B(t_m) - B_0}{B_0} \right\} DF(t,t_m) \quad \text{参考债券价值的增长}$
$- \sum_{t_j=t_1}^{t_m} C_j DF(t,t_j) \quad \text{LIBOR+利差的互换浮动支付}$
$- P (1 - R) \sum_{t_j=t_1}^{t_m} DF(t,t_j) \{S(t,t_{j-1}) - S(t,t_j)\} \quad \text{债券违约支付,}$

且参考债券满足：

$B(t_r) = 1$
$B(t_m) = \overline{DF(t_m,R)}t + \hat{C} \sum_{t_j=t_m}^{t_r} DF(t_m,t_j)|t$
$+ R \sum_{t_j=t_m}^{t_r} DF(t_m,t_j)|t S(m,t_{j-1}) - S(m,t_j)\}.$

本章中已定义的所有符号保留其原有含义。对于加法：

$P$ – 互换本金。
$\tilde{C}$ – 参考债券的固定利息。
$t_m$ – 互换到期日。
$t_R$ – 参考债券的到期日。
$B_0$ – 参考债券的初始价格。
$B(t_m)$ – 参考债券的最终价格（互换到期）。
$C_j$ – 时间 $t_j$ 的浮动利息支付。其计算方法为：
$C_j = P\{F(t_{j-1}, t_j) + margin^{TRS}\{t_j - t_{j-1}\}$
$DF(t_1, t_2)$ – 时间 $t_1$ 和 $t_2$ 之间的折现因子（从时间 $t_i$ 观察）为：

$DF(t_1, t_2) = \frac{D(t_2)}{D(t_1)}$

$\overline{DF(t_1, t_2)}|t$ – 时间 $t_1$ 和 $t_2$ 之间的违约折现因子（从时间 $t_i$ 观察）：

$\overline{DF(t_1, t_2)}|t = \frac{DF(t_1, t_2)}{DF(t_1, t_1)}$（此处原文公式存在重复，已按原文保留）

## 7.5 股票衍生品

### 7.5.1 股票互换 (TRS)

TRS 由一个权益部分（其利息由股票价值的变化决定）和一个根据远期利率支付的浮动部分组成。在这里，我们忽略股息的影响，并假设互换两个部分的货币是相同的。

#### 权益部分 (Equity Leg)

设权益部分由时间 $t_k=1, \dots, N_e$ 的利息支付指定，其中 $\tau_k = t_k - t_{k-1}$。如果在时间 $t$ 发生下次利息支付，则权益部分的价值为：

$V_e(t) = \frac{S(t)}{DF(t,t_i)} - L(t_{i-1}) DF(t,t_i) + \sum_{k=i+1}^{N_e} \frac{S(t)}{DF(t,t_k)} \frac{S(t)}{DF(t_{k-1})} DF(t,t_k),$

其中 $S(t)$ 是时间 $t$ 的股票价值，$L(t_{i-1})$ 是时间 $t_{i-1}$ 的权益价值，$DF(t,t_k)$ 是时间 $t$ 和 $t_k$ 之间的折现因子。可以看到，时间 $t_i$ 的股票价值 $S(t_i)$ 是通过将当前价值 $S(t)$ 除以折现因子 $DF(t,t_i)$ 得到的：$S(t_i) = S(t)/DF(t,t_i)$。

#### 浮动部分 (Floating Leg)

设浮动部分由时间 $t_m=1, \dots, N_f$ 的利息支付，其中 $\tau_f = t_m - t_{m-1}$。如果在时间 $t_j$ 发生下次利息，则浮动部分的价值为：

$V_f(t) = L(t_{j-1})(R(t_{j-1}) + \Phi) \tau_f DF(t,t_j) + \sum_{m=j+1}^{N_f} \frac{S(t)}{DF(t,t_{m-1})} \{F(t,t_{m-1}, t_m) + \tau_f DF(t,t_m)\},$

其中 $\Phi$ 是用于计算利息的利差，$F(t,t_{m-1}, t_m)$ 是时间 $t$ 之间 $t_{m-1}$ 和 $t_m$ 之间的远期利率，$R(t_{j-1})$ 是用于在 $t_{j-1}$ 和 $t_j$ 计算支付的重置利率。

#### 支付方权益互换 (Payer Equity TRS)

支付方 TRS 的所有支付权益部分，因此在时间 $t$ 互换的价值为：

$ERS_{Sp}(t) = V_f(t) - V_e(t)$

TRS 的接收方接收权益利息，互换的价值为：

$ERS_{Tc}(t) = -V_f(t) + V_e(t)$

现在我们计算权益互换价值的表达式。由于 $F(t,t_{m-1}, t_m) = \frac{1}{t_m - t_{m-1}} \left( \frac{DF(t,t_{m-1})}{DF(t_m)} - 1 \right)$，我们：

$\tau_f F(t,t_{m-1}, t_m) = \left( \frac{DF(t,t_{m-1})}{DF(t_m)} - 1 \right),$

将方程 (7.5.5) 代入方程 (7.5.2) 并使用方程 (7.5.3)，得到：

$ERS_{Sp}(t) = \sum_{m=j+1}^{N_f} \frac{S(t)DF(t,t_m)}{DF(t,t_{m-1})} - 1\} + \sum_{m=j+1}^{N_f} \frac{S(t)}{DF(t,t_{m-1})} \Phi \tau_f DF(t,t_m) + L(t_{j-1})(R(t_{j-1}) + \Phi) \tau_f DF(t,t_j) - \sum_{k=i+1}^{N_k} \left( 1 - \frac{DF(t,t_k)}{DF(t,t_{k-1})} \right) - \left( \frac{S(t)}{DF(t,t_i)} \right\} DF(t,t_i).$

如果 $N_e = N_f = N$ 且 $\tau_e = \tau_f = \tau$，则所有的权益和浮动部分重合，方程 (7.5.6) 简化为：

$ETRS_p(t) = S(t) \sum_{k=j+1}^{N} \frac{DF(t,t_k)}{DF(t,t_j)} \Phi \tau DF(t,t_k) + L(R + \Phi) \tau DF(t,t_j) - \left\{\frac{S(t)}{DF(t,t_j)} - L\right\}DF(t,t_j).$

因此，如果利差 $\Phi$ 为零，权益互换的价值为：

$ETRS_p(t) = L(t_{j-1}) R(t_{j-1}) \tau DF(t,t_j) - \left\{\frac{S(t)}{DF(t,t_j)} - L\right\}DF(t,t_j).$

在这种情况下，权益互换在时间 $t$ 的价值取决于：

