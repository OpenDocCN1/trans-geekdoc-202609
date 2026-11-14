

对于均值，我们有（使用第 3.4.4.1 节的结果）

$p(\mu_k|\mathbf{S}_k, \mathbf{z}, \mathbf{x}) = \mathcal{N}(\mu_k|\mathbf{m}_k, \mathbf{V}_k)$ (12.41)

\(\mathbf{V}_k^{-1} = \mathbf{V}_0^{-1} + N_k\mathbf{\Sigma}_k^{-1}\) (12.42)

\(\mathbf{m}_k = \mathbf{V}_k(\mathbf{\Sigma}_k^{-1}N_k\overline{\mathbf{x}}_k + \mathbf{V}_0^{-1}\mathbf{m}_0)\) (12.43)

\(N_k \stackrel{\Delta}{=} \sum_{i=1}^N \mathbb{I}(z_i = k)\) (12.44)

\(\overline{\mathbf{x}}_k \stackrel{\Delta}{=} \frac{\sum_{i=1}^N \mathbb{I}(z_i = k) \mathbf{x}_i}{N_k}\) (12.45)

对于协方差，我们有（使用第 3.4.4.2 节的结果）

$p(\mathbf{\Sigma}_k|\mu_k, \mathbf{z}, \mathbf{x}) = \text{IW}(\mathbf{\Sigma}_k|\mathbf{S}_k, \nu_k)$ (12.46)

\(\mathbf{S}_k = \mathbf{S}_0 + \sum_{i=1}^N \mathbb{I}(z_i = k) (\mathbf{x}_i - \mu_k)(\mathbf{x}_i - \mu_k)^\top\) (12.47)

\(\nu_k = \nu_0 + N_k\) (12.48)

## 12.3.6 吉布斯采样中的 Metropolis

实施吉布斯采样时，我们需要从全条件分布中采样。如果分布是共轭的，我们可以以封闭形式计算全条件分布，但在一般情况下，我们需要设计特殊算法来从全条件分布中采样。

一种方法是使用 MH 算法；这称为 Metropolis within Gibbs。特别是，要从 $x_i^{s+1} \sim p(x_i|x_{1:i-1}^{s+1}, x_{i+1:D}^s)$ 采样，我们分 3 步进行：

