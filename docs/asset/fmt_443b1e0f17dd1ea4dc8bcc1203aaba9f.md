
# 基于 CNN 的深度学习技术在电影评论情感分析的应用

Prateek Garg

¹ 跨学科研究与技术中心，奇特卡拉大学工程技术学院，印度旁遮拉拉邦。

## 摘要

Twitter、Facebook、Instagram 等只是由于互联网使用率激增而涌出的许多讨论平台之一，为人们提供了发表观点的地方。电影既会收到赞誉，也会收到批评。科学家和研究人员仔细考虑这些评论以提取有用信息。意见挖掘（也称为情感分类）是一个不断发展的领域，它利用机器学习和深度学习来分析评论中所表达的情感倾向。由于文本通常含有丰富的语义信息，情感分析已成为自然语言处理（NLP）中最活跃的研究方向。深度学习的持续进步极大提高了分析这些内容的能力。卷积神经网络（CNN）常用于自然语言处理，因为它是最成功的深度学习方法之一。本文详细介绍了基于 CNN 的电影评论分析的方法、数据集、结果和局限性。

**关键词：** CNN，深度学习技术，电影评论，情感分析。

> * **通讯作者 Prateek Garg**: 跨学科研究与中心，奇特卡拉大学，印度旁遮拉邦；邮箱：prateek.garg.org@chitkara.edu.in

## 引言

电子产品的普及与在线社交媒体（如 Twitter）的兴起相一致[1]。高效提取和分类大量观点（通常以纯文本形式呈现）的情感挑战吸引了数据分析师的关注[2]。由于深度学习算法的进步，NLP 模型在意见挖掘和文本分类方面变得更加有效[3]。在考虑电子商务服务或产品时，大多数客户会在阅读评论文章后进行购买。不幸的是，虚假评价的泛滥[5]是这些评论的根本问题，且尚未得到完全解决。为了帮助公司和机构增强其营销策略，并深入了解客户对商品和品牌的想法，所建议的方法利用对用户评价进行意见挖掘[6]。由于个人在平台上相互互动，并就各种问题和故事以评论和意见的形式表达自己的观点，社交媒体上累积了大量的非结构化信息[7]。在衡量用户如何反应时，情感分析是金标准。在过去，由于研究人员已经使用了许多种基于机器学习和自然语言处理的技巧来探测这些情绪[8]。然而，由于其有效性，基于深度学习的解决方案正变得越来越流行。图像处理现在是基于人工智能系统领域的一项日益增长的技术。人们利用人工智能机器学习方法来探索情感识别[9]。情感识别是研究人的面部表情、肢体语言和语调如何揭示他们对电影的真实感受。评估结果显示，所提出的 CNN-BiLSTM 混合系统在精确率、召回率、F 值和准确率方面均优于传统的深度学习和机器学习方法。这种利用了混合深度学习算法的方法已成功应用于 IMDB 评论数据集[14]。

通过在活动持续期间按设定间隔监控观众反应，所提出的系统希望为活动制片人或管理员提供可靠、客观的反馈。同时也包含了“卷积神经网络”、“情绪分类”、“深度学习”和“ReLU”等词汇[15]。

## 拟议工作

![](img/5e4d8ef2afa52a8404b28106580e19e4_543_0.png)

图 (1) 系统流程图。

每个输入窗口都会经过卷积，卷积由一个线性层（后接非线性层）组成。让我们正式地假设它：

- $(x_1,...,x_n)$ - 输入单词的符号，$x_i \in \mathbb{R}^d$；
- $d$（输入通道） - 输出嵌入维度；
- $k$（卷积核大小） - 卷积窗口的长度（在图中，$k=3$）；
- $m$（输出通道） - 卷积滤波器的总数（或生成的通道数）。

这使得卷积成为一个线性层，$W \in \mathbb{R}^{(k\cdot d)\times m}$。对于大小为 $k$ 的窗口 $(X_1,\dots,X_{1+k-1})$，这种向量相加即为卷积的操作过程。

