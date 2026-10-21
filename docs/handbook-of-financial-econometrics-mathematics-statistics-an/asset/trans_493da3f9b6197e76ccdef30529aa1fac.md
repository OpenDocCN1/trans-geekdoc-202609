
$(\alpha, \delta)$ 的估计 $\hat{\beta}$ 为

$$\hat{\beta} = (x_h' x_h)^{-1} x_h' y_h, \quad \text{var}(\hat{\beta}) = (x_h' x_h)^{-1} \sigma_v^2 (1 - \rho^2)$$

$(\alpha, \delta)$ 的后验分布为

$$\begin{pmatrix} \alpha \\ \delta \end{pmatrix} \mid \hat{\beta}, d, \rho, \sigma_v \sim N(\tilde{\beta}, \tilde{V})$$

其中 $\tilde{V} = \text{var}(\hat{\beta})^{-1} + (\sigma_{\beta_0}^2)^{-1}$，$\tilde{\beta} = \tilde{V}\big(\text{var}(\hat{\beta})^{-1} \hat{\beta} + (\sigma_{\beta_0}^2)^{-1} \beta_0\big)$。

$d$ 的后验分布可以类似地推导。由 $u_t$ 与 $\varepsilon_t$ 之间的关系，我们有

$$\varepsilon_t = \frac{\rho}{\sigma_v} u_t + b_{1t},$$

其中 $u_t$ 与 $b_{1t}$ 独立，且 $b_{1t} \sim N(0, 1 - \rho^2)$。

由于我们有 $\tilde{r}_t = d + \sqrt{h_{t-1}} \varepsilon_t$，代入 $u_t$ 与 $\varepsilon_t$ 的关系，方程可写为

$$\left( \frac{\tilde{r}_t}{\sqrt{h_{t-1}}} - \frac{\rho}{\sigma_v} u_t \right) = \frac{1}{\sqrt{h_{t-1}}} d + b_{1t}.$$

令

$$y_r = \frac{\tilde{r}_t}{\sqrt{h_{t-1}}} - \frac{\rho}{\sigma_v} u_t \quad \text{and} \quad x_r = \frac{1}{\sqrt{h_{t-1}}}$$

则 $\hat{d} = (x_r' x_r)^{-1} x_r' y_r$，$\text{var}(\hat{d}) = (x_r' x_r)^{-1} (1 - \rho^2)$。

假设 $d$ 的先验为正态分布，均值为 $d_0$，方差为 $\sigma_{d_0}^2$，则其后验分布为 $d \sim N(\tilde{d}, \tilde{V}_d)$，其中 $\tilde{V}_d = \text{var}(\hat{d})^{-1} + (\sigma_{d_0}^2)^{-1}$，$\tilde{d} = \tilde{V}_d\big(\text{var}(\hat{d})^{-1} \hat{d} + (\sigma_{d_0}^2)^{-1} d_0\big)$。

我们使用单步抽样器来更新 $h_t$。也就是说，在给定时间 $t$ 的其他状态变量和参数的情况下，推导出波动率 $h_t$ 的后验。随着时间向前推移，我们继续更新剩余的波动率状态变量。使用随机游走Metropolis算法对 $h_t$ 的后验进行抽样。注意状态方程中存在跳跃成分，我们在给定跳跃大小的条件下更新 $h_t$。我们将方程(52.4)重写如下：

$$\tilde{r}_t \equiv r_t - \xi_t^r J_t^r = d + \sqrt{h_{t-1}} \varepsilon_t$$

$$\tilde{h}_t \equiv h_t - \xi_t^v J_t^v = \alpha + \delta h_{t-1} + \sqrt{h_{t-1}} u_t,$$

其中 $\tilde{h}_t \equiv h_t - \xi_t^v J_t^v$ 是 $h_t$ 中与跳跃无关的部分。

在时间 $t + 1$，我们有

$$\tilde r_{t+1} \equiv r_{t+1} - \xi_{t+1}^r J_{t+1}^r = d + \sqrt{\tilde h_t + \xi_t^v J_t^v}\, \varepsilon_t$$

$$\tilde h_{t+1} \equiv h_{t+1} - \xi_{t+1}^v J_{t+1}^v = \alpha + \delta(\tilde h_t + \xi_t^v J_t^v) + \sqrt{\tilde h_t + \xi_t^v J_t^v}\, u_t,$$

因为

$$p(\tilde h_t|h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v,\xi_{t+1}^v J_{t+1}^v)=\frac{p(\tilde h_t,h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v)}{p(h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v,\xi_{t+1}^v J_{t+1}^v)}$$

$$=\frac{p(\tilde h_{t+1}|\tilde h_t,\bullet)p(\tilde h_t|h_{t-1},\bullet)p(h_{t-1})}{p(\tilde h_{t+1}|h_{t-1},\bullet)p(h_{t-1})}$$

$$\propto p(\tilde h_{t+1}|\tilde h_t,\bullet)p(\tilde h_t|h_{t-1},\bullet)$$

因此，我们得到 $\tilde h_t$ 的后验

$$p(\tilde h_t|h_{t-1},\tilde h_{t+1},\xi_t^v J_t^v,\xi_{t+1}^v J_{t+1}^v)$$

$$\propto (\tilde h_t + \xi_t^v J_t^v)^{-1} \exp\left\{ -\frac12 \left[ \operatorname{tr}\left( \sum^{*-1} \tilde e_t \tilde e_t' \right) + \operatorname{tr}\left( \sum^{*-1} \tilde e_{t+1} \tilde e_{t+1}' \right) \right] \right\}$$

$$\propto (\tilde h_t + \xi_t^v J_t^v)^{-1} \exp\left\{ -\frac{[\tilde h_t - (\alpha + \delta h_{t-1} + \psi(\tilde r_t - d))]^2}{2\Omega h_{t-1}} - \frac{(\tilde r_{t+1} - d)^2}{2(\tilde h_t + \xi_t^v J_t^v)} \right.$$

$$\left. - \frac{\delta^2}{2\Omega(\tilde h_t + \xi_t^v J_t^v)} \left[ \tilde h_t + \xi_t^v J_t^v - \frac{1}{\delta}[\tilde h_{t+1} - \alpha] \right]^2 + \frac{\psi}{\Omega} \frac{(\tilde h_{t+1} - \alpha)\tilde r_{t+1}}{\tilde h_t + \xi_t^v J_t^v} \right\}.$$

(52.6)

$\xi_t^v$ 的后验可由以下关系推导：

$$p(\xi_t^v|\xi_t^r, r_t, h_t, J_t = 1)$$

$$\propto p(r_t, h_t|\xi_t^v, \xi_t^r, J_t = 1) p(\xi_t^v|u_v, J_t = 1).$$

我们知道 $p(r_t, h_t|\theta, h_{t-1}, \xi_t^v, \xi_t^r) \propto h_{t-1}^{-1} |\Sigma|^{-1/2} e^{-\frac12 tr(\Sigma^{-1} e_t e_t')}, e_t = (\varepsilon_t, u_t)'$。因此，

$$p(\xi_t^v|\xi_t^r, r_t, h_t, J_t = 1)$$

$$\propto p(r_t, h_t|\xi_t^v, \xi_t^r, J_t = 1) p(\xi_t^v|u_v, J_t = 1)$$

$$\propto \left\{ e^{-\frac12 tr(\Sigma^{-1} e_t e_t')} \right\} \left\{ e^{-\frac{\xi_t^v}{u_v}} \right\}$$

其中 $u_t = (h_t - \alpha - \delta h_{t-1} - \xi_t^v J_t^v)/\sqrt{h_{t-1}}$。$J_t^r$ 服从伯努利分布，其中取1的概率为 $p_t^r$。容易看出 $\frac{p_t^r}{1-p_t^r}=O_t^r$，所以 $p_t^r = \frac{O_t^r}{1+O_t^r}$。

我们选择Beta分布作为 $\lambda_r$ 的先验，即 $\text{prior}(\lambda_r)=\text{Beta}(a,b)\propto \lambda_r^{a-1}(1-\lambda_r)^{b-1}$。后验为 $p(\lambda_r|J_r)\propto p(J_r|\lambda_r)\text{prior}(\lambda_r)\propto[\lambda_r^{\sum_{t=1}^T J_t}(1-\lambda_r)^{T-\sum_{t=1}^T J_t}]\lambda_r^{a-1}(1-\lambda_r)^{b-1}\propto\lambda_r^{a^*}(1-\lambda_r)^{b^*}$，其中 $a^*=a+\sum_{t=1}^T J_t-1$，$b^*=b+T-\sum_{t=1}^T J_t-1$。

$u_r$ 和 $\sigma_r^2$ 的后验可以按照标准回归理论推导，因此此处省略。状态方程中的跳跃的后验可以用类似方法推导。

假设 $u_v$ 的先验服从 $IG(\varphi_v,\lambda_v)$。因此，后验可以写为

$p(u_v|\xi_{t|t=1}^v)\propto p(\xi_{t|t=1}^v|u_v)\text{prior}(u_v)$

$\propto u_v^{I}\exp\!\left(-\frac{1}{u_v}(\xi_{i1}^v+\xi_{i2}^v+\cdots+\xi_{iI}^v)\right)u_v^{-(\varphi_v+1)}\exp\!\left(-\frac{\lambda_v}{u_v}\right)$

$\propto u_v^{-(\varphi_v+I+1)}\exp\!\left(-\frac{\lambda_v+\sum_{t=1}^I\xi_{it}^v}{u_v}\right)$.

因此，$u_v$ 的后验服从逆伽马分布 $IG(\varphi_v+I,\lambda_v+\sum_{t=1}^I\xi_{it}^v)$。

## 52.3 实证结果

我们的数据集是1996年1月10日至2003年10月12日泰铢的日变动率，共1,877个观测值。我们的样本期涵盖了亚洲金融危机，这使我们能够利用各种跳跃模型来研究市场崩溃事件。图52.1绘制了泰铢的日变动率；不同时期的波动性差异巨大。例如，1997年5月之前的时期，日变动率很少超过1%，但在之后的时期这变得非常普遍。极端值在我们的时间序列中也扮演重要角色；一些数据点明显大于其他数据点。

我们首先使用Merton（1976a，1976b）的独立跳跃模型开始对泰铢跳跃行为的实证研究。

$r_{t+1}=u+\sigma\varepsilon_{t+1}+\zeta_{t+1}J_{t+1}$,

其中 $\varepsilon_{t+1}$ 服从标准正态分布，$\zeta_{t+1}$ 是均值为 $\zeta_0$、方差为 $\sigma_\zeta^2$ 的正态随机变量。这里，$\zeta_{t+1}$ 代表那些罕见但数量较大的观测值，且 σ_ζ² > σ²。换言之，该模型假设外汇变动率是两个正态分布随机变量的混合。如果泰铢存在任何跳跃行为，该模型的估计结果应能让我们对其有一个基本了解。表52.2总结了Merton独立跳跃模型的MCMC估计结果。估计收敛很快，因此统计量由最后2,000次迭代计算得出；舍弃前1,000次迭代。该模型将泰铢日变动率分为两组：低跳跃组，均值为 u = −0.0019，标准差为 σ = 0.316；高跳跃组，均值为 ζ₀ + u = 0.145，标准差为 √(σ_ζ² + σ²) = 2.2。发生高跳跃的概率为 λ = 0.138。注意，表52.3中样本标准差为0.926，因此大多数汇率变动（低跳跃组）远小于样本标准差。因此，估计结果表明，少数日变动率大于通常水平的观测值对样本标准差的贡献很大。

尽管Merton的独立跳跃模型表明泰铢日变动率的某些部分明显大于其他部分，但估计结果有些不太合理。出现高跳跃观测值的概率 λ 为0.138，这意味着一年中有超过30个交易日出现高跳跃值。常识告诉我们，这一频率过高。这一结果的一个原因是该模型未考虑汇率时间序列中众所周知的异方差效应。为了解释条件异方差效应，我们首先估计一个平方根SV模型，其结果见表52.1。

与英镑/美元、德国马克/美元、日元/美元和瑞士法郎/美元的估计类似（Kim, Shephard, and Chib, 1998），泰铢/美元时间序列具有较高的持续性方差（δ = 0.993）。杠杆效应较小（ρ = −0.012），这与英镑和德国马克的行为相似（Jacquier et al., 2003）。然而，估计是有偏的，这从以下三点可以清楚地看出。第一，估计波动率的期望值为0.637，远小于样本方差0.857。第二，在1997年7月2日下跌之前，估计波动率从4月17日开始持续上升了53天。在汇市中没有任何异常行为的迹象可以与4月份的波动率上升相关联。第三，7月2日的估计方差为5.261，这意味着17%的变动是超过七个标准差的实现。此类事件发生的概率如此之低，强烈表明存在估计偏差。
