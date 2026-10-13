
通过最大化 $L(\cdot,\cdot;\boldsymbol{\theta})$ 来估计 $\boldsymbol{\theta}$，可以得到一个估计值，该估计值保证了根据最大似然准则，相应分布对可用训练集的最佳拟合。然而，我们的最终目标不是对数据的生成“机制”建模。我们的最终目标是正确地对它们进行分类。让我们将公式 [(16.62)](#Chp016_805-853_B9780443292385000226.xhtml#deq109) 重写为：

```
$L(Y,X;\boldsymbol{\theta}) = \sum\limits_{n = 1}^{N}\ln P(y_{n}|\boldsymbol{x}_{n};\boldsymbol{\theta}) + \sum\limits_{n = 1}^{N}\ln p(\boldsymbol{x}_{n};\boldsymbol{\theta}).$
```

为了偏向分类任务，仅最大化上述两项中的第一项来获得 $\boldsymbol{\theta}$ 更为合理，即：

```
$L_{c}(Y,X;\boldsymbol{\theta}) = \sum\limits_{n = 1}^{N}\ln P(y_{n}|\boldsymbol{x}_{n};\boldsymbol{\theta}) = \sum\limits_{n = 1}^{N}\left( \ln p(y_{n},\boldsymbol{x}_{n};\boldsymbol{\theta}) - \ln\sum\limits_{y_{n}}p(y_{n},\boldsymbol{x}_{n};\boldsymbol{\theta}) \right),$ (16.63)
```

其中对 $y_{n}$ 的求和是对 $y_{n}$ 所有可能取值（类别）进行的。这被称为*条件对数似然*（参见例如 [19,20,67]）。所得估计值 $\widehat{\boldsymbol{\theta}}$ 保证了在给定特征值的情况下，后验类概率在训练数据集上整体最大化；毕竟，贝叶斯分类是基于根据后验概率的最大值来选择 $\boldsymbol{x}$ 的类别。然而，必须小心。采用此类方法的代价是条件对数似然不可分解，必须调用更复杂的优化方案。最大化条件对数似然并不保证错误概率也被最小化。只有当 $\boldsymbol{\theta}$ 的估计旨在最小化经验错误概率时，才能保证这一点。然而，这种准则难以处理，因为它不可微；已有尝试通过使用近似平滑函数或爬山贪婪技术来处理它（例如 [58] 及其参考文献）。请注意，条件对数似然背后的基本原理与第 [15.4.3](#Chp015_755-803_B9780443292385000214.xhtml) 节讨论的条件随机场背后的原理密切相关。

![Figure 16.25 The Bayesian network associated with the naive Bayes classifier. The joint PDF factorizes as p(y,x\_{1},\\ldots,x\_{l}) = p(y)\\prod\_{i = 1}^{l}p(x\_{i}|y)Equation.](images/B9780443292385000226/gr025.jpg)
