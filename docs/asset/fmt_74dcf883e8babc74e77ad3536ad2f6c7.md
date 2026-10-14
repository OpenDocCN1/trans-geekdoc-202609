
请注意，主题 ID 为 `-1` 的情况。这对应于 HDBSCAN 算法输出的未分配聚类。未分配聚类包含所有未能分配到其他聚类的事物。它通常可以被忽略，但如果它过大，则说明我们选择的参数可能不适合我们的数据。可以查看未分配聚类的内容来验证其是否包含不相关的词汇。

#### 3.5.3.3 主题可视化

![Listing 3.6 Visualizing the 10 largest topics](img/comp3_6.jpg)

Listing 3.6 Visualizing the 10 largest topics

![Figure 3.7 The 10 largest topics.](img/fig3_7.jpg)

Figure 3.7 The 10 largest topics.

![Listing 3.7 Visualizing the cosine similarity of the 20 largest topics](img/comp3_7.jpg)

Listing 3.7 Visualizing the cosine similarity of the 20 largest topics

BERTopic 还可以使用 `visualize_heatmap` 方法显示主题嵌入向量的余弦相似热图，如 Listing 3.7 所示。热图在 Fig. 3.8 中显示，并展示了每对主题的嵌入向量之间重叠程度。

![Figure 3.8 Heatmap of the cosine similarity of the 20 largest topics.](img/fig3_8.jpg)

Figure 3.8 Heatmap of the cosine similarity of the 20 largest topics.

#### 3.5.3.4 主题内容

![Listing 3.8 Print the topic size and representative words](img/comp3_8.jpg)

Listing 3.8 Print the topic size and representative words

现在我们来看一个主题的示例。我们在 Fig. 3.7 中查看了最大的 10 个主题，因此这里我们将查看最大和最小主题、中位数主题以及未分配聚类的内容。Listing 3.8 展示了一个简单的辅助函数，用于打印主题的大小以及与该主题最相关的 10 个词汇。

![](img/comp3_9.jpg)

![Listing 3.9 Unassigned cluster](img/comp3_9a.jpg)

Listing 3.9 Unassigned cluster

首先，我们查看未分配聚类（主题 ID 为 `-1`），以验证我们可以安全忽略其内容。它在 Listing 3.9 中。

如我们所见，未分配聚类的内容包含不强烈属于任何主题的词汇。最大、最小和中位数主题分别在 Listings 3.10、3.11 和 3.12 中显示。

![](img/comp3_10.jpg)

![Listing 3.10 Largest topic: Italian food restaurants](img/comp3_10a.jpg)

Listing 3.10 Largest topic: Italian food restaurants

![Listing 3.11 Smallest topic: the ambiance and arrangement of stores](img/comp3_11.jpg)

Listing 3.11 Smallest topic: the ambiance and arrangement of stores

![](img/comp3_12.jpg)

![](img/comp3_12a.jpg)

![Listing 3.12 Median topic: Nightlife in Charlotte, NC](img/comp3_12b.jpg)

Listing 3.12 Median topic: Nightlife in Charlotte, NC

## 3.6 案例研究：微调 Bert

### 3.6.1 目标

本案例研究的目标是提供微调标准 BERT 模型的逐步演示，用于任何句子分类任务，我们选择情感分类作为样本流行任务。

### 3.6.2 数据、工具和库

我们选择 Google Play 应用评论数据集。该数据集包含 15,746 条样本，分为三类：负面、中性和正面。我们使用 Huggingface 转换器库进行微调任务，并使用标准的 Python 数据科学栈进行其他数据处理和可视化 \[249\] (Fig. 3.9, Fig. 10, Fig. 3.11)。

![Figure 3.9 Exploratory data analysis of the sentiment classification dataset.](img/fig3_9.jpg)

Figure 3.9 Exploratory data analysis of the sentiment classification dataset.

![Figure 3.10 Training and validation loss throughout training.](img/fig3_10.jpg)

Figure 3.10 Training and validation loss throughout training.

![Figure 3.11 Confusion matrix of test set.](img/fig3_11.jpg)

