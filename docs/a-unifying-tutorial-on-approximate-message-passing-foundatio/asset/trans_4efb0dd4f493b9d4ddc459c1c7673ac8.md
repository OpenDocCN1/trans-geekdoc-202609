

## 4.1. GAMP的主定理

我们在此指出，虽然 (G2) 通常比 (B2) 是更强的要求，但若对某个固定 \(c \in \mathbb{R}\) 有 \(\tilde{\beta}^0 \equiv \hat{\beta}^0(n) = c 1_p\) 对所有 \(n\) 成立，则 (G1) 蕴含 (G2) 和 (G3)。如同在第 3 节中，对 \(\beta \equiv \beta(n)\) 如稀疏性或逐元素非负性的约束将体现在“限制先验分布” \(\pi_{\bar{\beta}}\) 的形式中。注意

\((\Sigma_0)_{11} = \text{c-}\lim_{n \to \infty} \left( \frac{p}{n} \cdot \frac{\|\beta\|^2}{p} \right) = \frac{\mathbb{E}(\tilde{\beta}^2)}{\delta} > 0 \quad (4.5)\)

由 (G1) 和 (G2)。另外，(G1) 中关于 \(\varepsilon \equiv \varepsilon(n)\) 的条件若对每个 \(n\) 满足 \(\varepsilon_1, \dots, \varepsilon_n \stackrel{\text{iid}}{\sim} P_{\bar{\varepsilon}}\) 则成立。

**状态演化**：令 \(\Sigma_0\) 如 (G2) 所示，状态演化参数 \((\mu_k \in \mathbb{R}, \sigma_k \in [0, \infty), \Sigma_k \in \mathbb{R}^{2 \times 2}: k \in \mathbb{N})\) 递归定义为

\(\mu_{k+1} := \mathbb{E}(\partial_z \tilde{g}_k(Z, Z_k, \bar{\varepsilon})), \quad \sigma_{k+1}^2 := \mathbb{E}(\tilde{g}_k(Z, Z_k, \bar{\varepsilon})^2) = \mathbb{E}(g_k(Z_k, Y)^2), \quad (4.6)\)

\(\Sigma_{k+1} := \frac{1}{\delta} \begin{pmatrix} \mathbb{E}(\tilde{\beta}^2) & \mathbb{E}\{\bar{\beta} f_{k+1}(\mu_{k+1}\bar{\beta} + \sigma_{k+1}G_{k+1})\} \\ \mathbb{E}\{\bar{\beta} f_{k+1}(\mu_{k+1}\bar{\beta} + \sigma_{k+1}G_{k+1})\} & \mathbb{E}\{f_{k+1}(\mu_{k+1}\bar{\beta} + \sigma_{k+1}G_{k+1})^2\} \end{pmatrix} \quad (4.7)\)

对 \(k \in \mathbb{N}_0\)，其中我们取 \((Z, Z_k) \sim N_2(0, \Sigma_k)\) 与 \(\bar{\varepsilon} \sim P_{\bar{\varepsilon}}\) 独立，定义 \(Y := h(Z, \bar{\varepsilon})\)，并取 \(G_{k+1} \sim N(0, 1)\) 与 \(\bar{\beta} \sim \pi_{\bar{\beta}}\) 独立。在 (G4) 下，如同在 Lemma 2.2 中所示，若 \(\sigma_1 > 0\)，则对所有 \(k \in \mathbb{N}\) 均有 \(\sigma_k > 0\) 且 \(\Sigma_k\) 为正定矩阵。在 (4.6) 中，\(\partial_z \tilde{g}_k\) 表示 \(\tilde{g}_k\) 对其第一个自变量的偏导数；注意由 (G4) 可知，\(z \mapsto \tilde{g}_k(z, u, v)\) 是 Lipschitz 连续的，因此对于所有 \((u, v) \in \mathbb{R}^2\) 几乎处处可微，故 \(\mu_{k+1}\) 有定义。

