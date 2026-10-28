
由于对所有 $t$ 都有 $\gamma_t = \gamma \leq \frac{1}{4L}$，我们有 $\frac{1}{2} - L\gamma_t \geq \frac{1}{4}$。此外，$\left(\frac{1}{2} + L\gamma_t\right) \leq \left(\frac{1}{2} + \frac{L}{4L}\right) = \frac{3}{4}$。因此，我们得到

$$\frac{1}{4}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] \leq \frac{\mathbb{E}[\mathcal{L}_H(\boldsymbol{\theta}_t)] - \mathbb{E}[\mathcal{L}_H(\boldsymbol{\theta}_{t+1})]}{\gamma_t} + \gamma_t \frac{L\sigma^2}{(n-f)b} + \frac{3}{4}\left(4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right).$$

将 $\gamma_t = \gamma$ 代入上式，然后在 $t = 1$ 到 $t = T$ 上对两边取平均，可得

$$\frac{1}{T}\sum_{t=1}^T \mathbb{E}\left[\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\|^2\right] \leq \frac{4\left(\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H(\boldsymbol{\theta}_{T+1})\right]\right)}{\gamma T} + \frac{4L\sigma^2}{(n-f)b}\gamma + 3\left(4\kappa\frac{\sigma^2}{b} + \kappa\zeta\right).$$

由于 $\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H(\boldsymbol{\theta}_{T+1}) \leq \mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^*$ $^b$，且初始模型 $\boldsymbol{\theta}_1$ 是给定的，我们有 $\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H(\boldsymbol{\theta}_{T+1})\right] \leq \mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^*\right] = \mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^*$。至此证明完毕。

$\square$

$^a$ 我们可以利用平方函数 $(\cdot)^2$ 上的 Jensen 不等式进行同样的推理。
$^b$ 相关推理参见定理 3.1 的证明。

## 驻点弹性性质

在定理 4.1 中选取合适的学习率 $\gamma$ 后，我们得到如下推论，该推论进而使我们能够刻画 Robust DMGD 的驻点弹性性质。

**推论 4.1** *设假设 3.1、3.2 和 4.1 成立。考虑 Robust DMGD 算法运行 $T$ 次迭代，批次大小为 $b \in [1, m)$，且使用一个 $(f, \kappa)$-鲁棒平均规则 $F$。设 $H$ 为任意包含 $n - f$ 个诚实节点的集合，$\Delta_H$ 为满足 $\mathcal{L}_H(\boldsymbol{\theta}_1) - \mathcal{L}_H^* \leq \Delta_H$ 的实数值。如果*

$$\gamma_t = \gamma = \min\left\{\frac{1}{4L}, \sqrt{\frac{(n-f)b\Delta_H}{\sigma^2LT}}\right\}, \forall t \in [T],$$

那么，在 $T \ge \frac{16(n-f)bL\Delta_H}{\sigma^2}$ 的条件下，以下结论成立：

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right] \le 8\sqrt{\frac{L\sigma^2\Delta_H}{(n-f)bT}}+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

**证明** 注意到定理 4.1 中的所有条件均成立。因此，由定理 4.1 可得

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right] \le \frac{4(\mathcal{L}_H(\theta_1)-\mathcal{L}_H^*)}{\gamma T}+\frac{4L\sigma^2}{(n-f)b}\gamma+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

由于上式中的 $\mathcal{L}_H(\theta_1)-\mathcal{L}_H^*\le \Delta_H$，我们有

$$\frac{1}{T}\sum_{t=1}^{T}\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right] \le \frac{4\Delta_H}{\gamma T}+\frac{4L\sigma^2}{(n-f)b}\gamma+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

(4.29)

由于假设 $T \ge \frac{16(n-f)bL\Delta_H}{\sigma^2}$，根据 (4.28) 中 $\gamma$ 的定义，我们有

$$\gamma=\sqrt{\frac{(n-f)b\Delta_H}{\sigma^2LT}}.$$

