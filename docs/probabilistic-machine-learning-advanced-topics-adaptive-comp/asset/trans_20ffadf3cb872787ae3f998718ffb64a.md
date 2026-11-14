


且

\(\mathbb{V} [y_n] = \frac{d^2 A}{d \eta_n^2} = N_n \mu_n (1 - \mu_n)\) (15.17)

二项回归的示例见第 15.3.9 节。

## 15.1.1.3 泊松回归

若响应变量为整数计数，\(y_n \in \{0, 1, ...\}\)，我们可以使用**泊松回归**，其定义为

\(p(y_n|\boldsymbol{x}_n, \boldsymbol{w}) = \text{Poi}(y_n|\exp(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n))\) (15.18)

其中

\(\text{Poi}(y|\mu) = e^{-\mu} \frac{\mu^y}{y!}\) (15.19)

为泊松分布。泊松回归广泛应用于生物统计学领域，其中 \(y_n\) 可能表示给定人员或地点的疾病数量，或高通量测序环境中基因组位点的读数数量（例如，参见 [Kua+09]）。

对数概率密度函数由以下公式给出

\(\log p(y_n|\boldsymbol{x}_n, \boldsymbol{w}) = y_n \log \mu_n - \mu_n - \log(y_n!)\) (15.20)

其中 \(\mu_n = \exp(\boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n)\)。因此，GLM 形式如下

\(\log p(y_n|\boldsymbol{x}_n, \boldsymbol{w}) = y_n \eta_n - A(\eta_n) + h(y_n)\) (15.21)

其中 \(\eta_n = \log(\mu_n) = \boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n\)，\(A(\eta_n) = \mu_n = e^{\eta_n}\)，且 \(h(y_n) = -\log(y_n!)\)。因此

\(\mathbb{E} [y_n] = \frac{dA}{d \eta_n} = e^{\eta_n} = \mu_n\) (15.22)

且

\(\mathbb{V} [y_n] = \frac{d^2 A}{d \eta_n^2} = e^{\eta_n} = \mu_n\) (15.23)

## 15.1.1.4 零膨胀泊松回归

在许多形式的计数数据中，观察到的 0 的数量大于模型所预期的数量，即使在考虑预测因素之后也是如此。直觉上，这是因为可能存在许多产生无结果的方式。例如，考虑预测某产品的销售数据。如果销售量为 0，是意味着该产品不受欢迎（因此需求很低），还是说它只是卖完了（意味着需求高，但供应为零）？基因组学、流行病学等领域也存在类似问题。

为处理此类情况，通常使用**零膨胀泊松**或**ZIP**模型。该模型的似然函数是两个分布的混合：0 处的尖峰和标准泊松分布。形式上，我们定义

\(\text{ZIP}(y|\rho, \lambda) = \begin{cases} \rho + (1 - \rho) \exp(-\lambda) & \text{if } y = 0 \\ (1 - \rho) \frac{\lambda^y \exp(-\lambda)}{y!} & \text{if } y > 0 \end{cases}\)

这里，\(\rho\) 是选择尖峰的先验概率，\(\lambda\) 是泊松分布的速率。我们可以看到，生成 0 有两种“机制”：要么以概率 \(\rho\) 选择尖峰，要么以概率 \(1 - \rho\) 仅仅因为泊松速率很低而生成零计数。（后一种情况的概率为 \(\lambda^0 e^{-\lambda} / 0! = e^{-\lambda}\)。）

## 15.1.2 具有非标准链接函数的 GLM

我们已看到，输出分布的均值参数由 \(\mu = \ell^{-1}(\eta)\) 给出，其中函数 \(\ell\) 为链接函数。该函数有多种选择，如下所述。

**标准链接函数** \(\ell\) 满足 \(\theta = \ell(\mu)\) 的性质，其中 \(\theta\) 为标准（自然）参数。因此

\(\theta = \ell(\mu) = \ell(\ell^{-1}(\eta)) = \eta\)

