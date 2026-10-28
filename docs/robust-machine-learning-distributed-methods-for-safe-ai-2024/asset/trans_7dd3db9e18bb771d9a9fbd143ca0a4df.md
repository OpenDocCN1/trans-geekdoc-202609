
将 (4.17) 中的 $A_t$ 代入上式，我们得到

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right] \le 2\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \nabla\mathcal{L}_i(\boldsymbol{\theta}_t)\right\|^2\right] + 2\mathbb{E}_t\left[\left\|\nabla\mathcal{L}_H - \mathbf{g}_t^H\right\|^2\right]$$

$$+ \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right].$$

回顾定理 3.1 的证明可知，在假设 3.2 下，有 $\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \nabla\mathcal{L}_i(\boldsymbol{\theta}_t)\right\|^2\right] \le \frac{\sigma^2}{b}$。因此，由于诚实节点独立计算各自的局部梯度，且 $|H| = n - f$，我们有 $\mathbb{E}_t\left[\left\|\nabla\mathcal{L}_H - \mathbf{g}_t^H\right\|^2\right] \le \frac{\sigma^2}{(n-f)b} \le \frac{\sigma^2}{b}$。将上述观察代入上式中，我们得到

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right] \le \frac{4\sigma^2}{b} + \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right].$$

上式对每个节点 $i \in H$ 均成立。因此，

$$\frac{\sum_{i \in H} \mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right]}{n - f} \le \frac{4\sigma^2}{b} + \frac{\sum_{i \in H} \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right]}{n - f}.$$

根据假设 4.1，有 $\frac{1}{n-f} \sum_{i \in H} \mathbb{E}_t\left[\left\|\nabla\mathcal{L}_i(\boldsymbol{\theta}_t) - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right] \le \zeta$。因此，由上式我们得到

$$\frac{1}{n-f} \sum_{i \in H} \mathbb{E}_t\left[\left\|\mathbf{g}_t^{(i)} - \mathbf{g}_t^H\right\|^2\right] \le \frac{4\sigma^2}{b} + \zeta.$$

在 (4.16) 两边取条件期望 $\mathbb{E}_t[\cdot]$，然后代入上式，即可完成证明。$\square$

上述关于 $\delta_t$ 的上界在后续关于鲁棒 DSGD 收敛性的分析中起着关键作用。我们首先考虑损失函数为非凸函数的情形，正如在第 3 章中所做的那样。对于该情形推导出的一些结果，将在处理强凸损失函数时证明是有用的。

## 4.4.2 非凸损失函数的情形

在本节中，我们考虑鲁棒性参数为 $f$ 的鲁棒 DMGD 算法，即假设 $n$ 个节点中有 $n - f$ 个节点是诚实的。我们首先在下面的定理 4.1 中分析算法收敛到诚实节点平均损失函数的驻点。然后，我们将推导该方法完成 $T$ 次迭代后获得的 $(f, \epsilon)$-驻点韧性性质，该性质对应于第 4.1.3 节中描述的特定聚合规则。回顾：对于非空集合 $S \subseteq [n]$，$\mathcal{L}_S$ 表示 $S$ 的平均损失函数，即

$$\mathcal{L}_S(\theta) := \frac{1}{|S|} \sum_{i \in S} \mathcal{L}_i(\theta).$$

我们令 $\mathcal{L}_S^* := \min_{\theta \in \mathbb{R}^d} \mathcal{L}_S(\theta)$。还要回顾，$\mathbb{E}[\cdot]$ 表示算法 5 在 $T$ 次迭代后对随机性的全期望，即 $\mathbb{E}[\cdot] = \mathbb{E}_1[\ldots\mathbb{E}_T[\cdot]]$。

定理 4.1 假设 3.1、3.2 和 4.1 成立。考虑鲁棒 DMGD 算法的 $T$ 次迭代，其中批量大小 $b \in [1, m)$，学习率为常数，即对所有 $t \in [T]$，有 $\gamma_t = \gamma \le \frac{1}{4L}$。如果聚合 $F$ 是一个 $(f, \kappa)$-鲁棒平均，那么对于任意由 $n - f$ 个诚实节点组成的集合 $H \subseteq [n]$，以下结论成立：

