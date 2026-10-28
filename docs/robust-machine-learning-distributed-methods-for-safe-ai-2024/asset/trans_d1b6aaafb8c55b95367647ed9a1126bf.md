
$$+ z\kappa (1 - \beta_t)^2 \frac{\sigma^2}{b} + z(1 - \beta_t)\kappa \zeta$$
$$- \gamma_{t-1} \left( \frac{1}{2} - 2\gamma_{t-1}L \right) \mathbb{E} \left[ \|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 \right]$$
$$+ 8Lz\gamma_{t-1}\beta_t^2 \mathbb{E} \left[ \|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 \right].$$

回顾一下，由于假设 4.2，$\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2 \geq 2\mu \left( \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \mathcal{L}_H^* \right)$。利用此式并重新排列项，可得

$$\mathbb{E}[V_t] \leq \left( 1 - 2\mu\gamma_{t-1}\left( \frac{1}{2} - 2\gamma_{t-1}L - 8Lz\beta_t^2 \right) \right) \mathbb{E} \left[ \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \mathcal{L}_H^* \right]$$
$$+ \left( 2\gamma_{t-1} + z(1 + 6L\gamma_{t-1})\beta_t^2 \right) \mathbb{E} \left[ \|\boldsymbol{\xi}_{t-1}\|^2 \right]$$
$$+ z(1 - \beta_t)^2 \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b}$$
$$+ \kappa \left( 2\gamma_{t-1} + z4L\beta_t^2\gamma_{t-1} + z\beta_t \right) \mathbb{E} \left[ M_{t-1}^H \right] + z\kappa(1 - \beta_t)\zeta. \quad (6.53)$$

令

$$A_t := 2\gamma_{t-1} + z(1 + 6L\gamma_{t-1})\beta_t^2, \quad \text{and} \quad B_t := 2\gamma_{t-1} + z4L\beta_t^2\gamma_{t-1} + z\beta_t.$$

由上式代入 (6.53)，可重写为

$$\mathbb{E}[V_t] \leq \left( 1 - 2\mu\gamma_{t-1}\left( \frac{1}{2} - 2\gamma_{t-1}L - 8Lz\beta_t^2 \right) \right) \mathbb{E} \left[ \mathcal{L}_H(\boldsymbol{\theta}_{t-1}) - \mathcal{L}_H^* \right]$$
$$+ A_t \mathbb{E} \left[ \|\boldsymbol{\xi}_{t-1}\|^2 \right] + B_t\kappa \mathbb{E} \left[ M_{t-1}^H \right] + z(1 - \beta_t)^2 \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b}$$
$$+ z(1 - \beta_t)\kappa\zeta.$$

注意，由于 $z = \frac{1}{64L}$，$\beta_t \leq 1$，且 $\gamma_{t-1} \leq \frac{1}{144L}$，我们有

$$\frac{1}{2} - 2\gamma_{t-1}L - 8Lz\beta_t^2 \geq \frac{1}{2} - 2\gamma_{t-1}L - \frac{1}{8} \geq \frac{1}{8}.$$

因此，由上式可得

$$\mathbb{E}[V_t] \le \left(1 - \frac{\mu}{4}\gamma_{t-1}\right)\mathbb{E}[\mathcal{L}_H(\theta_{t-1}) - \mathcal{L}_H^*] + A_t\mathbb{E}[\|\xi_{t-1}\|^2] + B_t\kappa\mathbb{E}[M_{t-1}^H] + z(1 - \beta_t)^2\left(\kappa + \frac{1}{n - f}\right)\frac{\sigma^2}{b} + z\kappa(1 - \beta_t)\zeta. \quad (6.54)$$

### $A_t$ 的上界

