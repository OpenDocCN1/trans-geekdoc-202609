
其中，$\alpha^o(\cdot)$ 是激活函数，$b^{aw}$ 是输入层的偏置。因此，隐藏单元与输出层之间的权重链接由 $y_n$ 表示。上述公式适用于 1 和 $t$ 之间的所有值。在每一步，输入向量都由隐藏层用于预测输出层的最终结果。当 CNN 处于隐藏状态时，它收集了之前状态特定数据。输出层的准确分类由合并数据提供。

## 结果与讨论

本节解释了如何评估所提出的深度 CNN 技术。评估所提出的基于 Hadoop 的深度 CNN 技术的一种方法是将其与更多方法比较。

## 测试环境

所提出的基于 Hadoop 的深度 CNN 在 `PYTHON` 中实现，运行在 `Windows` 上。为了评估所提出的基于 Hadoop 的深度 CNN 技术，我们使用来自 Twitter Sentiment 数据集。

## 性能指标

分类精度、特异性和敏感性是评估所提出的基于 Hadoop 的深度 CNN 方法的少数标准。将所提出的基于 Hadoop 的深度 CNN 与 `SVM`、`NB` 和 `PSO` 等传统方法进行比较。性能指标如分类精度、特异性和敏感性用于评估所提出的基于 Hadoop 的深度 CNN 方法。

![](img/5e4d8ef2afa52a8404b28106580e19e4_470.png)

**图 (2)** 情感分类准确率 vs Mapper 数量

在图 (2) 中，我们看到不同训练百分比的分类准确率。$N=5$ Mapper 的分类分析在图 (2a) 中所示。`SVM`、`NB` 和所提出的基于 Hadoop 的深度 CNN 方法实现的分类准确率分别为 0.9086、0.9112、0.9206 和 0.9300，训练百分比为 90%。Mapper 数量为 6 的分类准确率在图 (2b) 中所示。`SVM`、`NB` 和所提出的基于 Hadoop 的深度 CNN 方法实现的分类准确率分别为 0.9063、0.9100、0.9232 和 0.9300，训练百分比为 90%。

![](img/5e4d8ef2afa52a8404b28106580e19e4_471.png)

分类精度、特异性和敏感性是评估所提出的基于 Hadoop 的深度 CNN 方法的少数标准。将所提出的基于 Hadoop 的深度 CNN 与 `SVM`、`NB` 和 `PSO` 等传统方法进行比较。

# Bert 与 Word2vec 在文本情感分析方法上的对比

Manish Nagpal¹, *
Chitkara 工程科学与技术大学， 与与技术跨学科研究中心，Chitkara 大学，旁遮普邦，印度

* **通讯作者 Manish Nagpal:** manish.nagpal.orp@chitkara.edu.in

## 摘要

本研究提出了一种创建数据集的新方法，用于训练能够分析社交媒体帖子语调的神经网络。论文详细阐述了如何在神经网络中使用 `word2vec` 和 `BERT` 算法来分析社交媒体消息并评估其情感基调。该算法使用了余弦相似度以及基于微调后的词频-文档频率（`TF-IDF`）特征的本体论映射的混合方法进行语义搜索。执行过程包括情感分析、短语提取过程、文本信念指示、基于关键词的搜索以及文本总结等。通过实验证明了所提方法的有效性。还测试了在创建情感分析训练集时，文本的词干提取（`stemming`）和词形还原（`lemmatization`）的效率。

**关键词：** Bert 模型，文本情感分析，训练推文，测试推文，词向量。

# 引言

文本的词向量表示通常通过 `WordVec`、`GloVe` 等工具获得 [1]。这些方法会丢失词的语境。情感分析是一项高度应用化的技术，有助于解决在线讨论线程无组织以及需要精确定位用户数据等问题 [2, 3]。尽管情感分析领域已取得一些进展，但仍有许多值得学习的地方。一个紧迫的问题是不同的文本特征表示方法和选择机制如何影响分类性能 [4, 5]。迷包（`Memes`）是在线内容领域的一种新现象。迷包包含了对某个主题、物品、人物或事物的感受 [6]。迷包可以以文本、图片或两者的结合形式存在。迷包可能是讽刺的、批判的、幽默的，甚至是政治色彩的 [7]。现有研究大多侧重于文本。互联网的普及使得通过各种在线论坛分享广泛主题的观点成为可能。对于企业和数据科学家来说，检查这些评论中包含的信息至关重要 [8]。数据分析的方法数之多数。近年来，使用语言模型进行情感分析和文本分类的研究工作也有增加。本研究使用来自常用电子商务网站 `Zappos` 和 `Yelp` 的用户评论，将两种文本分类方法——支持向量机（`SVM`）和神经网络（`NN`）——与四种文本嵌入方法——`word2vec`、`Glove`、`BERT` 以及 `GPT-2` 的结果进行了对比 [9, 10]。

