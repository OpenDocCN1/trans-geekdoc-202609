
## 附录 A 凸分析基础

我们非正式地回顾本书中使用的一些凸函数的基本概念。为可读性考虑，我们避免了为数学严谨性可能需要的非本质技术条件。凸分析更正式、更严谨的处理可参见 (Rockafellar, 2015)。

### A.1 定义

**定义 A.1** 向量空间中的集合 $\Omega$ 是凸集，如果对所有 $w,w'\in\Omega$ 和 $\alpha\in[0,1]$，$\alpha w+(1-\alpha)w'\in\Omega$。实值函数 $\phi(w)$ 在凸集 $\Omega$ 上是凸函数，如果其上镜图 $\{(w,t)\in\Omega\times\mathbb{R}: t\ge\phi(w)\}$ 是凸集。

我们也说函数 $\phi(w)$ 是凹的，如果 $-\phi(w)$ 是凸的。

**命题 A.2** *函数 $\phi(w)$ 在 $\Omega$ 上是凸的当且仅当对所有 $\alpha\in(0,1)$ 和 $w,w'\in\Omega$,*
$$\phi(\alpha w+(1-\alpha)w')\le\alpha\phi(w)+(1-\alpha)\phi(w').$$

**命题 A.3** *函数 $\phi(w)$ 在 $\Omega$ 上是凸的，如果对所有 $w\in\Omega$，存在一个向量 $g$ 使得对所有 $w'\in\Omega$,*
$$\phi(w')\ge\phi(w)+g^\top(w'-w).$$
*这里 $g$ 在凸分析中被称为次梯度，可能不唯一。*

*如果凸函数 $\phi(w)$ 在 $\Omega$ 的内点 $w$ 处可微，则 $g=\nabla\phi(w)$ 是唯一的。*

为避免混淆，本书中我们将用 $\nabla\phi(w)$ 表示凸函数 $\phi(w)$ 的任意次梯度。非唯一次梯度的一个例子是给定的单变量凸函数 $\phi(w)=|w|$，对于该函数，任意 $g\in[-1,1]$ 在 $w=0$ 处都是次梯度。

**定义 A.4** 给定 $\lambda>0$，函数 $\phi(w)$ 在 $w$ 上是 $\lambda$-强凸的，如果对所有 $w,w'\in\Omega$，
$$\phi(w')\ge\phi(w)+\nabla\phi(w)^\top(w'-w)+\frac{\lambda}{2}\|w-w'\|_2^2.$$

强凸函数可能不可微。一个例子是单变量函数 $\phi(w)=|w|+\frac12 w^2$，它是 $\lambda=1$ 强凸的，但在 $w=0$ 处不可微。下面的定义在理论分析中经常使用。它甚至可以应用于非凸函数。

