
# 多变量数据集特征

- 总出现次数：50,425 次。
- 课程负载：4。
- 部门：计算机科学。
- 区分性特征：真实。
- 属性计数：1。
- 关联任务：分类。
- 道德丧失？否。

## 系统模型

在这项研究中，我们展示了一种关键词加权的评估文本分类系统。实验结果表明：(1) 关键词权重可能会优先考虑高判别性的关键评估，提供评估文本更佳的特征表达，并更好地纠正错误的评估。两个 `SoftGRU` 模型可以从电子商务评估文本中提取更多语义特征，具有更好的分类性能，并在各种商品评估集和句子向量维度下为虚假评估提供更多益处。

在电子商务产品评论的文本数据中，真实评估与虚假评估在信息内容、评估短语的使用以及相对于真实购物评估的多样性上均不同。真实消费者在试图增强或损害产品影响时，倾向于使用更少的词汇。这项工作提供了一种基于关键词权重的 `TF-IDF` 方法，根据评估数据的特征来提高虚假评估程度。词汇表由关键词使用的语言形成，通过对超过阈值的关键词向量赋予更高权重来提高模型的分类准确性。图 (1) 代表了系统流程图。

### 程序

通过 `TF-IDF` 计算文本密度。

### 入取

电子商务评估文本集 $T = \{T_1, T_2, \dots, T_N\}$。

1. 文本 $T = \{T_1, T_2, \dots, T_N\}$ 中每个单词的词频 $f(T,x)$
2. 频率大于平均值的词集 $C = \{C_1, C_2, \dots\}$
3. 找出 $C$ 中每个单词的 `TF-IDF` 值
4. 收集关键词集 $X = \{X_1, X_2, \dots, X_N\}$ 以及 $T, C$
5. 对于每一个 $T'_i$ 执行
6. 使用文本集，找到第 $i$ 个单词向量 $t'_i$
7. 对于每一个 $X'_i$ 执行
8. 使用文本集，找到第 $i$ 个单词向量 $X'_i$

$Sim_i = \frac{c_i s_i}{\|c_i\| \|s_i\|}$

9. 计算值值 `Sim = {$sim_1, sim_2, \dots, sim_n$}`，合并集合
10. 结束循环
11. 在集合 `Sim` 中选择 $maxsim_n$ 作为单词向量 $t_n$ 的权重 $w_n$，添加权重集 $W = \{w_1, w_2, \dots, w_n\}$
12. 结束循环

$W_i = \frac{\exp(w_i)}{\sum_{j=1}^n \exp(wj)}$

13. 归一化权重
14. 返回 $W_i$

文本通过注意力机制深度 `GRU` 模型后，已经过了有效的预处理。词嵌入层、`Dropout` 层、`GRU` 层、`Tanh` 层、注意力层和 `Softmax` 层仅是拟议注意力深度 `GRU` 的少数层。

`Fasttext` 是一种基于词的嵌入方法，用于特征提取。每个字母 ($\omega$) 都被拆分为推文中的字符串。为了确保准确识别稀有词，这种将单词划分为更小单元的过程取决于先确定的 `k` 值。在这种表示中，根词被写为所有词素之和，

> $s(\omega, \epsilon) = \sum_{h \in H_{H\omega}} g_h \ v_{\epsilon}$

其中，$h$ 表示每个组件单词，$H_{H\omega}$ 表示子词组。$\epsilon$ 表示上下文，$v_{\epsilon}$ 表示每种情况下的上下文向量。`GRU` 层接收编码后的单词并结合输入 $v_t$ 和 $y_{t-1}$ 生成输出 $y_t$，公式如下，

$rs_t = \sigma(J_r v_t + D_r y_{t-1})$

$ud_t = \sigma(J_u v_t + D_u y_{t-1})$

$\hat{y}_t = tanh(J_e v_t + D(r_t \odot y_{t-1}))$

$y_t = (1 - ud_t) \odot y_{t-1} + ud_t \odot \hat{y}_t$

