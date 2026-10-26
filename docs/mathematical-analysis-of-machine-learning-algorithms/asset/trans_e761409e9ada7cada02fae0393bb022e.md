
方程 (a) 利用了这样一个事实：对于每个臂 $a$，当 $a_t = a$ 时，$\hat{n}_{t-1}(a_t)$ 从 $m = 1$ 取到 $m = \hat{n}_T(a) - 1$，每个值出现一次。在最后一个不等式的推导中，我们使用了 Jensen 不等式和 $\sqrt{z}$ 的凹性，这意味着

$$\sum_{a=1}^{K} \sqrt{\hat{n}_T(a)-1} \le \sqrt{K \sum_{a=1}^{K} (\hat{n}_T(a)-1)} = \sqrt{K(T-K)}.$$

这就得到了期望的界。

## 例 16.4

假设在定理 16.3 中，$\mu(a_*) \approx 0$。在这种情况下，我们可以在定理 13.5 中使用以下乘性 Chernoff 界来得到一个上置信界。我们知道以至少 $1 - \delta$ 的概率，

$$\mu(a) \le \frac{e}{e-1} \hat{\mu}_t(a) + \frac{e \ln(1/\delta)}{(e-1)\hat{n}_t(a)} \quad \text{and} \quad \hat{n}_t(a)=m.$$

这意味着我们可以在算法 16.1 中使用上置信界

$$\hat{c}_t(a) = \frac{1}{e-1} \hat{\mu}_t(a) + \frac{e \ln\left((2\hat{n}_t(a)+1)^2/\delta\right)}{(e-1)\hat{n}_t(a)}$$

为了得到比定理 16.3 更好的遗憾界，我们还需要对下置信区间使用乘性 Chernoff 界，然后用这样的乘性下置信区间界重复定理 16.3 的分析。我们将其留作练习。

## 例 16.5

假设对于每个臂 $a$，奖励 $r_t(a)$ 是次高斯随机变量，但不同臂具有不同的奖励分布：

$$\ln \mathbb{E} \exp(\lambda r_t(a)) \le \lambda \mathbb{E} r_t(a) + \frac{\lambda^2}{2} M(a)^2,$$

其中 $M(a)$ 已知。于是可以得到与定理 16.3 相似的界，其中 UCB 估计依赖于臂并包含 $M(a)$。

还可以得到一个依赖于 $a_*$ 与任意其他 $a$ 之间差距的引理 16.2 的改进版本。

## 引理 16.6

设 $a_* \in \arg \max_a \mu(a)$。令

$$\delta_1 = \Pr[\exists t > K : \mu(a_*) > \hat{\mu}_{t-1}(a_*) + \hat{c}_{t-1}(a_*)],$$

