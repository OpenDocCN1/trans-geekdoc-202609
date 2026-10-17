
![Figure 16.18 The black trajectory is not allowed to occur under the HMM model of Fig. 16.17. Transitions from state k = 3 to state k = 2 and from k = 3 to k = 1 are not permitted. In contrast, the state unfolding in the red curve is in agreement with the model.](img/gr018.jpg)

**图 16.18** 黑色轨迹不允许出现在 图 16.17 的 HMM 模型下。从状态 $k=3$ 到 $k=2$ 以及从 $k=3$ 到 $k=1$ 的转移是不允许的。相反，红色曲线的状态展开符合该模型。

### 16.5.1 推理

与任何图模型任务一样，最终目标是推理。在分类/识别背景下，有两种特别感兴趣的推理类型。我们在语音识别框架下讨论此问题；类似论证适用于其他应用。给定一组（输出变量）观测值 $\mathbf{y}[1], \dots, \mathbf{y}[N]$，我们必须判断这些观测对应哪个口语单词。在数据集中，每个口语单词由一个 HMM 模型表示，该模型是大量训练的结果。一个 HMM 模型由以下参数集完全描述：

#### HMM 模型参数

1.  **状态数**，$K$。
2.  `n = 1` 时初始状态处于状态 `k` 的概率，即 `P[k]`，`k = 1, 2, …, K`。
3.  转移概率集合 `P[ij]`，`i, j = 1, 2, …, K`。
4.  状态发射分布 `p(y|k)`，`k = 1, 2, …, K`，可以是离散的，也可以是连续的。通常，这些概率分布可能是参数化的，即 `p(y|k; θ[k])`，`k = 1, 2, …, K`。

在推理之前，假设所有涉及的参数都是已知的。HMM 参数的学习发生在训练阶段；我们稍后将讨论它。

对于识别，可以使用许多种评分。这里我们将讨论两种作为我们图模型方法直接结果的替代方案。关于更详细的讨论，请参见例如文献 [72]。

在第一种方法中，计算观测序列的联合分布，这是在将所有隐变量边缘化之后进行的；针对每个模型/词都执行此操作。然后选择得分值最大的那个词。这种方法对应于**求和-乘积规则**。另一种途径是为每个模型/词计算格子图中的最优轨迹；即得分最高的联合概率轨迹。随后，我们选择对应于最大最优值的模型/词。这种方法是**最大-求和规则**的一种实现。

###### 求和-乘积算法：HMM 情况

第一步是将 图 16.15 的有向图转换为无向图。^(¹¹⁴)

```
x_n^T = [x_{n,1}, x_{n,2}, ..., x_{n,K}]:
{
    x_{n,i} = 0,  i ≠ k
    x_{n,k} = 1.
}
```

然后我们可以紧凑地写为

```
P(x_1) = ∏_{k=1}^K P_k^{x_{1,k}}, (16.32)
```

和

$P(\mathbf{x}_{n}|\mathbf{x}_{n - 1}) = \prod\limits_{i = 1}^{K}\prod\limits_{j = 1}^{K}P_{ij}^{x_{n - 1,j}x_{n,i}}.$

![Equation](img/si225.png)(16.33)

确实，如果跳跃是从时间 *n* − 1 的特定状态 *j* 到时间 *n* 的特定状态 *i*，那么前面乘积中唯一保留的项就是对应的因子，*P*[*i**j*]。作为 图 16.15 的贝叶斯网络模型的直接结果，完整集合的联合概率分布写为

$p(Y,X) = P(\mathbf{x}_{1})p(\mathbf{y}_{1}|\mathbf{x}_{1})\prod\limits_{n = 2}^{N}P(\mathbf{x}_{n}|\mathbf{x}_{n - 1})p(\mathbf{y}_{n}|\mathbf{x}_{n}),$

![Equation](img/si227.png)(16.34)

其中

$p(\mathbf{y}_{n}|\mathbf{x}_{n}) = \prod\limits_{k = 1}^{K}\left( p(\mathbf{y}_{n}|k;\mathbf{\theta}_{k}) \right)^{x_{n,k}}.$