本研究以 `Twitter` 为案例研究，旨在对社交网络信息进行情感分析和观点识别。确定一条推文的语调是中性的、良好的还是负面的的一种方法是使用情感分析。发现特定推文是否包含对产品创作的有用观点是态度检测的目标。我们的主要目标是通过比较 `Word2Vec` 和 `BERT` 嵌入词的情感评估和观点识别来实现的。为了确定哪种方法在海量数据下工作效果更好，本研究还比较了标准机器学习与深度学习。因此，研究目标如下：

- `Word2Vec` 和 `BERT` 都能产生词嵌入，比较它们在情感评估和观点识别方面的性能。
- 评估深度学习和传统机器学习方法处理中等规模数据集的效果。
- 利用应用情感评估和观点识别的结果为产品推荐提供信息。

# 相关工作

本研究建议了一种用于文本情感分析的神经网络框架来解决这一问题。它结合了预训练的语言模型、双向短期记忆网络以及注意力机制。这一概念被称为 Transformer 的双向编码表示。首先，使用 `BERT` 预训练获取包含语境语义信息的词向量。本文使用双向长短期记忆网络来提取与语境相关的特征。开发了注意力机制以进行文本情感分类、突出关键点并对检索到的信息加权。在 `SST`（斯坦福情感树库库）测试集上，准确率可达 89.17%，表明比以前的方法准确性有所提高 [11]。

在研究中，我们使用 `TF-IDF` 根据词在文本中的出现频率对其进行排名，从而确定其相对重要性。为了进一步研究文本的情感负载，我们使用了带核的 `SVM` 和 `ELM`。实验结果表明，带核的 `ELM` 比 `SVM` 能更快地提供准确的分类 [12]。

本研究使用基于文本和基于图片的印尼语迷包来检查四种情感评估方法的有效性。首先检索文本迷包，然后利用决策树、卷积神经网络（`CNN`）、朴素贝叶斯和支持向量机等监督机器学习技术进行分类。根据结果显示，在分析迷包内容的情感时，朴素贝叶斯方法达到了最高精度（在本例中为 65.4%）[13]。

与目前的其他方法相比，所建议的基于 Hadoop 的深度 CNN 方法更更为优异。未来可以通过引入额外特征来改进特征提取过程。

## 参考文献