$rs_t, ud_t,$ 和 $y_t$ 分别是维度为 $d$ 的隐藏门、更新门和重置门。$\sigma$ 是 `sigmoid` 函数的符号，$J_r, J_u, J_e, D_u$ 是风险 `GRU` 层的参数设置。可以使用 `Tanh` 函数学习用于进行困难判断的非线性分类边界。特别地，我们检索了与加强词、削弱词、否定词、词素、语义和句法相关的特征。`SentiWordNet` 是一个用于研究词之间语义连接的词汇库。每个词都根据同义词集（`synsets`）被赋予一个正分和一个负分，表示如下，图 (2) 表示了基于注意力 `GRU` 的文本分类。

![](img/5e4d8ef2afa52a8404b28106580e19e4_55_0.png)

$P_s = \frac{1}{b} \sum_{t \in Z} Sp(t)$

```
$N_s = \frac{1}{b} \sum_{st \in Z} Sn(st)$
```

其中 $Sp$ 和 $Sn$ 分别显示 `Senti WordNet` 的正面和负面评分。$P_s$ 和 $N_s$ 表示词在同义词集方面的正面和负面评估。$b$ 意味着该术语 $\alpha$ 有许多同义词。注意力层接收这些特征及其得分，预测每个特征的关联性，然后移除重复特征以处理降维。可以使用加权和法计算特征向量，如下：

```
$y^{(k)} = \sum_{n=1}^{P_k} Y_i^{(k)} y_i^{(k)}$
```

其中 $y^{(k)}$ 是 `GRU` 层在 $i$ 处的输出，权重 $y_i^{(k)}$ 表示为：

```
$\Gamma_i^{(k)} = aj_i^{(k)} + b$
```

其中，$a, b$ 分别对应相应的网络设置。在 `softmax` 层中，根据注意力层的输出，将特征向量分为五类类别之一：强正面、正面、负面、强负面和中性。预处理后的推文作为所提出的基于关注的 `GRU` 情感分类模型的输入，所得分类结果如图 2 所示。

## 结果与讨论

使用本研究提供的 `SVM` 方法、`SOFTGRU` 模型和 `DBN` 模型进行了分类和比较实验。此处仅使用了耳机评估数据集，并随机选择了训练数据与测试数据之间 7:3 的划分。图 (3) 显示了实验结果。

上述图表证明了 `SOFTGRU` 算法在准确率、精确率、召回率和 `F1` 分数四个性能指标上保持了一致性。存在很大变化。该方法随着训练样本数量的增加出整体上升趋势，表明分类准确性随训练学习同步增长。本研究中提出的每种方法的效率也明显优于竞争算法。

![](img/5e4d8ef2afa52a8404b28106580e19e4_58_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_58_1.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_58_2.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_58_3.png)

图 (3) 性能分析。

## 结论

在研究中，我们提供了一种关键词加权的方法来对文本进行分类评估。实验结果表明：1) 关键词加权可能会优先考虑高判别性的关键评估，为被评估文本提供更好的分类特征表现，并更好地执行错误评估。(2) 通过在多个商品评估集和向量维度上比较分类模型的性能，揭示了 `SgtGRU` 模型能更好地提取电子商务评估测试的语义特征，从而获得更好的分类性能并对错误评估更有益处。

## 参考文献

- [1] Zhi-ming Q., Jinxian L.. Application of PCFA in Assessing Security Technique in E-Commerce Affairs2009 Second International Symposium on Electronic Commerce and Security413417200910.1190/ISECS.2009.25
- [2] Liu L.. Investigation on E-Commerce Base on Suffix Trees and Moore's Law2009 International Conference on Environmental Science and Information Application Technology502727009
- [3] Sanyuan S., Xiao W., Tang G., Li C.. Investigation of primary components analysis in influential factors of E-Commercedevelopment200910.109/CCM34
- [4] Zhang D., Zhang M., Xiao D., Liao C.. Coordination formation and application in virtual organizations2004
- [5] Xiao D., Liao C., Li-ping D., Minghe H.. Security scheme for mobile agent2016
- [6] Longjun H., Caiying Z., Li-ping D., Minghe H.. Research and Implementation of E-commerce Platform Based.NET Framework2009
- [7] Khan M., Da S., Nascimento C.D., Albuquerque V.H., Chauhan S.. Fingerprint Biometric-based Self-Authentication200911.1007/978-3-470
- [8] Yadav S.P., Zaidi S., Nascimento C.D., Albuquerque V.H., Chauhan S.. Analysis and Design of automatically generating for GPS Based Tracking System2023 International Conference on Artificial Intelligence and Smart Communication (AISC)Greater Noida, India.202315.10.1109/AISC56616.20231008518
- [9] AirAsia's e-commerce websites on its consumer behavior.Int. J Tourism Hosp. Asia Pac202353
- [10] Li F., Chen H., Wu Q., Tu J., Zhang J., Chen H.. AllEG: Domain Knowledge Graph Construction and Application in e-commerceProceedings of the 29th ACM International Conference on Information & Management202010.1145/334031.342685

