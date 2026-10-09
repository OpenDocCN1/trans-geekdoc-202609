

Bolukbasi等人[2016]的一项工作很好地说明了嵌入技术的潜力。在这项研究中，作者使用Google新闻语料库训练了一个标准的word2vec嵌入算法。他们考察了既定*性别*词汇之间的差异（例如，*man*的向量减去*woman*的向量，或者*father*的向量减去*mother*的向量），以此在嵌入空间中建立一条从男性气质到女性气质的轴线。然后，他们计算了大量本应性别中立的术语在这条轴上的位置。例如，图8.12展示了位于这条男对女轴线极端位置的职衔。显而易见，嵌入空间已经*学到*了——基于新闻文章中词语的使用方式——这些职业在刻板印象中通常被视为女性和男性职业。

![](img/315929ad4bddd26368466d02e06e2385_351_0.png)

图 8.12：摘自Bolukbasi等人[2016]的图表，展示了在基于Google新闻训练的嵌入空间中，位于估算出的男对女轴极端位置的职衔。

除了指出记者的大男子主义外，作者还强调了这样一种事实：在此数据上训练的机器学习算法将采纳相同的偏见。由训练数据中的偏见导致的人工智能偏见是一个行业正在努力解决的重要问题。在这种情况下，他们提出了一种巧妙的解决方案：你获取所有*应该*性别中立的词汇，并*减去*它们嵌入向量中估算出的性别方向。正如从巴黎减去法国会得到一个与“首都”这一通用概念相关的位置一样，这种代数运算应当使这些职业移动到不再存在性别偏见的位置。事实上，作者证明，在这些去偏向量上训练的机器学习算法在回答要求性别中立答案的问题时表现得更出色。

有多种不同的软件解决方案可用于拟合嵌入。Google发布了word2vec的C代码，它已被封装以便在包括R在内的多种语言中使用。`text2vec`包实现了Glove和其他嵌入算法，且作者提供了许多演示其用法的实例。如果你愿意使用Python，有许多选择，包括`gensim`库中快速且内存高效的实现（该库还提供了一些演示笔记本）。虽然本书不会详细讲解代码细节，但词嵌入现在已成为一种非常普遍的操作，你应该不难找到适合你的计算环境和数据规模的实现方案。

- Matthew Gentzkow, Bryan Kelly, 和 Matt Taddy. Text-as-data. NBER working paper 23276, 2017.
- Frederick Mosteller 和 David L. Wallace. Inference in an authorship problem. Journal of the American Statistical Association, 58:275–309, 1963.
- Daniel Jurafsky 和 James H. Martin. Speech and Language Processing, 第2版. Prentice Hall, 2009.
- Matthew Gentzkow 和 Jesse Shapiro. What drives media slant? Evidence from U.S. daily newspapers. Econometrica, 78:35–72, 2010.
- 这也优于通过回归到按总言语量归一化的计数所得到的结果。
- David M. Blei, Andrew Y. Ng, 和 Michael I. Jordan. Latent Dirichlet allocation. Journal of Machine Learning Research, 3:993–1022, 2003.
- David M. Blei 和 John D. Lafferty. Dynamic topic models. In Proceedings of the 23rd international conference on Machine learning, pages 113–120, 2006.
- Matthew D. Hoffman, David M. Blei, Chong Wang, 和 John Paisley. Stochastic variational inference. The Journal of Machine Learning Research, 14: 1303–1347, 2013.
- Matt Taddy. On estimation and selection for topic models. In Proceedings of the 15th International Conference on Artificial Intelligence and Statistics (AISTATS 2012), 2012.
- 该软件从未试图拟合 K = 25，因为贝叶斯因子（BF）从 10 到 15 以及从 15 到 20 都下降了。
- 在这个例子中，我们需要将比率 $\lambda_T$ / $\lambda_I$ 从默认值 0.01 降低到 0.001（通过 `lmr=le-3`），以获得一组包含足够低惩罚的候选模型。如果你运行 `gamir` 并发现 AICc 选择了候选集边缘的模型（即最小惩罚处，$\lambda$），你就会知道需要这样做。你希望模型选择算法选择候选集*内部*的模型。
- Matt Taddy. *Multinomial inverse regression for text analysis*. *Journal of the American Statistical Association*, 108: 755–770, 2013b.
- Jeffrey Pennington, Richard Socher, 和 Christopher Manning. *Glove: Global vectors for word representation*. In *Proceedings of the 2014 Conference on Empirical Methods in Natural Language Processing (EMNLP)*, pages 1532–1543, 2014.
- Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg S. Corrado, 和 Jeff Dean. *Distributed representations of words and phrases and their compositionality*. In *Advances in Neural Information Processing Systems*, pages 3111–3119, 2013.
- 共现矩阵不必是对称的。例如，你可以为每个词定义前后长度不同的共现窗口。在这种情况下，*U* 和 *V* 中的每一个都将包含独特的*方向性*嵌入信息。但常见的方法都是对称的。
- Tolga Bolukbasi, Kai-Wei Chang, James Y. Zou, Venkatesh Saligrama, 和 Adam T. Kalai. *Man is to computer programmer as woman is to homemaker? Debiasing word embeddings*. In *Advances in Neural Information Processing Systems*, pages 4349–4357, 2016.