$$\frac{1}{T}\sum_{t=1}^T \mathbb{E}\left[\left\|\nabla \mathcal{L}_H(\theta_t)\right\|^2\right] \le \frac{4\left(\mathcal{L}_H(\theta_1)-\mathcal{L}_H^*\right)}{\gamma T} + \frac{4L\sigma^2}{(n-f)b}\gamma + 3\kappa\left(\frac{4\sigma^2}{b}+\zeta\right).$$

证明：考虑任意 $t \in [T]$，以及任意由 $n - f$ 个诚实节点组成的集合 $H \subseteq [n]$。与定理 3.1 证明中的 (3.8) 类似，逐点损失函数的 Lipschitz 光滑性（即假设 3.1）与鲁棒 DMGD 中 $\theta_{t+1}$ 的定义相结合，可得

$$\mathbb{E}_t\left[\mathcal{L}_H(\theta_{t+1})\right] \le \mathcal{L}_H(\theta_t) - \gamma_t\left\langle\nabla \mathcal{L}_H(\theta_t), \mathbb{E}_t\left[\hat{\mathbf{g}}_t\right]\right\rangle + \frac{L}{2}\gamma_t^2 \mathbb{E}_t\left[\left\|\hat{\mathbf{g}}_t\right\|^2\right]. \tag{4.20}$$

回顾 (4.14)，有

$$\hat{\mathbf{g}}_t = F\left(\mathbf{g}_t^{(1)}, \ldots, \mathbf{g}_t^{(n)}\right) = \mathbf{g}_t^H + \boldsymbol{\delta}_t. \tag{4.21}$$

由于对每个诚实的节点 $i \in H$，有 $\mathbb{E}_t\left[\mathbf{g}_t^{(i)}\right] = \nabla \mathcal{L}_i(\boldsymbol{\theta}_t)$，因此 $\mathbb{E}_t\left[\mathbf{g}_t^{H}\right] = \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)$。于是，

$$\mathbb{E}_t\left[\widehat{\mathbf{g}}_t\right] = \nabla \mathcal{L}_H(\boldsymbol{\theta}_t) + \mathbb{E}_t\left[\boldsymbol{\delta}_t\right]. \tag{4.22}$$

接下来，利用 (4.21) 中的三角不等式，以及对于实数 $a_1, a_2$，有 $(a_1 + a_2)^2 \le 2a_1^2 + 2a_2^2$，我们得到

$$\mathbb{E}_t\left[\left\|\widehat{\mathbf{g}}_t\right\|^2\right] \le 2\mathbb{E}_t\left[\left\|\mathbf{g}_t^H\right\|^2\right] + 2\mathbb{E}_t\left[\left\|\boldsymbol{\delta}_t\right\|^2\right]. \tag{4.23}$$

将 (4.22) 和 (4.23) 代入 (4.20)，我们得到

$$\begin{aligned}\mathbb{E}_t\left[\mathcal{L}_H(\boldsymbol{\theta}_{t+1})\right] &\le \mathcal{L}_H(\boldsymbol{\theta}_t) - \gamma_t\left\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2 + L\gamma_t^2\mathbb{E}_t\left[\left\|\mathbf{g}_t^H\right\|^2\right] \\ &- \gamma_t\langle\nabla \mathcal{L}_H(\boldsymbol{\theta}_t), \mathbb{E}_t\left[\boldsymbol{\delta}_t\right]\rangle + L\gamma_t^2\mathbb{E}_t\left[\left\|\boldsymbol{\delta}_t\right\|^2\right]. \end{aligned} \tag{4.24}$$

**上界** $\mathbb{E}_t\left[\left\|\mathbf{g}_t^H\right\|^2\right]$。注意

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^H\right\|^2\right] = \mathbb{E}_t\left[\left\|\mathbf{g}_t^H - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right] + \left\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2.$$

回顾上述引理 4.1 的证明，在假设 3.2 下，有 $\mathbb{E}_t\left[\left\|\mathbf{g}_t^H - \nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2\right] \le \frac{\sigma^2}{(n-f)b}$。因此，

$$\mathbb{E}_t\left[\left\|\mathbf{g}_t^H\right\|^2\right] \le \frac{\sigma^2}{(n-f)b} + \left\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2.$$

将上式代入 (4.24)，我们得到