- [1] Skuza M., Romanowski A. Sentiment analysis of Twitter data within big data distributed environment for sentiment prediction. 2015 Federated Conference on Computer Science and Information Systems (FedCSIS)1394135420150150.15439/2015F230
- [2] Romanowski A., Skuza M., Towards Predicting Stock Price Moves with Aid of Sentiment Analysis on Twitter Social Network Data and Big Data Processing Environment.. 2017.,10.1007/978-3-319-47208-9
- [3] Amrutphale Y., Vijayrajya N., Malviya A. A Novel Adaptive Approach for Sentiment Analysis on Social Data 2020..10.1007/978-981-15-2071.6-60
- [4] Yadav S.P., Saidi Z., Nacimento C.D., de Albuquerque V.H., Chauhan S. Analysis and Design of automatically generating for GPS Based Moving Object Tracking 2023 International Conference on Artificial Intelligence and Smart Communication (AISc) Greater Noida, India 2023 15.1109/AISC5626.202310851
- [5] Rane I., Twespa: A modern approach to Twitter sentiment analysis. Int. J. Res. Appl. Sci. Eng. Technol.20202852
- [6] Mohan L., Elaydom S. A Novel approach to build Collective User Analysis for Twitter. Int. J. Web.... 201799112
- [7] Samariya D., Matariya A., Raval D., Babu L.D., Raj E.D., Vekariya B. A Hybrid Approach for Big Data Analysis of Cricket Fan Sentiments in 2016..10.1007/978-981-10-129-5
- [8] Veshwar G., Arockiam L. A Novel Lexicon Based Approach to Enhance the Accuracy of Sentiment Analysis on Big Data
- [9] Ahmet A., Abdullah T. Real-Time Social Media Analytics With Language Models: A Big Data Approach 14th International Conference on Big Data Science and Engineering (BigDataSE) 202024180.1109/BigDataSE5071.2020
- [10] Khan M., Malviya A. Big data sentiment analysis of twitter data using Hadoop framework and learning International Conference on Emerging Trends in Information Technology and Engineering (ic-ET) 20201511009/icET4793.2020
- [11] Rodrigues A.P., Chunplak N. A new big data approach for topic classification and sentiment analysis of Twitter data. Evol. 201911
- [12] Badani B., Shi R., Dong J. A Novel Machine Learning Approach for Sentiment Analysis on Twitter Incorporating the Universal Language Model Fine-Tuning and SVM. Applied System Innovation 202210.3390/asi5010
- [13] Rodrigues A.P., Rao A.S., Chunplak N. Sentiment Analysis of Real Time Data Using Big Data International Conference on Computational Systems and Information Technology for Sustainable Solution (CSITSS) 2017161109/CSITSS.2017.844756
- [14] Srivastava A., Singh V., all G.S. Sentiment Analysis of Twitter Data. Int. J. Health c. Syst. Inform. 201914211610.4018/IJHIS.201904101

使用了相同的数据集。结果表明，与之前的研究相比，通过准确率值衡量，该语言模型产生了最先进的结果。使用建议的文本过滤策略训练 `ELECTRA` 语言模型获得了最佳结果 [14]。

结果表明，`BERT` 与 `SVM` 和 `NN` 结合时，在两个数据集上都是性能最好的文本嵌入方法。总而言之，使用 `NN` 进行整体文本分类的效果被证明优于使用 `SVM`。我们的目标是通过探索性工作提供一个多维度的比较，以识别最适用于消费者评论数据的算法，结论是：`BERT` 和 `NN` 在绝大多数情况下都能产生足够的结果 [15]。

## 拟议工作

## 系统模型

本研究评估了 `Word2Vec`（一种流行的词嵌入方法）与 `BERT`（一种 Transformer 模型）以及许多流行的机器学习和深度学习算法的表现。这种比较的主要目的是确定哪种方法最适用于情感分析和观点识别任务，并确定更换词嵌入策略是否会提高模型性能。可以通过情感分析来确定推文的内容是负面的、有利的还是中性的。然而，进行观点识别是为了确定给定的推文是否包含对产品开发过程可能有贡献的观点。然后，我们评估了深度学习与传统的机器学习技术。此分析的目的是确定在处理中等规模数据集时，两种方法中哪种更好。最后，将使用性能最好的模型来构建词图，以辅助根据推文中表达的态度和观点来传播建议的过程。

## 文本预处理

对于情感分析，我们仅从数据集中提取了两个列：“文本”（包含实际推文）以及“航空公司态度”（给出每条推文的评分值：有利、不利或极不利）。“文本”列经过了某些准备过程，例如通过从 `Spacy` 获取的停用词表删除麻烦的字符和停用词。样本中的前 3000 条推文被手动标记了一个二元变量，用于观点识别任务。标记为“是”标记的推文包含了有用的观点，这些观点可能被用于文本分类过程中。这些发推文的人都对产品有特定的喜欢或厌恶的事物，并在帖子中解释了原因。回答为“否”的推文表示它们没有为新产品开发（`NPD`）阶段提供任何有用的反馈。`Twitter` 发布者经常表达对产品的情感，但并不对其主张提供任何具体的证据。此“否”类别还包括提出问题的推文。标记完成后，我们采用了与情感分析任务相同的预处理方法。

用户评论中存在许多拼写错误、缩写、多义词和俚语表达。然而，噪声输入会对推荐系统的性能产生负面影响，降低情感分类的准确性。预处理的四个步骤如下：