```
$u_i = [x_i, \dots, x_{i+k-1}] \in \mathbb{R}^{k\cdot d}$
```

与其卷积矩阵相乘：

```
$F_i = u_i \times W$
```

输入上卷积过程中的每个窗口都经过相同的线性变换。

在执行卷积层的卷积操作后，数据的特征被提取；然而，派生特征的维度很大；为了解决这个问题并降低网络开发成本，在卷积层之后添加了一个池化层：

```
$l_t = \tanh(x_t * k_t + b_t)$
```

$l_t$ 是激活函数，tan 是卷积输出值，$x_t$ 是输入向量，$k_t$ 代表卷积核的密度，而 $b_t$ 是卷积核的偏置。

特征由卷积层提取。卷积过程由卷积层的过滤器执行。为了从单个输入向量生成许多特征图或激活图，应用了过滤器。使用函数`model.Add(Conv1D(filters=32, kernel size=8, activation='relu'))`来创建一个卷积层。滤波器的数量由`filters`表示，而卷积核的大小由卷积窗口或卷积核大小`kernel size`表示。CNN 层的输出随后使用修正线性单元（ReLU）激活函数进行激活。该层的任何负输出都被替换为零。该层的输出与输入形状相似。

最大池池化采样层（Maximum Layer Pooling Subsampling）通过缩小空间表示的大小降低网络的计算复杂度。最大池化是一种常用的采样方法。最大池化层保留最关键的特征图或数据并丢弃其余部分。在`model`函数的帮助下创建了一个最大池化层。插入`MaxPooling1D (pool_size=2)`。

全连接层用于分类。全连接层（FCL）使用 Kara 的稠密层构建，并接收池化后的输出。在此层之后，使用基础的 Sigmoid 激活函数来验证 0 到 1 之间的输出。结果是一个二值，其中 0 表示负面情绪，1 表示正面情绪。

## 结果与讨论

## 数据收集

在这里，我们评估了用于情感分析的神经网络模型的性能。电影评论数据集可以在多处找到，例如 GitHub、Kaggle.com、UCI 机器学习库以及互联网电影数据库 (IMDb)。我们从 IMDb 爬取了评论数据并使用。影评人经常在 IMDb 等电影评分网站上发布他们的见解和评分，以帮助人们决定是否观看该电影。本研究使用了来自 IMDb（在线电影数据库）的两个数据集。研究人员可以访问并通常认可这些数据集。Kaggle.com 有两个数据集，其中数据集 I 包含了 IMDb 上电影的观众评分，共有 25,000 条评分，其中一半正面，一半负面。Kaggle.com 上还有一个名为“dataset II”的包含 50,000 条电影评论的二分类数据集。

## 数据归一化

数据清洗对于提高情感分析的“准确性”和可靠性至关重要。电影文本评论是系统的输入。仅包含英文编写的评论，点、括号和句号等标点符号已被留空。通过正则表达式，我们需要通过删除单词中的标点符号、仅仅重音符号的标记、包含数字、单个字母以及无值的标记来清理这些文本。

我们注意到数据集包含 HTML 元素和标点。因此，我们通过移除任何 HTML 元素和其他非字母数字字符清理了这些集合。我们消除了所有多余的空格并将其转换为小写。首先消除标点符号，留下了无意义的单个字符。在它们的位置，我们插入了一个分割我们收集数据的间隙。之后，数据集已清洗，它们被分为两部分：训练和测试。百分之七十五用于训练，其余百分之二十五用于测试。对于数据集 I 的 25,000 条评分，18,750 条用于训练；对于数据集 II 的 50,000 条评论，37,500 条用于训练，12,500 条用于测试。

表 1 TF-IDF 文档表示。

