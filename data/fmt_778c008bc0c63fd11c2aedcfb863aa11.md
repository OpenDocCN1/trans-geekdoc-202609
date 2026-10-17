
It can be easily seen from Figure 15.4 that dominating or most important features like “Knowledge”, “Presentation”, and “Intelligent” having higher weights in comparison to the features “Young”, “Hair Style”, “Notes”, etc.

## 15.4 Result Analysis

We have processed feedback in two different domains. In the first domain, we have processed textual feedbacks of product, i.e., laptops, and in the second domain, we have processed feedbacks of professionals, i.e., teachers. Summary of results accomplished by different important modules/phases/steps are given in Table 15.4.

To measure the effectiveness of proposed system, we have compared features identified by our system with pre tagged features. In laptops’ feedback dataset, each sentence is labeled with appropriate aspect term and its sentiments while in teachers’ feedback, we have manually assigned related aspect term with each sentence. In our experiment, we have found that our system is performing better than baseline method [8]. To estimate system performance, we have divided feedbacks of teachers and laptops into training and test sets in the ratio of 3:1. System is trained by using statistical and linguistic knowledge extracted from the training set. Average accuracy, precision, and recall of our proposed system for teachers and laptops are shown in Figure 15.5.

**Table 15.4** Summary of results accomplished by different important modules/steps.

| **Module/phase/step** | **Processing remark** | **No. of words are treated as valid features in teachers feedbacks** | **No. of words are treated as valid features in laptops feedbacks** |
| --- | --- | --- | --- |
| **Data Collection** | Feedback collection from specified remote location. | No of Sentences: 7,342 Total words: 66,767 Unique words: 6,047 | No of Sentences: 3,048 Total words: 29,623 Unique words: 3,005 |
| **Feature Selector (Topic modeling)** | Number of topics has taken, i.e., K (20). | Words from each topic = 15 Total no of words = 15 × 20 = 300 | Words from each topic = 15 Total no of words = 15 × 20 = 300 |

# 16 Spark-增强深度神经网络框架用于医学短语嵌入

**Amol P. Bhopale**`\*` 和 **Ashish Tiwari**

*计算机科学与工程系，Visvesvaraya 国立工程学院，Nagpur，印度*

> **摘要**
>
> 信息检索（IR）技术的核心问题是查询词的有限集合，使用这些词时无法帮助检索到具有相似上下文词的文档。虽然词嵌入在自然语言处理（NLP）领域取得了巨大的进步，但它无法处理上下文相似的短语。本文提出了一种基于深度神经网络的嵌入式解决方案，它不仅考虑相似的上下文词，还能处理语义短语。为确保可扩展性，本文采用基于 `Spark` 的 `map-reduce` 框架，利用 NLP 技术提取短语并构建新的标注数据集。本文使用 `Word2Vec` 连续词袋（CBOW）模型在标注数据集上学习嵌入，并从中提取上下文相似的短语。鉴于医学领域的进步以及临床决策支持对有效信息检索技术的需求，本方法在 `TREC-2014 CDS` 轨道提供的数据集上进行评估。该数据集包含 733,125 篇 PubMed 文章，已在众多信息检索实验中使用。实验结果表明，有意义的短语及其上下文相似形式均可观察到，这些短语可进一步用于查询扩展任务。
>
> ***Keywords***: `Phrase embedding`, `information retrieval`, `medical concept`, `deep neural network`, `spark`

## 16.1 Introduction

在诸多 NLP 应用，如情感分析、网络检索和语言翻译中，短语被视为重要的语言单元。假设在相似上下文中出现的词通常含义相近 [1]。深度神经网络技术的进步使词向量表示能够在更具信息的上下文中呈现相似形式。与象征性语言表示相比，这些富含信息的嵌入式在各种 NLP 任务中提供了帮助 [2]。低维词嵌入的巨大成功也被广泛用于其他领域，如网络 [3] 和用户 [4] 嵌入。最初，嵌入仅为单词生成，近年来也扩展到短语。在信息检索（IR）任务中，短语嵌入通过将词的含义丰富为其上下文相似形式来发挥作用，具有许多科学和医学领域的应用，技术概念常以多词术语的形式出现。

本文的动机是进行医学短语嵌入，以应对互联网上日益庞大的关于患者、疾病和医疗报告的数字内容。实践者常因查询词数量少或仅使用缩写而难以检索决策支持文档。短语嵌入可以推断其包含的上下文属性，并捕捉非组成性语义。本文研究了在大规模数据集上训练短语嵌入模型的方法，并通过相似度得分实现基于相似短语的提取，以辅助查询扩展任务，提高检索文档的质量。

