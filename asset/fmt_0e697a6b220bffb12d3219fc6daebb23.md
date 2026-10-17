
在研究中，我们使用情感分析来确定 Amazon.com 上的评分和评论的匹配程度。确定文本语调是正面还是负面并将其标记为相应情感的过程被称为情感分析。消费者可能会对 Amazon.com 等电子商务网站上的评估进行权衡，并表示其意见的极性。在某些情况下，评论和评分之间存在差异。我们使用深度学习来分析 Amazon.com 产品评论的情感，以寻找评分不一致的评论。利用段落向量（`paragraph vector`）将文本评估转换为数值数据，然后将其输入到带有循环单元的神经网络中。我们构建了一个考虑评论与产品数据之间语义连接的模型。此外，我们还构建了一个网络服务，使用训练好的模型来预测提交评论的评分值，如果预期评分与提交评分不符，则向评论者提供反馈。

**关键词：** 亚马逊（Amazon），深度学习技术，机器学习，产品评论，情感分析。

## 引言

由于社交媒体和电子商务平台的泛滥，情感分析（也称为意见挖掘）近年来已成为学术界的一个热点。情感分析是一种根据人们选择选择的词汇来确定他们对特定话题有何种感受的方法 [1, 2]。在 Amazon.com 等电子商务网站上，客户在提供评论的同时会评分。自然语言处理（NLP）和机器学习技术被用于从给定的陈述中分析说话者的意图。情感分析涉及将文本分为正面、负面和中性类别。意见挖掘是 [3] 有系统地收集和分析对特定主题、产品或服务的反馈的实践。情感分析是分析收集到的意见中所反映出的反映的过程。在当今高度互联的世界，电子商务已占据了所有零售活动的大部分 [4]。客户可以从智能手机的便利地订购产品并让其送达家门口 [5]。然而，这个商业平台也有缺点，即消费者对所购买商品的价值一无所知。因此，此类服务为客户在购买商品后提供反馈提供了平台 [6]。你可以了解到客户是如何仅仅注册他们的评估的。客户反馈分可以帮助业务经理判断评论趋势是有好是有坏的，但对此进行人工分析是耗时且容易出错的 [7]。现代世界的趋势是数字化。数字经济中蓬勃发展的电子商务部门帮助所有人节省时间，让他们在不离开家中舒适环境的情况下购物 [8]。电子商务系统需要进行调整或完全废弃。公司所有者可以使用这些输入来更好地理解市场并做出明智的决策 [9]。在线产品评估的激增促进了近年来电子商务的兴起。客户的购买决策受到其他用户推荐和投诉的很大影响。解释和分类文本数据被称为情感极性分析 [10]。

## 相关工作

我们编写这项研究的目标是使用 Amazon 的数据集开发用于产品评分和文本评论的情感分析。我们实现了几种不同的学习方法，包括线性支持向量机宏模型、随机森林、多项式神经网络、朴素贝叶斯和逻辑回归。使用随机森林分类器，我们实现了 91.90% 的成功率。此外，我们采用使用 LSTM 的 RNN 作为一种深度学习的方法，并获得了最高的准确率（97.52%），RNN-LSTM 是适用于我们模型最佳的方法 [11]。

通过使用丢弃层（`dropout layer`）并从隐藏层中随机删除神经元，可以提高泛化误差。丢弃层设置为 0.3，因为在该值下，模型性能最佳。最后，通过全连接层决定特征是否具有正面或负面的情感。

## 结论

