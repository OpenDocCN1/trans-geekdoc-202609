
这些使用每个节点具有250个分支的单个随机网格计算出的。这些值表明，一个高精度的随机网格产生的结果优于100个低精度网格的平均值。在最后一列中，我们展示了使用6000步二项式网格获得的结果，在该网格中，可以在每个时间步行使期权。二项式期权价值高于真实值（后者仅允许在四个不同的时间行使期权），这与二项式网格额外的灵活性是一致的。

## 5.6 精选练习

- 1. 编写一个程序为贝尔穆德期权定价——与美式期权不同，这些期权只能在特定时间行权。
- 2. 为具有随时间变化的障碍的期权定价——在障碍位置设置网格线。
- 3. 证明跳转概率相等（p = 1/2）的二项式网格具有

$$d = \exp(rddt)\{1 - \sqrt{\exp(\sigma^2 dt) -1}\}$$

和

$$u = \exp(rddt)\{1 + \sqrt{\exp(\sigma^2 dt) -1\}$$

- 4. 证明 $Z_t = \log(S_t)$ 的网格特征特征为

$$\Delta Z = \sqrt{\sigma^2 \Delta t + (r - \frac{\sigma^2}{2})^2 \Delta t^2}$$

和

$$p = \frac{1}{2}\{1 + (r - \frac{\sigma^2}{2})(\frac{\Delta t}{\Delta Z})\}$$

- 5. 为一个执行价格取决于资产价格高于或低于给定障碍水平的期权定价。

## 第 6 章
## 多资产期权

## 6.1 引言

在本节中，我们考虑在 Black-Scholes 定价框架内对多资产、*篮子*期权进行定价。这些期权将使用以下技术进行定价：

- 解析方法。
- 蒙特卡洛方法。
- 多维网格。

解析方法对于具有已知*闭式*解的多资产欧式期权定价非常有用。它们对于低维欧式期权特别适用，当闭式表达式的计算不是过于困难时。

蒙特卡洛方法的优点是可以容易地计算多资产欧式期权的价值，但早期行权的可能性较难；而这是美式期权所必需的。

另一方面，多维网格技术可以轻松地评估美式期权。然而，随着维数的增加，网格的编程变得越来越困难，而且计算机存储的限制将其限制在涉及大约四个或更少资产的问题。

## 6.2 多资产 BLACK–SCHOLES 方程

在第 2 章中，我们提到，当单个资产的价格 $S$ 在时间间隔 $dt$ 内的价格变化 $dS$ 遵循几何布朗运动 (GBM) 时，由：

$$dS = rSdt + \sigma dW$$

其中 $r$ 是无风险利率，$\sigma$ 是资产 $S$ 的波动率，且 $dW \sim N(0,dt)$。

我们还证明了伊藤 引理，$Y = \log(S)$ 所遵循的过程为：

$$dY = (r - \sigma^2/2)dt + \sigma dW$$

其中 $dY$ 是 $\log(S)$ 的值在时间间隔 $dt$ 内的变化。随后，我们推导了针对单个基础资产期权的价值 $V$ 所满足的（Black–Scholes）偏微分方程。该方程为：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

上述结果可以推广到多资产期权。假设 $m$ 个资产遵循以下过程：

$$dY_i=(r-\sigma_i^2/2)dt+\sigma_idW_i, \quad i=1,\dots,m, \quad (6.2.1)$$

其中下标 $i$ 指与第 $i$ 个资产相关的值。$m$ 维随机向量 $dW$ 分布为 $dW \sim N(0,C)$。$C$ 的对角元素为 $C_{ii}=Var[dW_i]=dt, i=1,\dots,m$，非对角元素为：

$$C_{ij}=E[dW_id_j]=\rho_{ij}dt, \quad i=1,\dots,m, \quad i\neq j,$$

我们也可以通过引入 $m$ 维向量 $Y$ 来写上述方程，其分布为：

$$dY\sim N(v,C), \quad (6.2.2)$$

其中 $v$ 是均值向量，$C$ 是协方差矩阵。协方差矩阵的元素为：

$$ \tilde{C}_{ij}=\sigma_i\sigma_j\rho_{ij}dt, \quad i\neq j,i=1,\dots,m,j=1,\dots,m,\quad\quad(6.2.3)$$

其中 $\rho_{ij}$ 是资产 $i$ 与资产 $j$ 之间的相关系数，即 $dW_i$ 与 $dW_j$ 之间的相关性，均值向量 $v$ 为：

$$v_i=r-\sigma_i^2/2, \quad i=1,\dots,m. \quad\quad(6.2.4)$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

针对 $n$ 个资产的期权价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2}+rS\frac{\partial V}{\partial S}-rV = 0$$

