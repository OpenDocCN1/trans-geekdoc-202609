
## 3.5.3 不变先验

如果我们以不变量的形式拥有关于某个问题的“客观”先验知识，我们可能能够将其编码为先验，如下所示。

### 3.5.3.1 平移不变先验

位置-尺度族是一类由位置参数 $\mu$ 和尺度参数 $\sigma$ 参数化的概率分布族。如果 $x$ 是该族中的随机变量，则 $y = a + bx$ 也是同一族中的随机变量。

在推断位置参数 $\mu$ 时，直觉上合理的做是使用平移不变先验，该先验满足以下性质：赋予任何区间 $[A, B]$ 的概率质量与赋予任何其他等宽平移区间（例如 $[A-c, B-c]$）的概率质量相同。即，

```
\int_{A-c}^{B-c} p(\mu) d\mu = \int_A^B p(\mu) d\mu (3.237)
```

这可以通过使用实现

```
p(\mu) \propto 1 (3.238)
```

因为

```
\int_{A-c}^{B-c} 1 d\mu = (B-c) - (A-c) = (B-A) = \int_A^B 1 d\mu (3.239)
```

这与高斯分布（未知均值 $\mu$ 且固定方差）的 Jeffreys 先验相同。这是因为根据公式 (3.62)，$F(\mu) = 1/\sigma^2 \propto 1$，因此 $p(\mu) \propto 1$。

### 3.5.3.2 尺度不变先验

在推断尺度参数 $\sigma$ 时，我们可能希望使用尺度不变先验，该先验满足以下性质：赋予任何区间 $[A, B]$ 的概率质量与赋予任何其他区间 $[A/c, B/c]$（其中 $c > 0$）的概率质量相同。即，

```
\int_{A/c}^{B/c} p(\sigma) d\sigma = \int_A^B p(\sigma) d\sigma (3.240)
```

这可以通过使用实现

```
p(\sigma) \propto 1/\sigma (3.241)
```

因为此时

```
\int_{A/c}^{B/c} \frac{1}{\sigma} d\sigma = [\log \sigma]_{A/c}^{B/c} = \log(B/c) - \log(A/c) = \log(B) - \log(A) = \int_A^B \frac{1}{\sigma} d\sigma (3.242)
```

这与高斯分布（固定均值 $\mu$ 且未知尺度 $\sigma$）的 Jeffreys 先验相同。这是因为根据公式 (3.62)，$F(\sigma) = 2/\sigma^2$，因此 $p(\sigma) \propto 1/\sigma$。

### 3.5.3.3 学习不变先验

每当我们拥有希望模型满足的某种不变性知识时，我们可以利用它来编码相应的先验。有时这可以通过解析方法完成（参见例如 [Rob07, 第 9 章]）。当这不可行时，可能可以通过求解变分优化问题来学习不变先验（参见例如 [NS18]）。

## 3.5.4 参考先验

定义非信息性先验的一种方法是将其视为在数据集上平均后与所有可能后验分布距离最远的分布。这是 **参考先验** [Ber05; BBS09] 的基本思想。更准确地说，如果 \( p(\theta) \) 最大化了后验与先验之间的预期 KL 散度，则称其为参考先验：

```
$$ p^*(\theta) = \underset{p(\theta)}{\text{argmax}} \int_{\mathcal{D}} p(\mathcal{D}) D_{\text{KL}} (p(\theta|\mathcal{D}) \| p(\theta)) d\mathcal{D} \quad (3.243) $$
```

其中 \( p(\mathcal{D}) = \int p(\mathcal{D}|\theta)p(\theta)d\theta \)。这等同于最大化互信息 \( \mathbb{I}(\theta, \mathcal{D}) \)。我们可以通过注意到以下事实来消除对数据集的积分：

```
$$ \int p(\mathcal{D}) \int p(\theta|\mathcal{D}) \log \frac{p(\theta|\mathcal{D})}{p(\theta)} = \int p(\theta) \int p(\mathcal{D}|\theta) \log \frac{p(\mathcal{D}|\theta)}{p(\mathcal{D})} = \mathbb{E}_{\theta} [D_{\text{KL}} (p(\mathcal{D}|\theta) \| p(\mathcal{D}))] \quad (3.244) $$
```

这里我们利用了 \( \frac{p(\theta|\mathcal{D})}{p(\theta)} = \frac{p(\mathcal{D}|\theta)}{p(\mathcal{D})} \) 这一事实。

可以证明，在一维情况下，相应的先验等价于 Jeffreys 先验。在高维情况下，我们可以利用链式法则一次计算一个参数的参考先验。然而，这在计算上可能变得不可行。关于基于变分推理（第 10.1 节）的可处理近似，请参见 [NS17]。

