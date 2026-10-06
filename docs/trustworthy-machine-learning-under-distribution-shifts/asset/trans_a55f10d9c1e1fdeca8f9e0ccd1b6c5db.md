
# 7 证明与理论分析

假设 10 (Lipschitz 平滑)。 $\mathcal{L}(\theta; (x, y))$ 对于每个样本 $(x, y)$ 都是可微的且满足 $l$-Lipschitz 平滑的：

$|\nabla_{\theta}\mathcal{L}(\theta_1; (x, y)) - \nabla_{\theta}\mathcal{L}(\theta_2; (x, y))|| \leq l|\theta_1 - \theta_2||, \quad \forall \omega, (x, y);$

$|\nabla_{\omega}\mathcal{L}(\theta; \omega_1) - \nabla_{\omega}\mathcal{L}(\theta; \omega_2)| \leq l|\omega_1 - \omega_2||, \quad \forall \theta.$

备注 16。因此期望函数 $\mathcal{L}$ 也具有 Lipschitz 平滑性质：

$|\nabla_{\theta}\mathcal{L}(\theta_1; \omega) - \nabla_{\theta}\mathcal{L}(\theta_2; \omega)| \leq E||\nabla_{\theta}\mathcal{L}(\theta_1; (x, y)) - \nabla_{\theta}\mathcal{L}(\theta_2; (x, y))|| \leq l|\theta_1 - \theta_2||, \quad \omega$;

$|\nabla_{\omega}\mathcal{L}(\theta; \omega_1) - \nabla_{\omega}\mathcal{L}(\theta; \omega_2)| \leq E||\nabla_{\omega}\mathcal{L}(\theta; (x, y)) - \nabla_{\omega}\mathcal{L}(\theta; (x, y))|| \leq l|\omega_1 - \omega_2||, \quad \theta.$

假设 12 (PL 条件)。损失函数 $\mathcal{L}(\theta, \cdot)$ 在每个 $\theta$ 上均满足 PL 条件，存在 $\mu > 0$ 使得 $|\nabla_{\theta}\mathcal{L}(\theta, \omega)||^2 \geq 2\mu[|\nabla_{\theta}\mathcal{L}(\theta, \omega) - \mathcal{L}(\theta, \omega)|], \quad \forall \theta, \omega.$

## 7.1.3 有用引理

在这一部分，我们将证明一些用于证明收敛界的必要引理。

我们会在开头给出该问题的驻点的定义。

定义 13 (驻点测度)。对于任何 $\epsilon \geq 0$，如果 $\mathbb{E}|\nabla L^{*}(\theta)||| \leq \epsilon$，则定义 $\theta$ 为我们问题的 $\epsilon$-驻点。

备注 14。对于极小问题，通常有两种衡量驻点的方法。一种是双侧测量，当 $\mathbb{E}||\nabla_{\theta}\mathcal{L}(\theta, \omega)||| \leq \epsilon$ 且 $\mathbb{E}||\nabla_{\omega}\mathcal{L}(\theta, \omega)||| \leq \epsilon$ 时，我们称 $(\theta, \omega)$ 为 $(\epsilon, \epsilon)$-驻点。在 [352] 中已经证明当 $L^*$ 平滑时，这些测度可以相互转换，这在我们使用 SharpDRO 算法计算模型参数 $\theta$ 时所示。因此，我们在这里选择 $\mathbb{E}|L^{*}(\theta)|$ 作为测度。

引理 2。[353] 在假设 10 和 12 下，$L^{*}(\theta)$ 是 $(1+\frac{l}{2\mu})$-Lipschitz 平滑的，其梯度为：

$\nabla_{\theta}L^{*}(\theta) = \nabla_{\theta}\mathcal{L}(\theta, \omega^{*})$.

引理 3。[353] 在假设 10 和 12 下，$\omega^{*}(\cdot)$ 关于其变量是平滑的：

$|\omega^*(\theta_1) - \omega^*(\theta_2)| \leq \frac{l}{2\mu}|\theta_1 - \theta_2||, \quad \theta_1, \theta_2.$

## 1 SHARPDRO 的证明

引理 4. 我们给出一个估计：

```
$\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t)\|^2 \leq (4\rho^2l^2 + 2\rho l + 2)\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + (5\rho^2l^2 + 2)\frac{\sigma^2}{M}.$
```

证明。

```
$\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t)\|^2 = -\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + \mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2$
+ 2\mathbb{E}g_{\theta}(\theta_{t+1/2}, \omega_t), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t).$.
```

对于交叉积项，我们进行如下拆分：

