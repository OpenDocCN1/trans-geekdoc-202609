
## 数学推导

$$
\mathcal{F}(q,\mathbf{\xi}) = \int q(\mathcal{X}^{l})\ln\frac{p(\mathcal{X}^{l}|\mathcal{X};\mathbf{\xi})p(\mathcal{X};\mathbf{\xi})}{q(\mathcal{X}^{l})}d\mathcal{X}^{l}
= \int q(\mathcal{X}^{l})\ln\frac{p(\mathcal{X}^{l}|\mathcal{X};\mathbf{\xi})}{q(\mathcal{X}^{l})}d\mathcal{X}^{l} + \ln p(\mathcal{X};\mathbf{\xi})
$$

(12.66)

其中上述等式成立是因为 $\ln p(\mathcal{X};\mathbf{\xi})$ 不依赖于 $q(\mathcal{X}^{(l)})$，且后者积分为 1（作为概率分布）。右边第一项是所谓的 KL 散度（公式 (2.161)）的负值，该散度在 $q(\mathcal{X}^{(l)})$ 和 $p(\mathcal{X}^{(l)}|\mathcal{X};\mathbf{\xi})$ 之间，我们将其记为 `KL(q \parallel p)`。回顾一下，KL 散度衡量两个分布有多大差异。如果两个分布相等，则它们的 KL 散度为零。因此，最终我们得到：

$$
\ln p(\mathcal{X};\mathbf{\xi}) = \mathcal{F}(q,\mathbf{\xi}) + KL(q \parallel p)
$$

(12.67)

因为 KL 散度是非负量，即 `KL(q \parallel p) \ge 0`（习题 12.7），所以可得：

![Equation](img/fx013.jpg)

(12.68)

换句话说，泛函 `ℱ(q, ξ)` 是对数似然函数的一个下界。此外，当 `KL(q \parallel p) = 0` 时，该界变得紧致，这 *当且仅当* `q(X^(l)) = p(X^(l) | X; ξ)` 时成立。而且，前述界对 *所有* 分布 `q` 和 *所有* 参数 `ξ` 均有效。

前述发现为通过最大化其下界来最大化 `ln p(X; ξ)` 铺平了道路。这符合一类更通用的优化算法，称为 *极小化-极大化*（或极大化-极小化）（MM）方法 [20]。采用一个极小化代价函数（下界）且更易于最大化的代理函数。然后，迭代地最大化该下界将代价函数推向局部最大值。请注意，在我们的情况下，`ℱ` 的最大化涉及两项，即 `q` 和 `ξ`。我们将采用一种广泛使用的技术，称为 *交替优化*。这种方法强制要求一个迭代过程。从某些初始条件开始，先“冻结”所涉及项中一项的值，并针对另一项进行最大化。然后冻结后一项的值，针对前一项进行优化。这些交替步骤持续进行直到收敛。在我们当前的语境中，从任意的 `ξ^((0))` 开始，第 `(j + 1)` 次迭代包含以下步骤：

### 步骤 1：保持 `ξ^((j))` 固定，针对 `q` 进行优化

如果 `KL(q \parallel p) = 0`，则此步骤使 (12.68) 中的下界变紧，这仅在以下情况下发生：

`q^((j + 1))(X^(l)) = p(X^(l) | X; ξ^((j)))`,

(12.69)

即，如果我们令 `q(X^(l))` 等于给定 `X` 和 `ξ^((j))` 的后验分布；正如公式 (12.67) 所示，这使得界变得紧致，即：

`ln p(X; ξ^((j))) = ℱ(p(X^(l) | X; ξ^((j))), ξ^((j)))`,

(12.70)

### 步骤 2：固定 $q^{(j+1)}$

固定 $q^{(j+1)}$，将其代入 (12.68) 中 $q$ 的位置，并且因为该界对任意 $q$ 都成立，所以关于 $\boldsymbol{\xi}$ 进行最大化，即

$$
\boldsymbol{\xi}^{(j + 1)} = \arg\max_{\boldsymbol{\xi}} \mathcal{F}\left( p\left( \mathcal{X}^{l}|\mathcal{X};\boldsymbol{\xi}^{(j)} \right),\boldsymbol{\xi} \right).
$$

因此，我们现在得到了以下不等式：

$$
\ln p(\mathcal{X};\boldsymbol{\xi}^{(j+1)}) \ge \mathcal{F}(p(\mathcal{X}^{(l)}|\mathcal{X};\boldsymbol{\xi}^{(j)}),\boldsymbol{\xi}^{(j+1)}) \ge \mathcal{F}(p(\mathcal{X}^{(l)}|\mathcal{X};\boldsymbol{\xi}^{(j)}),\boldsymbol{\xi}^{(j)}),
$$

考虑到右边最后一项等于 $\ln p(\mathcal{X};\boldsymbol{\xi}^{(j)})$，我们得到

![Equation](img/fx014.jpg)

现在很容易看出，我们已经重新推导出了 EM 算法。确实，从公式 (12.63) 中 $\mathcal{F}(\cdot, \cdot)$ 的定义，我们可以得到

