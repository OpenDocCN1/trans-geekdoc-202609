

![](img/ca72c1626f4850f058a9edc138c1ac73_144_0.png)

图 3.18：八校模型的后验 p(θ₀, log(τ)|D)，使用 (a) 集中参数化和 (b) 非集中参数化。由 schools8.ipynb 生成。

![](img/ca72c1626f4850f058a9edc138c1ac73_144_1.png)

图 3.19：分层高斯贝叶斯模型。(a) 集中参数化。(b) 非集中参数化。

请参见图 3.19b 以获取相应的图形模型。通过将 θⱼ 写成其父节点的确定性函数加上一个局部噪声项，我们减少了 θⱼ 与 τ 以及其他 θₖ 变量之间的依赖性，这可以提高推理算法的计算效率，如我们在第 12.6.5 节中讨论的那样。这种重参数化在分层贝叶斯模型中广泛使用。

### 3.6.3 分层条件模型

在第 15.5 节中，我们讨论分层贝叶斯广义线性模型，它们为每个组 j 学习条件分布 p(y|x, θⱼ)，使用形式为 p(θⱼ|ξ) 的先验。在第 17.6 节中，我们讨论分层贝叶斯神经网络，将这一想法推广到非线性预测器。

## 3.7 经验贝叶斯

在第 3.6 节中，我们讨论了分层贝叶斯作为从数据推断参数的一种方法。不幸的是，此类模型中的后验推断在计算上可能具有挑战性。在本节中，我们讨论了一种计算方便的近似方法，即先计算超参数的点估计 \(\hat{\xi}\)，然后计算条件后验 \(p(\theta|\hat{\xi}, \mathcal{D})\)，而不是联合后验 \(p(\theta, \xi|\mathcal{D})\)。

要估计超参数，我们可以最大化边缘似然：

```
\(\hat{\xi}_{mml}(\mathcal{D}) = \operatorname{argmax}_{\xi} p(\mathcal{D}|\xi) = \operatorname{argmax}_{\xi} \int p(\mathcal{D}|\theta)p(\theta|\xi)d\theta\) \tag{3.260}
```

这种技术称为 **二类最大似然**，因为我们优化的是超参数，而不是参数。(在神经网络的上下文中，这有时被称为 **证据程序** [Mac92a; WS93; Mac99]。) 一旦我们估计了 \(\hat{\xi}\)，我们就用常用的方法计算后验 \(p(\theta|\hat{\xi}; \mathcal{D})\)。

由于我们从数据估计先验参数，这种方法称为 **经验贝叶斯 (EB)** [CL96]。这违反了先验应独立于数据选择的原则。然而，我们可以将其视为对完整分层贝叶斯模型推理的一种计算廉价的近似，就像我们将 MAP 估计视为一级模型 \(\theta \to \mathcal{D}\) 推理的近似一样。事实上，我们可以构建一个层次结构，其中执行的积分越多，就变得“越贝叶斯”，如下所示。

| 方法 | 定义 |
| :--- | :--- |
| 最大似然估计 | \(\hat{\theta} = \operatorname{argmax}_{\theta} p(\mathcal{D}|\theta)\) |
| MAP 估计 | \(\hat{\theta} = \operatorname{argmax}_{\theta} p(\mathcal{D}|\theta)p(\theta|\xi)\) |
| ML-II（经验贝叶斯） | \(\hat{\xi} = \operatorname{argmax}_{\xi} \int p(\mathcal{D}|\theta)p(\theta|\xi)d\theta\) |
| MAP-II | \(\hat{\xi} = \operatorname{argmax}_{\xi} \int p(\mathcal{D}|\theta)p(\theta|\xi)p(\xi)d\theta\) |
| 全贝叶斯 | \(p(\theta|\xi, \mathcal{D}) \propto p(\mathcal{D}|\theta)p(\theta|\xi)p(\xi)\) |

请注意，ML-II 比“常规”最大似然更不容易过拟合，因为通常超参数 \(\xi\) 的数量少于参数 \(\theta\) 的数量。我们将在下面给出一些简单示例，并在本书后面部分介绍更多应用。

### 3.7.1 分层二项模型的经验贝叶斯

在本节中，我们重新审视第 3.6.1 节的分层二项模型，但使用经验贝叶斯代替全贝叶斯推理。我们可以解析地积分掉 \(\theta_j\)，并写下

![](img/ca72c1626f4850f058a9edc138c1ac73_146_0.png)

图 3.20：使用经验贝叶斯拟合的分层二项模型的数据和推断。由 eb_binomial.py 生成。

直接给出边缘似然：结果表达式为

```
p(\mathcal{D}|\boldsymbol{\xi}) = \prod_j \int \text{Bin}(y_j|N_j, \theta_j)\text{Beta}(\theta_j|a, b)d\theta_j \tag{3.261}
\propto \prod_j \frac{B(a+y_j, b+N_j-y_j)}{B(a, b)} \tag{3.262}
= \prod_j \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} \frac{\Gamma(a+y_j)\Gamma(b+N_j-y_j)}{\Gamma(a+b+N_j)} \tag{3.263}
```

[Min00c] 中讨论了关于 a 和 b 最大化此边缘似然的各种方法。

在估计超参数 a 和 b 后，我们可以将它们代入，以常规方式使用共轭分析计算每个组的后验 p(\theta_j|\hat{a}, \hat{b}, \mathcal{D})。我们在图 3.20 中展示了结果；它们与图 3.15 所示的全贝叶斯分析非常相似，但 EB 方法要快得多。