![Equation](img/si228.png)(16.35)

对应的连接树可以从图 16.15 中的图平凡地获得。将有向连接替换为无向连接并考虑大小为二的团，得到图 16.19A 中的图。然而，由于所有 `y[n]` 变量均被观测到（*实例化*），且不需要边缘化，它们的乘法贡献可以被相应的条件概率吸收，从而得到图 16.19B 的图。或者，如果考虑节点 `(x[1], y[1])` 和 `(x[n-1], x[n], y[n])`，`n = 2, 3, …, N`，形成与以下势函数相关联的团，也可以获得此连接树：

```
ψ1 = P(x[1])p(y[1]|x[1]) (16.36)
```

和

```
ψn = P(x[n]|x[n-1])p(y[n]|x[n]), n = 2, …, N. (16.37)
```

图 16.19B 的连接树是通过从团中消除节点（从 `x[1]` 开始）得到的。注意归一化常数等于一，`Z = 1`。

![Figure 16.19 (A) The junction tree that results from the graph of Fig. 16.15. (B) Because yn are observed, their effect is only of a multiplicative nature (no marginalization is involved) and their contribution can be trivially absorbed by the potential functions (distributions) associated with the latent variables.](img/gr019.jpg)

**图 16.19** (A) 由图 16.15 的图得到的连接树。(B) 因为 `y[n]` 被观测到，它们的影响仅具有乘法性质（不涉及边缘化），且它们的贡献可以平凡地被与潜在变量相关联的势函数（分布）吸收。

要将求和-乘积规则应用于连接树，公式 (16.5) 现在变为

$$

\mu_{V_{n}\rightarrow S_{n}}(\mathbf{x}_{n}) = \sum\limits_{\mathbf{x}_{n - 1}}\psi_{n}(\mathbf{x}_{n - 1},\mathbf{y}_{n},\mathbf{x}_{n})\mu_{S_{n - 1}\rightarrow V_{n}}(\mathbf{x}_{n - 1}) = \sum\limits_{\mathbf{x}_{n - 1}}\mu_{S_{n - 1}\rightarrow V_{n}}(\mathbf{x}_{n - 1})P(\mathbf{x}_{n}|\mathbf{x}_{n - 1})p(\mathbf{y}_{n}|\mathbf{x}_{n}).

$$

![Equation](img/si234.png)

此外，

$$

\mu_{S_{n-1}\rightarrow V_{n}}(\mathbf{x}_{n-1}) = \mu_{V_{n-1}\rightarrow S_{n-1}}(\mathbf{x}_{n-1}).

$$

![Equation](img/si235.png) (16.38)

因此，

####### 概率消息传递公式

$$

\mu_{V_n \rightarrow S_n}(\mathbf{x}_n) = \sum_{\mathbf{x}_{n-1}} \mu_{V_{n-1} \rightarrow S_{n-1}}(\mathbf{x}_{n-1}) P(\mathbf{x}_n | \mathbf{x}_{n-1}) p(\mathbf{y}_n | \mathbf{x}_n)

$$

![Equation](img/si236.png) (16.39)

初始条件为：

$$

\mu_{V_1 \rightarrow S_1}(\mathbf{x}_1) = P(\mathbf{x}_1) p(\mathbf{y}_1 | \mathbf{x}_1)

$$

![Equation](img/si237.png) (16.40)

在 HMM 文献中，通常使用“alpha”符号表示交换的消息，即：

$$

\alpha(\mathbf{x}_n) := \mu_{V_n \rightarrow S_n}(\mathbf{x}_n)

$$

![Equation](img/si238.png) (16.41)

如果考虑消息传递在节点 $V_n$ 处终止，则根据公式 (16.7)，并考虑到变量 $\mathbf{y}_1, \dots, \mathbf{y}_n$ 被聚类到观测值（回顾公式 (15.44) 后的相关注释），可以很容易地看出：

$$

\alpha(\mathbf{x}_n) = p(\mathbf{y}_1, \mathbf{y}_2, \dots, \mathbf{y}_n, \mathbf{x}_n)

