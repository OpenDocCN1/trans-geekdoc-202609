

$\mathcal{H}_k(h)$：对 $1 \le \ell \le k$，由 $\mathcal{H}_k(e, f, g)$ 可知
$$
v_j^{k,\ell}/n = \langle h^j, m^\ell \rangle_n - b_\ell \langle m^{j-1}, m^{\ell-1} \rangle_n \xrightarrow{c} \bar{b}_\ell \bar{\mathbf{T}}_{j,\ell} - \bar{b}_\ell \bar{\mathbf{T}}_{j,\ell} = 0
$$
对所有 $1 \le j \le k$ 成立。对于 $\ell = 0$，根据定义有 $m^{-1} = 0$，因此由 $\mathcal{H}_k(f)$ 的第二部分可知，对所有 $1 \le j \le k$，$v_j^{k,0}/n = \langle h^j, m^0 \rangle_n \xrightarrow{c} 0$。

$\mathcal{H}_k(i)$：回顾 (A.4) 得知 $\alpha^k = (M_k^\top M_k/n)^+ (M_k^\top m^k/n) \in \mathbb{R}^k$。由 $\mathcal{H}_k(e)$ 可知，对所有 $1 \le j, \ell \le k$，
$(M_k^\top M_k/n)_{j\ell} = \langle m^{j-1}, m^{\ell-1} \rangle_n \xrightarrow{c} \bar{\mathbf{T}}_{j,\ell}$ 且 $(M_k^\top m^k/n)_j = \langle m^{j-1}, m^k \rangle_n \xrightarrow{c} \bar{\mathbf{T}}_{j,k+1}$。按第 A.4 节的记号，这意味着 $M_k^\top m^k/n \xrightarrow{c} \bar{\mathbf{T}}^{[k],k+1} \in \mathbb{R}^k$ 且 $M_k^\top M_k/n \xrightarrow{c} \bar{\mathbf{T}}^{[k]} \in \mathbb{R}^{k \times k}$。在 (A4) 下，引理 2.2 保证 $\bar{\mathbf{T}}^{[k]}$ 为正定，从而可逆，我们现在应用完全收敛的连续映射定理（引理 B.2）推导出
$$
\alpha^k = (M_k^\top M_k/n)^+ (M_k^\top m^k/n) \xrightarrow{c} (\bar{\mathbf{T}}^{[k]})^{-1} \bar{\mathbf{T}}^{[k],k+1} = \bar{\alpha}^k,
$$
如 (A.14) 所定义。

$\mathcal{H}_k(j)$：回顾 (A.4) 以及第 A.2 节开头的定义，我们可以写成
$$
\|\hat{m}^k\|_n^2 = \|P_k^\perp m^k\|_n^2 = \|m^k\|_n^2 - \|P_k m^k\|_n^2
$$
$$
= \|m^k\|_n^2 - (\alpha^k)^\top (M_k^\top M_k/n) \alpha^k.
$$
现在，由 $\mathcal{H}_k(e)$ 得 $\|m^k\|_n^2 \xrightarrow{c} \bar{\mathbf{T}}_{k+1,k+1} = \tau_{k+1}^2$ 且 $M_k^\top M_k/n \xrightarrow{c} \bar{\mathbf{T}}^{[k]} \in \mathbb{R}^{k \times k}$，且由 $\mathcal{H}_k(i)$ 得 $\alpha^k \xrightarrow{c} \bar{\alpha}^k \in \mathbb{R}^k$，所以
$$
\|\hat{m}^k\|_n^2 = \|m^k\|_n^2 - (\alpha^k)^\top (M_k^\top M_k/n) \alpha^k \xrightarrow{c} \bar{\mathbf{T}}_{k+1,k+1} - (\bar{\alpha}^k)^\top \bar{\mathbf{T}}^{[k]} \bar{\alpha}^k = \tau_{k+1}^2,
$$
如 (A.15) 所定义。

