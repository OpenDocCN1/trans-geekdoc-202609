

## 第65章

## 相对风险厌恶估计量的抽样分布：理论与应用

Marvin J. Karson, David C. Cheng and Cheng Few Lee

- 65.1 引言 ................ 2324
- 65.2 RRA估计量的概率密度函数的推导 ................ 2324
- 65.3 一个实证例子 ................ 2330
- 65.4 总结 ................ 2333
- 参考文献 ................ 2333
- 附录65A ................ 2334
- 注释 ................ 2335

Brown和Gibbons（1985）根据平均市场收益率和市场收益率的方差，建立了相对风险厌恶估计理论。然而，合适的相对风险厌恶估计量的精确抽样分布尚未被推导。首先，我们从理论上推导了Brown和Gibbons最大似然估计量的密度。结果表明，中心t分布不适用于检验所估计的相对风险厌恶分布的显著性。然后，我们通过Brown和Gibbons最大似然估计量的线性变换，推导出了最小方差无偏估计量。该密度函数既不是中心t分布，也不是非中心t分布。接着，我们编制了这一新分布的密度函数表。文中给出了一个实证例子来说明这一新抽样分布的应用。

Marvin J. Karson
新罕布什尔大学
电子邮箱：mjkarson@comcast.net

David C. Cheng
阿拉巴马大学

Cheng Few Lee
罗格斯大学
电子邮箱：cflee@business.rutgers.edu

*本章是题为“Sampling distribution of the relative risk aversion estimator: Theory and applications”的论文的重印版，该论文发表于《Review of Quantitative Finance and Accounting》，第5卷（1），43-54页（1995）。

## 65.1 引言

Brown和Gibbons（1985）根据平均市场收益率和市场收益率的方差，建立了相对风险厌恶估计理论。然而，相对风险厌恶估计量的精确抽样分布尚未被推导出来。本章的主要目的是推导一个合适的相对风险厌恶（RRA）估计量的精确抽样分布。基于该抽样分布的统计推断，对于研究金融中许多重要问题具有重大意义。例如，对数效用函数的适用性——它对金融中某些重要结果至关重要——现在可以基于单位相对风险厌恶的原假设进行检验（参见，例如，Cox等，1985；Hakanson，1970；Kraus和Litzenberger，1975；Merton，1971；Rubinstein，1977；Samuelson，1969）；风险厌恶程度变化对风险资产需求和储蓄决策的影响（参见，例如，Rothschild和Stiglitz，1971）现在可以进行实证评估；总风险厌恶变化对股票价格过度波动这一有争议问题的贡献（参见，例如，Grossman和Shiller，1981）也可以被正确估计。

65.2节将假定对数正态模型，推导一致最小方差无偏RRA估计量以及最大似然估计量的精确抽样分布。65.3节将探讨RRA估计量抽样分布的应用。65.4节总结研究结果。

## 65.2 RRA估计量的概率密度函数的推导

首先，我们建立一些符号和基本的对数正态分布设定。将市场收益率记为随机变量R_m，无风险收益率记为随机变量R_f。我们还令X = (1 − R_m)/(1 − R_f)，Y = log X。假设有一个容量为T的随机样本，其R_m的样本值为R_mt，R_f的样本值为R_ft，其中t = 1,2,…,T。那么X_t = (1 − R_mt)/(1 − R_ft)是X的第t个样本观测值，Y_t是Y的第t个样本观测值。我们将

Y_t = log X_t = log(1 − R_mt)/(1 − R_ft) = log(1 − R_mt) − log(1 − R_ft), (65.1)

视为第t个样本观测值的超额市场收益率。最后，我们将样本平均超额市场收益率记为

Ȳ = log X̄ = overline{log(1 − R_m)} − overline{log(1 − R_f)} = Σ_{t=1}^T Y_t / T

并将超额市场收益率的样本方差记为

S² = Σ_{t=1}^T (Y_t − Ȳ)² / (T − 1)。

在研究基于效用的资产定价模型时，Brown和Gibbons（1985）假设Y服从正态分布，或者等价地，X服从对数正态分布，参数为μ和σ²，分别为Y的均值和方差，并用估计量

β̂_ML = Ȳ / S² + 1/2. (65.2)

来估计相对风险厌恶参数β = (μ/σ²) + 1/2。注意，如果在(2)中使用((T − 1)/T) S²而不是S²，则β̂_ML才是最大似然估计量。

需要指出的是，β̂_ML是Ȳ / S²的函数。¹ 我们将证明，β的一致最小方差无偏估计量也是Ȳ / S²的函数，因此，我们首先在Y的正态性假设下推导Ȳ / S²的概率密度函数（pdf）。

因此，设Y₁, Y₂, …, Y_T是来自均值为μ、方差为σ²的正态分布的容量为T的随机样本，其中对于t = 1,2,…,T，Y_t由(65.1)给出。那么，由统计抽样理论，以下精确结果是众所周知的（Hogg and Craig, 1978）；

- 1. Ȳ服从均值为μ、方差为σ²/T的正态分布，
- 2. (T − 1) S² / σ²服从自由度为T − 1的卡方分布，
- 3. Ȳ与S²统计独立，

