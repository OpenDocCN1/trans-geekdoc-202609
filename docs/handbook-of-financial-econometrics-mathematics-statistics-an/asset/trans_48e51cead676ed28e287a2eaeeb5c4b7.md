

## 看涨期权定价

决策树

价格 = 30，行权价 = 32，U = 1.1000，D = 0.9000，N = 4，R = 0.03

计算次数：31

二项式看涨期权价格 = 3.2359

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3754_0.png)

图 102.3：看涨期权定价决策树。

参数——期数 n 变得非常大。Benninga 和 Czaczkes（2000）证明，当期数 n 大于 500 时，二项式值将接近布莱克-舒尔斯值。这里，我们将以强生公司看涨期权作为实际示例进行说明。参数如下：S = 93.45，X = 92.5，T = 0.3589，r = 2.75%。σ = 13.01%，该值是根据强生公司（JNJ）股票的日收益率估计得出的。市场观察到的看涨期权价格为 C = 3.65。

## 看涨期权定价

决策树
价格 = 30，行权价 = 32，U = 1.1052，D = 0.9048，N = 4，R = 0.03
计算次数：31
二项式看涨期权价格 = 2.0375
布莱克-舒尔斯看涨期权价格 = 1.9406，d1 = -0.0727，d2 = -0.2727，N(d1) = 0.4710，N(d2) = 0.3925

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3755_0.png)

图 102.4：布莱克-舒尔斯看涨期权定价的决策树近似。

对于布莱克-舒尔斯期权定价模型（OPM），我们可以得到
$N(d_1)=0.6175,\quad N(d_2)=0.5875.$

由布莱克-舒尔斯模型得出的看涨期权理论价值应为
$C = S N(d_1) - e^{-rT} X N(d_2) = 3.90.$

表 102.1 显示了随着 $n$ 增大，二项式 OPM 值如何收敛到布莱克-舒尔斯 OPM，其中上升因子（$u$）和下降因子（$d$）相应调整。

表 102.1：不同期数下的二项式 OPM 估计值。

| 期数 (n) | 上升因子 (u) | 下降因子 (d) | 二项式 OPM 的理论值 |
|---|---|---|---|
| 3 | 1.0460 | 0.9560 | 4.1285 |
| 4 | 1.0397 | 0.9618 | 3.8844 |
| 5 | 1.0355 | 0.9657 | 4.0306 |
| 6 | 1.0323 | 0.9687 | 3.9122 |
| 7 | 1.0299 | 0.9710 | 3.9888 |
| 8 | 1.0279 | 0.9728 | 3.9232 |
| 9 | 1.0263 | 0.9744 | 3.9657 |
| 10 | 1.0250 | 0.9757 | 3.9282 |

前面的例子表明，Excel 程序可用于演示二项式期权定价模型，并且当期数趋近无穷时，该模型可以收敛到布莱克-舒尔斯模型。

## 102.4 比较 Cox 等人与 Rendleman 和 Bartter 推导 OPM 的方法

Cox 等人（1979）以及 Rendleman 和 Bartter（1979）都使用方程 (102.13) 来展示当观测期数 n 趋近无穷时，二项式模型如何简化为布莱克-舒尔斯模型。在本节中，我们简要讨论这两篇论文所采用的方法。

### 102.4.1 Cox 等人的方法

Cox 等人（1979）使用以下二项式期权定价模型推导布莱克-舒尔斯模型：