$$\delta_2 = \Pr[\exists t > K, a \in \{1,\dots,K\}\setminus\{a_*\} : \mu(a) < \hat{\mu}_{t-1}(a) - \hat{c}'_{t-1}(a)].$$

定义 $\Delta(a) = \mu(a_*) - \mu(a)$，且

$$T(a) = \max \{m : \Delta(a) \le \hat{c}_{t-1}(a) + \hat{c}'_{t-1}(a), \hat{n}_{t-1}(a) = m, K < t \le T\} \cup \{0\}.$$

那么对于算法 16.1，以至少 $1 - \delta_1 - \delta_2$ 的概率，有

$$\mathrm{REG}_T \le \inf_{\Delta_0>0} \left[ \sum_{a=1}^{K} T(a)\Delta(a)\mathbf{1}(\Delta(a) > \Delta_0) + (T-K)\Delta_0 \right] + \sum_{a=1}^{K} \Delta(a).$$

### 证明

引理 16.2 的证明表明以至少 \(1-\delta\) 的概率，对于所有 \(t \ge K+1\)，

$$\mu(a_*) \le \mu(a_t) + [\hat{c}'_{t-1}(a_t)+\hat{c}_{t-1}(a_t)]\mathbf{1}(a_t\ne a_*),$$

这意味着

$$\Delta(a_t) \le [\hat{c}'_{t-1}(a_t)+\hat{c}_{t-1}(a_t)]\mathbf{1}(a_t\ne a_*).$$

利用本引理的假设，我们得到对于所有 \(a\ne a_*\) 和 \(1\le t\le T\)，\(\hat{n}_{t-1}(a)\mathbf{1}(a_t=a)\le T(a)\)。

由此可知对于所有 \(a\ne a_*\)，令 \(t\) 为满足 \(a_t=a\) 的最后时刻，则 \(t\le T\) 且 \(\hat{n}_T(a)=\hat{n}_{t-1}(a_t)+1\le T(a)+1\)。于是我们对任意 \(\Delta_0\ge0\) 得到如下遗憾界：

$$\sum_{t=1}^{T}|\mu(a_*)-\mu(a_t)|=\sum_{a=1}^{K}\hat{n}_T(a)\Delta(a)$$

$$\le \sum_{a=1}^{K}\Delta(a)+\sum_{a=1}^{K}(\hat{n}_T(a)-1)\Delta_0+\sum_{a=1}^{K}(\hat{n}_T(a)-1)\Delta(a)\mathbf{1}(\Delta(a)>\Delta_0)$$

$$\le \sum_{a=1}^{K}\Delta(a)+(T-K)\Delta_0+\sum_{a=1}^{K}T(a)\Delta(a)\mathbf{1}(\Delta(a)>\Delta_0).$$

第二个不等式使用了 \(\sum_{a=1}^{K}\hat{n}_T(a)=T-K\) 且 \(\hat{n}_T(a)-1\le T(a)\)。这就得到了该界。

我们注意到在引理 16.6 中，\(\delta_1\) 仍是上置信界的失效概率，而 \(\delta_2\) 是下置信界的失效概率。量 \(T(a)\) 的直观意义是：在我们抽取臂 \(a\) 超过 \(T(a)\) 次之后，\(a\) 的置信区间变得小于差距 \(\Delta(a)\)，这意味着我们未来不会再选择臂 \(a\)。也就是说，\(T(a)\) 是对某个特定臂 \(a\) 的最大拉取次数。这意味着选择 \(a\) 造成的遗憾被 \(T(a)\Delta(a)\) 所上界。

利用引理 16.6，我们现在可以在定理 16.7 中得到一个依赖于差距的界。

## 定理 16.7

假设奖励 \(r_t(a)\in[0,1]\)。令 \(a_*\in\arg\max_a\mu(a)\)。

取

$$\hat{c}_t(a)=\sqrt{\frac{\ln(2(\hat{n}_t(a)+1)^2/\delta)}{2\hat{n}_t(a)}}.$$

我们有

$$\mathrm{REG}_T\le \inf_{\Delta_0>0}\left[(T-K)\Delta_0+\sum_{a=1}^{K}\frac{2\ln(2KT^2/\delta)}{\Delta(a)}\mathbf{1}(\Delta(a)>\Delta_0)\right]+\sum_{a=1}^{K}\Delta(a).$$

### 证明

由定理 16.3 的证明可知，在取

$\hat{c}'_t(a) = \sqrt{\frac{\ln\left(2K(\hat{n}_t(a)+1)^2/\delta\right)}{2\hat{n}_t(a)}}$

时，\(T(a)\) 定义中的不等式 $\Delta(a) \le \hat{c}_{t-1}(a) + \hat{c}'_{t-1}(a)$ 意味着

$\Delta(a) \le \sqrt{\frac{2\ln(2KT^2/\delta)}{\hat{n}_{t-1}(a)}}$

这意味着 $\hat{n}_{t-1}(a) \le \frac{2\ln(2KT^2/\delta)}{\Delta(a)^2}$。

因此 $T(a) \le \frac{2\ln(2KT^2/\delta)}{\Delta(a)^2}$。这由引理 16.6 得出期望的结果。

## 例 16.8

我们可以在定理 16.7 的依赖于差距的遗憾界中取 $\Delta_0 = 0$，并得到 $\mathrm{REG}_T \le \sum_{a=1}^K \frac{2\ln(2KT^2/\delta)}{\Delta(a)} + K$。

## 例 16.9

定理 16.7 的依赖于差距的遗憾界蕴含了定理 16.3 的不依赖于差距的遗憾界。事实上，若取 $\Delta_0 = \sqrt{\frac{K\ln(KT/\delta)}{T}}$，则由定理 16.7 可得遗憾 $\mathrm{REG}_T = O\left(\sqrt{KT\ln(KT/\delta)}\right)$。

迄今为止我们得到的结果要求在已知置信水平 $\delta$ 的情况下构造 UCB。这对于某些应用可能不方便。在下面，我们展示利用类似的分析，可以得到一个不依赖于 $T$ 或 $\delta$ 的 UCB 构造的遗憾分析。在分析中，我们首先引入一个引理来在无需考虑对所有 $t$ 统一成立的事件的情况下替代引理 16.6。引理 16.10 是引理 16.6 的一个变体，它分别考虑每个特定的时间步 $t$。它导出了一个在期望意义下成立的类似结果。

## 引理 16.10

设 $a_* \in \arg\max_a \mu(a)$。对 $t > K$，定义 $\delta_1(t) = \Pr[\mu(a_*) > \hat{\mu}_{t-1}(a_*) + \hat{c}_{t-1}(a_*)]$，$\delta_2(t) = \Pr[\exists a \in \{1,\dots,K\}\setminus\{a_*\} : \mu(a) < \hat{\mu}_{t-1}(a) - \hat{c}'_{t-1}(a)]$，且令

$\delta=\sum_{t>K}[\delta_1(t)+\delta_2(t)].$

定义 $\Delta(a)=\mu(a_*)-\mu(a)$，$M=\sup_a\Delta(a)$，且

$T(a)=\max\{m:\Delta(a)\le \hat c_{t-1}(a)+\hat c'_{t-1}(a),\hat n_{t-1}(a)=m, K<t\le T\}\cup\{0\}$。

那么对于算法 16.1，有

$\mathbb{E}\,\mathrm{REG}_T\le \inf_{\Delta_0>0}\left[\sum_{a=1}^{K}T(a)\Delta(a)\mathbf{1}(\Delta(a)>\Delta_0)+(T-K)\Delta_0+(K+\delta)M\right].$

### 证明

我们对任意固定的 $t>K$ 得到以概率 $1-\delta_1(t)$，$$\mu(a_*)\le \hat\mu_{t-1}(a_t)+\hat c_{t-1}(a_t).$$

此外，以概率 $1-\delta_2(t)$，$$\hat\mu_{t-1}(a_t)\le \mu(a_t)+\hat c'_{t-1}(a_t).$$

由引理 16.2 的相同推导可知以概率 $1-\delta_1(t)-\delta_2(t)$，$$\Delta(a_t)=\mu(a_*)-\hat\mu_{t-1}(a_t)\le \hat c_{t-1}(a_t)+\hat c'_{t-1}(a_t).$$

这意味着 $\hat n_{t-1}(a_t)\le T(a_t)$。由此可知对所有 $t>K$，

$\Pr(\hat n_{t-1}(a_t)>T(a_t))\le \delta_1(t)+\delta_2(t).$ \tag{16.4}

现在令

$\delta(a)=\sum_{t=K+1}^{T}\mathbb{E}\,\mathbf{1}(a_t=a,\hat n_{t-1}(a)>T(a)),$

则

$\sum_{a=1}^{K}\delta(a)=\sum_{a=1}^{K}\sum_{t=K+1}^{T}\Pr(a_t=a,\hat n_{t-1}(a)>T(a))$  
$\qquad=\sum_{t=K+1}^{T}\Pr(\hat n_{t-1}(a_t)>T(a_t))\le\delta.$

最后一个不等式使用了 (16.4) 和 $\delta$ 的定义。

现在我们对任意固定的 $a$ 有

$\mathbb{E}\,\hat n_T(a)=1+\mathbb{E}\sum_{t=K+1}^{T}\mathbf{1}(a_t=a)$

$\qquad=1+\sum_{t=K+1}^{T}\mathbb{E}\,\mathbf{1}(a_t=a,\hat n_{t-1}(a)\le T(a))+\sum_{t=K+1}^{T}\mathbb{E}\,\mathbf{1}(a_t=a,\hat n_{t-1}(a)>T(a))$

$\qquad\le 1+T(a)+\delta(a).$ \tag{16.5}
