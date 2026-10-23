

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_216_0.png)

*图 7.10：来自5维对称狄利克雷分布在不同的参数值下的样本。(a) $\tilde{\alpha} = (0.1, \dots, 0.1)$。这会产生非常稀疏的分布，其中有许多0。(b) $\tilde{\alpha} = (1, \dots, 1)$。这会得到更均匀（且稠密）的分布。由 dirichlet_samples_plot.py 生成。*

狄利克雷分布的 pdf 定义如下：

$\mathrm{Dir}(\boldsymbol{\theta} \mid \tilde{\boldsymbol{\alpha}}) \triangleq \frac{1}{B(\tilde{\boldsymbol{\alpha}})} \prod_{k=1}^{K} \theta_k^{\tilde{\alpha}_k -1} \mathbb{I}(\boldsymbol{\theta} \in S_K) \tag{7.47}$

其中 $B(\tilde{\boldsymbol{\alpha}})$ 是多元贝塔函数，

$B(\tilde{\boldsymbol{\alpha}}) \triangleq \frac{\prod_{k=1}^{K} \Gamma(\tilde{\alpha}_k)}{\Gamma(\sum_{k=1}^{K} \tilde{\alpha}_k)} \tag{7.48}$

图 7.9 展示了当 $K = 3$ 时狄利克雷分布的一些图形。我们看到，$\tilde{\alpha}_0 = \sum_k \tilde{\alpha}_k$ 控制分布的强度（即分布有多尖锐），而 $\tilde{\alpha}_k$ 控制峰值出现的位置。例如，$\mathrm{Dir}(1,1,1)$ 是均匀分布，$\mathrm{Dir}(2,2,2)$ 是以 $(1/3,1/3,1/3)$ 为中心的宽分布，$\mathrm{Dir}(20,20,20)$ 是以 $(1/3,1/3,1/3)$ 为中心的窄分布。$\mathrm{Dir}(3,3,20)$ 是一个非对称分布，其密度更多地集中在其中一个角上。如果对所有 $k$ 都有 $\tilde{\alpha}_k < 1$，我们会在单纯形的各个角得到“尖峰”。当 $\tilde{\alpha}_k < 1$ 时，来自该分布的样本将是稀疏的，如图 7.10 所示。

### 7.2.2.3 后验

我们可以将多项式似然与狄利克雷先验结合来计算后验，如下所示：

$p(\boldsymbol{\theta} \mid \mathcal{D}) \propto p(\mathcal{D} \mid \boldsymbol{\theta}) \mathrm{Dir}(\boldsymbol{\theta} \mid \tilde{\boldsymbol{\alpha}}) \tag{7.49}$
$= \left[ \prod_k \theta_k^{N_k} \right] \left[ \prod_k \theta_k^{\tilde{\alpha}_k -1} \right] \tag{7.50}$
$= \mathrm{Dir}(\boldsymbol{\theta} \mid \tilde{\alpha}_1 + N_1, \dots, \tilde{\alpha}_K + N_K) \tag{7.51}$
$= \mathrm{Dir}(\boldsymbol{\theta} \mid \tilde{\boldsymbol{\alpha}}) \tag{7.52}$

### 7.2.2.5 边际似然

按照第 7.2.1.5 节的相同推理，可以证明狄利克雷-类别模型的边际似然为

$p(\mathcal{D}) = \frac{B(N + \boldsymbol{\alpha})}{B(\boldsymbol{\alpha})}$ \tag{7.60}

其中

$B(\boldsymbol{\alpha}) = \frac{\prod_{k=1}^K \Gamma(\alpha_k)}{\Gamma(\sum_k \alpha_k)}$ \tag{7.61}

因此，我们可以将上述结果改写成如下形式，这也是文献中通常呈现的形式：

$p(\mathcal{D}) = \frac{\Gamma(\sum_k \alpha_k)}{\Gamma(N + \sum_k \alpha_k)} \prod_k \frac{\Gamma(N_k + \alpha_k)}{\Gamma(\alpha_k)}$ \tag{7.62}

