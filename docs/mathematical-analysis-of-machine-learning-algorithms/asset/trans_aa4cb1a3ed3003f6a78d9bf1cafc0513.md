
利用这种表示，我们有

$$\hat f(x)=\begin{bmatrix}\langle\hat w,\psi(x,1)\rangle\\ \vdots\\ \langle\hat w,\psi(x,q)\rangle\end{bmatrix}=\sum_{i=1}^{n}\begin{bmatrix}\langle[\psi(X_i,1),\ldots,\psi(X_i,q)]\tilde{\alpha}_i,\psi(x,1)\rangle\\ \vdots\\ \langle[\psi(X_i,1),\ldots,\psi(X_i,q)]\tilde{\alpha}_i,\psi(x,q)\rangle\end{bmatrix}=\sum_{i=1}^{n}k(x,X_i)\tilde{\alpha}_i.$$

并且

$$\langle\hat w,\hat w\rangle=\sum_{i=1}^{n}\left\langle[\psi(X_i,1),\ldots,\psi(X_i,q)]\tilde{\alpha}_i,\sum_{j=1}^{n}[\psi(X_j,1),\ldots,\psi(X_j,q)]\tilde{\alpha}_j\right\rangle=\sum_{i=1}^{n}\sum_{j=1}^{n}\tilde{\alpha}_i^{\mathsf T}K(X_i,X_j)\tilde{\alpha}_j.$$

这意味着 $Q_1(\hat w)=Q_2(\tilde\alpha)$。类似地，存在 $\tilde w$ 使得 $Q_1(\tilde w)=Q_2(\hat\alpha)$。因此 $Q_1(\hat w)=Q_2(\tilde\alpha)\ge Q_2(\hat\alpha)=Q_1(\tilde w)$。这意味着 $\tilde w$ 是 (9.15) 的解，从而证明了该结果。

为了利用 Rademacher 复杂度对向量值函数进行泛化分析，我们可以采用定理 6.28 的以下推广。证明与引理 6.29 相似。

### Theorem 9.30

考虑 $L(p,y)$ 关于 $L_1$-范数是 $\gamma_1$-Lipschitz 的：