- 分词：对评论者的反馈进行分词，以便以多种方式使用。
- 删除和修正：执行四种操作，包括标点符号修正、删除不必要的单词、拼写纠和俚语修正。
- 替换：除了替换表情符号，还执行了词干提取和缩写扩展。
- 词性标记：可以使用名为“词性标记”的技术将单词分解为其组件。

特征提取过程始于预处理步骤。以下是预处理的阶段：

- 应该删除包含 `URL (http://url)`、标签 (`#`)、转发推文 (`RT`) 或指向 `@username` 链接的用户评论。
- 去掉“happy”中多的 y。
- 将所有大写字母改为小写字母（例如变为 good）。
- 必须不惜代价避免拼写错误和俚语。
- 移除停用词，这些词是介词、连词和限定词等频繁使用但没有特殊含义的词。单词删除描述了这一操作。
- 词干程序涉及从词干词中定位根词，以缩小术语的大小。去掉任何复数、性别、变位等情况。

## 词嵌入

使用了两个 (2) 个神经元进行构建。处理的文本分类问题非常适合 `softmax` 多维激活函数。我们的研究包含了 `Google News` 训练的 50 维 `Glove` 嵌入、来自英语维基百科的 250 维 `Word2Vec` 嵌入数据以及来自英语维基百科的 128 维 `BERT` 嵌入数据。我们使用 `TensorFlow` 技术进行预处理和模型构建。最终分析中仅包含了训练集中的一百 (100) 次评估。

1. 显示了 BERT-CNN 的结果。

表 1 BERT-CNN 结果。

| N-Grams | 准确率 (%) | 精确率 (%) | 召回率 (%) | F 分数 (%) |
| :--- | :--- | :--- | :--- | :--- |
| N = 1 | 65.02 | 65.02 | 65.15 | 65.08 |
| N = 2 | 79.45 | 79.50 | 80.04 | 79.77 |
| N = 3 | 88.20 | 88.45 | 89.01 | 88.73 |
| N = 4 | 87.65 | 87.65 | 87.80 | 87.72 |
| 所有单词 | 84.00 | 84.00 | 84.20 | 84.10 |

表 2 Word2Vec CNN。

| N-Grams | 准确率 (%) | 精确率 (%) | 召回率 (%) | F 分数 (%) |
| :--- | :--- | :--- | :--- | :--- |
| N = 1 | 65.02 | 65.02 | 65.15 | 65.08 |
| N = 2 | 79.45 | 79.50 | 80.04 | 79.77 |
| N = 3 | 88.20 | 88.45 | 89.01 | 88.73 |
| N = 4 | 87.65 | 87.65 | 87.80 | 87.72 |
| 所有单词 | 86.00 | 84.00 | 84.20 | 82.10 |

用于情感分析的最优模型——深度学习 `BERT`，看起来似乎是意见检测中表现最差的模型。深度学习 `BERT` 提供了最好的精确率，但召回率最低。这意味着许多包含深有见解的推文被深度学习 `BERT` 误分类为没有相关意见。该研究的首要目标之一是从消费者那里收集深有见解的评论，以改进现有产品并开发新产品，因此这是非常令人警惕的。如果像深度学习 `BERT` 这样的模型消除了许多改进产品的有用建议，那么产品可能无法改进。

在将 `BERT` 与 `Word2Vec` 进行比较时，我们发现 `BERT` 词嵌入在情感和意见分类方面的表现都更好。然而，评估模型有效性的技术更为关键。在这种情况下，组合模型比深度学习更可靠。当用于情感和意见分类任务时，即使即使与各种词嵌入方法配对，深度学习的结果仍然保持一致。深度学习似乎不那么可靠，并且需要更多的人工准备。使用相同文本和数据准备方法的组合模型在数据集上的表现似乎更好。中小型的数据集也可能导致深度学习的不可靠性。因此，我们希望同时进行情感和意见分类模型构建，要利用的最优模型是结合了平衡随机森林的 `BERT`。表 2 显示了 `Word2Vec CNN`。

## 结论