## 7.2.3 高斯-高斯模型

在本节中，我们推导一元高斯分布的后验 $p(\mu, \sigma^2|\mathcal{D})$。为简单起见，我们分三步来讨论：仅推断 $\mu$、仅推断 $\sigma^2$，然后同时推断两者。多元情形参见第 7.2.4 节。

### 7.2.3.1 给定 $\sigma^2$ 时 $\mu$ 的后验

如果 $\sigma^2$ 是已知常数，那么 $\mu$ 的似然具有如下形式

$p(\mathcal{D}|\mu) \propto \exp\left( - \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - \mu)^2 \right)$ \tag{7.63}

可以证明共轭先验是另一个高斯分布 $\mathcal{N}(\mu| \tilde{m}, \tilde{\tau}^2)$。应用针对高斯分布的贝叶斯法则（式 (3.102)），我们发现相应的后验为

$p(\mu|\mathcal{D}, \sigma^2) = \mathcal{N}(\mu| \hat{m}, \hat{\tau}^2)$ \tag{7.64}

$\hat{\tau}^2 = \frac{1}{ N/\sigma^2 + 1/\tilde{\tau}^2 } = \frac{\sigma^2 \tilde{\tau}^2}{ N \tilde{\tau}^2 + \sigma^2 }$ \tag{7.65}

$\hat{m} = \hat{\tau}^2 \left( \frac{\tilde{m}}{\tilde{\tau}^2} + \frac{N\bar{y}}{\sigma^2} \right) = \frac{\sigma^2}{ N \tilde{\tau}^2 + \sigma^2 } \tilde{m} + \frac{N \tilde{\tau}^2}{ N \tilde{\tau}^2 + \sigma^2 } \bar{y}$ \tag{7.66}

其中 $\bar{y} \doteq \frac{1}{N} \sum_{n=1}^N y_n$ 是经验均值。

如果我们用精度参数来表述，这一结果就更容易理解；精度参数正好是方差的倒数。具体来说，令 $\lambda = 1/\sigma^2$ 表示观测精度，$\tilde{\lambda} = 1/ \tilde{\tau}^2$ 表示先验的精度。于是我们可以将后验改写如下：

$p(\mu\mid\mathcal{D},\lambda)=\mathcal{N}(\mu\mid\hat{m},\hat{\lambda}^{-1})$

$\hat{\lambda}=\tilde{\lambda}+N\lambda$

$\hat{m}=\frac{N\lambda\bar{y}+\tilde{\lambda}\tilde{m}}{\hat{\lambda}}=\frac{N\lambda}{N\lambda+\tilde{\lambda}}\bar{y}+\frac{\tilde{\lambda}}{N\lambda+\tilde{\lambda}}\tilde{m}$

这些方程相当直观：后验精度 $\hat{\lambda}$ 等于先验精度 $\tilde{\lambda}$ 加上 $N$ 倍的观测精度 $\lambda$。此外，后验均值 $\hat{m}$ 是经验均值 $\bar{y}$ 与先验均值 $\tilde{m}$ 的凸组合。这清楚地表明后验均值是经验均值与先验之间的一种折中。如果先验相对于信号强度较弱（$\tilde{\lambda}$ 相对于 $\lambda$ 较小），我们会把更多权重放在经验均值上。如果先验相对于信号强度较强（$\tilde{\lambda}$ 相对于 $\lambda$ 较大），我们会把更多权重放在先验上。如图 7.11 所示。还要注意，后验均值是用 $N\lambda\bar{x}$ 表示的，因此拥有 $N$ 个精度各为 $\lambda$ 的测量值，等价于拥有一个取值为 $\bar{x}$、精度为 $N\lambda$ 的测量值。

为了进一步理解这些方程，考虑观测到单个数据点 $y$ 之后的后验（即 $N=1$）。此时后验均值可以写成以下几种等价形式：

$\hat{m}=\frac{\tilde{\lambda}}{\hat{\lambda}}\tilde{m}+\frac{\lambda}{\hat{\lambda}}y$