回顾 $A_t := 2\gamma_{t-1} + z(1 + 6L\gamma_{t-1})\beta_t^2$。代入 $z = \frac{1}{64L}$，可得 $A_t = z\left(128L\gamma_{t-1} + (1 + 6L\gamma_{t-1})\beta_t^2\right) = z\left(128L\gamma_{t-1} + \beta_t^2 + 6L\gamma_{t-1}\beta_t^2\right)$。由于 $\beta_t \le 1$，我们有 $\beta_t^2 \le \beta_t$ 且 $6L\gamma_{t-1}\beta_t^2 \le 6L\gamma_{t-1}$。利用这些，可得 $A_t \le z\left(134L\gamma_{t-1} + \beta_t\right)$。将 $\beta_t = 1 - 144L\gamma_{t-1}$ 代入并利用当 Lipschitz 光滑性（即假设 3.1）和强凸性（即假设 4.2）同时成立时，有 $L \ge \mu$（参见附录 A.2），可得

$$A_t \le z\left(1 - 10L\gamma_{t-1}\right) \le z\left(1 - 10\mu\gamma_{t-1}\right) \le z\left(1 - \frac{\mu}{4}\gamma_{t-1}\right). \quad (6.55)$$

### $B_t$ 的上界

回顾 $B_t := 2\gamma_{t-1} + z4L\beta_t^2\gamma_{t-1} + z\beta_t$。与上文 $A_t$ 类似，可得

$$B_t \le z\left(132L\gamma_{t-1} + \beta_t\right) = z\left(1 - 12L\gamma_{t-1}\right) \le z\left(1 - \frac{\mu}{4}\gamma_{t-1}\right). \quad (6.56)$$

将 (6.55) 和 (6.56) 代入 (6.54)，可得

$$\mathbb{E}\left[V_t\right] \le \left(1-\frac{\mu}{4}\gamma_{t-1}\right)\left(\mathbb{E}\left[\mathcal{L}_H\left(\boldsymbol{\theta}_{t-1}\right)-\mathcal{L}_H^*\right] + z\mathbb{E}\left[\left\|\boldsymbol{\xi}_{t-1}\right\|^2\right] + \kappa z\mathbb{E}\left[M_{t-1}^H\right]\right) + z\left(1-\beta_t\right)^2\left(\kappa+\frac{1}{n-f}\right)\frac{\sigma^2}{b} + z\left(1-\beta_t\right)\kappa\zeta.$$

回顾 $V_t$ 在 (6.49) 中的定义，$\mathbb{E}\left[\mathcal{L}_H\left(\boldsymbol{\theta}_{t-1}\right)-\mathcal{L}_H^*\right] + z\mathbb{E}\left[\left\|\boldsymbol{\xi}_{t-1}\right\|^2\right] + \kappa z\mathbb{E}\left[M_{t-1}^H\right] = \mathbb{E}\left[V_{t-1}\right]$。因此，上式可写为

$$\mathbb{E}\left[V_t\right] \le \left(1-\frac{\mu}{4}\gamma_{t-1}\right)\mathbb{E}\left[V_{t-1}\right] + z\left(1-\beta_t\right)^2\left(\kappa+\frac{1}{n-f}\right)\frac{\sigma^2}{b} + z\left(1-\beta_t\right)\kappa\zeta.$$

将 $\beta_t = 1-144L\gamma_{t-1}$ 和 $z = \frac{1}{64L}$ 代入上式即完成证明。$\square$

## 收敛结果

注意，定理 6.2 中给出的序列 $(\mathbb{E}\left[V_t\right])_{t \in [T+1]}$ 的增长情况与引理 3.1 中 $(U_t)_{t \in [T+1]}$ 的增长情况相对应，其中 $U_t := \mathbb{E}\left[V_t\right]$，且 $\alpha_1, \alpha_2, \alpha_3$ 设为如下：

$$\alpha_1 := \frac{\mu}{4}, \alpha_2 := 324L\left(\kappa+\frac{1}{n-f}\right)\frac{\sigma^2}{b} \text{ and } \alpha_3 := \frac{9}{4}\kappa\zeta. \qquad (6.57)$$