$$

![Equation](img/si241.png) (16.42)

这也可以从公式 (16.39) 和 (16.40) 中的相应定义推导出来；除 `x[n]` 之外的所有隐变量都已被边缘化掉了。这是一组 *K* 个概率值（对应 `x[n]` 的每个取值一个）。例如，对于 `x[n] : x[n, k] = 1`，`α(x[n])` 是轨迹在时刻 *n* 处于状态 *k* 且获得了直到并包括时刻 *n* 的特定观测值的概率。从公式 (16.42) 可以很容易地得到包含 *N* 个时间瞬间的观测序列的联合概率分布（证据），即

![Equation](img/fx007.jpg)

正如本节开头所述，这是一个用于分类/识别的量。

在信号处理“术语”中，`α(x[n])` 的计算被称为*滤波*递归。根据 `α(x[n])` 的定义，我们有 \[2\]

![Equation](img/fx008.jpg)(16.43)

正如将在第 17 章中讨论的卡尔曼滤波器那样，那里唯一的区别将是求和被积分所取代。在采用了高斯分布后，这些积分转化为相应均值和协方差矩阵的更新。公式 (16.43) 的物理意义是：预测器利用 *n* 时刻之前的所有过去信息提供状态预测。然后，该信息根据在时刻 *n* 接收到的观测 `y[n]` 进行修正。因此，基于直到并包括当前时刻 *n* 的整个观测序列的更新信息可以通过以下方式轻松获得：

```
P(\mathbf{x}_{n}|Y_{[1:n]}) = \frac{\alpha(\mathbf{x}_{n})}{p(Y_{[1:n]})},
```

其中分母由 `∑[x[n]] α(x[n])` 给出，且 `Y[[1 : n]] := (y[1], …, y[n])`。

现在让我们继续进行第二阶段的消息传递，方向与之前相反，以获得

$$

\mu_{V_{n + 1}\rightarrow S_{n}}(\mathbf{x}_{n}) = \sum\limits_{\mathbf{x}_{n + 1}}\mu_{S_{n + 1}\rightarrow V_{n + 1}}(\mathbf{x}_{n + 1})P(\mathbf{x}_{n + 1}|\mathbf{x}_{n})p(\mathbf{y}_{n + 1}|\mathbf{x}_{n + 1}),

$$

![Equation](img/si249.png)

其中

$$\mu_{S_{n + 1}\rightarrow V_{n + 1}}(\mathbf{x}_{n + 1}) = \mu_{V_{n + 2}\rightarrow S_{n + 1}}(\mathbf{x}_{n + 1}).$$

![Equation](img/si250.png)

因此，

$$

\mu_{V_{n + 1}\rightarrow S_{n}}(\mathbf{x}_{n}) = \sum\limits_{\mathbf{x}_{n + 1}}\mu_{V_{n + 2}\rightarrow S_{n + 1}}(\mathbf{x}_{n + 1})P(\mathbf{x}_{n + 1}|\mathbf{x}_{n})p(\mathbf{y}_{n + 1}|\mathbf{x}_{n + 1}),

$$

![Equation](img/si251.png) (16.44)

其中

*μ*[*V*[*N* + 1] → *S*[*N*]](**x**[*N*]) = 1.

![Equation](img/si252.png)(16.45)

请注意，*μ*[*V*[*n* + 1] → *S*[*n*]](**x**[*n*]) 涉及 *K* 个值，并且对于其中每一个值的计算都要执行 *K* 次求和。因此，复杂度按每个时刻 𝒪(*K*²) 缩放。在 HMM 文献中，使用符号“beta”,

*β*(**x**[*n*]) :  = *μ*[*V*[*n* + 1] → *S*[*n*]](**x**[*n*])。

![Equation](img/si255.png)(16.46)

根据公式 (16.44) 和 (16.45) 中的递归定义，其中 **x**[*n* + 1], **x**[*n* + 2], …, **x**[*N*] 已被边缘化掉，我们可以等价地写成