因此，(65.6)给出了$W_1$和$W_2$的联合pdf，其中$-\infty < W_1 < \infty$，$0 < W_2$，以参数$\mu$和$\sigma$以及样本容量$T$为指标。通过将$g(w_1,w_2)$在$W_2$的样本空间上积分，可以得到$W_1$的边际pdf。也就是说，$W_1$的pdf是(65.6)关于$W_2$从0到$\infty$的定积分，而由于这是一个收敛无穷级数的定积分，积分与求和可以互换，从而得到一个收敛无穷级数的定积分之和。在这里，这种互换也是允许的，因为被积分和被求和的函数是可测的，且积分与求和均存在。$^2$

因此，若$f(w_1)$表示$W_1$的pdf，则

$$f(w_1)=\int_{0}^{\infty} g(w_1,w_2)dw_2$$

$$=c\sum_{r=0}^{\infty}\left(\frac{\mu}{\sigma^2/T}w_1-\frac12\right)^r \frac1{r!}\int_{0}^{\infty} w_2^{r+\frac{T-1}{2}} e^{-\frac1{2\sigma^2/T}w_1^2 w_2^2} dw_2.$$\tag{65.7}

(65.7)最右边的积分为

$$\int_{0}^{\infty} w_2^{r+\frac{T-1}{2}} e^{-\frac1{2\sigma^2/T}w_1^2 w_2^2} dw_2$$

$$=\int_{0}^{\infty}\left(\frac{\sqrt{2}\sigma}{\sqrt{T}w_1}\right)^{r+\frac{T-1}{2}} \frac{\sigma}{\sqrt{T}\sqrt{2}}\frac1{w_1}e^{-v\frac12(r+\frac{T-1}{2})-\frac12}dv$$

$$=\left(\frac{\sqrt{2}\sigma}{\sqrt{T}w_1}\right)^{r+\frac{T-1}{2}} \frac{\sigma}{\sqrt{T}\sqrt{2}}\frac1{w_1}\int_{0}^{\infty} e^{-v\frac12(r+\frac{T-1}{2}-1)}dv,\tag{65.8}$$

而(65.8)最右边的积分可以写为

$$\int_{0}^{\infty} e^{-v} v^{\frac{2r+T+1}{4}-1} dv = \Gamma\left(\frac{2r+T+1}{4}\right).$$

为了强调(65.8)是$w_1^2$的函数，可以将其写为

$$\left(\frac{\sqrt{2}\sigma}{\sqrt{T}}\right)^{r+\frac{T-1}{2}} \frac{\sigma}{\sqrt{2}\sqrt{T}}\left(\frac1{w_1^2}\right)^{\frac{2r+T+1}{4}} \Gamma\left(\frac{2r+T+1}{4}\right).\tag{65.8a}$$

将(65.8)与(65.7)结合，W1的pdf为

f(w1)=c sigma/(sqrt(2) sqrt(T)) (sqrt(2) sigma / sqrt(T))^{(T-1)/2} sum_{r=0}^{infty} ( mu/(sigma^2/T) w1 - 1/2 )^r * 1/r! (sqrt(2) sigma / sqrt(T))^r Gamma((2r+T+1)/4) (1/w1^2)^{(2r+T+1)/4}, -infty < w1 < infty. (65.9)

现在从W1变换到U = (T - 1)W1/sigma^2，因为U = Ybar / S^2，而我们要寻求的正是U的分布。由(65.9)，在合并同类项并化简后，U的pdf为，即

f(u)=c1 sum_{r=0}^{infty} Gamma((2r+T+1)/4) 1/r! ( 2 mu T u - (T-1) / (sqrt(2T) sigma) )^r (1/u^2)^{(2r+T+1)/4}, -infty < u < infty. (65.10)

其中

c1 = e^{-T mu^2 / (2 sigma^2)} / [ sqrt(pi) 2^{(T+3)/4} ( sigma sqrt(T)/(T-1) )^{(T-1)/2} Gamma((T-1)/2) ] > 0,

以及参数$-\infty < \mu < \infty$，$\sigma > 0$和样本容量$T > 1$。

因此，(65.10)用T、μ和σ给出了统计量U = Ybar / S^2的精确抽样分布。也就是说，(65.10)给出了我们感兴趣的统计量的精确pdf，其参数为T、μ和σ。我们可以定义U的一个函数，例如U' = 2 sqrt(T) sigma U/(T - 1)，当σ未知时它不是一个统计量，但其pdf由T和比值mu sqrt(T)/sigma参数化。这等价于求V1 = sqrt(T) Z1/sigma与V2 = Z2/2之比的pdf，而不是Z1/Z2的pdf。然而，我们实际上感兴趣的是U的另一个不同函数的pdf，即beta_hat_ML。事实上，给定U = Ybar / S^2的精确抽样分布，由(65.10)，可以很容易求出beta_hat_ML = Ybar / S^2 + 1/2的精确抽样分布。不过，考虑Brown和Gibbons（1985）所考虑的对数正态假设下β的一致最小方差无偏（MVU）估计量是很有意义的。首先，我们将给出……的另一种表示。

