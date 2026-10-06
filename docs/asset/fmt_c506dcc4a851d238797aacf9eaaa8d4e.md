
# 多语言仇恨言检测

Dibya Ranjan, Jitesendra Pratap, Abhinav Kumar

## 目录

1. [引言](#1-引言)
2. [什么是仇恨言？](#2-什么是仇恨言)
3. [仇恨言识别](#3-仇恨言识别)
   3.1. [英语识别](#31-英语识别)
   3.2. [其他语言识别](#32-其他语言识别)
   3.3. [混合代码识别](#33-混合代码识别)
4. [讨论](#4-讨论)
5. [结论与未来方向](#5-结论与未来方向)

## 参考文献

Chopra, S., Sawhney, P., Mathur, and R. R. Shah (2020). 印地语-英语仇恨检测：作者画像、去偏与实用视角。见 *Proceedings of the AAAI Conference on Artificial Intelligence*, 34, pp. 386–393.

Dave, B., S. Bhat, and P. Majumder (2021). 使用 `tf-df` 字符 `n-gram` 和 `nuclei` 进行混合代码中的希望言论检测。见 *Proceedings of the First Workshop on Language Technology for Equality, Diversity and Inclusion*, pp. 114–117.

Dowlar, S. and R. Mamidi (2021). `Edione@lt-id-eacl2021`: 用于希望言论检测的卷积神经网络预训练 `Transformer`。见 *Proceedings of the First Workshop on Language Technology for Equality, Diversity and Inclusion*, pp. 86–91.

Hassan, A., V. Qazvini, and D. Radev (2010). 态度是什么？识别在线讨论的句子。见 *Proceedings of the 2010 Conference for Empirical Methods in Natural Language Processing*, pp. 1245–1256.

Junaida, M. and A. Ajes (2021). `Ku np@lt-id-eacl2021`: 基于上下文嵌入的公平、多样性和包容性多语言希望言论检测。见 *Proceedings of the First Workshop on Language Technology for Equality, Diversity and Inclusion*, pp. 79–85.

Kumar, A., Saumya, and P. Roy (2022). `SOA_NLP@LT-EDI-EACL2022`: 一用于 YouTube 评论希望言论检测的集成模型。见 *Proceedings of the Second Workshop on Language Technology for Equality, Diversity and Inclusion*, pp. 222–238, 爱尔兰，都柏林。计算语言协会。

Lee, H.-S Rao, J.-U. Park, and Y-S Han (2018). 基于增强缺失和非攻击词列表的攻击性文本检测系统。决策支持系统, 13, 22–31.

Mozafi, M., R. Farahbakhsh, and N. Crespi (2019). 用于社交媒体言论检测的基于 `BERT` 的迁移学习方法。见 *International Conference on Complex Metrics and Their Applications*, pp. 928–940. Springer。

Roy, P., S. Shawal, A. Kumar, and B. R. Chakravarthi (2022). `IIITSurat@LT-EDI-ACL2022`: 使用机器学习的希望言论检测。见 *Proceedings of the Second Workshop on Language Technology for Equality, Diversity and Inclusion*, pp. 120–126, 爱尔兰，都柏林。计算语言协会。

Roy, P. K., A. Singh, A. K. Tripathi, and T. K. Das (2022). 网络欺凌检测：一种集成机器学习方法。计算科学与工程国际期刊, 25, 315–324. https://doi.org/10.1504/ijcse.2022.123121

Roy, P. K., A. K. Tripathi, and T. K. Das (2022). 使用机器学习技术识别社交网络中的网络欺凌帖子。见 Saho, J.P., Tripathi, A.K., Mohanty, M., Li, K.C., and Nayak, A.K. (eds) *Advances in Distributed Computing and Machine Learning*. Lecture Notes in Networks and Systems, 302 (pp. 186–195). Springer. https://doi.org/10.1007/978-9814-46017-8

Roy, P. K., A. K. Tripathi, T. K. Das and X.-Z. Gao (2020). 一种使用深度卷积神经网络的希望言论检测框架。见 *IEEE Access*, 8, pp. 204951–204962, doi:10.1109/ACCESS.2020.3037073

Roy, P. K. and S. Chahar (2020). 社交网站上的虚假资料检测：全面综述。*IEEE Transactions on Artificial Intelligence*, vol. 1, no. 3, pp. 271–285, doi:10.1109/TAI.2021.3064901

## 社交媒体平台上的希望言论检测

Roy, P. M., S. Bhawal, and C. N. Subalalitha (2022年9月). 使用深度集成框架进行达罗毗语中的仇恨言和攻击性语言检测。*Computer Speech and Language*, 75, C. https://doi.org/10.1016/j.csl.2021.101386

Santosh, T. and K. Aravind (2019). 印地语-英语混合代码社交媒体文本中的仇恨言检测。见 *Proceedings of ACM India Joint International Conference on Data Science and Management of Data*, pp. 310–313.

Saumya, S. and A. K. Mishra (2021). `liitwdw@It-eacl2021`: 基于上下文嵌入的公平、多样性和包容性多语言希望言论检测。见 *Proceedings of the First Workshop on Language Technology for Equality, Diversity and Inclusion*, pp. 79–85.

---

## 1. 引言

自 `COVID-19` 爆发以来，世界一直经历着艰难时期。这场疫情严重影响了许多人的生活。当无法进行线下教学时，学校和学院恢复在线教学。疫情影响了所有领域，但教育领域受影响最大。

仇恨言自 `Web 2.0` 出现以来一直是一个难题，因为它允许用户创建和分享。`Facebook`、`Twitter` 和 `YouTube` 等功能允许用户相互互动。这些平台提供的匿名性为这些煽动者提供了便利。根据文献 [2]，`Facebook` 等大公司因在防止这些行为方面做得不够而受到批评。开发仇恨言系统有助于建立一个更好的社会。然而，在当前环境下制定策略要困难得多。

最初，研究主要关注英语。随着互联网的发展，它开始支持其他语言，针对这些语言的仇恨言识别也随之开始。在几年里，针对混合代码内容的仇恨言识别取得了显著进展。因此，本章对文献进行了详细综述。虽然已有关于该主题的综述，但本章旨在补充 `Lucas` 等人 [3]、`Schmidt` 和 `Wiegand` [4]、`Fortuna` 和 `Nunes` [5] 以及 `Poletto` 等人 [6] 的工作。

本文后续章节安排如下：在第 5.2 节中介绍问题。第 5.3 节解释了所有文献，随后在第 5.4 节进行讨论，最后在第 5.5 节得出结论并提出未来方向。

## 2. 什么是仇恨言？

即使对人类来说，定义仇恨言也不容易。因此，并没有一个公认的仇恨言定义，且定义的各个方面存在差异，尚未完全达成共识。然而，仇恨言论与可接受的自由表达之间的界限非常模糊，因此我们对于精确定义仇恨言论感到犹豫 [7]。在本节中，我们从多个来源收集了仇恨言论的定义，并将它们总结在表 5.1 中。

尽管这些定义存在相似之处，但它们并没有通过单一且具体的特征达成共识。因此，根据作者 [14] 的观点，对仇恨言论进行简单解释有助于识别仇恨言论的研究，使其更容易进行标注，从而提高标注的可信度。

### 表 5.1 仇恨言论定义

| 来源 | 定义 |
|---|---|
| 《美国宪法百科全》 [8] | “仇恨言论是指基于种族、宗教、民族起源、国籍、性别、残障、性取向或性别身份等属性攻击个人或群体的言论。” |
| 欧洲人权法院 [9] | “所有传播、煽动或证明种族仇恨、排外主义、反犹太太主义或其他基于不容忍的仇恨正合理的表达形式，包括通过激进民族主义和民族中心主义表现的不容忍，以及对少数群体和移民背景人士的敌意。” |
| `Facebook` [10] | “禁止根据人们实际或感知的种族、民族、国籍、宗教、性别、性别身份、性取向或残障攻击他人的内容。我们允许可能被视为潜在威胁或攻击的幽默或讽刺尝试。这包括许多人可能认为趣味低俗的内容（笑话、单口喜剧、流行歌词等）。” |
| `YouTube` | “仇恨言论是指基于某些属性（如种族或民族起源、宗教、残障、性别、年龄、退伍军人身份以及性取向/性别身份）对个人或群体促进暴力或仇恨的内容。在被视为仇恨言论与不视为之间存在着微妙的界限。事实上，批评一个国家通常是可以的，但不能仅仅根据民族对某群人发表恶意、仇恨的评论。” |
| `Twitter` [12] | “仇恨行为：您不能基于种族、民族、国籍、性取向、性别身份、宗教信仰、残障或严重疾病煽动暴力或直接攻击他人。” |
| `Almagor` [13] | “由于实际或感知的先天特征，而针对个人或群体的具有偏见动机的、敌意的、恶意的言论。” |
| `Fortuna` 等人 [5] | “仇恨言论是一种基于特定特征（如外貌、宗教、血统、国籍或民族起源、性取向、性别身份或其他）攻击或贬低、煽动对群体暴力或仇恨的语言，它可以以不同的语言风格出现，以微妙的形式或在使用幽默时出现。” |

## 3. 仇恨言论识别方法

本研究旨在了解仇恨言论识别领域的文献。为了实现这一目标，我们对现有文献进行了系统综述，这与本课题更为相关。

随着 `Web 2.0` 的出现，用户可以与互联网其他用户进行互动，仇恨言论问题随之产生。该领域的早期文献可以追溯到上个十年的早期。以来，该领域有了大量研究，但这个问题在 `COVID-19` 大流行期间引起了广泛关注。在早期，大多数研究仅关注英语。在上个世纪末，当人们可以使用其他语言在互联网上编写内容时，文献中出现了非英语语言的仇恨言论识别研究。近年来，文献中出现了大量关于语言混合或代码混合（`code-mixed`）的研究。

在文献中，所有提出的方法都使用了某些机器学习/深度学习来分类仇恨言论。因此，存在大量使用机器学习的方法，如逻辑回归 [15]、支持向量机 (`SVM`) [16]、随机森林 [17]、决策树 [18]，以及深度学习方法，如全连接神经网络 [19]、卷积神经网络 (`CNN`) [20]、长短期记忆网络 (`LSTM`) [21]。`n-gram` 方法使用了如词袋模型 (`BoW`) [22]、`n-词嵌入` 等文本特征。这并非首次关于仇恨言论识别的综述，但大多数关于该主题的综述是根据所使用的算法和/或使用的特征对文献进行分类的。

### 3.1 仇恨言论与攻击性语言研究

大多数基础方法使用简单特征作为强度、用户意图、仇恨目标 [27] 用于仇恨言论。此外，更流行的方法将特征提取与传统机器学习相结合以实现目的 [28]。它们使用了词逆文档频率 (`tf-idf`)、语义、词汇、主题建模、情感、`BoW` 以及嵌入技术，如 `FastText`、`GloVe` 和 `Word2Vec` [29]。一些作者使用了降维技术来减少复杂性 [30]。`Wagner` 和 `Hirschberg` [26] 提出了一种使用带有线性核的 `SVM` 来检测仇恨言论的方法。该方法实现了 94% 的准确率。

特别是来自 `Transformer` 的双向编码器表示（`BERT`）。多项研究调查了 `BERT` 在仇恨言论检测中的性能，几乎所有作者都认为 `BERT` 模型优于其他深度学习模型 [44–46]。例如，`Rasinghe` 等人 [47] 将 `BERT` 与 `FastText`、`CNN` 和 `LSTM` 进行了比较。同样，`Saleh Alatawi` 等人 [45] 将 `BERT` 与 `BiLSTM` 和 `LSTM` 进行了比较，`BERT` 显示出性能的显著提升。即使在所有多语言任务中 [48] 如此。有些研究比较了不同的 `BERT` 模型，发现结合两个 `BERT` 模型的性能优于单个预训练 `BERT` 模型 [49]。在最近的一项仇恨言论检测竞赛中，十表现模型中有七个在子任务中使用了 `BERT`。

所有关于仇恨言论检测的研究如果没有丰富的语料库都是是不可能的。因此，在表 5.2 中，列出了适用于英语仇恨言论的数据集。

### 表 5.2 英语可用数据集

| 数据集 | 关注点 | 规模 | 来源 | 策略 |
|---|---|---|---|---|
| `AAM` [45] | 种族主义 | 1,999 | `Twitter` | 非二分类 |
| `DPGC` [50] | 白人至上 | 10,568 | `Stormfront` | 二分类 |
| `DMWW` [33] | 仇恨言论、种族主义、性别歧视、同性恋恐惧 | 24,802 | `Twitter` | 非二分类 |
| `ENNVB` [51] | 仇恨言论、攻击 | 27,330 | `Twitter` | 多级 |
| `ETHOS` [52] | 仇恨言论 | 998 | `Reddit` | 二分类 |
| `ETHOS` [52] | 仇恨言论 | 433 | `YouTube` | 非二分类 |
| `GKH` [53] | 仇恨言论 | 62M | `Twitter` | 二分类 |
| `H` [54] | 暴力 | 24,840 | `YouTube` | 二分类 |
| `HSH` [55] | 仇恨言论 | 159,572 | `Wikipedia` | 二分类 |
| `KKS` [56] | 网络欺凌 | 2,235 | `YouTube` | 二分类 |
| `KTHS` [57] | 仇恨言论 | 16,130 | `Twitter` | 二分类 |
| `MGANH` [58] | 仇恨言论、种族主义、性别歧视 | 975 | `Twitter` | 多级 |
| `NSG` [59] | 攻击性语言 | 168M | `Reddit` | 二分类 |
| `NTTMC` [60] | 辱性语言 | 31M | 新闻网站 | 多级 |
