

我们可以引入一个随机变量 $Z'$，它与 $Z$ 具有相同的边缘分布，但与 $j$ 独立：

$$p(Z')=\frac{1}{N}\sum_{j=1}^{N}p_j(Z').$$

现在，考虑任意且可能随机的估计量 $\hat{\theta}=\mathcal{A}(Z)$。令 $\hat{\theta}'=\mathcal{A}(Z')$。根据 KL 散度的数据处理不等式（见定理 B.4），以 $(j,Z)$ 为输入、以二元输出 $h(j,Z)=\mathbb{1}(Q(\hat{\theta},D_j)<\epsilon)$（其中 $\mathbb{1}(\cdot)$ 为示性函数）可以得到

$$\mathrm{KL}\bigl(\mathbb{1}(Q(\hat{\theta},D_j)<\epsilon)\,\|\,\mathbb{1}(Q(\hat{\theta}',D_j)<\epsilon)\bigr)\leq \mathrm{KL}((j,Z)\,\|\,(j,Z'))=I(j,Z).$$

现在令 $q=\Pr(Q(\hat{\theta},D_j)<\epsilon)$，$q'=\Pr(Q(\hat{\theta}',D_j)<\epsilon)$，则我们的不等式可以改写为

$$\mathrm{KL}(q\|q')=q\ln\frac{q}{q'}+(1-q)\ln\frac{1-q}{1-q'}\leq I(j,Z).$$

由于 $\hat{\theta}'$ 与 $j$ 独立，并且

$$\left|\{j:Q(\hat{\theta}',D_j)<\epsilon\}\right|\leq m$$

对每个 $\hat{\theta}'$ 都成立，我们得到

$$q'\leq m/N.$$

若 $q\leq m/N$，我们就证明了所需的不等式。否则，因为 $\mathrm{KL}(q\|q')$ 作为 $q'$ 的函数在 $[0,q]$ 上递减，我们有

$$q\ln\frac{q}{m/N}+(1-q)\ln\frac{1-q}{1-m/N}\leq I(j,Z).$$

由于 $q\ln q+(1-q)\ln(1-q)\geq-\ln 2$，我们得到

$$-\ln 2+q\ln\frac{N}{m}+(1-q)\ln\frac{N}{N-m}\leq I(j,Z).$$

这意味着

$$q\leq\frac{I(j,Z)+\ln 2}{\ln(N/m)}.$$

因此我们得到所需的界。 $\square$

### 示例 12.12
在定理 12.11 中，若取 $\Theta=\{1,\ldots,N\}$，$Q(\theta,D_j)=\mathbb{1}(\theta\neq j)$，且 $\epsilon=1$，则 $m=1$。注意 $1/N\leq\ln 2/\ln(N)$，我们得到以下结果

$$\frac{1}{N}\sum_{j=1}^{N}\Pr_{Z\sim D_j}(\mathcal{A}(Z)=j)\leq\frac{I(j,Z)+\ln 2}{\ln N}.$$

这就蕴含了定理 12.10 的 Fano 不等式。

下面的示例给出了 $m > 1$ 的一个应用。

### 示例 12.13
在定理 12.11 中，若在 $N > 2$ 时取 $\Theta = [1, N]$，$Q(\theta, \mathcal{D}_j) = |\theta - j|$，且 $\epsilon = 1$，则 $m = 2$。注意 $2/N \le \ln 2 / \ln(N/2)$，我们得到以下结果：

$\frac{1}{N} \sum_{j=1}^{N} \Pr_{Z \sim \mathcal{D}_j} (|\mathcal{A}(Z) - j| < 1) \le \frac{I(j, Z) + \ln 2}{\ln(N/2)}$。

下面的结果表明，如果分布 $\{\mathcal{D}_j\}$ 彼此接近，那么定理 12.11 中的互信息 $I(j, Z)$ 很小。

### 引理 12.14
*定理 12.11 中的互信息 $I(j, Z)$ 满足不等式*

$I(j, Z) \le \frac{1}{N^2} \sum_{j=1}^{N} \sum_{k=1}^{N} \mathrm{KL}(\mathcal{D}_j||\mathcal{D}_k) \le \sup_{j,k} \mathrm{KL}(\mathcal{D}_j||\mathcal{D}_k)$。

证明
我们有

$I(j, Z) = \frac{1}{N} \sum_{j=1}^{N} \mathbb{E}_{Z \sim \mathcal{D}_j} \ln \frac{p_{\mathcal{D}_j}(Z)}{\frac{1}{N} \sum_{k=1}^{N} p_{\mathcal{D}_k}(Z)}$

$\le \frac{1}{N^2} \sum_{j=1}^{N} \sum_{k=1}^{N} \mathbb{E}_{Z \sim \mathcal{D}_j} \ln \frac{p_{\mathcal{D}_j}(Z)}{p_{\mathcal{D}_k}(Z)}$,

其中该不等式使用了 Jensen 不等式和 $-\ln z$ 的凸性。

下面的极小极大风险下界是广义 Fano 不等式直接应用于 KL 散度的乘积分布得到的。我们将其证明留作练习。

### 定理 12.15
*考虑一个分布族 $\mathcal{P}$，它包含一个有限子集 $\{\mathcal{D}_1, \dots, \mathcal{D}_N\}$。令 $Q$ 为 $\Theta \times \mathcal{P}$ 上的损失函数，且*

下面的示例说明如何使用该结果。

### 示例 12.16
考虑 $d$ 维高斯均值估计问题，其目标是基于观测 $Z_1,\dots,Z_n \sim \mathcal{D}=N(\theta,I)$，估计具有未知均值 $\theta \in \mathbb{R}^d$ 且满足 $\|\theta\|_2 \le 1$ 的高斯分布 $N(\theta,I)$。令 $\hat\theta$ 为估计均值，并定义度量

$Q(\hat\theta,\mathcal{D}) = Q(\hat\theta,\theta) = \|\hat\theta - \theta\|_2.$

于是，对于某个小的 $\epsilon > 0$，我们关心需要多少样本 $n$ 才能得到误差不超过 $0.5\epsilon$ 的估计。

为了应用定理 12.15，我们考虑球 $B(4\epsilon)=\{\theta:\|\theta\|_2\le4\epsilon\}$。由定理 5.3 可知，在 $B(4\epsilon)$ 中存在 $N=((4\epsilon)/(2\epsilon))^d=2^d$ 个中心 $\{\theta_j:j=1,\dots,N\}$，使得当 $j\neq k$ 时 $\|\theta_j-\theta_k\|_2>2\epsilon$。由于 $\|\hat\theta-\theta_j\|_2+\|\hat\theta-\theta_k\|_2\ge\|\theta_j-\theta_k\|_2>2\epsilon$，我们得到

$|\{k: Q(\theta,\theta_k)<\epsilon\}| \le 1.$

令 $p_j=N(\theta_j,I)$。这意味着对所有 $\theta_j,\theta_k\in B(4\epsilon)$，有

$\mathrm{KL}(p_j\|p_k)=\frac12\|\theta_j-\theta_k\|_2^2\le32\epsilon^2.$

定理 12.15 的条件在以下情况下成立：

$\ln(N)=\ln(2^d)\ge\ln4+64n\epsilon^2\ge\ln4+2n\sup_{j,k}\mathrm{KL}(p_j\|p_k).$

这意味着，如果

$n\le\frac{(d-2)\ln2}{64\epsilon^2},$

那么对所有均值估计量 $\hat\theta$，存在 $\theta_j\in B(4\epsilon)$，使得对于来自 $p_j$ 的 $n$ 个独立同分布样本，

$\mathbb{E}\|\hat\theta-\theta_j\|_2\ge0.5\epsilon.$

## 12.4 最小二乘回归的极小极大分析
对于示例 12.6 中的最小二乘回归问题，我们考虑一个函数类 $\mathcal{F}$，它包含最优预测规则 $f_{\mathcal{D}}(X)=\mathbb{E}[Y|X]$，并且

$Q_{\mathrm{LS}}(f,\mathcal{D})=\mathbb{E}_{X\sim\mathcal{D}}(f(X)-f_{\mathcal{D}}(X))^2.$

下面的结果是定理 12.15 的直接推论。

### 定理 12.17
考虑回归模型，其中 $X\sim\mathcal{D}_X$ 且 $\mathcal{D}_X$ 已知，并且

$Y = f_{\mathcal{D}}(X) + \epsilon,$

其中 $\epsilon$ 是零均值噪声，可能依赖于 $f_{\mathcal{D}}(\cdot)\in\mathcal{F}$。假设存在 $\sigma>0$，使得

$\mathbb{E}_{X\sim\mathcal{D}_X}(f(X)-f'(X))^2 \ge 2\sigma^2 KL(\mathcal{D}_f||\mathcal{D}_{f'}),$

其中 $\mathcal{D}_f$ 是当 $f_{\mathcal{D}}=f$ 时 $(X,Y)$ 的分布。若 $\mathcal{F}$ 包含 $N$ 个函数 $f_1,\dots,f_N$，使得

$\ln N \ge \ln 4 + n\sigma^{-2} \sup_{j,k} \mathbb{E}_{X\sim\mathcal{D}}(f_j(X)-f_k(X))^2,$

则

$r_n(\mathcal{P},Q_{LS}) \ge 0.125 \inf_{j\neq k} \mathbb{E}_{X\sim\mathcal{D}_X}(f_j(X)-f_k(X))^2.$

证明 定义 $Q(f,f') = \mathbb{E}_{X\sim\mathcal{D}}(f(X)-f'(X))^2$。注意，对于每个 $f \in \mathcal{F}$，我们关联一个 $\mathcal{D}_f \in \mathcal{P}=\{\mathcal{D}_f:f\in\mathcal{F}\}$。我们还令 $\epsilon = 0.25\min_{j\neq k}Q(f_j,f_k)$，并且可以验证对所有 $j\neq k$，

$\max(Q(f,f_j),Q(f,f_k)) \ge (Q(f,f_j)+Q(f,f_k))/2 \ge Q(f_j,f_k)/4 \ge \epsilon.$

这意味着我们可以取 $m=1$，并作为定理 12.15 的直接推论得到该定理。

下面的结果表明，定理 12.17 的条件对高斯噪声成立。

### 命题 12.18
*考虑 $\mathcal{D}_f(X,Y)$，使得对所有 $f \in \mathcal{F}$，$X \sim \mathcal{D}_X$ 都相同，且对某个常数 $\sigma>0$ 有 $Y \sim N(f(X),\sigma^2)$。则*

$\mathbb{E}_{X\sim\mathcal{D}_X}(f(X)-f'(X))^2 = 2\sigma^2 KL(\mathcal{D}_f||\mathcal{D}_{f'}).$

证明 我们考虑与每个 $f\in\mathcal{F}$ 相关联的关于 $Z=(X,Y)$ 的分布 $\mathcal{D}$，其密度定义为

$p_{\mathcal{D}}(Z)=p_{\mathcal{D}_X}(X)\,p_{N(0,1)}((Y-f(X))/\sigma),$

其中 $p_{\mathcal{D}_X}(X)$ 是 $X\sim\mathcal{D}_X$ 的密度，$p_{N(0,1)}$ 是标准正态分布的密度。使用这一记号，我们有

$KL(\mathcal{D}_{\hat f}||\mathcal{D}_f)=\frac{\mathbb{E}_X(\hat f(X)-f(X))^2}{2\sigma^2}.$

这就证明了所需结果。

对于其他噪声模型，例如伯努利噪声（其中 $Y\in\{0,1\}$），也可以得到类似的结果。

### 命题 12.19
*假设 $Y\in\{0,1\}$，使得*

$\mathbb{E}[Y|X]=f(X)$

*对某个 $f\in\mathcal{F}$ 成立，并令 $\mathcal{D}_f(Z)$ 为 $Z=(X,Y)$ 的分布。若存在 $c\in(0,0.5)$，且对所有 $f\in\mathcal{F}$ 和所有满足 $f(X)\in[c,1-c]$ 的 $X$，则存在 $\sigma>0$，使得对所有 $f,f'\in\mathcal{F}$，*

$\mathbb{E}_{X\sim\mathcal{D}_X}(f(X)-f'(X))^2 \ge 2\sigma^2 KL(\mathcal{D}_f||\mathcal{D}_{f'}).$

