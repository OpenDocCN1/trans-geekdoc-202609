
置换等价的概念可用于所有固定块长 $n$ 的码。它使用对称群 $S_n$ 作为运动群。两个码等价当且仅当它们在 $S_n$ 下处于同一轨道。$S_n$ 下的稳定子是码的置换自同构群。

在加性码的特殊情况下，以下更一般的等价概念更为自然。

### 18.11 Definition.
$q$-线性 $q^m$-元码 $\mathcal{C}$ 与 $\mathcal{D}$ 是单项等价的，如果存在 $n$ 个对象的置换 $\pi$ 以及元素 $A_i \in GL(m,q)$ 使得

$(x_0,x_1,\dots,x_{n-1}) \in \mathcal{C} \iff (A_0x_{\pi(0)},A_1x_{\pi(1)},\dots,A_{n-1}x_{\pi(n-1)}) \in \mathcal{D}$

对所有 $x = (x_0,\dots,x_{n-1}) \in \mathcal{C}$ 成立。

运动群是 $GL(m,q)$ 与 $S_n$ 的 wreath 积，其阶为 $|GL(m,q)|^n \times n!$，两个加性码在单项意义下等价当且仅当它们在此较大群作用下处于同一轨道。wreath 积的元素由 $(n+1)$-元组 $(A_0,\dots,A_{n-1},\pi)$ 描述，其中系数 $A_i \in GL(m,q)$ 且置换 $\pi \in S_n$。将单项群的元素写为 $g(A_0,\dots,A_{n-1},\pi)$。

### 18.12 Definition.
长度为 $n$ 的码 $\mathcal{C}$ 在置换意义下是循环的，如果存在 $n$ 轮换 $\pi \in S_n$ 使得 $\pi(\mathcal{C}) = \mathcal{C}$。

$q$-线性 $q^m$-元码 $\mathcal{C}$ 在单项意义下是循环的，如果它在单项群的元素 $g(A_0,\dots,A_{n-1},\pi)$ 下不变，其中 $\pi \in S_n$ 是一个 $n$ 轮换。

由于 $n$ 轮换在 $S_n$ 中共轭，很明显每个在置换意义下循环的码都与一个在置换 $\pi = (0,1,\dots,n-1)$ 下不变的码置换等价。

### 18.13 Proposition.
设 $\mathcal{C}$ 为长度 $n$ 的 $q$-线性 $q^m$-元码且在单项意义下循环。则以下成立：