为实现可扩展性，本文采用 `Spark` `map-reduce` 框架，利用其多线程架构利用 CPU 处理海量数据。`map` 函数用于将数据集划分并生成短语，该过程通过在特殊字符和停用词处识别短语边界（即所谓的 chunking）来实现。`reduce` 函数收集高频短语并与显式标注的语料库一起，生成用于学习短语嵌入的标注数据集。为学习短语嵌入，本文将短语视为一个整体，并采用与文中 [5] 所述词嵌入技术相同的方式进行嵌入学习。本文的主要贡献如下：

*   提出一种无监督的短语生成技术，用于提取有意义的短语并在数据集中进行标注。
*   采用基于 `Spark` 的 `map-reduce` 框架高效处理大规模数据集，实现短语提取和语料库标注。
*   提出一种基于 `word2vec CBOW` 的短语嵌入模型，能够在同一向量空间中学习短语和词的嵌入。
*   在 `TREC-CDS 2014` 数据集上评估所提模型的有效性。

本文其余部分组织如下。在 Section 16.2 中讨论相关工作，随后在 Section 16.3 中介绍短语提取与嵌入技术。Section 16.4 描述实验设置，Section 16.5 展示结果并讨论 outcomes，Section 16.6 给出结论，最后列出参考文献。

## 16.2 Related Work

文档表示有着悠久的历史。在文献 [6] 中，作者提出了潜在语义分析（LSA）技术，将文档表示为低维词空间；通过奇异值分解将大规模词‑文档矩阵分解为一组正交因子。在潜在狄里克雷分配（LDA）中，term 依赖通过潜在变量来表示 [7]。这些技术的主要挑战在于它们仅考虑文档层面的词共现，来计算 term 之间的关联。

更近期，词嵌入被用作表示词在低维向量空间的一种解决方案，可能提升 term‑dependency 模型的表现。已有多种基于计数和基于预测的方法用于学习嵌入 [8]。在 [5] 中，作者利用神经语言模型最大化词与其上下文共现概率来学习词嵌入。

受词嵌入启发，分布式方法被提出用于短语嵌入 [9]，将短语视为一个整体。然而，短语对于捕捉词义在许多任务中至关重要。在 [10] 中，作者提出了特征丰富的组合转换（FCT）模型，该模型对每种短语类型使用词向量加权求和来构建短语表示。Zhao 等人 [11] 提出了一种组合模型，用于构建短语或句子意义，采用了向量‑张量‑向量乘法来学习短语表示。在 [12] 中，短语嵌入被用于从长篇科学论文中提取和排序关键词。在 [13] 中，作者提出了一种混合方法，通过线性组合分布式分量和组合分量，并加入个性化短语组合约束，学习短语嵌入表示。

## 16.3 Proposed Approach

短语嵌入是一个三阶段过程（如 Figure 16.1 所示）：第一阶段，从语料库中发现高频短语；第二阶段，在捕获的短语基础上对语料库进行标注；第三阶段，使用新标注的数据集在 `word2vec` 模型上进行训练。

### 16.3.1 Phrase Extraction

生成短语嵌入的第一步是从语料库中提取短语，即由一组词组成的集合。文献 [14] 提出“chunking”作为最具语言学重量的检测短语的方法。如 Figure 16.2 所示，第一步是根据特殊字符（如句号、分号、逗号）的出现将整个语料库划分为若干段落。停用词用于为每个候选短语设定边界。该过程产生大量候选短语，随后根据频率进行过滤。

```
The very first step in generating phrase embedding is to extract phrases which are made up of a group of words. In [14] has proposed “chunking” as one of the most linguistically heavy approach of detecting phrases. As shown in Figure 16.2, the first step is to split-up entire corpus into segments based on the occurrences of special characters such as a period, semicolon, and comma. Stop words are used to set the boundary for each candidate phrase. This process produces a large number of candidate phrases which are filtered out based on the frequency count.
```

本研究采用了内置的多线程基于 `Spark` 的轻量级方法，以确保可扩展性和效率。因此，使用 `PySpark` 包来在 Python 中获取 `Spark` 环境。如图 16.3 所示，多个 `map` 线程读取文本文档并应用基本 NLP 技术，如将文本转换为小写并将停用词视为边界，以生成候选短语。`Reduce` 函数收集所有满足最小频率计数的短语。

![Figure 16.1 The three-phase proposed approach.](img/fig16-1.jpg)

**Figure 16.1** The three-phase proposed approach.

![Figure 16.2 Phrase extraction sequence.](img/fig16-2.jpg)

**Figure 16.2** Phrase extraction sequence.

![Figure 16.3 Map-reduce framework.](img/fig16-3.jpg)

**Figure 16.3** Map-reduce framework.

### 16.3.2 语料标注