建议的方法利用了 YouTube 上的两个视频评论和一个六层卷积神经网络。该模型的准确率在 60% 到 84% 之间。建议将该模型用于更全面的数据集。尽管我们付出了最大努力，该模型在应用于更大的电影评论数据集时，准确率仅为 55%。通过修改许多参数并引入一种名为“全局最大池化”（`global max-pooling`）的新层，我们将 Alexandre Cunha 的模型准确率从 55% 提高到了 92%。由于数据集的大小和每个评估的简短，所提出的六层模型准确率较低。我们的七层卷积神经网络使用电影影评人员的数据进行了训练。我们的模型在数据集 I 上实现了 91.18% 的准确率、92.53% 的召回率、91.94% 的 F 分和 91.79% 的精确率；在数据集 II 上实现了 91.98% 的准确率、94.14% 的精确率、89.93% 的召回率和 91.72% 的 F 分。我们概述了数据清洗方法和策略，并评估了不同算法的效率、召回率和准确率。我们的最终目标是识别出最有前景的机器学习模型以便进一步研究。

## 参考文献

- [1] Alotaifi F., Gupta V.G.. Sentiment analysis system using hybrid word embeddings with convolutional recurrent neural network. Int. Arab J. Inf. Technol. 2022 193330350.34028/iaijt/19/3

- [2] Kaliapp N.K., Thamasaputhri Rajeshwari S., Dakshinamoorthy P., Sundaraju N., Sundar R.. Intelligent video surveillance using enhanced deep belief based multilayer convolution neural network classification techniques. Photogramm. Rec 20231781409050210.111/phor.12429 

- [3] Amrani G., Adadi A., Berrada M., Souirti Z., Boujraf S.. EEG signal analysis using deep learning: A. systematic literature review 2021 Fifth International Conference On Intelligent Computing in Data Sciences (ICDS)18 2021 10.1109/ICDS53782

- [4] Yadav S.,P., Fusion of Medical Images in Wavelet Domain: A Discrete Mathematical Model. Ingeniería Solidaria Universidad Cooperativa de Colombia-UCC.202114258

- [5] Gandhi U., Malav K., Karthick G.. Sentiment Analysis on Twitter Using Convolutional Neural Network (CNN) and Long Short Memory (LSTM). Wirel. Public.20221601109/975

- [6] Nabeel M., Große C.. Classifying Disinformation on Twitter Using Convolutional Neural Network International Conference on Information Systems and Privacy.20226896931.1109/577

- [7] Vaishisht V., Pandey A.K., Yadav S.. Speech Recognition using Machine Learning. IEIE Transactions on Smart Processing & Computing The Institute of Electronics Engineers of Korea.2021103223910.

- [8] Mohamed B.,A., Ani-S.. Research of Medical Image Analysis Using Deep Learning.202021928/uhdjst.v425-90

- [9] Ma X., Zhou Q.. Special issue on deep learning and neural computing for intelligent sensing and neural control. Comput. Appl.2021181811007/s00521-020-0478-9

- [10] Kaur J., Saxena S., Jah S.. Facial Emotion Recognition 2022 International Conference on Computational Intelligence and Sustainable Engineering (CISES).202254857.984436

- [11] Yu D.. Intelligent Analysis System of Movie Reviews Using Deep Learning and Convolutional Networks 2021 IEEE Conference on Telecommunications, Optics and Computer Science (TOCS)617620211109/53301.

- [12] Sabha S., Cheik N., Kabul H., Sentiment Analysis for IMDb Using Deep Learning Signal Processing and their Applications (IPA)20221601109/IPAS4004.978624

- [13] Alzahani M., Aladhani T.,subari S., Althobaiti M., Fahad A.. Developing an Intelligent System with Deep Learning Algorithms for E-Commerce Product Reviews. Comput. Intel. Neurosci.20222021109/2522/3384007135964

- [14] Krishna M., Duraisamy B., Vankara J.. Deep Learning Techniques for Sentiment Analysis on Datasets International Conference on Advance Computing and Innovative Technologies (ICACITE)20226896931.1109/ICACITE53722.2022.983898

- [15] S. Sinha, Jayan and comparison of deep-learning techniques and hybrid model for sentiment analysis for movie review. Proc. 202223rd Int. Conf. Emerging Technol. (INCET) Bengaluru, India 20215