（此处省略原文中重复的多次“价值 $V$ 满足以下条件：以及 $\frac{\partial V}{\partial t}+\frac{\sigma^2}{2}\frac{\partial^2 V}{\partial S^2} \dots =0$”部分）

对于 $m$ 个资产的最大值，其收益为 $C = \max(S_1, \dots, S_m) - K$ 或 $\max(S_1, \dots, S_m - K)$，或者对于 $m$ 个资产的最小值，其收益为 $P = \min(S_1, \dots, S_m) - K$ 或 $\min(S_1, \dots, S_m - K)$，价值 $V$ 满足：

$$\frac{\partial V}{\partial t}+\frac{1}{2}\sum_{i=1}^m \sigma_i^2 \frac{\partial^2 V}{\partial S_i^2}+\sum_{i=1}^m \sum_{j \neq i} \sigma_i \sigma_j \rho_{ij} S_i S_j \frac{\partial^2 V}{\partial S_i \partial S_j}+\sum_{i=1}^m r S_i \frac{\partial V}{\partial S_i}-rV = 0$$

对于 $m$ 个资产的最大值和均值向量 $v$ 为：

$$v_i=r-\sigma_i^2/2, \quad i=1,\dots,m.$$

$m$ 个资产的价值 $V$ 满足以下条件：

$$\frac{\partial V}{\partial t}+\frac{1}{2}\sum_{i=1}^m \sigma_i^2 \frac{\partial^2 V}{\partial S_i^2}+\sum_{i=1}^m \sum_{j \neq i} \sigma_i \sigma_j \rho_{ij} S_i S_j \frac{\partial^2 V}{\partial S_i \partial S_j}+\sum_{i=1}^m r S_i \frac{\partial V}{\partial S_i}-rV = 0$$

对于 $m$ 个资产的最大值，其收益为 $C = \max(S_1, \dots, S_m) - K$ 或 $\max(S_1, \dots, S_m - K)$，或者对于 $m$ 个资产的最小值，其收益为 $P = \min(S_1, \dots, S_m) - K$ 或 $\min(S_1, \dots, S_m - K)$，价值 $V$ 满足：

$$\frac{\partial V}{\partial t}+\frac{1}{2}\sum_{i=1}^m \sigma_i^2 \frac{\partial^2 V}{\partial S_i^2}+\sum_{i=1}^m \sum_{j \neq i} \sigma_i \sigma_j \rho_{ij} S_i S_j \frac{\partial^2 V}{\partial S_i \partial S_j}+\sum_{i=1}^m r S_i \frac{\partial V}{\partial S_i}-rV = 0$$

## 6.3 多维蒙特卡洛

此外，蒙特卡洛模拟可以包括：

- 具有路径依赖的收益率；具有厚尾的通常被称为障碍期权。
- 复杂时间依赖（例如 ARMA, GARCH 或  过程）的市场参数。
蒙特卡洛的主要缺点是：

- 计算美式期权的价值很困难。
- 无法通过有限差分法达到相同的精度。

## 6.4 方差减小技术

| 数量 | 标准方法 | 对立变量 | 控制变量 | Sobol |
|---|---|---|---|---|
| 500 | 0.0456 | 0.0213 | 0.0124 | 0.0054 |
| 1000 | 0.0312 | 0.0156 | 0.0087 | 0.0031 |
| 1500 | 0.0268 | 0.0134 | 0.0076 | 0.0025 |
| 2000 | 0.0234 | 0.0117 | 0.0066 | 0.0019 |
| 2500 | 0.0208 | 0.0104 | 0.0059 | 0.0015 |
| 3000 | 0.0189 | 0.0095 | 0.0053 | 0.0013 |

方差减小的目标是在不显著增加模拟次数的情况下减少蒙特卡洛估计器的方差。常用的技术有：

- 对立变量
- 控制变量
- 性采样
- 拟蒙特卡洛方法（使用 Sobol 序列）
