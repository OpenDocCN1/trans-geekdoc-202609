

| Y | X | P/N | 名称 | 模型 | 精确 |
|---|---|---|---|---|---|
| \(\mathbb{R}\) | - | P | 单样本 t 检验 | \(y \sim \mathcal{N}(\mu, \sigma^2)\) | \(\checkmark\) |
| \(\mathbb{R}\) | - | N | Wilcoxon 符号秩检验 | \(SR(y) \sim \mathcal{N}(\mu, \sigma^2)\) | \(N > 14\) |
| \((\mathbb{R}, \mathbb{R})\) | - | P | 配对样本 t 检验 | \(y_2 - y_1 \sim \mathcal{N}(\mu, \sigma^2)\) | \(\checkmark\) |
| \((\mathbb{R}, \mathbb{R})\) | - | N | Wilcoxon 配对秩和检验 | \(SR(y_2 - y_1) \sim \mathcal{N}(\mu, \sigma^2)\) | \(\checkmark\) |
| \(\mathbb{R}\) | \(\mathbb{R}\) | P | Pearson 相关 | \(y \sim \mathcal{N}(\beta_0 + \beta_1 x, \sigma^2)\) | \(\checkmark\) |
| \(\mathbb{R}\) | \(\mathbb{R}\) | N | Spearman 相关 | \(R(y) \sim \mathcal{N}(\beta_0 + \beta_1 R(x), \sigma^2)\) | \(N > 10\) |
| \(\mathbb{R}\) | \(\{0, 1\}\) | P | 双样本 t 检验 | \(y \sim \mathcal{N}(\beta_0 + \beta_1 x, \sigma^2)\) | \(\checkmark\) |
| \(\mathbb{R}\) | \(\{0, 1\}\) | P | Welch's t 检验 | \(y \sim \mathcal{N}(\beta_0 + \beta_1 x, \sigma_x^2)\) | \(\checkmark\) |
| \(\mathbb{R}\) | \(\{0, 1\}\) | N | Mann-Whitney U 检验 | \(SR(y) \sim \mathcal{N}(\beta_0 + \beta_1 x, \sigma_x^2)\) | \(N > 11\) |
| \(\mathbb{R}\) | \([J]\) | P | 单因素方差分析 | \(y \sim \mathcal{N}(f_{\text{aov}}(x; \boldsymbol{\beta}), \sigma^2)\) | \(\checkmark\) |
| \(\mathbb{R}\) | \([J]\) | N | Kruskal-Wallis 检验 | \(R(y) \sim \mathcal{N}(f_{\text{aov}}(x; \boldsymbol{\beta}), \sigma^2)\) | \(N > 11\) |
| \(\mathbb{R}\) | \([J] \times [K]\) | N | 双因素方差分析 | \(y \sim \mathcal{N}(f_{\text{aov2}}(x_1, x_2; \boldsymbol{\beta}), \sigma^2)\) | \(\checkmark\) |

表 3.2: 许多常见的统计检验等同于对简单线性模型参数进行推断。这里 P/N 表示参数检验与非参数检验；我们通过使用秩函数 \(R(y)\) 或符号秩函数 \(SR(y)\) 来近似后者。最后一列标记为 "exact"，指定了该近似足够准确、无法与精确结果区分开来的样本量。当输入变量为分类变量时，\(x_1 \in [J]\)，其中 \([J] = \{1, \dots, J\}\)，我们使用方差分析函数 \(f_{\text{aov}}(x_1, \boldsymbol{\beta})\) 来定义输出的均值。当有两个分类输入时，\(x_1 \in [J]\) 和 \(x_2 \in [K]\)，我们使用 \(f_{\text{aov2}}(x_1, x_2; \boldsymbol{\beta})\)。改编自 https://lindeloev.github.io/tests-as-linear/ 的速查表。

其中 \(\boldsymbol{\mu} = [\mu_1, \mu_2]\)，并且

