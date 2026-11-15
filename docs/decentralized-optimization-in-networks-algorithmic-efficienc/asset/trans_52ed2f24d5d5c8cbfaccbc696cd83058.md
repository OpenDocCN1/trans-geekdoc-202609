

### 证明。

在此，我们的目标是确定 $\hat{\alpha}$ 和 $\beta$ 的适当范围，使得 $\rho(\mathbf{G}_{\hat{\alpha}, \beta}) < 1$。借助 [49] 中的引理 13，我们观察到，对于一个五维正向量 $\boldsymbol{\gamma} = [\gamma_1, \gamma_2, \gamma_3, \gamma_4, \gamma_5]^{\mathrm{T}}$，若 $\rho(\mathbf{G}_{\hat{\alpha}, \beta})\boldsymbol{\gamma} \prec \boldsymbol{\gamma}$，则意味着 $\rho(\mathbf{G}_{\hat{\alpha}, \beta}) < 1$。基于此，我们可以推导出以下不等式组：

$\beta(\gamma_3\sigma + \gamma_5\hat{\alpha}|s|) < \gamma_1(1 - \sigma) - C\hat{\alpha}, \quad (2.19\text{a})$
$\beta a_1(\gamma_3 + \gamma_5\hat{\alpha}|s|) < \gamma_2(1 - \lambda) - (\gamma_1\hat{\mathrm{g}} + \gamma_4 a_1)\hat{\alpha}, \quad (2.19\text{b})$
$\beta(\gamma_3 a_2 + \gamma_5\hat{\alpha}|s|) < \gamma_3 - a_3\gamma_1 - C\hat{\alpha}, \quad (2.19\text{c})$
$\hat{\mathrm{g}}\beta(\gamma_3 a_2 + \gamma_5\hat{\alpha}|s|) < \gamma_4(1 - \sigma) - \gamma_1\hat{\mathrm{g}}\hat{a}_3 - \hat{\mathrm{g}}C\hat{\alpha}, \quad (2.19\text{d})$
$\hat{\mathrm{g}}\beta(\gamma_3 a_2 + \gamma_5\hat{\alpha}|s|) < \gamma_5 - \gamma_1\hat{\mathrm{g}}\hat{a}_3 - a_3\gamma_4 - \hat{\mathrm{g}}C\hat{\alpha}, \quad (2.19\text{e})$

其中 $C = \hat{\mathrm{g}}\sqrt{n}\gamma_1 + \hat{\mathrm{g}}\sqrt{n}\gamma_2 + \hat{\mathrm{g}}\hat{a}_3$。初步，我们消去 (2.19b) 中的 $\lambda$。假设 $\hat{\alpha} < \mu$，根据引理 2.5，我们可推导出 $\lambda = 1 - \frac{\mathbb{1}_n^{\mathrm{T}}\mathrm{diag}(\boldsymbol{\alpha})\mathbb{1}_n}{nL} \leqslant 1 - \frac{1}{L}\hat{\alpha}$。因此，(2.19b) 可简化为

$\beta a_1(\gamma_3 + \gamma_5\hat{\alpha}|s|) < \gamma_2\frac{1}{L}\hat{\alpha} - (\gamma_1\hat{\mathrm{g}} + \gamma_4 a_1)\hat{\alpha}. \quad (2.20)$

由于上述不等式（即 (2.19a)、(2.19c)、(2.19d)、(2.19e) 和 (2.20)）的右边均为正值，因此可以推导出

$\hat{\alpha} < \frac{\gamma_1(1 - \sigma)}{C}, \quad (2.21\text{a})$
$\hat{\alpha} < \frac{\gamma_3 - a_3\gamma_1}{C}, \quad (2.21\text{b})$
$\hat{\alpha} < \frac{\gamma_4(1 - \sigma) - \gamma_1\hat{\mathrm{g}}\hat{a}_3}{\hat{\mathrm{g}}C}, \quad (2.21\text{c})$
$\hat{\alpha} < \frac{\gamma_5 - \gamma_1\hat{\mathrm{g}}\hat{a}_3 - a_3\gamma_4}{\hat{\mathrm{g}}C}, \quad (2.21\text{d})$
$\gamma_2 > L(\gamma_1\hat{\mathrm{g}} + \gamma_4 a_1). \quad (2.21\text{e})$

为确保 $\hat{\alpha}$ 保持为正，我们可按如下方式确定 $\gamma_1$ 范围的上限：