通过特征工程挖掘文本中的相关信息。该实验使用 `Python` 定义文本数据集，结果表明，我们的模型在准确率、召回率和 `F` 值方面优于使用经典机器学习方法训练的基准模型。

**关键词：** 情感极性判断、特征工程、机器学习、文本分类。

> * 通讯作者 Sorabh Sharma：Chitkara 工程与技术大学商业与技术跨学科研究中心，Chitkara 大学，旁遮普邦，印度；电子邮件（电子邮箱）：sorabh.sharma.org@chitkara.edu.in

## 引言

受 COVID-19 大疫情影响，全球所有活动都停止了。在这种情况下，照顾个人的心理和情感健康与照顾身体健康同样关重要。由于远程办公已成为常态，用户现在利用 `Twitter` 表达他们对局势的感受，他们的推文可以通过这种方式进行分析 [1, 2]。文本情感分析是许多自然语言处理（`NLP`）任务的必要组成，随着社交媒体平台的日益普及，从互联网数据中筛选有用见解已变得越来越重要 [3]。鉴于近期的发展，我们正在考虑使用基于深度学习的模型来管理情感分类。由于 2019 年 7 月 20 日发生的服务故障，Bank Mandiri 的价格在 2019 年 7 月 22 日开盘时较开盘价下跌了 0.95% [4, 5, 6]。为了寻找 `Twitter` 或在线媒体报道态度、观点与 Bank Mandiri 银行（`BMRI`）股票价格之间的联系 [7]，跌幅扩大到较前价格的 1.27%。利用文本挖掘获取数据，使用逻辑回归对模型进行优化，并使用 `FastText` 进行特征扩展以通过减少词汇差异来预测情感 [8]。然后，在年底，进行了皮尔逊相关系数测试，以查看 5 月至 9 月的情感预测与股票价格是否相关。连接 Bank Mandiri 的股票价格数据，以了解客户对 Bank Mandiri 提供的某些服务的满意度 [9]。事实证明，将高效的词表示方法（词嵌入）与现代机器学习模型相结合时，自动化文本分类任务的得到了很大程度的提高。然而，在训练词向量表示不足方面，此类方法的效能尚未经过评估。在模式识别、图像分析和文本分类方面，卷积神经网络已被证明非常有效 [10]。

## 相关工作

我们研究系统的目标是通过从 `Twitter` 收集数据并根据关键词进行处理，分析随时间变化的用户情绪。`Fasttext` 是 `Facebook` 开发的一种文本分类工具，它通过将推文尽可能快速准确地分类为以下心理状态：愤怒、宽慰、无聊、快乐、仇恨、有趣、爱意、惊讶、热情和空虚。`FastText` 是一种流行的自然语言处理（`NLP`）库，用于表示和分类文本。跨越时间的情感分类揭示了普通大众的状态以及其演变情况 [11]。

提出了一种使用 `FastText` 和多尺度 `DCNN`（深度卷积神经网络）的文本情感分类模型，以增强中文文本情感分类的有效性。首先使用 `FastText` 模型构建文本向量矩阵。之后，使用多尺度滤波器从内容向量矩阵中提取多个特征图。最后，将合并的特征图输入 `DPCNN`（深度池化卷积神经网络）模型进行情感分析。使用中文情感挖掘语料库（`ChnSentiCorp`）进行测试，通过多系列测试比较了使用所提模型与其他技术进行文本情感分类的准确性 [12]，结果证明了其效能。

