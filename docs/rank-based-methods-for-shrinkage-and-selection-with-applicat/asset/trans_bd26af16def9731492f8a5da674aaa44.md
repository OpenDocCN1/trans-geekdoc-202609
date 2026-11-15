

\left\| \max \sum_{i=1}^n W_{n_i}(t_j) u_i \right\| = O\left(n^{-\frac{1}{6}}\right).

我们还假设函数 \(g(\cdot)\) 和 \(h_s(\cdot)\) 在 \([0, 1]\) 上对 \(s=1, ..., p\) 满足阶数为 1 的 Lipschitz 条件。

为了估计 \(\boldsymbol{\beta} = (\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top\)，我们最小化 Jaeckel 的秩离散函数

\(D_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) = \sum_{i=1}^n (\gamma_i - \boldsymbol{x}_{i(1)}^\top \boldsymbol{\beta}_1 - \boldsymbol{x}_{i(2)}^\top \boldsymbol{\beta}_2 - \tilde{g}(t_i, \boldsymbol{\beta}_1, \boldsymbol{\beta}_2)) a_n(R_{ni}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2))\)
\(= \sum_{i=1}^n (\hat{\gamma}_i - \boldsymbol{z}_{i(1)}^\top \boldsymbol{\beta}_1 - \boldsymbol{z}_{i(2)}^\top \boldsymbol{\beta}_2) a_n(R_{ni}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)),\)

关于 \((\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)\)，其中

\(a_n(R_{ni}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)) = \varphi\left(\frac{R_{ni}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)}{n+1}\right), \quad i=1, 2, ..., n\)

这些得分基于 \(\hat{\gamma}_i - \boldsymbol{z}_{i(1)}\boldsymbol{\beta}_1 - \boldsymbol{z}_{i(2)}\boldsymbol{\beta}_2\) 在

\((\hat{\gamma}_1 - \boldsymbol{z}_{1(1)}\boldsymbol{\beta}_1 - \boldsymbol{z}_{1(2)}\boldsymbol{\beta}_2, ..., (\hat{\gamma}_n - \boldsymbol{z}_{n(1)}\boldsymbol{\beta}_1 - \boldsymbol{z}_{n(2)}\boldsymbol{\beta}_2)\)

其中 \(\int_0^1 \varphi(u)du = 0\) 且

\(A_\varphi^2 = \int_0^1 |\varphi(u)|\{u(1-u)\}^{\frac{1}{2}}du < \infty.\)

回顾，\(\varphi : (0, 1) \mapsto \mathbb{R}\) 是得分生成函数，假设其在 \((0, 1)\) 上非恒定、非递减且平方可积。

除了公式 (7.2.5) 之外，得分还可以按以下方式定义：

\(a_n(i) = \mathbb{E}[\varphi(U_{i:n})], \quad i=1, ..., n,\)

其中 \(U_{1:n} \le ... \le U_{n:n}\) 是来自均匀分布 \(\mathcal{U}(0, 1)\) 的容量为 \(n\) 的样本的阶次统计量。

考虑

\(\frac{\partial D_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)}{\partial (\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)} = -\boldsymbol{L}_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)\)
\(= -(L_{n1}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2), ..., L_{nn}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2))^\top,\)

其中

\(\boldsymbol{L}_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) = \sum_{i=1}^n (z_i - \bar{z}_n) a_n(R_{ni}(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2))\)

$$L_{nj}(\boldsymbol{\beta}_1,\boldsymbol{\beta}_2) = \sum_{i=1}^n (z_{ij}-\bar{z}_{nj})a_n(R_{nj}(\boldsymbol{\beta}_1,\boldsymbol{\beta}_2)), j=1,\dots,p.$$

然后，定义 \((\boldsymbol{\beta}_1^\top, \boldsymbol{\beta}_2^\top)^\top\) 的 URE 为

$$\hat{\boldsymbol{\beta}}_n^{\text{UR}} = (\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}\top}, \hat{\boldsymbol{\beta}}_{2n}^{\text{UR}\top})^\top = \operatorname{argmin}_{\boldsymbol{\beta}_1 \in \mathbb{R}^{p_1}, \boldsymbol{\beta}_2 \in \mathbb{R}^{p_2}} \{D_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2)\}.$$

注意，如果 \(\beta_2 = \mathbf{0}\) 成立，则 \(\beta_1\) 的 RRE 为

$$\hat{\boldsymbol{\beta}}_n^{\text{RR}} = (\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}\top}, \mathbf{0}^\top)^\top, \quad \text{where } \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} = \operatorname{argmin}_{\boldsymbol{\beta}_1 \in \mathbb{R}^{p_1}} \{D_n(\boldsymbol{\beta}_1, \mathbf{0})\}.$$

可以验证

$$\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}} = \operatorname{argmin}_{\boldsymbol{\beta}_1 \in \mathbb{R}^{p_1}} \sum_{j=1}^{p_1} |L_{nj}(\boldsymbol{\beta}_1, \mathbf{0})|.$$

让我们定义