$\mathcal{H}_{k+1}(a)$：令 $R_{n1}, \dots, R_{n5}$ 为定义 (A.22) 中 $\Delta^{k+1} \equiv \Delta^{k+1}(n) \in \mathbb{R}^n$ 的各个分量（按出现顺序）。要证明 $\|\Delta^{k+1}\|_{n,r} \xrightarrow{c} 0$，只需证明对 $s=1,\dots,5$ 有 $\|R_{ns}\|_{n,r} \xrightarrow{c} 0$。首先观察，由于由 $\mathcal{H}_k(i)$ 得 $\alpha^k \xrightarrow{c} \bar{\alpha}^k \in \mathbb{R}^k$，且由 $\mathcal{H}_k(b)$ 得对所有 $1 \le \ell \le k$ 有 $\|h^\ell\|_{n,r} = O_c(1)$，故
$\|R_{n1}\|_{n,r} \le \sum_{\ell=1}^k |\alpha_\ell^k - \bar{\alpha}_\ell^k| \|h^\ell\|_{n,r} = \sum_{\ell=1}^k o_c(1) O_c(1) = o_c(1)$。
至于 $R_{n2}$，由 $\mathcal{H}_k(e)$ 可知，对所有 $1 \le j, \ell \le k$ 有 $(M_k^\top M_k/n)_{j\ell} = \langle m^{j-1}, m^{\ell-1} \rangle_n \xrightarrow{c} \bar{\mathbf{T}}_{j,\ell}$，故 $M_k^\top M_k/n \xrightarrow{c} \bar{\mathbf{T}}^{[k]} \in \mathbb{R}^{k \times k}$，且由引理 2.2 该矩阵正定。我们现在可应用完全收敛的连续映射定理（引理 B.2）推导出 $(M_k^\top M_k/n)^+ \xrightarrow{\text{c}} (\bar{\mathbf{T}}^{[k]})^{-1}$；类似论证见上文 $\mathcal{H}_k(i)$。由 $\mathcal{H}_k(h)$ 可知，对所有 $0 \le \ell \le k$ 有 $v^{k,\ell}/n \xrightarrow{\text{c}} 0 \in \mathbb{R}^k$，故
$$
\tilde{w}^k \equiv \tilde{w}^k(n) := (M_k^\top M_k)^+ \left( v^{k,k} - \sum_{\ell=1}^k \alpha_\ell^k v^{k,\ell-1} \right) \xrightarrow{\text{c}} 0,
$$
（严格而言由完全收敛的斯卢茨基定理，引理 B.2）。由于由 $\mathcal{H}_k(b)$ 得对 $1 \le \ell \le k$ 有 $\|m^{\ell-1}\|_{n,r} = O_c(1)$，故 $\|R_{n2}\|_{n,r} = \|M_k\tilde{w}^k\|_{n,r} \le \sum_{\ell=1}^k |\tilde{w}_\ell^k| \|m^{\ell-1}\|_{n,r} = \sum_{\ell=1}^k o_c(1) O_c(1) = o_c(1)$。

接下来考虑 $R_{n3}$，引入 $\xi_1, ..., \xi_k \overset{\text{iid}}{\sim} N(0,1)$，由引理 A.18 可知，对每个 $n > k$，$\|P_k \tilde{Z}^{k+1}\|_{n,r}$ 在随机意义上被 $\sum_{i=1}^k |\xi_i| / n^{1/r}$ 支配。由示例 1(a)，$\sum_{i=1}^k |\xi_i| / n^{1/r} \le k \max_{1 \le i \le k} |\xi_i| / n^{1/r} = o_c(1)$，故 $\|P_k \tilde{Z}^{k+1}\|_{n,r} \xrightarrow{\text{c}} 0$。由于由 $\mathcal{H}_k(j)$ 得 $\|\dot{m}^k\|_n \xrightarrow{\text{c}} \dot{\tau}_{k+1} \in (0, \infty)$，推得 $\|R_{n3}\|_{n,r} = \|\dot{m}^k\|_n \|P_k \tilde{Z}^{k+1}\|_{n,r} = o_c(1)$。

对于剩余分量 $R_{n4}$ 和 $R_{n5}$，论证与证明 $\mathcal{H}_1(a)$ 中的类似。回顾 $(\tilde{Z}^{k+1}, \dot{\zeta}^{k+1}) \equiv (\dot{Z}^{k+1}(n), \dot{\zeta}^{k+1}(n)) \sim N_n(0, I_n) \otimes N(0, 1/n)$。引入 $\zeta \sim N(0, 1)$，由示例 1(a) 有 $|\dot{\zeta}^{k+1}| \stackrel{d}{=} n^{-1/2} |\zeta| \xrightarrow{\text{c}} 0$，且由引理 B.12 和命题 1.2 有 $\|\dot{Z}^{k+1}\|_{n,r} = (n^{-1} \sum_{i=1}^n |\dot{Z}_i^{k+1}|^r)^{1/r} \xrightarrow{\text{c}} \mathbb{E}(|\zeta|^r)^{1/r} \in (0, \infty)$。由 $\mathcal{H}_k(j)$ 有 $\|\dot{m}^k\|_n - \dot{\tau}_{k+1} = o_c(1)$。此外，由 $\mathcal{H}_k(i)$ 得 $\alpha^k = \bar{\alpha}^k + o_c(1) = O_c(1)$，且由 $\mathcal{H}_k(b)$ 得对 $0 \le \ell \le k$ 有 $\|m^\ell\|_{n,r} = O_c(1)$，故由 (A.4) 可知
$$
\| \dot{m}^k \|_{n,r} = \|(I - P_k) m^k\|_{n,r} \le \|m^k\|_{n,r} + \sum_{\ell=1}^k |\alpha_\ell^k| \|m^{\ell-1}\|_{n,r}
$$
$$
= O_c(1) + \sum_{\ell=1}^k O_c(1) O_c(1) = O_c(1).
$$