*β*(**x**[*n*]) = *p*(**y**[*n* + 1], **y**[*n* + 2], …, **y**[*N*]|**x**[*n*])。

![Equation](img/si257.png)(16.47)

也就是说，在 **x**[*n*] 的值给定条件下，例如 **x**[*n*] : *x*[*n**k*] = 1，*β*(**x**[*n*]) 是当系统在时刻 *n* 处于状态 *k* 时，观测值 **y**[*n* + 1], …, **y**[*N*] 被发射的联合分布的值。

我们现在拥有计算边缘分布所需的所有“要素”。从公式 (16.7) 可得（基于 HMM 的独立性质进行解释）

*p*(**x**[*n*], **y**[1], **y**[2], …, **y**[*N*]) = *μ*[*V*[*n* − 1] → *S*[*n*]](**x**[*n*]) *μ*[*V*[*n* + 1] → *S*[*n*]](**x**[*n*]) = *α*(**x**[*n*]) *β*(**x**[*n*]),

进而得到

这部分递归称为*平滑*递归。请注意，在此计算中，过去（通过*α*(**x**[*n*]））和未来（通过*β*(**x**[*n*]））数据均参与其中。

求得*γ*(**x**[*n*])的另一种方法是通过其自身的递归以及*α*(**x**[*n*])，从而避免使用*β*(**x**[*n*])（问题 16.16）。在此场景下，两个传递的消息均与关于**x**[*n*]的概率相关，在处理线性动态系统的情况时具有特定优势。

最后，由公式(16.6)并回顾公式(16.38)、(16.41)和(16.46)，我们得到

$p(\mathbf{x}_{n-1}, \mathbf{x}_n, Y) = P(\mathbf{x}_n|\mathbf{x}_{n-1})p(\mathbf{y}_n|\mathbf{x}_n)\mu_{S_n \to V_n}(\mathbf{x}_n)\mu_{S_{n-1} \to V_n}(\mathbf{x}_{n-1}) = \alpha(\mathbf{x}_{n-1})P(\mathbf{x}_n|\mathbf{x}_{n-1})p(\mathbf{y}_n|\mathbf{x}_n)\beta(\mathbf{x}_n)$

![Equation](img/si264.png) (16.50)

或

$$p(\mathbf{x}_{n-1}, \mathbf{x}_n|Y) = \frac{\alpha(\mathbf{x}_{n-1})P(\mathbf{x}_n|\mathbf{x}_{n-1})p(\mathbf{y}_n|\mathbf{x}_n)\beta(\mathbf{x}_n)}{p(Y)} := \xi(\mathbf{x}_{n-1}, \mathbf{x}_n).$$

![Equation](img/si265.png) (16.51)

因此，*ξ*(·, ·) 是一个包含 *K*² 个概率值的表。令 *ξ*(*x*[*n* − 1, *j*], *x*[*n*, *i*]) 对应于 *x*[*n* − 1, *j*] = *x*[*n*, *i*] = 1。那么 *ξ*(*x*[*n* − 1, *j*], *x*[*n*, *i*]) 就是系统在时刻 *n* − 1 和 *n* 分别处于状态 *j* 和 *i* 的概率，条件是给定的观测序列。

在第 15.7.4 节中，提出了一种消息传递方案，用于高效计算联合分布的最大值。这也可以应用于与 HMM 相关的连接树。由此产生的算法称为 *Viterbi* 算法。Viterbi 算法直接源自通用的 max-sum 算法。该算法与之前推导的算法相似；只需将求和运算替换为最大值运算。正如我们在讨论 max-product 规则时所评论的，计算使联合概率最大化的完整集合序列（**y**[*n*], **x**[*n*]), *n* = 1, 2, …, *N*，使用回溯，等价地定义了二维网格中的最优轨迹。

除了识别之外，另一个在实践中感兴趣的推理任务是预测，即给定一个 HMM 和观测序列 **y**[*n*], *n* = 1, 2, …, *N*，最优地预测值 **y**[*n* + 1]。这也可以通过适当的边缘化高效地执行（问题 16.17）。

### 16.5.2 HMM 中的参数学习
