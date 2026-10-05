

```
$val(S \cup \{j\}) = val(S)$
```

对于所有

```
$S \subseteq \{1, \dots, p\}$
```

那么

```
$$\phi_j = 0$
```

**相加性（Additivity）** 对于一个组合收益为 val+val 的游戏，其相应的 Shapley 值如下：

```
$$\phi_j + \phi_j^-
```

假设你训练了一个随机森林，这意味着预测是许多决策树的平均值。相加性性质保证了对于某个特征值，你可以单独计算每棵树的 Shapley 值，对它们取平均值，从而得到该特征对于随机森林的 Shapley 值。

## 8.5.3.2 直观理解

理解 Shapley 值的直观方法是以下插图：特征值以随机顺序进入房间。房间里的所有特征值参与游戏（即对预测做出贡献）。特征值的 Shapley 值是当该特征加入它们时，房间内联盟所获得的预测值的平均变化。

## 8.5.3.3 估算 Shapley 值

为了计算精确的 Shapley 值，必须评估包含第 j 个特征和不包含第 j 个特征的所有可能的特征值联盟（集合）。对于多个特征，该问题的精确解变得困难，因为可能的联盟数量呈指数级增长，因此 Strumbel 等人 (2014)$^{34}$ 提出了基于蒙特卡洛采样的近似方法：

```
$$\phi_j = \frac{1}{M} \sum_{m=1}^M (\hat{f}(x_m^j) - \hat{f}(x_m^-))
```

> $^{34}$Strumbel, Erik, and Igor Kononenenko. "Explaining prediction models and individual predictions with feature contributions." Knowledge and information systems 41.3 (2014): 647-665.

## 8.5 SHAPLEY 值

$\hat{f}(x_j^m)$ 是 x 的预测，其中随机数量的特征被来自随机数据点 $z$ 的特征值替换，特征 j 的相应值除外。向量 $x_j^m$ 与 $x_j^m$ 几乎完全相同，但值 $x_j^m$ 同样取自采样的 $z$。这 $M$ 个新实例中的每一个都是由两个实例组合而成的“弗兰肯斯坦怪物”。注意，在下面的算法中，特征的顺序实际上并没有改变——每个特征保持在传递给 `predict` 函数的相同位置。在这里在这里仅作为一种“技巧”：通过赋予特征一个新的顺序，我们获得了一种随机机制，帮助我们组合出“弗兰肯斯坦怪物”。对于出现在特征 $x_j$ 左侧的特征，我们从原始观测中取值，对于右侧的特征，我们从随机实例中取值。

单个特征值的近似 Shapley 估算：

- * 输出：第 j 个特征值的 Shapley 值
- * 需要：迭代次数 M、感兴趣的实例 x、数据矩阵 X 以及机器学习 f

- * 对于所有 $m=1, \dots, M$：
    - 从数据矩阵 X 中抽取随机实例 $z$
    - 选择特征值的随机排列 $o$
    - 选择顺序 $x_o = (x_{(1)}, \dots, x_{(j)}, \dots, x_{(p)})$
- 选择顺序 $z_o = (z_{(1)}, \dots, z_{(j)}, \dots, z_{(p)})$
- 构建两个实例
    - 带有：$x_{+j} = (x_{(1)}, \dots, x_{(j-1)}, z_{(j)}, z_{(j+1)}, \dots, z_{(p)})$
    - 不带：$x_{-j} = (x_{(1)}, \dots, z_{(j-1)}, x_{(j)}, z_{(j+1)}, \dots, z_{(p)})$

- * 计算边际贡献：$\phi_j^m = \hat{f}(x_{+j}) - \hat{f}(x_{-j})$

- * 计算平均值 Shapley 值：$\phi_j(x) = \frac{1}{M} \sum_{m=1}^M \phi_j^m$

