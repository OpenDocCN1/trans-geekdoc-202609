

![](img/2fa0633d317c0872f05788febf717c11_361_0.png)

## 图 17.2 域与迹

回顾在此上下文中**迹的传递性**，在练习 12.1.16 中证明：若 $K \subseteq L \subseteq F$ 是三个域的塔，则 $tr_{F|K}$ 是 $tr_{L|K} \circ tr_{F|L}$ 的连接。设 $W \subset F$ 为 $(q^2 + 1)$ 次单位根的群。将 $\mathcal{K}_q$ 的点记为 $P(0) = (1,0)$ 和 $P(a,w) = (1, a w)$，其中 $0 \neq a \in \mathbb{F}_4$ 且 $w \in W$。

数 3、$q - 1$ 和 $q^2 + 1$ 两两互素。这意味着点 $P(0)$ 与 $P(a,w)$ 两两不同。将 $P(0)$ 与 $\mathcal{K}_q$ 的其余两点不共线作为练习 17.3.3 留下。我们证明 $P(a,w)$ 构成一个帽。起初我们需要一个判据来决定 $K$ 的哪些元素是 $W$ 的元素在迹 $T$ 下的像。这由希尔伯特定理 90 的加法版本、命题 17.21 给出。

### 17.56 引理。
*设 $0 \neq \alpha \in \mathbb{F}_{q^2}$。以下等价：*

- 存在 $w \in W$ 使得 $T(w) = \alpha$。
- $Tr(1/\alpha) \in \mathbb{F}_4 \setminus \mathbb{F}_2$。
- $tr(1/\alpha) = 1.$

**证明** 因为迹的传递性，第二和第三条件等价。我们有 $w^{q^2} = 1/w$ 对 $w \in W$ 成立，故 $T(w) = w + 1/w$。由此 $T(w) = \alpha$ 等价于 $(w/\alpha)^2 + (w/\alpha) + 1/\alpha^2 = 0$。显然 $w = 1$ 不是解。设 $tr(1/\alpha) = 0$。由命题 17.21，$x^2 + x + 1/\alpha^2 = 0$ 的解在 $K$ 中。于是 $w \in K$，矛盾。这说明此情形下无解。结论现在由计数得出：$w = 1$ 是唯一使 $T(w) = 0$ 的 $w \in W$，且每个 $\alpha \neq 0$ 在 $W$ 中在 $T$ 下至多有两个原像。于是每个满足 $tr(1/\alpha) = 1$ 的 $\alpha \in K$ 必须有两个这样的原像。

设 $P(a1, w1)$, $P(a2, w2)$, $P(a3, w3)$ 为 $\mathcal{K}_q$ 的不同点且共线。设 $1$, $\lambda$, $\lambda + 1$ 为仿射线性组合的系数，其中 $\lambda \in F_q \setminus F2$。这给出方程

$(\lambda + 1)a1 w1 = a2 w2 + \lambda a3 w3$.

先假设对某些 $i \neq j$ 有 $a_i = a_j$。我们可以设 $a2 = a3 = 1$ 且 $w3 = 1$。方程为

$(\lambda + 1)a1 w1 = w2 + \lambda$.

由于第二和第三点不同，于是 $w2 \neq 1$。对两边应用范数 $(N(x) = x^{q^2+1})$ 得 $(\lambda^2 + 1)a1^2 = \lambda^2 + 1 + \lambda \alpha$，其中 $\alpha = T(w2)$。由于 $w2 \neq 1$，有 $\alpha \neq 0$。于是 $a1 \neq 1$。方程

$1/\alpha (a1^2 + 1) = \lambda/(\lambda^2 + 1) = 1/(\lambda + 1) + 1/(\lambda + 1)^2$

经应用 $Tr$ 后给出

$(a1^2 + 1)Tr(1/\alpha) = Tr(1/(\lambda + 1) + 1/(\lambda + 1)^2) = tr(1/(\lambda + 1))$

（最后等式由迹的定义得出）。迹的传递性表明 $tr$ 关于 $tr_{K|F_q}$ 分解。由于 $tr_{K|F_q}$ 在 $F_q$ 上消失，于是 $(a1^2 + 1)Tr(1/\alpha) = 0$，故 $Tr(1/\alpha) = 0$，与引理 17.56 矛盾。

现在设 $a_i$ 为 $F4$ 中两两不同（且非零）的元素。我们可以选记号使得

$(\lambda + 1)w1 = \omega w2 + \lambda \omega$.