Stein 引理（Lemma A.20）可用于推导 \(\mu_{k+1}\) 的某些替代表达式，日后将有所用；关于以下引理的证明，请参见 Mondelli and Venkataramanan (2020, Proposition 3.1) 或 第 A.9 节。

**引理 4.1。** 对每个 \(k \in \mathbb{N}\)，令 \(\tilde{G}_k \sim N(0, 1)\) 与 \((Z, \bar{\varepsilon})\) 独立，则 \((Z, Z_k, \bar{\varepsilon}) \stackrel{d}{=} (Z, \mu_{Z,k}Z + \sigma_{Z,k}\tilde{G}_k, \bar{\varepsilon})\)，其中
\[
\begin{aligned}
\mu_{Z,k} &:= \frac{\mathbb{E}(\bar{\beta}f_k(\mu_k\bar{\beta} + \sigma_k\tilde{G}_k))}{\mathbb{E}(\bar{\beta}^2)} = \frac{\Sigma_{21}}{\Sigma_{11}}, \\
\sigma_{Z,k}^2 &:= \frac{\mathbb{E}(\bar{\beta}^2)\mathbb{E}(f_k(\mu_k\bar{\beta} + \sigma_k\tilde{G}_k)^2) - \mathbb{E}(\bar{\beta}f_k(\mu_k\bar{\beta} + \sigma_k\tilde{G}_k))^2}{\delta \mathbb{E}(\bar{\beta}^2)} \\
&= \Sigma_{22} - \frac{\Sigma_{12}^2}{\Sigma_{11}},
\end{aligned}
\]
(4.8)

