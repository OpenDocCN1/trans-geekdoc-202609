

对比 (A.7) 和 (A.21) 中分别定义的 $h^{k+1,k}$ 和 $\bar{h}^{k+1}$，其中 $k \in \{0, 1, \dots, n-1\}$，我们看到 (A.7) 中的随机量 $\alpha^k$ 和 $\|m^k\|_n$ 在 (A.21) 中分别被来自 (A.14) 和 (A.15) 的确定性量 $\bar{\alpha}^k \in \mathbb{R}^k$ 和 $\bar{\tau}_{k+1} \in (0, \infty)$ 所取代；在非退化假设 (A4) 下，这些恰好是下面命题 A.16(i,j) 中的正确极限值。

我们现在可以给出本小节的主要结果。为了简化记号，我们将经常省略诸如 $h^k \equiv h^k(n)$、$v^{k,\ell} \equiv v^{k,\ell}(n)$、$\alpha^k \equiv \alpha^k(n)$ 和 $\Delta^k \equiv \Delta^k(n)$ 等量对 $n$ 的依赖。

## 命题 A.16.

对于满足 (A0)–(A5) 以及 (A4) 的对称 AMP 递归 (2.1) 序列，当 $n \rightarrow \infty$ 时，对每个 $k \in \mathbb{N}$，以下结论成立：

- (a) $\|\Delta^k\|_{n,r} \xrightarrow{\mathcal{L}} 0$；
- (b) 对 $1 \le j \le k$，$\|h^j\|_{n,r} = O_c(1)$；对 $0 \le j \le k$，$\|m^j\|_{n,r} = O_c(1)$；
- (c) 对每个 $\psi \in \text{PL}_{k+1}(r)$，$n^{-1} \sum_{i=1}^n \psi(h_i^1, \dots, h_i^k, \gamma_i) \xrightarrow{\mathcal{L}} \mathbb{E}(\psi(\bar{G}_1, \dots, \bar{G}_k, \bar{\gamma}))$；
- (d) 对每个 $\phi \in \text{PL}_{k+1}(1)$，$n^{-1} \sum_{i=1}^n m_i^0 \phi(h_i^1, \dots, h_i^k, \gamma_i) \xrightarrow{\mathcal{L}} \mathbb{E}(F_0(\bar{\gamma}) \cdot \phi(\bar{G}_1, \dots, \bar{G}_k, \bar{\gamma}))$；
- (e) 对 $1 \le j, \ell \le k+1$，$\langle m^{j-1}, m^{\ell-1} \rangle_n \xrightarrow{\mathcal{L}} \mathbb{E}(\bar{G}_j \bar{G}_\ell) = \bar{\mathbf{T}}_{j,\ell}$；
- (f) 对 $1 \le j, \ell \le k$，$\langle h^j, m^\ell \rangle_n = \langle h^j, f_\ell(h^\ell, \gamma) \rangle_n \xrightarrow{\mathcal{L}} \mathbb{E}(\bar{G}_j f_\ell(\bar{G}_\ell, \bar{\gamma})) = \mathbb{E}(f'_\ell(\bar{G}_\ell, \bar{\gamma})) \mathbb{E}(\bar{G}_j \bar{G}_\ell) = \bar{b}_\ell \bar{\mathbf{T}}_{j,\ell}$；对 $1 \le j \le k$，$\langle h^j, m^0 \rangle_n \xrightarrow{\mathcal{L}} 0$；
- (g) $b_k = \langle f'_k(h^k, \gamma) \rangle_n \xrightarrow{\mathcal{L}} \mathbb{E}(f'_k(\bar{G}_k, \bar{\gamma})) = \bar{b}_k$；
- (h) 对 $0 \le \ell \le k$，$v^{k,\ell}/n = (H_k^\top m^\ell - b_\ell M_k^\top m^{\ell-1})/n \xrightarrow{\mathcal{L}} 0$；
- (i) $\alpha^k \xrightarrow{\mathcal{L}} \bar{\alpha}^k$；
- (j) $\|\bar{m}^k\|_n \xrightarrow{\mathcal{L}} \bar{\tau}_{k+1} = \text{Var}^{1/2}(\bar{G}_{k+1} \mid \bar{G}_1, \dots, \bar{G}_k)$。

### 注释 A.17.

在 (A4) 以及注释 A.1(a) 的替代假设下，如果将上述所有地方的 \(\xrightarrow{\mathcal{L}}\) 替换为 \(\rightarrow^p\)，并将 $O_c(1)$ 替换为 $O_p(1)$，则上述断言 (a)–(j) 仍然成立。

