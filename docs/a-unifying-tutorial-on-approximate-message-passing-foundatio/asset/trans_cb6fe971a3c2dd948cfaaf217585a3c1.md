

for \( z \in \mathbb{R} \).（函数 \( \eta^{-1} M_\eta \) 称为 M 的 *莫鲁包络*。）我们注意到，\( \text{prox}_{\eta M}(z) \) 在 (4.25) 中是对每个 \( z \in \mathbb{R} \) 达到此最小值的唯一 \( t \)，并且 \( M_\eta \) 是可微凸函数，且对所有 \( z \) 满足 \( S_\eta(z) := (M_\eta)'(z) = z - \text{prox}_{\eta M}(z) \)；参见例如 Rockafellar (1997, Theorem 31.5) 和 Parikh and Boyd (2013, Section 3.2)。此外，\( S_\eta \) 是非递减且 1-Lipschitz 的（cf. Parikh and Boyd, 2013, Sections 2.3 and 3.1）。

对于 \( k \in \mathbb{N}_0 \)，(4.23)-(4.24) 中的函数 \( \bar{g}_k, g_k, f_{k+1} \) 由以下给出

\(\bar{g}_k(u, v) = v - \text{prox}_{\bar{b}_k M}(v - u) = u + S_{\bar{b}_k}(v - u),\)
\(g_k(u, v) = \frac{S_{\bar{b}_k}(v - u)}{\bar{b}_k}, \qquad f_{k+1}(w) = -\frac{w}{\bar{c}_k}.\)

Given \( \bar{b}_0 > 0 \), \( \hat{\beta}^0 \in \mathbb{R}^p \) and \( \hat{r}^0 := y - X\hat{\beta}^0 \)，我们现在用 \( \hat{r}^k = y - \theta^k \) 和 \( \hat{\beta}^{k+1} = f_{k+1}(\beta^{k+1}) = -\beta^{k+1}/\bar{c}_k \) 来重写 GAMP 算法 (4.29)，并得到递归

\(\hat{\beta}^{k+1} = \frac{\delta \bar{b}_{k+1}}{\bar{b}_k} X^\top S_{\bar{b}_k}(r^k) + \hat{\beta}^k,\)
\(\hat{r}^{k+1} = y - X\hat{\beta}^{k+1} + \frac{\bar{b}_{k+1}}{\bar{b}_k} S_{\bar{b}_k}(r^k) \qquad \text{for } k \in \mathbb{N}_0,\) (4.53)

其中 \( \bar{b}_{k+1} = -1/(\delta \bar{c}_k) \)。此外，将 (4.29) 的状态演化递归 (4.6)-(4.7) 用 \( \tilde{\mu}_k := \delta \bar{b}_k \mu_k \)、\( \tilde{\sigma}_k := \delta \bar{b}_k \sigma_k \) 和 \( \tau_k := \mathbb{E}((Z - Z_k)^2)^{1/2} \) 表示，其中 \( (Z, Z_k) \sim N(0, \Sigma_k) \)，我们有 \( \tau_0 = \mathbb{E}((Z - Z_0)^2)^{1/2} \) 和

\(\tilde{\mu}_{k+1} = \delta \mathbb{E}(S'_{\bar{b}_k}(\bar{\varepsilon} + \tau_k G_k)), \qquad \tilde{\sigma}_{k+1}^2 = \delta^2 \mathbb{E}(S_{\bar{b}_k}(\bar{\varepsilon} + \tau_k G_k)^2),\)
\(\bar{b}_{k+1} = -\frac{1}{\delta \bar{c}_k} = \frac{\bar{b}_k}{\delta \mathbb{E}(S'_{\bar{b}_k}(\bar{\varepsilon} + \tau_k G_k))},\)
\(\tau_{k+1}^2 = \frac{\mathbb{E}(\bar{\beta}^2)(\tilde{\mu}_{k+1} - 1)^2 + \tilde{\sigma}_{k+1}^2}{\delta}\) (4.54)

对于 \( k \in \mathbb{N}_0 \)，其中 \( \bar{\varepsilon} \sim P_\Xi \) 与 \( G_k \sim N(0, 1) \) 独立。

现在转向第 4.4 节中的 **步骤 1**，我们寻求 (4.53)-(4.54) 的满足以下条件的不动点 \( (\hat{r}^*, \hat{\beta}^*, \bar{b}_* > 0, \tilde{\mu}_*, \tilde{\sigma}_*, \tau_*) \)：

\( 0 = \delta X^\top S_{\bar{b}_*}(\hat{r}^*), \qquad \hat{r}^* = y - X\hat{\beta}^* + S_{\bar{b}_*}(\hat{r}^*), \) (4.55)

\(\check{\mu}_* = \delta \mathbb{E}(S'_{\tilde{b}_*}(\bar{\varepsilon} + \tau_* G_*)) = 1, \quad \tau_*^2 = \delta \mathbb{E}(S_{\tilde{b}_*}(\bar{\varepsilon} + \tau_* G_*)^2), \quad \check{\sigma}_* = \sqrt{\delta} \tau_* , \tag{4.56}\)

其中 \(\bar{\varepsilon} \sim P_{\bar{\varepsilon}}\) 与 \(G_* \sim N(0,1)\) 独立，且 \(\mu_* = \check{\mu}_*/(\delta\tilde{b}_*)\) 和 \(\sigma_* = \check{\sigma}_*/(\delta\tilde{b}_*)\) 是原始状态演化方程 (4.6) 的不动点。根据提案 4.4，\(\hat{\beta}^*\) 求解 (4.50) 中的 M-估计问题。假设

M 是连续可微的，且 \(S = M'\) 是绝对连续的，并满足 \(\sup_{w \in \mathbb{R}} S'(w) < \infty, \tag{4.57}\)

Donoho and Montanari (2016, Lemma 6.5) 表明，对于任何 \(\tau > 0\)，映射 \(b \mapsto \mathbb{E}(S'_{\tilde{b}}(\bar{\varepsilon} + \tau G_*)) =: F_\tau(b)\) 在 \((0, \infty)\) 上是连续的，且 \(\lim_{b \to 0} F_\tau(b) = 0\) 和 \(\lim_{b \to \infty} F_\tau(b) = 1\)，因此存在 \(b \equiv b_\tau > 0\) 满足 \(\mathbb{E}(S'_{\tilde{b}}(\bar{\varepsilon} + \tau G_*)) = \delta^{-1}\) 对于 \(\delta \in (1, \infty)\)。利用这一点，他们推断在 (4.57) 下，对于任何这样的 \(\delta\)，(4.56) 存在唯一解 \((\tau_*, \tilde{b}_*)\) (Donoho and Montanari, 2016, Corollary 4.4)。

第 4.4 节中 **步骤 2** 的函数 \(f_*, g_*\) 由 \(f_* : w \mapsto \delta \tilde{b}_* w\) 和 \(g_* : (u, v) \mapsto S_{\tilde{b}_*}(v - u) / \tilde{b}_*\) 给出，因此对于 \(n \in \mathbb{N}\) 和 \(p \equiv p_n\)，“静态”AMP 迭代 (4.35) 可写为

\(\hat{\beta}^{k+1} = X^\top S_{\tilde{b}_*}(\hat{r}^k) + \hat{\beta}^k, \quad \hat{r}^{k+1} = y - X \hat{\beta}^{k+1} + S_{\tilde{b}_*}(\hat{r}^k) \quad \text{for } k \in \mathbb{N}_0. \tag{4.58}\)

这里，\(\hat{r}^0 = y - X \hat{\beta}^0\) 且 \(\hat{\beta}^0 = \beta + \tilde{\sigma}_* \xi = f_*(\mu_* \beta + \sigma_* \xi) \in \mathbb{R}^p\)，其中 \(\xi \sim N_p(0, I_p)\) 与信号 \(\beta \in \mathbb{R}^p\) 独立。这种神谕初始化的选择确保相应的状态演化序列是静态的，对所有 \(k \in \mathbb{N}_0\) 均有 \(\tau_k = \tau_*\)。然后，在定理 4.2 的条件 (G0)-(G5) 下（取 \(r=2\)），根据注记 4.3 和 (4.10)，对于每个固定的 \(k \in \mathbb{N}\)，\(\hat{r}^k - \varepsilon \in \mathbb{R}^n\) 和 \(\hat{\beta}^k - \beta \in \mathbb{R}^p\) 的分量经验分布在 \(d_2\) 中完全收敛于 \(N(0, \tau_*^2)\) 和 \(N(0, \check{\sigma}_*^2) = N(0, \delta \tau_*^2)\)，分别当 \(n, p \to \infty\) 且 \(n/p \to \delta \in (1, \infty)\) 时。

我们指出，这个结果实际上可以通过直接将 (4.58) 转换为形式 (2.10) 的抽象非对称 AMP 迭代来推导。特别是，由于线性模型中 (4.1) 处 \(h(z, v) = z + v\) 且 \(S_\eta\) 对所有 \(\eta > 0\) 都是 1-Lipschitz 的，(G4) 中的函数 \(\tilde{g}_k = \tilde{g}_* : (z, u, v) \mapsto S_{\tilde{b}_*}(z + v - u) / \tilde{b}_*\) 确实是 Lipschitz 的。

与第 4.5 节一样，剩余的成分（第 4.4 节中的 **步骤 3**）是证明 (4.58) 中的迭代 \(\hat{\beta}^k\) 按 (4.36) 的意义收敛

到某个满足 (4.55) 的 \(\hat{\beta}^*\)，根据提案 4.4，它是一个 M-估计量。在 (4.57) 以及 M 强凸的额外假设下，即 \(\inf_{w \in \mathbb{R}} S'(w) > 0\)，Donoho and Montanari (2016, Theorem 4.1) 的结论确实是

\(\lim_{k \to \infty} \text{c-lim}_{p \to \infty} \frac{\|\hat{\beta}^k - \hat{\beta}^*\|^2}{p} = 0.\) (4.59)

结合 (4.58) 中迭代的状态演化表征，这得出了关于 M-估计量渐近性能的以下表征。

**定理 4.7** (Donoho and Montanari, 2016, Theorem 4.2)。考虑一系列满足 (G0) 和 (G1) 的线性模型 \(y = X\beta + \varepsilon\)，当 \(n, p \to \infty\) 时 \(n/p \to \delta \in (1, \infty)\)。假设损失函数 M 是连续可微的，且评分函数 \(S = M'\) 是绝对连续的，并满足 \(0 < \inf_{w \in \mathbb{R}} S'(w) \le \sup_{w \in \mathbb{R}} S'(w) < \infty\)。令 \((\tau_*, \bar{b}_*)\) 为 (4.56) 的唯一不动点。则

\(\sup_{\psi \in \text{PL}_2(2,1)} \left| \frac{1}{p} \sum_{j=1}^p \psi(\hat{\beta}_j^{\text{M}} - \beta_j, \beta_j) - \mathbb{E}(\psi(\sqrt{\delta}\tau_* G, \bar{\beta})) \right| \xrightarrow{c} 0\) (4.60)

当 \(n, p \to \infty\) 且 \(n/p \to \delta\) 时，其中 \(G \sim N(0,1)\)。特别地，\(\hat{\beta}^{\text{M}}\) 的渐近均方误差由以下给出

\(\text{c-lim}_{p \to \infty} \frac{\|\hat{\beta}^{\text{M}} - \beta\|^2}{p} = V(S_{b_*}; \bar{\varepsilon} + \tau_* G) = \frac{\mathbb{E}(S_{b_*}(\bar{\varepsilon} + \tau_* G)^2)}{\mathbb{E}(S'_{b_*}(\bar{\varepsilon} + \tau_* G))^2} = \frac{\tau_*^2 / \delta}{1/\delta^2} = \delta \tau_*^2.\) (4.61)

在信号向量 \(\beta \in \mathbb{R}^p\) 上的条件 (G1) 下，定理 4.7 给出了 \(\hat{\beta}^{\text{M}}, \beta \in \mathbb{R}^p\) 的分量的极限联合经验分布。结果表明，即使没有 (G1)，我们也有

\(\sup_{\psi \in \text{PL}_1(2,1)} \left| \frac{1}{p} \sum_{j=1}^p \psi(\hat{\beta}_j^{\text{M}} - \beta_j) - \mathbb{E}(\psi(\sqrt{\delta}\tau_* G)) \right| \xrightarrow{c} 0,\)

这从 \(\bar{\beta}\) 不出现在状态演化递归 (4.56) 中可以看出。将 (4.61) 中的方差泛函 \(V(S_{b_*}; \bar{\varepsilon} + \tau_* G)\) 与经典设置中的 \(V(S; \bar{\varepsilon})\)（即 (4.52)）进行比较，