这是产品分析中经常使用的分类模型。与现有的机器学习方法相比，所提方法将提供优的结果 [12]。

在这项研究中，我们使用机器学习方法来构建计算模型，能够自动识别对产品的正面和负面评价。我们使用 Amazon.com 的书籍评论数据进行研究。采用词袋模型（`bag of words`）对数据进行处理，以适应面向机器学习的策略，然后使用逻辑回归、朴素贝叶斯、支持向量机以及神经网络技术开发了模型。词嵌入（`Word embedding`）是在转向 LSTM 和门控循环单元（GRU）之前，用于将数据转换为以适应深度学习方法格式的方法之一。我们分别评估了预处理和未预处理的数据集，以评估机器学习和深度学习模型的效率。结果表明，在预处理和未预处理的数据集上，神经网络中的短语词袋模型（`bag of phrases`）获得的结果均优于任何其他方法 [13]。

本研究利用 SVM 和 CNN 这两种机器学习和深度学习分类算法，对 Amazon 客户产品评价的情感分析进行了对比研究 [14]。

我们的目标是根据我们认为每条客户评论的正面或负面程度对其进行分类。这些短语中的每一个对于我们情感极性检测的成功至关重要：特征提取、训练、分类和泛化。使用 Tf-Id 和分词器（`Tokenizer`）将评论转换为向量格式。然后，我们使用 LSTM、线性 SVM、RFB 和 Sigmoid 深度学习模型进行训练。然后根据准确率、F1 分数、精确率召回率对模型进行评估。对于 Amazon 客户评论，我们的 LSTM 模型预测准确率为 86%；对于 Yelp 评论，预测准确率为 85% [15]。

## 拟议工作

## 系统模型

我们开发了一种采用带有门控循环单元（GRU）的循环向量表示神经网络（RNN）的模型，它通过段落向量（`paragraph vectors`）和产品嵌入学习评论的低维表示，以解释 Amazon.com 评论的情感。首先，我们使用段落向量将 Amazon.com 产品评论转换为带有一组特征的数据。这些特征根据其产品进行分组，并按重要性进行排序。使用每组数据训练了带有 GRU 的 RNN。RNN 生成的倒数第二层向量是产品嵌入。产品属性和评论之间的时间交互是包含在这些表示中的信息类型。然后，通过将产品嵌入数据与段落向量生成的固定长度向量拼接，训练了一个支持向量。我们还建立了一个用户接口，让用户解决评论与评分之间的差异。一个人可能对某个产品非常热情，但只给一或两星；或者可能非常挑但仍然给五星评价。虽然这不寻常，但确实引起了依赖这些评价的消费者的担忧。为了解决这一担忧，1 星和 2 星的评论被认为是负面，3 星的评论被认为是中性，4 星和 5 星的评论被认为是正面。然后，我们构建了一个网络服务应用程序，使用我们的分类器根据用户反馈做出此类预测。如果提交评分的类别与其预测的类别不同，则会向用户发送警告。图 (1) 展示了我们的方法论框架。

![](img/5e4d8ef2afa52a8404b28106580e19e4_554_0.png)

**图 (1)** 系统模型。

## 数据收集与处理

Fang 等人为本研究的数据集从 Amazon.com 获取了约 350 万条商品评价。每条评论都有星级评分、产品标识符、帮助性评分、评论者标识符、评价标题、评价时间以及评价文本。总分为 5 分。在线评论中的超链接、HTML 标签、口语语言和其他过滤词汇，其中许多词汇对评论的整体意义没有贡献。如果将此类术语留在评论内容中，情况将变得更加复杂。为了解决这个问题，每条评论在转换为相应的向量之前都经过了预处理。

## 词汇开发

我们将所有评论语句拼接成一个巨大的字符串，并拆分这些短语，以生成数据集中的每一项。我们使用段落向量将评论转换为向量格式。*（注：此处原文文本 556 存在重复循环）*。然后根据准确率、F1 分数、精确率召回率对模型进行评估。