在这项研究中，我们在一个名为 `fastText` 的框架内引入了卷积神经网络（`CNN`）的使用。首先，我们使用 `fastText` 生成的词向量表示来馈 `CNN`。`FastText` 的目标是利用表示距离创建一个单个单词的自动模型。这允许将参数设置在良好的 `CNN` 点上，从而提高了神经网络在此类设置下的有效性。其次，我们开发了一个专门为情感分析定制的卷积神经网络结构。在这一架构中，我们将两组卷积层与池化层相结合。据我们所知，这是首次基于 `fastText` 和 `CNN` 的 9 层设计和架构模型被评估句子情感。为了使我们的模型更精确、更具适应性，我们采用了归一化（`Normalization`）和丢弃（`Dropout`）方法以及线性整流单元（`ReLU`）回归。对于该实验，我们使用了一个公开数据集，由电影评论摘要组成，标记为“负面”、“轻负面”、“中性”、“中度积极”或“积极”，以评估我们的方法。凭借 96.4% 的测试准确率，我们的 `ReLU` 配对网络在该数据集上的表现优于其他神经网络模型 [13]。

在 `FastText` 场景下，应用 90% 训练和 10% 测试的划分并包含扩展的逻辑回归，在模型改进场景中产了 71.8% 的效率。通过在正负面情感上使用优化模型，我们发现 5 月至 9 月的 `BMRI` 变化相关性最强 [14]。

在实验中，我们探讨了如何使用 `CNN` 模型解决文本分类问题。我们使用了公开数据集——`Ag News`、`Amazon Full & Polarity`、`Yahoo Question Yelp Full & Polarity`——利用流行的词嵌入方法 `Fast Text` 来训练模型。模型还包含了关于美国航空公司的推文。`Fast Text` 作为嵌入被证明是一种有前景的方法 [15]。

## 提出的工作

## 系统模型

图 (1) 展示了我们建议将文本分类为有害、无毒或模糊的概述概念。

![](img/5e4d8ef2afa52a840428106580e194_65_0)

**图 (1)** 用于文本分类的 `FastText` 与 `CNN`。

### FastText 模型

尽管训练模型的时间投入较高，但网络在广泛的 `NLP` 相关活动中表现出色。在 2016 年，`Facebook` 研究人员发布了 `FastText` 工具，可用于词向量和文本分类。图 (1) 显示了 `fastText` 的整体结构。

`fastText` 模型的输入部分与标准的词袋模型不同，它将句子的 `n-gram` 特性作为输入，并匹配句子中每个音节的表示。对于标准的词袋模型，例如“I like basketball”，将包含“I”、“like”、“play”和“basketball”，而 `fastText` 是模型的基础。除了上述之外，还实现了 `n-gram` 特性。通过使用 `n-gram` 特性，`FastText` 能够比以前产生更精确的句子表示。

- `Dim` - 决定 `fastText` 设置的向量中的单词数。

在多分类问题中，激活函数通常是 `Softmax` 函数，它返回给定输入属于 `k` 个类别之一的概率。当子类别数量很多且数据存在类别不平衡时，分层 `Softmax`（`hierarchical Softmax`）表现非常出色。与扁平的列表状结构不同，这里的类别以树形分布的形式呈现。哈夫编码树是分层 `Softmax` 层结构的基础，较短的树表示更常见的类别，较长的树表示较不常见的类别。通过对各个分支的节点进行深度优先搜索，来确定特定测试与某类匹配的概率。结果是概率较低的分支（或类别）可能会被消除。因此，与传统方法相比，大量类别数据的分类时间大幅降低。

多项式逻辑回归是 `softmax` 回归的另一种名称。`softmax` 回归的训练集可以表示为 (1)。

$$(x^{(1)}, y^{(1)}), ..., (x^{(m)}, y^{(m)}), y^{(i)} \in \{1, 2, ..., K\}$$ (1)

模型以 $x$ 为输入生成的 `K` 维向量的每个成员反映了 $x$ 对应于当前分类的概率。特别是，我们可以模型表示为 $h_{\theta}(x)$，如 (2) 所示。