$$\boldsymbol{C}_n = \frac{1}{n} \sum_{i=1}^n (\mathbf{z}_i - \bar{\mathbf{z}}_n)(\mathbf{z}_i - \bar{\mathbf{z}}_n)^\top,$$

其中 \(\mathbf{z}_i\) 是 \(\mathbf{Z}\) 的第 \(i\) 行，且 \(\bar{\mathbf{z}}_n = \frac{1}{n} \sum_{i=1}^n \mathbf{z}_i\)。我们假设 \(\boldsymbol{C}_n\) 可逆，并且

(a) \(\lim_{n \to \infty} \boldsymbol{C}_n = \boldsymbol{C}\) 和 (b) \(\lim_{n \to \infty} \max_{1 \le i \le n} (\mathbf{z}_i - \bar{\mathbf{z}}_n)^\top \boldsymbol{C}_n^{-1} (\mathbf{z}_i - \bar{\mathbf{z}}_n) = 0,\)

其中 \(\boldsymbol{C}\) 是维度为 \(p\) 的可逆矩阵。

在后续内容中，我们将根据需要使用以下分块：

$$\boldsymbol{C}_n = \begin{bmatrix} \boldsymbol{C}_{n11} & \boldsymbol{C}_{n12} \\ \boldsymbol{C}_{n21} & \boldsymbol{C}_{n22} \end{bmatrix}, \quad \boldsymbol{C} = \begin{bmatrix} \boldsymbol{C}_{11} & \boldsymbol{C}_{12} \\ \boldsymbol{C}_{21} & \boldsymbol{C}_{22} \end{bmatrix}$$

$$\boldsymbol{C}_n^{-1} = \begin{bmatrix} \boldsymbol{C}_{n11.2}^{-1} & -\boldsymbol{C}_{n11.2}^{-1} \boldsymbol{C}_{n12} \boldsymbol{C}_{n22}^{-1} \\ -\boldsymbol{C}_{n22}^{-1} \boldsymbol{C}_{n21} \boldsymbol{C}_{n11.2}^{-1} & \boldsymbol{C}_{n22.1}^{-1} \end{bmatrix},$$

其中 \(\boldsymbol{C}_{n22.1}\) 和 \(\boldsymbol{C}_{n11.2}\) 分别是 \(\boldsymbol{C}_{n11}\) 和 \(\boldsymbol{C}_{n22}\) 的 Schur 补，给出为

$$\boldsymbol{C}_{n22.1} = \boldsymbol{C}_{n22} - \boldsymbol{C}_{n21} \boldsymbol{C}_{n11}^{-1} \boldsymbol{C}_{n12},$$

$$\boldsymbol{C}_{n11.2} = \boldsymbol{C}_{n11} - \boldsymbol{C}_{n12} \boldsymbol{C}_{n22}^{-1} \boldsymbol{C}_{n21}.$$

## 定理 7.1

在假设的正则性条件下，当 $n \to \infty$ 时，

$$\sqrt{n}(\hat{\boldsymbol{\beta}}_n^{\text{UR}} - \boldsymbol{\beta}) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_1}(\mathbf{0}, \eta^2 \mathbf{C}^{-1}), \quad \eta^2 = \frac{A_{\varphi}^2}{\gamma^2(\varphi, \psi)},$$

其中 $\gamma(\varphi, \psi)$ 和 $A_{\varphi}$ 分别由公式 (7.1.3) 和 (7.2.6) 给出。

作为定理 7.1 的结果，当 $n \to \infty$ 时，我们有以下极限情况，

- (i) $\sqrt{n}(\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} - \boldsymbol{\beta}_1) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_1}(\mathbf{0}, \eta^2 \mathbf{C}_{11:2}^{-1}),$
- (ii) $\sqrt{n}(\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}} - \boldsymbol{\beta}_2) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_2}(\mathbf{0}, \eta^2 \mathbf{C}_{22:1}^{-1}),$
- (iii) $\sqrt{n}(\hat{\boldsymbol{\beta}}_{1n}^{\text{RR}} - \boldsymbol{\beta}_1) \xrightarrow{\mathcal{D}} \mathcal{N}_{p_1}(\mathbf{0}, \eta^2 \mathbf{C}_{11}^{-1}),$
- (iv) $\sqrt{n}(\hat{\beta}_{jn}^{\text{UR}} - \beta_j) \xrightarrow{\mathcal{D}} \mathcal{N}(0, \eta^2 C^{jj}),$ 其中 $C^{jj}$ 是 $\mathbf{C}^{-1}$ 的第 $j$ 个对角线元素。

## 7.2.1 惩罚 R 估计量

我们定义 LASSO R 估计量为

$$\begin{aligned} \sqrt{n}\hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda) &= \underset{(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) \in \mathbb{R}^p}{\text{argmin}} \left\{ D_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) + \lambda \eta \sqrt{C^{jj}} \mathbf{1}_p^\top |\boldsymbol{\beta}| \right\} \\ &= \left( \text{sgn}(\sqrt{n}\hat{\beta}_{jn}^{\text{UR}}) \left( |\sqrt{n}\hat{\beta}_{jn}^{\text{UR}}| - \lambda \eta \sqrt{C^{jj}} \right)^+ \bigg| j = 1, \dots, p \right)^\top \\ &= \left( \eta \sqrt{C^{jj}} \text{sgn}(Z_j)(|Z_j| - \lambda)^+ \bigg| j = 1, \dots, p \right)^\top, \quad (7.2.13) \end{aligned}$$