我们的研究得出结论：在情感分析和意见识别模型中，`BERT` 词产生的结果优于 `Word2Vec`。在将深度学习与平衡随机森林进行比较时，后者在情感分析方面的表现更好，而组合模型在意见检测方面的得分更高。我们发现 `BERT` 结合平衡随机森林是表现最好的单模型，因为它在使用较少计算资源的情况下产生了具有竞争力的结果，并且即使在稀疏输入数据下也能保持一致。在航空业务的文本分类方面，我们还使用了词图来提供一些有用建议。根据我们收集的数据，客户的优先事项是：便利性（包括金钱方面）、航班和预订、设施和服务。航班延误和取消是消费者不满意的主要原因，解决这些问题应该是航空公司的首要任务。我们的研究还通过建议一种更高效、经济的获取社交媒体推荐的方法，来辅助新产品开发（`NPD`）流程。资源较少的小企业可以应用本研究中使用的方法，利用自身的社交媒体数据来增强其产品。未来，研究人员可以使用更大的数据集测试深度学习与更传统的机器学习算法在恢复 `NPD` 情感和有价值意见方面的效力。

## 参考文献

- [1] Cahya R.A., Bachtiar F.A., Mahmudy W.F. Comparison of Bagging Ensemble Combination Rules for Imbalanced Text Sentiment Analysis 2021.05216/jitecs.202161206
- [2] Ko K.C., Liu S.K., Hsieh J.S., Yang R.H. To See: An Empirical Comparison of Methods for Text-Based Sentiment Analysis of Online Contents From People with Autism Spectrum Condition. In. J. Mark. Res. 2036544042210.1177/147085323158065
- [3] Vashisht V., Pandey A., Yadav S. An Overview of Fine-grained Text Analysis: Survey and Challenges. ACM Transactions on Asian and Low-Resource Language 2023222116
- [4] Guo X., Yu W., Wang X. Sentiment analysis based on two-channel 5th International Conference on Electrical Engineering, Computer Science and Informatics (EICS) 202223493510.96572
- [5] Xu Z., Jin B., Zhu H. Aspect-level sentiment analysis using convolutional neural network 15th International Symposium on Parallel and Distributed Computing (ISPC)
- [6] Kondal P., Wadkar Y., Atri B. Comparison of text sentiment analysis using recurrent neural network 3rd International Conference on Frontiers Technology of Information and Computer (FTIC) 20211441710.1109/FTIC54370
- [7] Purnamasari P., Taquyiddin M., Ratna A. Sentiment analysis of text memes: A Comparison Among Supervised Machine Learning methods 9th International Conference on Electrical Engineering, Computer Science and Informatics (EICS) 2022234935
- [8] Mariel W.C., Sasha S., Pramada S. Sentiment analysis: a comparison of deep learning neural network and SVM J. Phys. Ser. 2018809.1088/17426596/97
- [9] Guven Z.A. The comparison of language models with a novel text filtering approach for Turkish sentiment analysis
- [10] Yadav S.P., Bhati B.S., Mahato D.P., Kumar S. Federated Learning for IoT Applications EAI/Springer
- [11] Shen Y., Liu J. Comparison of text sentiment analysis based on Bert and Word2vec, 3rd International Conference on Frontiers Technology of Information and Computer (FTIC)
- [12] Zhang X., Zheng X. Comparison of text sentiment analysis based on machine learning 15th International Symposium on Parallel and Distributed Computing (ISPC)
- [13] Asmawati E., Saikhu A., Siahaan D. Sentiment analysis of text memes: A Comparison Among Supervised Machine Learning methods 9th International Conference on Electrical Engineering, Computer Science and Informatics (EICS)
- [14] Yang Z., Pang P.C., Kan H.Y. Performance comparison of deep learning text embeddings in sentiment analysis tasks with online consumer reviews Proceedings of the 2022 10th International Conference on Information Technology: IoT and Smart City

利用了一种改进的 `skip-gram` 方法。对于 `skip-gram` 算法的对抗训练，我们采用了 `L2` 正则化技术。它可以提升模型在文本情感分类任务中的性能，并增强其鲁棒性和泛化能力。为了从整个文本中提取信息同时抑制无关词汇的影响，我们部署了带有注意力机制的卷积神经网络。基于 `CNN` 的文本情感分类已经完成。与 `Twitter` 数据集上的其他分类器相比，我们的模型和算法被证明更高效、更准确。

**关键词：** 注意力机制、`CNN`、`Skip-gram` 模型、文本情感分类。