![](img/315929ad4bddd26368466d02e06e2385_354_0.png)

## 非参数方法

到目前为止，我们接触过的所有回归都是参数化的。它们对输入如何影响响应施加了限制，例如强制关系通过线性模型起作用。这被称为参数化分析，因为这些模型具有参数，并且通过优化参数来拟合数据。

非参数回归算法对x和y之间的关系所做假设更少。在纯粹形式下，随着观察更多数据，这些算法将学习x和y之间的真实关系，无论这种真实情况看起来如何。随着数据的积累，你的预测将任意接近真理。这种完全非参数的技术除了假设观测值之间独立外，对数据生成过程不做任何其他假设。本章将介绍回归（和分类）树及森林，作为一种完全非参数的回归方法，它们在商业数据科学中找到了成功的应用。

回顾你在本书其他部分学到的知识，你应该预期通过非参数方法获得的灵活性会导致过拟合，除非结合某种正则化。不幸的是，惩罚偏差和CV选择不适用于非参数回归的正则化——拟合对象不稳定，微小的数据扰动会导致预测性能截然不同。幸运的是，你可以使用一种称为袋装法（bagging）的技术来既稳定又正则化模型，当应用于树时，这就导致了随机森林。这种策略有时也被称为模型平均；它是实用非参数方法的必要组成部分。

袋装法很棒，但它只能帮助有限。当维度变得太大时，非参数方法的超级灵活性使得难以学到任何有用的东西。你在使用完全非参数回归时应谨慎，除非处于数据量远大于维度的设置中（即，只有当 $p \ll n$ 时，你才能使用非参数方法）。一个好经验法则是希望 $p < n/4$。在高维问题中，我们倾向于使用半参数方法，结合有针对性的非参数灵活性和鼓励稳定性与降维的参数限制。在章节末尾，我们将简要提及*高斯过程*，这是一种相对直观的半参数程序。而在**第10章**关于人工智能的部分，我们将介绍深度神经网络作为一种在当代机器学习（ML）中扮演明星角色的半参数方法。然而，有许多实际数据应用场景中 $p$ 很大但 $n$ 更大得多；在这些设置中，你应该考虑森林和其他基于树的方法作为你的默认预测工具。

### 决策树

决策树是一种将输入映射到结果的逻辑系统。树是*层次化*的：你使用一系列有序步骤（决策节点）来得出结论。

树逻辑使用一系列步骤来得出结论。**图 9.1** 展示了一个关于决定是否带伞去上班的过程的简单例子：每个分支都依赖于可用的预报数据（来自天气预报或当前状况），最终决定——*叶节点*——基于这些分支条件下的降雨预测。树节点具有父子结构：除了根节点（“醒来”）外，每个节点都有一个父节点，除了叶节点外，每个节点都有两个子节点。构建有效决策树的诀窍在于让决策节点序列组合起来做出良好的最终选择。