**定义 A.5** 函数 $\phi(w)$（不一定是凸的）在 $\Omega$ 上是 $L$-光滑的，如果它可微且对所有 $w,w'\in\Omega$，
$$\|\nabla\phi(w')-\nabla\phi(w)\|_2\le L\|w-w'\|_2.$$
我们说 $\phi(w)$ 是 $G$-Lipschitz 的，如果对所有 $w\in\Omega$，
$$\|\nabla\phi(w)\|_2\le G.$$

**命题 A.6** 如果 $\phi(w)$ 是 $L$-光滑的，则对任意 $w,w'\in\Omega$，
$$\phi(w')\le\phi(w)+\nabla\phi(w)^\top(w'-w)+\frac{L}{2}\|w-w'\|_2^2,$$
且 $\|\nabla^2\phi(w)\|_2\le L$。如果 $\phi$ 是 $G$-Lipschitz 的，则对任意 $w,w'\in\Omega$，
$$|\phi(w)-\phi(w')|\le G\|w-w'\|_2.$$

### A.2 基本性质

我们列出一些对本书分析有用的凸函数结果。

**命题 A.7** 如果 $\phi(w)$ 在 $\mathbb{R}^d$ 上是 $L$-光滑的，则对所有 $w,w'\in\mathbb{R}^d$，
$$\|\nabla\phi(w')-\nabla\phi(w)\|_2^2\le 2L\left[\phi(w)-\phi(w')-\nabla\phi(w')^\top(w-w')\right].$$

*证明* 设
$$\widetilde{\phi}(w)=\phi(w)-\phi(w')-\nabla\phi(w')^\top(w-w').$$
则 $\widetilde{\phi}(w)$ 是 $L$-光滑的，且由于凸性 $\widetilde{\phi}(w)\ge0$。设 $\eta=1/L$，则
$$0\le\widetilde{\phi}(w-\eta\nabla\widetilde{\phi}(w))$$
$$\le\widetilde{\phi}(w)-\eta\nabla\widetilde{\phi}(w)^\top\nabla\widetilde{\phi}(w)+\frac{\eta^2L}{2}\|\nabla\widetilde{\phi}(w)\|_2^2$$
$$=\widetilde{\phi}(w)-\frac{1}{2L}\|\nabla\widetilde{\phi}(w)\|_2^2.$$
第二个不等式使用了命题 A.6。这就得到了期望的界。$\square$

**命题 A.8** *如果 $\phi(w)$ 在闭凸集 $\Omega$ 上是凸的且*
$$w_*=\arg\min_{w\in\Omega}\phi(w),$$
*则存在一个次梯度 $\nabla\phi(w_*)$ 使得对所有 $w\in\Omega$,*
$$\nabla\phi(w_*)^\top(w-w_*)\ge0.$$
*此外，如果 $\phi(w)$ 是 $\lambda$-强凸的，且存在实数 $g\ge0$ 使得对所有 $w\in\Omega$,*
$$\nabla\phi(w)^\top(w_*-w)\ge -g\|w-w_*\|_2,$$
*则 $\|w_*-w\|_2\le g/\lambda$。*

*证明* 第一个结果源于凸优化理论 (Boyd and Vandenberghe, 2004; Rockafellar, 2015)，其说明 $w_*$ 是 $\phi(w)$ 在 $\Omega$ 上的极小化点当且仅当存在次梯度 $\nabla\phi(w_*)$ 使得
$$\forall w\in\Omega:\ \nabla\phi(w_*)^\top(w-w_*)\ge0.$$

利用强凸性的定义，我们得到
$$\phi(w_*)\ge\phi(w)+\nabla\phi(w)^\top(w_*-w)+\frac{\lambda}{2}\|w_*-w\|_2^2,$$
$$\phi(w)\ge\phi(w_*)+\nabla\phi(w_*)^\top(w-w_*)+\frac{\lambda}{2}\|w_*-w\|_2^2\ge\phi(w_*)+\frac{\lambda}{2}\|w_*-w\|_2^2.$$

将两个不等式相加，我们得到
$$0\ge\nabla\phi(w)^\top(w_*-w)+\lambda\|w-w_*\|_2^2\ge -g\|w-w_*\|_2+\lambda\|w-w_*\|_2^2.$$

这就得到了第二个界。

我们也在书中经常使用以下结果。

**命题 A.9 (Jensen 不等式)** *假设 $\phi(w)$ 是 $\Omega$ 上的凸函数。考虑 $w_1,\ldots,w_m\in\Omega$，以及非负数 $\alpha_1,\ldots,\alpha_m\in\mathbb{R}$ 使得 $\sum_{i=1}^m\alpha_i=1$。则*
$$\phi\left(\sum_{i=1}^m\alpha_iw_i\right)\le\sum_{i=1}^m\alpha_i\phi(w_i).$$

更一般地，设 $p$ 是 $\Omega$ 上的概率测度，则 $\phi(\mathbb{E}_{w\sim p}w)\le\mathbb{E}_{w\sim p}\phi(w)$。

*证明* 设 $w=\sum_{i=1}^m\alpha_iw_i$。利用凸性，我们知道对每个 $i$，
$$\phi(w_i)\ge\phi(w)+\nabla\phi(w)^\top(w_i-w),$$
其中 $\nabla\phi(w)$ 是 $\phi$ 的次梯度。乘以 $\alpha_i$ 并对 $i$ 求和，我们得到
$$\sum_{i=1}^m\alpha_i\phi(w_i)\ge\phi(w)+\nabla\phi(w)^\top\sum_{i=1}^m\alpha_i(w_i-w)=\phi(w).$$

这就完成了证明。更一般的不等式可以类似地证明。

该结果意味着 hinge loss
$$\phi(w)=\sup_{y}\max[0,b_y-x_y^\top w]$$
在 $\mathbb{R}^d$ 上是凸的，其中 $(x_y,b_y)\in\mathbb{R}^d\times\mathbb{R}$。

**命题 A.15** *设 $\phi(z)$ 是 $\mathbb{R}^q$ 上的凸函数，且 $A$ 是 $q\times d$ 矩阵。则 $\phi(Aw)$ 是 $\mathbb{R}^d$ 上的凸函数。*

**命题 A.16** *如果 $\phi(z)$ 在 $\Omega$ 上是凸的，则 $t\phi(z/t)$ 在 $\{(z,t): z/t\in\Omega,\ t\in\mathbb{R}_+\}$ 上是凸的。*

*证明* 我们有
$$(\alpha t+(1-\alpha)t')\phi\left(\frac{\alpha z+(1-\alpha)z'}{\alpha t+(1-\alpha)t'}\right) = (\alpha t+(1-\alpha)t')\phi\left(\frac{\alpha t(z/t)+(1-\alpha)t'(z'/t')}{\alpha t+(1-\alpha)t'}\right) \le \alpha t\phi(z/t)+(1-\alpha)t'\phi(z'/t').\qquad\text{(Jensen 不等式)}$$

这就证明了 $t\phi(z/t)$ 的凸性。

### A.4 矩阵迹函数

我们也可以直接为对称矩阵构造凸函数。

**定义 A.17** *设 $f(z)$ 是实值函数。对具有分解 $W=U^\top\Lambda U$ 的对称矩阵 $W$，其中 $\Lambda=\operatorname{diag}(\lambda_1,\ldots,\lambda_d)$ 是对角矩阵且 $U$ 是正交矩阵，我们定义*
$$f(W)=U^\top f(\Lambda)U,$$
*其中 $f(\Lambda)=\operatorname{diag}(f(\lambda_1),\ldots,f(\lambda_d))$。*

*如果 $f(z)$ 可微且导数为 $f'(z)$，则不难验证*
$$\left.\frac{d}{dt}\operatorname{trace}(f(W+t\Delta W))\right|_{t=0}=\operatorname{trace}(f'(W)\Delta W).$$

**定理 A.18** *设 $S_{[a,b]}^d$ 是特征值在 $[a,b]$ 中的 $d\times d$ 对称矩阵集合。如果 $f:[a,b]\to\mathbb{R}$ 是凸函数，则*
$$\operatorname{trace}(f(W))$$
*是 $S_{[a,b]}^d$ 上的凸函数。这意味着对 $W,W'\in S_{[a,b]}^d$,*
$$\operatorname{trace}(f(W'))\ge\operatorname{trace}(f(W))+\operatorname{trace}(f'(W)(W'-W)),$$
*其中 $f'(z)$ 是 $f(z)$ 的导数。*

这就证明了第一个期望结果。对于第二个结果，我们注意到
$$D_f(P\parallel Q)=\mathbb{E}_{z\sim Q}\left[f\left(\frac{p(z)}{q(z)}\right)-f(1)-g\left(\frac{p(z)}{q(z)}-1\right)\right],$$
它仅当 $p(z)/q(z)=1$ 几乎处处成立时为零。

下面的结果表明 $f$-散度在 $P$ 和 $Q$ 上是联合凸的。

**命题 B.3** *给定任意 $\alpha\in[0,1]$，概率测度 $P$, $P'$, $Q$, $Q'$，我们有*
$$D_f(\alpha P+(1-\alpha)P'\parallel\alpha Q+(1-\alpha)Q')\le\alpha D_f(P\parallel Q)+(1-\alpha)D_f(P'\parallel Q').$$

*证明* 这是函数 $q f(p/q)$ 在 $(p,q)\in\mathbb{R}_+\times\mathbb{R}_+$ 上关于 $(p,q)$ 联合凸的直接结果 (参见命题 A.16)。

$f$-散度的以下数据处理不等式对于建立统计估计的下界非常有用。

**定理 B.4 (数据处理不等式)** *设 $W$ 和 $Z$ 是 $\Omega$ 上的两个随机变量。设 $h:\Omega\to\Omega'$ 是一个数据处理映射，可以是随机函数。则*
$$D_f(h(W)\parallel h(Z))\le D_f(W\parallel Z).$$

*证明* 设 $W$ 和 $Z$ 分别服从概率测度 $P(W)d\mu$ 和 $Q(Z)d\mu$。设 $W'=h(W)$ 且 $Z'=h(Z)$。设 $P(W,W')$ 和 $Q(Z,Z')$ 是 $[W,W']$ 和 $[Z,Z']$ 的联合分布。根据数据处理的定义，条件分布满足
$$Q(Z'=x'|Z=x)=P(W'=x'|W=x).$$
