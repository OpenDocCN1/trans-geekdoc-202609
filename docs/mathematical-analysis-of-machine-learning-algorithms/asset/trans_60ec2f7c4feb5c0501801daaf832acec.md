

$$\mathbb{E}_{M_*}[r^h \mid x^h, a^h] = R^h_{M_*}(x^h, a^h).$$

我们假设$r^h + f_M^h(x^h, a^h) \in [0,1]$且$f_M^1(x^1) \in [0,1]$。我们还假设存在一个规划预言机，它能对任意给定模型$M \in \mathcal{M}$求解最优策略$\pi_M$和$Q$函数$f_M^h(x^h, a^h)$。

基于模型的强化学习的一个优势是：如果模型贝尔曼算子$(\mathcal{T}_M^h f)(x^h, a^h)$能被高效计算，则不需要完备性假设。在这种情况下，我们可以简单地将模型值与$r^h + f^{h+1}(x^{h+1})$进行比较，后者是真实贝尔曼算子$(\mathcal{T}_{M_*}^h f)(x^h, a^h)$的无偏估计。利用这一观察，可以定义以下损失函数

$$L^h(M, M', x^h, a^h, r^h, x^{h+1}) = \big((\mathcal{T}_M^h f_{M'})(x^h, a^h) - r^h - f_{M'}(x^{h+1})\big)^2, \qquad (18.16)$$

我们称之为值目标损失，以与Ayoub等人（2020）一致。自然地，一个好模型的值目标损失应当能很好地拟合历史数据。这使我们能够为$\mathcal{M}$中的模型定义一个版本空间。然后我们可以像算法17.4和算法18.1那样应用乐观的一般原则。所得到的算法在算法18.4中给出。由于我们不需要完备性，该算法的分析是算法17.4的直接扩展。

## 算法18.4 值目标损失UCB算法

```
输入：$\lambda, T, \mathcal{M}$
1 令 $\mathcal{F}_0=\{f_0\}$
2 令 $\beta_0=0$
3 对 $t=1,2,\dots,T$ 执行：
4   观察 $x_t^1$
5   令 $M_t\in\arg\max_{M\in\mathcal{M}_{t-1}}f_M(x_t^1)$。令 $\pi_t=\pi_{M_t}$
6   执行策略 $\pi_t$ 并观察轨迹 $(x_t,a_t,r_t)$
7   令 $\hat{M}_t=\arg\min_{M\in\mathcal{M}}\sum_{h=1}^H\sum_{s=1}^t L^h(M,M_s,x_s^h,a_s^h,r_s^h,x_s^{h+1})$，其中 $L^h(\cdot)$ 按 (18.16) 定义。
8   定义 $\mathcal{M}_t=\{M\in\mathcal{M}:\sum_{h=1}^H\sum_{s=1}^t\big((\mathcal{T}_M^h f_{M_s})(x_s^h,a_s^h)-(\mathcal{T}_{M_t}^h f_{M_s})(x_s^h,a_s^h)\big)^2\le\beta_t^2\}$，其中 $\beta_t$ 被适当选取。
9 从 $t=1$ 到 $t=T$ 的范围内随机返回一个 $\pi_t$
```

为了分析算法18.4，我们需要为基于模型的强化学习问题引入基于模型的贝尔曼误差的概念。

## 定义18.37（基于模型的贝尔曼误差）

对于基于模型的强化学习，给定模型$M$和候选$Q$函数$f$，我们将相应的基于模型的贝尔曼误差定义为

$$\mathcal{E}^h(M, f, x^h, a^h) = (\mathcal{T}_M^h f)(x^h, a^h) - (\mathcal{T}_{M_*}^h f)(x^h, a^h) = \mathbb{E}_M[r^h + f(x^{h+1}) \mid x^h, a^h] - \mathbb{E}_{M_*}[r^h + f(x^{h+1}) \mid x^h, a^h].$$

我们还使用以下简化记号：

$$\mathcal{E}^h(M, x^h, a^h) = \mathcal{E}^h(M, f_M, x^h, a^h).$$

$\mathcal{E}^h(M, x^h, a^h)$的定义与定义18.10中相应的无模型贝尔曼误差$\mathcal{E}^h(f_M, x^h, a^h)$一致：

$$\mathcal{E}^h(M, x^h, a^h) = \mathcal{E}^h(f_M, x^h, a^h). \quad (18.17)$$

这立即得到定理18.11对基于模型的强化学习的如下特化。其证明留作练习18.6。

## 定理18.38

考虑一个模型$M$，其价值函数为$f_M$，最优策略为$\pi_M$。那么我们有

$$[f_M(x^1) - V_{\pi_M}^1(x^1)] = \mathbb{E}_{(x,a,r)\sim \pi_M \mid x^1} \sum_{h=1}^H \mathcal{E}^h(M, x^h, a^h)$$

其中$V_{\pi_M}^1(x^1)$是真实底层MDP $M_*$的真实价值函数，$(x,a,r) \sim \pi_M \mid x^1$表示策略$\pi_M$在真实MDP $M_*$下的轨迹。

我们现在可以介绍基于模型的强化学习的贝尔曼消去系数的定义。与定义18.19中将同策略贝尔曼误差$\mathcal{E}^h(M_t, x_t^h, a_t^h)$归约为历史训练数据上的平方贝尔曼误差不同，我们可以将其归约为不同的损失函数。注意，与定义18.19类似，为了更一般性，我们以期望形式定义它。

## 定义18.39（基于模型的贝尔曼消去系数）

考虑任意损失函数序列$L = \{L_t^h(M, M_*): \mathcal{M} \times \mathcal{M} \to \mathbb{R}_+, t \in [T], h \in [H]\}$，其中每个损失函数$L_t^h$还可能依赖于$(M_t, x_t^h, a_t^h)$。一个基于模型的强化学习问题$\mathcal{M}$的$L$-损失贝尔曼消去系数$\mathrm{EC}_L(\epsilon, \mathcal{M}, T)$是最小的$d$，使得对于任意过滤序列$\{M_t, (x_t, r_t, a_t) \sim \pi_{M_t}, L_t\}_{t=1}^T$，

$$\mathbb{E} \sum_{t=2}^T \sum_{h=1}^H \mathcal{E}^h(M_t, x_t^h, a_t^h) \le \sqrt{d \, \mathbb{E} \sum_{h=1}^H \sum_{t=2}^T \left( \epsilon + \sum_{s=1}^{t-1} L_s^h(M_t, M_*) \right)}$$

定义18.39是通用的，因此它可以同时涵盖$Q$型问题和$V$型问题。本节中我们只考虑$Q$型问题。下面，我们介绍几个常用于基于模型的强化学习的$Q$型损失函数。

## 定理18.43

假设假设18.36成立。考虑函数类$\mathcal{F} = \{f^h(M', x^h, a^h): \mathcal{M} \times \mathcal{X} \times \mathcal{A} \to \mathbb{R}\}$，它包含$\{\mathcal{E}^h(M, \cdot, \cdot, \cdot): M \in \mathcal{M}\}$。假设在算法18.4中，我们令

$$\beta_t^2 \ge \inf_{\epsilon>0}\left[4\epsilon tH\left(1+4\epsilon\right)+3\ln\left(2\mathcal{N}(\epsilon,\mathcal{F},\|\cdot\|_\infty)/\delta\right)\right].$$

其中$\|f\|_\infty = \sup_{M', x^h, a^h} |f^h(M', x^h, a^h)|$。那么

$$\mathbb{E}\sum_{t=2}^{T}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right]\leq \delta HT+\sqrt{d\left(\epsilon HT+\delta HT^2+4\sum_{t=2}^{T}\beta_{t-1}^2\right)},$$

其中$V_{\pi_t}^1$是策略$\pi_t$的真实价值函数，$d = \mathrm{EC}_{Q\text{-}VT}(\epsilon, \mathcal{M}, T)$。

### 证明。

令$f_t = f_{M_t}$。对于$t \ge 2$，我们有

$$\begin{aligned} V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1) &= V_*^1(x_t^1)-f_t(x_t^1)+f_t(x_t^1)-V_{\pi_t}^1(x_t^1) \\ &\leq \mathbf{1}(M_*\notin\mathcal{M}_{t-1})+f_t(x_t^1)-V_{\pi_t}^1(x_t^1) \\ &= \mathbf{1}(M_*\notin\mathcal{M}_{t-1})+\mathbb{E}_{(x_t,a_t,r_t)\sim\pi_t\mid x_t^1}\sum_{h=1}^{H}\mathcal{E}^h(M_t,x_t^h,a_t^h). \end{aligned}$$

不等式利用了以下事实：如果$M_* \in \mathcal{M}_{t-1}$，则$f_t(x_t^1) = \max_{M\in\mathcal{M}_{t-1}} f_M(x_t^1) \ge V_*^1(x_t^1)$；如果$M_* \notin \mathcal{M}_{t-1}$，则$V_*^1(x_t^1) - f_t(x_t^1) \le 1$。第二个等式使用了定理18.38。

引理18.42表明$\Pr(M_* \in \mathcal{M}_{t-1}) \ge 1 - \delta$。我们有

$$\mathbb{E}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right]\leq \delta+\mathbb{E}\sum_{h=1}^{H}\mathcal{E}^h(M_t,x_t^h,a_t^h).$$