这是目前为止我们所做的假设。例如，对于伯努利分布，标准参数是对数几率 \(\eta = \log(\mu / (1 - \mu))\)，由 logit 变换给出

\(\eta = \ell(\mu) = \text{logit}(\mu) = \log \left( \frac{\mu}{1 - \mu} \right)\)

其反函数是 Sigmoid 或逻辑函数

\(\mu = \ell^{-1}(\eta) = \sigma(\eta) = 1 / (1 + e^{-\eta})\)

但是，我们可以自由使用其他类型的链接函数。例如，在第 15.4 节中，我们使用

\(\eta = \ell(\mu) = \Phi^{-1}(\mu)\)

\(\mu = \ell^{-1}(\eta) = \Phi(\eta)\)

这被称为**Probit 链接函数**。

另一种有时用于二元响应的链接函数是**互补 log-log**函数

\(\eta = \ell(\mu) = \log(-\log(1 - \mu))\)

这用于此类应用：我们要么观察到 0 个事件（记为 \(y=0\)），要么观察到 1 个或多个事件（记为 \(y=1\)），其中假设事件遵循速率为 \(\lambda\) 的泊松分布。

令 \(E\) 为事件数量。泊松假设意味着 \(p(E=0) = \exp(-\lambda)\)，因此

\(p(y=0) = (1 - \mu) = p(E=0) = \exp(-\lambda)\)

因此 \(\lambda = -\log(1 - \mu)\)。当 \(\lambda\) 是协变量的函数时，我们需要确保其为正，所以使用 \(\lambda = e^\eta\)，因此

\(\eta = \log(\lambda) = \log(-\log(1 - \mu))\)

## 15.1.3 最大似然估计

GLM 可以使用与拟合逻辑回归相似的方法进行拟合。特别是，负对数似然（忽略常数项）具有以下形式：

\(\text{NLL}(\boldsymbol{w}) = -\log p(\mathcal{D}|\boldsymbol{w}) = -\frac{1}{\sigma^2} \sum_{n=1}^N \ell_n\)

其中

\(\ell_n \triangleq \eta_n y_n - A(\eta_n)\)

其中 \(\eta_n = \boldsymbol{w}^\top \boldsymbol{x}_n\)。为简化记法，我们假设 \(\sigma^2 = 1\)。单个项的梯度可计算如下：

