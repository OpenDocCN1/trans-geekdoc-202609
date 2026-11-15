

在概率收敛方面，但似乎无法直接处理几乎必然收敛；如果我们只假设(A0)而不是上面更强的独立性条件，则不清楚(b)是否一般成立。之所以如此，是因为在许多关键技术论证中，感兴趣的某个随机序列$(X_n)$的收敛性是通过首先识别一个更易处理的序列$(Y_n)$来建立的，使得对所有$n$均有$Y_n \stackrel{d}{=} X_n$。要证明对于某个确定的$x$有$X_n \stackrel{c}{\to} x$，或者有$X_n = O_c(1)$，仅需根据完全收敛的定义1.1分别证明$Y_n \stackrel{c}{\to} x$或$Y_n = O_c(1)$即可。类似地，$Y_n \stackrel{p}{\to} x$意味着$X_n \stackrel{p}{\to} x$，且$Y_n = O_p(1)$意味着$X_n = O_p(1)$。但是，如果$Y_n \stackrel{a.s.}{\to} x$，则不一定推出$X_n \stackrel{a.s.}{\to} x$，而且如果$Y_n = O_{a.s.}(1)$，也未必就是$X_n = O_{a.s.}(1)$。

### 注记 A.2 (关于PL$_D(r,1)$上的一致性以及伪利普希茨函数与瓦萨斯坦收敛之间的联系)

AMP迭代的许多渐近收敛结果都以如下形式给出

\(\frac{1}{n} \sum_{i=1}^n \psi(X_{ni}^k) \rightsquigarrow \mathbb{E}(\psi(\bar{X}^k)) \in \mathbb{R}\) as \(n \to \infty\), for every \(\psi \in \text{PL}_D(r)\), (A.1)

其中\(r \in [2, \infty)\)，\(\rightsquigarrow\)表示注记A.1中讨论的三种随机收敛模式之一，随机向量\(\bar{X}^k, X_{ni}^k\)取值于某个固定的\(D \in \mathbb{N}\)的\(\mathbb{R}^D\)，且\(k \in \mathbb{N}\)是固定的迭代次数；通常，每个\(X_{ni}^k\)都依赖于索引为\(n\)的AMP递归前\(k\)次迭代中向量量的第\(i\)个坐标。回顾\(\widetilde{d}_r\)的定义(1.4)，我们从Corollary B.21推断出，任何形式为(A.1)的结论都可以自动升级为一致性陈述

\(\widetilde{d}_r(\mu_n^k, \bar{\mu}^k) = \sup_{\psi \in \text{PL}_D(r, 1)} \left| \frac{1}{n} \sum_{i=1}^n \psi(X_{ni}^k) - \mathbb{E}(\psi(\bar{X}^k)) \right| \rightsquigarrow 0\) as \(n \to \infty\). (A.2)

具有与(A.1)相同的收敛模式\(\rightsquigarrow\)，其中我们将\(\mu_n^k\)记作\(\mathbb{R}^D\)上\(X_{n1}^k, \dots, X_{nn}^k\)的经验分布，并将\(\bar{\mu}^k\)记作极限随机向量\(\bar{X}^k\)的分布。此外，根据Corollary B.21，(A.1)和(A.2)均等价于断言\(d_r(\mu_n^k, \bar{\mu}^k) \rightsquigarrow 0\)。本质上，这是因为\(d_r, \tilde{d}_r\)是等价度量，即它们在\(\mathbb{R}^D\)上具有有限\(r\)阶矩的概率分布空间\(\mathcal{P}_D(r)\)上诱导出相同的拓扑；参见Theorem B.17和Remark B.18。