`ℱ(p(𝒳^(l)|𝒳; ξ^((j))), ξ) = 𝒬(ξ, ξ^((j))) − ∫ p(𝒳^(l)|𝒳; ξ^((j))) ln p(𝒳^(l)|𝒳; ξ^((j))) d𝒳^(l)`,

![Equation](img/si285.png) (12.71)

其中 `𝒬(ξ, ξ^((j)))` 与公式 (12.40) 中相同，且右边第二项与 `ξ` 无关；该项等于与 `q^((j + 1))(𝒳^(l))` 相关的熵。通过这条路径重新推导 EM 算法清楚地表明，被最大化的量是对数似然 `ln p(𝒳; ξ)`，并且保证其值在每次组合迭代步骤后不会减少。图 12.10 示意性地说明了构成第 `(j + 1)` 次迭代的两个 EM 步骤。

![Figure 12.10 The E-step adjusts q^{(j)}: = q^{(j)}(\mathcal{X}^{l})Equation so that its KL divergence from p_{\cdot | \cdot}^{(j)}: = p(\mathcal{X}^{l}|\mathcal{X};\mathbf{\xi}^{(j)})Equation becomes zero. The M-step maximizes with respect to ξ. We used pj to denote the evidence function.](img/gr010.jpg)

图 12.10 E 步调整 `q^((j)) := q^((j))(𝒳^(l))`，使其与 `p[⋅|⋅]^((j)) := p(𝒳^(l)|𝒳; ξ^((j)))` 的 KL 散度变为零。M 步针对 `ξ` 进行最大化。我们用 `p^(j)` 表示证据函数。

毋庸置疑，EM 算法并非万能药。我们很快将寻找变体来处理后验概率无法以解析形式给出的情况。此外，仍存在 M 步在计算上难以处理的情况。为此，已提出了若干变体（参见例如 [31,34]）。

### 备注 12.5

*   **EM 算法的在线版本**：我们已经指出，在许多大数据应用场景中，在线版本在实践中是首选。EM 算法也不例外，已经提出了许多相关版本。文献 [34] 基于下界解释提出了一种在线 EM 算法。文献 [6] 采用了随机近似论证。文献 [25] 报告了不同技术的比较研究。

*   在实践中，执行期望步骤（E 步）往往是难以处理的。在下一章中，我们将看到变分方法作为克服这一障碍的一种途径。另一种替代路径是采用蒙特卡洛采样技术（第 14 章）从相关分布中生成样本，并利用相应的样本均值计算来近似期望（例如参见文献[8,11]）。

## 12.8 概率分布的指数族

到目前为止应该已经清楚，贝叶斯框架始于为条件分布采用一种特定的函数形式，该形式“解释”了给定参数下观测值的生成过程，同时还需要一个先验分布来描述相关参数的随机性。后者等同于对相应学习任务进行正则化，并表达了我们在接收任何观测值之前对参数值的不确定性。贝叶斯学习的目标是获得给定观测变量值条件下参数的后验分布。如果精心选择条件分布和先验分布，后验的计算可以大大简化。从*指数族*中选择这些分布，会使后验的计算变成一项相当简单的任务。指数族分布将在下一章中用到，届时将讨论近似贝叶斯推断方法。

我们将在一般框架下探讨概率分布指数族的话题。设 `x ∈ ℝ^l` 为随机向量，`θ ∈ ℝ^K` 为随机（参数）向量。如果参数化的概率密度函数（PDF）`p(x|θ)` 具有以下形式，则称其为指数形式：

```
p(x|θ) = g(θ)f(x)exp(ϕ^T(θ)u(x)),
```

(12.72)

其中

```
g(θ) = 1 / ∫ f(x)exp(ϕ^T(θ)u(x)) dx
```

(12.73)

是 PDF 的归一化常数。如果 `x` 是离散随机变量且相应函数表示概率质量函数 `P(x|θ)`，则存在类似的定义；在这种情况下，公式(12.73)中的积分变为求和。向量 `ϕ(θ)` 包含所谓的*自然参数*集合，而 `f`、`u` 是定义该分布的函数。从第 3.7 节的因子分解定理可以很容易地看出，`u(x)` 是参数 `θ` 的*充分统计量*。请注意，指数族的一个属性是充分统计量的数量，即 `u` 的维数，是有限的，且与观测值的数量无关。如果 `ϕ(θ) = θ`，则称该指数族处于*规范*形式。许多广泛使用的分布都属于指数族，例如正态分布、指数分布、伽马分布、卡方分布、贝塔分布、狄利克雷分布、伯努利分布、二项分布和多项分布。不属于这一族的分布示例包括边界未知的均匀分布、学生 *t* 分布、拉普拉斯分布以及大多数混合分布（例如参见文献[40,46]）。

指数族的一个优势在于可以为 `θ` 找到共轭先验；即，导致后验 `p(θ|X)` 与先验 `p(θ)` 具有相同函数形式的先验（第 3.11.1 节，备注 3.4）。

给定公式 (12.72)，其共轭先验由下式给出：

```
p(θ; λ, v) = h(λ, v)(g(θ))^(λ)exp(ϕ^T(θ)v)
```