> * 通作者 Madhur Grover：Centre for Interdisciplinary Research in Business and Technology, Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India; E-mail: madhur.grover.orp@chitkara.edu.in

## 引言

随着技术的进步，基于文本的网络存档已变得越来越常见。对于许多文本分类应用，传统机器学习中行之 `SVM` 和朴素贝叶斯分类器表现出色 [1]。然而，由于短文本中信息的稀乏以及卷积层和池化层的限制，这些分类器面临稀疏性问题并缺乏长期依赖关系 [2]。卷积神经网络（`CNN`）作为深度学习技术的典型示例，近年来在包括目标检测和图像处理在机器视觉任务中被广泛使用 [3, 4]。为了提高传统 `CNN` 的准确性和灵活性，我们在研究中引入了用于物体识别的 `RCNN` [4]。然而，`RCNN` 只能处理局部层级的数据，无法适应各种场景。用于处理自然语言的神经网络模型领域快速扩张，吸引了情感分析领域的更多关注 [5]。随着越来越多的人参与社交媒体，有更多数据需要分析。方面的情感分析被用于确定文本在各种语境下的极性 [6]。作为自然语言处理（`NLP`）的一个子领域，情感评估开始关注基于深度神经网络的模型 [7]。更多人使用社交媒体意味着有更多数据，这增加了分析的难度 [8]。方面的情感分析对于确定文本在不同语境下的整体语调非常有用。本研究引入了四种基于深度神经网络的方面意见挖掘算法 [8]，每种算法都有独特的输入词向量格式。我们引入了一种新颖的方面意见提取方法，该方法整合了卷积神经网络网络、注意力机制以及门控循环单元（`GRU`），它们都利用了不同的输入向量表示。本研究通过提出一种基于酒店业客户反馈的服务质量评估创新方法，丰富了相关文献 [9]。当科学家将收集的餐厅反馈作为用例将其技术与其他技术进行对比时，他们发现其在精确率、召回率、准确率以及 F 值方面均获得了优秀分数 [10, 16]。

## 相关工作

为了识别口语中的情感，我们提供了一种使用对数滤波器组能量的深度卷积循环神经网络（`CNN`）。学习区分特征的任务由卷积层负责。我们提出了一种卷积注意力方法来学习与任务相关的话语结构，其前提是更好地理解话语的内部工作机制有助于减少误解。为了描述情感语音的特征，我们额外衡量了模型中每个组件产生的性能提升。我们在 `eNTERFACE'05` 情感数据集上的实验结果支持了这一观点，表明比现有金标准技术提升了 4.62% [11]。

在本研究中，我们展示了使用改进 `skip-gram` 技术训练的卷积循环神经网络架构。对于 `skip-gram` 算法的对抗训练，我们使用了 `L2` 正则化技术。这不仅可以提升该模型在情感分类任务中的性能，还能使其具有韧性和泛化性。为了在提取文本意义数据的同时减少无关词的影响，我们使用了带有注意力机制的双向长短期记忆网络（`LSTM`）。基于 `CNN` 的情感分类终于成为现实。与 `IMDB` 数据集上的其他分类器相比 [12]，该模型和方法被证明是最高效且最准确的。

我们提出了一种基于认知科学和神经科学发现的结合自注意力机制的循环卷积神经网络（`A-RCNN`）来解决这一问题。与大多数在 `CNN` 卷积部分包含自注意力机制的方法不同，我们的技术将该机制单独划分到 `RCNN` 内部的一个独立层中。公开的数据集如 `CIF10`、`CIF100` 以及 `MNIST` 表明，我们的 `RCNN` 比普通 `CNN` 更准确。为了解决准确率低和计算量大的问题，我们建议使用带有注意的双向门控循环单元。`BiGRU` 模块可以高效地提取最关键的信息，从而提高准确率。通过 `Ninapro` 数据集和我们的数据集，我们分别获得了 92.72 和 97.85 的准确率。

## 拟议工作

## 研究缺口

自然语言处理（`NLP`）是人工智能的一个子领域，旨在通过分析书面或口头材料为计算机提供类人类的语言处理能力。人类拥有的所有信息是一团乱麻。机器很难从未处理的文本中提取意义。为了让机器从文本中学习，我们必须首先将其转换为向量。将文本转换为向量表示的过程被称为“词表示”。

