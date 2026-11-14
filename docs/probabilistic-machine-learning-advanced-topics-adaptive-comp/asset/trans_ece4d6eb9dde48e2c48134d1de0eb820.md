
对 \(k=0,1,\cdots,K-1\) 进行迭代，其中 \(\mathbf{z}^k \sim \mathcal{N}(\mathbf{0}, \mathbf{I})\)，且 \(\epsilon > 0\) 为步长。
假设我们仅为对比离散度运行一步朗之万MCMC。在此情况下，对数似然的梯度由以下公式给出：

```
\mathbb{E}_{p_{\mathcal{D}}(\mathbf{x})}[\nabla_\theta \log p_\theta(\mathbf{x})] = -\mathbb{E}_{p_{\mathcal{D}}(\mathbf{x})}[\nabla_\theta \mathcal{E}_\theta(\mathbf{x})] + \mathbb{E}_{\mathbf{x} \sim p_\theta(\mathbf{x})}[\nabla_\theta \mathcal{E}_\theta(\mathbf{x})]
\simeq -\mathbb{E}_{p_{\mathcal{D}}(\mathbf{x})}[\nabla_\theta \mathcal{E}_\theta(\mathbf{x})] + \mathbb{E}_{p_\theta(\mathbf{x}), \mathbf{z} \sim \mathcal{N}(\mathbf{0}, \mathbf{I})} \left[ \nabla_\theta \mathcal{E}_\theta \left( \mathbf{x} - \frac{\epsilon^2}{2} \nabla_\mathbf{x} E_{\theta^\prime}(\mathbf{x}) + \epsilon \mathbf{z} \right) \bigg|_{\theta^\prime=\theta} \right]. \quad (24.44)
```

对上述方程关于 \(\epsilon\) 进行泰勒级数展开并经过一些代数变形后，可以将其转换为如下形式 [Hyv07a]：

```
\frac{\epsilon^2}{2} \nabla_\theta D_F(p_{\mathcal{D}}(\mathbf{x}) \parallel p_\theta(\mathbf{x})) + o(\epsilon^2). \quad (24.45)
```

当 \(\epsilon\) 足够小时，它对应于分数匹配目标的重新缩放梯度。
一般来说，分数匹配最小化Fisher散度 \(D_F(p_{\mathcal{D}}(\mathbf{x}) \parallel p_\theta(\mathbf{x}))\)，而对比离散度最小化与KL散度 \(D_{KL}(p_{\mathcal{D}}(\mathbf{x}) \parallel p_\theta(\mathbf{x}))\) 相关的目标，如方程 (24.19) 所示。分数匹配与对比离散度之间的上述关联是这两个统计散度之间关联的自然结果，该关联由 *de Bruijn恒等式* [Cov99; Lyu12] 描述：

```
\frac{d}{dt} D_{KL}(q_t(\tilde{\mathbf{x}}) \parallel p_{\theta,t}(\tilde{\mathbf{x}})) = -\frac{1}{2} D_F(q_t(\tilde{\mathbf{x}}) \parallel p_{\theta,t}(\tilde{\mathbf{x}})).
```

这里 \(q_t(\tilde{\mathbf{x}})\) 和 \(p_{\theta,t}(\tilde{\mathbf{x}})\) 分别表示 \(p_{\mathcal{D}}(\mathbf{x})\) 和 \(p_\theta(\mathbf{x})\) 的平滑版本，通过向 \(\mathbf{x}\) 添加方差为 \(t\) 的高斯噪声得到；即，\(\tilde{\mathbf{x}} \sim \mathcal{N}(\mathbf{x}, t\mathbf{I})\)。

## 24.3.5 基于分数的生成模型

我们已经看到，通过学习标量能量函数 \(\mathcal{E}_\theta(\mathbf{x})\) 来使用分数匹配拟合EBM。或者，我们可以直接学习分数函数 \(\mathbf{s}_\theta(\mathbf{x}) = \nabla_\mathbf{x} \log p_\theta(\mathbf{x})\)；这被称为基于分数的生成模型，在第 25.3 节中讨论。这类无约束分数模型不保证输出保守向量场，这意味着它们不对应于任何函数的梯度。然而，两种方法似乎都能给出可比的结果 [SH21]。

## 24.4 噪声对比估计

学习EBM参数的另一个原则是 **噪声对比估计** (NCE)，由 [GH10] 引入。其思想是，我们可以通过将EBM与另一个具有已知密度的分布进行对比来学习EBM。

令 \(p_{\mathcal{D}}(\mathbf{x})\) 为我们的数据分布，令 \(p_{\text{n}}(\mathbf{x})\) 为具有已知密度的选定分布，称为噪声分布。该噪声分布通常很简单且具有易处理的pdf，例如 \(\mathcal{N}(\mathbf{0}, \mathbf{I})\)，这样我们可以高效地计算pdf并从中生成样本。存在学习噪声分布的策略，如下文所引用。此外，令 \(y\) 为服从伯努利分布的二进制变量，我们用它来定义噪声和数据的混合分布：\(p_{\text{n,data}}(\mathbf{x}) = p(y=0)p_n(\mathbf{x}) + p(y=1)p_D(\mathbf{x})\)。根据贝叶斯法则，给定来自此混合分布的样本 \(\mathbf{x}\)，\(y=0\) 的后验概率为