| 方案 | 使用 TF-IDF | 不使用 TF-IDF |
|---|---|---|
| CNN | 88.99 | 92 |
| Machines with Vector Support | 78.66 | 82.53 |
| Randomized Forest | 73.05 | 76.14 |
| KNN | 61.12 | 65.93 |
| Naive Bayes | 58.45 | 57.38 |
| Decision Tree | 54.96 | 55.61 |

表 2 通过 word2vec 的文档表示。

| ML 技术 | 准确性 |
|---|---|
| CNN | 93.68 |
| Machines with Vector Support | 65.98 |
| Randomized Forest | 73.05 |
| KNN | 61.12 |
| Naive Bayes | 49.11 |
| Decision Tree | 26.96 |

# 用于产品评论情感分析的机器学习与深度学习模型

Saket Mishra¹

¹ 印度旁遮普邦，奇特卡拉大学，奇特卡拉工程技术大学，商业与技术跨学科研究中心；电子邮箱：saket.mishra@chitkara.edu

## 摘要

$I_t = \vartheta_G[W_i(H_{t-1}, X_t) + B_i]$

其中 $\vartheta_G$ 对应 sigmoid 函数：

```
$f(x) = \frac{1}{1+e^{-x}}$
```

每个标题的分类概率使用此 sigmoid 函数计算。其输出在零和之一之间。

- **输出门：** 使用输入和当前状态计算新输出。简单来说：

```
$O_t = \vartheta_O[W_O \otimes(H_{t-1}, X_t) + B_O] \quad ()$
```

$\vartheta_C$ 双曲正切函数由 $\otimes$ 表示元素乘法。

- **遗忘门：** 应用活动来确定要忘记多少信息。简单来说：

```
$F_t = \vartheta_G[W_F \otimes(H_{t-1}, X_t) + B_F] \quad (4)$
```

然后我们计算以下状态和乘积：

```
$C_t = F_t \otimes C_{t-1}, X_t + I_t \otimes Q_t \quad (5)$
```

```
$H_t = O_t \otimes \vartheta_C(C_t) \quad (6)$
```

为了确定每个类的似概率，我们使用 softmax。

![](img/5e4d8ef2afa52a8404b28106580e19e4_529_0.png)

**图 (3)** 情感分析器。

在大多数情况下，双向 LSTM 架构。

![](img/5e4d8ef2afa52a8404b28106580e19e4_530_0.png)

**图 (4)** 双向 LSTM。

## 结果与讨论

推文从各种来源收集。研究人员查看了算法，如 GRU、LSTM 和双向算法，以确定最佳方案。图 (5) 展示了混淆矩阵。

| | 拥 | 负 |
|---|---|---|
| 拥 | 真阳性 (TP) | 假性 (FP) |
| 负 | 假性 (FN) | 真阴性 (TN) |

实际的混淆矩阵如图 (6) 所示。准确率、F 指数和敏感性是此处的一些指标。表 1 显示了所提方法与标准实践之间的比较。

| 指标 | 所提方法 | GRU | LSTM | 双向 CNN | DNN |
|---|---|---|---|---|---|
| 精确率 | 94.47 | 93.38 | 91.24 | 88.68 | 98.38 |
| 准确率 | 96.34 | 94.36 | 93.34 | 92.24 | 98.79 |
| F 指数 | 95.58 | 94.36 | 93.98 | 92.13 | 98.46 |
| 特异性 | 95.58 | 88.98 | 89.14 | 87.34 | 98.68 |
| 回召率 | 95.58 | 94.76 | 93.36 | 92.88 | 98.35 |
| 敏感性 | 96.57 | 93.33 | 91.46 | 88.34 | - |

如表所示，该分类器的性能优于现有的 SVM 算法，后者的性能表现不足。此外，所提出的分类方法也优于现有的 GRU、LSTM 以及混合（Hybrid）技术；相比之下，CNN 方法提供了大量理想的结果，包括令人瞩目的 99.32% 的清晰度、准确率、可靠性、F 值、灵敏度和记忆力。与所有其他现有的分类方法相比，这种表现非常出色。研究结果表明，所提出的 CNN 能够提供更优、更快速的情感预测。图 (7) 显示了精确率与推文数量的关系图，图 (8) 表示了召回率与推文数量的关系图，图 (9) 展示了 F 分与推文数量的关系图。