- 1. 提出 $x_i' \sim q(x_i'|x_i^s)$
- 2. 计算接受概率 \(A_i = \min(1, \alpha_i)\)，其中
  \(\alpha_i = \frac{p(x_{1:i-1}^{s+1}, x_i', x_{i+1:D}^s)/q(x_i'|x_i^s)}{p(x_{1:i-1}^{s+1}, x_i^s, x_{i+1:D}^s)/q(x_i^s|x_i')}\) (12.49)
- 3. 采样 \(u \sim U(0, 1)\)，若 \(u < A_i\) 则令 \(x_i^{s+1} = x_i'\)，否则令 \(x_i^{s+1} = x_i^s\)。

## 12.3.7 阻塞吉布斯采样

吉布斯采样可能相当缓慢，因为它一次只更新一个变量（即所谓的单站点更新）。如果变量高度相关，马尔可夫链在状态空间中移动会很慢。图 12.5 说明了这一点，其中我们展示了从二维高斯分布中采样的情形。椭圆代表协方差矩阵。吉布斯采样移动的步长由条件分布的方差控制。如果在某个坐标方向上方差为 \(\ell\)，但分布在该维度上的支撑为 \(L\)，那么我们需要 \(O((L/\ell)^2)\) 步骤才能获得一个独立样本。

![](img/ca72c1626f4850f058a9edc138c1ac73_536_0.png)

图 12.5: 使用吉布斯采样对偏态二维高斯分布进行采样时可能速度较慢的示例。改编自 [Bis06] 中的图 11.11。由 gibbs_gauss_demo.ipynb 生成。

在某些情况下，我们可以高效地一次采样一组变量。这称为 **阻塞吉布斯采样** [JKK95; WY02]，可以在状态空间中进行更大的移动。

例如，假设我们想对状态空间模型（如 HMM）进行贝叶斯推断，即我们想从
\( p(\theta, z|x) \propto p(\theta) \prod_{t=1}^T p(x_t|z_t, \theta) p(z_t|z_{t-1}, \theta) \)
采样。我们可以使用阻塞吉布斯采样，在 \( p(\theta|z, x) \) 和 \( p(z|x, \theta) \) 之间交替采样。前者易于实现（假设使用共轭先验），因为模型中的所有变量都是观测到的（参见第 29.8.4.1 节）。后者可以使用前向滤波后向采样（第 9.2.7 节）来完成。

## 12.3.8 坍缩吉布斯采样

有时通过解析地积分掉一些未知量，可以获得更大的加速。这称为 **坍缩吉布斯采样器**，它通常更高效，因为它在较低维空间中进行采样。这可能导致较低的方差，如第 11.6.2 节所讨论。

例如，考虑一个带有完全共轭先验的 GMM。它可以表示为图 12.6a 所示的 DPGM。由于先验是共轭的，我们可以解析地积分掉模型参数 \( \mu_k, \Sigma_k \) 和 \( \pi \)，因此唯一剩余的隐藏变量是离散指示变量 \( z \)。但是，一旦我们积分掉 \( \pi \)，所有的 \( z_i \) 节点就会相互依赖。同样，一旦我们积分掉 \( \theta_k = (\mu_k, \Sigma_k) \)，所有的 \( x_i \) 节点就会相互依赖，如图 12.6b 所示。尽管如此，我们仍然可以轻松计算全条件分布，从而实现吉布斯采样器，如下面所述。特别是，潜在指示变量的全条件分布由以下给出

\( p(z_i = k | z_{-i}, x, \alpha, \beta) \propto p(z_i = k | z_{-i}, \alpha, \beta) p(x | z_i = k, z_{-i}, \alpha', \beta) \) (12.51)
\( \propto p(z_i = k | z_{-i}, \alpha) p(x_i | x_{-i}, z_i = k, z_{-i}, \beta) \)
\( p(x_{-i} | z_{-i} = \bar{k}, z_{-i}, \beta) \) (12.52)
\( \propto p(z_i = k | z_{-i}, \alpha) p(x_i | x_{-i}, z_i = k, z_{-i}, \beta) \) (12.53)

![](img/ca72c1626f4850f058a9edc138c1ac73_537_0.png)

![](img/ca72c1626f4850f058a9edc138c1ac73_537_1.png)

图 12.6: (a) 表示为“展开” DPGM 的混合模型。(b) 积分掉连续潜在参数之后。

其中 \(\boldsymbol{\beta} = (\mathbf{m}_0, \mathbf{V}_0, \mathbf{S}_0, \nu_0)\) 是类条件密度的超参数。我们现在讨论如何计算这些项。

假设我们对混合权重使用形式为 \(\boldsymbol{\pi} \sim \text{Dir}(\boldsymbol{\alpha})\) 的对称先验，其中 \(\alpha_k = \alpha/K\)。那么我们可以从公式 (3.96) 获得公式 (12.53) 中的第一项，其中

\(p(z_1, \dots, z_N | \alpha) = \frac{\Gamma(\alpha)}{\Gamma(N + \alpha)} \prod_{k=1}^K \frac{\Gamma(N_k + \alpha/K)}{\Gamma(\alpha/K)}\) (12.54)

因此

\(p(z_i = k | \mathbf{z}_{-i}, \alpha) = \frac{p(\mathbf{z}_{1:N} | \alpha)}{p(\mathbf{z}_{-i} | \alpha)} = \frac{1}{\frac{\Gamma(N+1+\alpha)}{\Gamma(N+\alpha-1)}} \times \frac{\Gamma(N_k + \alpha/K)}{\Gamma(N_{k,-i} + \alpha/K)}\) (12.55)

\(= \frac{\Gamma(N + \alpha - 1)}{\Gamma(N + \alpha)} \frac{\Gamma(N_{k,-i} + 1 + \alpha/K)}{\Gamma(N_{k,-i} + \alpha/K)} = \frac{N_{k,-i} + \alpha}{N + \alpha - 1}\) (12.56)

其中 \(N_{k, -i} \triangleq \sum_{n \neq i} \mathbb{I}(z_n = k) = N_k - 1\)，并且我们利用了 \(\Gamma(x+1) = x\Gamma(x)\) 这一事实。

要获得公式 (12.53) 中的第二项，即在给定所有其他数据和所有分配的情况下对 \(\mathbf{x}_i\) 的后验预测分布，我们使用以下事实

\(p(\mathbf{x}_i | \mathbf{x}_{-i}, \mathbf{z}_{-i}, z_i = k, \boldsymbol{\beta}) = p(\mathbf{x}_i | \mathcal{D}_{-i,k}, \boldsymbol{\beta})\) (12.57)

其中 \(\mathcal{D}_{-i,k} = \{\mathbf{x}_j : z_j = k, j \neq i\}\) 是分配给簇 \(k\) 的所有数据，\(\mathbf{x}_i\) 除外。如果我们为 \(\boldsymbol{\theta}_k\) 使用共轭先验，我们可以以封闭形式计算 \(p(\mathbf{x}_i | \mathcal{D}_{-i,k}, \boldsymbol{\beta})\)。此外，我们可以通过缓存每个簇的充分统计量来高效更新这些预测似然。要计算上述表达式，我们将 \(\mathbf{x}_i\) 的统计量从其当前簇（即 \(z_i\)）中移除，然后在每个簇的后验预测分布下评估 \(\mathbf{x}_i\)。一旦我们选择了一个新簇，就将 \(\mathbf{x}_i\) 的统计量添加到这个新簇中。

算法 12.2 显示了该算法一步的伪代码，基于 [Sud06, p94]。（我们按随机顺序更新节点以提高混合时间，如 [RS97b] 所建议。）我们可以通过按顺序从 \(p(z_i|\mathbf{z}_{1:i-1}, \mathbf{x}_{1:i})\) 采样来初始化样本。在 GMM 的情况下，朴素采样器和坍缩采样器每步都需要 \(O(NKD)\) 时间。

```
Algorithm 12.2: Collapsed Gibbs sampler for a mixture model
for each i = 1 : N in random order do
   Remove \mathbf{x}_i's sufficient statistics from old cluster z_i
   for each k = 1 : K do
       Compute p_k(\mathbf{x}_i|\beta) = p(\mathbf{x}_i|\{\mathbf{x}_j : z_j = k, j \neq i\}, \beta)
   Compute p(z_i = k|\mathbf{z}_{-i}, \alpha) \propto (N_{k,-i} + \alpha/K)p_k(\mathbf{x}_i)
   Sample z_i ~ p(z_i|.)
   Add \mathbf{x}_i's sufficient statistics to new cluster z_i
```

使用坍缩采样器的主要优势是，它扩展到了具有“无限”数量混合成分的情况，如补充部分 31.2.2 中的狄利克雷过程混合模型。

## 12.4 辅助变量 MCMC

有时我们可以通过引入辅助变量来显著提高采样效率，以减少原始变量之间的相关性。如果原始变量用 \(\mathbf{x}\) 表示，辅助变量用 \(\mathbf{v}\) 表示，那么增强分布变为 \(p(\mathbf{x}, \mathbf{v})\)。我们假设从中采样比从边缘分布 \(p(\mathbf{x})\) 采样更容易。如果是这样，我们可以绘制联合样本 \((\mathbf{x}^s, \mathbf{v}^s) \sim p(\mathbf{x}, \mathbf{v})\)，然后只是“丢弃” \(\mathbf{v}^s\)，结果将是所需边缘分布的样本，\(\mathbf{x}^s \sim \sum_v p(\mathbf{x}, \mathbf{v})\)。我们将在下面给出一些示例。

### 12.4.1 切片采样

考虑从一维但多模态的分布 \(p(x) = \tilde{p}(x)/Z_p\) 中采样，其中 \(\tilde{p}(x)\) 是未归一化的，\(Z_p = \int \tilde{p}(x)dx\)。我们有时可以通过添加均匀辅助变量 \(v\) 来提高进行大移动的能力。我们定义联合分布如下：

\(\hat{p}(x, v) = \left\{ \begin{array}{ll} 1/Z_p & \text{if } 0 \le v \le \tilde{p}(x) \\ 0 & \text{otherwise} \end{array} \right.\)

\(x\) 上的边缘分布由以下给出

\(\int \hat{p}(x, v) dv = \int_0^{\tilde{p}(x)} \frac{1}{Z_p} dv = \frac{\tilde{p}(x)}{Z_p} = p(x)\)

因此，我们可以通过从 \(\hat{p}(x, v)\) 采样然后忽略 \(v\) 来从 \(p(x)\) 采样。为此，我们将使用一种称为切片采样 [Nea03] 的技术。

