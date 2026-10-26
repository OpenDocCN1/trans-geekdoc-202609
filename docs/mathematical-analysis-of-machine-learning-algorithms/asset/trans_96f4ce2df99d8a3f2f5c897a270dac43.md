
某些分布。相比之下，基于 Assouad 引理的分析采用分布之间的 TV 范数（见附录 B），该范数始终有限。对于某些序贯估计问题，使用这种方法也更容易。

## Lemma 12.27 (Generalized Assouad’s Lemma)

设 $\mathcal{P}$ 为有限的分布族。设 $d \ge 1$ 为整数，且 $Q$ 可分解为

$$Q(\theta,\mathcal{D})=\sum_{j=1}^{d}Q_j(\theta,\mathcal{D}),$$

其中 $Q_j \ge 0$ 均为非负。假设对所有 $j$，存在 $\mathcal{P}$ 的一个划分 $\mathcal{M}_j$。我们用记号 $\mathcal{D}'\sim_j\mathcal{D}$ 表示 $\mathcal{D}'$ 和 $\mathcal{D}$ 属于 $\mathcal{M}_j$ 中的同一划分。令 $m_j(\mathcal{D})$ 为包含 $\mathcal{D}$ 的划分中的元素个数。假设存在 $\epsilon,\beta \ge 0$ 使得

$$\forall\mathcal{D}'\sim_j\mathcal{D},\ \mathcal{D}'\ne\mathcal{D}:\qquad \inf_{\theta}\left[Q_j(\theta,\mathcal{D}')+Q_j(\theta,\mathcal{D})\right]\ge\epsilon,$$

$$\forall\mathcal{D}\in\mathcal{P}:\qquad \frac{1}{d(\mathcal{P})}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}_j}\frac{1}{m_j(\mathcal{D})-1}\sum_{\mathcal{D}'\sim_j\mathcal{D}}\|\mathcal{D}'-\mathcal{D}\|_{\mathrm{TV}}\le\beta,$$

其中 $\mathcal{P}_j=\{\mathcal{D}\in\mathcal{P}:m_j(\mathcal{D})>1\}$ 且 $d(\mathcal{P})=\sum_{j=1}^{d}|\mathcal{P}_j|$。令 $\mathcal{A}(Z)$ 为任意估计量，则我们有

$$\frac{1}{|\mathcal{P}|}\sum_{\mathcal{D}\in\mathcal{P}}\mathbb{E}_{Z\sim\mathcal{D}}\mathbb{E}_{\mathcal{A}}Q(\mathcal{A}(Z),\mathcal{D})\ge\frac{\epsilon d(\mathcal{P})}{2|\mathcal{P}|}[1-\beta],$$

其中 $\mathbb{E}_{\mathcal{A}}$ 关于 $\mathcal{A}$ 的内部随机性。

**Proof** 为记号方便，假设存在 $d\mu(z)$ 使得对所有 $\mathcal{D}\in\mathcal{P}$，$p_{\mathcal{D}}(z)d\mu(z)$ 为 $\mathcal{D}$ 的分布。则

$$\frac{2}{|\mathcal{P}|}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}}\mathbb{E}_{Z\sim\mathcal{D}}Q_j(\mathcal{A}(Z),\mathcal{D})\ge\frac{2}{|\mathcal{P}|}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}_j}\mathbb{E}_{Z\sim\mathcal{D}}Q_j(\mathcal{A}(Z),\mathcal{D})$$

$$=\frac{1}{|\mathcal{P}|}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}_j}\frac{1}{m_j(\mathcal{D})-1}\sum_{\substack{\mathcal{D}'\sim_j\mathcal{D}\\\mathcal{D}'\ne\mathcal{D}}}\left[\mathbb{E}_{Z\sim\mathcal{D}'}Q_j(\mathcal{A}(Z),\mathcal{D}')+\mathbb{E}_{Z\sim\mathcal{D}}Q_j(\mathcal{A}(Z),\mathcal{D})\right]$$

$$=\frac{1}{|\mathcal{P}|}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}_j}\frac{1}{m_j(\mathcal{D})-1}\sum_{\substack{\mathcal{D}'\sim_j\mathcal{D}\\\mathcal{D}'\ne\mathcal{D}}}\int\left[Q_j(\mathcal{A}(z),\mathcal{D})p_{\mathcal{D}}(z)+Q_j(\mathcal{A}(z),\mathcal{D}')p_{\mathcal{D}'}(z)\right]d\mu(z)$$