\(\boldsymbol{\Sigma} = \begin{pmatrix} \sigma_1^2 & \rho\sigma_1\sigma_2 \\ \rho\sigma_1\sigma_2 & \sigma_2^2 \end{pmatrix}\) (3.333)

我们对 \(\mu_j\) 和 \(\sigma_j\) 使用相同的（数据驱动）先验，并对相关性使用均匀先验，\(p(\rho) = \text{Unif}(-1, 1)\)，遵循 [BMM00]。一旦指定了模型，我们就可以以通常的方式进行后验推断，并计算 \(p(\rho > 0 | \mathcal{D})\) 等量。

## 3.10.3 常见统计检验对应于线性模型中的推断

我们现在已经看到了许多不同的检验，可能不清楚在什么情况下使用什么检验。幸运的是，[Lin19] 指出，许多最常见的检验都可以精确（或近似）地表示为关于广义线性模型或 GLM 参数的推断（无论是贝叶斯还是频率派，有关 GLM 的详情见第 15 章）。这种方法更易于理解且更灵活，如 [Kru15; GHV20b] 等文中详细讨论。我们在表 3.2 和下面的讨论中总结了一些这些结果。

### 3.10.3.1 使用秩变换近似非参数检验

使用“非参数检验”很常见，它将标准检验推广到数据不一定服从高斯分布或 Student 分布的场景。近似此类检验的一种简单方法是用原始数据的顺序统计量替换原始数据，然后应用标准参数检验，如 [CJ81] 所提。对于 \(N \ge 10\) 的样本量，这对标准非参数检验给出了良好的近似。具体来说，我们可以计算一个 **秩变换**，即将数据点（假设为标量）排序，然后用其在排序中的整数值替换。例如，\(\mathcal{D} = (3.6, 3.4, -5.0, 8.2)\) 的秩变换为 \(R(\mathcal{D}) = (3, 2, 1, 4)\)。或者，我们可以使用 **符号秩**，它先按绝对值大小对值进行排序，然后附加相应的符号。例如，\(\mathcal{D} = (3.6, 3.4, -5.0, 8.2)\) 的符号秩变换为 \(SR(\mathcal{D}) = (2, 1, -3, 4)\)。现在我们可以轻松地将参数模型（如 GLM）拟合到秩变换后的数据上，如图 3.28 所示。（在 [Doo+17] 中，他们对此提出了一种贝叶斯解释，其中顺序统计量被视为对底层隐性连续量的观察，并对其进行推断。）我们将在下面的章节中使用此技巧。

![](img/ca72c1626f4850f058a9edc138c1ac73_168_0.png)

图 3.28: 对某些数据（左）及其秩变换版本（右）应用一维线性回归的示例。由 linreg_rank_stats.ipynb 生成。

### 3.10.3.2 一个或两组上的度量预测变量（t 检验）