$$\begin{aligned}\mathbb{E}_t\left[\mathcal{L}_H(\boldsymbol{\theta}_{t+1})\right] &\le \mathcal{L}_H(\boldsymbol{\theta}_t) - \gamma_t(1 - L\gamma_t)\left\|\nabla \mathcal{L}_H(\boldsymbol{\theta}_t)\right\|^2 + \gamma_t^2\frac{L\sigma^2}{(n-f)b} \\ &- \gamma_t\langle\nabla \mathcal{L}_H(\boldsymbol{\theta}_t), \mathbb{E}_t\left[\boldsymbol{\delta}_t\right]\rangle + L\gamma_t^2\mathbb{E}_t\left[\left\|\boldsymbol{\delta}_t\right\|^2\right]. \end{aligned} \tag{4.25}$$

**下界** $\langle\nabla \mathcal{L}_H(\boldsymbol{\theta}_t), \mathbb{E}_t\left[\boldsymbol{\delta}_t\right]\rangle$。根据柯西-施瓦茨不等式，以及对于实数 $a_1, a_2$，有 $2a_1a_2 \le a_1^2 + a_2^2$，我们得到

$$\langle \nabla \mathcal{L}_H(\theta_t),\mathbb{E}_t[\delta_t]\rangle \ge -\|\nabla \mathcal{L}_H(\theta_t)\|\,\|\mathbb{E}_t[\delta_t]\|$$
$$\ge -\frac{\|\nabla \mathcal{L}_H(\theta_t)\|^2+\|\mathbb{E}_t[\delta_t]\|^2}{2}.$$

将上式代入 (4.25)，我们得到

$$\mathbb{E}_t[\mathcal{L}_H(\theta_{t+1})]\le \mathcal{L}_H(\theta_t)-\gamma_t\left(\frac{1}{2}-L\gamma_t\right)\|\nabla \mathcal{L}_H(\theta_t)\|^2+\gamma_t^2\frac{L\sigma^2}{(n-f)b}$$
$$\qquad +\frac{\gamma_t}{2}\|\mathbb{E}_t[\delta_t]\|^2+L\gamma_t^2\mathbb{E}_t\left[\|\delta_t\|^2\right].$$

注意，根据三角不等式，有 $\|\mathbb{E}_t[\delta_t]\|\le \mathbb{E}_t[\|\delta_t\|]$。将其与詹森不等式结合，我们得到 $\|\mathbb{E}_t[\delta_t]\|^2\le \mathbb{E}_t[\|\delta_t\|^2]$。将之代入上式，我们得到

$$\mathbb{E}_t[\mathcal{L}_H(\theta_{t+1})]\le \mathcal{L}_H(\theta_t)-\gamma_t\left(\frac{1}{2}-L\gamma_t\right)\|\nabla \mathcal{L}_H(\theta_t)\|^2+\gamma_t^2\frac{L\sigma^2}{(n-f)b}$$
$$\qquad +\gamma_t\left(\frac{1}{2}+L\gamma_t\right)\mathbb{E}_t\left[\|\delta_t\|^2\right]. \tag{4.26}$$

从引理 4.1 中我们回顾，当聚合 $F$ 是一个 $(f,\kappa)$-鲁棒平均，且假设 3.2 和 4.1 成立时，有 $\mathbb{E}_t[\|\delta_t\|^2]\le 4\kappa\frac{\sigma^2}{b}+\kappa\zeta$。将之代入 (4.26)，我们得到

$$\mathbb{E}_t[\mathcal{L}_H(\theta_{t+1})]\le \mathcal{L}_H(\theta_t)-\gamma_t\left(\frac{1}{2}-L\gamma_t\right)\|\nabla \mathcal{L}_H(\theta_t)\|^2+\gamma_t^2\frac{L\sigma^2}{(n-f)b}$$
$$\qquad +\gamma_t\left(\frac{1}{2}+L\gamma_t\right)\left(4\kappa\frac{\sigma^2}{b}+\kappa\zeta\right). \tag{4.27}$$

**总结步骤。** 在 (4.27) 两边取全期望 $\mathbb{E}[\cdot]$，并整理各项，我们得到

$$\left(\frac{1}{2}-L\gamma_t\right)\mathbb{E}\left[\|\nabla \mathcal{L}_H(\theta_t)\|^2\right]\le \frac{\mathbb{E}[\mathcal{L}_H(\theta_t)]-\mathbb{E}[\mathcal{L}_H(\theta_{t+1})]}{\gamma_t}$$
$$\qquad +\gamma_t\frac{L\sigma^2}{(n-f)b}+\left(\frac{1}{2}+L\gamma_t\right)\left(4\kappa\frac{\sigma^2}{b}+\kappa\zeta\right).$$
