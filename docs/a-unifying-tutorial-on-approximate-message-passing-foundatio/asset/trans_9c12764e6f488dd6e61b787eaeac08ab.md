
```
=^d \, | \mathcal{S}_k \sum_{\ell=1}^k \alpha_{\ell k} h^\ell + \| \hat{m}^k \|_n (P_{k\perp} \bar{Z}^{k+1}) + \tilde{\zeta}^{k+1} \hat{m}^k + M_k(M_k^\top M_k)\\ + \left( v^{k,k} - \sum_{\ell=1}^k \alpha_\ell^k v^{k, \ell-1} \right)\\ =: h^{k+1, k},\tag{A.7}
```

其中 $v^{k,\ell} \equiv v^{k,\ell}(n) := H_k^\top m^\ell - b_\ell M_k^\top m^{\ell-1} \in \mathbb{R}^k$ 对于 $\ell \in \{0, \dots, k\}$。

命题 A.11 证明的关键在于建立 (A.6)，它刻画了给定 $\mathcal{S}_k$ 下 $W$ 的条件分布。从直觉上看，将此视为对 $W$ 关于*线性约束* $Wm^0 = y^0, \dots, Wm^{k-1} = y^{k-1}$ 进行条件化所得是有帮助的。然而，由于 $m^1, \dots, m^{k-1}$ 是随机的且依赖于 $W$，这种启发式论证本身不足以构成命题 A.11 的正式证明。为了方便对技术细节感兴趣的读者，我们在下方给出更详细的解释。

注意，对于固定的 $k \in \mathbb{N}$ 和确定的 $y, a^0, a^1, \dots, a^k \in \mathbb{R}^n$，事件 $\Omega_{y, a^0, \dots, a^k} := \{ \gamma = y, m^0 = a^0, h^1 = a^1, \dots, h^k = a^k \}$ 可以表示为

```
\Omega_{y, a^0, \dots, a^k} = \{ \gamma = y, m^0 = a^0, W t^j = z^j \text{ for all } 0 \le j \le k-1 \}\\ = \{ \gamma = y, m^0 = a^0, W T_k = Z_k \},\tag{A.8}
```

其中 $t^j := f_j(a^j, y) \in \mathbb{R}^n$ 且 $z^j := a^{j+1} + \langle f_j'(a^j, y) \rangle_n f_{j-1}(a^{j-1}, y)$ 对于 $0 \le j \le k-1$，而 $T_k := (t^0 \ t^1 \ \dots \ t^{k-1})$ 和 $Z_k := (z^0 \ z^1 \ \dots \ z^{k-1})$ 是固定的 $n \times k$ 矩阵。现在对于 $W \sim \text{GOE}(n)$ 以及任何固定的 $T \in \mathbb{R}^{n \times k}$（秩为 $p$），我们可以通过写出 $W$ 给定 $WT$ 的条件分布，方法是

```
W = WP + (P + P^\perp)^\top W P^\perp = WP + (WP)^\top P^\perp + P^\perp W P^\perp,\tag{A.9}
```

其中 $P := TT^+$ 和 $P^\perp := I_n - TT^+$ 分别表示在 $\text{Im}(T)$ 和 $\text{Im}(T)^\perp$ 上的正交投影。(A.9) 右侧的前两项是 $WP = (WT)T^+$（因此也是 $WT$）的可测函数，而第三项 $P^\perp W P^\perp$ 与 $WT$ 独立。因此，$\mathbb{E}(W \mid WT) = WP + (WP)^\top P^\perp$。此外，我们可以写出 $P^\perp = \tilde{U} \tilde{U}^\top$，其中 $\tilde{U}$ 的列构成 $\text{Im}(T)^\perp$ 的一组标准正交基，因此 $P^\perp W P^\perp = \tilde{U}(\tilde{U}^\top W \tilde{U})\tilde{U}^\top$，且 $\tilde{U}^\top W \tilde{U} \sim \text{GOE}(n - p)$ 与 $WT$ 独立。对于 $Z \in \mathbb{R}^{n \times k}$，这使我们能够将“给定 $WT = Z$ 时 $W$ 的条件分布”解释为