其中 \( Z_j = \frac{\sqrt{n}}{\eta \sqrt{C^{jj}}} \hat{\beta}_{jn}^{\text{UR}} \)。

注意

$$\sqrt{n}\hat{\beta}_{jn}^{\text{LassoR}}(\lambda) = \begin{cases} \eta \sqrt{C^{jj}}(Z_j - \lambda \text{sgn}(Z_j)), & \text{if } |Z_j| > \lambda, \\ 0, & \text{otherwise.} \end{cases}$$

设 \( |Z_1| > \lambda, \dots, |Z_{p_1}| > \lambda\)，其余 \( p_2 \) 个分量为 \( 0\)。则

$$\sqrt{n}\hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda) = (\eta \sqrt{C^{jj}}(Z_j - \lambda \text{sgn}(Z_j)), j = 1, \dots, p_1, \mathbf{0}^\top)^\top$$

这是 LASSO R 估计量的向量。

接下来，我们考虑 \(\boldsymbol{\beta}\) 的岭回归 R 估计量。根据 Saleh et al. (2019)，它由以下公式给出

\(\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}(k)} = (\boldsymbol{I}_p + k\mathbf{C}^{-1})^{-1}\hat{\boldsymbol{\beta}}_n^{\text{UR}}, \quad (7.2.14)\)

其中岭回归参数 \(k > 0\)。

利用定理 7.1 边缘理论的结果，我们可以定义随后的岭回归 R 估计量为

\(\hat{\boldsymbol{\beta}}_{1n}^{\text{ridgeR}(k)} = (\boldsymbol{I}_{p_1} + k\mathbf{C}_{11:2}^{-1})^{-1}\hat{\boldsymbol{\beta}}_{1n}^{\text{UR}} \quad (7.2.15)\)

\(\hat{\boldsymbol{\beta}}_{2n}^{\text{ridgeR}(k)} = (\boldsymbol{I}_{p_2} + k\mathbf{C}_{22:1}^{-1})^{-1}\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}}, \quad (7.2.16)\)

分别。

如果怀疑 \(\boldsymbol{\beta}_2 = \mathbf{0}\) 可能成立，则岭回归 R 估计量的形式为

\(\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}(k)} = \left( \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}^\top}, \hat{\boldsymbol{\beta}}_{2n}^{\text{ridgeR}(k)^\top} \right)^\top . \quad (7.2.17)\)

最后，作为特例，当 \(\boldsymbol{\beta}_2 = \mathbf{0}\) 时，我们有以下简单形式

\(\hat{\boldsymbol{\beta}}_n^{\text{ridgeR}(k)} = \underset{(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) \in \mathbb{R}^p}{\text{argmin}} \{ D_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) + k\|\boldsymbol{\beta}_2\|^2 \}
= \left( \hat{\boldsymbol{\beta}}_{1n}^{\text{UR}^\top}, \frac{1}{1+k}\hat{\boldsymbol{\beta}}_{2n}^{\text{UR}^\top} \right)^\top . \quad (7.2.18)\)

我们还可以定义弹性网（Enet）R 估计量为

\(\hat{\boldsymbol{\beta}}_n^{\text{EnetR}}(\lambda, \alpha) = \underset{\boldsymbol{\beta} \in \mathbb{R}^p}{\text{argmin}} \left\{ D_n(\boldsymbol{\beta}_1, \boldsymbol{\beta}_2) + \lambda \left[ \alpha \eta \mathbf{1}_p^\top \mathbf{C}^{\frac{1}{2}} |\boldsymbol{\beta}| + \frac{1}{2}(1-\alpha) \boldsymbol{\beta}^\top \mathbf{C} \boldsymbol{\beta} \right] \right\}
= \left[ \boldsymbol{I}_p + \lambda(1-\alpha)\mathbf{C}^{-1} \right]^{-1} \hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda\alpha),\)

其中

\(\hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda\alpha) = \left( \text{sgn}(\hat{\beta}_{jn}^{\text{UR}}) \left( |\hat{\beta}_{jn}^{\text{UR}}| - \lambda \alpha \eta \sqrt{C^{jj}} \right)^+ \mid j=1, \dots, p \right)^\top .\)

对于正交归一情况，其中 \(\mathbf{C} = \boldsymbol{I}_p\)，Enet R 估计量的形式为

\(\hat{\boldsymbol{\beta}}_n^{\text{EnetR}}(\lambda, \alpha) = [1 + \lambda(1-\alpha)]^{-1} \hat{\boldsymbol{\beta}}_n^{\text{LassoR}}(\lambda\alpha)
= [1 + \lambda(1-\alpha)]^{-1} \left( \text{sgn}(\hat{\beta}_{jn}^{\text{UR}}) \left( |\hat{\beta}_{jn}^{\text{UR}}| - \lambda \alpha \eta \right)^+ ; j=1, \dots, p \right)^\top .\)