\(\boldsymbol{g}_n \triangleq \frac{\partial \ell_n}{\partial \boldsymbol{w}} = \frac{\partial \ell_n}{\partial \eta_n} \frac{\partial \eta_n}{\partial \boldsymbol{w}} = (y_n - A'(\eta_n)) \boldsymbol{x}_n = (y_n - \mu_n) \boldsymbol{x}_n\)

其中 \(\mu_n = f(\boldsymbol{w}^\top \boldsymbol{x}_n)\)，且 \(f\) 是从标准参数映射到均值参数的反链接函数。（例如，在逻辑回归的情况下，我们有 \(\mu_n = \sigma(\boldsymbol{w}^\top \boldsymbol{x})\)。）Hessian 矩阵由以下公式给出

\(\mathbf{H} = \frac{\partial^2}{\partial \boldsymbol{w} \partial \boldsymbol{w}^\top} \text{NLL}(\boldsymbol{w}) = - \sum_{n=1}^N \frac{\partial \boldsymbol{g}_n}{\partial \boldsymbol{w}^\top}\)

其中

\(\frac{\partial \boldsymbol{g}_n}{\partial \boldsymbol{w}^\top} = \frac{\partial \boldsymbol{g}_n}{\partial \mu_n} \frac{\partial \mu_n}{\partial \boldsymbol{w}^\top} = -\boldsymbol{x}_n f'(\boldsymbol{w}^\top \boldsymbol{x}_n) \boldsymbol{x}_n^\top\)

因此

\(\mathbf{H} = \sum_{n=1}^N f'(\eta_n) \boldsymbol{x}_n \boldsymbol{x}_n^\top\)

例如，在逻辑回归的情况下，\(f(\eta_n) = \sigma(\eta_n) = \mu_n\)，且 \(f'(\eta_n) = \mu_n(1 - \mu_n)\)。一般而言，我们看到 Hessian 矩阵为正定，因为 \(f'(\eta_n) > 0\)；因此负对数似然是凸的，所以 GLM 的 MLE 是唯一的（假设对所有 \(n\) 都有 \(f'(\eta_n) > 0\)）。

对于小型数据集，我们可以使用**迭代重加权最小二乘法**或**IRLS**算法（一种牛顿法形式）来计算 MLE（例如，参见 [Mur22, Sec 10.2.6]）。对于大型数据集，我们可以使用 SGD。（在实践中，将 SGD 与自动调节步长的方法相结合通常很有用，例如 [Loi+21]。）

## 15.1.4 贝叶斯推断

最大似然估计提供参数的点估计，但不传递任何不确定性概念，这对于假设检验（如第 3.10.3 节所解释）以及避免过拟合都很重要。为了计算不确定性，我们将对参数进行贝叶斯推断。为此，我们首先需要指定一个先验分布。选择合适的先验取决于链接函数的形式。例如，对截距项 \(\alpha \in \mathbb{R}\) 设置“平坦”或“无信息”先验，如果将 \(\alpha\) 传递通过 Sigmoid 函数，则不会转化为概率尺度上的无信息先验，如第 15.3.4 节所讨论。一旦选择了先验，我们就可以使用各种近似推断方法计算后验。对于小型数据集，HMC（第 12.5 节）最容易使用，因为你只需要写下对数似然和对数先验；然后我们可以使用 autograd 计算导数，并将其传递给 HMC 引擎（详情见例如 [BG13]）。

有许多标准软件包可用于（分层）GLM 的 HMC 分析，例如 Bambi (https://github.com/bambinos/bambi)，它是 PyMC/BlackJAX 之上的 Python 封装器；RStanARM (https://cran.r-project.org/web/packages/rstanarm/index.html)，它是 Stan 之上的 R 封装器；以及 BRMS (https://cran.r-project.org/web/packages/brms/index.html)，它是另一个 Stan 之上的 R 封装器。这些库支持一种方便的公式语法，最初由 R 语言创建，用于紧凑地指定模型形式，包括输入之间可能的交互项。

对于大型数据集，HMC 可能会很慢，因为它是一个全批量算法。在这种情况下，变分贝叶斯（例如，参见 [HOW11; TN13]）、期望传播（例如，参见 [KW18]）或更专门的算法（例如，[HAB17]）是最佳选择。

## 15.2 线性回归

线性回归是 GLM 的最简单情况，指以下模型：

\(p(y|x, \theta) = \mathcal{N}(y|w_0 + w^T x, \sigma^2)\) (15.39)

其中 \(\theta = (w_0, w, \sigma^2)\) 是模型的所有参数。（在统计学中，参数 \(w_0\) 和 \(w\) 通常表示为 \(\beta_0\) 和 \(\beta\)。）我们在本书的前作 [Mur22] 中对该模型做了详细介绍。在本节中，我们将简要讨论最大似然估计，然后重点介绍贝叶斯分析。

### 15.2.1 普通最小二乘法

根据方程 (15.39)，我们可以推导数据的负对数似然如下：

\(NLL(w, \sigma^2) = - \sum_{n=1}^N \log \left[ \left( \frac{1}{2\pi\sigma^2} \right)^{\frac{1}{2}} \exp \left( - \frac{1}{2\sigma^2} (y_n - w^T x_n)^2 \right) \right]\) (15.40)

\(= \frac{1}{2\sigma^2} \sum_{n=1}^N (y_n - \hat{y}_n)^2 + \frac{N}{2} \log(2\pi\sigma^2)\) (15.41)

其中我们定义了预测响应 \(\hat{y}_n \triangleq w^T x_n\)。在 [Mur22, Sec 11.2.2] 中，我们表明 MLE 由以下公式给出

\(\hat{w}_{mle} = (X^T X)^{-1} X^T y\) (15.42)