![](img/5e4d8ef2afa52a8404b28106580e19e4_534_0.png)

图 (9) F 分与推文数量的关系图。

## 结论

我们的研究展示了深度学习方法在情感分析问题中的应用。我们的研究表明，截至 2021 年 7 月，针对全球范围内进行的接种活动，33.96% 的个人持积极态度，17.55% 持负面态度，48.49% 持中立。这些结果是使用基础 NLP 工具得出的。我们还使用了基于 RNN 的 LSTM 和 Bi-LSTM 来评估我们模型情感预测和分析的质量。LSTM 架构和 Bi-LSTM 模型在准确率、召回率、F-1 评分和混淆矩阵等指标上达到了高于平均水平的预测结果。尽管许多人已决定接种，但仍有许多人由于恐惧或拒绝而不确定如何。医疗领域的研究人员可能会从这项研究受益，更好地了解接种程序带来的挑战。制药公司、国家卫生部门以及如世界卫生大会（WHO）等国际组织可以获得疫苗有效性的清晰画像。他们将更清楚地了解需要修复哪些问题以恢复公众对疫苗的信任。帮助一线员工对抗新型冠病毒可能确保公众的安全和健康。

## 参考文献

- [1] Dutta, R., Das, N., Majumder M., Jana B. Aspect based sentiment analysis using multi-criteria decision-making and deep learning over COVID-19 pandemic in India. CAAI Trans. Technol. 2022367122294
- [2] Vhassan, S., A Deep Learning Approach for Public Sentiment Analysis in COVID-19 Pandemic 2022 2nd International Conference on Intelligent Technologies (CONIT) 2022216
- [3] Jayale R.S., Desai S.S., Aspect-Level Drug Reviews Sentiment Analysis and COVID-19 Drug prediction using PPI & DeepLearning 2021 International Conference on Computing, Communication and Green Engineering (CCGE) 15202110.1109/CCGE050943.2021977639
- [4] Yusuf S.A., Zaidi C.D.S., Nascimento C., de Albuquerque V.H.C., Chauhan S.S. Analysis and Design of automatically generating for GPS Based Moving Object Tracking System 2023 International Conference on Artificial Intelligence and Smart Communication (AISC) Greater Noida, India 2023 15.10119/AISC5666.2023.10085180
- [5] Vohra A., Garg, R. Deep learning sentiment analysis of public perception of working from home through tweets. J. Intell. Syst. 20236102552741000/s10844-022-00736-26034686
- [6] Alqani A., Rahman A. Arabic Tweets-Based Sentiment Analysis to Investigate the Impact of COVID-19 2023
- [7] Coban Ö., Ozel S. Inan A. Deep Learning-based Sentiment Analysis of Turkish users 2023
- [8] Jatla S., Avela D. Hybrid Model for Sentiment Analysis of COVID-19 2021
- [9] Das S., Jaingupta T. Effect of COVID-19 using deep learning 2021.1109/CCGE
- [10] Yadav S.P., Yadav S. Mathematical implementation of sentiment 2022
- [11] Mengist T., Kumar D. Analysis and Design of automatically generating for GPS Based Moving Tracking System 2023
- [12] Ng Q., Lim S., Yau C. A clear picture of the effectiveness of vaccinations 2022
- [13] Mehta S., Sentiment analysis of COVID-19 de-. Int. Appl. Sci.
- [14] Che S., Wang X., Zhang S. Correction to daily cases of COVID-19 2023
- [15] Kim J.H. CNN-based Deep Learning Techniques for Movie Review Analysis of Sentiments 14

（注：部分参考文献内容因原文存在截断或乱码，已按要求保留格式并进行对应翻译对齐）