从技术角度来看，随机量\(\tilde{d}_r(\mu_n^k, \bar{\mu}^k)\)和\(d_r(\mu_n^k, \bar{\mu}^k)\)的可测性由分析考虑保证；Proposition B.16表明，(A.2)中的上确界可以取在有界利普希茨函数的确定可计数子集\(T' \subseteq \text{PL}_D(r)\)上。

### 注记 A.3 (有限样本分析)

为了补充和细化一般AMP程序中类型为(A.1)的一些渐近结论，在适当假设下，相关的证明技巧已被调整，以建立对形式为\(n^{-1} \sum_{i=1}^n \psi(X_{ni}^k) - \mathbb{E}(\psi(\bar{X}^k))\)的量的浓度不等式，其中\(k, n \in \mathbb{N}\)且\(\psi \in \text{PL}_D(r, 1)\)为固定任意函数。对于\(r=2\)，Rush and Venkataramanan (2018)对非对称递归获得了此类有限样本保证，Barbier _et al._ (2020)对对称递归获得了此类保证。借助Lemma B.12（独立高斯随机变量的伪利普希茨函数之和的一般浓度结果），他们的结论可以推广到\(r > 2\)。看看上述结果是否可以扩展，以推导出Theorem 2.1的更强有限样本类比，形式为\(\tilde{d}_r(\nu_n(h^k, \gamma), N(0, \tau_k^2) \otimes \pi) = \sup_{\psi \in \text{PL}_2(r, 1)} |n^{-1} \sum_{i=1}^n \psi(h_i^k, \gamma_i) - \mathbb{E}(\psi(G_k, \bar{\gamma}))|\)或\(d_r(\nu_n(h^k, \gamma), N(0, \tau_k^2) \otimes \pi)\)（其中\(k, n \in \mathbb{N}\)）的浓度不等式，将是很有趣的。

### 注记 A.4 (条件(A2)和(A3))

对于\(r \ge 2\)，此前已在经验分布\(\nu_n(m^0)\)（\(n \in \mathbb{N}\)）的\((2r-2)\)阶矩的有界性假设下，为一般AMP迭代推导出了形式为(A.1)的结论。在(A2)中，我们将其放宽为经验\(r\)阶矩上的有界性条件\(\|m^0\|_{n,r} = O_c(1)\)，这更为自然，并且符合人们对于\(d_r\)收敛结果所期望的情况。为了适应这一较弱的假设，在Lemma B.24中我们采用Hölder不等式而不是Cauchy–Schwarz不等式，而Lemma B.24用于下文Proposition A.16(c)证明中的一个关键估计；参见(A.30)和(A.47)。通过对其他AMP结果的陈述和证明做出类似修改，理应可以避免提及\((2r-2)\)阶经验矩。

(A3)的主要目的是确保不同迭代\(h^j, h^\ell\)（由它们之间的内积\(\langle h^j, h^\ell\rangle_n\)衡量）之间的渐近依赖具有一个确定的极限表达式，即(2.6)中定义的\(\bar{T}_{j,\ell}\)；另见Proposition A.16(d, e, f)。(2.6)所捕获的极限协方差结构的存在对于Theorems 2.1和2.3的证明策略的成功至关重要；事实上，其存在是Theorem 2.3中更一般结论的_必要_条件，这一点可以通过 therein 对\(1 \le j, \ell \le k\)取\(\psi(x_1, \dots, x_k) := x_j x_\ell\)来看出。

### 注记 A.5.

根据(A1)有\(\pi \in \mathcal{P}_1(r)\)，回顾第1.1节可知，如果\(\bar{\gamma} \sim \pi\)，则对于所有\(\psi \in \text{PL}_1(r)\)（即\(\mathbb{R}\)上所有阶数为\(r\)的伪利普希茨函数的集合）均有\(\mathbb{E}(\psi(\bar{\gamma})) = \int_\mathbb{R} \psi d\pi < \infty\)。因此，在(A3)中，给定\(\mathbb{R}\)上的利普希茨函数\(F_0, \phi\)，Lemma B.22确保\(x \mapsto F_0(x)\phi(x)\)位于\(\text{PL}_1(2) \subseteq \text{PL}_1(r)\)（因为\(r \ge 2\)），因此\(\mathbb{E}(F_0(\bar{\gamma})\phi(\bar{\gamma}))\)是有限的。

通过相当常规的论证可以表明，以下条件蕴含了(A2)中的第一个条件以及(A3)；完整的论证参见第A.6节。

(A1⁺) 存在一个利普希茨函数\(\tilde{f}_0: \mathbb{R}^2 \rightarrow \mathbb{R}\)和一个概率分布\(\tilde{\nu}^0 \in \mathcal{P}_1(2)\)，使得当\(\bar{\eta} \sim \tilde{\nu}^0\)和\(\bar{\gamma} \sim \pi\)独立时，将\((\tilde{f}_0(\bar{\eta}, \bar{\gamma}), \bar{\gamma})\)的分布记为\(\mu^0\)，则有\(d_2(\nu_n(m^0, \gamma), \mu^0) \rightarrow^\mathbb{P} 0\)。

在应用中，(A1⁺)比(A3)更便于验证。注意，如果上述\(\tilde{\nu}^0\)满足\(d_2(\nu_n(h^0, \gamma), \tilde{\nu}^0 \otimes \pi) \rightarrow^\mathbb{P} 0\)，则(A1⁺)成立，此时取\(\tilde{f}_0 = f_0\)。

### 注记 A.6.

至少当_r_ = 2时，第2节中的主定理可以扩展到不满足非退化条件(A4)且极限协方差矩阵不必正定的抽象递归。这些退化情况可以通过先扰动利普希茨函数_f<sub>k</sub>*，然后应用一个与第A.8节Theorem 3.1的证明有一些相似之处的连续性论证来处理。中间步骤之一依赖于以下事实：

