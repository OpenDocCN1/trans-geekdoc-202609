
## 命题 18.33

在算法 18.3 中，我们令

$$\tilde d = \sum_{h=1}^{H} \mathrm{EC}_{V}^{h}(\epsilon,\mathcal{F},T)\max\left(1,\mathrm{CC}^{h}(\epsilon',\tilde\pi,\mathcal{F})\right),$$

则

$$\mathbb{E}\sum_{h=1}^{H}\sum_{t=2}^{T}\mathcal{E}^{h}(f_{t},x_{t}^{h},a_{t}^{h})\le\sqrt{\tilde d\mathbb{E}\sum_{t=2}^{T}\left(\epsilon H+\epsilon'HT+\sum_{s=1}^{t-1}\sum_{h=1}^{H}\bar{\mathcal{E}}^{h}(f_{t},\pi_{f_{s}},\tilde\pi)^{2}\right)},$$

其中

$$\bar{\mathcal{E}}^{h}(f,\pi,\tilde\pi)^{2}=\mathbb{E}_{\hat x^{h}\sim\pi}\mathbb{E}_{a^{h}\sim\tilde\pi(\cdot|\hat x^{h})}\mathcal{E}^{h}(f_{t},x^{h},a^{h})^{2}.$$

证明 令 $d_{1}^{h}=\mathrm{EC}_{V}^{h}(\epsilon,\mathcal{F},T)$，且 $d_{2}^{h}=\mathrm{CC}^{h}(\epsilon',\tilde\pi,\mathcal{F})$。我们得到

$$\mathbb{E}\sum_{h=1}^{H}\sum_{t=2}^{T}\mathcal{E}^{h}(f_{t},x_{t}^{h},a_{t}^{h})\le\sum_{h=1}^{H}\sqrt{d_{1}^{h}\mathbb{E}\sum_{t=2}^{T}\left(\epsilon+\sum_{s=1}^{t-1}\mathbb{E}_{\hat x\sim\pi_{f_{s}}}\mathcal{E}^{h}(f_{t},\hat x^{h},\pi_{f_{t}}(\hat x^{h}))^{2}\right)}$$

$$\le\sum_{h=1}^{H}\sqrt{d_{1}^{h}\mathbb{E}\sum_{t=2}^{T}\left(\epsilon+d_{2}^{h}\sum_{s=1}^{t-1}(\epsilon'+\mathcal{E}^{h}(f_{t},\pi_{f_{s}},\tilde\pi)^{2})\right)}$$

$$\le\sum_{h=1}^{H}\sqrt{d_{1}^{h}\max(1,d_{2}^{h})\mathbb{E}\sum_{t=2}^{T}\left(\epsilon+\epsilon' T+\sum_{s=1}^{t-1}\bar{\mathcal{E}}^{h}(f_{t},\pi_{f_{s}},\tilde\pi)^{2}\right)}.$$

第一个不等式使用了定义 18.27。第二个不等式使用了定义 18.30。然后我们使用 Cauchy–Schwarz 不等式得到结果。

利用命题 18.33，我们可以将遗憾减少到历史数据上的样本内预测误差。这使我们能够证明算法 18.3 的以下结果，其与定理 18.21 相似。

## 定理 18.34

假设假设 18.12 成立，$\mathcal{F}$ 关于 $\mathcal{G}$ 完备，且对所有 $g\in\mathcal{G}$ 有 $g^{h}(\cdot)\in[0,1]$。如果我们在算法 18.3 中设置 $\beta_{t}$ 为

$$\beta_{t}^{2}\ge\inf_{\epsilon>0}\left[4\epsilon t(4+\epsilon)+2.4\ln\left(16M(\epsilon,\mathcal{F},\|\cdot\|_{\infty})^{2}M(\epsilon,\mathcal{G},\|\cdot\|_{\infty})/\delta^{2}\right)\right],$$

其中 $M(\cdot)$ 表示 $\|\cdot\|_{\infty}$ 打包数，且 $\|f\|_{\infty}=\sup_{h,x,a}|f^{h}(x,a)|$，则我们有

$$\mathbb{E}\sum_{t=2}^{T}[V_{*}^{1}(x_{t}^{1})-V_{\pi_{t}}^{1}(x_{t}^{1})]\le\delta T+\sqrt{\tilde d H\left(\epsilon T+\epsilon' T^{2}+\delta T^{2}+4\sum_{t=2}^{T}\beta_{t-1}^{2}\right)},$$

其中 $\tilde d=\sum_{h=1}^{H}\mathrm{EC}_{V}^{h}(\epsilon,\mathcal{F},T)\max(1,\mathrm{CC}^{h}(\epsilon',\tilde\pi,\mathcal{F}))$。

证明概要 首先，我们希望通过使用其证明中的相同记号来证明定理 18.14 关于 $\beta_{t}$ 的类比。使用相同的次高斯对数矩生成函数，通过对每个轨迹取条件期望，我们得到定理 13.11 中 (18.4) 的以下对应形式。以至少 $1 - \delta/2$ 的概率，对所有 $f_e \in \mathcal{F}_e$, $g_e \in \mathcal{G}_e$ 和 $t \ge 0$，

$$\left|\underbrace{\sum_{s=1}^t \Delta_s^{h_s}(f_e,g_e)\epsilon_s^{h_s}(f_e)}_{A}\right| \le \frac{1}{\lambda}\sum_{s=1}^t \ln \mathbb{E}_{h_s}\mathbb{E}_{x_s^{h_s},a_s^{h_s}} \exp\left(\frac{\lambda^2\Delta_s^{h_s}(f_e,g_e)^2}{8}\right) + \frac{\ln(4M_1M_2/\delta)}{\lambda},$$

其中我们选择 $\lambda = 0.9$。令 $\xi = \lambda^2\Delta_s^{h_s}(f_e,g_e)^2/8$，则 $\xi \le 0.9^2/8 \le 0.102$，且因此

$$\frac{1}{\lambda}\ln\mathbb{E}\exp(\xi) \le \frac{1}{\lambda}[\mathbb{E}\exp(\xi)-1] \le \frac{\exp(0.102)}{\lambda}\mathbb{E}\xi.$$

通过结合前两个不等式，并使用 $\exp(0.102)\lambda \le 1$，且 $1/\lambda \le 1.2$，我们得到

$$A \le \sum_{s=1}^t \frac{1}{H}\sum_{h=1}^H \mathbb{E}_{x_s^{h}\sim\pi_s, a_s^{h}\sim\tilde{\pi}(\cdot|x_s^{h})}\frac{\Delta_s^{h}(f_e,g_e)^2}{8} + 1.2\ln(4M_1M_2/\delta).$$

该不等式可以替换定理 18.14 证明中的 $(18.4)$。同样的论证导致以下不等式作为 $(18.5)$ 和 $(18.6)$ 的对应形式。以至少 $1 - \delta$ 的概率，对所有 $f \in \mathcal{F}$, $g \in \mathcal{G}$，且 $t \ge 0$，

$$\left|\sum_{s=1}^t \Delta_s^{h_s}(f,g)\epsilon_s^{h_s}(f)\right| \le \frac{1}{4H}\sum_{s=1}^t\sum_{h=1}^H \mathbb{E}_{x_s\sim\pi_s, a_s\sim\tilde{\pi}(\cdot|x_s)}\Delta_s^{h}(f,g)^2 + \epsilon t(4+\epsilon) + 1.2\ln(4M_1M_2/\delta),$$

$$\left|\sum_{s=1}^t \Delta_s^{h_s}(f,f)\epsilon_s^{h_s}(f)\right| \le \frac{1}{4H}\sum_{s=1}^t\sum_{h=1}^H \mathbb{E}_{x_s\sim\pi_s, a_s\sim\tilde{\pi}(\cdot|x_s)}\Delta_s^{h}(f,f)^2 + \epsilon t(4+\epsilon) + 1.2\ln(4M_1/\delta).$$

我们可以设置

$$0.5\beta_t^2 \ge [\epsilon t(4+\epsilon) + 1.2\ln(4M_1M_2/\delta)] + [\epsilon t(4+\epsilon) + 1.2\ln(4M_1/\delta)]$$

如定理 18.14 证明中所述，并得到 $Q_* \in \mathcal{F}_t$，且

$$\frac{1}{H}\sum_{s=1}^t\sum_{h=1}^H \bar{\mathcal{E}}^h(f,\pi_s\tilde{\pi})^2 \le 4\beta_t^2,$$

其中 $\bar{\mathcal{E}}^h$ 在命题 18.33 中定义。结果现在直接由命题 18.33 和定理 18.21 的相同推导得出。$\square$

值得指出的是，虽然算法 18.3 返回具有良好平均遗憾的策略 $\pi_t$，但在线算法本身并不能实现这种遗憾，因为算法需要采用与 $\pi_t$ 不同的单步纯探索策略 $\tilde{\pi}$。该策略的目的是同等覆盖所有可能的动作（例如通过使用非线性 G-最优设计）。它类似于第 17.5 节中上下文 bandit 的纯探索，也采用非线性 G-最优设计。尽管如此，该算法可以在不知道底层 Bellman 分解的情况下，使用非线性 Q 函数类解决低 Bellman 秩 MDP 问题。如果我们考虑具有 d 维未知特征映射的线性 MDP，并假设我们有有限的 K 个动作，其中 F 包含 M_F 个成员，G 包含 M_G 个成员，则 \tilde d = \tilde O(HdK)，\beta_t^2 = \tilde O(ln(M_F M_G))。因此由算法 18.3 返回的 $\pi_t$ 的遗憾满足

\mathbb{E}[V_*^1(x_1^1) - V_{\pi_t}^1(x_1^1)] = \tilde O\left( H\sqrt{dK\ln(M_\mathcal{F}M_\mathcal{G})}\right).

与定理 18.21 的结果相比，该结果差了一个 $\sqrt{HK}$ 因子。$\sqrt{H}$ 因子是由于随机的 h_t 选择，它没有有效地利用轨迹中的所有数据。$\sqrt{K}$ 因子是由于在不知道底层 Bellman 分解的特征映射的情况下，使用非线性 Q 函数类进行纯探索。

## 18.5 基于模型的强化学习

在线性 MDP 中，版本空间 UCB 算法不需要知道或学习转移概率 P^h(x^{h+1}|x^h,a^h)。在强化学习中，这样的算法被称为无模型。另一方面，如果学习算法估计并使用转移概率 P^h(x^{h+1}|x^h,a^h) 信息，则相应的方法被称为基于模型。与查看 Q 函数类不同，在基于模型的 RL 中，我们考虑一类 MDP 模型并显式估计转移概率。

## 定义 18.35

在基于模型的 RL 问题中，我们给定一个 MDP 模型类 \mathcal{M}。每个 M \in \mathcal{M} 包含显式的转移概率

P_M^h(x^{h+1}|x^h,a^h),

和期望奖励

R_M^h(x^h,a^h) = \mathbb{E}_M[r^h|x^h,a^h].

我们使用 \mathbb{E}_M[\cdot] 表示相对于模型 M 的转移动态 P_M 的期望。给定 \mathcal{X} 上的任意 f^{h+1}，我们定义模型 Bellman 算子

(\mathcal{T}_M^h f)(x^h,a^h) = R_M^h(x^h,a^h) + \mathbb{E}_M[f^{h+1}(x^{h+1})|x^h,a^h].

我们使用 f_M = \{f_M^h(x^h,a^h)\}_{h=1}^H 表示模型 M 的 Q 函数，并使用 \pi_M = \pi_{f_M} 表示模型 M 下的相应最优策略。

我们还将对基于模型的 RL 提出以下假设。

## 假设 18.36

设 \mathcal{M} 为一类 MDP 模型。我们假设正确的模型 M_* \in \mathcal{M}：真实的转移概率由 P_{M_*}^h(x^{h+1}|x^h,a^h) 给出，且真实的期望奖励由
