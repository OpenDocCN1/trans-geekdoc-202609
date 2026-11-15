

## 4.2 选择函数 $f_k, g_k$ 以及对 $\beta$ 的推断

渐近估计误差：由于按假设(4.4)中的函数 $f_k$ 是 Lipschitz 的，如同推论 3.2 所示，在上述定理 4.2 的设置下，$\hat{\beta}^k$ 相对于任何损失函数 $\psi \in \text{PL}_2(r)$ 的渐近估计误差由下式给出

$$
\frac{1}{p} \sum_{j=1}^p \psi(\hat{\beta}_j^k, \beta_j) \xrightarrow{\mathcal{L}} \mathbb{E}\{\psi(f_k(\mu_k\bar{\beta} + \sigma_k G_k), \bar{\beta})\}
$$ (4.15)

对每个 $k \in \mathbb{N}$，当 $n, p \to \infty$ 且 $n/p \to \delta$ 时成立。特别地，取 $\psi(x, y) = |x - y|^q$（其中 $q \in [1, r]$），我们得到渐近归一化 $\ell_q$ 误差 c-$\lim_{p \to \infty} p^{-1} \|\hat{\beta}^k - \beta\|_q = \mathbb{E}\{(f_k(\mu_k\bar{\beta} + \sigma_k G_k) - \bar{\beta})^q\}^{1/q}$。

贝叶斯 GAMP：如果已知先验分布的极限 $\pi_{\bar{\beta}}$、噪声分布的极限 $P_{\bar{\varepsilon}}$ 以及初始 $\Sigma_0 \in \mathbb{R}^{2\times 2}$，那么在引理 3.7 的指导下，我们可以如同第 3.3 节一样进行，并为每个 $k$ 选择 (4.4) 中的 $f_k, g_k$，以最大化有效信噪比 $\rho_k = (\mu_k/\sigma_k)^2$ 和 $\rho_{Z,k} := (\mu_{Z,k}/\sigma_{Z,k})^2$。

具体地，对于某个 $k \in \mathbb{N}_0$，给定 (4.7) 中的矩阵 $\Sigma \equiv \Sigma_k \in \mathbb{R}^{2\times 2}$，我们可以从 (4.8) 得到 $\mu_{Z,k}, \sigma_{Z,k}$；反之，给定 $\mu_{Z,k}, \sigma_{Z,k}$，我们可以恢复 $\Sigma$，因为 $\Sigma_{11} = \delta^{-1} \mathbb{E}(\bar{\beta}^2)$ 是已知的，且 (4.8) 得出 $\Sigma_{21} = \Sigma_{11} \mu_{Z,k}$ 和 $\Sigma_{22} = \sigma_{Z,k}^2 + \Sigma_{11} \mu_{Z,k}^2$。现在令 $(Z, Z_k) \sim N_2(0, \Sigma_k)$ 与 $\bar{\varepsilon} \sim P_{\bar{\varepsilon}}$ 独立，并设 $Y = h(Z, \bar{\varepsilon})$，从而使得 $Y$ 与 $Z_k$ 在给定 $Z$ 的条件下条件独立。基于 $(Z, Z_k, Y)$ 的联合分布，令 $g_k^*: \mathbb{R}^2 \to \mathbb{R}$ 为满足下式的可测函数

$$
g_k^*(Z_k, Y) = \frac{\mathbb{E}(Z | Z_k, Y) - \mathbb{E}(Z | Z_k)}{\text{Var}(Z | Z_k)},
$$ (4.16)

其中 $\mathbb{E}(Z | Z_k) = m_k Z_k$，且

$$
m_k := \frac{\Sigma_{21}}{\Sigma_{22}} = \frac{\mu_{Z,k}}{\sigma_{Z,k}^2} \text{Var}(Z | Z_k),
$$

$$
\text{Var}(Z | Z_k) = \Sigma_{11} - \frac{\Sigma_{21}^2}{\Sigma_{22}} = \frac{\Sigma_{11} \sigma_{Z,k}^2}{\sigma_{Z,k}^2 + \Sigma_{11} \mu_{Z,k}^2} = \left( \frac{\delta}{\mathbb{E}(\bar{\beta}^2)} + \rho_{Z,k} \right)^{-1}.
$$

然后根据 (4.6)、(4.9) 和柯西-施瓦茨不等式，我们有

