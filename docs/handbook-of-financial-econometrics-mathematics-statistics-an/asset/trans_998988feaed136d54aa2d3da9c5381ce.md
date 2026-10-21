
特征方程的

$$1 - \sum_{i=1}^{q} \left(\alpha_{i1} + \frac{1}{2}\alpha_{i2}\right) \lambda^{i} - \sum_{j=1}^{p} \beta_{j} \lambda^{j} = 0 \tag{123.11}$$

绝对值大于1。

### 123.2.2.2 指数GARCH (EGARCH) (p, q) 模型

Nelson (1991) 提出了一种捕捉杠杆效应的另一模型

$$\log(h_t) = \omega + \sum_{i=1}^{q} \alpha_i g(z_{t-i}) + \sum_{j=1}^{p} \beta_j \log(h_{t-j}), \tag{123.12}$$

其中 \(g(z_{t-i}) = \kappa z_{t-i} + \varsigma(|z_{t-i}| - E(|z_{t-i}|))\)，且 \(\omega\)、\(\alpha_i\)、\(\beta_j\)、\(\kappa\) 和 \(\varsigma\) 为实数。该设定允许波动率的非对称性，并且通过指定对数波动率，避免了 \(\omega\)、\(\alpha_i\) 和 \(\beta_j\) 参数的正性限制。过程 \(\{h_t\}\) 在特征方程

$$1 - \sum_{j=1}^{p} \beta_j \lambda^{j} = 0 \tag{123.13}$$

的所有解的绝对值大于1时平稳。

## 123.2.3 GARCH(p, q) 模型的估计

