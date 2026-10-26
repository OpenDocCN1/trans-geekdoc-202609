
我们有以下定理，可用于估计核方法的覆盖数。该结果与问题的维度无关。

**Theorem 5.18**  设 $w=[w_1,w_2,\ldots]\in\mathbb{R}^{\infty}$ 且 $\psi(x)=[\psi_1(x),\psi_2(x),\ldots]\in\mathbb{R}^{\infty}$。设 $\Omega=\{w:\|w\|_2\le A\}$。给定 $\mathcal{X}$ 上的分布 $\mathcal{D}$，假设存在 $B_1\ge B_2\ge\cdots$ 使得

$$\mathbb{E}_{x\sim\mathcal{D}}\sum_{i\ge j}\psi_i(x)^2\le B_j^2.$$

定义

$$\tilde d(\epsilon)=\min\{j\ge 0:AB_{j+1}\le\epsilon\}.$$

则函数类 $\mathcal{F}$ 的 (5.3) 满足

$$\ln N(\epsilon,\mathcal{F},L_2(\mathcal{D}))\le \tilde d(\epsilon/2)\ln\left(1+\frac{4AB_1}{\epsilon}\right).$$

**Proof**  给定 $\epsilon>0$，考虑 $j=\tilde d(\epsilon/2)$ 使得 $AB_{j+1}\le\epsilon/2$。令 $\mathcal{F}_1=\{\sum_{i=1}^{j}w_i\psi_i(x):w\in\Omega\}$ 且 $\mathcal{F}_2=\{\sum_{i>j}w_i\psi_i(x):w\in\Omega\}$。由于对所有 $f\in\mathcal{F}_2$ 都有 $\|f\|_{L_2(\mathcal{D})}\le\epsilon/2$，我们有 $N(\epsilon/2,\mathcal{F}_2,L_2(\mathcal{D}))=1$。此外，定理 5.3 表明

$$\ln N(\epsilon/2,\mathcal{F}_1,L_2(\mathcal{D}))\le \tilde d(\epsilon/2)\ln\left(1+\frac{4AB_1}{\epsilon}\right).$$

注意 $\mathcal{F}\subset\mathcal{F}_1+\mathcal{F}_2$。我们有 $\ln N(\epsilon,\mathcal{F},L_2(\mathcal{D}))\le\ln N(\epsilon/2,\mathcal{F}_1,L_2(\mathcal{D}))+\ln N(\epsilon/2,\mathcal{F}_2,L_2(\mathcal{D}))$。这就得到了结果。

可以将 $d(\epsilon)$ 视为正则化线性系统 (5.3) 在尺度 $\epsilon$ 下的有效维度。下面的例子给出了定理 5.18 的一个推论。

**Example 5.19**  假设 $B_j=j^{-q}$，则

$$\ln N(\epsilon,\mathcal{F},L_2(\mathcal{D}))=O\left(\epsilon^{-q}\ln(1/\epsilon)\right).$$

若 $B_j=O(c^j)$ 对某个 $c\in(0,1)$，则

$$\ln N(\epsilon,\mathcal{F},L_2(\mathcal{D}))=O\left((\ln(1/\epsilon))^2\right).$$

对于一般的线性函数类 (5.3)，具有 $L_2$ 正则化 $\|w\|_2\le A$ 且 $\|\psi(x)\|_2\le B$，我们可以使用高斯复杂度估计和 Sudakov 下界（见定理 12.4）得到 $\ln N(\epsilon,\mathcal{F},L_2(\mathcal{D}))$ 的界。

此外，已知 $L_2$ 正则化线性函数类的均匀 $L_\infty$ 覆盖数可以按如下方式界定。证明可参见 Zhang (2002)。

**Theorem 5.20**  假设 $\Omega=\{w:\|w\|_2\le A\}$ 且 $\|\psi(x)\|_2\le B$，则函数类 (5.3) 具有以下覆盖数界：

$$\ln N(\mathcal{F},\epsilon,L_\infty(\mathcal{S}_n))\le\frac{36A^2B^2}{\epsilon^2}\ln\left[2\left((4AB/\epsilon)+2\right)n+1\right].$$