我们现在可以得到

$$\begin{aligned} \mathbb{E}\sum_{t=2}^{T}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right] &\leq \mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\mathcal{E}^h(M_t,x_t^h,a_t^h)+\delta T \\ &\leq \delta T+\sqrt{\operatorname{EC}_{Q\text{-}VT}(\epsilon,\mathcal{M},T)\,\mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\left(\epsilon+\sum_{s=1}^{t-1}\mathcal{E}^h(f_{M_s},x_s^h,a_s^h)^2\right)} \\ &\leq \delta T+\sqrt{\operatorname{EC}_{Q\text{-}VT}(\epsilon,\mathcal{M},T)\left(\epsilon HT+\delta HT^2+4\sum_{t=2}^{T}\beta_{t-1}^2\right)}. \end{aligned}$$

第二个不等式使用了定义18.39。最后一个不等式使用了以下事实：事件$M_* \notin \mathcal{M}_{t-1}$的概率至多为$\delta$，在这种情况下$\mathcal{E}^h(f_t, x_s^h, a_s^h)^2 \le 1$；当$M_* \in \mathcal{M}_{t-1}$时，有

$$\begin{aligned} \sum_{h=1}^{H}\sum_{s=1}^{t-1} \mathcal{E}^h(M_t, f_{M_s}, x_s^h, a_s^h)^2 &= \sum_{h=1}^{H}\sum_{s=1}^{t-1} \big((\mathcal{T}_{M_t}^h f_{M_s})(x_s^h, a_s^h) - (\mathcal{T}_{M_*}^h f_{M_s})(x_s^h, a_s^h)\big)^2 \\ &\le 2\sum_{h=1}^{H}\sum_{s=1}^{t-1}\Big[ \big((\mathcal{T}_{M_t}^h f_{M_s})(x_s^h, a_s^h) - (\mathcal{T}_{M_{t-1}}^h f_{M_s})(x_s^h, a_s^h)\big)^2 \\ &\qquad + \big((\mathcal{T}_{M_*}^h f_{M_s})(x_s^h, a_s^h) - (\mathcal{T}_{M_{t-1}}^h f_{M_s})(x_s^h, a_s^h)\big)^2\Big] \\ &\le 4\beta_{t-1}^2. \end{aligned}$$

