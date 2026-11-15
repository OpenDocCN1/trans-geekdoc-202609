

在 $\mathcal{S}_k$ 条件下服从相同分布。最后，回顾 $\dot{m}^k = (I - P_k) m^k = m^k - \sum_{\ell=1}^k \alpha_\ell^k m^{\ell-1}$，且对所有 $0 \le \ell \le k-1$，根据投影矩阵 $P_k = M_k M_k^+$ 的定义，有 $(M_k^+)^\top M_k^\top m^\ell = P_k^\top m^\ell = P_k m^\ell = m^\ell$。由此可得 $P_k^\perp (\tilde{\zeta}^{k+1} m^k) = \tilde{\zeta}^{k+1} m^k$ 且

$$
(M_k^+)^\top H_k^\top \dot{m}^k = (M_k^+)^\top \left( H_k^\top m^k - \sum_{\ell=1}^k \alpha_\ell^k H_k^\top m^{\ell-1} \right),
$$
$$
b_k m^{k-1} - \sum_{\ell=1}^k b_{\ell-1} \alpha_\ell^k m^{\ell-2}
$$
$$
= (M_k^+)^\top \left( b_k M_k^\top m^{k-1} - \sum_{\ell=1}^k \alpha_\ell^k b_{\ell-1} M_k^\top m^{\ell-2} \right).
$$

因此，由于 $(M_k^+)^\top = M_k (M_k^\top M_k)^+$，(A.7) 中定义的随机变量 $h^{k+1,k}$ 与 (A.13) 中的相同，故由 (A.12) 得出 $h^{k+1} \stackrel{d}{=} |_{\mathcal{S}_k} h^{k+1,k}$，正如所要求的。

## A.4 第 2.1 节中 AMP 主定理的证明概要

回顾定理 2.3 中极限协方差矩阵 $\bar{\mathbf{T}}^{[k]} \in \mathbb{R}^{k \times k}$ 的定义 (2.6)，我们首先概述构造一个单随机序列 $(\bar{G}_k : k \in \mathbb{N})$ 的标准方法，使得对每个 $k$ 都有 $(\bar{G}_1, \dots, \bar{G}_k) \sim N_k(0, \bar{\mathbf{T}}^{[k]})$。令 $\bar{\mathbf{T}}^{[k], k+1} := (\bar{\mathbf{T}}_{1, k+1}, \dots, \bar{\mathbf{T}}_{k, k+1}) \in \mathbb{R}^k$ 且

$$
\bar{\alpha}^k \equiv (\bar{\alpha}_1^k, \dots, \bar{\alpha}_k^k) := (\bar{\mathbf{T}}^{[k]})^{-1} \bar{\mathbf{T}}^{[k], k+1} \in \mathbb{R}^k \quad (A.14)
$$

对每个 $k \in \mathbb{N}$，后者定义良好，因为根据引理 2.2，在 (A4) 下 $\bar{\mathbf{T}}^{[k]}$ 是正定的。可以轻松验证，若 $(G_1, \dots, G_{k+1}) \sim N_{k+1}(0, \bar{\mathbf{T}}^{[k+1]})$，则 $G_{[k]} := (G_1, \dots, G_k)$ 与 $\xi_{k+1} := G_{k+1} - G_{[k]}^\top \bar{\alpha}^k = G_{k+1} - \sum_{\ell=1}^k \bar{\alpha}_\ell^k G_\ell$ 不相关，因此独立。这意味着

$$
G_{[k]}^\top \bar{\alpha}^k = \sum_{\ell=1}^k \bar{\alpha}_\ell^k G_\ell = \mathbb{E}(G_{k+1} \mid G_1, \dots, G_k)
$$

对每个 $k$ 均成立。此外，由于 $\bar{\mathbf{T}}^{[k+1]} = \text{Cov}(G_1, \dots, G_{k+1})$ 是正定的，且 $\xi_{k+1}$ 是 $G_1, \dots, G_{k+1}$ 的一个非平凡线性组合，故在 (A4) 下有

$$
0 < \mathrm{Var}(\xi_{k+1}) = \mathrm{Var}(\xi_{k+1}|G_1,\dots,G_k) = \mathrm{Var}(G_{k+1}|G_1,\dots,G_k) = \mathrm{Var}(G_{k+1}) - \mathrm{Var}(G_{[k]}^\top \bar{\alpha}^k) = \bar{\mathbf{T}}_{k+1,k+1} - (\bar{\alpha}^k)^\top \bar{\mathbf{T}}^{[k]} \bar{\alpha}^k = \tau_{k+1}^2 - (\bar{\mathbf{T}}^{[k],k+1})^\top (\bar{\mathbf{T}}^{[k]})^{-1} \bar{\mathbf{T}}^{[k],k+1} =: \dot{\tau}_{k+1}^2
$$