由于上文定理 6.2 可知对每个迭代 $t$ 都有 $\mathcal{L}_H\left(\boldsymbol{\theta}_t\right)-\mathcal{L}_H^* \le V_t$，因此可在强凸情形下得到算法 6 的次线性收敛性，与算法 5 类似。本质上，将定理 6.2 的结果与引理 3.1 的结果结合，可得到以下推论。为简化起见，我们将以 (6.57) 中定义的 $\alpha_2$ 和 $\alpha_3$ 参数来表述该推论。

**Corollary 6.2** *假设 3.1、3.2、4.1 和 4.2 成立。设 $T$ 为大于 2 的偶整数。考虑算法 6 的 $T$ 次迭代，其中批量大小 $b \in [1, m]$，$(f, \kappa)$-鲁棒聚合规则 $F$，学习率序列 $(\gamma_t)_{t \in [T]}$ 定义为*

$$\gamma_t = \begin{cases} \gamma_o & , \ t < T/2 \\ \frac{8}{\mu(s_o+t-\frac{T}{2})} & , \ t \ge T/2 \end{cases}, \qquad (6.58)$$

*其中 $\gamma_o$ 和 $s_o$ 为正实值且满足 $\gamma_o = \frac{8}{\mu s_o} \le \frac{1}{144L}$，以及动量系数序列 $(\beta_t)_{t\in[T]}$ 由 (6.47) 定义，其中 $c = 144L$。则以下成立：*

$$\mathbb{E} \left[ \mathcal{L}_H (\theta_{T+1}) - \mathcal{L}_H^{\star} \right] \le \frac{\Delta_o e^{-\frac{\mu}{8}\gamma_o (T-2)}}{T^2} + \frac{16(\alpha_2 \gamma_o + \alpha_3)(s_o - 1)^2}{\mu T^2}$$
$$+ \frac{128\alpha_2}{\mu^2 T} + \frac{8\alpha_3}{\mu},$$

*其中 $\Delta_o$ 为正实值且满足*

$$4(s_o - 1)^2 \left( \mathcal{L}_H(\theta_1) - \mathcal{L}_H^{\star} + \frac{1}{64L} \left( \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b} + \kappa \zeta \right) \right) \le \Delta_o,$$

*且常数 $\alpha_2, \alpha_3$ 定义于 (6.57)。*

*证明* 与推论 3.2 和定理 4.2 类似，我们使用第 3 章中给出的引理 3.1。首先，考虑 (6.58) 中定义的 learning rate 序列 $(\gamma_t)_{t\in[T]}$。当假设 3.1 和 4.2 同时成立时，有 $\mu \le L$，于是 $\frac{1}{144L} \le \frac{1}{\mu} \le \frac{4}{\mu}$。这意味着令 $\alpha_1 := \frac{\mu}{4}$，我们有

$$\gamma_o = \frac{8}{\mu s_o} = \frac{2}{\alpha_1 s_o} \le \frac{1}{144L} \le \frac{4}{\mu} = \frac{1}{\alpha_1}.$$

由上可知，序列 $(\gamma_t)_{t\in[T]}$ 满足引理 3.1 中所述的条件。

其次，由定理 6.2 回顾，对 $t \in [T]$，有

$$\mathbb{E} \left[ V_t \right] \le \left( 1 - \frac{\mu}{4} \gamma_{t-1} \right) \mathbb{E} \left[ V_{t-1} \right]$$
$$+ 324L \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b} \gamma_{t-1}^2 + \frac{9}{4} \kappa \zeta \gamma_{t-1}.$$

与定理 6.1 类似，注意上式即使对 $t = T + 1$ 仍成立，只要将算法 6 中局部随机梯度和对应动量向量的定义也应用于 $t = T + 1$。令 $U_t := \mathbb{E} \left[ V_t \right]$。上式意味着，对所有 $t \in [T]$，

$$U_{t+1} \le \left( 1 - \frac{\mu}{4} \gamma_t \right) U_t + 324L \left( \kappa + \frac{1}{n-f} \right) \frac{\sigma^2}{b} \gamma_t^2 + \frac{9}{4} \kappa \zeta \gamma_t.$$

