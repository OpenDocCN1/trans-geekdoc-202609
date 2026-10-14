
在我们计算主题分布后，我们需要查看每个主题中的评论类型。让我们先看主题大小的分布情况。

`Listing 3.5` 中的命令将输出主题大小的摘要表格。请注意，主题的大小是包含该主题的评论数量。表格在 `Fig. 3.6` 中显示。

![Figure 3.6 Table showing sizes and names of largest and smallest topics.](images/fig3_6.jpg)

[Figure 3.6](#ch3.xhtml#b3fig3_6) Table showing sizes and names of largest and smallest topics.

请注意，主题 ID 为 -1 的情况。这对应于 HDBSCAN 算法输出的未分配聚类。未分配聚类包含所有未能分配到其他聚类的事物。它通常可以被忽略，*但如果它过大，则说明我们选择的参数可能不适合我们的数据。* 可以查看未分配聚类的内容来验证其是否包含不相关的词汇。

#### 3.5.3.3 主题可视化

![Listing 3.6 Visualizing the 10 largest topics](images/comp3_6.jpg)

[Listing 3.6](#ch3.xhtml#b3list3_6) Visualizing the 10 largest topics

![Figure 3.7 The 10 largest topics.](images/fig3_7.jpg)

[Figure 3.7](#ch3.xhtml#b3fig3_7) The 10 largest topics.

![Listing 3.7 Visualizing the cosine similarity of the 20 largest topics](images/comp3_7.jpg)

[Listing 3.7](#ch3.xhtml#b3list3_7) Visualizing the cosine similarity of the 20 largest topics

BERTopic 还可以使用 *v**i**s**u**a**l**i**z**e**[*h*]*e**a**t**m**a**p* 方法显示主题嵌入向量的余弦相似热图，如 [Listing. 3.7](#ch3.xhtml#list3_7) 所示。热图在 [Fig. 3.8](#ch3.xhtml#fig3_8) 中显示，并展示了每对主题的嵌入向量之间重叠程度。

![Figure 3.8 Heatmap of the cosine similarity of the 20 largest topics.](images/fig3_8.jpg)

[Figure 3.8](#ch3.xhtml#b3fig3_8) Heatmap of the cosine similarity of the 20 largest topics.

#### 3.5.3.4 主题内容

![Listing 3.8 Print the topic size and representative words](images/comp3_8.jpg)

[Listing 3.8](#ch3.xhtml#b3list3_8) Print the topic size and representative words

现在我们来看一个主题的示例。我们在 [Fig. 3.7](#ch3.xhtml#fig3_7) 中查看了最大的 10 个主题，因此这里我们将查看最大和最小主题、中位数主题以及未分配聚类的内容。[Listing 3.8](#ch3.xhtml#list3_8) 展示了一个简单的辅助函数，用于打印主题的大小以及与该主题最相关的 10 个词汇。

![](images/comp3_9.jpg)![Listing 3.9 Unassigned cluster](images/comp3_9a.jpg)

[Listing 3.9](#ch3.xhtml#b3list3_9) Unassigned cluster

首先，我们查看未分配聚类（主题 ID 为 -1），以验证我们可以安全忽略其内容。它在 [Listing 3.9](#ch3.xhtml#list3_9) 中。

如我们所见，未分配聚类的内容包含不强烈属于任何主题的词汇。最大、最小和中位数主题分别在 [Listings 3.10](#ch3.xhtml#list3_10)、[3.11](#ch3.xhtml#list3_11) 和 [3.12](#ch3.xhtml#list3_12) 中显示。

![](images/comp3_10.jpg)![Listing 3.10 Largest topic: Italian food restaurants](images/comp3_10a.jpg)

[Listing 3.10](#ch3.xhtml#b3list3_10) Largest topic: Italian food restaurants

![Listing 3.11 Smallest topic: the ambiance and arrangement of stores](images/comp3_11.jpg)

[Listing 3.11](#ch3.xhtml#b3list3_11) Smallest topic: the ambiance and arrangement of stores

![](images/comp3_12.jpg)![](images/comp3_12a.jpg)![Listing 3.12 Median topic: Nightlife in Charlotte, NC](images/comp3_12b.jpg)

[Listing 3.12](#ch3.xhtml#b3list3_12) Median topic: Nightlife in Charlotte, NC

## 3.6 案例研究：微调 Bert

### 3.6.1 目标

本案例研究的目标是提供微调标准 BERT 模型的逐步演示，用于任何句子分类任务，我们选择情感分类作为样本流行任务。

### 3.6.2 数据、工具和库

我们选择 Google Play 应用评论数据集。该数据集包含 15,746 条样本，分为三类：负面、中性和正面。我们使用 Huggingface 转换器库进行微调任务，并使用标准的 Python 数据科学栈进行其他数据处理和可视化 \[[249](#refbib.xhtml#refbib_249)\] ([Fig. 3.9](#ch3.xhtml#fig3_9), [Fig. 10](#ch3.xhtml#fig3_10), [Fig. 3.11](#ch3.xhtml#fig3_11))。

![Figure 3.9 Exploratory data analysis of the sentiment classification dataset.](images/fig3_9.jpg)

[Figure 3.9](#ch3.xhtml#b3fig3_9) Exploratory data analysis of the sentiment classification dataset.

![Figure 3.10 Training and validation loss throughout training.](images/fig3_10.jpg)

[Figure 3.10](#ch3.xhtml#b3fig3_10) Training and validation loss throughout training.

![Figure 3.11 Confusion matrix of test set.](images/fig3_11.jpg)

[Figure 3.11](#ch3.xhtml#b3fig3_11) Confusion matrix of test set.

我们使用 BERT[BASE] 作为起始预训练 BERT 模型。Listing 3.6.3 展示了如何从转换器库加载预训练的 BERT 模型，并说明了用于微调 BERT 模型的分词输出 \[[249](#refbib.xhtml#refbib_249)\]。

### 3.6.3 实验、结果和分析

![](images/comp3_13.jpg)![](images/comp3_13a.jpg)

Listing 3.6.3 提供了将我们的数据集加载并分为训练、验证和测试的工具，同时创建每个数据分割的数据加载器，供微调迭代使用 \[[249](#refbib.xhtml#refbib_249)\]。

![](images/comp3_14.jpg)![](images/comp3_14a.jpg)

Listing 3.6.3 创建微调模型并设置相关损失、优化器和学习率调度的参数 \[[249](#refbib.xhtml#refbib_249)\]。

![](images/comp3_15.jpg)![](images/comp3_15a.jpg)![](images/comp3_16.jpg)![](images/comp3_16a.jpg)![](images/comp3_17.jpg)![](images/comp3_18.jpg)![](images/comp3_18a.jpg)

# CHAPTER 4Multilingual Transformer Architectures

DOI: [10.1201/9781003170082-4](https://doi.org/10.1201/9781003170082-4)

THE introduction of BERT \[[72](#refbib.xhtml#refbib_72)\] has transformed the area of Natural Language Processing (NLP) and resulted in state-of-the-art performance on a broad range of tasks. In the recent past, training NLP algorithms worked only with labeled data, which hindered their progress for years due to the limited availability and cost of collecting data for every new task and every new project. One major contribution of BERT is introducing a new pipeline for training NLP systems where algorithms can learn about core and generic natural language concepts from huge amount of cheap unlabeled data, a process also known as self-supervised learning or model pre-training. A pre-trained model is then fine-tuned for any specific downstream task using much smaller task-specific labeled datasets. This new pipeline of pre-training followed by fine-tuning constitutes the core of most advances in the machine learning field. The major success of BERT for English NLP tasks has motivated its use for other languages. However, using BERT's pipeline is only possible for languages with sufficiently large unlabeled data for pre-training. This motivated the development of multilingual models where models are pre-trained on multiple languages with the hope that the models will transfer core NLP knowledge from high-resource languages to low-resource ones and we end up with a polyglot model that aligns multilingual representations across languages.