将上式代入 (4.29) 即可完成证明。 $\square$

该推论表明，如果服务器从 Robust DMGD 执行过程中生成的所有模型中随机采样一个模型，那么即使在存在多达 $f$ 个对抗节点的情况下，（在期望意义下）该模型也能以有界的误差逼近 $\mathcal{L}_H$ 的一个驻点。具体而言，在推论 4.1 所述条件下，执行 Robust DMGD 算法的 $T$ 次迭代后，如果服务器输出从中间模型集合 $\{\theta_1,\ldots,\theta_T\}$ 中均匀选取的 $\tilde{\theta}$，则我们实现了（如定义 4.2 所定义的）$(f,\epsilon)$-驻点弹性，其中

$$\varepsilon \lesssim 8\sqrt{\frac{L\sigma^2\Delta_H}{(n-f)bT}}+3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right)\in O_T\left(\sqrt{\frac{\sigma^2}{(n-f)bT}+\kappa\frac{\sigma^2}{b}+\kappa\zeta}\right). \tag{4.30}$$

(4.30) 中训练误差的量级由三个主要项组成。第一项 $O_T\left(\sqrt{\frac{\sigma^2}{(n-f)bT}}\right)$ 是消失误差率，对应于在至少 $n-f$ 个诚实节点上运行原始 DMGD 算法的误差率（参见推论 3.1）。随着算法总迭代次数 $T$ 的增加，这一项趋于零；因此，它不是算法最终训练误差中的主导因素。第二项和第三项 $O_T\left(\kappa\frac{\sigma^2}{b}\right)$ 和 $O_T(\kappa\zeta)$ 是由对抗节点的存在所引入的（在最坏情况下）不消失误差。注意，与原始 DMGD 算法相反，在存在对抗节点的情况下，局部梯度噪声（以 $\sigma$ 衡量）会导致不可压缩的误差，这显然意味着学习过程可能产生较差的模型精度（或带来较高的训练误差）。正如第 6 章后面所示，这种由局部梯度估计噪声引起的误差增大可以通过在节点层面的模型更新中嵌入*梯度动量*来减小。然而，由梯度差异性（以 $\zeta$ 衡量）引起的误差通常是无法消除的。关于梯度差异性对鲁棒性限制的正式讨论，我们将推迟到第 5 章 5.3 节进行。

我们在表 4.2 中总结了当聚合规则 $F$ 为第 4.1.3 节所述规则之一时 Robust DMGD 算法的驻点弹性性质。回顾一下，当设置参数 $q=f$（其中 $f<\frac{n}{2}$）时，这些聚合规则中的每一个都在第 4.3.2 节中被证明是一个 $(f,\kappa)$-鲁棒平均。因此，配备这些聚合规则中任意一种的 Robust DMGD 方法的崩溃点最高可调至 $\frac{1}{2}$。表 4.2 中所示训练误差 $\varepsilon$ 的量级，是通过回忆以下事实得到的：对于 CWMed、GeoMed 和 Multi-Krum$_{f,1}$，$\kappa \in \mathcal{O}_n(1)$；对于 CWTM$_f$，$\kappa \in \mathcal{O}_n\left(\frac{f}{n}\right)$。对于 CWTM$_f$，我们令 $\frac{f}{n} < \frac{1}{2}\left(\frac{c}{1+c}\right)$，其中 $c$ 是一个正实值常数（见第 4.3.2 节）。我们注意到，虽然对于 CWTM$_f$，非消失误差项随 $\frac{f}{n}$ 线性增长，但对于其他三种聚合规则则不一定如此。这一现象可以解释为：CWMed、GeoMed 和 Multi-Krum$_{q_1,q_2}$ 是基于*中位数*的聚合规则，因此不会受益于系统中诚实节点的预期优势。中位数基规则的另一个性质是，它们的崩溃点始终是 $\frac{1}{2}$，与鲁棒性参数 $f$（即系统设计可容忍的最大对抗节点数）无关。而 CWTM 涉及一种平均操作，当系统预期拥有更多诚实节点时，这有助于提高精度。具体而言，当使用 CWTM 作为聚合规则时，我们可以用 Robust DMGD 算法的崩溃点来换取更好的训练误差。稍后将在下面对此进行更多讨论。类似的性质也可以通过使用预聚合方案赋予基于中位数的聚合规则，该方案将在第 5 章中介绍和分析。