最后一个不等式使用了$M_t \in \mathcal{M}_{t-1}$和$M_* \in \mathcal{M}_{t-1}$。

基于模型方法的一个优势是，可以使用命题18.41中比值目标贝尔曼消去系数更弱的其他类型的贝尔曼消去系数。我们可以考虑Hellinger贝尔曼消去系数，它将同策略贝尔曼误差归约为历史训练数据上的Hellinger损失。后者可以使用对数似然（KL）损失和后验采样来界定，如推论10.26所示。因此，一种更通用的基于模型强化学习方法（使用更弱的贝尔曼消去系数）是使用对数似然损失直接估计模型参数$M$。给定轨迹$S_{t-1} = \{(x_s^h, a_s^h, r_s^h): h = 1,\dots, H, s = 1,\dots, t - 1\}$，我们可以定义一个带有乐观Feel-Good项的后验如下

$$p_t(M \mid x_1^t, S_{t-1}) \propto p_0(M) \exp\left( \lambda \sum_{s=1}^{t-1} f_M(x_s^1) + \sum_{h=1}^{H} \sum_{s=1}^{t-1} L_s^h(M) \right), \tag{18.18}$$

其中

$$L_s^h(M) = -\tilde{\eta}(R_M^h(x_s^h, a_s^h) - r_s^h)^2 + \eta \ln P_M^h(x_s^{h+1} \mid x_s^h, a_s^h).$$

然后我们可以像算法18.5那样使用后验采样，它只需要计算价值$f_M^1(x^1)$。与值目标方法相比，算法18.5用对数似然替代了对$h \ge 1$的$f_{M_s}^{h+1}(x_s^{h+1})$的积分，这对许多问题更为简单。由于该算法依赖于更弱的Hellinger贝尔曼消去系数，它在探索中可以更有效。例如，它适用于诸如基于模型的线性MDP（我们稍后将讨论）等值目标方法无法处理的问题。

尽管可以为算法18.5推导出一般的遗憾分析（例如参见Agarwal和Zhang，2022a），但一般分析除了对数似然项外，还需要处理奖励项和Feel-Good项$f_M^1(x_s^1)$。接下来，我们想专注于对数似然项的分析，因此我们将考虑如下简化版本。我们假设期望奖励已知，因此对所有$M \in \mathcal{M}$，$R_M^h(x^h, a^h) = R_{M_*}^h(x^h, a^h)$。此外，我们假设$x_t^1$的分布已知，因此$f_M = \mathbb{E}_{x^1} f^1(x^1)$也是给定的。通过这些修改，我们可以将(18.18)简化为

