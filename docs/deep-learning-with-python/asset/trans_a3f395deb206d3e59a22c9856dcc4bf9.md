
to create a Transformer encoder, one of the basic components of the Transformer architecture, and we’ll apply it to the IMDB movie review classification task.

## 11.4.1 理解自注意力

当你阅读这本书时，可能会浏览某些部分，认真阅读其他部分，这取决于你的目标或兴趣。如果你的模型也这样做呢？这是一个简单却强大的想法：模型看到的并非所有输入信息对当前任务都同样重要，因此模型应该对某些特征“多加关注”，而对其他特征“少加关注”。

这听起来耳熟吗？你在这本书中已经两次遇到过类似的概念：

- 卷积网络中的最大池化会查看空间区域中的一组特征，并只保留一个特征。这是一种“全有或全无”的注意力形式：保留最重要的特征，丢弃其余部分。
- TF-IDF 归一化根据不同标记可能携带的信息量，为标记分配重要性分数。重要标记会被增强，而无关标记会被淡化。这是一种连续形式的注意力。

你可以想象出许多不同形式的注意力，但它们都始于为一组特征计算重要性分数，更相关的特征得分更高，不太相关的特征得分更低（参见图 11.5）。这些分数应如何计算，以及应该如何使用它们，会因方法而异。

![](img/ab452ecf572a1f1372915be13bd8088f_361_0.png)

图 11.5 深度学习中“注意力”的一般概念；输入特征会被分配“注意力分数”，这些分数可用于指导输入的下一个表示。

关键的是，这种注意力机制不仅可以用于突出或擦除某些特征，还可以用于使特征具有上下文感知能力。你刚刚学习过词嵌入——捕捉不同单词之间语义关系“形状”的向量空间。在嵌入空间中，一个单词有固定的位置——与空间中每个其他单词的固定关系集。但语言的运作方式并非完全如此：一个词的含义通常取决于上下文。当你标记日期时，你谈论的并不是约会时的同一个“date”，也不是你会在市场上购买的那种 date。当你说“我一会儿见”时，“see”这个词的含义与“我会把这个项目做到底”或“我明白你的意思”中的“see”有细微差别。当然，像“he”、“it”、“in”这样的代词的含义完全取决于句子，甚至可以在一个句子中多次变化。

显然，一个智能的嵌入空间会根据周围的其他单词，为一个单词提供不同的向量表示。这就是自注意力发挥作用的地方。自注意力的目的是利用序列中相关标记的表示来调制标记的表示。这产生了具有上下文感知能力的标记表示。考虑一个示例句子：“The train left the station on time.” 现在，考虑句子中的一个单词：station。我们谈论的是哪种车站？可能是广播电台吗？也许是国际空间站？让我们通过自注意力算法来弄清楚（参见图 11.6）。

![](img/ab452ecf572a1f1372915be13bd8088f_362_0.png)

图 11.6 自注意力：在“station”与序列中每个其他单词之间计算注意力分数，然后用这些分数对单词向量的加权求和，结果成为新的“station”向量。

步骤 1 是计算“station”的向量与句子中每个其他单词之间的相关性分数。这些就是我们的“注意力分数”。我们将简单地使用两个单词向量之间的点积作为其关系强度的度量。这是一个计算效率很高的距离函数，在 Transformer 出现很久以前，它就已经是关联两个词嵌入的标准方法。在实际中，这些分数还会经过缩放函数和 softmax 处理，但目前这只是一个实现细节。

步骤 2 是计算句子中所有单词向量的加权和，权重为我们的相关性分数。与“station”密切相关的单词会对总和贡献更多（包括“station”单词本身），而无关单词几乎不贡献。得到的向量是我们对“station”的新表示：一个包含周围上下文的表示。特别是，它包含了部分“train”向量，澄清这实际上是一个“火车站”。

你会对句子中的每个单词重复此过程，从而生成编码句子的新向量序列。让我们看看类似 NumPy 的伪代码：