```
p_{n,data}(y=0 | \mathbf{x}) = \frac{p_{n,data}(\mathbf{x} | y=0)p(y=0)}{p_{n,data}(\mathbf{x})} = \frac{p_n(\mathbf{x})}{p_n(\mathbf{x}) + \nu p_D(\mathbf{x})}
```

其中 \(\nu = p(y=1)/p(y=0)\)。

令我们的EBM \(p_\theta(\mathbf{x})\) 定义为：

```
p_\theta(\mathbf{x}) = exp(-\mathcal{E}_\theta(\mathbf{x}))/Z_\theta
```

与大多数其他EBM不同，在NCE中 \(Z_\theta\) 被视为可学习的（标量）参数。鉴于该模型，类似于上述噪声与数据的混合，我们可以定义噪声与模型分布的混合：\(p_{n,\theta}(\mathbf{x}) = p(y=0)p_n(\mathbf{x}) + p(y=1)p_\theta(\mathbf{x})\)。给定此噪声/模型混合分布，\(y=0\) 的后验概率为：

```
p_{n,\theta}(y=0 | \mathbf{x}) = \frac{p_n(\mathbf{x})}{p_n(\mathbf{x}) + \nu p_\theta(\mathbf{x})}
```

在NCE中，我们通过标准条件最大似然目标，将 \(p_{n,\theta}(y|\mathbf{x})\) 拟合到 \(p_{n,data}(y|\mathbf{x})\)，从而间接地将 \(p_\theta(\mathbf{x})\) 拟合到 \(p_D(\mathbf{x})\)：

```
\theta^* = argmin_\theta \mathbb{E}_{p_{n,data}(\mathbf{x})}[D_{KL}(p_{n,data}(y | \mathbf{x}) || p_{n,\theta}(y | \mathbf{x}))]
```

```
= argmax_\theta \mathbb{E}_{p_{n,data}(\mathbf{x},y)}[\log p_{n,\theta}(y | \mathbf{x})],
```

这可以使用随机梯度上升来求解。就像任何其他深度分类器一样，当模型足够强大时，\(p_{n,\theta^*}(y|\mathbf{x})\) 将在最优时与 \(p_{n,data}(y|\mathbf{x})\) 匹配。在这种情况下：

```
p_{n,\theta^*}(y=0 | \mathbf{x}) \equiv p_{n,data}(y=0 | \mathbf{x})
\Longleftrightarrow \frac{p_n(\mathbf{x})}{p_n(\mathbf{x}) + \nu p_{\theta^*}(\mathbf{x})} \equiv \frac{p_n(\mathbf{x})}{p_n(\mathbf{x}) + \nu p_D(\mathbf{x})}
\Longleftrightarrow p_{\theta^*}(\mathbf{x}) \equiv p_D(\mathbf{x})
```

因此，\(E_{\theta^*}(\mathbf{x})\) 是一个与数据分布 \(p_D(\mathbf{x})\) 匹配的未归一化能量函数，\(Z_{\theta^*}\) 是相应的归一化常数。

作为对比离散度和分数匹配所不具备的一个独特特性，NCE在其训练过程中将能量模型的归一化常数作为副产品提供出来。当EBM非常具表达性时，例如具有许多参数的深度神经网络，我们可以假设它能够逼近归一化概率密度并将 \(Z_\theta\) 吸收进 \(\mathcal{E}_\theta(\mathbf{x})\) 的参数中 [MT12]，或者等价地，固定 \(Z_\theta = 1\)。用NCE训练得到的EBM将是自归一化的，即拥有接近1的归一化常数。

在实践中，选择合适的噪声分布 \(p_n(\mathbf{x})\) 对NCE的成功至关重要，特别是对于结构化和高维数据。正如 Gutmann 和 Hirayama [GH12] 所论证的，当噪声分布接近数据分布（但不完全相同时），NCE效果最好。已经提出许多方法来自动调谐噪声分布，例如对抗性对比估计 [BLC18]、条件NCE [CG18] 和流式对比估计 [Gao+20]。NCE还可以使用Bregman散度进一步推广（第 5.1.10 节），此处引入的公式将归结为一种特例。

### 24.4.1 与分数匹配的关联

噪声对比估计提供了一组针对不同 \(p_n(\mathbf{x})\) 和 \(\nu\) 而变化的目标。这种灵活性可能允许通过手动调整 \(p_n(\mathbf{x})\) 和 \(\nu\) 来适应任务的特殊属性，也可能为不同方法提供统一视角。特别是，当使用合适的 \(p_n(\mathbf{x})\) 和 \(p_{n,\boldsymbol{\theta}}(y \mid \mathbf{x})\) 的略有不同的参数化时，我们可以从NCE中恢复分数匹配 [GH12]。

