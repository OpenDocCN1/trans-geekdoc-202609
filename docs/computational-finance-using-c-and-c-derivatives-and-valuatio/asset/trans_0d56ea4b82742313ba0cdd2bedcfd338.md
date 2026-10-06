

# 212 章 | 7 其他金融衍生品

一种在到期日 $t_i$ 通过 $DF(t,t_i)$ 支付 1 个货币单位的零票息债券。为了方便起见，我们还将使用简记符号 $F_k = F(t,t_{k-1},t_k)$ 和 $DF_i = DF(t,t_i)$。

所有可交易资产相对于零票息债券价格 $DF_k$ 进行定价的概率测度（即 $DF_k$ 是计价基）将记为 $Q^k$；在该测度下，相对价格为鞅。我们将布朗运动记为 $W^t$。

### 情况 $i = k$

在这里，$DF_k$ 作为计价基在远利率 $F_k$ 到期。

由于 $DF_k(1+\tau F_k)$ 是可交易价格，$(1+\tau F_k)/DF_k$ 在 $Q^k$ 下是鞅。

此外，由于 $DF_k(1+\tau F_k)/DF_k = 1+\tau F_k$，且 $\tau$ 和 $1$ 是常数，$F_k$ 在 $Q^k$ 下必须是鞅。$F_k$ 的过程漂移项为零

$dF_k = F_k\sigma_kW_k$

对于 $i \neq k$ 的一般情况，$F_k$ 的过程为：

$dF_k = F_k\mu_k dt + F_k\sigma_kW^k$

其中 $\mu_k$ 需要待确定。方程 (7.2.41) 可以重写为：

$dF_k = F_k\sigma_k \left(\frac{\mu_k}{\sigma_k} dt + dW^i\right)$

比较方程 (7.2.41) 和 (7.2.42)，我们得到：

$dW^k = \left(\frac{\mu_k}{\sigma_k}\right) dt + dW^i$

该方程给出了概率测度 $Q^k$ 下布朗运动之间的关系。我们现在将展示如何计算 $\mu_k$ 的值。

### 情况 $i < k$

在这里，我们考虑 $DF_i$ 在远利率 $F_i$ 到期之前的情况。

#### 情况 $i = k-1$

在这种情况下，$DF_{k-1}$ 是计价基，远利率为 $F_k = F(t,t_{k-1},t_k)$，计价基在时间 $t_{k-1}$ 到期，而远利率在 $t_k$ 到期。

由于 $DF_k$ 是可交易价格，$\phi = DF_k/DF_{k-1}$ 在 $Q^{k-1}$ 下是鞅，因此漂移为零。

现在：

$\phi = \frac{DF_k}{DF_{k-1}} = \frac{1}{1+\tau F_k}$

$DF_{k-1} = DF_k(1+\tau F_k)$

其中我们使用的 $Q^{k-1}$ 下 $F_k$ 的随机过程为：

$dF_k = F_k\mu_k dt + F_k\sigma_kW^{k-1}$

且漂移项 $\mu_k$ 待确定。

# 利率衍生品节 | 7.2 213

使用伊藤 公式，我们有：

$d\phi = \frac{\partial\phi}{\partial F_k}dF_k + \frac{1}{2}\frac{\partial^2\phi}{\partial F_k^2}E[(dF_k)^2], \text{ 其中 } E[(dF_k)^2] = \sigma_k^2 F_k^2 dt, \quad (7.2.47)$

其中根据方程 (7.2.44)：

$\frac{\partial\phi}{\partial F_k} = -\frac{\tau}{(1+\tau F_k)^2}, \quad \frac{\partial^2\phi}{\partial F_k^2} = \frac{2\tau^2}{(1+\tau F_k)^2}. \quad (7.2.48)$

将 (7.2.48) 中的值代入 (7.2.47)，得到：

$d\phi = -\frac{\tau}{(1+\tau F_k)}F_k\mu_k dt + F_k\sigma_kW^{k-1} + \frac{1}{2}\frac{\tau^2\sigma_k^2 F_k^2}{(1+\tau F_k)^2}.$

可以重新排列为：

$d\phi = -\frac{\tau F_k\mu_k}{1+\tau F_k}dt + \frac{\tau^2\sigma_k^2 F_k^2}{(1+\tau F_k)^2}dt - \frac{\tau F_k\sigma_k}{1+\tau F_k}dW^{k-1}. \quad (7.2.49)$

现在由于方程 (7.2.49) 无漂移：

$$-\frac{\tau F_k\mu_k}{1+\tau F_k} + \frac{\tau^2\sigma_k^2 F_k^2}{(1+\tau F_k)^2}dt = 0$$

且：

$\mu_k = \frac{\tau\sigma_k^2 F_k^2}{1+\tau F_k}. \quad (7.2.50)$

将方程 (7.2.50) 代入方程 (7.2.46)：

$dF_k = \frac{\tau\sigma_k^2 F_k^2}{1+\tau F_k}dt + F_k\sigma_kW^{k-1}$

或者：

$dF_k = F_k\sigma_k \frac{\tau F_k}{1+\tau F_k}dt + F_k\sigma_kW^{k-1}. \quad (7.2.51)$

比较方程 (7.2.51) 和 (7.2.40)，得到：

$dW^k = \frac{\tau F_k}{1+\tau F_k}dt + dW^{k-1}. \quad (7.2.52)$

这是在概率测度 $Q^{k-1}$ 和 $Q^k$ 下布朗运动 $dW^{k-1}$ 和 $dW^k$ 之间的关系。让 $Q^{k-2}$ 下 $F_k$ 的随机过程为：

