
`Naïve Bayes`，顾名思义，是又一种试图逼近 `Bayes classifier` 的方法。正如我们将看到的，它通过做出 `conditional independence` 的简单假设来实现这种近似，而这种假设在实践中不太可能得到满足。

## 8.16.1 什么使得朴素贝叶斯“朴素”？

为了理解和欣赏是什么使得贝叶斯“朴素”，我们必须首先回顾这样一个事实：当我们实施诸如 `linear discriminant analysis` 之类的方法时，在实现模型时会做出大量假设。例如，我们假设密度函数是 `multivariate normal`；在 `linear discriminant analysis` 的情况下，我们假设协方差相等（在 `QDA` 中则不然）。所有这些假设使得拟合模型的任务相对“简单”，其含义是我们可以在“清单”上划掉许多项目，并假设它们是 `constant` 而非 `variable`。也就是说，通过在模型中做出假设，我们可以专注于我们想要关注的变化，并将其他要素视为“固定”而不波动，这类似于实验者在调查对象之外保持经验条件恒定，即所谓的 `experimental manipulation`。
另一个例子是，`linear regression` 在关系为线性的假设下是一个很好的模型。参数假设在促进任务方面有多么重要！它们可以说“为...做好准备”，以便我们可以迈出下一步并估计函数形式。我们从床铺已铺好一半开始。统计建模的很大一部分，实际上与大多数理论和叙述一样，是 `the specifying of assumptions a priori`（[邵, 2023](#ref.xhtml#re_CIT000334)）。
这就是 `Naïve Bayes` 与诸如 `linear discriminant analysis` 之类方法不同的地方。对于 `Naïve Bayes`，我们通常不会对参数形式做出假设，也不会对参数密度做出假设，例如施加 `multivariate normal` 分布。这并不是说我们不做 `any` 假设，而是我们所做的假设相当有限。下面是我们通常对 `Naïve Bayes` 所做的假设：
> `Within the kth class, the p predictors are independent.`
但上面到底是什么？请回顾基础概率论中事件 `A` 和 `B` 的独立性假设，
`p(A∩B) = p(A)p(B)`
其含义是联合事件 `A` 和 `B` 的概率等于它们无条件概率的乘积。请回顾如果两个事件不独立，则联合事件会涉及 `conditional` 概率：
`p(A∩B) = p(A)p(B/A)`
在 `A` 和 `B` 独立的情况下，有 `p(B) = p(B/A)`，于是我们得到，
```
\begin{array}{l}
{p\left( A \cap B \right) = p\left( A \right)p\left( B/A \right)}\\
{\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\, = p\left( A \right)p\left( B \right)}\\
\end{array}
```
(8.39)
等式 (8.39) 在概率论中通常也被称为 `product rule for independent events`。我们将把这一假设推广到 `densities` 而非变量，并表述为
`f[k](x) = f[k1](x[1]) ⋅ f[k2](x[2]) ⋅ ... ⋅ f[kp](x[p])`
其中不同的密度现在由 `k` 对 `p` 个变量进行索引。`Naïve Bayes` 假设对于给定的类别、组或类别，`predictors are independent`（[Hastie 等, 2009](#ref.xhtml#re_CIT000145)）。如果我们选择将组或类别直接纳入独立性陈述中，那么独立性陈述就成为 `conditional independence`：
`p(A,B/C) = p(A/C)p(B/C)`
(8.40)
其中 `C` 现在是在概率陈述中明确指出的类别成员，而不需要在我们之前对条件独立性的定义中“附加”成员陈述。也就是说，条件独立性只是将独立性的概念推广到条件概率。虽然 `Naïve Bayes` 的假设在技术上是关于条件独立性的，但正如许多其他作者所做的那样，谈论 `independence` 的假设而不是不断陈述 `conditional independence.` 更有意义。也就是说，我们在此讨论中隐含地指独立性 `within a particular class`。
现在，停下来想一想——`Are two events A and B ever truly independent?` 也就是说，我们能否现实地想象任何两个 `real` 事件是完全独立的？可能不会，不会比我们想象两个事件完全不相关更多。所有变量至少在 `some` 程度上相关，就像几乎所有事件在某种程度上相互依赖，至少在 `probabilistically` 意义上如此。你同事发现其变量之间存在相关性是 `expected` 的。`unexpected` 的结果是发现相关性恰好为 0。同样对于概率依赖，赢得彩票的概率很可能与老鼠住在你家里的概率 `not` 独立。我们经常 `assume` 它们是独立的（并且有充分理由，从实用角度看它们 `are`），但在概率上它们（可能）并非如此，即使由此产生的概率微乎其微。`Correlations and probabilities are not necessarily reflective of empirical processes`，尤其是考虑到概率通常是在连续尺度上测量的。
即使考虑到经验上的独立性几乎从未得到满足，做出独立性的 `assumption` 仍然是一个有用、务实且简化的假设，就像我们对 `LDA` 等事物所采用的假设是有用（且简化）的那样。因此，`Naïve Bayes` 并没有完全抛弃假设的制定，但可以说它所做的假设相当 `simple` 且 `easy`，例如条件独立性的假设。尽管如此，强调这里存在 `some` 假设很重要，即使它非常简单和基础。正如本书反复强调的那样，很少有程序是完全没有 `any` 假设的，即使它们被宣传为假设很少。即使在非参数技术中，我们通常也会发现隐藏的假设，尽管它们的重要性或影响通常远不及竞争对手的假设繁多的参数对应方法。
在 `Naïve Bayes` 中，条件独立性的假设是为了 `utility` 而做出的。我们事先知道它可能不成立。它是为了 `convenience` 和 `pragmatism` 而做出的，类似于在 `LDA` 中假设高斯分布的想法。`Naïve Bayes` 会正确估计吗？可能不会，因此它是 `biased` 的，但随着偏差的增加，方差会减小，这类似于使用 `ridge regression` 会增加偏差但减少方差。再次回顾基本的偏差-方差权衡：
`E(y[0]-f̂(x[0]))² = Var(f̂(x[0])) + [Bias[f̂(x[0])]]² + Var(ε)`
在 `Naïve Bayes` 的情况下，`Var(f̂(x[0]))` 通常会减少，而代价是偏差 `[Bias[f̂(x[0])]]²` 增加。
`Naïve Bayes` 易于理解，因为它更容易被理解为 `Bayes theorem` 的扩展，再次回顾如下：
```
p\left( y = k \middle| x = x_{i} \right) = \frac{\pi_{k}f_{k}\left( x_{i} \right)}{\sum\limits_{l = 1}^{K}{\pi_{1}f_{l}\left( x_{i} \right)}}
```
(8.41)
由于 `f[k](x[i]) = f[k1](x[1]) ⋅ f[k2](x[2]) ⋅ ... ⋅ f[kp](x[p])` 是条件独立性的结果，一旦我们将其代入贝叶斯的 (8.41)，我们就得到