**表 4.2** 在推论 4.1 所述条件下，针对一般非凸情形，Robust DMGD 使用所列聚合规则完成 $T$ 次迭代后所获得的 $(f,\varepsilon)$-驻点弹性性质。对于除 CWTM$_f$ 外的所有聚合规则，我们假设 $\frac{f}{n}<\frac{1}{2}$。对于 CWTM$_f$，根据第 4.3.2 节的讨论，我们假设 $\frac{f}{n}\leq\frac{c}{2(1+c)}$，其中 $c$ 是一个正实值常数。

| 聚合规则 | 崩溃点 | 训练误差 $\varepsilon$ |
|---|---:|---|
| CWMed | $\frac{1}{2}$ | $O_{n,T}\left(\sqrt{\frac{\sigma^2}{(n-f)bT}+\frac{\sigma^2}{b}+\zeta}\right)$ |
| GeoMed | $\frac{1}{2}$ | $O_{n,T}\left(\sqrt{\frac{\sigma^2}{(n-f)bT}+\frac{\sigma^2}{b}+\zeta}\right)$ |
| CWTM$_f$ | $\frac{f+1}{n}$ | $O_{n,T}\left(\sqrt{\frac{\sigma^2}{(n-f)bT}+\frac{f}{n}\frac{\sigma^2}{b}+\frac{f}{n}\zeta}\right)$ |
| Multi-Krum$_{f,1}$ | $\frac{f+1}{n}$ | $O_{n,T}\left(\sqrt{\frac{\sigma^2}{(n-f)bT}+\frac{\sigma^2}{b}+\zeta}\right)$ |

## 将分析应用于鲁棒 DSGD 和鲁棒 DGD

上述鲁棒性分析可直接应用于鲁棒 DSGD（即批次大小 $b=1$ 的算法 5），只需在定理 4.1 和推论 4.1 中代入 $b=1$ 即可。对于鲁棒 DGD，即在全局阶段采用鲁棒聚合的 DGD，我们不存在梯度噪声。在定理 4.1 中代入 $\sigma = 0$，并令 $\gamma$ 为任意小于 $\frac{1}{4L}$ 的常数，我们可以推断鲁棒 DGD 是 $(f, \varepsilon)$-驻点弹性的，其中当使用 CWMed、GeoMed 或 Krum 作为聚合规则时 $\varepsilon \in \mathcal{O}_T\left(\frac{1}{T} + \kappa\zeta\right)$，且 $\kappa \in \mathcal{O}_n(1)$；当使用 CWTM$_f$ 作为聚合规则时 $\kappa \in \mathcal{O}_n\left(\frac{f}{n}\right)$。可以预期，与 Robust DMGD 相反，在实现鲁棒 DGD 时，梯度计算噪声不会对不可压缩的训练误差作出贡献。然而，在整个训练样本上计算真实梯度的代价在实践中是相当高的。为减小噪声对训练误差的影响，鲁棒 DGD 的一个高效替代方案是在 Robust DMGD 中引入梯度动量。该方案将在第 6 章中介绍。

## 崩溃点、训练误差与梯度复杂度之间的相互影响

考虑采用聚合规则 CWTM$_f$ 的 Robust DMGD 方法，其中鲁棒性参数 $f < \frac{n}{2}$。如表 4.2 所示，在执行 $T$ 次迭代后，我们获得的训练误差为

$$\varepsilon \in \mathcal{O}_{n,T}\left(\sqrt{\frac{\sigma^2}{(n-f)bT}} + \frac{f}{n}\frac{\sigma^2}{b} + \frac{f}{n}\zeta\right).$$