$$C = S \left[ \sum_{j=a}^{n} \frac{n!}{j!(n-j)!} p^{j} (1-p)^{n-j} \frac{u^{j} d^{n-j}}{\hat{r}^{n}} \right] - X \hat{r}^{-n} \left[ \sum_{j=a}^{n} \frac{n!}{j!(n-j)!} p^{j} (1-p)^{n-j} \right] = S B_{1}(a; n, p') - X \hat{r}^{-n} B_{2}(a; n, p),$$ (102.23)

其中

$$B_1(a; n, p') = \sum_{j=a}^{n} C_j p'^{j} (1 - p')^{n-j},$$

$$B_2(a; n, p) = \sum_{j=a}^{n} C_j p^{j} (1 - p)^{n-j},$$

$$p' \equiv (u/\hat{r})p \text{ and } 1 - p' \equiv (d/\hat{r})(1 - p),$$

$$\hat{r} = 1 + \text{interest rate over one period},$$

a 是使期权到期时处于价内所需的最小向上股价变动次数。换句话说，a 是使得 $u^j d^{n-j} S - X > 0$ 成立的最小整数 j 值。

为了证明二项式期权定价公式收敛于布莱克-舒尔斯期权定价公式的连续形式这一极限结果，我们假设 h 表示连续股价变动之间经过的时间。因此，如果 t 是到期的固定日历时间长度，n 是每期长度为 h 的总期数，则 $h = \frac{t}{n}$。随着交易频率的增加，h 将更接近零。当 $h \to 0$ 时，这等价于 $n \to \infty$。

$\hat{r}$ 是 1 加上长度为 h 的交易时期内的利率。我们不仅希望 $\hat{r}$ 依赖于 n，而且希望它以特定方式依赖于 n——这样当 n 变化时，总回报 $\hat{r}^n$ 保持不变。我们将 r 记为 1 加上固定日历时间单位上的利率，那么在时间 t 内，总回报应为 $r^t$。于是，我们得到如下方程：

$$\hat{r}^n = r^t \tag{102.24}$$

对于任意选择的 n 都成立。因此，$\hat{r} = r^{\frac{t}{n}}$。令 $S^*$ 为初始价格为 S 的第 n 期结束时的股票价格。如果有 j 次向上移动，则广义表达式应为

$$\log(S^*/S) = j \log u + (n - j) \log d = j \log(u/d) + n \log d. \tag{102.25}$$

因此，j 是成功概率为 p 的二项随机变量的一个实现。我们得到 $\log(S^*/S)$ 的期望为

$$E(\log(S^*/S)) = [p \log(u/d) + \log d] n \equiv \tilde{\mu} n \tag{102.26}$$

其方差为

$$\text{var}(\log S^*/S) = [\log(u/d)]^2 p(1-p) n \equiv \tilde{\sigma}^2 n. \tag{102.27}$$

我们考虑将原始时间段 $t$ 划分为许多长度为 $h$ 的更短子时段，使得 $t = nh$。我们的做法需要在保持原始时间段 $t$ 固定的情况下增大 $n$。当 $n \to \infty$ 时，我们至少希望所假设的股价运动的连续复利收益率的均值和方差与实际股价的相一致。将 $\tilde{\mu}n$ 和 $\tilde{\sigma}^2n$ 的实际经验值分别记为 $\mu t$ 和 $\sigma^2t$。然后我们希望选择 $u$、$d$ 和 $p$，使得当 $n \to \infty$ 时，$\tilde{\mu}n \to \mu t$ 且 $\tilde{\sigma}^2n \to \sigma^2t$。

简单的代数运算表明，我们可以通过如下设定来实现这一目标：

$$u = e^{\sigma\sqrt{\frac{t}{n}}},\quad d = e^{-\sigma\sqrt{\frac{t}{n}}},$$ $$p = \frac{1}{2} + \frac{1}{2}\left(\frac{\mu}{\sigma}\right)\sqrt{\frac{t}{n}}.\tag{102.28}$$

此时，为了继续深入，我们需要中心极限定理的李雅普诺夫条件如下（Ash 和 Doleans-Dade 1999，Billingsley 2008）。

### 李雅普诺夫条件

假设 $X_1,X_2,\dots$ 是独立且一致有界的随机变量，满足 $E(X_i)=0$，令 $Y_n = X_1 + \cdots + X_n$，且 $s^2 = E(Y_n^2) = \operatorname{Var}(Y_n)$。

如果存在某个 $\delta>0$，使得 $\lim_{n\to\infty}\sum_{k=1}^n \frac{1}{s_n^{2+\delta}}E|X_k|^{2+\delta}=0$，则当 $n\to\infty$ 时，$\frac{Y_n}{s_n}$ 的分布收敛于标准正态分布。

### 定理. 如果

$$\frac{p|\log u - \tilde{\mu}|^3 + (1-p)|\log d - \tilde{\mu}|^3}{\tilde{\sigma}^3\sqrt{n}} \to 0 \text{ as } n\to\infty,\quad \text{then}\tag{102.29}$$ $$\Pr\left[\frac{\log\left(\frac{S^*}{S}\right) - \tilde{\mu}n}{\tilde{\sigma}\sqrt{n}} \le z\right] \to N(z),\tag{102.30}$$

其中 $N(z)$ 是标准正态分布的累积分布函数。

### 证明. 由于

$$p|\log u - \tilde{\mu}|^3 = p|\log u - p\log\frac{u}{d} - \log d|^3 = p(1-p)^3\left|\log\frac{u}{d}\right|^3$$ 且 $$(1-p)|\log d - \tilde{\mu}|^3 = (1-p)|\log d - p\log\frac{u}{d} - \log d|^3 = p^3(1-p)\left|\log\frac{u}{d}\right|^3,$$ 我们有 $$p|\log u - \tilde{\mu}|^3 + (1-p)|\log d - \tilde{\mu}|^3 = p(1-p)\big[(1-p)^2 - p^2\big]\left|\log\frac{u}{d}\right|^3.$$

因此

$$\frac{p|\log u - \tilde{\mu}|^3 + (1-p)|\log d - \tilde{\mu}|^3}{\tilde{\sigma}^3\sqrt{n}}$$

$$= \frac{p(1-p)[(1-p)^2 - p^2] |\log \frac{u}{d}|^3}{\left(\sqrt{p(1-p)}\log\left(\frac{u}{d}\right)\right)^3 \sqrt{n}}$$

$$= \frac{(1-p)^2 + p^2}{\sqrt{np(1-p)}}.$$

回顾 $p = \frac{\hat{r}-d}{u-d}$，其中 $\hat{r}=r^{t/n}$，$u = e^{\sigma\sqrt{t/n}}$，$d = e^{-\sigma\sqrt{t/n}}$，我们有

$$p = \frac{e^{\frac{t}{n}\log r} - e^{-\sigma\sqrt{\frac{t}{n}}}}{e^{\sigma\sqrt{\frac{t}{n}}} - e^{-\sigma\sqrt{\frac{t}{n}}}}$$

$$= \frac{1 + \frac{t}{n}\log r - \left[1 - \sigma\sqrt{\frac{t}{n}} + \frac12\sigma^2\frac{t}{n}\right] + O(n^{-3/2})}{1 + \sigma\sqrt{\frac{t}{n}} - \left[1 - \sigma\sqrt{\frac{t}{n}}\right] + O(n^{-3/2})}$$

$$= \frac12 + \frac12\left[\frac{\log r - \frac12\sigma^2}{\sigma}\right]\sqrt{\frac{t}{n}} + O(n^{-1})$$

因此，当 $n \to \infty$ 时，$\frac{(1-p)^2+p^2}{\sqrt{np(1-p)}} \to 0$。

因此，方程 (102.29) 所述定理成立的条件得到满足。需要注意的是，条件 (102.29) 是 $\delta = 1$ 时李雅普诺夫条件的特例。接下来，我们将证明方程 (102.23) 给出的二项式期权定价模型确实与布莱克-舒尔斯期权定价公式一致。我们可以看到，方程 (102.23) 中存在明显的相似性。为了证明极限结果，我们需要证明：

当 $n \to \infty$ 时，$B_1(a; n, p') \to N(x)$ 且 $B_2(a; n, p) \to N(x - \sigma\sqrt{t})$。在本节中，我们只证明第二个收敛结果，因为同样的论证对第一个收敛也成立。根据 $B_2(a; n, p)$ 的定义，显然

$$1 - B_2(a; n, p) = \Pr(j \le a - 1)$$

$$= \Pr\left(\frac{j - np}{\sqrt{np(1-p)}} \le \frac{a - 1 - np}{\sqrt{np(1-p)}}\right). \tag{102.31}$$

