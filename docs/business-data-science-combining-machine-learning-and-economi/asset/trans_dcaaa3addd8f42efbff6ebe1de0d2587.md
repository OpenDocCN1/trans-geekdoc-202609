
## 关联规则

要在 R 中查找一组关联规则，你可以使用 `arules` 软件包中的 `apriori` 函数。围绕 `arules` 软件包构建了一整套生态系统，服务于市场购物篮分析的世界。要使用它，你需要先使用 `arules` 将数据转换为某种特殊的购物篮格式，但经过这些操作后，该软件包的使用变得非常简单。在此，我们对 lastfm 数据拟合关联规则，并返回提升度（lift）和置信度（confidence）较高的规则。

```r
> library(arules)
> playlists <- split(x=lastfm$artist, f=lastfm$user)
> playlists <- lapply(playlists, unique)
> playtrans <- as(playlists, "transactions")
>
> # find rules with support > .01 & confidence >.5 & length (# artists) <= 3
> musicrules <- apriori(playtrans,
+          parameter=list(support=.01, confidence=.5, maxlen=3))
> inspect(subset(musicrules, subset=lift > 5))
```

|  | 左项 (lhs) | 右项 (rhs) | 支持度 (support) | 置信度 (confidence) | 提升度 (lift) |
|---|---|---|---|---|---|
| 1 | {t.i.} | => | {kanye west} | 0.01040000 | 0.5672727 | 8.854413 |
| 2 | {the pussycat dolls} | => | {rihanna} | 0.01040000 | 0.5777778 | 13.415893 |
| 4 | {sonata arctica} | => | {nightwish} | 0.01346667 | 0.5101010 | 8.236292 |
| 5 | {judas priest} | => | {iron maiden} | 0.01353333 | 0.5075000 | 8.562992 |
| 20 | {led zeppelin, the doors} | => | {pink floyd} | 0.01066667 | 0.5970149 | 5.689469 |
| 21 | {pink floyd, the doors} | => | {led zeppelin} | 0.01066667 | 0.5387205 | 6.802027 |

我们发现，Judas Priest 的听众听 Iron Maiden 的可能性是普通人的九倍，而同时喜欢 Led Zeppelin 和 The Doors 的听众喜欢 Pink Floyd 的可能性是普通人的六倍。

关联规则可以提供一些有用的见解，但它们仅限于产品对或小产品集之间的比较。该算法以现代标准衡量仍然相当缓慢。相反，我们可以看看我们更广泛的工具箱。主题建模是一种特别适用于协同过滤的工具。多项响应模型非常适合二值选择数据，一旦你拟合了主题得分，你就可以建议那些在你的用户偏好的主题中出现概率较高的新产品。这是一个标准且稳健的 ML 工具（主题建模）在商业场景中具有即时适用性的例子，而在该场景中许多人仍在使用更旧的技术（市场购物篮关联规则）。

使用 `maptx`，我们发现在这份数据上它再次（巧合地）选择了 $K = 10$ 个主题，或者更准确地说是流派。每个主题/流派中排名前几的“词”现在是音乐艺术家。当我们按流派提升度对艺术家进行排序时，我们会看到那些相对于普通大众而言，特定流派听众更有可能喜欢的顶级艺术家。

```r
> lastfm <- read.csv("lastfm.csv", colClasses=rep("factor",4))
> # convert to slam sparse matrix
> x <- simple_triplet_matrix(i=as.numeric(lastfm$user),
    j=as.numeric(lastfm$artist), v=rep(1,nrow(lastfm)),
    nrow = nlevels(lastfm$user), ncol = nlevels(lastfm$artist),
    dimnames = list(levels(lastfm$user), levels(lastfm$artist)))
> summary( tpcs <- topics (x, K=5*(1:5)) )
```

按主题相对于空值的术语提升度（及使用百分比）排名前 5 的短语：

- [1] 'equilibrium', 'hypocrisy', 'turisas', 'norther', 'bloodbath' (13.6)
- [2] 'of montreal', 'animal collective', 'sufjan stevens', 'broken social scene', 'andrew bird' (12.5)
- [3] 'jordin sparks', 'the pussycat dolls', 'leona lewis', 'rihanna', 'kelly Clarkson' (11.1)
- [4] 'aerosmith', 'dire straits', 'lynryd skynyrd', 'led zeppelin', 'eric clapton' (10.2)
- [5] 'charlie parker', 'captain beefheart & his magic band', 'billie holiday', 'chet baker' (9.5)
- [6] 'the pigeon detectives', 'kaiser chiefs', 'dirty pretty things', 'the fratellis' (9.1)
- [7] 'comeback kid', 'the bouncing souls', 'chiodos', 'a day to remember', 'underoath' (8.9)
- [8] 'enya', 'garbage', 'pidzama porno', 'hey', 'skinny puppy' (8.8)
- [9] 'nas', 'j dilla', 'common', 'talib kweli', 'notorious b.i.g.' (8.7)
- [10] 'ferry corsten', 'paul van dyk', 'above & beyond', 'armin van buuren', 'tiesto' (7.6)