- $\mathcal{C}$ 与在 $g(I,\dots,I,A'_{n-1},\pi)$ 下不变的码单项等价，其中 $\pi = (0,1,\dots,n-1)$。
- 若 $\mathcal{C}$ 在 $g(A_0,\dots,A_{n-1},(0,\dots,n-1))$ 下不变且 $A_0A_1\dots A_{n-1}=I$，则 $\mathcal{C}$ 在置换意义下循环。
- 若 $\mathcal{C}$ 在 $g(I,\dots,I,A,(0,\dots,n-1))$ 下不变且 $\operatorname{ord}(A)$ 与 $n$ 互素，则 $\mathcal{C}$ 在置换意义下循环。

### Proof
我们刚刚看到可以假设 $\mathcal{C}$ 在 $g(A_0,A_1,\dots,A_{n-1},\pi)$ 下不变，其中 $\pi = (0,1,\dots,n-1)$。我们有 $(x_i) \in \mathcal{C}$ 蕴含 $(A_i x_{i+1}) \in \mathcal{C}$。现在令

$\mathcal{C}' = \{(B_0x_0,\dots,B_{n-1}x_{n-1}) \mid x = (x_0,\dots,x_{n-1}) \in \mathcal{C}\}$。

令 y_i = B_i x_i。则 $(y_i) \in C'$ 蕴含 $(B_i A_i B_{i+1}^{-1} y_{i+1}) \in C'$。选择 $B_i$ 使得（对 $i = 0$）$B_1 = B_0 A_0$，（对 $i = 1$）$B_2 = B_1 A_1 = B_0 A_0 A_1$，直到（对 $i = n − 2$）$B_{n−1} = B_{n−2} A_{n−2} = B_0 A_0 … A_{n−2}$。由此可知 $C'$ 在 $g(I,…,I,A,(0,1,…,n−1))$ 下不变，如所声称。 这里 $A = B_0(A_0 A_1 … A_{n−1}) B_0^{-1}$，是 $A_0 A_1 … A_{n−1}$ 的一个共轭。关于置换意义下循环性的第一个陈述由此得出。现在设 $C$ 在 $g = g(I,…,I,A,(0,…,n−1))$ 下不变且 $\operatorname{ord}(A) = u$ 与 $n$ 互素。则 $g^u$ 的 $u$ 个系数等于 $A$，其余为 $I$。$g^u$ 的置换是一个 $n$ 轮换。第一个陈述蕴含 $C$ 在置换意义下循环。

循环群 $G = \langle g(A_0,…,A_{n−1},(0,…,n−1))\rangle$ 的阶是 $n$ 的倍数，并在 $\mathbb{F}_q$ 上的 $n$ 维向量空间 $V$ 上作用。循环码是 $V$ 的 $G$ 子模。如果 $G$ 在 $V$ 上的作用完全可约，则理论大大简化。

### 18.14 Definition.
设群 $G$ 在向量空间 $V = V(n,K)$ 上作用。不可约子模 $A \subset V$ 是非零的 $G$ 子模，且不包含真 $G$ 子模（不同于 $0$ 和 $A$ 本身）。若对 $V$ 中每一个 $G$ 子模 $A \subset V$，存在 $A$ 的直接补 $B$ 且 $B$ 是 $G$ 模，则称 $G$ 的作用完全可约。

如果作用完全可约，那么在某种程度上只需知道不可约模，因为每个 $G$ 子模都是不可约模的直和。仍有工作要做，因为模表示为不可约模直和的方式可能不唯一。然而，与完全可约性不满足的情况相比，情况要简单得多。这就是 Maschke 定理发挥作用的地方。

### 18.15 Theorem (Maschke).
在定义 18.14 的情形下，设 $G$ 的阶与底层域的特征 $p$ 互素。则 $G$ 的作用完全可约。

另见 [130]，第 666 页。这个基本定理是循环码理论中常假设 $\gcd(n,p) = 1$ 的原因。

## Additive codes which are cyclic in the permutation sense
回顾情形：$W$ 是由置换 $(0,1,…,n−1)$ 生成的循环群。它将向量空间 $V(n,q)$ 上的坐标循环置换。$W$ 子模恰好是 $\mathbb{F}_q$ 上的循环线性码。我们假设 $\gcd(n,p) = 1$。由于 Maschke 定理，$W$ 在 $V(n,q)$ 上的作用完全可约。设 $r = \operatorname{ord}_n(q)$ 为 $q$ 在模 $n$ 下计算时的阶。则 $n \mid (q^r − 1)$ 且 $r$ 是具有此性质的最小自然数。设 $F = \mathbb{F}_{q^r}$。于是我们在 $F^*$ 中找到一个阶为 $n$ 的循环群。将 $W$ 与 $\mathbb{F}_q^*$ 的此子群等同起来是有益的。设 $W = \langle\alpha\rangle$。

由于我们对循环 **additive** 码感兴趣，我们的字母表为 $E = \mathbb{F}_q^m$，并研究 $W$ 在 $V_m = E^n = \mathbb{F}_q^{mn}$ 上的作用。然而请记住，我们将 $V_m$ 的元素（码字）视为 $E$ 上的 $n$-元组，而不是 $\mathbb{F}_q$ 上的 $nm$-元组。将码字的 $n$ 个分量称为外坐标（与 $W$ 的元素 $\alpha^i$，$i = 0,\ldots,n-1$ 之间一一对应），将字母表 $E$ 的 $m$ 个坐标称为内坐标。设 $V_{m,F} = V_m \otimes F = (F^m)^n$ 通过常数扩张得到，$W$ 在外坐标上作用。我们将码 $C \subset V_m = E^n = \mathbb{F}_q^{nm}$ 与其常数扩张 $C \otimes F \subset V_{m,F}$ 联系起来，并利用关于在较大域 $F$ 和子域 $\mathbb{F}_q$ 上定义的码之间关系的基本事实。特别是，我们将每个子码 $U \subset V_{m,F}$ 与其迹码 $tr(U) \subset V_m$ 关联，后者通过在每个内坐标上应用迹 $tr = tr_{F|\mathbb{F}_q}$ 得到。

投影到 $m$ 个内坐标之一。我们于是得到空间 $\mathbb{F}_q^n$ 和 $F^n$。$F^n$ 的元素可由次数 $< n$ 的一元多项式 $p(X) \in F[X]$ 唯一描述，其中由 $p(X)$ 定义的码字为求值 $ev(p(X)) = (p(\alpha^i))$，$i = 0,\ldots,n-1$。对每个内坐标做此操作，我们看到 $V_{m,F}$ 的元素可由多项式 $p_j(X) \in F[X]$ 的 $n$-元组 $(p_1(X),\ldots,p_m(X))$ 唯一描述，其中次数 $< n$，对应的码字为求值 $ev(p_1(X),\ldots,p_m(X)) = (p_1(\alpha^i),p_2(\alpha^i),\ldots,p_m(\alpha^i))_i$（$m$-元组的 $n$-元组，每个 $nm$ 个分量都在 $F$ 中）。

考虑伽罗瓦群 $G = Gal(F|\mathbb{F}_q)$（阶为 $r$ 的循环群）及其在 $\mathbb{Z}/n\mathbb{Z}$ 上的轨道，即分圆陪集。我们将 $\mathbb{Z}/n\mathbb{Z}$ 的元素解释为循环群 $W$ 元素描述中 $\alpha$ 的指数。对每个次数 $< n$ 的多项式 $p(X) \in F[X]$，考虑出现在 $p(X)$ 中的单项式的指数以及它们在分圆陪集上的分布。

### 18.16 Definition.
设 $\mathcal{P}$ 为 $F[X]$ 中次数 $< n$ 的多项式空间。则 $\mathcal{P}$ 是 $n$ 维 $F$ 向量空间。设 $A \subseteq \mathbb{Z}/n\mathbb{Z}$ 为指数集合。$F$ 向量空间 $\mathcal{P}(A)$ 由次数 $< n$ 且所有单项式次数都在 $A$ 中的多项式 $\in F[X]$ 组成。$A$ 的伽罗瓦闭包 $\tilde{A}$ 是与 $A$ 非平凡相交的所有分圆陪集的并。

注意 $\mathcal{P}(A)$ 是维数为 $|A|$ 的 $F$ 向量空间，且与 $ev(\mathcal{P}(A)) \subset V_{1,F}$ 同构。定义 18.16 的术语由明显事实所证实，即码 $ev(\mathcal{P}(A)) \subset V_{1,F} = F^n$ 的伽罗瓦闭包是 $ev(\mathcal{P}(\tilde{A}))$。

## Linear cyclic codes (case $m = 1$)
我们有 $\mathcal{P} = \oplus_Z \mathcal{P}(Z)$，其中 $Z$ 在分圆陪集上变化，对应地 $V_{1,F} = F^n = \oplus_Z ev(\mathcal{P}(Z))$。由于 $ev(\mathcal{P}(Z))$ 是伽罗瓦闭的，我们也有 $V_1 = \mathbb{F}_q^n = \oplus tr(ev(\mathcal{P}(Z)))$ 且 $dim_{\mathbb{F}_q}(tr(ev(\mathcal{P}(Z)))) = dim_F(ev(\mathcal{P}(Z))) = |Z|$。设 $V_1(Z) = tr(ev(\mathcal{P}(Z)))$。我们的首要任务是在 $V_1$ 中识别不可约 $W$ 子模（不可约循环码）。
