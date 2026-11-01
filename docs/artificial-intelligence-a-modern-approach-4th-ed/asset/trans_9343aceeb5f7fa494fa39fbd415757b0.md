
# 引言

-   `Transformer` 模型使用 `self-attention` 并且可以建模长距离上下文以及局部上下文。它们可以有效利用硬件矩阵乘法。
-   包含预训练上下文词嵌入的 `Transfer learning` 使模型能够从非常大的未标注语料库中开发并应用于一系列任务。预训练用于预测缺失词的模型在针对目标域进行微调后可以处理其他任务，例如问答和文本蕴含。

## 参考文献和历史注记

自然语言中词语和短语的分布遵循 `Zipf’s Law` (Zipf, 1935, 1949)：第 `nth` 个最受欢迎词的频率大致与 `n` 成反比。这意味着我们存在数据稀疏问题：即使有数十亿词的训练数据，我们仍不断遇到之前未见过的新词和短语。

对新词和短语的泛化得益于能够捕捉基本洞见的表示，即含义相似的词出现在相似的上下文中。Deerwester et al.(1990) 通过分解由词语及其出现的文档构成的共现矩阵，将词语投影到低维向量中。另一种可能性是将周围的词语——比如一个 5 词窗口——视为上下文。Brown et al. (1992) 根据词的二元组上下文将词语分组为层次聚类；这已被证明对诸如命名实体识别等任务有效 (Turian et al., 2010)。`WORD2VEC` 系统 (Mikolov et al., 2013) 是首次显著展示通过训练神经网络获得的词嵌入优势的演示。`GloVe` 词嵌入向量 (Pennington et al., 2014) 是通过直接对从数十亿词文本中获得的词共现矩阵进行操作得到的。Levy and Goldberg (2014) 解释了这些词嵌入为何以及如何能够捕捉语言规律。

Bengio et al. (2003) 开创了神经网络在语言模型中的使用，提出将“(1) 每个词的分布式表示与 (2) 用这些表示表达的词序列概率函数”结合起来。Mikolov et al. (2010) 展示了使用 `RNNs` 在语言模型中建模局部上下文。Jozefowicz et al. (2016) 展示了训练于十亿词的 `RNN` 如何能胜过精心手工制作的 `n-gram` 模型。Peters et al. (2018) 强调了词语的上下文表示，他们称之为 `ELMO` (`Embeddings from Language Models`) 表示。

请注意，一些作者通过测量困惑度来比较语言模型。概率分布的困惑度为 `2H`，其中 `H` 是该分布的熵（参见 [第19.3.3节](#Chapter19-03.xhtml#sec19-3-3)）。在其他条件相同的情况下，困惑度更低的语言模型是更好的模型。但在实践中，其他条件很少相等。因此，衡量在真实任务上的性能比依赖困惑度更有信息量。

### 困惑度

Howard and Ruder (2018) 描述了 `ULMFIT` (`Universal Language Model Finetuning`) 框架，它使得在无需大量目标域文档语料的情况下微调预训练语言模型变得更容易。Ruder et al. (2019) 提供了关于 NLP 迁移学习的教程。

Mikolov et al. (2010) 提出了使用 `RNNs` 进行 NLP 的想法，而 Sutskever et al. (2015) 提出了使用深度网络进行序列到序列学习的想法。Zhu et al. (2017) 和 (Liu et al., 2018b) 表明无监督方法有效，并且使数据收集变得容易得多。很快发现这类模型在各种任务上表现惊人，例如图像描述 (Karpathy and Fei-Fei, 2015; Vinyals et al., 2017b)。

Devlin et al. (2018) 表明使用掩码语言建模目标预训练的 `Transformer` 模型可以直接用于多个任务。该模型被称为 `BERT` (`Bidirectional Encoder Representations from Transformers`)。预训练的 `BERT` 模型可以针对特定领域和特定任务进行微调，包括问答、命名实体识别、文本分类、情感分析以及自然语言推理。

`XLNET` 系统 (Yang et al., 2019) 通过消除预训练和微调之间的一致性差异改进了 `BERT`。`ERNIE 2.0` 框架 (Sun et al., 2019) 通过考虑句子顺序和命名实体的存在，而不仅仅是词语共现，从训练数据中提取更多信息，并被证明优于 `BERT` 和 `XLNET`。作为回应，研究人员重新审视并改进了 `BERT`：`ROBERTA` 系统 (Liu et al., 2019b) 使用了更多数据和不同的超参数及训练流程，并发现它可以与 `XLNET` 相媲美。`Reformer` 系统 (Kitaev et al., 2020) 将可考虑的上下文范围扩展到多达一百万词。与此同时，`ALBERT` (A Lite BERT) 则朝另一个方向发展，将参数数量从 108 百万减少到 12 百万（以便适配移动设备），同时保持高精度。

`XLM` 系统 (Lample and Conneau, 2019) 是一个使用多语言训练数据的 `Transformer` 模型。这对机器翻译有用，但也为单语任务提供了更稳健的表示。另两个重要系统 `GPT-2` (Radford et al., 2019) 和 `T5` (Raffel et al., 2019) 在本章中描述。后者论文还介绍了 35 亿词的巨型干净抓取语料库 (`C4`)。

已提出了各种有前景的预训练算法改进 (Yang et al., 2019; Liu et al., 2019b)。预训练上下文模型由 Peters et al. (2018) 和 Dai and Le (2016) 描述。

`GLUE` (`General Language Understanding Evaluation`) 基准测试，一套用于评估 NLP 系统的任务和工具集合，由 Wang et al. (2018a) 提出。任务包括问答、情感分析、文本蕴含、翻译和句法分析。`Transformer` 模型在排行榜上占据主导地位（人类基线远在第九位），以至于引入了新版本 `SUPERGLUE` (Wang et al., 2019)，其任务旨在对计算机更难，但对人类仍然容易。

在 2019 年底，`T5` 以 89.3 分成为整体领先者，仅比人类基线 89.8 低半分。在十项任务中的三项中，`T5` 实际上超过了人类表现：是/否问答（例如“Is France the same time zone as the UK?”）以及两项阅读理解任务，即在阅读段落或新闻文章后回答问题。

机器翻译是语言模型的主要应用。1933 年，Petr Troyanskii 获得了“翻译机”的专利，但当时没有计算机来实现他的想法。1947 年，Warren Weaver 借鉴密码学和信息论的工作，给 Norbert Wiener 写信说：“When I look at an article in Russian, I say: ‘This is really written in English, but it has been coded in strange symbols. I will now proceed to decode.”’ 社区随后尝试以这种方式解码，但他们没有足够的数据和计算资源使该方法实用。