其中 \(\Sigma \equiv \Sigma_k\)。因此，\(\mu_{k+1} = \mathbb{E}(\partial_z\tilde{g}_k(Z, \mu_{Z,k}Z + \sigma_{Z,k}\tilde{G}_k, \bar{\varepsilon}))\) 且 \(\sigma_{k+1}^2 = \mathbb{E}(\tilde{g}_k(Z, \mu_{Z,k}Z + \sigma_{Z,k}\tilde{G}_k, \bar{\varepsilon})^2)\)。并且，
\[
\begin{aligned}
\mu_{k+1} &= \frac{\delta}{\mathbb{E}(\bar{\beta}^2)}\mathbb{E}(Zg_k(Z_k, Y)) - \mu_{Z,k}\mathbb{E}(g'_k(Z_k, Y)) \\
&= \mathbb{E}\left(\frac{\mathbb{E}(Z \mid Z_k, Y) - \mathbb{E}(Z \mid Z_k)}{\text{Var}(Z \mid Z_k)}g_k(Z_k, Y)\right).
\end{aligned}
\]
(4.9)

在给出本小节的主要结果之前，我们做进一步的正则性假设，其与 (B5) 类似。

(G5) 对每个 \(k \in \mathbb{N}_0\)，记 \(D_k \subseteq \mathbb{R}^2\) 为 \(g'_k\) 的不连续点集合，则有 \(\mathbb{P}((Z_k, Y) \in D_k) = 0\)，且 \(f'_{k+1}\) 几乎处处连续（勒贝格意义下）。

**定理 4.2.** 假设 (G0)-(G5) 对由 \(n\) 和 \(p \equiv p_n\) 索引的 GAMP 递归 (4.4) 成立，且 \(n/p \to \delta \in (0, \infty)\) 与 \(\sigma_1 > 0\)。则对每个 \(k \in \mathbb{N}_0\)，我们有

\[
\sup_{\psi \in \text{PL}_2(r, 1)} \left| \frac{1}{p} \sum_{j=1}^p \psi(\beta_j^{k+1}, \beta_j) - \mathbb{E}(\psi(\mu_{k+1}\bar{\beta} + \sigma_{k+1}G_{k+1}, \bar{\beta})) \right| \xrightarrow{\mathsf{p}} 0,
\]
(4.10)

\[
\sup_{\psi \in \text{PL}_3(r, 1)} \left| \frac{1}{n} \sum_{i=1}^n \psi(\theta_i^k, \theta_i, \varepsilon_i) - \mathbb{E}(\psi(\mu_{Z,k}Z + \sigma_{Z,k}\tilde{G}_k, Z, \bar{\varepsilon})) \right| \xrightarrow{\mathsf{p}} 0
\]
(4.11)

当 \(n, p \to \infty\) 且 \(n/p \to \delta\) 时，其中 \(\theta_i \equiv \theta_i(n) = x_i^\top \beta\) 对 \(n \in \mathbb{N}\) 和 \(1 \le i \le n\) 成立。

记 \(\nu_p(\beta^k, \beta)\) 为 \(\beta^k, \beta \in \mathbb{R}^p\) 分量的联合经验分布，并记 \(\breve{\nu}^k\) 为 \((\mu_k \bar{\beta} + \sigma_k G_k, \bar{\beta})\) 的分布，则 (4.10) 的结论可表示为

\(\tilde{d}_r(\nu_p(\beta^k, \beta), \breve{\nu}^k) \xrightarrow{c} 0, \quad \text{or equivalently} \quad d_r(\nu_p(\beta^k, \beta), \breve{\nu}^k) \xrightarrow{c} 0 \quad \text{as } n \to \infty.\)

同样地，(4.11) 表示联合经验分布 \(\nu_n(\theta^k, \theta, \varepsilon)\) 在 \(d_r\) 意义下完全收敛于 \((\mu_{Z,k} Z + \sigma_{Z,k} \tilde{G}_k, Z, \bar{\varepsilon}) \stackrel{d}{=} (Z_k, Z, \bar{\varepsilon})\) 的分布。

**解释：** 非正式地说，当 \(p\) 较大时，\(\beta^k\) 的分量的经验分布近似等于 \(\mu_k \beta + \sigma_k \xi\) 的分量的经验分布，其中 \(\xi \sim N_p(0, I_p)\) 与 \(\beta \in \mathbb{R}^p\) 独立。通过与基于受损观测 \(\mu_k \bar{\beta} + \sigma_k G_k\) 估计 \(\bar{\beta} \sim \pi_{\bar{\beta}}\) 的限制一元问题类比，我们可以将 \(\beta^k\) 视为 *有效观测*，并将 \(\rho_k := (\mu_k / \sigma_k)\) 视为 *有效信噪比*；回顾 Corollary 3.2 之后的讨论。

**注 4.3.** 类似于注 2.4，在定理 4.2 的设置中，条件 (G5) 确保

\(c_k = \frac{1}{n} \sum_{i=1}^n g'_k(\theta_i^k, y_i) \xrightarrow{c} \mathbb{E}(g'_k(Z_k, Y)) =: \bar{c}_k,\)

\(b_{k+1} = \frac{1}{n} \sum_{j=1}^p f'_{k+1}(\beta_j^{k+1}) \xrightarrow{c} \frac{\mathbb{E}(f'_{k+1}(\mu_{k+1}\bar{\beta} + \sigma_{k+1} G_{k+1}))}{\delta} =: \bar{b}_{k+1}\)

(4.12)

当 \(n, p \to \infty\) 且 \(n/p \to \delta\) 时，对每个 \(k \in \mathbb{N}_0\) 成立。事实上，若在 (4.4) 中分别将 \(b_k, c_k\) 替换为 \(\bar{b}_k, \bar{c}_k\)，则定理在 (G0)-(G4) 下成立，此时不需要 (G5)。

通过定义指定限制高斯变量 \(G_1, G_2, ...\) 和 \(\tilde{G}_1, \tilde{G}_2, ...\) 的协方差结构的增广状态演化，我们可以建立联合经验分布 \(\nu_p(\beta^1, ..., \beta^k, \beta)\) 和 \(\nu_n(\theta^0, ..., \theta^k, \theta)\) 的 \(d_r\) 极限，类似于 (3.7) 和定理 3.1。为简化表述，我们不给出此更强结论。其证明在大多数方面与定理 4.2 的证明相同，现予以总结。

