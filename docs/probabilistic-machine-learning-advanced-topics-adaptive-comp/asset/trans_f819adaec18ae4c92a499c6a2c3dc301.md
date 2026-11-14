

![](img/ca72c1626f4850f058a9edc138c1ac73_916_0.png)

和未知的真实数据分布 $p^*$。回顾方程 (26.2)，在隐式模型中我们无法评估 $q_\theta(\boldsymbol{x})$，因此无法使用最大似然训练。由于隐式模型提供了采样程序，我们转而寻找仅使用模型样本的学习原则。

隐式模型中学习的任务是：从两组样本中判断它们的分布是否彼此接近，并量化它们之间的距离。我们可以将其视为一种基于比较的“双样本”或无似然学习方法。实现这一点的方法有很多，包括通过二分类使用分布偏差或距离、矩法以及其他方法。图 26.2 展示了不同基于比较学习方法的概览。

## 26.2.1 指导原则

我们正在寻找满足以下要求的目标函数 $\mathcal{D}(p^*, q)$：

- 1. 关于学习数据分布的保证：$\text{argmin}_q \mathcal{D}(p^*, q) = p^*$。
- 2. 只能使用来自数据分布和模型分布的样本进行评估。
- 3. 评估计算成本低。

许多分布距离和偏差满足第一项要求，因为按定义它们满足以下条件：

\[
\mathcal{D}(p^*, q) \ge 0; \quad \mathcal{D}(p^*, q) = 0 \iff p^* = q \tag{26.3}
\]

然而，许多分布距离和偏差无法满足另外两项要求：它们无法仅使用样本进行评估（例如 KL 散度），或者计算上不可处理（例如 Wasserstein 距离）。克服这些挑战的主要方法是通过引入比较模型来 *通过优化近似所需量*，该模型通常称为 **鉴别器** 或 **批评家** $D$，使得：

\[
\mathcal{D}(p^*, q) = \underset{D}{\text{argmax}} \mathcal{F}(D, p^*, q) \tag{26.4}
\]

其中 $\mathcal{F}$ 是一个仅通过样本依赖于 $p^*$ 和 $q$ 的泛函。在我们讨论的情况下，模型和批评家都是参数化的，参数分别为 $\boldsymbol{\theta}$ 和 $\boldsymbol{\phi}$；我们不是针对分布或函数进行优化，而是针对参数进行优化。对于批评家，这导致了优化问题 $\text{argmax}_{\boldsymbol{\phi}} \mathcal{F}(D_{\boldsymbol{\phi}}, p^*, q_0)$。对于模型参数 $\boldsymbol{\theta}$，精确目标 $\mathcal{D}(p^*, q_\theta)$ 被替换为通过使用 $D_{\boldsymbol{\phi}}$ 提供的可处理近似。一种确保 $\mathcal{F}(D_{\boldsymbol{\phi}}, p^*, q_\theta)$ 可以仅使用模型和未知数据分布的样本进行估计的便捷方法是仅在期望中依赖于两个分布：$\mathcal{F}(D_{\boldsymbol{\phi}}, p^*, q_\theta) = \mathbb{E}_{p^*(\boldsymbol{x})} f(\boldsymbol{x}, \boldsymbol{\phi}) + \mathbb{E}_{q_\theta(\boldsymbol{x})} g(\boldsymbol{x}, \boldsymbol{\phi})$ (26.5)，其中 $f$ 和 $g$ 是实值函数，其选择将定义 $\mathcal{F}$。对于隐式生成模型，这可以改写为使用采样路径 $\boldsymbol{x} = G_{\boldsymbol{\theta}}(\boldsymbol{z}), \, \boldsymbol{z} \sim q(\boldsymbol{z})$：$\mathcal{F}(D_{\boldsymbol{\phi}}, p^*, q_\theta) = \mathbb{E}_{p^*(\boldsymbol{x})} f(\boldsymbol{x}, \boldsymbol{\phi}) + \mathbb{E}_{q(\boldsymbol{z})} g(G_{\boldsymbol{\theta}}(\boldsymbol{z}), \boldsymbol{\phi})$ (26.6)，这可以通过蒙特卡洛估计来估算 $\mathcal{F}(D_{\boldsymbol{\phi}}, p^*, q_\theta) \approx \frac{1}{N} \sum_{i=1}^N f(\widehat{\boldsymbol{x}}_i, \boldsymbol{\phi}) + \frac{1}{M} \sum_{i=1}^M g(G_{\boldsymbol{\theta}}(\widehat{\boldsymbol{z}}_i), \boldsymbol{\phi}); \quad \widehat{\boldsymbol{x}}_i \sim p^*(\boldsymbol{x}); \quad \widehat{\boldsymbol{z}}_i \sim q(\boldsymbol{z})$ (26.7)。接下来，我们将看到如何实例化这些指导原则，以找到函数 $f$ 和 $g$ 从而得到可用于训练隐式模型的目标 $\mathcal{F}$：类概率估计（第 26.2.2 节）、$f$-偏差的界限（第 26.2.3 节）、积分概率度量（第 26.2.4 节）和矩匹配（第 26.2.5 节）。