Figure 3.11 Confusion matrix of test set.

我们使用 `BERT[BASE]` 作为起始预训练 BERT 模型。Listing 3.6.3 展示了如何从转换器库加载预训练的 BERT 模型，并说明了用于微调 BERT 模型的分词输出 \[249\]。

### 3.6.3 实验、结果和分析

![](img/comp3_13.jpg)

![](img/comp3_13a.jpg)

Listing 3.6.3 提供了将我们的数据集加载并分为训练、验证和测试的工具，同时创建每个数据分割的数据加载器，供微调迭代使用 \[249\]。

![](img/comp3_14.jpg)

![](img/comp3_14a.jpg)

Listing 3.6.3 创建微调模型并设置相关损失、优化器和学习率调度的参数 \[249\]。

![](img/comp3_15.jpg)

![](img/comp3_15a.jpg)

![](img/comp3_16.jpg)

![](img/comp3_16a.jpg)

![](img/comp3_17.jpg)

![](img/comp3_18.jpg)

![](img/comp3_18a.jpg)

# CHAPTER 4 Multilingual Transformer Architectures

DOI: [10.1201/9781003170082-4](https://doi.org/10.1201/9781003170082-4)

THE introduction of BERT \[72\] has transformed the area of Natural Language Processing (NLP) and resulted in state-of-the-art performance on a broad range of tasks. In the recent past, training NLP algorithms worked only with labeled data, which hindered their progress for years due to the limited availability and cost of collecting data for every new task and every new project. One major contribution of BERT is introducing a new pipeline for training NLP systems where algorithms can learn about core and generic natural language concepts from huge amount of cheap unlabeled data, a process also known as self-supervised learning or model pre-training. A pre-trained model is then fine-tuned for any specific downstream task using much smaller task-specific labeled datasets. This new pipeline of pre-training followed by fine-tuning constitutes the core of most advances in the machine learning field. The major success of BERT for English NLP tasks has motivated its use for other languages. However, using BERT's pipeline is only possible for languages with sufficiently large unlabeled data for pre-training. This motivated the development of multilingual models where models are pre-trained on multiple languages with the hope that the models will transfer core NLP knowledge from high-resource languages to low-resource ones and we end up with a polyglot model that aligns multilingual representations across languages.

本章涵盖了多语言 Transformer 架构的最新发展。多语言 Transformer 架构完全由以下几项定义：

- 模型架构（层和组件）
- 预训练任务
- 预训练数据
- 微调任务和基准

本章首先介绍不同的多语言 Transformer 架构用于自然语言理解（NLU）和自然语言生成（NLG）。第 4.2 节接着描述多语言数据的最新状态，包括用于下游 NLP 任务的无标签预训练数据和微调基准。第 4.3 节提供对多语言 Transformer 模型内部工作机制的一些见解。最后，第 4.4 节提供一个零射多语言情感分类的实践案例研究。

## 4.1 多语言 Transformer 架构

本节讨论多语言 Transformer 的不同结构设计。我们将多语言 Transformer 划分为 (i) 自然语言理解（NLU）架构和 (ii) 自然语言生成（NLG）架构。表 4.1\[74\] 提供了本书出版时可用的具有影响力的多语言 Transformer 模型的摘要。

TABLE 4.1 多语言语言模型摘要 \[74\]

| 模型 | #参数 | 目标函数 | 预训练单语 | 预训练平行 | #语言 | Ref. |
| --- | --- | --- | --- | --- | --- | --- |
| IndicBERT | 33M | MLM | IndicCorp | ✗ | 12 | \[137\] |
| mBERT | 172M | MLM | [Wikipedia](http://Wikipedia) | ✗ | 104 | \[72\] |
| Amber | 172M | MLM, TLM, CLWA, CLSA | [Wikipedia](http://Wikipedia) | ✓ | 104 | \[121\] |
| MuRIL | 236M | MLM, TLM | CommonCrawl + [Wikipedia](http://Wikipedia) | ✓ | 17 | \[141\] |
| VECO-small | 247M | MLM, CS-MLM | CommonCrawl | ✓ | 50 | \[175\] |
| Unicoder | 250M | MLM, TLM, CLWR, CLPC, CLMLM | [Wikipedia](http://Wikipedia) | ✓ | 15 | \[125\] |
| XLM-15 | 250M | MLM, TLM | [Wikipedia](http://Wikipedia) | ✓ | 15 | \[63\] |
| InfoXLM-base | 270M | MLM, TLM, XLCO | CommonCrawl | ✓ | 94 | \[48\] |
| XLM-R-base | 270M | MLM | CommonCrawl | ✗ | 100 | \[61\] |
| HiCTL-base | 270M | MLM, TLM, HICTL | CommonCrawl | ✓ | 100 | \[266\] |
| Ernie-M-base | 270M | MLM, TLM, CAMLM, BTMLM | CommonCrawl | ✓ | 100 | \[194\] |
| HiCTL-Large | 559M | MLM, TLM, HICTL | CommonCrawl | ✓ | 100 | \[266\] |
| Ernie-M-Large | 559M | MLM, TLM, CAMLM, BTMLM | CommonCrawl | ✓ | 100 | \[194\] |
| InfoXLM-Large | 559M | MLM, TLM, XLCO | CommonCrawl | ✓ | 94 | \[48\] |
| XLM-R-Large | 559M | MLM | CommonCrawl | ✗ | 100 | \[61\] |
| RemBERT | 559M | MLM | CommonCrawl + [Wikipedia](http://Wikipedia) | ✗ | 110 | \[54\] |
| X-STILTS | 559M | MLM | CommonCrawl | ✗ | 100 | \[198\] |
| XLM-17 | 570M | MLM, TLM | [Wikipedia](http://Wikipedia) | ✓ | 17 | \[63\] |
| XLM-100 | 570M | MLM, TLM | [Wikipedia](http://Wikipedia) | ✗ | 100 | \[63\] |
| VECO-Large | 662M | MLM, CS-MLM | CommonCrawl | ✓ | 50 | \[175\] |

### 4.1.1 基础多语言 Transformer

多语言 Transformer 模型通常基于 mBERT 架构 \[72\]。本节描述多语言 Transformer 架构的基本组件。

**输入层** 输入是一系列 token，它们来自有限词汇表的一对一热表示，通常是子词库。该词汇表一般通过拼接多个语言的单语数据，使用诸如 BPE \[223\]、WordPiece \[273\] 或 SentencePiece \[144\] 等算法学习。为确保不同语言和脚本在词汇表中得到良好表示，可采用指数加权抽样，或为语言簇学习独立的词汇表，从而分割词汇表大小 \[55\]。

**Transformer 层** 多语言语言模型（mLM）通常构成 Transformer 的编码器。它由 `N` 层组成，每层包含 `k` 个注意力头，随后是前馈神经网络。注意力头通过对输入序列中所有其他 token 的表示，使用加权线性组合计算每个 token 的嵌入。将所有注意力头的嵌入拼接后，再经过前馈网络，得到每个输入词的 `d` 维嵌入。

**输出层** 通常，最终 Transformer 层的输出被用作每个 token 的上下文表示，而 `[CLS]` token 对应的嵌入被视为整个输入文本的嵌入。也可以通过对 token 嵌入进行池化来生成文本嵌入。输出层包含一次线性变换，随后是 Softmax，它以前一层的 token 嵌入为输入，并产生词汇表中 token 的概率分布。

$$\\begin{array}{l} {\\mathcal{L}\_{MLM}^{(x)} = - \\frac{1}{|M\_{x}|}{\\sum\\limits\_{i \\in M\_{x}}}l}ogP(x\_{i}|x\\_{\\smallsetminus M\_{x}})} \\\\ \\end{array}$$  

(4.1)

Fig. 4.1 图 4.1 展示了 MLM 任务，其中 `x` 和 `y` 代表不同语言中的单语输入句子。尽管该任务不考虑汇聚的掩码输入的多语言信息，但它已展示出在生成跨语言表示方面的巨大价值，这些表示在不同语言之间高度对齐。下文的“洞察”部分将提供更多细节，说明导致这种行为的因素。