其中 `λ > 0` 和 `v` 被称为*超参数*；即控制其他参数的参数。因子 `h(λ, v)` 是适当的归一化常数。很容易看出，将先验 PDF 定义为公式 (12.74) 所示，将条件 PDF 定义为公式 (12.72) 所示，则后验 `p(θ|x)` 将具有与公式 (12.74) 相同的形式。

在给出一些示例之前，让我们更深入地探讨一下 `λ` 和 `v` 的作用，以及 `g(θ)` 和 `ϕ(θ)` 在公式 (12.74) 和 (12.72) 中的存在意义。假设 `x` 和 `θ` 满足公式 (12.72)–(12.74)，且令 `X = {x[1], …, x[N]}` 为一组独立同分布观测值。则

```
p(X|θ) = (g(θ))^N ∏_{n=1}^N f(x_n) exp( ϕ^T(θ) ∑_{i=1}^N u(x_i) )
```

和

### 贝叶斯后验分布推导

$$
p(\mathbf{\theta}|\mathcal{X}) \propto p(\mathcal{X}|\mathbf{\theta})p(\mathbf{\theta}) \propto {(g(\mathbf{\theta}))}^{\lambda + N}\exp\left( \mathbf{\phi}^{T}(\mathbf{\theta})\left( \mathbf{v} + \sum\limits_{n = 1}^{N}\mathbf{u}(\mathbf{x}_{n}) \right) \right).
$$

![Equation](img/si306.png)(12.76)

换句话说，后验分布具有以下超参数：

$$
\widetilde{\lambda} = \lambda + N,\quad \widetilde{\mathbf{v}} = \mathbf{v} + \sum\limits_{n = 1}^{N}\mathbf{u}(\mathbf{x}_{n}).
$$

![Equation](img/si307.png)(12.77)

解释公式 (12.77)，可以将 $\lambda$ 视为先验信息隐式贡献给贝叶斯学习过程的有效观测数量，而 $\mathbf{v}$ 是这些（隐式）$\lambda$ 个观测值对充分统计量贡献的总信息量。它们的具体值基本上量化了设计者希望嵌入问题中的先验知识量。

### 示例 12.4：高斯-伽马共轭对

设随机变量 $x$ 为标量，并假设

$$
p(x|\sigma²) = \mathcal{N}(x|\mu, \sigma²),
$$

![Equation](img/si308.png)(12.78)

其中 $\mu$ 已知，$\sigma²$ 将被视为未知随机参数。我们将证明：

1. $p(x|\sigma²)$ 属于指数族分布。

2. 使用精度 $\beta = \frac{1}{\sigma²}$ 在代数运算上更方便。因此，

$$
p(x|\beta) = \frac{\beta^{1/2}}{\sqrt{2\pi}}\exp\left( - \frac{1}{2}\beta{(x - \mu)}^{2} \right).
$$

![Equation](img/si312.png)(12.79)

3. 因此，$p(x|\beta)$ 属于指数族分布，具有

#### 数学推导与共轭先验分析

##### 基础函数定义

$$f(x) = \frac{1}{\sqrt{2\pi}},\quad \phi(\beta) = -\beta,\quad u(x) = \frac{1}{2}(x - \mu)²$$

![Equation](img/si314.png)

##### 归一化常数计算

$$g(\beta) = \frac{1}{\int_{-\infty}^{+\infty}\frac{1}{\sqrt{2\pi}}\exp\left( -\frac{1}{2}\beta(x - \mu)² \right)dx} = \beta^{1/2}$$

![Equation](img/si315.png)

##### 共轭先验分布

**2.** 方程 (12.78) 的共轭先验服从伽马分布。

方程 (12.74) 对应的共轭先验变为：

$$p(\beta;\lambda,v) = h(\lambda,v)\beta^{\frac{\lambda}{2}}\exp(-\beta v)$$

![Equation](img/si316.png) (12.80)

##### 伽马分布形式

其形式为：

$$\text{Gamma}(\beta|a,b) = \frac{1}{\Gamma(a)}b^{a}\beta^{a - 1}\exp(-b\beta)$$

![Equation](img/si317.png) (12.81)

##### 参数定义

参数为（参见第 2 章）：

$$a = \frac{\lambda}{2} + 1$$

![Equation](img/si318.png)

$$b = v$$

![Equation](img/si319.png)

归一化常数 $h(\lambda,v)$ 必然等于：

$$\frac{b^a}{\Gamma(a)}$$

![Equation](img/si320.png) ![Equation](img/si321.png)

函数 $\Gamma(a)$ 定义为：

$$\Gamma(a) = \int_{0}^{\infty} x^{a-1} e^{-x} dx$$

![Equation](img/si323.png)

###### 1. 单变量高斯分布的共轭先验

如果我们得到多个观测值 $x_n$，$n = 1, 2, \dots, N$，那么根据公式 (12.76) 和 (12.77)，结果后验将是一个 Gamma 分布，其参数为：

$$
\widetilde{b} = b + \frac{1}{2}\sum_{n=1}^{N}{(x_n - \mu)}² = b + \frac{N}{2}{\widehat{\sigma}}_{\text{ML}}²,
$$