$$
\rho_{k+1} = \frac{\mu_{k+1}^2}{\sigma_{k+1}^2} = \frac{\mathbb{E}(g_k^*(Z_k, Y) g_k(Z_k, Y))^2}{\mathbb{E}(g_k(Z_k, Y)^2)} \le \mathbb{E}(g_k^*(Z_k, Y)^2),
$$

当 $g_k$ 是 $g_k^*$ 的（非零）标量倍数时取等号。

现在给定某个 $k \in \mathbb{N}$ 的 $\mu_k, \sigma_k$，我们希望找到 $f_k: \mathbb{R} \rightarrow \mathbb{R}$，使得定义 $\Sigma \equiv \Sigma_k$（如同 (4.8) 所示），下列量

$$
\rho_{Z,k} = \frac{\mu_{Z,k}^2}{\sigma_{Z,k}^2} = \frac{\Sigma_{21}^2 \Sigma_{11}^{-2}}{\Sigma_{22} - \Sigma_{21}^2 \Sigma_{11}^{-1}} = \left( \frac{\Sigma_{22}}{\Sigma_{21}^2} \Sigma_{11}^2 - \Sigma_{11} \right)^{-1}
$$

尽可能大。由于 $\Sigma_{11} = \delta^{-1} \mathbb{E}(\bar{\beta}^2)$ 是固定的，这相当于最大化

$$
\frac{\Sigma_{21}^2}{\Sigma_{22}} = \frac{\mathbb{E}(\bar{f}_k(\mu_k \bar{\beta} + \sigma_k \bar{G}_k))^2}{\mathbb{E}(f_k(\mu_k \bar{\beta} + \sigma_k \bar{G}_k)^2)}.
$$

再次根据柯西-施瓦茨不等式（见第 3.3 节中的 (3.19)），这可以通过取 $f_k$ 为满足下式的任意（非零）标量倍数 $f_k^*$ 来实现

$$
f_k^*(\mu_k \bar{\beta} + \sigma_k \bar{G}_k) = \mathbb{E}(\bar{\beta} \mid \mu_k \bar{\beta} + \sigma_k \bar{G}_k), \quad (4.17)
$$

此时 $\Sigma_{21} = \Sigma_{22} < \Sigma_{11}$。$f_k^*$ 的精确表达式由 Tweedie 公式 (3.17) 给出，如果 $\tilde{\beta} \sim \pi_{\bar{\beta}}$ 满足引理 3.8 的条件，则 $f_k^*$ 是 Lipschitz 的。正如我们在 (3.18) 中所见，选择 $f_k = f_k^*$ 还最小化了给定 $\mu_k, \sigma_k$ 的渐近平均平方误差 $\mathbb{E}\{(f_k(\mu_k \bar{\beta} + \sigma_k G_k) - \bar{\beta})^2\}$；换句话说，$f_k^*$ 是贝叶斯最优（即 MMSE）去噪函数。

通过为 $k \in \mathbb{N}$ 递归定义 $g_k = g_k^*$（或其某个标量倍数）和 $f_{k+1} = f_{k+1}^*$，使用 (4.16) 和 (4.17)，并配合通过 (4.6)-(4.7) 的相应状态演化参数序列 $(\mu_k^*, \sigma_k^*, \mu_{Z,k}^*, \sigma_{Z,k}^*: k \in \mathbb{N})$，我们得到形式为 (4.4) 的 _贝叶斯 GAMP 算法_。Rangan (2011, Section IV-B) 最初将一个版本作为和-积环式信念传播算法的近似推导出来。Bayes-GAMP 迭代的极限经验分布可以由定理 4.2 得到，前提是函数 $f_k^*$ 和 $\tilde{g}_k^*: (z, u, v) \mapsto g_k^*(u, h(z, v))$ 均为 Lipschitz 且满足 (G0)-(G5)。

即使 $\pi_{\bar{\beta}}$ 不完全已知，仍然有可能将 $f_k, g_k$ 的选择定制为更广泛的先验分布类，这些分布在信号 $\beta$ 中诱导某种结构。例如，如果我们被告知 $\beta \in \mathbb{R}^p$ 最多有 $sp$ 个非零项，其中 $s \in (0, 1)$ 且对每个 $p \equiv p_n$ 成立，那么如同第 3.3 节一样，我们可以将每个 $f_k$ 取为某个 $t_k > 0$ 的软阈值函数 $\mathrm{S}_{t_k}: u \mapsto \operatorname{sgn}(u)(|u|-t_k)_+$。使用适当选择阈值 $t_k$ 的这种形式的 AMP 递归 (4.19)（用于第 4.3 节中的线性模型），Bayati 和 Montanari (2012) 推导了 Lasso 估计量的精确高维渐近结果；参见第 4.5 节。