应用 $N$ 得 $\lambda^2 + 1 = \omega + \lambda^2 \omega + \lambda \alpha$，其中 $\alpha = T(w2)$。我们有 $\alpha \neq 0$，否则 $\lambda \in F4$，这是不可能的，因为 $F_q \cap F4 = F2$。方程的等价形式为 $\lambda^2 \omega + \lambda \alpha + \omega = 0$。乘以 $\omega/\alpha^2$ 得 $x^2 + x + 1/\alpha^2 = 0$，其中 $x = \lambda \omega/\alpha$。这给出 $tr(1/\alpha) = 0$，再次与引理 17.56 矛盾。

本小节所呈现的构造表明，我们可以在 $PG(4, q)$ 中找到约 $2.5 q^2$ 个点的帽，对奇数 $q$，以及在 $q = 2^{\text{odd}}$ 时在 $AG(4, q)$ 中大小约 $3 q^2$ 的帽。像 $\approx 3q^2$ 这样的表达式表示点数是 $q$ 的多项式，以 $3q^2$ 为首项。这些似乎是 $PG(4, q)$ 中已知的最大帽，除了仅对个别小 $q$ 有效的构造之外。注意我们的 $AG(4, q)$ 中的帽可视为对偶 $BCH$ 码（见练习 17.3.4）。对于 $q = 2^{\text{even}}$，在 $PG(4, q)$ 中似乎没有已知大小约 $c q^2$ 且 $c > 2$ 的帽族。此外，所有这些帽族都远离已知的上界。

考虑由 $(3q^3 + 4)$ 帽 $\mathcal{K}_q \subset AG(4, q)$ 几何描述的代码 $C_q$，其中 $q = 2^f$, $f$ 为奇数。由于与 Kloosterman 码的密切联系，$C_q$ 的权分布可以确定。在特殊情形 $q = 8$，这给出一个 $[196, 5, 164]_8$ 码。由于它包含维数为 4 且最小距离为 168 的子码，我们可以应用加长并得到一个 $[200, 5, 168]_8$ 码（见 [81]）。

## 帽的一般上界

我们从仿射帽的一般上界开始。

### 17.57 定义。
记 $C_k(q)$ 为 $AG(k, q)$ 中帽的最大大小，$c_k(q) = C_k(q)/q^k$ 为其相对大小。

由于 $AG(k, q)$ 是 $q$ 个 $AG(k-1, q)$ 的不交并（见练习 17.3.5），于是 $C_k(q) \le q C_{k-1}(q)$，故 $c_k(q) \le c_{k-1}(q)$。我们有 $c_3(q) = 1/q$（见练习 17.3.7）。我们将导出 $c_{k-1}(q) - c_k(q)$ 的下界。这特别表明 $AG(k, q)$ 中的极大帽不能与每个超平面相交于极大帽。

如常，设 $q = p^f > 2$。设 $A \subset AG(k, q)$ 为一帽。由于 $q > 2$，我们可以找到非零元素 $\lambda_i \in F_q$ 使得 $\lambda_1 + \lambda_2 + \lambda_3 = 0$。$\lambda_i$ 在整个证明中固定。设 $V = F_q^k = AG(k, q)$ 且 $T : F_q \longrightarrow F_p$ 为迹函数。置 $Q = |V| = q^k$。最后，复数 $\zeta = \exp(2\pi i / p)$ 是 $p$ 次单位根。目标是对 $|A|$ 给出上界。为此，研究复数 $S = \sum_{y \in V\setminus\{0\}} \sum_{a1,a2,a3 \in A} \zeta^{T((\sum_i \lambda_i a_i)\cdot y)}$。该数易于确定：反转求和次序并将内和对所有 $y \in V$ 延拓。对应于 $y = 0$ 的额外项为 $|A|^3$。由于 $\zeta$ 的所有幂之和为零，内和在 $a1 = a2 = a3$ 时才不消失。我们得到 $S = |A|(Q - |A|^2)$。

现在我们对 $|S|$ 给出上界。设 $0 \neq \lambda \in \mathbb{F}_q$ 且 $0 \neq y \in V$。考虑复数 $U(\lambda)_y = \sum_{a\in A} \zeta^{T((\lambda a)\cdot y)}$。设 $u(\lambda)_y = |U(\lambda)_y|$。