GARCH(p, q) 模型中方程 (123.1) 和 (123.4) 的参数向量为 \(\theta = (\theta_1, \dots, \theta_{k+p+q+2}) = (\mu, \gamma_1, \dots, \gamma_k; \omega, \alpha_1, \dots, \alpha_q; \beta_1, \dots, \beta_p)'\)。参数的真实值未知并记为

$$\theta_0 = (\theta_{01}, \dots, \theta_{0k+p+q+2}) = (\mu_0, \gamma_{01}, \dots, \gamma_{0k}; \omega_0, \alpha_{01}, \dots, \alpha_{0q}; \beta_{01}, \dots, \beta_{0p})'.$$

GARCH(p, q) 模型的阶数（即 k、p 和 q）假定已知以估计参数。尽管我们不对标准化随机变量 \(z_t\) 假设任何特定分布，但我们使用正态分布。则拟似然为

$$L_T(\theta) = L_T(\theta; y_1, \dots, y_T) = \prod_{t=1}^{T} \frac{1}{\sqrt{2\pi \tilde{h}_t}} \exp\left(-\frac{\tilde{\varepsilon}_t^{2}}{2\tilde{h}_t}\right), \tag{123.14}$$

其中

$$\tilde{\varepsilon}_t = \tilde{\varepsilon}_t(\theta) = y_t - \mu - \sum_{i=1}^{k} \gamma_i y_{t-i}, \quad \text{and} \quad \tilde{h}_t = \tilde{h}_t(\theta) = \omega + \sum_{i=1}^{q} \alpha_i \tilde{\varepsilon}_{t-i}^2 + \sum_{j=1}^{p} \beta_j \tilde{h}_{t-j}. \tag{123.15}$$

如果初始值给定为 \(y_0,\ldots ,y_{1-k-p},\tilde{\varepsilon}_0,\ldots ,\tilde{\varepsilon}_{-q},h_0,\ldots ,h_{1-p}\)，则对任意 \(\theta\)，\(\tilde{h}_t\) 和 \(\tilde{\varepsilon}_t\) 对于 \(t=1,\ldots ,T\) 的值可从方程 (123.15) 计算得到。拟极大似然估计量 (QMLE) 由解 \(\hat{\theta}_T\) 定义，满足 \(\hat{\theta}_T = \arg \max_{\theta} L_T(\theta)\)。对 \(L_T(\theta)\) 取对数，解等价于

$$\hat{\theta}_T = \hat{\theta}(y_1,\ldots ,y_T) = \arg\min_{\theta} l_T(\theta), \tag{123.16}$$

其中

$$l_T(\theta) = l(\theta; y_1,\ldots ,y_T) = \frac{1}{T}\sum_{t=1}^{T} l_t, \quad \text{and} \quad l_t = \log(\tilde{h}_t) + \frac{\tilde{\varepsilon}_t^2}{\tilde{h}_t}. \tag{123.17}$$

该估计方法适用于 GJR 和 EGARCH 的其他模型，尽管本文未明确讨论这些模型。

## 123.2.4 GARCH(p,q) 的 QMLE 的渐近性质

在合适的正则条件下，QMLE 是强相合的：

$$\hat{\theta}_T \to \theta_0 \text{ (almost surely), as } T \to \infty \tag{123.18}$$

并且渐近正态分布<sup>5</sup>：

$$\sqrt{T}(\hat{\theta}_T - \theta_0) \to N(0,\Sigma), \quad \text{as} \quad T \to \infty, \tag{123.19}$$

其中 \(\Sigma = J^{-1} I J^{-1}\)，

$$I = E_{\theta_0}\left(\frac{\partial l_t(\theta_0)}{\partial\theta}\frac{\partial l_t(\theta_0)}{\partial\theta'}\right), \quad \text{and} \quad J = E_{\theta_0}\left(\frac{\partial^2 l_t(\theta_0)}{\partial\theta\partial\theta'}\right). \tag{123.20}$$

<sup>5</sup>参见 Francq 和 Zakoian (2010) 第 7 章中的定理 7.4 和 7.5 以获得严格的正则条件和证明。QMLE 的相合性和渐近正态性的证明在数学上非常复杂。

### 表 123.1：条件协方差 (\(H_t\)) 中的参数个数。

| n | 2 | 4 | 10 |
|---|---|---|---|
| VEC-GARCH | 21 | 210 | 6105 |
| BEKK-GARCH(K = 1) | 11 | 42 | 255 |
| BEKK-GARCH(K = 2) | 19 | 74 | 455 |
| CCC-GARCH | 11 | 42 | 255 |
| CCC-GARCH(diagonal) | 7 | 18 | 75 |
| DCC-GARCH | 13 | 44 | 257 |
| DCC-GARCH(diagonal) | 9 | 20 | 77 |

注：GARCH 的阶数为 p = q = 1，n 为变量的维度数。所有模型的 VAR(k) 参数个数相同，已从表中排除。DCC-GARCH 将在第 123.4 节中解释。

对角 VECH (DVECH)，由 Bollerslev 等 (1988) 提出，以及 Engle 和 Kroner (1995) 的 BEKK (Baba–Engle–Kraft–Kroner) 模型。BEKK 模型的变化包括 Ding 和 Engle (2001) 的对角 BEKK 模型、Noureldin 等 (2014) 的旋转 BEKK 模型、Noureldin 等 (2014) 的对角旋转 BEKK、Ding 和 Engle (2001) 的标量 BEKK 以及 Noureldin 等 (2014) 的标量旋转 BEKK。

DVECH 模型的应用见 Bauwens 等 (2007) 和 Ledoit 等 (2003)，BEKK 模型的应用包括 Beirne 等 (2013) 和 Hecq 等 (2016)。

MGARCH 模型的第二类基于将协方差矩阵分解为条件方差和相关性的乘积。Bollerslev (1990) 的常数条件相关 (CCC) 模型和 Engle (2002) 的动态条件相关 (DCC) 模型属于第二类。特别是，DCC 模型以多种方式被修改，例如 Aielli (2013) 的修正 DCC (cDCC) 模型、Bauwens 等 (2016) 的 Almon-shuffle DCC 模型、Hafner 和 Franses (2009) 的广义 DCC 模型以及 Noureldin 等 (2014) 的旋转 DCC 模型。CCC 和 DCC 模型在实证研究中被最广泛使用。参见 Amado 和 Terasvirta (2014) 以及 Laurent 等 (2013) 关于 CCC 模型的最新实证应用，以及 Tsukuda 等 (2017)、Aielli 和 Caporin (2014) 和 Audrino (2014) 等关于 DCC 模型的应用。

Bauwens 等 (2006)、Silvennoinen 和 Terasvirta (2009) 以及 Francq 和 Zakoian (2010, 第 11 章) 提供了 GARCH 模型多元扩展的最新有用综述。我们不会详细回顾所有多元 GARCH 模型的发展。相反，我们将注意力限制在应用观点中最重要的一些模型上，并考虑这些模型如何解决上述矛盾要求。

## 123.3.1 代表性多元 GARCH 模型

我们从多元（向量）自回归 k 阶或 VAR(k) 模型开始

$$Y_t = \mu + \sum_{i=1}^{k} \Gamma_i Y_{t-i} + \varepsilon_t, \quad t = 1, \ldots, T, \tag{123.21}$$

其中 \(Y_t = (Y_{1t}, \ldots, Y_{nt})'\) 是 n 维向量，且 \(\mu, \Gamma_i, \varepsilon_t\) 相应定义。我们假设特征方程

$$\left| I - \sum_{i=1}^{k} \Gamma_i \lambda^i \right| = 0 \tag{123.22}$$

的所有解的绝对值大于1。在该条件下，若 \(\{\varepsilon_t\}\) 平稳，则过程 \(\{Y_t\}\) 平稳。

方程 (123.21) 中的过程 \(\{\varepsilon_t\}\) 是多元 GARCH 模型，如果其前两个条件矩存在并满足：

$$(i) \ E(\varepsilon_t \mid I_{t-1}) = 0, \quad (ii) \ H_t = \mathrm{Var}(\varepsilon_t \mid I_{t-1}), \tag{123.23}$$

其中 \(\varepsilon_t = H_t^{1/2} z_t\)，\(H_t > 0\)（正定），\(z_t \sim \text{i.i.d.}\)，\(E(z_t) = 0\)，\(\mathrm{Var}(z_t) = I\)，且 \(I_{t-1}\) 在 (123.23) 中表示截至时间 \(t - 1\) 可用的信息。\(Y_t\) 的条件期望为

$$E(Y_t \mid I_{t-1}) = \mu + \sum_{i=1}^{k} \Gamma_i Y_{t-i}. \tag{123.24}$$

\(n \times n\) 条件方差-协方差矩阵 \(H_t\) 为正定，且有 \(n \times (n + 1)/2\) 个不同元素。文献中提出了关于 \(H_t\) 过程的许多不同设定方式。

### 123.3.1.1 VEC-GARCH(p,q) 模型

用 \(\mathrm{vech}(\cdot)\) 表示将自变量方阵的下三角部分堆叠起来的算子（若 \(A = (a_{ij})\)，则 \(\mathrm{vech}(A) = (a_{11}, \ldots, a_{n1}, a_{22}, \ldots, a_{n2}, \ldots, a_{nn})'\)）。由 Bollerslev、Engle 和 Wooldridge (1988) 提出的 VEC-GARCH(p,q) 模型定义为

$$\mathrm{vech}(H_t) = \omega + \sum_{i=1}^{q} A^{(i)} \mathrm{vech}(\varepsilon_{t-i} \varepsilon_{t-i}') + \sum_{j=1}^{p} B^{(j)} \mathrm{vech}(H_{t-j}). \tag{123.25}$$

其中 \(\omega\) 是大小为 \(\{n(n + 1)/2\} \times 1\) 的向量，且 \(A^{(i)}\) 和 \(B^{(j)}\) 是 \(\{n(n + 1)/2\} \times \{n(n + 1)/2\}\) 的矩阵。方程 (123.21) 中模型的參數和