将上述内容综合起来，可知
$$
\| R_{n4} \|_{n,r} + \| R_{n5} \|_{n,r} = \|\dot{m}^k\|_n - \dot{\tau}_{k+1} \|\dot{Z}^{k+1}\|_{n,r} + |\dot{\zeta}^{k+1}| \|\dot{m}^k\|_{n,r}
$$
$$
= o_c(1) O_c(1) + o_c(1) O_c(1) = o_c(1).
$$

我们已经证明了对 $s=1,\dots,5$ 有 $\|R_{ns}\|_{n,r} \xrightarrow{\text{c}} 0$，故 $\|\Delta^{k+1}\|_{n,r} \le \sum_{s=1}^5 \|R_{ns}\|_{n,r} \xrightarrow{\text{c}} 0$。

$\mathcal{H}_{k+1}(b)$：由归纳假设 $\mathcal{H}_k(b)$ 可知，对所有 $1 \le j \le k$ 有 $\|h^j\|_{n,r} = O_c(1)$，且对所有 $0 \le j \le k$ 有 $\|m^j\|_{n,r} = O_c(1)$。现在取 $j = k+1$。对每个整数 $n > k$，由命题 A.11 中的 (A.7) 和 (A.21) 可知
$$
h^{k+1}(n) \stackrel{d}{=}|_{\mathcal{S}_k} h^{k+1,k}(n) = \tilde{h}^{k+1}(n) + \Delta^{k+1}(n)
$$
$$
= \sum_{\ell=1}^k \bar{\alpha}_\ell^k h^\ell(n) + \bar{\tau}_{k+1} \tilde{Z}^{k+1}(n) + \Delta^{k+1}(n), \quad \text{(A.38)}
$$
其中确定的 $\bar{\alpha}^k \in \mathbb{R}^k$ 取自 (A.14)，且 $\tilde{Z}^{k+1} \equiv \tilde{Z}^{k+1}(n) \sim N_n(0, I_n)$ 与 $\mathcal{S}_k \equiv \mathcal{S}_k(n) = \sigma(\gamma, m^0, h^1, \dots, h^k)$ 独立。然后由 $\mathcal{H}_{k+1}(a)$ 得 $\|\Delta^{k+1}\|_{n,r} = o_c(1)$，且 $\|\tilde{Z}^{k+1}\|_{n,r} = O_c(1)$，如上文 $\mathcal{H}_{k+1}(a)$ 证明的最后部分所示。由此及 $\mathcal{H}_k(b)$ 可得
$$
\|h^{k+1}\|_{n,r} \stackrel{d}{=} \|h^{k+1,k}\|_{n,r} \le \sum_{\ell=1}^k |\bar{\alpha}_\ell^k| \|h^\ell\|_{n,r} + \|\Delta^{k+1}\|_{n,r}
$$
$$
= O_c(1) + o_c(1) = O_c(1).
$$

此外，取 $L' > 0$ 使得 $f_{k+1}$ 为 $L'$-Lipschitz，我们可以如同证明 $\mathcal{H}_1(b)$ 中一样论证，推导出
$$
\|m^{k+1}\|_{n,r} = \|f_{k+1}(h^{k+1}, \gamma)\|_{n,r} \le |f_{k+1}(0,0)|
$$
$$
+ L'(\|h^{k+1}\|_{n,r} + \|\gamma\|_{n,r}) = O_c(1).
$$

$\mathcal{H}_{k+1}(c)$：我们再次利用分配相等 (A.38)，结合引理 B.6(c) 意味着，对每个整数 $n > k$ 有 $(\gamma, h^1, \dots, h^k, h^{k+1}) \stackrel{d}{=}|_{\mathcal{S}_k} (\gamma, h^1, \dots, h^k, h^{k+1,k})$。因此，对任何固定的 $\psi \in \text{PL}_{k+2}(r)$，有 $n^{-1} \sum_{i=1}^n \psi(h_i^1, \dots, h_i^k, h_i^{k+1}, \gamma_i) \stackrel{d}{=} n^{-1} \cdot \sum_{i=1}^n \psi(h_i^1, \dots, h_i^k, h_i^{k+1,k}, \gamma_i) =: T_n$，对每个这样的 $n$ 成立，故只需证明 $T_n \rightarrow^\mathcal{C} \mathbb{E}(\psi(\bar{G}_1, \dots, \bar{G}_k, \bar{G}_{k+1}, \bar{\gamma}))$。我们将 $T_n$ 分解为
$$
\frac{1}{n} \sum_{i=1}^n \psi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) + \frac{1}{n} \sum_{i=1}^n \{ \psi(h_i^1, \dots, h_i^k, h_i^{k+1,k}, \gamma_i)
$$
$$
- \psi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) \} =: T_{n1} + T_{n2} \quad \text{(A.39)}
$$
对每个 $n > k$，并试图通过模仿和扩展证明 $\mathcal{H}_1(c)$ 中的类似论证，建立 $T_{n1} \rightarrow^\mathcal{C} \mathbb{E}(\psi(\bar{G}_1, \dots, \bar{G}_k, \bar{G}_{k+1}, \bar{\gamma}))$ 和 $T_{n2} \rightarrow^\mathcal{C} 0$。