```
def self_attention(input_sequence):
    output = np.zeros(shape=input_sequence.shape)
    for i, pivot_vector in enumerate(input_sequence):
        scores = np.zeros(shape=(len(input_sequence), ))
        for j, vector in enumerate(input_sequence):
            scores[j] = np.dot(pivot_vector, vector.T)
        scores /= np.sqrt(input_sequence.shape[1])
        scores = softmax(scores)
        new_pivot_representation = np.zeros(shape=pivot_vector.shape)
        for j, vector in enumerate(input_sequence):
            new_pivot_representation += vector * scores[j]
        output[i] = new_pivot_representation
    return output
```

- 遍历输入序列中的每个标记。
- 计算标记与每个其他标记之间的点积（注意力分数）。
- 按归一化因子缩放，并应用 softmax。
- 按注意力分数对所有标记求加权和。
- 该和即为我们的输出。

当然，在实际中你会使用向量化实现。Keras 提供了一个内置层来处理它：MultiHeadAttention 层。以下是使用方法：

```
num_heads = 4
embed_dim = 256
mha_layer = MultiHeadAttention(num_heads=num_heads, key_dim=embed_dim)
outputs = mha_layer(inputs, inputs, inputs)
```

读到这里，你可能在想

- 为什么要将 inputs 传递给层 *三* 次？这似乎是多余的。
- 我们所说的这些“多头”是什么？这听起来很吓人——如果把它们切掉，它们也会重新长出来吗？

这两个问题都有简单的答案。让我们看一下。

## 泛化自注意力：查询-键-值模型

到目前为止，我们只考虑过一个输入序列。然而，Transformer 架构最初是为机器翻译开发的，其中你需要处理两个输入序列：当前正在翻译的源序列（例如“How’s the weather today?”）以及将其转换为的目标序列（例如“¿Qué tiempo hace hoy?”）。Transformer 是一个序列到序列模型：它被设计用于将一个序列转换为另一个序列。你将在本章后面深入学习序列到序列模型。

现在让我们退一步。我们介绍的自注意力机制，在示意图中执行以下操作：

```
outputs = sum(inputs * pairwise_scores(inputs, inputs))
```

这意味着“对 inputs（A）中的每个标记，计算该标记与 inputs（B）中每个标记的相关程度，并使用这些分数对来自 inputs（C）的标记求加权和。” 关键的是，没有什么要求 A、B 和 C 必须引用同一个输入序列。在一般情况下，你可以使用三个不同的序列来执行此操作。我们将称它们为“query”、“keys”和“values”。该操作变为“对 query 中的每个元素，计算该元素与每个 key 的相关程度，并使用这些分数对 values 求加权和”：

```
outputs = sum(values * pairwise_scores(query, keys))
```

这一术语源自搜索引擎和推荐系统（参见图 11.7）。假设你正在输入一个查询从你的收藏中检索照片——“dogs on the beach”。在内部，数据库中的每张照片都由一组关键字描述——“cat”、“dog”、“party”等。我们将称这些关键字为“keys”。搜索引擎首先会将你的查询与数据库中的 keys 进行比较。“Dog” 得到 1 的匹配，“cat” 得到 0 的匹配。然后它会按匹配强度（即相关性）对这些 keys 进行排名，并按相关性顺序返回与前 N 个匹配项关联的照片。

从概念上讲，这就是 Transformer 风格注意力在做的事情。你有一个描述你正在寻找的内容的参考序列：即 query。你有一个试图从中提取信息的知识体：即 values。每个 value 都分配了一个 key，该 key 用一种可以轻松与查询比较的格式描述 value。你只需将 query 与 keys 匹配。然后返回 values 的加权和。

在实际中，keys 和 values 通常是同一个序列。例如，在机器翻译中，query 将是目标序列，而源序列将同时扮演 keys 和 values 的角色：对于目标中的每个元素（例如