$$|L(p,y)-L(p',y)|\le \gamma_1\|p-p'\|_1.$$

考虑

$$\mathcal G=\left\{L([f_1(x),\ldots,f_q(x)],y):f_j(x)\in\mathcal F_j\ (j=1,\ldots,q)\right\},$$

则

$$R(\mathcal G,\mathcal S_n)\le \gamma_1\sum_{j=1}^{q}R(\mathcal F_j,\mathcal S_n).$$

对于向量核方法，我们可以考虑使用特征表示的硬约束版本：

$$\hat w=\underset{w\in\mathcal H}{\arg\min}\ \frac{1}{n}\sum_{i=1}^{n}L(\langle w,\psi(X_i,\cdot)\rangle,Y_i)\quad\text{subject to }\langle w,w\rangle\le A^2. \tag{9.17}$$

我们有以下 Rademacher 复杂度的估计。

### Lemma 9.31

设

$$\mathcal G=\left\{L(\langle w,\psi(x,\cdot)\rangle,y):\langle w,w\rangle\le A^2\right\},$$

则在定理 9.30 中定义的 $\gamma_1$ 下，

$$R(\mathcal{G},\mathcal{S}_n) \le \frac{\gamma_1 A}{n}\sum_{j=1}^{q}\sqrt{\sum_{i=1}^{n} k_{j,j}(X_i,X_i)}$$

并且

$$R_n(\mathcal{G},\mathcal{D}) \le \gamma_1 A\sum_{j=1}^{q}\sqrt{\frac{1}{n}\mathbb{E}_{\mathcal{D}} k_{j,j}(X,X)}.$$

**证明.** 我们可以设 $\mathcal{F}_j=\{\langle w,\psi(x,j)\rangle\mid\langle w,w\rangle\le A^2\}$。由定理 9.20 可得

$$R(\mathcal{F}_j,\mathcal{S}_n)\le \frac{A}{n}\sqrt{\sum_{i=1}^{n} k_{j,j}(X_i,X_i)}.$$

并且

$$R_n(\mathcal{F}_j,\mathcal{D})\le A\sqrt{\frac{1}{n}\mathbb{E}_{\mathcal{D}}k_{j,j}(X,X)}.$$

现在我们可以应用定理 9.30 得到期望的上界。$\square$

如果 $k_{j,j}(x,x)\le B^2$ 对所有 $j$ 和 $x$ 成立，则推论 9.31 给出上界

$$R(\mathcal{G},\mathcal{S}_n)\le \frac{\gamma_1 qAB}{\sqrt{n}}.$$

该上界的一个缺点是 Rademacher 复杂度在 $q$ 上是线性的，当 $q$ 很大时通常是次优的。对于此类问题，需要更精细的 Rademacher 复杂度估计。

### Example 9.32

考虑 $q$ 类分类问题的结构化 SVM 损失函数 (Tsochantaridis et al., 2005)，其中 $y\in\{1,\ldots,q\}$，且对 $f\in\mathbb{R}^q$，

$$L(f,y)=\max_{\ell}\left[\gamma(y,\ell)-(f_y-f_\ell)\right],$$

其中 $\gamma(y,y)=0$ 且 $\gamma(y,\ell)\ge 0$。该损失试图以间隔 $\gamma(y,\ell)$ 将真实类别 $y$ 与备选 $\ell\ne y$ 分开。它关于 $\|f\|_1$ 是 Lipschitz 的，且 $\gamma_1=1$。因此对于 $k_{\ell,\ell}(x,x)\le B^2$ 对所有 $x$ 和 $\ell$ 成立的问题，由推论 9.31 可得

$$R(\mathcal{G},\mathcal{S}_n)\le \frac{qAB}{\sqrt{n}}.$$

对于结构化 SVM 损失，可以从定理 5.20 的覆盖数估计得到一个更好的 Rademacher 复杂度上界，见命题 9.33。该上界仅对数地依赖于 $q$，我们将其证明留作练习。

### Proposition 9.33

考虑一个关于 $L_\infty$-范数是 $\gamma_\infty$-Lipschitz 的损失函数 $L(f,y)$：

$$|L(p,y)-L(p',y)| \leq \gamma_\infty\|p-p'\|_\infty.$$

设 $\mathcal{F}=\{f(x)=[f_1(x),\ldots,f_q(x)]: f_\ell(x)=\langle w,\psi(x,\ell)\rangle,\ \langle w,w\rangle\leq A^2\}$。假设 $\sup_{x,\ell}\|\psi(x,\ell)\|\leq B^2$。设 $\mathcal{G}=\{L(f,y):f\in\mathcal{F}\}$。则存在常数 $c_0>0$ 使得

$$R(\mathcal{G},S_n)\leq \frac{c_0\gamma_\infty AB\ln n\sqrt{\ln(nq)}}{\sqrt{n}}.$$

也可以考虑结构化 SVM 的软正则化版本

$$\hat{w}=\arg\min_w\left[\frac{1}{n}\sum_{i=1}^{n}L(\langle w,\psi(X_i,\cdot)\rangle,Y_i)+\frac{\lambda}{2}\langle w,w\rangle\right],$$

并使用第 7 章的稳定性分析对其进行分析。事实上，可以很容易验证当 $\sup_{x,\ell}\|\psi(x,\ell)\|_2\leq B$ 时，$L(\langle w,\psi(x,\cdot)\rangle,y)$ 在 $w$ 上是 $B$-Lipschitz 的。定理 7.8 表明对于结构化 SVM 问题，我们有期望泛化上界

$$\mathbb{E}_{S_n}\mathbb{E}_{D}L(\langle\hat{w},\psi(X)\rangle,Y)\leq\inf_w\left[\mathbb{E}_{D}L(\langle w,\psi(X)\rangle,Y)+\frac{\lambda}{2}\langle w,w\rangle\right]+\frac{B^2}{\lambda n}.$$

结构化 SVM 的例子表明对于某些向量值估计问题，稳定性分析可用于获得使用经验过程理论可能更难以获得的结果。

## 9.5 Refined Analysis: Ridge Regression

尽管 Rademacher 复杂度分析导致了有用的泛化结果，但它们并不总是紧的。此外，为了获得更快的收敛速率，我们需要采用局部 Rademacher 复杂度分析，如第 6.5 节所述。

对于岭回归问题，

$$\hat{w}=\arg\min_w\left[\frac{1}{n}\sum_{i=1}^{n}(w^\top\psi(X_i)-Y_i)^2+\lambda w^\top w\right], \tag{9.18}$$

我们证明可以直接获得更快的速率。这里为了方便使用向量记号 $u^\top v=\langle u,v\rangle$。

为简单起见，我们将考虑可实现的情况，即存在 $w_*$ 使得

$$Y=w_*^\top\psi(X)+\epsilon, \tag{9.19}$$

其中 $\epsilon$ 是可能依赖于 $X$ 的零均值随机噪声。

以下基本结果在岭回归的理论分析中有用。

由此可知，如果 $\operatorname{Var}(\epsilon_i\mid X_i)\leq\sigma^2$，则

$$\begin{aligned}
\mathbb{E}\left[(\hat{w}^{\mathsf T}\psi(X)-w_*^{\mathsf T}\psi(X))^2\mid\{X_i\}_{1}^{n}\right]
&=\frac{1}{n^2}\sum_{i=1}^{n}\mathbb{E}\left[(a_i\epsilon_i)^2\mid X_i\right]+\lambda^2\left[\psi(X)^{\mathsf T}\hat{\Sigma}_{\lambda}^{-1}w_*\right]^2\\
&\leq\frac{1}{n^2}\sum_{i=1}^{n}a_i^2\sigma^2+\lambda^2\left[\psi(X)^{\mathsf T}\hat{\Sigma}_{\lambda}^{-1}w_*\right]^2\\
&\leq\frac{\sigma^2}{n}\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}^2+\lambda^2\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}^2\|w_*\|_{\hat{\Sigma}_{\lambda}^{-1}}^2\\
&\leq\left((\sigma^2/n)+\lambda\|w_*\|_2^2\right)\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}^2.
\end{aligned}$$