$=\tilde{m}+\frac{\lambda}{\hat{\lambda}}(y-\tilde{m})$

$=y-\frac{\tilde{\lambda}}{\hat{\lambda}}(y-\tilde{m})$

第一个方程是先验均值与数据的凸组合。第二个方程是先验均值向数据 $y$ 调整。第三个方程是数据向先验均值调整；这被称为**收缩**估计。如果我们定义权重 $w=\tilde{\lambda}/\hat{\lambda}$，这一点就更容易看到。于是我们有

$\hat{m}=y-w(y-\tilde{m})=(1-w)y+w\tilde{m}$

注意，对于高斯分布，后验均值与后验众数是相同的。因此，我们可以用上述方程进行 MAP 估计。简单例子见习题 4.2。

### 7.2.3.2 给定 $\mu$ 时 $\sigma^2$ 的后验

如果 $\mu$ 是已知常数，$\sigma^2$ 的似然具有如下形式

$p(\mathcal{D}\mid\sigma^2)\propto(\sigma^2)^{-N/2}\exp\left(-\frac{1}{2\sigma^2}\sum_{n=1}^{N}(y_n-\mu)^2\right)$

此时我们不能再忽略前面的 $1/(\sigma^2)$ 项。标准共轭先验是逆伽马分布（第 3.4.5 节），由下式给出：

$\mathrm{IG}(\sigma^2\mid\tilde{a},\tilde{b})=\frac{\tilde{b}^{\tilde{a}}}{\Gamma(\tilde{a})}(\sigma^2)^{-(\tilde{a}+1)}\exp\left(-\frac{\tilde{b}}{\sigma^2}\right)$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_220_0.png)

图 7.11：在 $\sigma^2$ 已知时推断一元高斯的均值。(a) 使用强先验 $p(\mu) = \mathcal{N}(\mu|0,1)$。(b) 使用弱先验 $p(\mu) = \mathcal{N}(\mu|0,5)$。由 gaussInferParamsMean1d.m 生成。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_220_1.png)

图 7.12：从无信息先验出发对 $\sigma^2$ 的后验进行序贯更新。数据由已知均值 $\mu = 5$、未知方差 $\sigma^2 = 10$ 的高斯分布生成。由 gauss_seg_update_sigma_1d.py 生成。

将似然与先验相乘，我们看到后验也服从 IG 分布：

$p(\sigma^2|\mu, \mathcal{D}) = \mathrm{IG}(\sigma^2 | \hat{a}, \hat{b})$ \tag{7.76}
$\hat{a} = \tilde{a} + N/2$ \tag{7.77}
$\hat{b} = \tilde{b} + \frac{1}{2} \sum_{n=1}^N (y_n - \mu)^2$ \tag{7.78}

示意见图 7.12。

使用 $\mathrm{IG}(\tilde{a}, \tilde{b})$ 分布时有一点小小的不便：先验的强度同时体现在 $\tilde{a}$ 和 $\tilde{b}$ 中。因此，在贝叶斯统计学文献中，通常使用 IG 分布的另一种参数化形式，即（缩放）逆卡方分布：

$\chi^{-2}(\sigma^2 | \tilde{\nu}, \tilde{\tau}^2) = \mathrm{IG}(\sigma^2 | \tilde{\nu}/2, \tilde{\nu} \tilde{\tau}^2/2) \propto (\sigma^2)^{-\tilde{\nu}/2 -1} \exp(- \tilde{\nu} \tilde{\tau}^2 / (2\sigma^2))$ \tag{7.79}

这里 $\tilde{\nu}$（称为自由度或 dof 参数）控制先验的强度，而 $\tilde{\tau}^2$ 编码先验均值。使用这一先验时，后验变为

$$p(\sigma^2|\mathcal{D},\mu)=\chi^{-2}(\sigma^2|\hat{\nu},\hat{\tau}^2)\tag{7.80}$$
$$\hat{\nu}=\tilde{\nu}+N\tag{7.81}$$
$$\hat{\tau}^2=\frac{\tilde{\nu}\tilde{\tau}^2+\sum_{n=1}^N(y_n-\mu)^2}{\hat{\nu}}\tag{7.82}$$