**定理 4.2 的证明（草稿）。** 如前所述，总体目标是处理 (4.4) 中 \(y\) 对 \(X\)（通过 \(\theta = X\beta\)）的依赖，并表明有效观测的“噪声”分量 \(\tilde{\beta}^k \equiv \tilde{\beta}^k(n) := \beta^k - \mu_k\beta\) 在较大 \(n\) 时近似为高斯分布（且与 \(\beta\) 独立）。为此，考虑将第二个更新步骤改写为

\(\begin{aligned} \tilde{\beta}^{k+1} \equiv \beta^{k+1} - \mu_{k+1}\beta &= X^\top \tilde{g}_k(\theta, \theta^k, \varepsilon) \\ - \left( \begin{matrix} \beta \\ f_k(\tilde{\beta}^k + \mu_k\beta) \end{matrix} \right) \left( \begin{matrix} \mu_{k+1} \\ (\partial_2\tilde{g}_k(\theta, \theta^k, \varepsilon))_n \end{matrix} \right). \end{aligned} \tag{4.13}\)

此处，\(\tilde{g}_k(\theta, \theta^k, \varepsilon) = g_k(\theta^k, y) = \hat{r}^k\)（对分量应用 \(\tilde{g}_k\)），\(f_k(\tilde{\beta}^k + \mu_k\beta) = f_k(\beta^k) = \hat{\beta}^k\)，且 \(\partial_2\tilde{g}_k(z, u, v) := g'_k(u, h(z, v))\) 与 \(\tilde{g}_k\) 对其第二个自变量的偏导数一致（在后者有定义的地方）。(4.13) 的一个有用特性是，与 \(y\) 不同，噪声向量 \(\varepsilon\) 由 (G0) 独立于 \(X\)。由于 \(\theta\) 和 \(\theta^k\) 均依赖于 \(X\)，这表明将 \(\tilde{\theta}^k := (\theta \ \theta^k) \in \mathbb{R}^{n \times 2}\) 视为一个整体，并将 (4.4) 中的第一个更新步骤改写为

\(\begin{aligned} \tilde{\theta}^k \equiv (\theta \ \theta^k) &= X \left( \begin{matrix} \beta \\ f_k(\tilde{\beta}^k + \mu_k\beta) \end{matrix} \right) \\ - \bar{g}_{k-1}(\theta, \theta^{k-1}, \varepsilon) \left( 0 \ \frac{p}{n} \langle f'_k(\tilde{\beta}^k + \mu_k\beta) \rangle_p \right), \end{aligned} \tag{4.14}\)

其中 \(\frac{p}{n}\langle f'_k(\tilde{\beta}^k + \mu_k\beta)\rangle_p = \frac{p}{n}\langle f'_k(\beta^k)\rangle_p = b_k\)。如此，我们已将 (4.4) 改写为矩阵值 AMP 迭代 (4.13)-(4.14)，它不再是实用目的下的有效算法，但更便于理论分析。的确，其渐近性可通过对此类抽象递归 (A.52) 应用主定理来推导；参见 第 A.7 节。 (4.6) 中 \(\mu_{k+1} = \mathbb{E}(\partial_z \tilde{g}_k(Z, Z_k, \bar{\varepsilon})) \equiv \mathbb{E}(\partial_1 \tilde{g}_k(Z, Z_k, \bar{\varepsilon}))\) 定义的意义在于，(4.13) 中的最后一项是基于 \(\tilde{g}_k\) 的导数（梯度）的非线性修正项。 (4.14) 中的最后一项具有类似解释，即作为 (4.4) 中原始 \(b_k\) 的多元类比，二者共同确保 (4.13)-(4.14) 中迭代的限制经验分布确实为高斯分布。