第一个等式使用了 (9.20)，以及 $\epsilon_i$ 是独立零均值随机变量的事实。第一个不等式使用了 $\mathbb{E}[\epsilon_i^2]\leq\sigma^2$。第二个不等式使用了 (9.21) 和 Cauchy–Schwarz 不等式。最后一个不等式使用了 $\|w_*\|_{\hat{\Sigma}_{\lambda}^{-1}}^2\leq\|w_*\|_2^2/\lambda$。

此外，如果每个 $\epsilon_i$ 是次高斯的，则

$$\begin{aligned}
\ln\mathbb{E}\left[e^{\mu(\hat{w}^{\mathsf T}\psi(X)-w_*^{\mathsf T}\psi(X))}\mid\{X_i\}_{1}^{n}\right]
&=-\mu\lambda\psi(X)^{\mathsf T}\hat{\Sigma}_{\lambda}^{-1}w_*+\ln\mathbb{E}\left[e^{(\mu/n)\sum_{i=1}^{n}a_i\epsilon_i}\mid\{X_i\}_{1}^{n}\right]\\
&\leq-\mu\lambda\psi(X)^{\mathsf T}\hat{\Sigma}_{\lambda}^{-1}w_*+\frac{\mu^2\sigma^2}{2n^2}\sum_{i=1}^{n}a_i^2\\
&\leq\mu\lambda\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}\|w_*\|_{\hat{\Sigma}_{\lambda}^{-1}}+\frac{\mu^2\sigma^2}{2n}\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}^2\\
&\leq\mu\sqrt{\lambda}\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}\|w_*\|_2+\frac{\mu^2\sigma^2}{2n}\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}^2.
\end{aligned}$$

第一个等式使用了 (9.20)。第一个不等式使用了次高斯噪声假设。第二个不等式使用了 (9.21) 和 Cauchy–Schwarz 不等式。最后一个不等式使用了 $\|w_*\|_{\hat{\Sigma}_{\lambda}^{-1}}\leq\|w_*\|_2/\sqrt{\lambda}$。这意味着 $\hat{w}^{\mathsf T}\psi(X)-w_*^{\mathsf T}\psi(X)$ 是次高斯的。期望的概率界可由定理 2.12 中的标准次高斯尾部不等式得到。

引理 9.34 表明模型在任意测试数据点 $X$ 处的置信度与 $\|\psi(X)\|_{\hat{\Sigma}_{\lambda}^{-1}}$ 成正比。这意味着对于岭回归，可以在任意数据点 $X$ 处获得置信区间。特别地，如果我们对训练数据中所有 $X_i$ 的 $w_*^{\mathsf T}\psi(X_i)$ 估计感兴趣，则通过对 $\{X_1,\ldots,X_n\}$ 取并界，我们以概率 $1-\delta$ 得到，

$$\frac{1}{n}\sum_{i=1}^{n}(\hat{w}^{\mathsf T}\psi(X_i)-w_*^{\mathsf T}\psi(X_i))^2=O\left(\left(\lambda\|w_*\|_2^2+\frac{\sigma^2\ln(n/\delta)}{n}\right)\operatorname{trace}\left(\hat{\Sigma}_{\lambda}^{-1}\hat{\Sigma}_0\right)\right).$$

也可以使用 $\chi^2$ 尾概率界的推广来更直接地得到训练预测误差的上界，而无需因并界而支付 $\ln n$ 的代价。