### 3.7.2 分层高斯模型的经验贝叶斯

在本节中，我们重新审视第 3.6.2.1 节的分层高斯模型。然而，我们使用经验贝叶斯拟合该模型。

为简单起见，我们假设所有组的 \(\sigma_j^2 = \sigma^2\) 相同。当方差相等时，我们可以像下面所示推导出闭式 EB 估计。我们有
\(p(y_j|\mu, \tau^2, \sigma^2) = \int \mathcal{N}(y_j|\theta_j, \sigma^2)\mathcal{N}(\theta_j|\mu, \tau^2)d\theta_j = \mathcal{N}(y_j|\mu, \tau^2 + \sigma^2)\)

因此边缘似然为
\(p(\mathcal{D}|\mu, \tau^2, \sigma^2) = \prod_{j=1}^J \mathcal{N}(y_j|\mu, \tau^2 + \sigma^2)\)

因此，我们可以使用高斯分布的常规 MLE 估计超参数。对于 \(\mu\)，我们有
\(\hat{\mu} = \frac{1}{J} \sum_{j=1}^J y_j = \bar{y}\)

这是总体均值。对于 \(\tau^2\)，我们可以使用矩匹配，这等价于高斯分布的 MLE。这意味着我们将模型方差等于经验方差：
\(\hat{\tau}^2 + \sigma^2 = \frac{1}{J} \sum_{j=1}^J (y_j - \bar{y})^2 \triangleq v\)

因此 \(\hat{\tau}^2 = v - \sigma^2\)。由于我们知道 \(\tau^2\) 必须为正，通常使用以下修正估计：
\(\hat{\tau}^2 = \max\{0, v - \sigma^2\} = (v - \sigma^2)_+\)

鉴于此，后验均值变为
\(\hat{\theta}_j = \lambda \mu + (1 - \lambda)y_j = \mu + (1 - \lambda)(y_j - \mu)\)

其中 \(\lambda_j = \lambda = \sigma^2/(\sigma^2 + \tau^2)\)。不幸的是，我们无法在 3.6.2.1 节的八校数据集上使用上述方法，因为它使用不等的 \(\sigma_j\)。然而，我们仍然可以使用 EM 算法或其他基于优化的方法。

### 3.7.3 马尔可夫模型的经验贝叶斯（n-gram 平滑）

第 2.6.3.3 节讨论的加一平滑的主要问题是，它假设所有 n-gram 等可能，这不太现实。一种更复杂的方法，称为删除插值 [CG96]，将转移矩阵定义为双gram 频率 \(f_{jk} = N_{jk}/N_j\) 和单gram 频率 \(f_k = N_k/N\) 的凸组合：
\(A_{jk} = (1 - \lambda)f_{jk} + \lambda f_k = (1 - \lambda)\frac{N_{jk}}{N_j} + \lambda \frac{N_k}{N}\)

术语 \(\lambda\) 通常通过交叉验证设置。还有一种密切相关的技术，称为回退平滑；其思想是，如果 \(f_{jk}\) 太小，我们就“回退”到更可靠的估计，即 \(f_k\)。

![](img/ca72c1626f4850f058a9edc138c1ac73_148_0.png)

图 3.21：一个马尔可夫链，我们在转移矩阵 A 的每一行上放置不同的狄利克雷先验，但狄利克雷的超参数是共享的。

我们现在表明，这种启发式方法可以解释为转移矩阵 A 每一行对应的参数向量的分层贝叶斯模型的经验贝叶斯近似。我们的介绍遵循 [MP95]。

首先，让我们在转移矩阵的每一行上使用独立的狄利克雷先验：

```
A_j ~ Dir(alpha_0 m_1, ..., alpha_0 m_K) = Dir(alpha_0 m) = Dir(alpha)
```

其中 A_j 是转移矩阵的第 j 行，m 是先验均值（满足 sum_k m_k = 1），alpha_0 是先验强度（参见图 3.21）。就之前的记号而言，我们有 theta_j = A_j 和 xi = (alpha, m)。

后验由 A_j ~ Dir(alpha + N_j) 给出，其中 N_j = (N_j1, ..., N_jK) 是记录从状态 j 转移到每个其他状态次数的向量。后验预测密度为

```
p(X_{t+1} = k | X_t = j, D) = (N_jk + alpha_0 m_k) / (N_j + alpha_0) = (f_jk N_j + alpha_0 m_k) / (N_j + alpha_0)
```

```
= (1 - lambda_j) f_jk + lambda_j m_k
```

其中

```
lambda_j = alpha_0 / (N_j + alpha_0)
```

这与公式 (3.270) 非常相似但不完全相同。主要区别在于，贝叶斯模型使用上下文相关的权重 lambda_j 将 m_k 与经验频率 f_jk 组合，而不是使用固定权重 lambda。这类似于自适应删除插值。此外，我们不是回退到经验边缘频率 f_k，而是回退到模型参数 m_k。

唯一剩下的问题是：我们应该为 alpha 和 m 使用什么值？让我们使用经验贝叶斯。

由于我们假设在给定 alpha 的情况下，转移矩阵的每一行在先验上是独立的，我们马尔可夫模型的边缘似然由以下给出：

```
p(D | alpha) = prod_j B(N_j + alpha) / B(alpha)
```