对 \( k \in \mathbb{N} \)，故 \( \dot{\tau}_{k+1} \in (0, \infty) \) 满足 \( \dot{\tau}_{k+1}^2 = \mathrm{Var}(\xi_{k+1}) \le \mathrm{Var}(G_{k+1}) = \tau_{k+1}^2 \)。现在令 \( \bar{G}_1 \sim N(0, \tau_1^2) \)，并对 \( k \in \mathbb{N} \) 归纳定义

$$
\bar{G}_{k+1} := \sum_{\ell=1}^k \bar{\alpha}_\ell^k \bar{G}_\ell + \dot{\tau}_{k+1} \dot{\zeta}_{k+1},
$$

其中 \( \dot{\zeta}_{k+1} \sim N(0, 1) \) 与 \( (\bar{G}_1, \dots, \bar{G}_k) $ 独立。于是 \( (\bar{G}_k : k \in \mathbb{N}) \) 是一个随机序列，对每个 $k$ 均有 \( (\bar{G}_1, \dots, \bar{G}_k) \sim N_k(0, \bar{\mathbf{T}}^{[k]}) \)，正如所期望的。有了上述定义，我们在此记录一些关键恒等式。根据 (2.6)，我们当然有

$$
\mathrm{Cov}(\bar{G}_k, \bar{G}_\ell) = \mathbb{E}(\bar{G}_k \bar{G}_\ell) = \bar{\mathbf{T}}_{k,\ell} =
\begin{cases}
\tau_1^2 & \text{if } k = \ell = 1 \\
\mathbb{E}(F_0(\bar{\gamma}) \cdot f_{k-1}(\bar{G}_{k-1}, \bar{\gamma})) & \text{if } k > \ell = 1 \\
\mathbb{E}(f_{\ell-1}(\bar{G}_{\ell-1}, \bar{\gamma}) \cdot f_{k-1}(\bar{G}_{k-1}, \bar{\gamma})) & \text{if } k \ge \ell \ge 2,
\end{cases}
$$

其中 \( f_1, f_2, \dots $ 是 AMP 递推 (2.1) 中的 Lipschitz 函数，而 $\tau_1$ 和 $F_0$ 分别如 (A2) 和 (A3) 所示。这一事实是我们在主定理归纳证明中的一个重要断言（下文提议 A.16(e)）的基础。此外，对任意 $k, \ell \in \mathbb{N}$ 及任何带弱导数 $\varphi'$ 的 Lipschitz 函数 $\varphi : \mathbb{R} \to \mathbb{R}$，有

$$
\mathbb{E}(\bar{G}_k \varphi(\bar{G}_\ell)) = \mathbb{E}(\varphi'(\bar{G}_\ell))\mathbb{E}(\bar{G}_k \bar{G}_\ell) = \mathbb{E}(\varphi'(\bar{G}_\ell))\bar{\mathbf{T}}_{k,\ell}.
$$

这源自 Stein 引理，其一般表述见 Tsybakov (2009, Lemma 3.6) 和引理 A.20。

### 引理 A.15 (Stein 引理)

若 $Z \sim N(0, \sigma^2)$ 且 $\varphi : \mathbb{R} \to \mathbb{R}$ 是一条绝对连续函数，其弱导数为 $\varphi'$，且 $\varphi'(Z)$ 可积，则 $\mathbb{E}(Z\varphi(Z)) = \sigma^2 \mathbb{E}(\varphi'(Z))$。

事实上，(A.18) 中的第一个等式源自引理 A.15，只需写出 $\bar{G}_k = (\bar{\mathbf{T}}_{k,\ell}/\bar{\mathbf{T}}_{\ell,\ell})\bar{G}_{\ell} + \xi_{k\ell}$，其中 $\xi_{k\ell}$ 均值为零且与 $\bar{G}_{\ell}$ 独立，因而 $\mathbb{E}(\xi_{k\ell}\varphi(\bar{G}_{\ell})) = 0$。

我们在 (2.1) 中对函数序列 $(f_k)_{k=0}^\infty$ 和 $(f'_k)_{k=0}^\infty$ 的选择确保，对任意固定 $y \in \mathbb{R}$，可以在 (A.18) 中取 $\varphi = f_{\ell}(\cdot, y)$ 和 $\varphi' = f'_{\ell}(\cdot, y)$，从而对 $k, \ell \in \mathbb{N}$ 有 $\mathbb{E}(\bar{G}_k f_{\ell}(\bar{G}_{\ell}, y)) = \mathbb{E}(f'_{\ell}(\bar{G}_{\ell}, y))\mathbb{E}(\bar{G}_k\bar{G}_{\ell})$。由此（以及引理 B.7）可推出，若 $\bar{\gamma} \sim \pi$ 与 $\bar{G}_1, \bar{G}_2, \dots$ 独立，则

$$
\mathbb{E}(\bar{G}_k f_{\ell}(\bar{G}_{\ell}, \bar{\gamma})) = \mathbb{E}(f'_{\ell}(\bar{G}_{\ell}, \bar{\gamma}))\mathbb{E}(\bar{G}_k\bar{G}_{\ell}) = \bar{b}_{\ell} \bar{\mathbf{T}}_{k,\ell} \quad (A.19)
$$

对所有 $k, \ell \in \mathbb{N}$ 均成立，其中 $\bar{b}_{\ell} := \mathbb{E}(f'_{\ell}(\bar{G}_{\ell}, \bar{\gamma}))$。这构成下文提议 A.16 中断言 (f) 的一部分。

为了完成下文主要推导所需的技术准备，我们将建立 (A.16) 中高斯变量 $\bar{G}_{k+1} \sim N(0, \tau_{k+1}^2)$ 与上面第 A.2 节中 (A.5) 和 (A.7) 所定义的随机向量 $h^{k+1,k} \equiv h^{k+1,k}(n)$（对 $n \in \mathbb{N}$ 和 $k \in \{0, 1, \dots, n-1\}$）之间更明确的联系。对于这样的 $n$ 和 $k$，提议 A.11 断言 $h^{k+1}(n)$ 和 $h^{k+1,k}(n)$ 在 $\mathcal{S}_k \equiv \mathcal{S}_k(n) = \sigma(\gamma_j, m^0, h^j : 1 \le j \le k)$ 条件下服从相同分布，我们现在写 $h^{k+1,k}(n) = \tilde{h}^{k+1}(n) + \Delta^{k+1}(n)$，其中

$$
\tilde{h}^1 \equiv \tilde{h}^1(n) := \tau_1 \tilde{Z}^1 \quad \text{and} \quad \Delta^1 \equiv \Delta^1(n) := (\|m^0\|_n - \tau_1)\tilde{Z}^1 + \tilde{\zeta}^1 m^0, \quad (A.20)
$$

和

$$
\tilde{h}^{k+1} \equiv \tilde{h}^{k+1}(n) := \sum_{\ell=1}^k \bar{\alpha}_{\ell}^k h^\ell + \dot{\tau}_{k+1} \tilde{Z}^{k+1}, \quad (A.21)
$$

$$
\Delta^{k+1} \equiv \Delta^{k+1}(n) := \sum_{\ell=1}^k (\alpha_{\ell}^k - \bar{\alpha}_{\ell}^k) h^\ell + M_k(M_k^{\top} M_k)^+ \left(v^{k,k} - \sum_{\ell=1}^k \alpha_{\ell}^k v^{k,\ell-1}\right) - \|\tilde{m}^k\|_n(P_k \tilde{Z}^{k+1}) + (\|\tilde{m}^k\|_n - \dot{\tau}_{k+1})\tilde{Z}^{k+1} + \tilde{\zeta}^{k+1}\tilde{m}^k. \quad (A.22)
$$

回顾 $(\tilde{Z}^{k+1}, \tilde{\zeta}^{k+1}) \equiv (\tilde{Z}^{k+1}(n), \tilde{\zeta}^{k+1}(n)) \sim N_n(0, I_n) \otimes N(0, 1/n)$ 在提议 A.11 中被取为与 $\mathcal{S}_k \equiv \mathcal{S}_k(n)$ 独立，其中我们还定义了 $\alpha^k \equiv \alpha^k(n)$ 和 $v^{k,\ell} \equiv v^{k,\ell}(n)$，对 $0 \le \ell \le k$。

在上述分解中，我们在 (A.21) 中定义了 $\tilde{h}^{k+1}$ 以模仿 (A.16) 中极限高斯变量 $\bar{G}_{k+1}$ 的表达式。