流派 1 似乎是金属乐，2 是独立摇滚，3 是流行乐，4 是经典摇滚，等等。这些高提升度艺术家对于那些在每个流派得分较高的听众（即具有较大 `wik` 的听众）来说可能是很好的推荐。这些艺术家足够小众，尚未进入听众的视野，但基于他们对共同流派的兴趣，我们预计听众会喜欢这些音乐。

## 词嵌入

我们以一些源自深度学习工作的自然语言处理中令人兴奋的新方法作为本章的结束。*词嵌入*最初被作为一种技术提出，用于对深度神经网络的输入进行降维。如第 10 章所述，这种初始降维是当代 ML 系统成功的关键部分。然而，词嵌入本身也很有价值：它强加了一种空间结构于词语之上，使研究语言的人能够推理意义之间的距离，并考虑文档中词语组合背后的代数逻辑。

在最初的深度学习语境中，嵌入层用向量值替换每个单词，使得例如 *hotdog* 变为三维嵌入空间中的位置 [1, –5, 0.25]（这只是为了说明；嵌入空间通常超过 100 维）。将其与标准的“独热”或词袋表示法进行比较，在后者中，*hotdog* 将表示为一个二元向量，其长度等于词汇表中的单词数量，设为 *p*。这个二元向量将在 *hotdog* 维度上有一个 1，其余 *p* – 1 个位置为 0。词嵌入将语言表示从大的二元空间转换到了更小的实值（且丰富得多的）空间。

词嵌入的基本思想与我们之前关于因子建模的讨论中涉及的概念有关。在那些语境中，我们探讨了将文档“嵌入”向量空间的方法——将每个文档 *i* 表示为主题权重向量 $\omega_{oi}$ 或 PCA 得分向量 $v_i$。这提供了文档的降维表示。你得到的不再是 *p* 维的词袋表示，而是 *K* << *p* 维的因子（主题）表示。词嵌入采用类似的降维方法，但针对的是单词本身，而不是整个文档。

存在多种不同的嵌入算法——正如深度神经网络有多种不同的架构一样。最常见和通用的嵌入是基于*词共现矩阵*构建的。其中包括流行的 Glove$^{13}$ 和 Word2Vec$^{14}$ 框架。在这类方法中，第一步是定义共现的概念。例如，在常见的 skip-gram 表述中，具有“窗口大小” *b*，如果两个单词出现在同一句子内且彼此相距 *b* 个单词以内，则它们共现。对于词汇大小 *p*，这将导致一个稀疏的 *p* × *p* 共现矩阵，其中每个 [*i*, *j*] 条目是单词 *i* 和 *j* 共现的次数。设该矩阵为 $C$。词嵌入算法旨在近似 $C$ 为两个低维矩阵的乘积：

$$\mathbf{C} \approx \mathbf{U V}^{\prime} .$$
(8.5)

这里，$U$ 和 $V$ 各自是 $p \times K$ 维的稠密实值矩阵。$K$ 是嵌入空间的维度；因此，$K << p$，且 $U$ 和 $V$ 都是非常瘦长的矩阵。$U$ 和 $V$ 的每一行——例如，$u_{j}$ 和 $v_{j}$——则是第 *j* 个单词的 *K* 维嵌入。公式 8.3 的推论是

$$c_{i j} \approx \boldsymbol{u}_{i}^{\prime} \mathbf{v}_{j} = \sum_{k=1}^{K} u_{i k} v_{j k},$$
(8.6)

使得这些嵌入尽可能总结单词的含义，因为它们的内积——线性代数中标准的距离度量——定义了预期它们共现的程度。

求解 $U$ 和 $V$ 的一种方法是利用奇异值分解（SVD）求解公式 8.5。这是线性代数中的核心算法，也可用于例如求解对称方阵的特征值和特征向量（从而计算主成分）。在实践中，大多数软件嵌入解决方案使用 SVD 的替代方法，旨在处理 $C$ 中大量的稀疏性（因为在标准语料库的限制窗口中，大多数单词从不共现）。

在许多算法下，特别是当共现是对称的$^{15}$，$U$ 和 $V$ 将互为镜像。因此，标准做法是取其中一个向量——例如，$u_{j}$——作为单词 $j$ 的单一嵌入位置。如开头所述，这些位置最初被视为中间输出——作为深度神经网络输入的处理步骤。然而，社会科学家和语言学家发现，单词位置的空间包含了关于用于训练嵌入的文档语言的丰富信息。例如，Word2Vec 的作者强调了嵌入空间中代数运算的可能性：如果你取 Paris 的向量，减去 France，加上 Italy，那么你会得到一个靠近 Rome 向量坐标的位置。从数据科学的角度来看，词嵌入开辟了利用单词顺序和上下文在预测任务中优势的选项。作为一个例子，Taddy [2015a] 描述了一个围绕 word2vec 嵌入构建的简单贝叶斯分类器，并将该分类器与我们在本章中介绍的其他技术进行了比较。