$$\overset{(a)}{\ge}\frac{1}{|\mathcal{P}|}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}_j}\frac{1}{m_j(\mathcal{D})-1}\sum_{\substack{\mathcal{D}'\sim_j\mathcal{D}\\\mathcal{D}'\ne\mathcal{D}}}\int\epsilon\min\bigl(p_{\mathcal{D}}(z),p_{\mathcal{D}'}(z)\bigr)d\mu(z)$$

$$\overset{(b)}{=}\frac{1}{|\mathcal{P}|}\sum_{j=1}^{d}\sum_{\mathcal{D}\in\mathcal{P}_j}\frac{1}{m_j(\mathcal{D})-1}\sum_{\substack{\mathcal{D}'\sim_j\mathcal{D}\\\mathcal{D}'\ne\mathcal{D}}}\epsilon\left(1-\|\mathcal{D}-\mathcal{D}'\|_{\mathrm{TV}}\right).$$

在此推导中，第一个不等式使用了 $Q_j(\cdot) \ge 0$；$(a)$ 使用了引理的假设，且 $(b)$ 使用了 TV 范数的定义（见附录 B）。通过重排最后一项并使用 $\beta$ 的定义，我们得到期望的界。

这里陈述的 Assouad 引理是文献中出现的典型 Assouad 引理的推广。后者通常表述为

$\mathcal{P} = \{\mathcal{D}_\tau : \tau \in \{\pm1\}^d\}$,

且 $\mathcal{M}_j$ 包含在 $\{\pm1\}^d$ 中仅在坐标 $j$ 上与 $\tau$ 不同 的指标。下面的结果是使用该表示对 Assouad 引理的直接应用，且乘积分布的 TV 范数由定理 B.13 估计。

## Theorem 12.28

设 $d \ge 1$ 为整数且 $\mathcal{P}_d = \{\mathcal{D}_\tau : \tau \in \{-1,1\}^d\}$ 包含 $2^d$ 个概率测度。假设损失函数 $Q$ 可分解为

$Q(\theta, \mathcal{D}) = \sum_{j=1}^d Q_j(\theta, \mathcal{D})$, 

其中 $Q_j(\cdot, \cdot) \ge 0$。对任意 $j$ 和 $\tau$，令 $\tau^{-[j]}$ 为仅在坐标 $j$ 上与 $\tau$ 不同的指标。假设存在 $\epsilon, \beta_j \ge 0$ 使得

$\forall \tau: \quad [Q_j(\theta, \mathcal{D}_\tau) + Q_j(\theta, \mathcal{D}_{\tau^{-[j]}})] \ge \epsilon, \quad H(\mathcal{D}_\tau \| \mathcal{D}_{\tau^{-[j]}}) \le \beta_j.$

考虑基于 $\mathcal{S}_n \sim \mathcal{D}_\tau^n$ 的随机化 $\mathcal{A}(\mathcal{S}_n)$，其中 $\tau$ 为某值。我们有

$\frac{1}{2^d} \sum_\tau \mathbb{E}_{\mathcal{S}_n \sim \mathcal{D}_\tau^n} \mathbb{E}_\mathcal{A} Q(\mathcal{A}(\mathcal{S}_n), \mathcal{D}_\tau) \ge \frac{\epsilon d}{2} - \frac{\epsilon}{2} \sum_{j=1}^d \sqrt{2 - 2(1 - 0.5 \beta_j^2)^n}$, 

其中 $\mathbb{E}_{\mathcal{A}}$ 关于 $\mathcal{A}$ 的内部随机性。这意味着

$r_n(\mathcal{P}_d, Q) \ge \frac{\epsilon d}{2} - \frac{\epsilon}{2} \sum_{j=1}^d \sqrt{2 - 2(1 - 0.5 \beta_j^2)^n}$.

一般而言，若我们能选择 $\beta_j = O(\epsilon)$，则定理 12.28 推出界

$r_n(\mathcal{P}_d, Q) \ge \Omega(d\epsilon)$

当 $n = O(1/\epsilon^2)$ 时。下面的例子用具体应用说明这一点。

## Example 12.29

考虑观测 $Z_i \in \{0,1\}^d$，其中每个 $Z_i$ 有 $d$ 个分量 $Z_{i,j} \sim \text{Bernoulli}(\theta_j)$，$j = 1, \dots, d$。令 $\theta = [\theta_1, \dots, \theta_d] \in (0,1)^d$ 为待估计的模型参数。对 $\tau \in \{\pm1\}^d$，我们令 $\theta_{\tau,j} = \epsilon^2 (1 + \tau_j)/2$，其中 $\epsilon \in (0,0.5)$。令 $\mathcal{D}_\tau$ 为相应的 Bernoulli 分布，且 $\mathcal{P}_d = \{\mathcal{D}_\tau\}$。定义度量

$Q(\hat{\theta}, \theta) = \sum_{j=1}^d Q_j(\hat{\theta}, \theta), \quad Q_j(\hat{\theta}, \theta) = \left| \sqrt{\hat{\theta}_j} - \sqrt{\theta_j} \right|.$

Barron, 1999)。定理 12.11 中 Fano 不等式推广所使用的条件受 Zhang (2006) 分析的启发。

筛方法在 1980 年代在非参数统计中被提出（Grenander, 1981; Geman and Hwang, 1982），尽管 ERM 的次优性直到 much later 才被正式证明（Birgé and Massart, 1993）。筛方法和指数聚合方法均已知能达到最优收敛速率。Gibbs 算法的 minimax 分析可在 Zhang (2006) 中找到。当方差条件成立时，针对凸函数类的误设模型也成立类似结果（见例 3.18）。然而，使用 ERM 在与函数类中的最优函数竞争时，对于非凸函数类我们只能得到较差的结果（见例 3.25 和命题 8.12）。对于一般的非凸函数类，已知（见例 15.21）当模型被误设时，指数模型聚合优于经验风险最小化（见 Lecué, 2007; Audibert, 2007）。误设模型的情况不影响本章的 minimax 分析，因为我们在分析中仅考虑了良设模型。

## Exercises

- 12.1 证明命题 12.2。
- 12.2 考虑函数类

$\mathcal{F} = \{w^\top x : \|w\|_2 \le 1\}$.

考虑经验分布 $\mathcal{S}_n = \{X_1, \dots, X_n\}$ 使得对所有 $i$ 有 $\|X_i\|_2 \le 1$。导出高斯复杂度 $G(\mathcal{F}, \mathcal{S}_n)$ 的上界，并使用 Sudakov 次极小化得到 $N(\epsilon, \mathcal{F}, L_2(\mathcal{S}_n))$ 的上界。
- 12.3 使用定理 12.11、引理 12.14 和定理 B.6 证明定理 12.15。
- 12.4 考虑定义在 $[0,1)$ 上的函数类

$\mathcal{F} = \{f_0(x)\} \cup \{f_0(x) + 0.1 n^{-r/3} + n^{-r/2} \Delta f_u(x) : u \in \{\pm1\}^n\}$,

其中 $r \in (0,1]$。
令 $f_0(x)=0$ 且 $\Delta f_u(x)=u_j \forall x \in [(j-1)/n, j/n)$ $(j=1,\dots,n)$，令

$Y = f_*(x) + \epsilon, \quad \epsilon \sim N(0,1)$,

其中 $f_* \in \mathcal{F}$，且 $X$ 在 $[0,1)$ 上均匀抽取。
考虑最小二乘问题

$Q_{LS}(f, \mathcal{D}) = \mathbb{E}_{X \sim \mathcal{D}} (f(X) - f_{\mathcal{D}}(X))^2$,

并考虑 $n$ 个样本 $\mathcal{S}_n = \{(X_1,Y_1),\dots,(X_n,Y_n)\}$。

  - 求用这些 $n$ 个样本估计 $f_*$ 的 minimax 风险（ up to a constant）。
  - 证明存在足够小的常数 $c$ 使得以至少 0.5 的概率，至少有 $0.1 n$ 个桶 $[(j-1)/n, j/n)$ 使得恰好有一个 $X_i$ 属于 $[(j-1)/n, j/n)$。
  - 求对足够大的 $n$，$\mathcal{F}$ 上 ERM 方法的风险下界。
- 12.5 证明定理 12.24 和推论 12.25。
- 12.6 使用定理 12.28 推导出例 12.16 的下界。