$\gamma_1 < \min \left\{ \frac{\gamma_3}{a_3}, \frac{\gamma_4(1 - \sigma)}{\hat{\mathrm{g}}\hat{a}_3}, \frac{\gamma_5 - a_3\gamma_4}{\hat{\mathrm{g}}\hat{a}_3} \right\}. \quad (2.22)$

随后，我们将从 $\gamma_1$ 到 $\gamma_5$ 分配不同的值。我们将 $\gamma_1$ 和 $\gamma_2$ 与定理 2.1 中规定的值保持一致。通过整合 $\gamma_1$ 和 $\gamma_2$ 的允许范围，我们赋予 $\gamma_3 = a_3, \gamma_4 = \hat{\mathrm{g}}a_3, \gamma_5 = \hat{\mathrm{g}}a_3 + a_3\gamma_4$。将这些值代入不等式 (2.19) 和 (2.21) 后，我们可以确定 $\hat{\alpha}$ 和 $\beta$ 的适当范围。

借鉴前一证明的基础，我们随后建立了 ET-PDA 的总体线性收敛速率。对于所有 $t > 0$，我们按照 (2.16) 中定义的递归关系进行如下迭代：

\[
\mathbf{v}^t \leqslant \mathbf{G}_{\hat{\alpha}, \beta}^t \mathbf{v}_0 + \sum_{l=0}^{t-1} \mathbf{G}_{\hat{\alpha}, \beta}^{t-l-1} \mathbf{b}^l.
\]

若 $\rho(\mathbf{G}_{\hat{\alpha}, \beta}) < 1$，则可推导出 $\|\mathbf{G}_{\hat{\alpha}, \beta}^t\| \leqslant Q(\kappa_2)^t$、$\|\mathbf{G}_{\hat{\alpha}, \beta}^{t-l-1} \mathbf{b}^l\| \leqslant Q(\kappa_2)^t$，其中 $Q$ 为某常数，且 $0 < \max\{\kappa_1, \rho(\mathbf{G}_{\hat{\alpha}, \beta})\} \leqslant \kappa_2 < 1$。因此，(2.23) 可重新表述如下：

\[
\begin{aligned}
\|\mathbf{v}^t\| &\leqslant \|\mathbf{G}_{\hat{\alpha}, \beta}^t\|\|\mathbf{v}^0\| + \sum_{l=0}^{t-1} \|\mathbf{G}_{\hat{\alpha}, \beta}^{t-l-1} \mathbf{b}^l\| \\
&\leqslant Q\|\mathbf{v}^0\|(\kappa_2)^t + \sum_{l=0}^{t-1} Q(\kappa_2)^t = w^t(\kappa_2)^t,
\end{aligned}
\]

其中 $w^t = Q\|\mathbf{v}^0\| + Qt$。对于 $\kappa_2 < \kappa_3 < 1$，极限等式可表示为 $\lim_{t \to \infty} \|\mathbf{v}^t\|/(\kappa_3)^t = w^t(\kappa_2/\kappa_3)^t = 0$。在此，给定一个正常数 $Q_1$ 和一个极小常数 $r$，可得出 $\|\mathbf{v}_t\| \leqslant Q_1(\kappa_4)^t$，其中 $\kappa_4 = \kappa_3 + r$。定理 2.1 的证明至此结束。

### 注释 2.5。

定理 2.1 阐明，尽管引入了事件触发机制，ET-PDA 仍能在最大步长 $\hat{\alpha}$ 和动量系数 $\beta$ 在指定条件集内得到妥善调节的前提下，保持向最优经济调度解线性收敛的能力。此外，与触发条件相关的两个主要参数 $E$ 和 $\kappa_1$ 的选取相对简单，从而便于算法的实现。

### 定理 2.2。

在假设 2.1–2.3 的条件下，并假设序列 $\{\mathbf{x}^t\}$、$\{\mathbf{\theta}^t\}$、$\{\mathbf{y}^t\}$、$\{\hat{\mathbf{y}}^t\}$ 和 $\{\mathbf{z}^t\}$ 根据 (2.10) 或 (2.12) 进行迭代更新，若 $\hat{\alpha}$ 和 $\beta$ 的值遵循定理 2.1 的规定，则序列 $\{\mathbf{x}^t\}$ 将以 $O((\rho(\mathbf{G}_{\hat{\alpha}, \beta})/2)^t)$ 的收敛速率收敛至最优解 $\mathbf{x}^*$。

### 证明。

与众多受约束的去中心化算法 [17, 35, 42, 43] 类似，我们的分析通过审视原始变量与拉格朗日乘数之间的相互作用，深入探讨了原始变量序列的收敛速率。证明该定理的关键在于建立以下不等式：