```
$\mathbb{E}(g_{\theta}(\theta_{t+1/2}, \omega_t), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))$
$= \mathbb{E}(g_{\theta}(\theta_{t+1/2}, \omega_t) - g_{\theta}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))$
$+ \mathbb{E}(g_{\theta}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))$
$= \mathbb{E}(\nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))$
$\leq{(i)} \frac{1}{2}\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t)\|^2$
$- \nabla_{\theta}\mathcal{L}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))\|^2 + \frac{1}{2}\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + \mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2$
$+ \mathbb{E}(\nabla_{\theta}\mathcal{L}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))$
$\leq{(ii)} \frac{\rho^2l^2}{2}\mathbb{E}\|g_{\theta}(\theta_t, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + \frac{3}{2}\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + \rho l\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2$
$\leq{(iii)} (\rho + \frac{3}{2})\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + \frac{\rho^2l^2\sigma^2}{M}$.
```

其中不等式 (i) 源于 Cauchy-Schwarz 不等式；不等式 (ii) 源于 $L$ 的 Lipschitz 平滑性：

```
$\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t))\|^2 \leq l^2\|\theta_{t+1/2} - \theta_t\|^2$.
```

## 7 证明与理论分析

以及 Lipschitz 平滑性质：

$\langle\nabla_{\theta}\mathcal{L}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\rangle = (7.7)$
$\frac{1}{\rho}\langle\nabla_{\theta}\mathcal{L}(\theta_t + \rho\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\rangle \leq \frac{l}{\rho}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2, (7.8)$

且不等式 $(iii)$ 利用假设 8 处理第二项，我们有：

$\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 \leq 2\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + 2\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2$$\leq \frac{\sigma^2}{M} + 2\rho^2l\mathbb{E}\|g_{\theta}(\theta_t, \omega_t)\|^2 (7.9)$
$= \frac{\sigma^2}{M} + 2\rho^2l^2\mathbb{E}\|g_{\theta}(\theta_t, \omega_t)\|^2 \leq \frac{\sigma^2}{M}(2\rho^2l^2 + 1) + 4\rho^2l^2\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2,(7.10)$

通过结合上述不等式，我们可以得到：

$\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t)\|^2 \leq (4\rho^2l^2 + 2\rho)\mathbb{E}\|\nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + (5\rho^2l^2 + 2)\frac{\sigma^2}{M}. (7.11)$

## 引理 5. 对于函数 $L^*$ 的下降关系

$\mathbb{E}[L^*(\theta_{t+1})] \leq L^*(\theta_t) - \frac{\eta_0}{2}(1-5\rho l - \eta_0(4\rho^2l^2 + 2\rho))\mathbb{E}[L^*(\theta_t)] + \frac{\eta_0^2}{2}(1+\frac{\rho l}{2}) + l\eta_0^2(4\rho^2l^2 + 2\rho l)\mathbb{E}\|\nabla_{\theta}^{*}(\theta_t) - \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\|^2 + \frac{\eta_0^2\sigma^2}{2},$

这里我们使用了简记符号 $L = l + \frac{l}{2}$。证明。由于 $\mathbb{L}^*(\theta)$ 根据引理 2 是 $(l+\frac{l}{2})$-Lipschitz 平滑的，我们有：

$\mathbb{L}^*(\theta_{t+1}) \leq \mathbb{L}^*(\theta_t) + \langle\nabla\mathbb{L}^*(\theta_t), \theta_{t+1} - \theta_t\rangle + \frac{1}{2}(l+\frac{l}{2})\|\Delta\theta\|^2$
$= \mathbb{L}^*(\theta_t) - \eta_t\langle\nabla\mathbb{L}^*(\theta_t), g_{\theta}(\theta_{t+1/2}, \omega_t)\rangle + \frac{1}{2}(l+\frac{l}{2})\eta_t^2\|g_{\theta}(\theta_{t+1/2}, \omega_t)\|^2. (7.12)$

在 $(\theta_t, \omega_t)$ 上取期望，我们得到：

$\mathbb{E}[\mathbb{L}^*(\theta_{t+1})|\theta_t, \omega_t] \leq (7.13)$
$\mathbb{L}^*(\theta_t) - \eta_t\langle\nabla\mathbb{L}^*(\theta_t), \nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t)\rangle + \frac{1}{2}(l+\frac{l}{2})\eta_t^2\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t)\|^2. (7.14)$

我们再次对上述不等式两边取期望，得到：

$\mathbb{E}[\mathbb{L}^*(\theta_{t+1})] \leq \mathbb{E}[\mathbb{L}^*(\theta_t)] - \eta_t\mathbb{E}\langle\nabla\mathbb{L}^*(\theta_t), \nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t)\rangle + \frac{1}{2}(l+\frac{l}{2})\eta_t^2\mathbb{E}\|g_{\theta}(\theta_{t+1/2}, \omega_t)\|^2. (7.15)$

对于第二项，我们将其解构为：

$\mathbb{E}\langle\nabla\mathbb{L}^*(\theta_t), \nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t)\rangle =$
$\geq \mathbb{E}\langle\nabla\mathbb{L}^*(\theta_t), \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\rangle - \mathbb{E}\langle\nabla\mathbb{L}^*(\theta_t), \nabla_{\theta}\mathcal{L}(\theta_{t+1/2}, \omega_t) - \nabla_{\theta}\mathcal{L}(\theta_t, \omega_t)\rangle$