假设我们有一些数据 \(\mathcal{D} = \{y_n \sim \mathcal{N}(\mu, \sigma^2) : n = 1 : N\}\)，我们有兴趣检验原假设 \(\mu = 0\)。我们可以将其建模为带有常数输入（偏置项）且无协变量的线性回归模型：\(p(y_n|\boldsymbol{\theta}) = \mathcal{N}(y_n|\beta_0, \sigma^2)\)，其中 \(\beta_0 = \mu\)。现在我们可以以 GLM 的通常方式对 \(\beta_0\) 进行推断，然后进行假设检验。这等同于第 3.10.2.6 节讨论的 **单样本 t 检验**。对于非参数版本，我们可以使用符号秩变换对数据进行转换，从而拟合 \(SR(y_n) \sim \mathcal{N}(\mu, \sigma^2)\)。结果与 **Wilcoxon 符号秩检验** 非常接近。现在假设我们有两组的配对数据，\(\mathcal{D} = \{(y_{1n}, y_{2n}) : n = 1 : N\}\)，其中我们假设 \(y_{jn} \sim \mathcal{N}(\mu_j, \sigma^2)\)。我们有兴趣检验 \(\mu_1 = \mu_2\) 是否成立。一个更简单的替代方法是定义 \(y_n = y_{2n} - y_{1n}\)，我们使用 \(y_n \sim \mathcal{N}(\mu, \sigma^2)\) 对其建模。然后我们可以使用 **配对样本 t 检验**（在第 3.10.2.6 节中讨论）来检验 \(\mu = 0\) 是否成立。或者，我们可以对 \(SR(y_n)\) 进行推断，以得到 **Wilcoxon 配对秩和检验**。为了处理我们有两组非配对数据的情况，我们可以将数据表示为 \(\mathcal{D} = \{(x_n, y_n) : n = 1 : N\}\)，其中 \(x_n \in \{0, 1\}\) 表示输入属于组 0 还是组 1。我们假设数据来自以下线性回归模型：\(p(y_n|x_n) \sim \mathcal{N}(\beta_0 + \beta_1 x_n, \sigma^2)\)。现在我们可以以 GLM 的通常方式对 \(\boldsymbol{\beta}\) 进行推断，然后进行假设检验。这等同于第 3.10.2.8 节讨论的 **双样本 t 检验**。在非参数设置中，我们可以用 \(y\) 的符号秩变换替换 \(y\) 并使用模型 \(SR(y) \sim \mathcal{N}(\beta_0 + \beta_1 x, \sigma^2)\)。这与 **Mann-Whitney U 检验** 大致相同。

![](img/ca72c1626f4850f058a9edc138c1ac73_169_0.png)

图 3.29: 4 组单因素方差分析的示例。我们有兴趣检验红线的斜率是否为 0，这意味着所有组的均值相同。由 anova.ipynb 生成。

### 3.10.3.3 带度量预测因子的度量预测变量（相关性检验）

在本节中，我们假设数据形式为 \(\mathcal{D} = \{(x_n, y_n) : n = 1 : N\}\)，其中 \(x_n \in \mathbb{R}\) 和 \(y_n \in \mathbb{R}\) 具有 **Pearson 相关系数** \(\rho\)。我们有兴趣检验假设 \(\rho = 0\)。

我们可以使用第 3.10.2.9 节中的“定制”贝叶斯方法。或者，我们可以使用简单线性回归对其建模，写出 \(y_n \sim \mathcal{N}(\beta_0 + \beta_1 x, \sigma^2)\)。如果我们将输出 \(Y\) 缩放为标准差为 1，则会发现 \(\beta_1 = \rho\)，如 [Mur22, Sec 11.2.3.3] 所示。因此，我们可以使用 \(p(\beta_1|\mathcal{D})\) 来对 \(\rho\) 进行推断。

在非参数设置中，我们计算 \(x\) 和 \(y\) 的秩变换，然后如上所述继续。**Spearman 等级相关系数** 是秩变换数据上的 Pearson 相关系数。虽然 Pearson 相关性有助于评估线性关系的强度，但 Spearman 相关性可用于评估一般单调关系，无论是线性还是非线性。

如果我们有多个度量预测因子（即，\(\boldsymbol{x}_n \in \mathbb{R}^D\)），可以使用多元线性回归而不是简单线性回归。然后我们可以从回归权重的后验推导偏相关系数的后验。

### 3.10.3.4 带一个名义预测因子的度量预测变量（单因素方差分析）

在本节中，我们考虑这种情况：我们有一些数据 \(\mathcal{D} = \{(x_n, y_n) : n = 1 : N\}\)，其中 \(x_n \in \{1, \dots, J\}\) 表示输入属于哪一组。（这种离散分类变量通常称为 **因子**。）我们假设数据来自以下线性回归模型：\(p(y_n|x_n = j) \sim \mathcal{N}(\mu_j, \sigma^2)\)。我们有兴趣检验所有 \(\mu_j\) 是否相同。这传统上是使用 **单因素方差分析检验** 进行的，其中 ANOVA 代表 “analysis