这是对语料中的短语进行高亮的过程。有两种标注语料的方式：第一种是对整个语料预先标注短语并构建新的标注语料；第二种是在神经网络中增加一层，在学习嵌入之前对文档进行标注。本文遵循第一种方式以简化流程，构建了新的标注语料。在语料中，每个短语出现的位置，子词之间的空格被下划线“_”字符替换，如图 16.4 所示。

### 16.3.3 短语嵌入

显式标记的短语语料用于学习短语嵌入并训练神经网络模型。采用 `Word2Vec CBOW`–基于训练模型进行向量化和建模预标注短语语料。`CBOW` 模型最初在 [5] 中提出，用于在向量空间中高效表示词。它是一个迭代模型，继承了在 [15] 中提出的神经网络语言模型。`CBOW` 模型预测给定上下文词窗口中缺失词的概率。它还有助于提取语义丰富的二元组集合。

`CBOW` 模型包含三个可辨识的层，即输入层、隐藏层和输出层，如图 16.5 所示。这是一个三阶段过程；在第一阶段，使用前向传播技术训练模型。输入层和输出层的节点数取决于词汇量，而隐藏层的节点数代表向量维度。训练神经网络时，将上下文词的 one-hot 向量输入输入层，使用前向传播技术计算隐藏层的神经元值。与传统的人工神经网络不同，隐藏层神经元的权重仅通过考虑输入参数与输入层每个神经元的权重之和的乘积来计算，不考虑激活函数。在输出层，使用隐藏层与输出层之间的加权向量矩阵计算各神经元的概率值。在输出层，对每个上下文向量得到的概率值相加，以预测目标词向量，如图 16.5 所示的 Equation (16.1)。

![Figure 16.4 Sample annotated document.](img/fig16-4.jpg)

**Figure 16.4** Sample annotated document.

![Figure 16.5 Single context CBOW model.](img/fig16-5.jpg)

**Figure 16.5** Single context CBOW model.

(16.1) ![image](img/eq16-1.png)

其中 *c* 为上下文窗口的大小，*w[t]* 为目标词，*V* 为词汇量。输出层的概率用软最大函数表示，如 Equation (16.2) 所示。

(16.2) ![image](img/eq16-2.png)

此处，*u[w]* 是 *w[t]* 的目标嵌入向量，*v[w]* 是上下文嵌入向量。向量 *u[w]* 是最终嵌入向量，保存为结果；而 *v[w]* 被视为副产物。

![Figure 16.6 Generalized CBOW model.](img/fig16-6.jpg)

**Figure 16.6** Generalized CBOW model.

在第二阶段，计算输出层之间的实际目标词向量值与累加值之间的误差。如果检测到误差，则在第三阶段进行传统的反向传播。训练模型的目标是最大化在给定输入上下文词 *w[c]* 的情况下观测到实际输出词 *w[t]* 的条件概率。因此，损失函数定义为 *max(p(w[t]|w[c]))*。该损失函数也可以被视为两个概率分布之间交叉熵测度的特殊情况。通过梯度下降优化算法更新神经元的权重。在 `CBOW` 模型中，输入到隐藏层以及隐藏层到输出层的权重矩阵本质上是词向量，它们在训练过程中被学习。该过程以迭代方式进行，直到所有神经元达到最优权重。这些层间的学习向量也称为嵌入。模型训练完成后，可根据上下文序列预测词汇。图 16.6 给出了带有 *C* 上下文的广义 `CBOW` 模型。

## 16.4 实验设置

本节简要讨论数据收集和预处理所遵循的流程。后半部分介绍进行实验所需的参数调优。

### 16.4.1 数据集准备

为评估拟议工作，使用了广为人知的信息检索数据集，即 `TREC-Clinical Decision Support` 数据集，包含 733,138 篇 PubMed 文章。文章采用 NXML 格式，因此解析以提取标题和摘要为文本文件格式。每篇文章通过应用 NLP 技术（如小写化、去除特殊字符）进行预处理，并将整个 Trec 语料合并为一条文档一行的单一文本文档。

### 16.4.2 参数设置

使用 `Spark` 框架对短语提取过程进行并行化，以确保可扩展性。通过使用 10 个 `map-reduce` 函数线程，将给定语料分区，并执行不同的 NLP 操作以生成短语并标注数据集。停用词用于标记短语边界，每个 `mapper` 函数根据边界将句子划分为短语，而 `reduce` 函数收集频率大于 50 的短语。本研究使用 Python `gensim` 库实现 `word2vec CBOW` 模型。它通过表示每个词或短语的 150 维向量来获取词汇表，然后设置上下文窗口大小为 10，并训练嵌入模型 10 个时代。Table 16.1 总结了参数详情及其值。

**Table 16.1** 参数详情及其值。

| **Parameter** | **Description** | **Value** |
| --- | --- | --- |