我们看到后验自由度 $\hat{\nu}$ 等于先验自由度 $\tilde{\nu}$ 加上 $N$，后验平方和 $\hat{\nu}\hat{\tau}^2$ 等于先验平方和 $\tilde{\nu}\tilde{\tau}^2$ 加上数据平方和。

### 7.2.3.3 $\mu$ 和 $\sigma^2$ 的后验：共轭先验

现在假设我们想要同时推断均值和方差。相应的共轭先验是**正态-逆伽马**分布：

$$\text{NIG}(\mu,\sigma^2|\tilde{m},\tilde{\kappa},\tilde{a},\tilde{b})\triangleq\mathcal{N}(\mu|\tilde{m},\sigma^2/\tilde{\kappa})\,\text{IG}(\sigma^2|\tilde{a},\tilde{b})\tag{7.83}$$

不过，通常会对它使用一种重新参数化形式，称为**正态-逆卡方**或 **NIX** 分布 [Gel+14, p67]，其定义为

$$NI\chi^2(\mu,\sigma^2|\tilde{m},\tilde{\kappa},\tilde{\nu},\tilde{\tau}^2)\triangleq\mathcal{N}(\mu|\tilde{m},\sigma^2/\tilde{\kappa})\,\chi^{-2}(\sigma^2|\tilde{\nu},\tilde{\tau}^2)\tag{7.84}$$
$$\propto\left(\frac{1}{\sigma^2}\right)^{(\tilde{\nu}+3)/2}\exp\left(-\frac{\tilde{\nu}\tilde{\tau}^2+\tilde{\kappa}(\mu-\tilde{m})^2}{2\sigma^2}\right)\tag{7.85}$$

一些图形见图 7.13。沿着 $\mu$ 轴，分布形状类似高斯分布；沿着 $\sigma^2$ 轴，分布形状类似 $\chi^{-2}$ 分布；联合密度的等高线呈“压扁的鸡蛋”状。有趣的是，我们看到 $\mu$ 的等高线在 $\sigma^2$ 较小时更尖锐，这很合理，因为如果数据方差较低，我们就能更可靠地估计其均值。

可以证明（基于第 7.2.4.4 节）后验为

$$p(\mu,\sigma^2|\mathcal{D})=NI\chi^2(\mu,\sigma^2|\hat{m},\hat{\kappa},\hat{\nu},\hat{\tau}^2)\tag{7.86}$$
$$\hat{m}=\frac{\tilde{\kappa}\tilde{m}+N\bar{x}}{\hat{\kappa}}\tag{7.87}$$
$$\hat{\kappa}=\tilde{\kappa}+N\tag{7.88}$$
$$\hat{\nu}=\tilde{\nu}+N\tag{7.89}$$
$$\hat{\nu}\hat{\tau}^2=\tilde{\nu}\tilde{\tau}^2+\sum_{n=1}^N(y_n-\bar{y})^2+\frac{N\tilde{\kappa}}{\tilde{\kappa}+N}(\tilde{m}-\bar{y})^2\tag{7.90}$$

其解释如下。对于 $\mu$，后验均值 $\hat{m}$ 是先验均值 $\tilde{m}$ 与 MLE $\bar{x}$ 的凸组合；该后验的强度 $\hat{\kappa}$ 等于先验强度 $\tilde{\kappa}$ 加上数据点数量 $N$。对于 $\sigma^2$，我们改用平方和来处理：后验平方和 $\hat{\nu}\hat{\tau}^2$ 等于先验平方和 $\tilde{\nu}\tilde{\tau}^2$ 加上数据平方和 $\sum_{n=1}^N(y_n-\bar{y})^2$，再加上一个由于先验均值 $\tilde{m}$ 与 MLE $\bar{y}$ 之间的差异而产生的项。该后验的强度 $\hat{\nu}$ 等于先验强度 $\tilde{\nu}$ 加上数据点数量 $N$；