定义长度为 $Q-1$ 的实向量 $u(\lambda)$，其坐标由 $0 \neq y \in V$ 参数化，对应项为 $u(\lambda)_y$。我们有 $S = \sum_{y\neq0} U(\lambda1)_y U(\lambda2)_y U(\lambda3)_y$，特别地，$|S| \le \sum_{y\neq0} u(\lambda1)_y u(\lambda2)_y u(\lambda3)_y$。

我们对实向量 $u(\lambda)$ 知道什么？与确定 $S$ 类似的计算表明我们知道这些向量的长度：$\|u(\lambda)\|^2 = |A|(Q - |A|)$。

组合信息在以下引理中，即对项 $u(\lambda)_y$ 的上界：

### 17.58 引理。
设 $0 \neq \lambda \in \mathbb{F}_q$ 且 $0 \neq y \in V$。则 $u(\lambda)_y \le q C_{k-1}(q) - |A| = c_{k-1}(q) Q - |A|$。

证明 由于 $\lambda A$ 为帽，我们可以设 $\lambda = 1$。记 $\nu_c$ 为满足 $a\cdot y = c$ 的 $a \in A$ 的个数。由于满足 $v\cdot y = c$ 的 $v \in V$ 构成子空间 $AG(k-1,q)$（见练习 17.3.6），我们有 $\nu_c \le C_{k-1}(q)$。于是 $u(\lambda)_y = |\sum_{c\in\mathbb{F}_q} \nu_c \zeta^{T(c)}| = |\sum_{c\in\mathbb{F}_q} (C_{k-1}(q) - \nu_c) \zeta^{T(c)}|$（这里再次使用 $\zeta$ 的所有幂之和为零）$\le \sum_c (C_{k-1}(q) - \nu_c) = q C_{k-1}(q) - |A|$。

现在我们可利用前一引理的上界和经典的 Cauchy-Schwartz 不等式对 $|S|$ 给出上界。该不等式的最佳已知版本指出，对实向量 $x = (x1,\ldots,xn)$, $y = (y1,\ldots,yn)$，有 $|x\cdot y| \le \|x\|\|y\|$。

回顾 Plotkin 界的证明使用了该不等式的推论；见第 9 章。我们有 $|S| \le (c_{k-1}(q) Q - |A|)(|A|(Q - |A|))$。将该上界与 $|S|$ 的精确值比较给出 $C_k(q)$ 的以下界，即本小节的主要结果。

### 17.59 定理。
设 $q > 2$ 为素数幂。若 $k \ge 3$，则

$$c_k(q) \le \frac{q^{-k} + c_{k-1}(q)}{1 + c_{k-1}(q)}$$

等价地

$$(1 - c_k(q))(c_{k-1}(q) - c_k(q)) \ge c_k^2 - q^{-k}.$$

特别地，我们得到所期望的下降量 $c_{k-1}(q) - c_k(q)$ 的下界。定理 17.59 最初由 R. Meshulam [152] 在奇特征下利用傅里叶变换的机制得到。本节概述的直接方法是来自 [24]。它也涵盖特征 2 情形。

可由定理 17.59 导出渐近界：

### 17.60 定理。
设 $q > 2$ 且 $k \ge 3$。则

$$c_k(q) \le \frac{k + 1}{k^2}.$$

为了由定理 17.59 导出射影帽的界，需要以下递归构造：

### 17.61 定理。
设 $q > 2$。若 $PG(k-1,q)$ 中存在 $n$-帽，则 $AG(k,q)$ 包含一个 $(2n)$ 帽。

**证明** 对 $PG(k-1,q)$ 中帽的每个点 $(x_1 : \cdots : x_k)$，选取代表元 $x = (x_1,\ldots,x_k) \in \mathbb{F}_q^k$。设 $c \in \mathbb{F}_q, c \ne 0,1$。我们断言形如 $(x,1)$, $(cx,1)$ 的 $2n$ 个点构成 $AG(k,q)$ 中的帽。显然这些是 $2n$ 个不同点。它们在仿射空间中，因为它们避开超平面 $x_{k+1}=0$。它们构成帽的初等证明留给读者。

定理 17.61 与 17.60 一起给出以下结论：

### 17.62 定理。
设 $q > 2$ 且 $k \ge 3$。$PG(k,q)$ 中帽的大小被 $q^{k+1} \frac{k+2}{2(k+1)^2}$ 所限制。

定理 17.61 的加倍构造是递归帽构造的一个初等例子。下一小节将给出更多递归构造。

## 帽的递归构造

帽的一般乘积构造由 Mukhopadhyay [154] 给出。我们从一个稍作推广开始。