在其他正则化条件下也可以得到均匀 $L_\infty$ 覆盖数结果。特别感兴趣的是 $L_1$ 正则化的覆盖数，在此给出。证明也可参见 Zhang (2002)。

**Theorem 5.21**  *假设 $\Omega = \{ w \in \mathbb{R}^d : \|w\|_1 \le A \}$ 且 $\|\psi(x)\|_\infty \le B$，则函数类 (5.3) 具有以下覆盖数界：*

$$\ln N(\mathcal{F}, \epsilon, L_\infty(S_n)) \le \frac{288 A^2 B^2 (2 + \ln d)}{\epsilon^2} \ln\left(2\lceil (8AB/\epsilon) + 2 \rceil n + 1\right).$$

定理 5.20 和定理 5.21 中的均匀 $L_\infty$ 覆盖结果可以结合第 4.6 节的分析来研究大间隔方法。它们也可以用于研究第 9.4 节中考虑的向量值预测问题。

### 5.7 历史与文献评述

覆盖数和熵的概念由 Kolmogorov 和 Tikhomirov (1959) 引入。其中建立了若干光滑函数类的结果。此后，覆盖数的工具在经验过程的理论分析中被广泛使用。定理 5.2 证明中使用的体积比较论证是众所周知的，可参见 Lorentz (1966)。关于 Banach 空间和一般函数空间的熵估计，参见 Pisier (1999) 和 Edmunds 和 Triebel (1996)。光滑函数类的 bracketing 数估计可参见 van der Vaart 和 Wellner (1996, chapter 2.7)、van der Vaart (1994) 以及 Nickl 和 Pötscher (2007)。此类估计可作为下 bracketing 数的估计，可用于如第 3 章中那样分析 ERM。统计分析中 bracketing 数的额外应用，例如最大似然估计的分析，可参见 Birgé 和 Massart (1993)；van de Geer (1993, 2000)；以及 Wong 和 Shen (1995)。

在机器学习文献中，均匀覆盖数的应用变得普遍，很大程度上受到了原始 VC 分析 (Vapnik 和 Chervonenkis, 1971) 的影响。注意，对于光滑函数类，可以得到与 bracketing 结果类似的均匀覆盖数结果 (Nickl 和 Pötscher, 2007)。因此这不是一个严重的限制。对于 VC 类，$n$ 无关的经验 $L_1$ 覆盖数界已被 Dudley (1978) 和 Haussler (1992) 考虑。VC 维向实值 VC 子图类的推广在 Pollard (1984) 和 Haussler (1992) 中被研究。对 *fat-shattering dimension* 的额外推广在 Kearns 和 Schapire (1994) 以及 Bartlett 等 (1996) 中提出，也可用于得到覆盖数的界。然而，由于 fat-shattering 维度的复杂性，通常更直接地使用其他技术来估计覆盖数。因此本章不讨论 fat-shattering 维度。定理 5.6 的结果归功于 Haussler (1995)，其中也得到了匹配的下界。VC-hull 类的覆盖数估计可参见 van der Vaart 和 Wellner (1996, chapter 2.6) 和 Carl (1997)。核函数类的覆盖数界在 Guo 等 (1999)；Cucker 和 Smale (2002)；Zhou (2002, 2003)；以及 Kühn (2011) 中被研究。我们仅在定理 5.18 中考虑了一个简化版本。一般正则化线性函数类的均匀 $L_\infty$ 覆盖数界在 Zhang (2002) 中得到。这些界在 large-margin 分析和向量值预测问题中很有用。

### 练习

- **5.1** 考虑从 $\mathbb{R} \to [0,1]$ 的单调函数函数类 $\mathcal{F}$。证明对 $\mathbb{R}$ 上的任意分布 $\mathcal{D}$，

  $$\ln N_{[]}(\epsilon, \mathcal{F}, L_1(\mathcal{D})) \le \left\lceil \frac{2}{\epsilon} \right\rceil \ln \left\lceil \frac{2}{\epsilon} \right\rceil.$$

  提示：将 $\mathbb{R}$ 和 $[0,1]$ 离散化为规则网格并使用分段常数逼近。

