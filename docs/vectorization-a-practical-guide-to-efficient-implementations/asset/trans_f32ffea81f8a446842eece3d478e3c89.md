

![](img/e891acaacd4fb5b80dab2ed824618203_392_0.png)

图 10.10 创建 output_index_ads 矩阵的示例。(a) 创建账本矩阵以跟踪广告项索引 ads_indices 中应收集哪些索引。(b) 使用排序后的 ads_items 和位置账本 anchored_positions 将广告收集到输出中对应位置的分步迭代示例。让我们通过三个示例进行演示。在步骤 1 中，我们从位置 (0, 0) 开始。账本（中间）矩阵指向索引值 0。我们查找批次 0 中索引 0 处的值，从 ads_items 矩阵（左侧）中获取项 0（即填充值），并将此项放入输出 output_index_ads（右侧）。跳到步骤 5，位置 (0, 4)，账本（中间）表明我们应该收集索引 2 处的项，该项在 ads_items 矩阵（左侧）中具有项值 2。然后我们将项 2 放入 output_index_ads 矩阵（右侧）的对应位置。跳到倒数第二步，位置 (2, 6)，账本（中间）表明我们应该收集索引 3 处的项，该项对应 ads_items 矩阵（左侧）中的项值 1。因此，我们将项 1 放入 output_index_ads 矩阵（右侧）的位置 (2, 6)。

![](img/e891acaacd4fb5b80dab2ed824618203_393_0.png)

图 10.11 将广告和新闻输出索引合并到一个矩阵中。请注意，这两个矩阵互为补充。output_index_ads 中的值按新闻词汇表大小偏移。output_index_news 中的值转换回基于 0 的索引。

放置值，但可能涉及更复杂的索引操作。此特定示例说明在某些场景下，tf.gather 可以替代 tf.scatter_nd。

- 第 64-68 行重复相同的逻辑，但对象是新闻。请注意 output_index_ads 和 output_index_news 互为补充。图 10.11：output_index_ads 中的“空缺”/“空洞”可以由 output_index_news 在对应位置填充，反之亦然。

- 第 71-78 行试图将广告和新闻的两个输出索引矩阵合并为一个矩阵。但是，由于在这两个矩阵中新闻和广告的索引值都从 1 开始，如果我们直接将矩阵合并在一起，可能会在 output_index 矩阵中得到两个索引 1，从而混淆新闻和广告项。因此，我们按新闻的词汇表大小对广告索引进行偏移。我们还在最终的 output_index 矩阵中将索引转换回基于 0 的索引。这样一来，新闻索引值为 [0, 1, ..., <news_vocab_size - 1>]，广告索引值为 [<news_vocab_size>, <news_vocab_size + 1>, ..., <news_vocab_size + ads_vocab_size - 1>]。这就像我们使用合并的词汇表 vocab = concat([news_vocab, ads_vocab]) 进行索引一样。有关该转换的示例，请参见图 10.11。

- 第 80-84 行如果给出了两组的字符串词汇表，则应用 output_index 在合并词汇表中查找项名称。这将在最终输出中返回实际的项名称。

- 第 85-87 行改为返回索引，因为输入中缺少 news_vocab 或 ads_vocab。

我们可以使用以下示例测试我们的实现：

```python
news_scores = tf.constant([
    [0.7, 0.6, 0.5, 0.4, 0.3, 0.2, 0.1],
    [0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7],
    [0.1, 0.4, 0.2, 0.7, 0.6, 0.5, 0.3],
])
ads_scores = tf.constant([
    [0.5, 0.3, 0.1],
    [0.1, 0.4, 0.8],
    [0.2, 0.6, 0.4],
])
ads_positions = tf.ragged.constant([
    [2, 4], [3, 7], [0, 3, 6, 9]
])
dtype=tf.int64).to_sparse()
k = 8 # max number of contents to keep
news_vocab = tf.constant(["a", "b", "c", "d", "e", "f", "g"])
ads_vocab = tf.constant(["x", "y", "z"])
output, mask = arrange_ads_among_news(
    news_scores,
    ads_scores,
    ads_positions,
    news_vocab=news_vocab,
    ads_vocab=ads_vocab,
    k=k,
)
# output:
# <tf.Tensor: shape=(3, 8), dtype=string, numpy=
# array([[b'a', b'b', b'x', b'c', b'y', b'd', b'e', b'f'],
#        [b'g', b'f', b'e', b'z', b'd', b'c', b'b', b'y'],
#        [b'y', b'd', b'e', b'z', b'f', b'b', b'x', b'g']],
#       dtype=object)>
# mask:
# <tf.Tensor: shape=(3, 8), dtype=int64, numpy=
# array([[1, 1, 0, 1, 0, 1, 1, 1],
#        [1, 1, 1, 0, 1, 1, 1, 0],
#        [0, 1, 1, 0, 1, 1, 0, 1]])>
```