为了证明命题 A.16，我们通过对 \(k \in \mathbb{N}\) 进行归纳，逐一证明断言 (a)–(i)（按此顺序）。在此，我们将给出归纳论证的技术摘要（可与第 A.5 节的详细证明一同阅读），以突出其总体结构和关键特征。今后，我们将对 \(k \in \mathbb{N}\) 的归纳假设的部分 \((\cdots)\) 记为 \(\mathcal{H}_k(\cdots)\)。

\(\mathcal{H}_k(e, f)\)：这些是通过选择合适的伪 Lipschitz 函数 \(\psi \in \text{PL}_{k+1}(2) \subseteq \text{PL}_{k+1}(r)$（这些函数最多依赖其 \(k+1$ 个参数中的三个），从归纳假设 \(\mathcal{H}_k(c, d)$ 直接得出的结论。我们使用 \(\mathcal{H}_k(d)$ 来处理涉及 \(m^0$ 的内积，并对不涉及 \(m^0$ 的内积应用 \(\mathcal{H}_k(c)$。在 \(\mathcal{H}_k(e)$ 中，\(\langle m^{j-1}, m^{\ell-1} \rangle_n = \langle f_{j-1}(h^{j-1}, \gamma), f_{\ell-1}(h^{\ell-1}, \gamma) \rangle_n$ 的极限值被证明为

```
\begin{cases}
\mathbb{E}(f_{j-1}(\bar{G}_{j-1}, \bar{\gamma}) \cdot f_{\ell-1}(\bar{G}_{\ell-1}, \bar{\gamma})) = \mathbb{E}(\bar{G}_j \bar{G}_\ell) \qquad \text{for } 2 \le j, \ell \le k + 1 \\
\mathbb{E}(F_0(\bar{\gamma}) \cdot f_{j-1}(\bar{G}_{j-1}, \bar{\gamma})) = \mathbb{E}(\bar{G}_1 \bar{G}_\ell) \qquad \text{for } 1 = j < \ell \le k + 1,
\end{cases}
```

其中两个等式取自 (A.17)，并构成 (2.6) 中极限协方差 \(\bar{\text{T}}_{j, \ell}$ 定义的基础。此外，对于 \(1 \le j, \ell \le k$，\(\mathcal{H}_k(f)$ 第一行中的恒等式 \(\mathbb{E}(\bar{G}_j f_\ell(\bar{G}_\ell, \bar{\gamma})) = \mathbb{E}(f'_\ell(\bar{G}_\ell, \bar{\gamma})) \mathbb{E}(\bar{G}_j \bar{G}_\ell)$ 来自 (A.19)。这些恒等式 (A.17) 和 (A.19) 最终提供了 \(\mathcal{H}_k(h)$ 中 \(\langle h^j, m^\ell \rangle_n$ 的极限值与 \(b_\ell \langle m^{j-1}, m^{\ell-1} \rangle_n$ 之间的关键联系。

\(\mathcal{H}_k(g, h)$：这也源自 \(\mathcal{H}_k(c)$，但由于 \(f'_k: \mathbb{R}^2 \to \mathbb{R}$ 不一定属于 \(\text{PL}_2(r)$，我们而是应用分析性引理 B.10 和 B.14，而不是模仿 \(\mathcal{H}_k(e, f)$ 的证明。参见推论 B.21(b) 的证明以获取类似论证。\(\mathcal{H}_k(h)$ 立即从 \(\mathcal{H}_k(e, f, g)$ 得出。

\(\mathcal{H}_k(i, j)$：我们从 \(\mathcal{H}_k(e)$ 看出，矩阵 \(M_k^\top M_k / n \in \mathbb{R}^{k \times k}$ 完全收敛到极限协方差矩阵 \(\bar{\text{T}}^{[k]} = \text{Cov}(\bar{G}_1, \dots, \bar{G}_k) \in \mathbb{R}^{k \times k}$，该矩阵在 (A4) 下是正定的。在 \(\mathcal{H}_k(i)$ 中，我们考虑 \(\alpha^k = (M_k^\top M_k / n)^+ (M_k^\top m^k / n) \in \mathbb{R}^k$，这是 (A.4) 中定义的投影系数向量。根据 \(\mathcal{H}_k(e)$，\((M_k^\top M_k / n)^+\) 和 \(M_k^\top m^k / n$ 分别完全收敛到 \((\bar{\text{T}}^{[k]})^{-1}\) 和 \(\bar{\text{T}}^{[k], k+1}\)，从而 \(\alpha^k \xrightarrow{S} (\bar{\mathrm{T}}^{[k]})^{-1} \bar{\mathrm{T}}^{[k],k+1} = \bar{\alpha}^k\)，如 (A.14) 中所定义。对于 \(\mathcal{H}_k(j)$，我们回顾第 A.2 节开头的定义，并写出

\(\|\bar{m}^k\|_n^2 = \|P_k^\perp m^k\|_n^2 = \|m^k\|_n^2 - \|P_k m^k\|_n^2\)
\(= \|m^k\|_n^2 - (\alpha^k)^\top (M_k^\top M_k/n) \alpha^k.\)

将 \(\mathcal{H}_k(e, i)$ 应用于上述右边的各个项，我们推断出 \(\|\bar{m}^k\|_n^2 \xrightarrow{S} \bar{\mathrm{T}}_{k+1,k+1} - (\bar{\alpha}^k)^\top \bar{\mathrm{T}}^{[k]} \bar{\alpha}^k = \tilde{\tau}_{k+1}^2$，如 (A.15) 中所定义。

\(\mathcal{H}_{k+1}(a)$：得益于关键事实 \(\mathcal{H}_k(h)$ 以及原始 AMP 递归 (2.1)（随后在命题 A.11 的 (A.7) 中）中存在 Onsager 项 \(-b_k m^{k-1}$，(A.22) 中第二项的 \(\|\cdot\|_{n,r}$ 范数完全收敛到 0。利用 \(\mathcal{H}_k(b, i, j)$ 来处理此定义 (A.22) 的偏差项 \(\Delta^{k+1}$ 中的一些剩余项，我们得出结论 \(\|\Delta^{k+1}\|_{n,r} \xrightarrow{S} 0\)。

\(\mathcal{H}_{k+1}(b)$：利用来自命题 A.11 及 (A.21, A.22) 的分布相等式 \(h^{k+1} \stackrel{d}{=} h^{k+1,k} = \tilde{h}^{k+1} + \Delta^{k+1} = \sum_{\ell=1}^k \bar{\alpha}_\ell^k h^\ell + \tilde{\tau}_{k+1} \tilde{Z}^{k+1} + \Delta^{k+1}$，我们从 \(\mathcal{H}_{k+1}(a)$ 和归纳假设 \(\mathcal{H}_k(b)$ 推断出 \(\|h^{k+1}\|_{n,r} = O_c(1)$。由于根据 (A1) 有 \(\|\gamma\|_{n,r} = O_c(1)$，且 \(f_{k+1}$ 是 Lipschitz 的，这进一步意味着 \(\|m^{k+1}\|_{n,r} = \|f_k(h^{k+1}, \gamma)\|_{n,r} = O_c(1)$。

\(\mathcal{H}_{k+1}(c)$：这是命题 A.16 中的主要断言；根据推论 B.21(b)，它实际上等价于定理 2.3 的结论 (2.8)。我们首先条件于 \(\mathcal{S}_k = \sigma(\gamma, m^0, h^j : 1 \le j \le k)$ 并援引命题 A.11，该命题断言对于每个 \(n > k$，给定 \(\mathcal{S}_k$ 时 \(h^{k+1} \equiv h^{k+1}(n)$ 的条件分布与 (A.7) 中 \(h^{k+1,k} \equiv h^{k+1,k}(n)$ 的分布相同。在 \(\mathcal{H}_{k+1}(c)$ 的左边用 \(h^{k+1,k} = \tilde{h}^{k+1} + \Delta^{k+1}$ 替换 \(h^{k+1}$ 后，我们利用 \(\mathcal{H}_{k+1}(a, b)$ 表明 (A.22) 中的“偏差”项 \(\Delta^{k+1} \equiv \Delta^{k+1}(n)$ 渐近可忽略，因此 \(h^{k+1,k}$ 实际上可以在所有相关表达式中替换为 \(\tilde{h}^{k+1}$。在 (A.21) 中，\(\tilde{h}^{k+1}$ 被定义为 \(\sum_{\ell=1}^k \bar{\alpha}_\ell^k h^\ell + \tilde{\tau}_{k+1} \tilde{Z}^{k+1}$，其中 \(\sum_{\ell=1}^k \bar{\alpha}_\ell^k h^\ell$ 是先前迭代 \(h^1, \dots, h^k$ 的确定性线性组合，而 \(\tilde{\tau}_{k+1} \tilde{Z}^{k+1}$ 是一个具有 i.i.d. 分量且与 \(\mathcal{S}_k$ 独立的新高斯变量。

基于此，$\mathcal{H}_{k+1}(c)$ 的证明可分为两个阶段完成（由下文的 (A.42) 和 (A.40) 给出）：后一项高斯项的影响首先可以通过引用 $\mathcal{H}_{k+1}(b)$ 和一个一般性