$dF_k = F_k\mu_k dt + F_k\sigma_kW^{k-2}. \quad (7.2.53)$

其中 $dW^{k-2}$ 是概率测度 $Q^{k-2}$ 下的布朗运动，且漂移 $\mu_k$ 未知。

# 214 章 | 7 其他金融衍生品

在方程 (7.2.52) 中将 $k$ 替换为 $k-1$：

$dW^{k-1} = \frac{\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}dt + dW^{k-2}, \quad (7.2.54)$

并利用 (7.2.54) 替换方程 (7.2.52) 中的 $dW^{k-1}$，得到：

$dW^k = \frac{\tau F_k}{1+\tau F_k}dt + \frac{\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}dt + dW^{k-2}, \quad (7.2.55)$

将方程 (7.2.40) 中的 $dW^k$ 替换为 (7.2.55) 给出的表达式：

$dF_k = F_k\sigma_k\left(\frac{\tau F_k}{1+\tau F_k}dt + \frac{\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}dt\right), \quad (7.2.56)$

因此漂移为：

$\mu_k = \frac{\sigma_k^2 F_k}{1+\tau F_k} + \frac{\sigma_k\sigma_{k-1}F_{k-1}}{1+\tau F_{k-1}}, \quad (7.2.57)$

通用表达式可以以类似的方式推导出：

$dF_k = F_k\sigma_k \sum_{j=i+1}^k \frac{\sigma_j F_j}{1+F_j}dt + \sigma_kW^i, \quad (7.2.58)$

其中所有符号与之前相同，但 $i$ 可以取小于 $k$ 的任何整数。

### 情况 $i > k$

我们现在考虑计价基 $DF_i$ 在远利率 $F_k$ 到期之后的情况。

### 情况 $i = k+1$

在这里，$DF_{k+1}$ 是计价基，$F_k$ 是从 $t_{k-1}$ 开始在 $t_k$ 结束的远利率。由于 $DF_{k-1}$ 是可交易的，其相对价格 $\phi = DF_{k-1}/DF_{k+1}$ 在 $Q^{k+1}$ 下是鞅，因此漂移为零。

现在：

$\phi = \frac{DF_{k-1}}{DF_{k+1}} = (1+\tau F_k)(1+\tau F_{k+1}), \quad (7.2.59)$

其中 $F_k$ 和 $F_{k+1}$ 的过程为：

$dF_k = F_k(1+\tau F_k)\sigma_kW^{k+1}, \quad (7.2.60)$

$dF_k = F_k\mu_k dt + F_k\sigma_kW^{k+1}, \quad (7.2.61)$

且漂移项 $\mu_k$ 待确定。使用伊藤 公式，我们有：

$\phi = \frac{\partial\phi}{\partial F_k}dF_k + \frac{\partial\phi}{\partial F_{k+1}}dF_{k+1} + \frac{1}{2}\sum_{i=k}^{k+1} \sum_{j=k}^{k+1} \frac{\partial^2\phi}{\partial F_i\partial F_j}E[dF_i, dF_j], \quad (7.2.62)$

# 利率衍生品节 | 7.2 215

其中：

$\frac{\partial\phi}{\partial F_k} = \tau(1+\tau F_{k+1}), \quad \frac{\partial\phi}{\partial F_{k+1}} = \tau(1+\tau F_k)$

$\frac{\partial^2\phi}{\partial F_k^2} = 0, \quad \frac{\partial^2\phi}{\partial F_{k+1}^2} = 0, \quad \frac{\partial^2\phi}{\partial F_k\partial F_{k+1}} = \tau^2$

将 (7.2.63) 中的值代入 (7.2.62)，在展开 $d\phi$ 和 $dF_k$ 后，我们得到：

$E[dF_k, dF_{k+1}] = \rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt, \quad (7.2.63)$

$d\phi = D + (1+\tau F_{k+1})F_k\sigma_kW^{k+1} + \tau(1+\tau F_k)F_{k+1}\sigma_{k+1}, \quad (7.2.64)$

其中方程 (7.2.64) 中的漂移项 $D$ 为：

$D = (1+\tau F_{k+1})F_k\mu_k dt + \tau^2\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt. \quad (7.2.65)$

现在由于 $\phi$ 在 $Q^{k+1}$ 下是鞅，我们知道 $D=0$，因此方程 (7.2.65) 导致：

$(1+\tau F_{k+1})F_k\mu_k dt = -\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}dt. \quad (7.2.66)$

这意味着漂移为：

$$\mu_k = \frac{-\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{1+\tau F_{k+1}}. \quad (7.2.67)$$

将 $\mu_k$ 代入方程 (7.2.61)：

$dF_k = F_k\sigma_k \left( \frac{-\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1} dt + dW^{k+1}}{1+\tau F_{k+1}} \right). \quad (7.2.67)$

比较方程 (7.2.67) 和方程 (7.2.40)，得到：

$dW^k = \frac{-\rho_{k,k+1}\sigma_k\sigma_{k+1}F_{k+1}}{1+\tau F_{k+1}}dt + dW^{k+1}. \quad (7.2.68)$

这是布朗运动 $dW^k$ 和 $dW^{k+1}$ 之间的关系。

### $i \ge 2$

让 $Q^{k+2}$ 下 $F_k$ 的随机过程为：

$dF_k = F_k\mu_k dt + F_k\sigma_kW^{k+2}. \quad (7.2.69)$