## 参考文献

Charles R. Harris, K. Jarrod Millman, Stéfan J. van der Walt, Ralf Gommers, Pauli Virtanen, David Cournapeau, Eric Wieser, Julian Taylor, Sebastian Berg, Nathaniel J. Smith, Robert Kern, Matti Picus, Stephan Hoyer, Marten H. van Kerkwijk, Matthew Brett, Allan Haldane, Jaime Fernández del Río, Mark Wiebe, Pearu Peterson, Pierre Gérard-Marchant, Kevin Sheppard, Tyler Reddy, Warren Weckesser, Hameer Abbasi, Christoph Gohlke, and Travis E. Oliphant.

Np.partition. https://numpy.org/doc/stable/reference/generated/numpy.partition.html, 2023.

Iris A. M. Huijben, Wouter Kool, Max B. Paulus, and Ruud J. G. van Sloun. 关于机器学习中离散随机性的 Gumbel-Max 技巧及其扩展的综述。IEEE 模式分析与机器智能汇刊，45(2):1353–1371，2022 年 3 月。

## 11

## 从零构建语言模型

在本书中，我们举例说明了如何从零构建深度学习模型（例如，第 6 章，案例研究：分解机；第 9 章案例研究：视觉变换器 (ViT)）。所提出的解决方案是该主题多年研究的成果。在本章中，让我们追踪使用变压器架构的语言建模演变，以说明机器学习模型，特别是像 LLaMA (Large Language Model Meta AI) 这样的大语言模型 (LLM) 是如何诞生的。到本章结束时，我希望读者能体会到机器学习研究所投入的大量努力。

### 11.1 基于变压器的语言建模

在变压器架构 [Vaswani et al., 2017] 引入之前，基于深度学习的自然语言建模一直依赖于先前引入的序列表示架构，如循环神经网络 (RNN) 和卷积神经网络 (CNN)。然而，这些架构有一个局限性：在从长文本/文档序列中学习时，它们倾向于只记住最近遇到的标记而忘记先前遇到的标记（例如，段落的开头）。深度学习研究人员使用称为**感受野**大小的指标来评估架构从输入信号中学习的能力，该概念借用自视觉神经科学。如果模型可以记忆并从长序列（在 1D 序列建模中）或大区域（在 2D/3D 计算机视觉问题中）中学习，则据说它具有大感受野。感受野有限会给语言翻译或问答等任务带来问题，在这些任务中，文本输入（即提示）可能非常长（例如，数百个单词）。试想一下，有人问了你一个极长的问题，但你只能记住说的最后几个词。如果你无法回忆起开头问了什么，你怎么能理解问题并因此给出回答呢？注意力机制，特别是我们在第 5 章中讨论的缩放点积自注意力，已被证明可以在原始变压器论文 [Vaswani et al., 2017] 中解决这个问题。通过对输入标记进行成对点积运算，模型在序列建模过程中学习关注要“注意”的内容（这里双关~）。变压器模型是在神经机器翻译的背景下引入的。然而，后来的研究表明，变压器模型在学习长序列数据方面尤其强大。已证明，变压器架构使研究人员不仅在自然语言处理 (NLP) 领域，而且在包括但不限于文本转语音（例如 FastSpeech2 [Ren et al., 2020]）、语音转文本（例如 Whisper [Radford et al., 2022]）、计算机视觉（例如我们在第 9 章中讨论的 ViT [Dosovitskiy et al., 2021] 模型）、药物发现（例如 SMILES [Honda et al., 2019; Grechishnikova, 2021]）和推荐引擎（例如 SASRec [Kang and McAuley, 2018]）等领域构建最先进的模型。

### 11.1.1 变压器架构的编码器和解码器

原始变压器使用编码器-解码器架构，其中编码器压缩输入，然后解码器解压缩隐藏状态以生成特定于翻译任务的输出。值得一提的是，最近的一项研究表明，变压器模型是表示学习的强大数据压缩器 [Yu et al., 2023]，其有趣的口号是“无处不在压缩”。最简单的编码器-解码器架构是自动编码器，我们在第 8 章中介绍过，其中编码器和解码器具有相同的架构（即一个全连接层）。变压器则使用注意力、层归一化和前馈层的组合来压缩和解压缩数据。编码器块和解码器块之间的关键区别在于：

- 编码器使用双向注意力。这意味着过去的标记可以用于预测未来的标记，而未来的标记也可以用于预测过去的标记。

- 解码器使用掩码或因果注意力。过去的标记可以用于预测未来的标记，但反之则不行。在第 5 章中，当我们讨论缩放点积注意力机制时，我们已经说明了这两种注意力机制。

- 针对原始变压器论文，解码器块还通过额外的注意力层接收来自编码器层隐藏状态的输入。因此，编码器层只有一个注意力层，而解码器层有两个注意力层。然而，在更近期的架构中