首先，有一个感兴趣的实例 x、一个特征 j 和迭代次数 M。在每次迭代中，都会生成特征的随机顺序。通过组合感兴趣实例 $x$ 和样本 $z$ 的值创建两个新实例。实例 $x_{+j}$ 是感兴趣的实例，但特征 $j$ 之后的所有值都被替换为来自样本 $z$ 的特征值。实例 $x_{-j}$ 与 $x_{+j}$ 相同。计算预测的差异：

```
$\phi_j^m = \hat{f}(x_{+j}) - \hat{f}(x_{-j})$
```

对所有这些差异取平均值：

```
$\phi_j(x) = \frac{1}{M} \sum_{m=1}^M \phi_j^m$
```

平均处理隐含地根据 X 的概率分布对样本进行加权。对每个特征重复此过程以获得所有的 Shapley 值。

## 8.5.4 优点

预测与平均值之间的差异公平地分布在实例的特征上——这种性质将 Shapley 值与 LIME 等方法区分开来。LIME 不能保证预测是公平的。Shapley 值可能是提供完整解释的方法。在需要解释性的情况下——例如需要可解释性——Shapley 值可能是唯一的方法。Shapley 值可以提供完整的解释，因为它基于理论，并且在在某些情况下是公平分布的。Shapley 值提供了对比解释。通过与数据集的平均值进行比较，而不是单个点，Shapley 值是有效的。Shapley 值提供了局部性，LIME 等方法不具备这一点。Shapley 值的公理——效率、对称性、相加性——为解释提供了合理的依据。Shapley 值的解释是直观的。

## 8.5.5 缺点

计算 Shapley 值的精确值需要大量的计算。在 99% 的情况下，近似 Shapley 值是可行的，因为可能的联盟数量是 $2^k$。通过限制迭代次数 M，可以计算 Shapley 值。为了准确计算 Shapley 值，M 应该足够大。计算 Shapley 值会增加方差。通过计算 Shapley 值可以减少计算时间。Shapley 值在解释时存在问题，这在 LIME 产生的方法是不可能的。Shapley 值在解释模型时是可靠的。Shapley 值在在解释特征时是基于边际分布的，这优于 LIME 产生的方法。Shapley 值在解释模型时是符合理论的。Shapley 值可以提供稀疏解释（如 LIME 产生）。

## 8.5 SHAP

SHAP 是 Shapley 值的估算方法，由 Lundberg 和 Lee (2016)$^{35}$ 引入，Shapley 值是基于数据的。Shapley 值返回每个特征的解释。另一种方法是 breakDown，它在 *breakDown R 包*$^{41}$ 中实现，BreakDown 也显示了特征对预测的贡献，但计算

## 8.5.6 软件与替代方案

Shapley 值在 R 的 `iml` 和 `fastshap`$^{39}$ 包中实现。在 Julia 中，可以使用 `Shapley`$^{40}$。

SHAP 作为一种 Shapley 值的估算方法将在*下一章节*中介绍。另一种方法是 breakDown，它在 *breakDown R 包*$^{41}$ 中实现，BreakDown 也显示了特征对预测的贡献，但计算

> $35$https://github.com/lundberg/shap
$36$Lundberg, Scott, M., and Su-Lee, A. "A unified approach to interpreting model predictions." Advances in Neural Information Processing Systems (2017).
$37$Sundarajan, Mukund, and Amir Najafahi. "The Shapley values for model explanation." arXiv preprint:1908.08474 (2019).
$38$Janzing, Dominik, Leonin Morris, and Patrick Böck. "Feature relevance quantification in explainable AI. A causal problem." International Conference on Artificial Intelligence and Statistics. PMLR (2020).
$39$https://github.com/mlmgwell/fastshap
$40$https://github.com/ExpandingMan/Shapley.jl
$41$Staniak, Mateusz, and Przemysław Bielec. "Explanations of model predictions with life and breakDown packages." arXiv preprint arXiv:1804.01955 (2018).

