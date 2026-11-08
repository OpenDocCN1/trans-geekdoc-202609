
虽然 `Seq2Seq` 模型的编码器-解码器方法很直观，并且是向前迈出的一大步，但该方法的缺点是单个固定长度的表示必须代表整个句子的所有信息，并且随着句子长度的增加，这种情况预计会变得越来越困难（这一事实在实证研究中得到了证实）。`RNNsearch` 模型通过允许其解码器回看输入文档并决定在生成翻译中的下一个词元时应最关注哪些词，从而改进了 `Seq2Seq`。这个 `attention mechanism` 为输入句子中的每个词生成权重，这些权重通过一个 `softmax` 神经元求和为一。解码器在预测位置 `i` 处翻译中的下一个词元时用作其输入的上下文向量 `c[i]`<mml:math><mml:msub><mml:mrow><mml:mi>c</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F000121si86.png) 只是编码器产生的输入中每个词元 `j` 的隐藏状态（即嵌入 `h[j]`<mml:math><mml:msub><mml:mrow><mml:mi>h</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F000121si88.png)）的平均值，按其注意力权重 `α[ij]`<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="normal">&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">ij</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F000121si90.png) 加权：

`c[i] = ∑[j] α[ij] h[j]`.<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="italic">c</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">i</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:msub><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi mathvariant="italic">j</mml:mi></mml:mrow></mml:msub><mml:mrow><mml:msub><mml:mrow><mml:mi mathvariant="normal">&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">ij</mml:mi></mml:mrow></mml:msub></mml:mrow><mml:msub><mml:mrow><mml:mi mathvariant="italic">h</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">j</mml:mi></mml:mrow></mml:msub><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000121si91.png)

这里，注意力权重 `α[ij]`<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="normal">&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">ij</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F000121si92.png) 旨在表示输入中第 `j`<mml:math><mml:mi>j</mml:mi></mml:math>![Equation](images/F000121si93.png) 个词对应于（或至少能提供信息给）译出输出中第 `i`<mml:math><mml:mi>i</mml:mi></mml:math>![Equation](images/F000121si94.png) 个词的概率。更一般地，`attention weights` 是学习得到的权重，通过类比于认知过程中的注意力，人类决定关注显著的事物，同时忽略与当前情况无关的事物来为输入的各部分赋予重要性（[图 11.7](#Ch012_433-471_B9780443158889000121.xhtml#f0040)）。在 `NLP` 中，`attention weights` 通常应用于输入中的词元，其中词元可以是词，或在子词级别，如音节。

![图 11.7 RNNsearch 使用的简单注意力机制。鸣谢：James Foulds](images/F000121f11-07-9780443158889.jpg)

[图 11.7](#Ch012_433-471_B9780443158889000121.xhtml#Bf0040) `RNNsearch` 使用的简单注意力机制。鸣谢：James Foulds

## 11.3 Transformer 架构

我们迄今为止讨论的 `NMT` 模型使用诸如 `LSTMs` 之类的循环神经网络。这些模型按顺序处理数据，这是一个主要的计算瓶颈。在 `RNN` 模型中，序列必须一次处理一个词元，这会根据序列长度减慢处理速度，并且这种处理无法通过 `GPU` 或 `TPU` 轻松并行化。卷积神经网络是另一种选择，这些模型可以并行化。然而，`CNNs` 不能直接建模长程依赖关系，而这对许多 `NLP` 应用（包括 `NMT`）很重要。

为了解决这种情况，Google 的研究人员提出了 `transformer`，一种旨在仅使用注意力来避免 `RNNs` 和卷积的架构。这比 `RNNs` 实现了更多的并行化，同时仍能捕捉长程依赖关系。虽然他们的所述目标是加快 `LLMs` 的训练，但 `transformer` 方法也带来了 `NLP` 性能的显著提升。尽管这种改进中的很大一部分可能归因于并行化所能实现的大规模训练，但架构的其他优势可能也起作用，包括 `transformer` 模型能够一次考虑整个句子（或更多），以及注意力在引导模型关注文本显著部分方面的有效性。其应用已超越 `NMT`，成为 `LLMs` 的最先进技术及其在大多数 `NLP` 任务中的应用，以及扩展到计算机视觉等其他领域。我们现在将讨论基于 `transformer` 的语言模型的组件。

### 缩放点积注意力

正如我们之前讨论的，注意力是一种神经网络技术，用于确定应关注数据的哪个部分。`transformer` 模型使用一种专门的注意力版本，称为 `scaled dot-product attention`。我们将使用信息检索隐喻来看待注意力，其中我们可能关注的感兴趣的 `items`（例如句子中的其他词）类似于我们正在搜索的网页，而决定当前重要的信息（例如当前词）类似于搜索查询。`items` 假定具有向量嵌入，称为 `key`，它决定其与“`query`”的相关性，后者也具有嵌入。某个项目的 `key` 不必与其 `value` 相同，后者是我们将用于在它确实显著时向前表示它的向量嵌入。然后，注意力可以被理解为试图通过根据 `key` 和 `query` 之间的相似性分配相关性分数（又名 `attention weights`）来“检索”其 `key` 与 `query` 相关的 `items` 的 `values`。