$ZT^\perp + (ZT^\perp)^\top P^\perp + \tilde{U}^\top W \tilde{U}$,

的分布，其中 $\tilde{W} \sim \text{GOE}(n - p)$。我们将此分布表示为 $\mathcal{L}_Z(T)$。

鉴于 (A.8) 以及 $W$ 与 $(m^0, \gamma)$ 在 (A0) 中独立的假设，启发式地论证如下很有诱惑力：

$W \mid \{\gamma = y, m^0 = a^0, h^1 = a^1, \dots, h^k = a^k\}$

\(\overset{d}{=} W \mid \{\gamma = y, m^0 = a^0, WT_k = Z_k\}\)

\(\overset{d}{=} W \mid \{WT_k = Z_k\} \sim \mathcal{L}_{Z_k}(T_k)\),

并以此得出结论：$W$ 在 $\mathcal{S}_k = \sigma(\gamma, m^0, h^1, \dots, h^k)$ 给定下具有（正则）条件分布 $\mathcal{L}_\omega \equiv \mathcal{L}_{Y_k(\omega)}(M_k(\omega))$，并注意对于 $\omega \in \Omega_{y, a^0, \dots, a^k}$，有 $M_k(\omega) = T_k$ 和 $Y_k(\omega) = Z_k$。然而，这种推理似乎涉及明确对潜在零概率事件进行条件化，且上述论证并未在形式上予以证明；有关相关风险，参见 Borel 悖论 (Dudley, 2002, pp. 350–351)。

如前所述，问题在于 $M_k$ 是随机的，且通常与 $W$ 不独立，而上一段中的分布断言依赖于 $T$ 是固定的这一事实。尽管如此，关键在于，$M_k$ 的随机性及其对 $W$ 的依赖性由于命题 A.8 中建立的条件独立性，结果并未造成不可调和的困难。由此结果可知 $\mathbb{E}(W \mid \mathcal{S}_k) = W P_k + (W P_k)^\top P_k^\perp$，因此命题 A.11 中的条件分布等式 (A.6) 及其证明中的分解 (A.11) 是 (A.9) 的适当类似物。

## A.3 第 A.2 节结果的证明

命题 A.8 证明中的一个关键成分是下面的引理 A.12，它扩展了 GOE($n$) 分布的正交不变性性质。给定一组有限的不相交可测空间 $(\mathcal{X}_1, \mathcal{A}_1), \dots, (\mathcal{X}_m, \mathcal{A}_m)$，我们将不相交并集 $\sqcup_{k=1}^m \mathcal{X}_k$ 配备 $\sigma$-代数 $\{\sqcup_{k=1}^m A_k : A_k \in \mathcal{A}_k \text{ for all } k\}$。

### 引理 A.12.