# 用于文本分类的 Skip Gram 模型

当单词表示为向量时，这些向量之间的接近程度表明这些词在语义上是关联的。图片的左侧是通常与女性相关的术语，而右侧是通常与男性相关的短语。因此，如果我们输入“耳环（earrings）”一词，计算机会正确将其与女性关联起来。系统模型如图（1）所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_495_0.png)

图（1）系统模型。

我们需要能够自动学习每个词上下文的无监督学习方法，因为任何语言的词汇都是巨大的，人类无法进行分类。发现同义词的一种方法是 `skip-gram`，它依赖于无监督学习。

当给定目标短语时，`skip-gram` 用于预测其周围的单词。与之相反的是 `CBOW` 算法。在这里，你可以输入所需的术语并返回其上下文中的单词。

通过输出层的权重矩阵隐藏了隐藏层的输出向量进行相乘。接着，我们使用 `softmax` 激活函数来确定特定单词 $w(t)$ 出现在特定上下文位置 $c(t)$ 的概率。Skip Gram 模型如图 (2) 所示。

## 输入投影输出

![](img/5e4d8ef2afa52a8404b28106580e19e4_496_0.png)

图 (2) Skip gram 模型。

- 1. 一，我们的数据集或文本中所有不同术语的列表。词汇（`Vocabulary`）指的是计算机已经熟悉的术语集。字母 'V' 代表词汇。隐藏层有 N 个神经元，其中 N 是神经元的总数。
- 2. 必须预测单词的最大可能上下文位置等于窗口大小。$c$ 是以像素为单位的窗口。在提供的架构图中，例如，窗口大小为 2，因此我们将对位置在 $(t-2)$ 到 $(t-1)$ 之间的上下文单词进行预测。
- 3. 围绕特定单词的可能预测单词数量被称为“上下文窗口”。上下文窗口的值用 $k$ 表示，等于 $2*c$，其中 $c$ 是窗口大小。提供的图片上下文窗口值为 4。
- 4. 输入向量的大小（或维度）为 $|V|$。对每个单词使用单一的“热编码”（`hot encoding`）。
- 5. 六，隐藏层(W) 权重矩阵的维度为 $[V], N]$。数组的大小可以使用模运算 $|||$ 确定。
- 6. 隐藏层产生一个名为 $H[N]$ 的向量。
- 7. 隐藏层和输出层之间权重矩阵 $W'$ 的维度为 $[N,V]$。当我们对 $W'$ 和 $H$ 进行点积时，我们得到向量 $U[v]$。

## 基于注意的 CNN

注意力机制的使用被认为是增强卷积神经网络表示能力和更好地捕捉远距离特征交互的尖端方法。然而，我们发现了两个问题：注意力图的近似问题和它们的容量不足问题，这些问题在依赖认知激活的当前模型中经常被忽略。为了同时解决这两个问题，我们首先通过一种 `AW-卷积` 为 `CNN` 提出了一种注意力模块，其中注意力图的形状取权重的形式，而不是激活本身。我们提出的注意力模块是先前工作的扩展，该工作利用基于注意力的方法研究了通道级数据和空间数据之间的关系。我们建议的注意力模块已经在许多图像分类和物体识别数据集上进行了测试，证明了它的有效性。

在这里，我们检查了基于注意力激活的模型中通常被忽略的两个问题：注意力图的近似和容量不足。我们创建了一个注意力模块，主要利用 `A 卷积` 来同时解决这两个问题；我们的注意力图的形状与权重对应，而不是激活。此外，改进了注意力图的计算分支，以在速度和精度之间提供更好的平衡。最后，为了提高基于注意力的模型的整体表示能力，我们将提出的注意力模块与许多现有的模块相结合。

我们首先定义标准卷积层中使用的基本符号。通常，一个卷积层包含三个刺激：输入 (I)、权重 (K) 以及输出 (O)。总体批大小、输入路径的数量、输入特征的高度和宽度分别为 $N, C_1, H$，对于输入到刺激 $I$ 的特征图为 $R(N,C_1H,W)$。在等式 $K R(C_2,h,w)$ 中，$K$、$h$ 和 $w$ 的值分别代表输出路径的数量、高度和宽度。

```latex