bi-GRU 或 CNN 模型。作为设计的最后一步，我们使用线性层将 8 特征空间压缩到 4 维。

整合袋层（`incorporate bag layer`）和线性层是快速文本架构模型中的两个主要隐藏层。根据我们的经验，模型采用了 2-gram 嵌入和“均值”（`mean`）模式对袋的值进行平均处理并进行收缩。因此，通过将梯度张量设为稀疏张量，省略了向量中的“o”值，因为信息中的短语并非都是相等的。使用线性回归将权重回归到嵌入维度并将其缩小到预测特征的数量，第二层被用作分类器。这些层中的权重均分分布在 -0.5 到 0.5 之间。Pyorch 中交叉熵损失函数日志输入中的 softmax 用于将每个信息点的向量值分配给特征的似然概率。采用随机梯度法和调度器（`scheduler`）作为优化器。每个训练次（`epoch`），调度器按初始梯度的0.9 降低学习率。

## 结果与讨论

首先，我们使用 Genium 框架创建了一个由段落级评论组成的简单模型。来自 Amazon.com 的超过250万条评论被转换为 300 维固定长度向量。在对上述模型进行 15 次迭代时，我们使用了 0.025 的学习率、10 的间隔大小和 30 个工作线程。

Amazon 最著名的产品之一是以产品评论形式提供的客户反馈。自1995年发布第一条评论以来，亚马逊上的无数消费者已撰写了超过1000万条评论，与其他购物者分享他们的想法和经验。因此，自然语言处理（NLP）、信息检索（IR）和机器学习（ML）等领域的科研人员可能会亚马逊客户评论中发现大量的有用数据。因此，我们正在公开这些信息，以鼓励学术之外的进一步研究，以提高对客户产品体验的了解。特别是，该数据集旨在代表消费者评分和评论的横截、产品感知的区域差异以及评论中的营销潜力。

该数据集主要包含两个部分：客户评论的内容和描述它们的信息：

- 有一个 1995 年至 2015 年间 Amazon.com 市场客户评论和其他信息的数据库。目标是更容易调查客户评论的特征（及发展），这可能包括个人用于评价物品的标准以及他们描述体验时使用的语言。（平均分 5 分中的 4.9 分）。

- 为了了解不同国家不同群体如何评估物品，我们汇集了由 Amazon 客户用多种语言和来自多个 Amazon 市场编写的评论。（5 语言超过 20 万条客户评分）。

- 此前一个包含非合规评估的数据集已因召回而停止流通。此前通过同意某些数据使用的条款和条件获得访问权限的人，可以在相同条件下继续使用。

## 访问亚马逊客户评论数据集

研究人员现在可以访问超过 1300 万条用户评论。您可以在 AWS 美国东部区域（US East Region）名为“amazon-reviews-pds”的 S3 存储桶中找到这些信息。文件为 TSV 格式。数据文件以制表符分隔且没有引号转义字符；每行代表单条评论。每个训练次之后，指令率降低了 0.002。在生成产品评论的 300 维嵌入数据后，我们根据“产品 ID”对其进行聚类，并按“评论时间”排序。序列的最后一步嵌入被用作产品的嵌入。表2 展示了 CNN 和 RNN-GRU 的迭代情况。

表 1 CNN 和 RNN-GRU 的损失值。

| 损失值 | CNN | | RNN-GRU | |

| :--- | :--- | :--- | :--- | :--- |

| 准确率 (Exactness) | 回召率 (Recollection) | 准确率 (Accuracy) | 回召率 (Recollection) |

| 10 | 0.5987 | 0.4183 | 0.8168 | 0.8987 | 0.8183 |

| 9 | 0.5940 | 0.4314 | 0.8189 | 0.8940 | 0.8114 |

| 8 | 0.5915 | 0.4265 | 0.8185 | 0.8915 | 0.8265 |