## 26.2.2 使用二分类器进行密度比估计

比较两个分布 $p^*$ 和 $q_\theta$ 的一种方法是计算它们的密度比 $r(\boldsymbol{x}) = \frac{p^*(\boldsymbol{x})}{q_\theta(\boldsymbol{x})}$。如果且仅当比率在 $q_\theta$ 的支撑集上处处为 1 时，分布才相同。由于我们无法评估隐式模型的密度，因此必须根据上述建立的指导原则，开发仅从样本计算密度比的技术。幸运的是，我们可以使用第 2.7.5 节的技巧，将密度估计转换为二分类问题，从而写出 $\frac{p^*(\boldsymbol{x})}{q_\theta(\boldsymbol{x})} = \frac{D(\boldsymbol{x})}{1 - D(\boldsymbol{x})}$ (26.8)，其中 $D(\boldsymbol{x})$ 是训练用于区分来自 $p^*$ 和 $q_\theta$ 的样本的鉴别器或批评家。对于参数化分类，我们可以学习带参数 $\boldsymbol{\phi}$ 的鉴别器 $D_{\boldsymbol{\phi}}(\boldsymbol{x}) \in [0, 1]$。利用关于概率分类的知识和见解，我们可以通过最小化任何合适的评分规则 [GR07b]（另见第 14.2.1 节）来学习参数。对于熟悉的 Bernoulli 对数损失（或二元交叉熵损失），我们得到目标：

\[
V(q_\theta, p^*) = \text{arg max}_{\boldsymbol{\phi}} \mathbb{E}_{p(\boldsymbol{x}|y) p(y)} [y \log D_{\boldsymbol{\phi}}(\boldsymbol{x}) + (1 - y) \log(1 - D_{\boldsymbol{\phi}}(\boldsymbol{x}))] = \text{arg max}_{\boldsymbol{\phi}} \mathbb{E}_{p(\boldsymbol{x}|y=1)p(y=1)} \log D_{\boldsymbol{\phi}}(\boldsymbol{x}) + \mathbb{E}_{p(\boldsymbol{x}|y=0)p(y=0)} \log(1 - D_{\boldsymbol{\phi}}(\boldsymbol{x})) \tag{26.9}
\]

\[
= \text{arg max}_{\boldsymbol{\phi}} \frac{1}{2} \mathbb{E}_{p^*(\boldsymbol{x})} \log D_{\boldsymbol{\phi}}(\boldsymbol{x}) + \frac{1}{2} \mathbb{E}_{q_\theta(\boldsymbol{x})} \log(1 - D_{\boldsymbol{\phi}}(\boldsymbol{x})) \tag{26.10}
\]