## 3.6 分层先验

贝叶斯模型需要为参数指定先验 \( p(\theta) \)。先验的参数称为 **超参数**，并将用 \( \xi \) 表示。如果这些参数未知，我们可以在其上设置先验；这定义了一个 **分层贝叶斯模型**，或 **多层模型**，可可视化如下：\( \xi \to \theta \to \mathcal{D} \)。我们假设超参数的先验是固定的（例如，我们可能使用某种最小信息性先验），因此联合分布的形式为

```
$$ p(\xi, \theta, \mathcal{D}) = p(\xi)p(\theta|\xi)p(\mathcal{D}|\theta) \quad (3.245) $$
```

希望是，我们可以通过将参数本身视为数据点来学习超参数。

这种方法适用的常见场景是，当我们有 \( J > 1 \) 个相关数据集 \( \mathcal{D}_j \)，每个数据集都有其自身参数 \( \theta_j \) 时。如果 \( \mathcal{D}_j \) 是小数据集（例如，条件 \( j \) 对应于罕见的特征组合或人口稀少区域），则独立推断每个组 \( j \) 的 \( p(\theta_j|\mathcal{D}_j) \) 可能会产生较差的结果。我们当然可以汇合所有数据来计算单一模型 \( p(\theta|\mathcal{D}) \)，但这将无法让我们建模子总体。分层贝叶斯模型让我们可以从数据量大的组（因此后验 \(p(\theta_j|\mathcal{D})\) 较充分）借用统计强度，以帮助数据量少的组（因此后验 \(p(\theta_j|\mathcal{D})\) 高度不确定）。其思想是，充分信息的组 \(j\) 将对 \(\theta_j\) 有很好的估计，从中我们可以推断 \(\xi\)，并可用于帮助估计数据较少的组 \(k\) 的 \(\theta_k\)。（信息通过图形模型中的隐藏共享父节点 \(\xi\) 共享，如图 3.14 所示。）我们将在下面给出一些示例。

拟合此类模型后，我们可以计算两种后验预测分布。如果我们想要预测现有组 \(j\) 的观测值，则需要使用

\(p(y_j|\mathcal{D}) = \int p(y_j|\theta_j)p(\theta_j|\mathcal{D})d\theta_j\) (3.246)

但是，如果我们想要预测尚未测量的新组的观测值，但该新组与现有组 \(1:J\) 可比（或 **可互换与**），则需要使用

\(p(y_*|\mathcal{D}) = \int p(y_*|\theta_*)p(\theta_*|\xi)p(\xi|\mathcal{D})d\theta_*d\xi\) (3.247)

我们将在下面给出一些示例。（更多信息可以参见例如 [GH07; Gel+14a]。）

### 3.6.1 分层二项模型

假设我们想要估计不同人群（无论是人还是动物）中某种疾病的患病率。设 \(N_j\) 为第 \(j\) 组的大小，\(y_j\) 为第 \(j = 1:J\) 组的阳性病例数。我们假设 \(y_j \sim \text{Bin}(N_j, \theta_j)\)，并希望估计比率 \(\theta_j\)。由于某些组的人口规模可能较小，如果分别估计每个 \(\theta_j\)，我们可能会得到不可靠的结果；例如，我们可能观察到 \(y_j = 0\) 从而得到 \(\hat{\theta}_j = 0\)，即使真实感染率更高。

一种解决方案是假设所有 \(\theta_j\) 都相同；这被称为 **参数绑定**。得到的汇合 MLE 为 \(\hat{\theta}_{\text{pooled}} = \frac{\sum_j y_j}{\sum_j N_j}\)。但是，所有组具有相同比率的假设相当强。一种折中方法是假设 \(\theta_j\) 相似，但可能存在组特异性变异。这可以通过假设 \(\theta_j\) 来自某个共同分布（例如 \(\theta_j \sim \text{Beta}(a, b)\)）来建模。完整的联合分布可以写成

\(p(\mathcal{D}, \theta, \xi) = p(\xi)p(\theta|\xi)p(\mathcal{D}|\theta) = p(\xi) \left[ \prod_{j=1}^J \text{Beta}(\theta_j|\xi) \right] \left[ \prod_{j=1}^J \text{Bin}(y_j|N_j, \theta_j) \right]\) (3.248)

其中 \(\xi = (a, b)\)。在图 3.14 中，我们使用有向图形模型来表示这些假设（关于此类图表的解释见第 4.2.8 节）。

还需要指定先验 \(p(\xi)\)。遵循 [Gel+14a, 第 110 页]，我们使用

\(p(a, b) \propto (a + b)^{-5/2}\) (3.249)