具体来说，我们将噪声分布 \(p_n(\mathbf{x})\) 选择为扰动后的数据分布：给定一个小的（确定性）向量 \(\mathbf{v}\)，令 \(p_n(\mathbf{x}) = p_D(\mathbf{x} - \mathbf{v})\)。从这个 \(p_n(\mathbf{x})\) 中采样很高效，因为我们可以先抽取任意数据点 \(\mathbf{x}' \sim p_D(\mathbf{x}')\)，然后计算 \(\mathbf{x} = \mathbf{x}' + \mathbf{v}\)。然而，由于 \(p_D(\mathbf{x})\) 未知，难以评估 \(p_n(\mathbf{x})\) 的密度。由于NCE中 \(p_{n,\boldsymbol{\theta}}(y \mid \mathbf{x})\) 的原始参数化（方程 (24.48)）依赖于 \(p_n(\mathbf{x})\) 的pdf，我们无法直接应用标准NCE目标。相反，我们用 \(p_{\boldsymbol{\theta}}(\mathbf{x} - \mathbf{v})\) 替换 \(p_n(\mathbf{x})\)，并用以下形式参数化 \(p_{n,\boldsymbol{\theta}}(y = 0 \mid \mathbf{x})\)。

\(p_{n,\boldsymbol{\theta}}(y = 0 \mid \mathbf{x}) := \frac{p_{\boldsymbol{\theta}}(\mathbf{x} - \mathbf{v})}{p_{\boldsymbol{\theta}}(\mathbf{x}) + p_{\boldsymbol{\theta}}(\mathbf{x} - \mathbf{v})}\)

在这种情况下，NCE目标（方程 (24.50)）归约为：

\(\boldsymbol{\theta}^* = \text{argmin}_{\boldsymbol{\theta}} \mathbb{E}_{p_D(\mathbf{x})} [\log(1 + \exp(\mathcal{E}_\boldsymbol{\theta}(\mathbf{x}) - \mathcal{E}_\boldsymbol{\theta}(\mathbf{x} - \mathbf{v}))) + \log(1 + \exp(\mathcal{E}_\boldsymbol{\theta}(\mathbf{x}) - \mathcal{E}_\boldsymbol{\theta}(\mathbf{x} + \mathbf{v})))]

在 \(\boldsymbol{\theta}^*\) 处，我们有一个满足以下条件的解：

\(p_{n,\boldsymbol{\theta}^*}(y = 0 \mid \mathbf{x}) \equiv p_{n,\text{data}}(y = 0 \mid \mathbf{x})\)

\(\Longrightarrow \frac{p_{\boldsymbol{\theta}^*}(\mathbf{x} - \mathbf{v})}{p_{\boldsymbol{\theta}^*}(\mathbf{x}) + p_{\boldsymbol{\theta}^*}(\mathbf{x} - \mathbf{v})} \equiv \frac{p_D(\mathbf{x} - \mathbf{v})}{p_D(\mathbf{x}) + p_D(\mathbf{x} - \mathbf{v})}\)

这意味着 \(p_{\boldsymbol{\theta}^*}(\mathbf{x}) \equiv p_D(\mathbf{x})\)，即我们的模型与数据分布匹配。

正如 Gutmann 和 Hirayama [GH12] 以及 Song 等人 [Son+19] 所指出的，当 \(\|\mathbf{v}\|_2 \approx 0\) 时，通过泰勒展开，NCE目标方程 (24.50) 具有以下等价形式

\(\text{argmin}_{\boldsymbol{\theta}} \frac{1}{4} \mathbb{E}_{p_D(\mathbf{x})} \left[ \frac{1}{2} \sum_{i=1}^d \left( \frac{\partial \mathcal{E}_\boldsymbol{\theta}(\mathbf{x})}{\partial x_i} v_i \right)^2 + \sum_{i=1}^d \sum_{j=1}^d \frac{\partial^2 \mathcal{E}_\boldsymbol{\theta}(\mathbf{x})}{\partial x_i \partial x_j} v_i v_j \right] + 2 \log 2 + o(\|\mathbf{v}\|_2^2).\)

与方程 (24.38) 比较，我们立即看到，上述目标等于SSM的目标，如果我们忽略隐藏在 \(o(\|\mathbf{v}\|_2^2)\) 中的小额外项，并对 \(\mathbf{v}\) 关于用户指定分布 \(p(\mathbf{v})\) 取期望。

## 24.5 其他方法

除了基于MCMC的训练、分数匹配和噪声对比估计之外，还有其他用于学习EBM的方法。下面我们简要介绍其中一些示例。感兴趣的读者可以从其中的参考文献了解更多细节。