| 损失 | 目标函数 ($D := D(\boldsymbol{x}; \boldsymbol{\phi}) \in [0, 1]$) |
| :--- | :--- |
| Bernoulli 损失 | $\mathbb{E}_{p^*(\boldsymbol{x})}[\log D] + \mathbb{E}_{q_\theta(\boldsymbol{x})}[\log(1 - D)]$ |
| Brier 得分 | $\mathbb{E}_{p^*(\boldsymbol{x})}[-(1 - D)^2] + \mathbb{E}_{q_\theta(\boldsymbol{x})}[-D^2]$ |
| 指数损失 | $\mathbb{E}_{p^*(\boldsymbol{x})}[(-1/D)^{1/2}] + \mathbb{E}_{q_\theta(\boldsymbol{x})}[(-1/(1-D))^{1/2}]$ |
| 错误分类 | $\mathbb{E}_{p^*(\boldsymbol{x})}[-I[D \le 0.5]] + \mathbb{E}_{q_\theta(\boldsymbol{x})}[-I[D > 0.5]]$ |
| 铰链损失 | $\mathbb{E}_{p^*(\boldsymbol{x})}[-\max(0, 1 - \log(D/(1-D)))] + \mathbb{E}_{q_\theta(\boldsymbol{x})}[-\max(0, 1 + \log(D/(1-D)))]$ |
| 球形 | $\mathbb{E}_{p^*(\boldsymbol{x})}[\alpha D] + \mathbb{E}_{q_\theta(\boldsymbol{x})}[\alpha(1 - D)] \; ; \alpha = (1 - 2D + 2D^2)^{-1/2}$ |

表 26.1：可在基于类概率的隐式生成模型学习中最大化的合适评分规则。基于 [ML16]。

同样的程序可以扩展到超出 Bernoulli 对数损失的其他用于二分类的合适评分规则，例如表 26.1 中所示的规则（改编自 [ML16]）。最优鉴别器 D 为 $p^*(x) / (p^*(x)+q_\theta(x))$，因为：

\[
\frac{p^*(x)}{q_\theta(x)} = \frac{D^*(x)}{1 - D^*(x)} \implies D^*(x) = \frac{p^*(x)}{p^*(x) + q_\theta(x)} \tag{26.11}
\]

通过将最优鉴别器代入评分规则 (26.10)，我们可以证明目标 V 也可以解释为 Jensen-Shannon 偏差的最小化。

\[
V^*(q_\theta, p^*) = \frac{1}{2} \mathbb{E}_{p^*(x)}[\log \frac{p^*(x)}{p^*(x) + q_\theta(x)}] + \frac{1}{2} \mathbb{E}_{q_\theta(x)}[\log(1 - \frac{p^*(x)}{p^*(x) + q_\theta(x)})] \tag{26.12}
\]

\[
= \frac{1}{2} \mathbb{E}_{p^*(x)}[\log \frac{p^*(x)}{p^*(x) + q_\theta(x)}] + \frac{1}{2} \mathbb{E}_{q_\theta(x)}[\log(\frac{q_\theta(x)}{p^*(x) + q_\theta(x)})] - \log 2 \tag{26.13}
\]

\[
= \frac{1}{2} D_{KL} \left( p^* \| \frac{p^* + q_\theta}{2} \right) + \frac{1}{2} D_{KL} \left( q_\theta \| \frac{p^* + q_\theta}{2} \right) - \log 2 \tag{26.14}
\]

\[
= \text{JSD}(p^*, q_\theta) - \log 2 \tag{26.15}
\]

其中 JSD 表示 Jensen-Shannon 偏差：

\[
\text{JSD}(p^*, q_\theta) = \frac{1}{2} D_{KL} \left( p^* \| \frac{p^* + q_\theta}{2} \right) + \frac{1}{2} D_{KL} \left( q_\theta \| \frac{p^* + q_\theta}{2} \right) \tag{26.16}
\]

这建立了最优二分类与分布偏差之间的联系。通过使用二分类，我们能够仅使用样本来计算分布偏差，这是学习隐式生成模型所需的重要属性；正如指导原则（第 26.2.1 节）所表达的那样，我们已经将一个难以处理的估计问题——如何估计 JSD 偏差——转化为一个优化问题——如何学习一个可用于近似该偏差的分类器。

我们希望训练生成模型的参数 $\theta$ 以最小化偏差：

\[
\min_{\theta} \text{JSD}(p^*, q_\theta) = \min_{\theta} V^*(q_\theta, p^*) + \log 2 \tag{26.17}
\]

\[
= \min_{\theta} \frac{1}{2} \mathbb{E}_{p^*(x)} \log D^*(x) + \frac{1}{2} \mathbb{E}_{q_\theta(x)} \log(1 - D^*(x)) + \log 2 \tag{26.18}
\]