### 谱初始化

在定理 4.2 的条件下，由 (4.15) 和引理 4.1 可知，对于每个 $k \in \mathbb{N}$，通用 GAMP 过程 (4.4) 中的估计 $\hat{\beta}^k$ 满足当 $n, p \to \infty$ 且 $n/p \to \delta$ 时，$\langle \hat{\beta}^k, \beta \rangle_p = p^{-1} \sum_{j=1}^p \hat{\beta}_j^k \beta_j \xrightarrow{c} \mathbb{E}(\bar{\beta} f_k(\mu_k \bar{\beta} + \sigma_k G_k)) = \mu_{Z,k} \mathbb{E}(\bar{\beta}^2)$。为了确保存在某个 $k$ 使得 $\mu_{Z,k} \neq 0$，并因此使相应的 $\hat{\beta}^k$ 与信号 $\beta$ 具有非零的渐近经验相关性，有时需要从具有自身性质的导频估计量 $\hat{\beta}^0 \in \mathbb{R}^p$ 开始，即 c-$\lim_{p \to \infty}\langle \hat{\beta}^0, \beta \rangle_p \neq 0$。实际上，假设状态演化递归 (4.6)-(4.7) 中的极限随机变量满足

$$
\mathbb{E}(\bar{\beta}) = 0 \quad \text{and} \quad \mathbb{E}(Z|Y) = 0 \quad \text{almost surely,} \quad (4.18)
$$

其中后一条件等同于 Mondelli 和 Venkataramanan (2020) 中的 (3.13)。现在给定使得 c-$\lim_{n\to\infty}\langle \hat{\beta}^0, \beta \rangle_p = \delta(\Sigma_0)_{21} = 0$ 的估计量 $\hat{\beta}^0 \in \mathbb{R}^p$，我们从引理 4.1 可知 $\mu_{Z,0} = 0$ 且 $Z_0$ 与 $(Z, Y)$ 独立，因此在 (4.16) 中几乎必有 $g_0^*(Z_0, Y) = \mathbb{E}(Z|Y)/\text{Var}(Z) = 0$，且根据 (4.9) $\mu_1 = \mathbb{E}(g_0^*(Z_0, Y)g_0(Z_0, Y)) = 0$。这意味着 $\mu_{Z,1} \mathbb{E}(\bar{\beta}^2) = \delta(\Sigma_1)_{21} = \mathbb{E}(\bar{\beta} f_1(\sigma_1 G_1)) = 0$，由 $\bar{\beta}$ 和 $G_1$ 的独立性得出。继续归纳，我们得出对于所有 $k \in \mathbb{N}$，$\mu_k = \mu_{Z,k} = 0$，与对 $k \in \mathbb{N}_0$ 的 $g_k, f_{k+1}$ 的选择无关，因此对于每个 $k \in \mathbb{N}_0$，$\hat{\beta}^k$ 作为 $\beta \in \mathbb{R}^p$ 的估计量在渐近上是无信息的。

因此，虽然在某些广义线性模型（例如第 4.3 节中的线性模型）中，对于某个固定的 $c \in \mathbb{R}$，取 $\hat{\beta}^0 = c \mathbf{1}_p$ 就足够了，但当 (4.18) 成立时需要不同的初始化器。我们注意到，其中的第二个条件在相位检索模型中是满足的，其中 $y_i = h(x_i^\top \beta, \varepsilon_i) = (x_i^\top \beta)^2 + \varepsilon_i$ 对 $1 \le i \le n$ 成立，更一般地，在所有形式为 (4.1) 且对所有 $z, w$ 满足 $h(z, w) = h(-z, w)$ 的不可识别模型中（因此对所有 $z$，(4.2) 中的 $Q(\cdot | z) = Q(\cdot | -z)$）也满足。实际上，对于这样的函数 $h$，我们有 $\mathbb{E}(Z|Y) = \mathbb{E}(Z|h(Z, \bar{\varepsilon})) = -\mathbb{E}(Z|h(Z, \bar{\varepsilon}))$，因此几乎必有 $\mathbb{E}(Z|Y) = 0$。