- **5.2** 对于练习 5.1，可以使用更复杂的论证来证明

  $$\ln N_{[]}(\epsilon, \mathcal{F}, L_p(\mathcal{D})) \le \frac{K_p}{\epsilon},$$

  其中 $K_p$ 是依赖于 $p$ 的常数（参见 van der Vaart 和 Wellner, 1996, Theorem 2.7.5）。利用该结果界定具有有界总变差的实值函数类的 bracketing 数：

  $$\mathcal{F} = \{f: V(f) \le B\}, \quad V(f) = \sup_{x_0 \le x_1 \le \cdots \le x_m} \sum_{i=1}^{m} |f(x_i) - f(x_{i-1})|.$$

- **5.3** 假设对所有 $g \in \mathcal{G}$ 都有 $g(z) \in [0,1]$。证明对 $p \ge 1$，

  $$\ln N(\epsilon, \mathcal{G}, L_p(\mathcal{D})) \le \ln N(\epsilon^p, \mathcal{G}, L_1(\mathcal{D})).$$

- **5.4** 考虑 $\mathbb{R}^d$ 中的以下集合：

  $$\Omega = \{x: \|x\|_p \le 1\},$$

  其中 $1 \le p < 2$。证明存在常数 $C_p$ 和 $r_p$ 使得

  $$\ln N(\epsilon, \Omega, \|\cdot\|_2) \le C_p \epsilon^{-r_p} \ln d.$$

- **5.5** 考虑集合

  $$\Omega = \left\{ x = [x_1, x_2, \dots] \in \mathbb{R}^\infty : \sum_{i=1}^{\infty} i \cdot x_i^2 \le 1 \right\},$$

  其度量由 $L_2$ 范数 $\|x\|_2 = \sqrt{\sum_{i=1}^{\infty} x_i^2}$ 诱导。推导 $\ln N(\epsilon, \Omega, \|\cdot\|_2)$ 的上界和下界。

## Rademacher 复杂度与集中不等式

在第 3 章和第 4 章中，我们使用覆盖数和指数概率不等式得到了均匀收敛结果。本章考虑一种不同但密切相关的方法。在这种方法中，我们首先使用所谓的 *Rademacher complexity* 对底层经验过程上确界的期望进行界定，然后使用 *concentration inequalities* 得到高概率界。这种方法简化了泛化分析中的各种推导。

### 6.1 Rademacher 复杂度

使用第 3.3 节的记号，我们给定函数类 $\mathcal{G} = \{\phi(w,z): w \in \Omega\}$，并对训练误差的均匀收敛感兴趣

$$\phi(w, \mathcal{S}_n) = \frac{1}{n} \sum_{i=1}^n \phi(w, Z_i)$$

在训练数据 $\mathcal{S}_n = \{Z_1, \dots, Z_n\} \sim \mathcal{D}^n$ 上，到测试误差

$$\phi(w, \mathcal{D}) = \mathbb{E}_{Z \sim \mathcal{D}} \phi(w, Z)$$

在测试数据 $\mathcal{D}$ 上。特别地，在学习算法的一般分析中，我们希望估计相关经验过程的上确界

$$\sup_{w \in \Omega} [\phi(w, \mathcal{D}) - \phi(w, \mathcal{S}_n)].$$

我们引入以下定义，这将在本章的分析中很有用。

**Definition 6.1** 给定经验过程 $\{\phi(w, \mathcal{S}_n): w \in \Omega\}$，其中 $\mathcal{S}_n \sim \mathcal{D}^n$，定义该经验过程的上确界期望为

$$\epsilon_n(\mathcal{G}, \mathcal{D}) = \mathbb{E}_{\mathcal{S}_n} \sup_{w \in \Omega} [\phi(w, \mathcal{D}) - \phi(w, \mathcal{S}_n)],$$ 

它将被 referred to as 函数类 $\mathcal{G}$ 的 *uniform convergence complexity*。

该量越小，训练误差与测试误差之间的差距越小，这意味着我们过拟合越少。在第 3 章中，我们