\[
\sum_{i=1}^n \frac{\mu_i}{2}(x_i^{t+1} - x^*) \leqslant \sum_{i=1}^n (\nabla q_i(\theta^*)(\theta_i^t - \theta^*) + \frac{1}{2\mu_i}(\theta_i^t - \theta^*) + \theta_i^t(x_i^* - c_i).
\]

鉴于 $x^*$ 代表问题 (2.2) 的最优解集，故最优变量与常数之间的差值之和为零，*即*，$\sum_{i=1}^n (x_i^* - c_i) = 0$。此外，当 $\hat{\alpha}$ 和 $\beta$ 均满足定理 2.1 的先决条件时，我们可推断 $\theta_i^t$ 收敛至 $\theta^*$。因此，当 $t$ 趋于无穷大时，(2.25) 的右边趋于零，表明序列 $\{x^t\}$ 以 $O((\rho(\mathbf{G}_{\hat{\alpha}, \beta})/2)^t)$ 的速率收敛至 $x^*$。定理 2.2 的证明至此完成。

### 注释 2.6。

利用定理 2.1 中规定的 $\hat{\alpha}$ 和 $\beta$ 的界限，我们在定理 2.2 中展示了序列 $\{x^t\}$ 向 $x^*$ 收敛的结果。值得注意的是，定理 2.1 中提到的参数 $\gamma_1$、$\gamma_2$、$\gamma_3$、$\gamma_4$ 和 $\gamma_5$ 可调节，其具体值由网络拓扑和相关成本函数决定。

### 定理 2.3。

在假设 2.1–2.3 的前提条件满足，且 $\hat{\alpha}$ 和 $\beta$ 按照定理 2.1 的要求选取的情况下，当 $E > (3Q_1 + 2Q_1 L)(1 + (\kappa_1)^2) / (\kappa_1)^2$ 时，对所有 $i \in \mathcal{V}$ 以及任意 $t > 0$，均有 $t_i^{k(i,t)+1} - t_i^{k(i,t)} \gg 2$ 成立。

### 证明。

依据由 (2.9) 表示的测量误差以及定理 2.1 中概述的约束 $\|\mathbf{v}^t\| \leqslant Q_1(\kappa_4)^t$，我们可以推断出

\[
\begin{aligned}
\|\epsilon_{i,o}^t\| + \|\epsilon_{i,z}^t\| \\
= \|\theta_i^{k(i,t)} - \theta_i^t\| + \|z_i^{k(i,t)} - z_i^t\| \\
\leqslant \|\theta_i^{k(i,t)} - \bar{\theta}_i^{k(i,t)}\| + \|\bar{\theta}_i^{k(i,t)} - \bar{\theta}^t\| + \|\bar{\theta}^t - \bar{\theta}_i^t\| \\
+ \|z_i^{k(i,t)} - \bar{z}_i^{k(i,t)}\| + \|\bar{z}_i^{k(i,t)} - \bar{z}^t\| + \|\bar{z}^t - z_i^t\| \\
\leqslant (3Q_1 + 2Q_1 L)(\kappa_4)^{t_i^{k(i,t)}} + (3Q_1 + 2Q_1 L)(\kappa_4)^t.
\end{aligned}
\tag{2.26}
\]

重新审视触发条件 (2.8)，随后得到

\[
E(\kappa_1)t_i^{k(i,t)+1} \leqslant (3Q_1 + 2Q_1 L)(\kappa_1)^{t_i^{k(i,t)+1}} + (3Q_1 + 2Q_1 L)(\kappa_1)^{t_i^{k(i,t)}}.
\tag{2.27}
\]

鉴于 $\kappa_1$ 小于 $\kappa_4$，出现以下不等式：

\[
t_i^{k(i,t)+1} - t_i^{k(i,t)} \geqslant \frac{\ln \frac{(3Q_1 + 2Q_1 L)}{E - (3Q_1 + 2Q_1 L)}}{\ln \kappa_1}.
\tag{2.28}
\]

只要 $E$ 落在定理 2.3 规定的范围内，则假设 $t_i^{k(i,t)+1}$ 与 $t_i^{k(i,t)}$ 之间的间隔不小于 2。定理 2.3 的证明至此完成。

### 注释 2.7。

我们摒弃了传统的周期性或连续采样格式，采用了更高效的非周期采样方法，以规避类似齐诺现象，如文献 [2, 3, 17, 35, 41–43] 所述。这一转变不仅验证了事件触发预测数据同化（ET-PDA）的可行性，还显著降低了每次迭代的通信与计算开销，从而提升了整体执行效率。