设 \(\mathcal{G} \subseteq \mathcal{F}\) 为一个子-\(\sigma\)-代数，并设 \(X : (\Omega, \mathcal{F}, \mathbb{P}) \to \sqcup_{k=1}^n \mathbb{R}^{k \times k}\) 为一个可测函数。假设 \(\Omega$ 存在分解为不相交事件 \(\Omega_1, \dots, \Omega_m \in \mathcal{G}$，使得对每个 \(k = 1, \dots, m$，映射 \(X$ 在 \(\Omega_k$ 上取值于 \(\mathbb{R}^{n_k \times n_k}$，且在 \(\Omega_k$ 上给定 \(\mathcal{G}$ 具有条件分布 \(\text{GOE}(n_k)$，其中 \(n_k \in \{1, \dots, n\}$ 为某个（确定性）值。此外，设 \(Q = (Q_1 \ Q_2) : (\Omega, \mathcal{F}, \mathbb{P}) \to \sqcup_{k=1}^n \mathbb{O}_k$ 为一个 \(\mathcal{G}$-可测函数，使得在每个事件 \(\Omega_k$ 上，映射 \(Q$ 取值于 \(\mathbb{O}_{n_k}$，且 \(Q_1, Q_2$ 分别具有 \(\ell_k$ 和 \(n_k - \ell_k$ 列，其中 \(\ell_k \in \{1, \dots, n_k - 1\}$ 为某个（确定性）值。那么，给定 \(\mathcal{G}$，我们有以下结论：

- (a) \(Q^\top X Q$ 在 \(\Omega_k$ 上给定 \(\mathcal{G}$ 具有条件分布 \(\text{GOE}(n_k)$，对每个 \(k = 1, \dots, m$ 成立；
- (b) \(Q_2^\top X Q_2$ 在 \(\Omega_k$ 上给定 \(\mathcal{G}$ 具有条件分布 \(\text{GOE}(n_k - \ell_k)$，对每个 \(k = 1, \dots, m$ 成立；
- (c) \(Q^\top X Q_1$ 和 \(Q_2^\top X Q_2$ 是条件独立的。

### 注释 A.13.

注意，如果 \(n_1 = \dots = n_m = n$，则在引理的第一个条件下，根据注释 B.4，$X$ 具有无条件分布 \(\text{GOE}(n)$ 且与 \(\mathcal{G}$ 独立。因此，在具有指导意义的特殊情况 \(m=1$ 和 \(1 \le \ell_1 < n = n_1$ 中，上述结果简化如下：假设 \(X \sim \text{GOE}(n)$ 且与 \(\mathcal{G}$ 独立，并且此外 \(Q = (Q_1 \ Q_2) : (\Omega, \mathcal{F}, \mathbb{P}) \to \mathbb{O}_n$ 是一个 \(\mathcal{G}$-可测映射，使得 \(Q_1, Q_2$ 分别具有 \(\ell_1$ 和 \(n - \ell_1$ 列。那么

- (a) \(Q^\top X Q \sim \text{GOE}(n)$ 且与 \(\mathcal{G}$ 独立；
- (b) \(Q_2^\top X Q_2 \sim \text{GOE}(n - \ell_1)$ 且与 \(\mathcal{G}$ 独立；
- (c) \(Q^\top X Q_1$ 和 \(Q_2^\top X Q_2$ 是独立的，并且在给定 \(\mathcal{G}$ 下也是条件独立的。

### 引理 A.12 的证明.

(a) 对 \(\ell = 1, \dots, n$，设 \(\mathcal{A}_\ell$ 和 \(\mathcal{B}_\ell$ 分别为 \(\mathcal{X}_\ell := \mathbb{R}^{\ell \times \ell}$ 和 \(\mathcal{Y}_\ell := \mathbb{O}_\ell$ 上的博雷尔 \(\sigma$-代数。定义 \(\phi_\ell : \mathcal{X}_\ell \times \mathcal{Y}_\ell \to \mathcal{X}_\ell$ 为 \(\phi_\ell(M, J) := J^\top M J$，并且对于 \(J \in \mathbb{O}_\ell$，设 \(\iota_J : \mathcal{X}_\ell \to \mathcal{X}_\ell \times \mathcal{Y}_\ell$ 为映射 \(M \mapsto (M, J)$。那么，GOE($\ell$) 的正交不变性性质可以重述为：对每个 \(J \in \mathbb{O}_\ell$，GOE($\ell$) = GOE($\ell) \circ (\phi_\ell \circ \iota_J)^{-1}$。因此，观察到在 \(\Omega_k$ 上 \(\phi_{n_k}(X, Q) = Q^\top X Q$，并将引理 B.6(b) 应用于 \(\phi_{n_k}$，我们可得 \(Q^\top X Q$ 在 \(\Omega_k$ 上给定 \(\mathcal{G}$ 具有条件分布 GOE($n_k$) ，如要求所示。

- (b) 对 \(k = 1, \dots, m$，设 \(\psi_k : \mathcal{X}_{n_k} \to \mathcal{X}_{n_k - \ell_k}$ 表示提取 \(n_k \times n_k$ 矩阵右下角 \((n_k - \ell_k) \times (n_k - \ell_k)$ 块的映射。那么，每当 \(W \sim \text{GOE}(n_k)$ 时，\(\psi_k(W) \sim \text{GOE}(n_k - \ell_k)$，因此对每个 \(J \in \mathbb{O}_{n_k}$，\(\text{GOE}(n_k - \ell_k) = \text{GOE}(n_k) \circ \psi_k^{-1} = \text{GOE}(n_k) \circ (\phi_{n_k} \circ \iota_J)^{-1} \circ \psi_k^{-1}$。故我们可以将引理 B.6(b) 应用于 \(\psi_k \circ \phi_{n_k}$，从而得出 \(Q_2^\top X Q_2$ 在 \(\Omega_k$ 上给定 \(\mathcal{G}$ 具有条件分布 GOE($n_k - \ell_k$) 。

- (c) 对 \(\omega \in \Omega$，设 \(P_\omega$、\(Q_\omega$ 和 \(R_\omega$ 分别表示给定 \(\mathcal{G}$ 下 \(Q^\top X Q_1$、\(Q_2^\top X Q_2$ 和 \((Q^\top X Q_1, Q_2^\top X Q_2)$ 的条件分布。对 \(k = 1, \dots, m$，设 \(\tilde{\psi}_k : \mathcal{X}_{n_k} \to \mathbb{R}^{n_k \times \ell_k}$ 表示提取 \(n_k \times n_k$ 矩阵前 \(\ell_k$ 列的映射。现在定义 \(\Psi_k : \mathcal{X}_{n_k} \to \mathbb{R}^{n_k \times \ell_k} \times \mathcal{X}_{n_k - \ell_k}$ 为 \(\Psi_k(M) := (\tilde{\psi}_k(M), \psi_k(M))$。那么，每当 \(W \sim \text{GOE}(n_k)$ 时，\(\tilde{\psi}_k(W)$ 和 \(\psi_k(W)$ 是独立的，因此 \(\text{GOE}(n_k) \circ \Psi_k^{-1} = (\text{GOE}(n_k) \circ \tilde{\psi}_k^{-1}) \otimes (\text{GOE}(n_k) \circ \psi_k^{-1})$。由于在 \(\Omega_k$ 上 \((Q^\top X Q_1, Q_2^\top X Q_2) = (\Psi_k \circ \phi_k)(X, Q)$，我们可以将引理 B.6(b) 应用于 \(\tilde{\psi}_k \circ \phi_{n_k}$、\(\psi_k \circ \phi_{n_k}$ 和 \(\Psi_k \circ \phi_{n_k}$，从而推断对所有 \(\omega \in \Omega_k$ 有 \(R_\omega = P_\omega \otimes Q_\omega$。由于 \(k \in \{1, \dots, m\}$ 任意，我们得出对所有 \(\omega \in \Omega = \sqcup_{k=1}^m \Omega_k$ 有 \(R_\omega = P_\omega \otimes Q_\omega$，这与引理 B.9(b) 一起蕴含 \(Q^\top X Q_1$ 和 \(Q_2^\top X Q_2$ 在给定 \(\mathcal{G}$ 下是条件独立的。\(\square\)

### 命题 A.8 的证明.

我们对 \(k \in \{0, 1, \dots, n-1\}$ 进行归证。当 \(k=0$ 时，情况平凡，因为根据假设 \(W \sim \text{GOE}(n)$ 且与 \((m^0, \gamma)$ 独立。对于一般的 \(1 \le k \le n-1$（当 \(n \ge 2$ 时），设 \(\check{U}_{k-1}$ 为任意一个 \(\mathcal{S}_{k-2}$-可测的 \(n \times (n - r_{k-1})$ 矩阵，其列构成 \(V_{k-1}$ 的一组标准正交基，并固定一个任意的 \(\mathcal{S}_{k-1}$-可测的 \(n \times (n - r_k)$ 矩阵 \(\check{U}_k$，其列构成 \(V_k$ 的一组标准正交基。此外，设 \(E \equiv E_{k-1}$ 为事件 \(\{\check{m}^{k-1} \neq 0\} = \{r_k = r_{k-1} + 1\} \in \mathcal{S}_{k-1}$，并注意 \(n - r_{k-1} \ge n - k + 1 \ge 2$。

接下来，定义一个 \(\mathcal{S}_{k-1}$-可测的 \(n \times (n - r_{k-1})$ 矩阵 \(\check{U}$，在 \(E$ 上令 \(\check{U} := (\check{m}^{k-1} \check{U}_k)$，在 \(E^c = \{\check{m}^{k-1} = 0\}$ 上令 \(\check{U} := \check{U}_k$。令 \(\check{U}$ 为
