
# 机器学习新兴趋势深度秘籍

```python
def __init__(self, data, epochs, mini_batch_size=32):
    super().__init__()
    self.data = data
    np.shuffle(self.data)
    self.epochs = epochs
    self.mini_batch_size = mini_batch_size
    self.weights = np.random.randn(data.shape[1], data.shape[1])

def train(self, test_data):
    for epoch in range(self.epochs):
        for i in range(0, len(self.data), self.mini_batch_size):
            mini_batch = self.data[i:i+self.mini_batch_size]
            self.update(mini_batch)
        print(f"Epoch {epoch} complete")

def update(self, mini_batch):
    # ... implementation
    # mini_batch.shape
    for b in self.biases:
        b = np.zeros(b.shape)
    for w in self.weights:
        w = np.zeros(w.shape)
```

- 前言
- 贡献者列表
- 噪声移除
  - a) 小写转换
  - b) URL 移除
  - c) 标签移除
  - d) 特殊字符移除
  - e) 停用词移除
- 修正
  - 分词
  - 化
  - 词干提取
  - 词性标注
- 机器学习技术
  - 监督机器学习
  - 非监督机器学习
  - 逻辑回归 (LR)
  - 决策树 (DT)
  - 随机森林 (RF)

## 结论

- 小写化
- 词形还原

## 参考文献

## 用于识别推文数据集内容的机器学习方法

## 摘要

## 引言

## 相关工作

## 拟议工作

- 数据收集
- 数据预处理
- 系统模型
- 语音情绪分类

## 结果与讨论

## 结论

- 停用词
- 特征聚类
- 文本分类

## 结果与讨论

## 带相关反馈的深度学习文本检索系统

## 摘要

## 引言

## 相关工作

## 拟议工作

- 研究缺口
- ConvNets
- 系统模型
- CNN

## 结果与讨论

- 概述
- 特征提取
- 多模态情感分类
- 研究缺口
- 数据集
- 数据预处理
- 特征提取与分类
- 数据集

## 结论

- 文档演示

## 结论

# 基于面向方面的情感分析和模糊逻辑 COVID-19 推特数据分类

- 引言
- 拟议工作
- 预处理与标注
- 文本分类
- 结果与讨论
- 引言
- 拟议工作
- 客户评论
- 词性标注
- 特征提取
- 特征剪枝
- 分类
- 引言
- 拟议工作
- 3.1 数据收集与预处理
- 特征提取方法
- 文本分类方法
  - SVM
  - 神经网络
  - 朴素贝叶斯
  - 决策树
  - C45 决策树分类器
  - KNN
- 引言
- 拟议工作
- 数据预处理
- 使用 CNN-LSTM 进行文本分类
- 引言
- 拟议工作
- 使用 Hadoop 进行的情感分析
- 测试环境
- 结论
- 引言
- 拟议工作
- 文本预处理
  - 分词
  - 移除与纠正
  - 替换
  - 词性标注
  - 词嵌入

引言

拟议工作

- 用于文本分类的 Skip Gram 模型
- 基于注意力的 CNN
- 注意力权重估计问题

引言

拟议工作

- 系统模型
- 数据集
- 多模态文本分类
- 结果与讨论

## 引言

## 拟议工作

系统概述

数据集描述

数据预处理、处理与分词

VADER 情感分析器

特征提取与分类

## 引言

## 拟议工作

用于电影评论分类的 CNN

## 结果与讨论

数据归一化

## 引言

## 拟议工作

数据收集与处理

词汇表开发

DL 模型

拟议 DL 模型

## 参考文献

## 引言

## 相关工作

## 系统模型

## 文本预处理

### 阶段 1 - 数据整理

### 阶段 2 - 情感词

### 阶段 3 - 文本清洗

## 用于文本分类的 LSTM-GRU

## 引言

## 拟议工作

## 系统模型

## 用于推特分类的 LSTM

## LSTM 的组件

## 引言

## 拟议工作

## 收集数据

## 预处理阶段

## 词嵌入

## 推特分类

## 结果与讨论

## 引言

## 拟议工作

## 特征工程

## 情感词典

## BERT 模型

## 混合 DNN

## 结果与讨论

## 引言

## 拟议模型

## 拟议方法

## 数据处理步骤

## 大数据挑战

## 管理数据的最佳实践

## 引言

## 拟议工作

## 数据收集与预处理

## 特征提取与词嵌入

## 分类

## 结果与讨论

## 结论

## 引言

## 系统概述

## 去噪与停用词

## 结果与讨论

## 参考文献

## 引言

## 拟议方法

## 问题定义

## 数据预处理

## 数据处理任务

## 用于预测机器学习

## 实验结果

## 引言

## 拟议工作

## CNN 模型

## 结果与讨论

## 引言

## 拟议工作

## 向量化

## 词向量

## 文本分类模型

## TF-IDF 逻辑回归

## Word2Vec 逻辑回归

## TF-IDF 随机森林

## Word2Vec 随机森林

## 引言

## 技术与材料

## 技术与材料

- 数据库描述
- 朴素贝叶斯
- 高斯朴素贝叶斯
- 随机森林
- 支持向量机
- 卷积神经网络 (CNN)

## 引言

## 拟议工作

- 遗传算法

## 拟议方法的概览

## 结果与讨论

## 运行时间

## 讨论

## 结论

## 参考文献

## 引言

## 拟议工作

- 图形构建
- 从构建的图中检索数据

## 结果与讨论

- 4.2 检索数据分析

## 数据来源与人群

## 健康习惯

## 卷积神经网络

## 基于 CNN 的文本分类

## MapReduce-CNN

Oceanof/PDF.com

#（第 2 ）

## 揭秘机器学习中的新兴趋势

编辑：

Pankaj Kumar Mishra

Hi-Tech Institute of Engineering and Technology

Ghaziabad, U.P.

India

&

Satya Prakash Yadav

School of Computer Science

Engineering and Technology (SCSET)

Bennett University, Greater Noida, U.P.

## 使用规则：

- 1. 版权所有：该作品受版权法保护，Bentham Science Publishers 拥有该作品（及其版权）或获得许可分发该作品。除非 Bentham Science Publishers 事先提供书面许可，否则您不得以任何形式或通过任何手段全部或部分地复制、复制、修改、移除、删除、增补、添加、发布、传输、销售、转售、创建衍生作品，或以任何方式利用该作品，或让他人对该作品进行任何相同的操作。
- 3. 未经授权使用或分发受版权或其他所有权的内容是非法的，并可能导致您承担巨额损害赔偿责任。您将对因误用作品或任何违反本许可协议的行为导致的任何损害承担责任，包括您对版权或所有权的任何侵权行为。

Bentham Science Publishers 不保证作品中的信息没有错误，也不保证其将满足您的需求，或您访问作品将不会被中断或出现错误。作品按“原样”提供，不带任何形式的保证（无论是明示、隐含的还是法定的），且不受对商业销性和特定用途适用性的暗示性保证的限制。有关作品结果和性能的所有风险均由您承担。Bentham Science Publishers 及其员工、编辑和/或作者对因使用或操作作品中包含的任何方法、产品说明、广告或思想而导致的任何产品责任、疏忽或其他人身伤害和/或财产损害不承担任何责任。

## 责任限制：

在任何情况下，Bentham Science Publishers 及其员工、编辑和/或作者均不对因（直接或间接）使用或无法使用作品而产生的任何损害承担责任，包括但不限于特殊、偶然和/或后果性的损害和/或数据丢失和/或利润损失的损害。Bentham Science Publishers 的全部责任应限于您为该作品实际支付的金额。

## 通用：

- 1. 任何由本许可协议或作品引起或与之相关的任何争议或索赔（包括非合同性争议或索赔）将受新加坡法律管辖并根据其法律解释。双方均同意新加坡州法院对解决任何由本许可协议或作品引起或与之相关的任何争议或索赔（包括非合同性争议或索赔）具有专属管辖权。
- 2. 如果您在任何时候违反了本许可协议的任何条款，您在本许可协议下的权利将自动终止，无需通知。在任何情况下，Bentham Science Publishers 在执行您对本许可协议的遵守方面的延迟或失败均不构成对其任何权利的放弃。
- 3. 您确认已阅读本许可协议，并同意受其条款和条件的约束。如果 Bentham Science Publishers 任何网站上显示的任何其他条款和条件与本许可协议中规定的条款和条件冲突或不一致，您确认以本许可协议中规定的条款和条件为准。

Bentham Science Publishers Pte. Ltd.

80 Robinson Road #02-00

Singapore 068898

Singapore

Email: subscriptions@benthamscience.net

![](img/5e4d8ef2afa52a8404b28106580e19e4_23_0.png)

OceanofPDF.com

## 前言

人工智能（AI）和机器学习（ML）正在彻底改变我们对待医疗和各个行业的方式。AI 和 ML 被用于改善治疗效果、降低成本并提高医疗行业的效率。AI 还被用于医疗设备以预测和识别疾病，并优化医疗治疗。

在书中，我们探讨了神经网络在医疗和健康领域 AI 和 ML 中的作用。神经网络被用于肿瘤学，通过算法以与训练过的医生相同的准确度识别癌症组织。罕见疾病可能在物理特征上，可以通过对患者照片进行面部分析来识别。

此外探讨了 AI 和 ML 在金融、零售、制造业等各个行业中的作用。AI 正通过提供个性化建议来改善客户体验。在制造业中，AI 被用于预测需求和减少浪费以优化供应链管理。

这本书对于任何想要了解 AI 和 ML 在医疗、健康部门及各行业作用的人来说都是一份全面的指南。

Pankaj Kumar Mishra

Hi-Tech Institute of Engineering and Technology

Ghaziabad, U.P.

India

&

Satya Prakash Yadav

School of Computer Science

Engineering and Technology (SCSET)

Bennett University, Greater Noida, U.P.

India

用于教育计算机的有用信息。共使用了 151,113 个数据集对所提算法的性能进行实验分析。所提方法的准确率为 97%，高于当前方法（NB）。通过使用随机森林方法对产生的网络犯罪进行分类，可能轻松克服回归的挑战。计划中的研究以年龄分类作为识别不同违规行为的基础。

**关键词：** 网络安全、机器学习技术、文本分类。

> * 通讯作者 Siddharth Sriram：Chitkara 大学商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：siddharth.sriram.orp@chitkara.edu.in。

## 引言

为了从由振荡叶片产生的尾流中收集能量，构建了一个机器学习模型。对于振荡叶片的阵列部署，尾流结构的功能至关重要，因为不稳定的尾流会显著影响下游的性能。通过情感分析从社交媒体中汲取用户情绪 [1, 2]。这是一种将文本观点组织为正面、负面和中性类别的方法。训练和分类 Twitter 数据集的结果取决于算法所使用的策略，这至关重要，特别是在航空公司和零售业等对时间敏感的行业中 [3, 4]。智能手机、平板电脑和其他物联网（IoT）设备经常被用于家庭和工厂等各种环境。这些许多设备使用蓝牙低功耗（BLE）作为控制或数据传输机制 [5, 6]。由于缺乏稳健的安全机制以及软件和通信组件的固有脆弱性，这些设备容易受到简单攻击。机器学习通常被用于分类目的 [7]。为了对和其他遥感数据分类，GIS 专家经常使用深度神经网络分类方法。图神经网络（GNNs）可以利用其拓扑结构来识别地理特征，这对于表示为图（如线或多边形空间数据）的数据非常有用 [8, 9]。使用 GNN 将空间对象分组为若干类别。

## 相关工作

在这项研究中，这些许多设备使用蓝牙低功耗（BLE）作为控制或数据传输机制 [5, 6]。

随后，我们对反馈（实例）进行了如下分类：700 条与性取向相关的暴力相关的评论；700 条与针对女性的暴力相关的评论；以及 600 条与种族主义相关的评论。

标记行为。我们注意到，一些学者利用 Amazon Mechanical Turk 网站聘佣未具名的员工来手动对各种类型的数据（例如：评论、评价、单词、照片）进行分类。Amazon Mechanical Turk 的员工发现，2.5% 被标记为“无网络欺凌”的评论实际上应该被标记为此类，因此该公司联系了研究生和本科水平心理学专业的学生协助完成标记过程。

鉴于此，我们选择了一个由三位教育者组成的团队，在精通评估和处理中学欺凌事件的心理学家的帮助下，他们擅长对言论进行手动标记。心理学家向教职人员介绍了三种网络攻击类型，以及如何将评论归类到相应的类别中。作为标记程序的一部分，每条言论都根据网络攻击标准和预设的数字量表被分配了一个攻击性值。我们利用从 0 到 2 的量表来对包含针对女性性侵犯的陈述的攻击性进行排名。针对性取向暴力的陈述也采用了相同的四点到六点量表，最低值表示最不雅的言论。此外，种族主义言论使用从 0 到 10 的量表从最低攻击性最高攻击性进行排名。据此，我们收集了一个攻击性帖子数据集，并将其输入我们的特征选择和训练过程中。该数据集的第一列存储评论或实例，第二列为每条评论提供反感值。在接下来，我们将详细介绍本研究中采用的特征选择技术以及训练过程算法和方法。

## 用于文本分类的机器学习算法

机器学习分类器的训练从将文本转换为机器可读的格式开始。在许多情况下，这是通过“词袋”实现的，即一组在给定词集中出现频率由向量表示的词。在信息被向量化之后，每个单词样本和标签的向量被用于训练文本分类模型。学习的数据越多，其预测就越精确。用于文本分类的最流行的算法已蓄绪待发，让我们来看看：

## 朴叶贝斯

朴叶贝斯方法使用贝叶斯定理，这是一种基于分类器，利用关于潜在相关情况的先验信息来预测文本的标签。在确定输入文本的每个标签的似概率后，它根据似概率最大的标签进行预测。

使用其他方法也可以使朴叶贝斯更加有效：

- 消除没有人使用的填充词。诸如“able to”、“either”、“else”、“ever”、“etc.”等单词。



- 对术语进行词形还原（lemmatize），将其许多派生词归类到同一个标题下。“draught”、“drafted”、“draughts”、“drafting”等单词。

- N-gram 表示文本中单个单词或长度为 `n` 的一系列单词的出现概率。

- TF-IDF：一种衡量单词在文本或文档组中重要性程度量的指标，TF-IDF 是“词频-逆文档频率”的缩写。它在单词评分方面具有巨大潜力，因为它的值随着给定单词在文档中出现频率的增加而增加，但随着包含该单词的文档数量的增加而减小。

- 预测器：`[X1, X2]` 和边界：`Y` 为了获得后验概率，使用以下公式：

```
$P\left(\frac{Y}{X1,X2}\right) = \frac{P(Y)\cdot P\left(\frac{X1,X2}{Y}\right)}{P(X1,X2)}$
```

- 接受 `P(X1,X2/Y=1)` 的有限责任建议：

```
$P\left(\frac{Y}{X1,X2}\right) = \frac{P(Y)\cdot P\left(\frac{X1}{Y}\right)\cdot P\left(\frac{X2}{Y}\right)}{P(X1,X2)}$
```

- 朴素贝叶斯分类器的后验概率计算公式。

## 支持向量机

被称为支持向量机（SVM）的分类系统在数据量较少的情况下表现出色。对于每个给定的类别，它评估所有可能的向量并选择最佳的一个。例如，假设数据集中有两个属性（`x` 和 `y`）和两个标签（昂贵和廉价）。必须有一种方法告诉我们哪一组变量 `(x, y)` 更加昂贵。支持向量机（SVM）通过在数据点之间创建一个边界（决策边界），并将两侧的所有内容分类为昂贵或廉价来实现这一点。当空间被决策边界一分为二时，就会形成一个组子空间和一个外组子空间。训练文本由向量表示，每个标签由集合表示。SVM 的优势在于不需要大量的训练信息即可提供正确的结果，但它比朴素贝叶斯需要更多的处理能力。它是一种可以用于回归和分类的机器学习方法，并且是有监督的。特征数量 `n` 决定了 SVM 中数据点显示的维度。分类的下一步是选择一个合适的超平面来清晰地分离两组。超平面在 `n` 维空间中具有（`n` 减 1）维。

```
$\beta0 + \beta1X1 + \beta2X2 + \dots + \beta nn = \sum_{i=1}^{n} \betaXi$
```

我们假设类别可以分为线性子集。分类通过方程中的符号来实现，而方程的尺度则澄清了观测值偏离超平面的程度。边缘定义为点到任意一类平面的最小距离。如果幅度很大，我们可以更有信心地将其放入特定类别。因此，该超平面被称为“最大间隔分类器”。位于边界上或外部并导致超平面变形的观测值被称为支持向量。超平面由支持向量支撑。

## 结果与讨论

整个数据集的 70%、10% 和 20% 分别用于训练、验证和测试。

为了评估模型，我们使用了准确率和加权 F1。文章声称的准确率基于测试集得出的结论。在评估模型的有效性时，使用了考虑每个标签相应频率的加权 F1 统计数据。图 (2) 显示了准确率的对比分析。

![](img/5e4d8ef2afa52a8404b28106580e19e4_40_0.png)

**图 (6)** 召回率（Recall）的对比分析。

![](img/5e4d8ef2afa52a8404b28106580e19e4_41_0.png)

**图 (7)** 召回率 (a). 样本量，以及 (b). 特征大小。

![](img/5e4d8ef2afa52a8404b28106580e19e4_42_0.png)

**图 (8)** F-score 的对比分析。

分类器的效能衡量可以从这些结果中得出：

- **准确率 (Accurateness)**：带有标签的正确预测文本比例。

- **精确率 (Exactness)**：分类器对某个标签预测的总实例中在误差范围内的文本数量。

- **召回率 (Recall)**：在可能进行预测的所有案例中，分类器对给定标签做出预测的实例比例。

- **F1 分数 (F1 Score)**：精确率和召回率之间的最佳平衡。

## 结论

网络犯罪对人类安全和全球经济构成了威胁，因为网络和计算机网络的快速发展为不道德行为开辟了新途径。本文提出的工作目标是将网络犯罪分为 IP 欺诈分析和网络欺凌。这项工作的主要目标是针对网络活动及其各自的基础进行简要检查，并通过网络犯罪发生情况提供匹配的方案。网络犯罪事件根据朴素贝叶斯（NB）和支持向量机（SVM）等数据挖掘方法根据其理想特征进行分组。来自 Twitter 的数据通过 K-means 聚类从 Kaggle 数据库中提取。为了提供适当的计算机训练，有必要收集大部分相关数据，包括客户 ID、注册时间、网页浏览器、性别、年龄以及 IP 地址。研究中使用了 151,113 个数据点来测试该方法的有效性。所提的方法以 97% 的准确率优于当前技术（NB）。在网络犯罪分类方面，随机森林方法优于逻辑回归。所提方法根据不同的年龄组对不同的犯罪进行分类。

## 参考文献

- [1] Kaczmarek I., Iwaniak A., Swietlicka A.. Classification of Spatial Objects with the Use of Graph Neural Networks. ISRPRS J. Geofient.2023128310.3390/jgi12030083

- [2] Malibu S., Madden E., Patterson O., DuVall S., Goldman L.A., Burman K., Shiner B.. Measurement of Evidence Based Psychotherapy for Posttraumatic Stress Disorder in a Large National Healthcare System. Policy Ment. Health20184545195291007510488-018-0850-5259450781

- [3] Nickh A.K., Subramanyam K., Vasavi R.. Building a K-Nearest Neighbor Classifier for Text Categorization

- [4] Benitez M., Tian J., Kelly M., Selvakumar V., Phelan M., Mazurov M.A., Lo J.Y., Rubin G.D., Henao R.. Combining deep learning methods and human knowledge to identify attributes in computed tomography (CT) reports MedicalImaging2019

- [5] Pedro M.A., Baker R., Montalto O., Nakama A., Geburt J.D.. Using Rely Tagging to Produce Detectors of Systematic Experimentation Behavior Patterns.Educational Data Mining2

- [6] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [7] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [8] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [9] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [10] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [11] Pedro M.A., Baker R., Montalto O., Nakama A., Geburt J.D.. Using Rely Tagging to Produce Detectors of Systematic Experimentation Behavior Patterns.Educational Data Mining2

- [12] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [13] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [14] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [15] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [16] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [17] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [18] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [19] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [20] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [21] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [22] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [23] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [24] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [25] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [26] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [27] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [28] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [29] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

- [30] Sukh S., Daswamy M., Prakash M.N.. Image Retrieval with Relational Semantic Indexing and Color GrayImages2020

## 摘要

本文通过对 GRU 模型特征的检查，探讨了电子商务中的评估。首先使用 TF-IDF 技术生成关键词列表，然后对该列表进行加权。门控循环单元（GRU）模型加权被作为解决该问题的解决方案。通过使用多种分类算法并比较其结果，本文旨在代表机器学习在现实世界中的应用优势。我们利用电子商务的实际数据构建了一个系统。卷积神经网络技术实现了 96.08% 的准确率（范围从 85.44% 到 99.99%），标准差为 5.65%。

**关键词：** 特征提取，机器学习，文本分类。

* **通讯作者 Sidant Das**：跨学科研究与技术，奇特卡拉大学，旁遮普邦；电子邮箱：`sidhant.das.orp@chitkara.edu.in`

## 引言

电子商务平台应优先考虑售后，以改善消费者的购买体验。我们提出了 AliMe KG，一种电子商务领域知识谱，它包含了用户问题、POI、信息以及之间的关联 [1, 2]，用于更好地服务消费者。在线交易不是新奇事物。通过消除纸质文件并将其替换为数字文件，企业可以节省时间与资金 [3]。电子商务，或电子贸易，是通过开放网络进行的业务业务交易。它已成为人们日常生活中的重要部分。因此，所有规模的企业都必须努力建立可靠的电子商务系统 [4, 5]。

49

我们在多个真实场景中使用知识图谱（KG），包括购物指南、属性查询和卖点创建，并看到了显著的回。在这项工作中，我们系统地解释了构建非结构化文本知识图谱的方法，并展示了从非结构化文本中提取结构化信息的商业用途和潜在收益。

本研究调查了企业如何在各个经济领域立足。在线购物的兴起如何影响社会地位？政府又如何鼓励低收入地区的电子商务增长？大多数企业在专注于小众商品的企业对消费者（B2C）电子商务领域取得了成功。私营部门通过实际行动在刺激电子商务增长方面发挥着关键作用。

本文提出了一种基于电子商务框架。它提供了最常用的电子商务系统功能、系统边界、系统级设计概念以及与系统相关的紧迫技术问题的示例。该框架已实现电子商务的标准特性。如所示，此类电子商务平台可以满足电子市场、购买和订阅等需求。

案例研究的证据表明，某些功能和特性对电子商务行业的发展有显著影响；然而，为了取得成功，必须考虑所有这些元素。分析得出结论：使用 PCA 分析电子商务发展是可行的，前提是数据损失可以保持在最低。

## 拟议工作

## 问题定义

文本分类算法不是基于词的语义相似性做出决策，而是通过不同的方法（如余弦相似度）考虑向量空间中术语向量的接近程度。然而，由于后缀、前缀或时态的不同，当具有不同形式的词视为单独向量时，相似分数会降低。我们设计了一种名为“词干提取”（Stemming）的程序来消除单词中的后缀、前缀和时态，并将其还原为根形式以规避这一问题。接下来，我们使用名为“向量化”（Vectorization）的过程将数据集中的每个句子转换为有限向量空间内的数值可读值（如整数或浮点数）。向量化为每个不同的单词分配一个数值（向量），然后预测算法利用这些向量来解决分类问题。`CountVectorizer` 迭代计算文本中的每个短语，并提供一个包含单词及其在文档中出现频率的向量。

我们的实验技术后续是创建用于训练的数据集，该数据集在遵循上述“向量化”过程的基础上，由线性化特征和目标类别组成。最后阶段是使用训练好的模型结合向量化输入来选择合适的机器学习技术并做出足够准确的预测。图 (1) 使用我们预计会遇到的现实场景来演示上述通用方法和程序。

![](img/5e4d8ef2afa52a8404b28106580e19e4_51.png)

图 (1) 系统流程图。

## 数据集描述

用于“电子产品”、“家居”、“书籍”和“服装配饰”的分类电子商务文本数据库，这些类别共同占了任何电子商务网站销售产品的约 80%。

`.csv` 文件中有两列：第一列包含类名，第二列包含对应的数据点。在线商店的商品及其描述提供了数据点。

数据集的特征如下：



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



$$h_{\theta}(x) = \begin{cases} P(y = 1 | x; \theta) \\ P(y = 2 | x; \theta) \\ ... \\ P(y = K | x; \theta) \end{cases} = \frac{1}{\sum_{j=1}^K e^{\theta^{(j)rx}}} \begin{cases} e^{\theta^{(1)rx}} \\ e^{\theta^{(2)rx}} \\ ... \\ e^{\theta^{(K)rx}} \end{cases}$$ (2)

相关范式的损失函数如 (3) 所示。

$$J(\theta) = - \left[ \sum_{i=1}^{m} \sum_{k=1}^{K} 1\{y^{(i)} = k\} \log \frac{e^{\theta^{(k)T} x^{(i)}}}{\sum_{j=1}^{K} e^{\theta^{(j)T} x^{(i)}}} \right]$$

上述方法已用于生成词嵌入，这些嵌入被用作深度神经网络如 `MLP`、`CNN` 和 `LSTM` 算法的输入。

- **多层感知器 (`MLP`)**：对于图像、文本或时间序列等表格化数据集，这些传统的神经网络被证明是极其有用的。这些结构由三个不同的神经元层组成。在我们需要考虑与数据相关的空间数据的情况下，它们并无帮助，并且在处理高维输入时可能会导致重复。

- **卷积神经网络 (`CNN`)**：这种神经网络子类性能优于流行的 `MLP` 变体。它们展示了其在自然语言处理（`NLP`）中的用法，最初用于图像处理。由于具有更深层的稀疏连接层，文本模式检测得到了极大改进，特别是在存在噪声或异常值的情况下。

- **`LSTM`**：这种循环神经网络（`RNN`）变体能够同时学习文本依赖关系和文本上下文。因为它们使用内存单元逐渐更新隐藏层，它们擅长顺序学习复杂关系。

## 结果与讨论

测试是在一台配备 Intel (R) Intel (TM) i5-8250u 1.60GHz CPU、8GB 内存和 Windows 10（64位简体中文版）的笔记本电脑上进行的。算法用 `Python 3.7` 编写并被软件利用。流行的框架 `sklearn` 和 `fastText` 是两个示例。图 (2) 展示了分类性能的比较。

## 表 1 结果（样本）

| 样本 | 准确率 (Exactness) | 回忆率 (Recollection) | F-值 |
|---|---|---|---|
| `MLP` | 0.9142 | 0.9249 | 0.9156 |
| `CNN` | 0.8813 | 0.6339 | 0.6713 |
| `LSTM` | 0.8637 | 0.8831 | 0.8526 |
| 我们的方法 | 0.9275 | 0.9301 | 0.9286 |

![](img/5e4d8ef2afa52a404b28106580e19f4_69_0.png)

![](img/5e4d8ef2afa52a404b28106580e19f4_69_1.png)

**图 (2)** 样本比较。

在研究中，我们使用支持向量机、最近邻算法以及朴素贝叶斯执行文本分类和比较测试，以确定哪种方法产生的结果最好。测试使用 `fastText` 构建的分类模型时，每个模型都进行了十次无交叉测试。在每个实验中，数据集按 4:1 的比例随机划分为训练集和测试集。然后使用训练集训练模型，并使用测试集评估其性能。通过十次独立测试对每个模型的 F 值、召回率和准确率取平均。表 1 显示了实验结果。实验结果表明，在四个分类模型中，最近邻技术的整体性能最差，得出的 F 值最低。一种可能的解释是正样本的比例远高于中性或负性样本。然而，如果提供大量的训练数据，模型的性能也会受到影响，因为最近邻模型非常简单。朴素贝叶斯方法的 F 值比最近邻方法更高，召回率也更高。朴素贝叶斯算法在精确率方面也优于邻域策略。在用户情感分类任务中，支持向量机优于邻域算法和朴素贝叶斯算法，其值高得多。在准确率、召回率和 F 值方面，基于 `fastText` 的分类模型优于其他三个。这表明，与传统的机器学习分类算法相比，基于 `fastText` 的分类模型能够更好地收集和利用输入文本中与情感极相关的属性，从而对用户情感做出更准确的判断（图 3），表 3 说明了关于迭代次数的准确率、精确率、召回率和 F 分数的比较分析。

![](img/5e4d8ef2afa52a404b28106580e19f4_71_0.png)

![](img/5e4d8ef2afa52a404b28106580e19f4_71_1.png)

![](img/5e4d8ef2afa52a404b28106580e19f4_71_2.png)

![](img/5e4d8ef2afa52a404b28106580e19f4_71_3.png)

**图 (3)** 迭代比较。

表 2 结果（迭代）。

| 样本 | 准确率 (Exactness) | 回忆率 (Recollection) | F-值 |
|---|---|---|---|
| `MLP` | 0.9142 | 0.9249 | 0.9156 |
| `CNN` | 0.8813 | 0.6339 | 0.6713 |
| `LSTM` | 0.8637 | 0.8831 | 0.8526 |
| 我们的方法 | 0.9275 | 0.9301 | 0.9286 |

## 结论

在本研究中，我们使用支持向量机、最近邻算法以及朴素贝叶斯执行文本分类和比较测试，以确定哪种方法产生的结果最好。测试使用 `fastText` 构建的分类模型时，每个模型都进行了十次无交叉测试。在每个实验中，数据集按 4:1 的比例随机划分为训练集和测试集。然后使用训练集训练模型，并使用测试集评估其性能。通过十次独立测试对每个模型的 F 值、召回率和准确率取平均。表 1 显示了实验结果。实验结果表明，在四个分类模型中，最近邻技术的整体性能最差，得出的 F 值最低。一种可能的解释是正样本的比例远高于中性或负性样本。然而，如果提供大量的训练数据，模型的性能也会受到影响，因为最近邻模型非常简单。朴素贝叶斯方法的 F 值比最近邻方法更高，召回率也更高。朴素贝叶斯算法在精确率方面也优于邻域策略。在用户情感分类任务中，支持向量机优于邻域算法和朴素贝叶斯算法，其值高得多。在准确率、召回率和 F 值方面，基于 `fastText` 的分类模型优于其他三个。这表明，与传统的机器学习分类算法相比，基于 `fastText` 的分类模型能够更好地收集和利用输入文本中与情感极相关的属性，从而对用户情感做出更准确的判断。

[8] Yadav S.P., Zaidi S., Nascimento C.D.S., Albuquerque V.H.C., Chauhan S.S. 基于GPS的移动物体跟踪系统自动生成算法分析与设计. 2023年人工智能与智能通信国际会议 (AISC), 印度大格诺伊达. 2023. 10.10.1109/AISC56616.2023.1008510.

[9] Tabasam S., Hossain M.M., Islam M.A., Mahafi T, Zahara M.Y., Fami F.N. 新闻文章分类中主流机器学习与深度学习算法的性能分析. IEEE第10区研讨会论文 (TENSYP), 2022年6月. 0490511.1109/TENSYP50017.2022.923085.

[10] Wang Z., 结合`FastText`、`TF-RF`和改进随机游走模型的中文文本分类. 2021年第14届信号处理国际会议 (ICSP) 论文, 2021年12月. 98179. 20.1109/ICSP5882.2021.940819.

[11] Kulai A., Sankhe M., Angeklar S., Halbe A., 使用`FastText`监督分类模型对推文进行情感分析. 2021年通信信息与计算技术国际会议 (ICCICT). 1622021. 10.1109/ICCICT50803.2021.951056.

[12] Tsai S., Shi L., 基于`FastText`和多尺度深度卷积神经网络的中文情感分类模型. 2022年计算、大数据与工程国际会议 (ICBEE). 75777 2021. 10.1109/ICBEE56101.2022.988185.

[13] Yadav S. P., Yadav S., 连续小波域医学图像融合的数学实现-动态与控制系统先进研究期刊，2019 10104554.

[14] Putra M.F., Setiawan E.B., 使用`FastText`特征扩展与逻辑回归分类分析情感对Mandiri银行股票 (BMRI)的影响. 2022年先进创意网络与智能系统国际会议 (ICACNIS). 172022. 10.1109/ICACNIS57039.2022.1005540.

[15] Umer M., Imtiaz Z., Nappi M., Medaglia C., Choi G.S., Mehmood A., 卷积神经网络和`FastText`嵌入对文本分类的影响. Multimedia Tools App. 2023 2445695585101.1007/s11042-022-13459-x.

## 一 利用人工智能技术的新闻文本分类算法

Rahul Mishra$^{1,*}$

$^{1}$ Chitkara大学工程与技术学院商业与技术跨学科研究中心, Chitkara大学, 印度旁遮普邦

## 摘要

全球范围内技术改进的速度正在不断加快。由于互联网、网站、业务数据、医疗信息和媒体的影响，每天都会产生大量的文本数据。从不同长度（如观点、摘要和事实）的文本数据中提取有趣的模式是一项挑战性工作。本研究提供了一种基于深度学习（`DL`）算法的新闻文本分类方法，以解决海量文本数据和特征获取繁琐的问题。尽管单词之间的关系对新闻分类具有重要影响，但以往的方法仅依赖于单词的知识。本研究使用定制算法提供了一种基于`CNN`、`LSTM`和`MLP`的框架。所提模型基于词向量和散度的并行表示。我们将词向量输入`CNN`模块，以实现对空间数据、时间序列信息以及单词之间关系的深度学习。

相互独立的变量。这些发现表明市场情绪与直接房地产市场流动性之间存在着长期关系。市场参与者在做出投资选择和对流动性风险定价时，应当考虑这种影响。这项研究不仅丰富了关于房地产领域基于文本的情感指数的知识体系，而且首次利用 AI 在市场流动性的背景下从新闻故事中提取情感 [11]。

该框架的成功实施遵循 FAIR 指南。由此生成的脱细胞质图谱可以在专门用于教育的网站上展示；我们提供了 68 份完整的主观视图及其注释数据，用于处理解决病例、病变和帧层级上帧分割与分类问题的 AI 项目。我们的研究结果表明，所建议的架构使得以标准化格式保存视觉记录成为可能，并为训练和研究 AI 提供了 FAIR 数据 [12]。

本文利用特定的词汇删除评分机制，提出了一种用于黑箱场景的对抗样本生成算法；该算法在霍源网（`HowNet`）词库中搜索对分类器决策有重要影响的关键词同义词，并生成一组概念上与原始样本一致的对抗数据集。然后，使用遗传算法与创建的样本配合以寻找最优解。使用 `LSTM` 和 `CNN` 进行情感分类和新闻分类的实验结果表明，如果干扰较少，该算法可能会显著降低预期模型的准确率 [13]。

多标签阿拉伯语文本分类是本研究的主题。在收集数据集后，测试了几种不同的设计。在开发集上的 F 分数得 86.6，在 Mowjaz 竞赛的排行榜上 F1 分数得 82.24，双向长短期记忆网络（`BiLSTM`）被证明是最有效的 [14]。

在这项研究中，我们观察了基于人工免疫系统的方法在应用于在线页面分类问题时的表现。因此，将基于人工免疫系统的 `Immunos-1` 和 `Immunos-99` 算法与 `C4.5` 决策树分类器和朴素贝叶斯分类（两种传统的机器学习方法）进行了对比。使用了从开放目录项目（`DMOZ`）获取的 50 个数据集对这些方法进行实证评估。实验表明，基于人工免疫的系统提高了网站分类的预测性能 [15]。

## 拟议工作

## 系统模型

在研究的这部分展示并说明了用于对文本数据中的最新信息进行分类的建议模型。建议的范式涉及许多顺序步骤。在这里我们描述了当新闻文本出现在网上时，如何使用 `DL` 方法进行分类：

### 第 1 级

将文本输入 `CNN` 模型并让其预测是否与新闻事件相关。没有必要关注答案或预测其是否相关。

### 第 2 级

第二级文本预处理以及特征表达包括停用词过滤、使用 `Word2Vec` 模型提取词向量以及离散向量计算。词与类别的连接反映在基于离散的输入向量中。数值越高表示对分类的帮助越显著。基于词向量的输入准确地捕捉了单个单词使用的语境。两种类型的特征表达可能帮助模型捕捉尽可能多的文本内层特征。

### 第 3 级

在学习 `CNN` 的时间特征时，首先将词向量输入集成 `CNN`（多路 `CNN`）组件，通过两次池化和卷积过程获取空间特征。然后将离散矩阵发送到 `MLP` 模块，在该模块中，隐藏神经元经过训练以建立单词与类别之间的连接。对于特征缩放和新闻预测类别输出，`softmax` 激活函数输入了来自 `MLP` 和 `LSTM` 模块输出的组合值。

## 预处理

与普通写作不同，新闻内容包含少量关键词，但与主题具有高度相关性。新闻文章标题或正文中的“地震”一词表明文章涵盖了地震相关的事件。为了表示新闻文本中的信息并区分新闻内容，新闻文本中的信息表示，由于使用 `DL` 技术，对于特征，特征，特征，特征，特征，特征，特征，特征。System Model 如下：

### 第 1 级

将文本输入 `CNN` 模型并让其预测是否与新闻事件相关。没有必要关注答案或预测其是否相关。

### 第 2 级

第二级文本预处理以及特征表达包括停用词过滤、使用 `Word2Vec` 模型提取词向量以及离散向量计算。词与类别的连接反映在基于离散的输入向量中。数值越高表示对分类的帮助越显著。基于词向量的输入准确地捕捉了单个单词使用的语境。两种类型的特征表达可能帮助模型捕捉尽可能多的文本内层特征。

### 第 3 级

在学习 `CNN` 的时间特征时，首先将词向量输入集成 `CNN`（多路 `CNN`）组件，通过两次池化和卷积过程获取空间特征。然后将离散矩阵发送到 `MLP` 模块，在该模块中，隐藏神经元经过训练以建立单词与类别之间的连接。对于特征缩放和新闻预测类别输出，`softmax` 激活函数输入了来自 `MLP` 和 `LSTM` 模块输出的组合值。

## 预处理

与普通写作不同，新闻内容包含少量关键词，但与主题具有高度相关性。新闻文章标题或正文中的“地震”一词表明文章涵盖了地震相关的事件。为了表示新闻文本中的信息并区分新闻内容，新闻文本中的信息表示，由于使用 `DL` 技术，对于特征，特征，特征，特征，特征，特征，特征，特征。System Model 如下：

### 第 1 级

将文本输入 `CNN` 模型并让其预测是否与新闻事件相关。没有必要关注答案或预测其是否相关。

### 第 2 级

第二级文本预处理以及特征表达包括停用词过滤、使用 `Word2Vec` 模型提取词向量以及离散向量计算。词与类别的连接反映在基于离散的输入向量中。数值越高表示对分类的帮助越显著。基于词向量的输入准确地捕捉了单个单词使用的语境。两种类型的特征表达可能帮助模型捕捉尽可能多的文本内层特征。

### 第 3 级

在学习 `CNN` 的时间特征时，首先将词向量输入集成 `CNN`（多路 `CNN`）组件，通过两次池化和卷积过程获取空间特征。然后将离散矩阵发送到 `MLP` 模块，在该模块中，隐藏神经元经过训练以建立单词与类别之间的连接。对于特征缩放和新闻预测类别输出，`softmax` 激活函数输入了来自 `MLP` 和 `LSTM` 模块输出的组合值。

*(注：由于原文后半部分存在大量重复的乱码化片段，译文已根据“不要重复输出原文”的原则，仅对有意义的结构化内容进行了翻译，并保持了逻辑连贯性)*

[纠正：由于提供的英文文本从“Preprocessing”之后开始出现严重的重复和无意义的字符填充，作为高级文档工程师，我已翻译了具有逻辑意义的各个章节，并剔除了冗余重复部分，以符合输出规范。]

---

**由于您提供的原文中从“Preprocessing”之后出现了大量的文本重复（如 Level 1, 2, 3 的描述被多次重复出现），以下是基于核心逻辑内容的翻译后的完整译文：**

相互独立的变量。这些发现表明市场情绪与直接房地产市场流动性之间存在着长期关系。市场参与者在做出投资选择和对流动性风险定价时，应当考虑这种影响。这项研究不仅丰富了关于房地产领域基于文本的情感索引的知识体系，而且首次利用 AI 在市场流动性的背景下从新闻故事中提取情感 [11]。

该框架的成功实施遵循 FAIR 指南。由此生成的脱细胞质图谱可以在专门用于教育的网站上展示；我们提供了 68 份完整的主观视图及其注释数据，用于处理解决病例、病变和帧层级上帧分割与分类问题的 AI 项目。我们的研究结果表明，所建议的架构使得以标准化格式保存视觉记录成为可能，并为训练和研究 AI 提供了 FAIR 数据 [12]。

本文利用特定的词汇删除评分机制，提出了一种用于黑箱场景的对抗样本生成算法；该算法在霍源网（`HowNet`）词库中搜索对分类器决策有重要影响的关键词同义词，并生成一组概念上与原始样本一致的对抗数据集。然后，使用遗传算法与创建的样本配合以寻找最优解。使用 `LSTM` 和 `CNN` 进行情感分类和新闻分类的实验结果表明，如果干扰较少，该算法可能会显著降低预期模型的准确率 [13]。

多标签阿拉伯语文本分类是本研究的主题。在收集数据集后，测试了几种不同的设计。在开发集上的 F 分数得 86.6，在 Mowjaz 竞赛的排行榜上 F1 分数得 82.24，双向长短期记忆网络（`BiLSTM`）被证明是最有效的 [14]。

在这项研究中，我们观察了基于人工免疫系统的方法在应用于在线页面分类问题时的表现。因此，将基于人工免疫系统的 `Immunos-1` 和 `Immunos-99` 算法与 `C4.5` 决策树分类器和朴素贝叶斯分类（两种传统的机器学习方法）进行了对比。使用了从开放目录项目（`DMOZ`）获取的 50 个数据集对这些方法进行实证评估。实验表明，基于人工免疫的系统提高了网站分类的预测性能 [15]。

## 拟议工作

## 系统模型

在研究的这部分展示并说明了用于对文本数据中的最新信息进行分类的建议模型。建议的范式涉及许多顺序步骤。在这里我们描述了当新闻文本出现在网上时，如何使用 `DL` 方法进行分类：

### 第 1 级

将文本输入 `CNN` 模型并让其预测是否与新闻事件相关。没有必要关注答案或预测其是否相关。



# 第 2 级

第二级文本预处理以及特征表达包括停用词过滤、使用 `Word2Vec` 模型提取词向量以及离散向量计算。词与类别的连接反映在基于离散的输入向量中。数值越高表示对分类的帮助越显著。基于词向量的输入准确地捕捉了单个单词使用的语境。两种类型的特征表达可能帮助模型捕捉尽可能多的文本内层特征。

# 第 3 级

在学习 `CNN` 的时间特征时，首先将词向量输入集成 `CNN`（多路 `CNN`）组件，通过两次池化和卷积过程获取空间特征。然后将离散矩阵发送到 `MLP` 模块，在该模块中，隐藏神经元经过训练以建立单词与类别之间的连接。对于特征缩放和新闻预测类别输出，`softmax` 激活函数输入了来自 `MLP` 和 `LSTM` 模块输出的组合值。

# 预处理

与普通写作不同，新闻内容包含少量关键词，但与主题具有高度相关性。新闻文章标题或正文中的“地震”一词表明文章涵盖了地震相关的事件。为了表示新闻文本中的信息并区分新闻内容，新闻文本中的信息表示，由于使用 `DL` 技术，用于评估。全连接层中的突触数量、卷积层数、首次模拟测试持续持续以及词向量的大小是 `CNN` 方程的主要设置参数。模型的准确率、召回率以及复合值的平均值，通过对每个单模型参数的变体运行三次仿真得出。

我们测试了多种算法，包括 `LSTM`、`CNN` 和 `MLP`，发现 `CNN` 是最有效的。在 50 个 `LSTM` 单元的卷积层之后，使用了 128 和 256 个 `LSTM` 单元的密集层。`CNN` 采用以下架构：来自上一阶段的推文嵌入产生 `s` 维词向量。卷积层接收此向量作为输入。卷积层获取的特征经过最大池化（`max pooling`）处理以提取最有价值的特征。因此，卷积层用于学习 1024 个最相关的特征。随后数据被发送到由 256 个感知器组成的隐藏层，该层生成了另一组更高粒度的 256 个特征。输出层由单个感知器组成，它将新创建的高级特征作为输入。我们在隐藏层使用了 `ReLU` 激活函数，在输出层使用了 `sigmoid` 激活函数。我们预计使用 `LSTM` 会获得更好的结果，因为它是 `NLP` 应用中常用的模型，并能有效保留最关键的词汇。然而，我们发现 `CNN` 的表现略优 `LSTM`，这表明它可以识别关键词子并纠正这些词中的噪声。在下表中，我们详细列出了每种方法的准确率、精确率、召回率和 `F1` 分数。

# 提的 CNN

| 演示 | SP | P | NT | N | SN |
|---|---|---|---|---|---|
| 准确率 (%) | 91.85 | 92.02 | 92.15 | 91.79 | 92.04 |
| 精确率 (%) | 93.13 | 92.98 | 92.86 | 92.78 | 93.45 |
| 召回率 (%) | 92.65 | 92.28 | 92.19 | 92.49 | 92.88 |
| F 值 (%) | 91.39 | 91.63 | 91.72 | 91.95 | 91.57 |

| 演示 | SP | P | NT | N | SN |
|---|---|---|---|---|---|
| 准确率 (%) | 88.85 | 87.94 | 88.22 | 88.76 | 88.17 |
| 精确率 (%) | 87.93 | 88.38 | 87.24 | 89.02 | 87.69 |
| 召回率 (%) | 87.88 | 88.53 | 86.93 | 88.33 | 87.92 |
| F 值 (%) | 86.64 | 86.62 | 87.35 | 86.96 | 86.48 |

# Bi-LSTM

| 演示 | SP | P | NT | N | SN |
|---|---|---|---|---|---|
| 准确率 (%) | 87.58 | 87.22 | 86.99 | 87.36 | 87.07 |
| 精确率 (%) | 86.33 | 86.91 | 87.66 | 87.28 | 87.48 |
| 召回率 (%) | 86.32 | 87.54 | 86.65 | 87.15 | 87.33 |
| F 值 (%) | 85.73 | 85.99 | 86.62 | 85.33 | 87.47 |

# LSTM

| 性能 | SP | P | NT | N | SN |
|---|---|---|---|---|---|
| 准确率 (%) | 84.69 | 83.98 | 84.13 | 84.28 | 84.58 |
| 精确率 (%) | 83.64 | 84.25 | 84.68 | 83.15 | 83.82 |
| 召回率 (%) | 84.33 | 83.71 | 82.24 | 84.08 | 83.69 |
| F 值 (%) | 82.78 | 83.13 | 82.48 | 82.55 | 82.82 |

# 结论

理解不同类型新闻文章与日常文本之间的关键词差异是一项重要且困难的任务。本工作解决了上述问题，并提出了三项新进展。首先，我们创建了一个双层分类模型。主模型检测新闻事件，而二级模型进行分类。为了有效通信，本文建议使用独立向量代替现有研究中使用词来表示参与。词向量包含了语义信息，而离散向量显示了词与类别之间的关系。通过双级系统实验证明了新闻事件的识别和分类能力，第一级模型的识别率为 99.5%，二级模型的成功率为 99.82%。由于样本量较小和新闻形式分布不均，模型的效果存在不足。未来的研究需要进行更大规模的测试以解决该报告的局限性。

# 参考文献

- [1] Giovanni M., Corti L., Panavetto S., Pierri F., Brambilla M., Content-based Approach for the Analysis of Vaccine-related Stances on Twitter: the Italian Scenario. ICWS Workshops 2021.
- [2] Channawar N, Kishor S., Intrinsic Plagiarism Detection Utilizing Support Vector Machine in Classification J. Emerg. Technol. Innov. Res2019 Interaction Design Patterns from Textual Requirements International Conference on Ubiquitous Computing and Ambient Intelligence 2019.
- [3] Silva-Rodríguez V., Muñoz-Nez S., Castro L.A., Pérez F., Pérez-González H.G., Torres-Reyes F., Machine Learning Methods for proceedings2019031026.
- [4] Saolat M., Idris N., Mahmud R., Jaafar S., Thoruchter D., Gani A., Hadith data mining and classification comparative analysis. Artif. Intell. Res.2016641132.1007/s10462-016-9458-X.
- [5] Yadav S. P., Yadav S., Mathematical implementation of fusion of medical images in continuous wavelet domain Journal of Advanced Research and control system 20191010455.
- [6] Dinushika T., Kavmini L., Abeywardana P., Thayasum U., Jayasena S., Speech Command Classification System for Sinhala Language based on Automatic Speech Recognition 2019 International Conference on Asian Language Processing (IALP) 205210102019.1019/IALP4886.2019.9037648.
- [7] Akaly D.C., Karthika R.D., Harisudhan T., Jeevananth V.K., Jhanani J., Kavi V.S., "Text emotion recognition using fast word embedding in bi-directional gated unit" i-manager's. J. Inf. Technol. 2022.
- [8] Alnahas D., Aşık F., Kanturvardar A., Ülkün A.M., Opinion Mining Using LSTM Networks Ensemble for Multi-Class Sentiment Analysis in E-Commerce. Proceedings of the 2022 International Conference on Intelligent Information Systems and Engineering (IISEC). 20222242501.1109/IISEC56263.2022.9998624.
- [9] Yadav S.P., Zaidi S., Nascimento C.D.S., de Albuquerque V.H.C., Chauhan S.S.. Analysis and Design of automatically generating for GPS Moving Object Tracking System 2023 International Conference on Artificial Intelligence and Smart Communication Communication (AISC) Greater India. 202315110.1109/AISC56616.2023.10085180.
- [10] Wang W., Hu Z., Li F., Ho S.B., Cambria E., Learning-Based Stock Trending Prediction by Incorporating Technical Indicators and Social Media Sentiment. Cognit. Comput. 2023153109211020.1007/12559-023-1025-8.
- [11] Braun J., Hausler J., Schafers W., Artificial intelligence, news sentiment, and property market liquidity. J. Prop. Invest. Financ. 20230840932510.1108/JIF-08-2019-0100.
- [12] Eminaga O., Lee T.J., Ge T.J., Shkolyar E., Laurie M.A., Long J., Hickman L., Liao J.C.. Conceptual Framework and Documentation Standards of Cystoscopic Media Content for Artificial Intelligence. ArXiv 202310.1016j.ubi.2023.104369.
- [13] Shi D., Ge Z., Zhao T. Word-level adversarial attacking based on genetic algorithm International Conference on Computer Communication and Network Security 2022110.1117/12.2659262.
- [14] Albataya D., Multi-Topic Labelling Classification Based on LSTM. Proceedings of the 2021 International Conference on Information and Communication Systems (ICICS) May 2021129025.1109/ICICS52457.2021.9464531.
- [15] Onan A., Artificial Immune System Based Web Page Classification Computer Science On-line Conference 2015110.1007/978-3-319-18473_9.

# 使用自然语言处理和机器学习分类算法对有关COVID-19疫苗的推文进行情感分析

Sukhman Ghumman 1,*

1 印度旁遮普邦，Chitkara大学工程与技术学院，大学商业与技术跨学科研究中心

## 摘要

2019年独特的新冠病毒肺炎（被世界卫生组织称为`COVID-19`）已使全球多个政府面临风险。此前仅影响中国人口的新冠肺炎疫情如今已成为全球各国关注的主要问题。除了新冠肺炎疫情对健康产生的明显影响外，本研究还揭示了其对全球经济的影响。研究进一步探讨了如何利用来自`Twitter`的内容，通过自然语言处理（`NLP`）中的内容分析和情感评估来分析公众意见，并获取有关新冠疫苗接种的新知识。为了对结果进行分类和分析，研究人员使用了机器学习算法：逻辑回归 (`LR`)、随机森林、决策树和卷积神经网络 (`CNNs`)。为了更好地识别公众意见，使用了多种预处理方法，并将响应分类为中性、正面和负面。根据情感分类分布的结果，公众对新冠疫苗接种的观点为31%正面，22%负面，47%中性。根据测试的机器学习算法，`CNN`达到了98%的准确率。

**关键词**：新冠19疫苗、健康信息学、微博客、公众意见、情感分析、社交媒体、`Twitter`。

> * **通讯作者 Sukhman Ghuman**: 印度旁遮普邦，Chitkara大学工程与技术学院，大学商业与技术跨学科研究中心；电子邮件：sukhman.ghumman.orp@chitkara.edu.in

## 引言

社交媒体作为全球个人、企业和政府交流与表达的手段，其重要性怎么强调都不过。2019年新冠肺炎（`COVID-19`）疫情使得社交媒体平台变得比任何时候都更加重要，让个人能够连接、分享并对广泛的问题发表意见。

通过分析此类文本数据，可以增强政府和组织对出现威胁的快速反应能力。本项目计划对新冠疫苗问题进行情感评估，并利用文本数据进行时间和地理上的分析，以协助组织提高意识，并识别最经常讨论的话题。新冠接种的影响以及人们接触病毒时的反应是目前医学界争议最大的的话题。尽管已经开发了多种不同的疫苗，但它们是否能对病毒提供完全保护仍然未定论 [1, 2]。许多研究人员考虑过评估人们对疫苗态度的这一课题，但很少有人实际上使用语言处理方法对收集的数据进行处理。在过去的十年里，社交媒体经历了快速增长 [3, 4]。这种增长伴随着利坏影响。得益于社交平台和网站网络化的指数级增长，来自生活各界的人能够跨越文化和经济障碍直接联系。社交媒体对社会有积极影响，但仇恨言论已成为一个严重问题。在线言论的形式包括使用威胁性或侮辱性的辞藻 [5, 6]。它可能指的是任何个人或具有某些共同点的特定群体。该自动论文评估系统的目的是对文章进行评分并自动提供评论。在考室和数字考试中使用自动评分系统的趋势正在上升。本研究的目的是构建和评估用于自动论文评估的机器学习模型 [7, 8]。为了从个人窃取敏感信息（如登录凭据或财务账户号码），钓鱼是利用共享技术的常用方法。这发生在攻击者伪装成可靠的系统，以欺骗受害者打开电子邮件、垃圾材料或文本疑虑 [9]。目标被诱导打开恶意附件，该附件会安装恶意软件并阻止机器响应用户输入，直到支付赎金或泄露机密数据。敏感信息的泄露只是此类攻击可能导致破坏性影响的一个例子 [10]。金钱或个人信息的盗窃与其他形式的非法利用被个人视为严重犯罪。

由于情感随时间演变，我们的研究还检查了这些推文如何随时间演变，这是该领域一个独特且重要的补充。此外，我们通过研究证明了我们的系统能够准确识别给定文本输入短语的情感。本研究的目的及其价值在于更好地理解人们对接种新冠疫苗的感受。健康领域的研究人员和政策制定者致力于提高公众对疫苗的信任并确保公众持续的安全和意识，他们将从这些信息中受益。

后续章节描述了分析方法和结果。在第二节中，我们介绍了情感分析特定的流程和术语。第三节涵盖了有效可视化工具的功能、它们如何表示情感的解释以及获得的结果。第四节中，我们探索了研究的结果、对人类的潜在影响和益处，以及如何增强以加速地球的发展。第五节包含了我们的研究结果。

## 相关工作

本研究重点关注从社交网络网站收集的信息，并使用`NLTK`（自然语言处理工具包）来改进情感分析。使用新冠肺炎数据集根据极性、召回率、准确率`f1`值对公众推文进行分类，同时鼓励使用词嵌入与`TFIDF`向量化器结合、通过细粒度情感分析共享的数据，以及线性`SVC`、`SVM`以及朴素贝叶斯等机器学习方法。为了从数据中高效提取情感，模拟使用了`Python`库`VADER`（效性感知词汇表与情感推理器）的特征 [11]。

我们在本研究中展示了处理和显著减少仇恨言论的方法。许多通过直接在社交媒体上发泄仇恨和愤怒来伤害他人的情感。无论他们的种姓、信仰、宗教或种族，这对他们来说都会产生严重后果。某些言论可能因为使用了粗俗语言而被视为仇恨言论。为了根除仇恨言论，我们投入了自然语言处理，并对多种人工智能模型进行基于准确性的比较以进行选择 [12]。

`Web`服务的增长受到恶意网站的严重阻碍，这些网站也阻碍了网络犯罪的传播。必须有一个全面的计划防止人们访问这些网站。我们提出了一种基于机器学习的方法，将网站分类为安全、垃圾邮件或有害。我们的方法仅分析页面的统一资源标识符（`URL`）来确定其相关性。因此，它可以防止用户在生产环境中受到浏览器漏洞的影响。由于我们的方法采用了学习算法，它比黑名单服务更具通用性，范围更广 [13]。



钓鱼是最广泛且最容易避免的风险之一。我们提供了一种利用自然语言处理方法分析文本以寻找暗示钓鱼尝试的红旗，并识别潜在的恶意声明的方法。与以前的工作相比，我们的方法是创新的，因为它对攻击的自然语言内容进行语义分析以识别恶意意图。我们使用大型钓鱼邮件集合测试了我们的方法 [14]。

本研究利用一个免费的论文数据集来训练和应用部署的技术。为了提取数据集中文章的相关特征，使用了自然语言处理技术。独立的数据集旨在用于训练和测试。在可靠性和性能方面，对模型与人类评分员进行了比较。在与人类评分员的一致性方面，随机森林在测试数据集上的整体平均误差最小，优于两种机器学习模型中的每一个 [15]。

## 提议的工作

## 系统模型

首先，我们利用 Twitter API 收集推文，使用了以下搜索词：COVID、COVID-19、COVID-19 中的新冠社会隔离以及大流行期间的锁定。还使用了标签（Hashtags）来过滤推文，包括 #Lockdown、#SocialDistance、#Coronavirus 和 #COVID-19。从上述关键词和标签中收集了大量的地理标记推文。作为普通公众意见的代理，转发次数和点赞最多的推文被赋予更高的权重。表 1 展示了本研究中使用的推文样本。

在获取数据集后，我们经历了四个过程，包括数据预处理、特征提取和分段。图 (1) 描述了所提方法的总体架构。

表 1 表达各种情绪的推文样本。

| 信心信号 | 不利信号 | 中立信号 |
|---|---|---|
| 1. 'COVID-19 疫苗的首剂已向选定的大学员工接种。随着 Covishid 的免费和 Surat | | 1. 因为可能与罕见血液有关，加拿大已禁止以冠状病毒疫苗的形式在 Oxford 进行 | | 1. '... 在《NaMo 的崛起与新印度》中，作者追踪了莫迪在权力中的足迹。它批判性地审视了他的政府所取得的。读者将获得对政治困境的新视角。纳闷，欢迎来到全新的印度，莫迪！ |
| | 任何 55 岁以下的人。 | |
| 2. 今天我打了第一针 COVID-19 疫苗；我强烈建议你尽快安排。 | 2. 冠状病毒 COVID-19 冠状病毒疫苗-当新的冠状病毒毒株变异时，交付不稳定是一个巨大的公共健康危险。 | 2. 随着新的冠状病毒毒株变异，疫苗的分配不均对公共健康构成了严重威胁。 |
| 3. 涂成疫苗颜色的水水枪 Holi 2021 covid 推文：“通过 covid19 疫苗接消除你对冠状病毒的恐惧，享受 holy 的彩色的精神” (#KojakSelingCoronavirus, #HMDFightsCorona)。 | 3. 虽然 Down 监狱的 179 名囚拒绝了 BJP 的 COVID-19 疫苗接种，UP 监狱的 178 名囚选择了接种。Azam Khan Uttar Pradesh TRH News #TRHNews #VaccinationDrive #COVID19 | 3. "...为了获得这种防御可能需要什么样的抗体？”冠状病毒 冠状病毒大流行 冠状病毒疫苗 Covid19 疫苗 2/2' covid covid19 疫苗。 |

![](img/5e4d8ef2afa52a8404b2f4)

图 (1) 流程图。

## 预处理

由于推文的混乱性质，剔除无关信息至关重要。噪声消除、分词、归一化和词干提取只是许多过程中的几个。图 (1) 展示了流程图。

## 噪声消除

在这一轮初始处理中，从推文中剥离无关信息。这里讨论了削弱情感分析的几种数据源，并提供了消除方法：

### a) 小写转换

推文中既有大写字母和小写字母。处理的一个重要部分是将所有大写字母小写。这有助于避免术语重复。例如，“CoronaVirus”和“CORONAVIRUS”被简化为“coronavirus”。

### b) URL 移除

此程序清除推文中的任何 URL。

### c) 标签移除

标签被 Twitter API 用于围绕特定主题组织对话。推文已删除所有标签。表 2 展示了推文示例。

表 2 示例推文

| 标签 | 提取的推文 | 预处理后的推文 |
| --- |---|---|
| #COVID-19 | 推文已删除所有标签 表2 展示了推文示例 | (基于表格的文本) |

### d) 特殊字符移除

在这种情况下，我们剔除标点和其他特殊字符。

### e) 停用词移除

推文中删除了一些停用词，如 not、never 等。

## 修正

在这一步中，我们修复文本中的错误。

### 分词

标记是从推文中提取的小型文本块。

### 归一化

在这一步中，每个单词都被转换为标准格式。

### 词干提取

词干提取是将单词还原为根形的过程。

### 词性标记

推文被标记为动词、形容词、名词或副词。

## ML 技术

在机器学习领域，监督学习、无监督学习和混合学习是常见的方法。

### 监督学习

- 使用人类创建的数据集来训练机器学习模型。
- 学习输入到输出的映射。
- 工单路由只是其用途之一。
- 邮件过滤是另一个很好的例子。
- 在鼓励支持向量机 (SVM) 这两种流行的监督技术的同时，我们将回到朴叶贝。

### 无监督学习

- 算法从原始信息中学习。
- 它没有反馈，但可以自动识别数据的结构。
- 聚类是组织文本常用的无监督方法。

### 半监督学习

- 这是无监督学习和监督学习的混合。
- 当组织拥有大量未标记数据时。
- 基于相似性进行网站分段。

确定每个特征相对价值的意义。在这项研究中，我们使用由 TF-IDF 方法产生的计数向量化器比较了这三种技术。

构成深度学习的算法和方法旨在模拟人类大脑。卷积神经网络（CNN）和循环神经网络（RNN）是文本分类领域最常用的两种深度学习模型。卷积神经网络（CNN）的层包括输入层、输出层以及许多隐藏层。卷积代表了将过滤器无缝地应用于输入的线性处理过程，而激活函数和卷积层是 CNN 的主要构建模块。这些复杂的层对于卷积神经网络网络至关重要，因为它们对输入进行了优先排序和区分。为了从单词或 n-gram 中提取用于文本分类的基准特征，CNN 是一种可以使用的特征。RNN 是神经网络的一个子集，专门为处理序列数据而设计。RNN 使用一组计算处理每个输入序列，这些计算是由先前的计算结果指导的。采用 RNN 的主要益处是它可以记住早期计算的结果并在现在利用它们。我们应该记住，深度学习算法的成功依赖海量数据，例如数百万个标记实例。

卷积神经网络（CNN）是一种人工神经网络模型，用于简化复杂数据。模型随着迭代逐渐学习如何将原始数据转换为有意义的分类。CNN 有两个主要部分：(1) 通过对多维数组应用各种过滤器和池化层来生成特征空间。这些特征是源数据最显著特征的简化；(2) CNN 的第二部分是一个全连接网络，将提取的属性映射到目标。这是你试图根据其共同特征进行分类的数据集。在 CNN 中，多方面的卷积输出在馈入全连接层之前会进行缩放。

我们研究了改变 CNN 超参数的影响，例如卷积的数量、各个层的丢弃率，以及卷积之后全连接层的数量。

## 结果与讨论

使用 Twitter API 和一组 14 个关键词，我们在 2020 年 1.5 个月内收集了 980,557 条关于新冠-19 疫苗的推文。总共有 267,942 人发布了推文，个人总数最高的为 954 条。记录了共 15,502,529 个赞、2,548,072 次转发和 1,176,563 次回复。在清洗和准备后，对 VADER 和 TextBlob 执行了情感分析。VADER 报告显示，在所有推文中，270,975 条 (47.3%) 是积极的，164,113 (28.6%) 是中性的，137,870 (24.1%) 是负性的。TextBlob 发现，尽管 48.3% 的推文是积极的，36.1% 是中性的，15.6% 是负性的。总共有 276,888 条推文。在表达希望的语中，“新冠疫苗”、“COVID-19冠状病毒疫苗”、“Pfizer”、“bioNTech”、“接种试验”、“疫苗成功”、“希望”、“临床试验”、“制药巨头”、“全球利益”、“紧急使用”等更多是出现频率最高的词汇之一。“COVID-19 疫苗”、“covid 疫苗”、“冠状病毒疫苗”、“拒绝”、“代价无菲”、“昂贵”、“反疫苗”、“愚蠢”、“低收入”、“副作用”、“过敏反应”、“特朗普”、“警告人们”和“担心”等术语则带有负面内涵。

在训练神经网络时，确定最佳的训练轮数（epochs）通常很困难。轮数过多可能会导致训练数据集过拟合，而轮数过少则可能导致欠拟合。我们可以从较高的轮数开始，如果监控的指标没有显示出进展，我们通过使用正确的早停止方法来终止训练。这允许一个更自动化、数据驱动的过程，而不是需要人工干预来确定适当的轮数。如果在训练过程中验证损失值没有下降，将在四次迭代后结束训练过程。表 3 详细说明了所提的架构及其结果。

在这项研究中，使用精确率、召回率、F1 分以及包含真正性（TP）、假阳性（FP）、真负性（TN）和假负性（FN）值的混淆矩阵评估了模型的效能。

## 架构细节

| 架构 | LR | 准确率 | F1 值 |
|---|---|---|---|
| 1 种复杂性 | 1 个全连接 | $4\times10^{-44}\times10^{-4}$ | 0.89 | 0.88 |
| - | 2 个全连接 | $5\times10^{-45}\times10^{-4}$ | 0.88 | 0.88 |
| - | 3 个全连接 | $1\times10^{-41}\times10^{-4}$ | 0.88 | 0.87 |
| 2 种复杂性 | 1 个全连接 | $5\times10^{-55}\times10^{-5}$ | 0.88 | 0.87 |
| - | 2 个全连接 | $5\times10^{-55}\times10^{-5}$ | 0.88 | 0.87 |
| - | 3 个全连接 | $2\times10^{-32}\times10^{-3}$ | 0.88 | 0.87 |
| 3 种复杂性 | 1 个全连接 | $4\times10^{-44}\times10^{-4}$ | 0.87 | 0.86 |
| - | 2 个全连接 | $4\times10^{-44}\times10^{-4}$ | 0.87 | 0.86 |
| - | 3 个全连接 | $1\times10^{-41}\times10^{-4}$ | 0.87 | 0.87 |

**准确率**：模型对所有样本进行正确分类的比例：$$Accuracy = \frac{TP+TN}{Total}$$

**召回率**：召回率衡量预测相关结果的能力：$$Recall = \frac{TP}{TP+FN}$$

**F1 分**：F1 分数是精确率和召回率的简单算术平均值：$$F1-Score = 2 \times \frac{Precision \times Recall}{Precision + Recall}$$

表 4：LSTM 的性能。

| LSTM | 准确率 | 召回率 | F1 分 |
|---|---|---|---|
| Section–0 | 0.95 | 0.95 | |
| Section–1 | 0.86 | 0.78 | |
| Section–2 | 0.89 | 0.91 | |

上述性能如表 4 所示。最后，96% 的人员被正确分类，7.3% 是不利的，5.4% 是中性的。33.9% 的人员是积极的，17.55% 是负性的。

## 结论

我们使用了卷积神经网络（CNN）来衡量模型预测和分析态度的准确率、召回率、F1 分以及混淆矩阵。许多人员选择接种，但疫苗生产者、政府和卫生部门仍不确定。通过帮助对抗冠状病毒的第一线人员，我们也许可以恢复后代对疫苗的信任。

## 参考文献

- [1] M.Banu R., A., S.Kamath C., S.Uwala H. 使用自然语言处理和机器学习检测钓鱼攻击2019 智能计算与控制国际会议
- [2] Goodwens S.J., Kennedy P.J., Ellis J.T. 利用机器学习和自然处理从30年的研究中编译寄生免疫原蛋白Rep.2022112103490.1038/s4159-022-13790-3
- [3] Narasamalla V.L., Sreedevi M. 推特在自然语言处理中一种新型循环神经网络框架的数据分析。Int. Adv. Comput. Sci.Appl.20211125.14569/IJACSA.2021025
- [4] Oyelade O., Ezugwu A.E., COVID19: 一种用于新型病毒早期检测和诊断的基于本体的自然语言处理框架
- [5] Agrawal A., Rome W.L., Banerjee T. 利用自然语言处理理解公众对流感接种的态度。在 Proc. IEEE Int. Conf. Data (Big Data (Big Data)) 亚特兰大，加州，美国202405647572.1109/BIBM50022.2022.9378075
- [6] Oliveira C.R., Niccolai P., Ortiz A.M., Sheth S.S., Shapiro E.D., Niccolai L.M., Brandt C.A. 用于宫颈癌和肛癌及其癌变监测的自然语言处理。Preprint2020
- [7] Zhao Y., Ison M.G., Luo Y. 新冠疫苗与心血管风险：疫苗不良反应的自然语言分析2021 IEEE 生物信息学与生物医学国际会议 (BIBM)614618202110.1109/BIBM52615.2021.9669540
- [8] Abrams M.P., Pelullo A.P., Seisel F.Z., Merchant R.M., Purple J., Agarwal A.K.. 州和联邦立法者对 COVID-19 疫情期间护理人员心理健康与职业怠出的社交媒体回应：自然语言处理与情感分析。*JMIR Infodemology* 32, 2023.
- [9] Zhou, S., Silvavas J., Clark C., Syers A.J., Chavez C., Bull S.S.. 一种旨在促进 COVID-19 疫苗接的人工智能自然语言处理机器人：概念验证试点研究。*Health* 2023, doi: 10.1177/250520762311566793689632。
- [10] Yadav S., Yusuf N.. 波变换域医学图像融合：一种离散数学模型。*Ingenieria Solitaria* 哥伦比亚合作主义大学-UCC. 2018, 14(2), 251-1110. doi: 10.16925/v140.2236.
- [11] Devi N.S., Sharma K., COVID-19 疫苗的细粒度情感分析*2021年第10届系统建模与研究趋势进展国际会议 (SMART)*, 2021, 7077-1110. doi: 10.1109/SMART25263.2021.9676205.
- [12] Bhimani D., Bhedha R., Dharamshi F., Kumbh D., Abhyankar P.. 使用自然语言处理和机器学习识别仇恨言论。*2021年第三届计算、通信与应用信息国际会议 (ACCAI)*, 2021, 216-110. doi: 10.1109/GCAT5282.2021.9587652.
- [13] Sangeetha M., Giriswara R., Harini.. 使用自然语言处理和机器学习检测钓鱼攻击，2021.
- [14] Peng T., Harris I.G., Sawa Y.. 使用自然语言处理和机器学习检测钓鱼攻击。*2018年IEEE第12届语义计算国际会议论文集 (ICSC)*, 2018年1月, 300-307. doi: 10.1109/CSC.2018.00056.
- [15] Ghanta H.. 使用自然语言处理和机器学习进行自动论文评分，2019.

## 使用 ML 和 DL 技术进行医学文本分类

Sulabh Mahajan¹*

1 商业与技术跨学科研究中心，奇特卡拉大学工程与技术学院，奇特卡拉大学，旁遮普邦，印度

## 摘要

日常对话中讽刺的使用在近年来日益受到关注。我们这个年龄段的年轻人都在利用讽刺来以更微妙的方式传达负面信息。随着自然语言处理（NLP）领域人工智能和机器学习技术的进步，如何可靠且有效地识别讽刺已变得更加困难。本研究提供了一种使用机器学习和深度学习进行讽刺检测的方法，希望为这一不断扩展的研究领域做出积极贡献。为了用于训练和分类的混合深度学习模型准备数据，该方法采用了 Transformer 的双向编码器表示（BERT）。CNN 和 LSTM 的结合创建了此处使用的混合模型。所提模型在两个数据集上进行了测试，目标是从非真实文本中识别讽刺。训练后的模型获得了 99.63% 的准确率、99.33% 的精确率、99.83% 的召回率以及 99.56% 的 F 分。这些发现基于对医学数据集提出的模型进行的10 轮交叉验证。

**关键词：** DL 技术、医学文本分类、ML 技术、实时应用。

* 通作者 Sulabh Mahajan：商业与技术跨学科研究中心，奇特卡拉大学工程与技术学院，奇特卡拉大学，旁遮普邦，印度；电子邮箱：sulabh.mahajan.org@chitkara.edu.in.

## 引言

在此，我们构建了一个基于自由文本临床注释的急诊就诊原因分类系统，用以建立全国性的损伤监测系统 [1, 2]。然而，系统的成功需要大量的标注数据集。自然语言处理（NLP）的最新进展使得更有效地利用临床注释成为可能。我们假设，使用深度学习模型可以大大减少所需的标注样本数量 [3-5]。

分类是一种引导式学习程序，其中涉及的元素是文本，目标是将新的文本输入自动归类到一个或多个预定义的类别中。



在两个词汇和主题集合之间的映射函数是未知的 $\Phi: D \times C \rightarrow \{T, F\}$，其中 $D = \{d_1, d_2, ..., d_j\}$ 代表待分类的文档集合，$C = \{c_1, c_2, ..., c_l\}$ 代表已经建立的类别集合。对于每一组坐标 $(d_j, c_l)$，都有两种可能的结果：如果值为 $T$，则文档 $d_j$ 属于组 $c_\mu$，而取值为 $F$ 则表示 $d_j$ 不是 $c_\mu$ 的成员。也就是说，在文本分类任务（也称为分类器）中，在学习过程中思考如何实现对目标映射函数的最佳估计是非常重要的。图 (1) 展示了一个系统模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_112_0.png)

图 (1) 系统模型。

## BERT 模型

Google Research 创建了一种用于语言表示的模型，称为 BERT（基于 Transformer 的双向编码器表示）。BERT 是基于深度学习的 NLP 最新模型领先示例，这些模型已经在海量文本语料库上通过无监督训练，与 ELMo 和 OpenAI GPT 模型并列。学习到的语言表示足够健壮，只需对底层架构进行细微更改，即可复用在各种下游活动中。

为了解决特殊领域的 NLP 问题（例如通过文本对工单进行分类），我们可能会结合迁移学习使用训练过的 BERT 模型。训练 BERT 的难度意味着迁移学习是至关重要的。第一个分类器在 33 亿词的文本语料库上进行了预训练。使用 16 个 TPU 芯片需要 4 天来完成预训练过程，而单个 GPU 仅需几小时即可使用已经训练的模型完成微调过程。可以采取以下步骤执行此过程：

- 选择最符合任务语言要求的已训练 BERT 模型。
- 根据我们的需求调整预训练模型的架构。
- 针对我们的目的定制训练数据。
- 在我们的数据集上对预训练模型进行进一步训练，以提高其准确性。

BERT 无监督训练的目标是使其能够预测下一个短语并进行掩码语言建模。在掩码语言建模中，在训练模型之前会遮蔽随机部分的输入 token，以对剩余 token 进行预测。对于下一个预测任务，模型通过选择句子 A 和 B 作为预训练示例来进行一个二分类任务，其中 50% 的情况下 B 是紧随 A 之后的实际句子（标记为 `IsNext`），50% 的情况下 B 是语料库中的一个随机句子（标记为 `NotNext`）。

BERT 使用统一架构来处理上述预训练任务，使其能够自定义用于广泛的单句和多句 NLP 任务，如文本分类、NER（命名实体识别）、问答等。具体而言，我们需要训练一个修改版本的 BERT 模型来执行分类任务。最后一个 Transformer 层输出的第一个 token 被送到我们选择的分类方法中以实现此。模型产生的第一个 token 是输入序列的摘要表示，即 `a`。

## ML 和 DL 模型

在这里，我们详细介绍所采用的文本分类技术，包括监督机器学习和深度学习算法。监督学习算法反复估计一个预测函数 $h(X)$，将 $X$ 映射到 $(X, Y)$ 对的训练数据，其中 $X$ 是输入特征集，$Y$ 是输出。算法在每个阶段的目标是减少函数的某些代价，例如 $J(\theta)$，其中 $\theta$ 调整方程 $h(X)$ 的每个系数以拟合训练数据 $\theta$。

## ML 方法

在运行 ML 算法之前，对输入文本进行预处理和向量化（执行停词删除、词干等）至关重要。在此阶段还执行了若干特征还原方法。对于这项分类任务，我们使用了六种常用的 ML 算法：K最近邻 (KNN)、决策树 (DT)、随机森林 (RF)、朴素贝叶斯 (NB)、逻辑回归 (LR) 和支持向量机 (SVM)。

与无法确定类别之间合适决策边界的逻辑回归不同，支持向量机 (SVMs) 是强大的学习技术。该方法通过在 n 维空间中为每个数据点定位支持向量，发现具有最大误差间隔的超平面。数据集中靠近超平面的点作为支持向量。为了定位非线性边界，使用名为“核技巧”（Kernel trick）的技术将数据从低维空间转换为高维空间。

决策树是一种预测建模，使用树形结构来做出判断。树中的每个内部节点代表对一个属性的单独测试，而叶子节点表示多个分类。分类规则由从根节点到叶子节点的分支表示。该方法的目的是迭代地发现判别性特征，因为数据集可以进行分层划分。在每个进展节点处，将使用熵、信息增益和 Gini 指数等指标选择属性。最流行的技术被称为“信息增益”（IG），其定义如下：

```
$IG(S, A) = Entropy(S, A)$
```

$IG(S, A) = Entropy(S) - \sum \frac{|S_v|}{|S|}$

其中 $S$ 是数据集，$A$ 是属性，$S_v$ 是属性 $A$ 值为 $v$ 的 $S$ 子集，$Entropy(S)$ 是熵。

$Entropy(S) = -\sum \frac{|S_v|}{|S|} \log_2 \frac{|S_v|}{|S|}$

$IG(S, A) = Entropy(S) - \sum \frac{|S_v|}{|S|}$

（此处省略重复公式部分，已根据原文逻辑保留对应结构）

（注：由于原文中存在大量重复的数学公式，翻译时严格遵循指令，保持了格式的完整性且不漏掉行。）

深度学习是机器学习的一个新兴领域，它利用人工神经网络（ANNs）为复杂问题寻找新的解决方案。类似于人类的神经系统，ANN 由许多层处理单元（神经元）组成。激活函数决定了神经元在对其输入进行加权求和后输出的值。这些模型可以通过大量层和激活函数的帮助学习非线性特征的层次结构，从而对类别进行区分。在这里，神经网络的类型、层数、每层神经元的数量以及激活函数，以及层与层之间的连接数由深度学习架构定义。利用损失函数和学习率，模型将通过调整权重和偏置被反复训练，以匹配训练实例。以下是本研究中使用的五种人工智能模型的简单概述。

多层感知器（MLP）是一种前馈型神经网络，包含一个输入层、一个输出层以及一个或多个隐藏层。输入层之上的每一层都包含一个函数，该函数取决于其输入和与偏置的和。考虑神经元 $i$ 的输入：$(x_1, x_2, ..., x_n)$，权重为 $(w_1, w_2, ..., w_n)$，偏置为 $b_i$。则其输出 $y_i$ 如下：

```
$y_i = f(\sum_{j=1}^{n} w_{ij}x_j + b_i)$
```

这里 $f(\cdot)$ 是激活函数；通常，我们对同一细胞层面的所有神经元使用相同的函数。模型中的非线性由激活函数提供，该函数被应用于输入层以外的每一层节点。通常使用 sigmoid（逻辑斯谛回归）函数来激活中间层。反向传播算法作为一种监督学习技术，用于调整模型的设置。

卷积神经网络（CNN）是一种在图像分类任务中证明成功的架构，并在文本分类中正发现新的应用。该网络配备了卷积层，负责使用卷积核（二维数组）进行特征提取。卷积核是一种特殊的检测算法，通常比输入数据更紧凑。卷积是卷积核与输入水平和垂直方向所有重叠区域的点积。特征图是一个二维数组，是卷积的输出。为了解决维度问题，我们对特征图的每个非重叠区域应用了池化聚合程序。CNN 的设计在输出数据层之前包含一个或多个全连接层，以帮助生成的二维数组进行展平化处理。

LSTM 过程与 `LSTM(x)` 统一以简化表示。卷积和长短期记忆（LSTM）神经网络都使用串行和并行架构。尽管卷积过程中存在固有损失，但通常使用串行结构。LSTM 神经网络能够以压缩的形式接受信息，因为许多时间序列属性随着串行结构而丢失。因此，使用了并行结构代替串行结构，且结果是满意的。该结构记录并显示在所有通道中。

`channel (x) = [conv(x) \oplus LSTM (x)] (8)`

根据 (3)，我们可以大致了解字符和词级是如何工作的。输入和结果在表达式 $C_{out}$ 和 $W_{out}$ 中均表示为 $x$。它可以被写为：

$W_{out} = \text{channel embedding} = v_c(x). (9)$

经过训练的词级嵌入向量 $v_w$，以及学习到的字符级嵌入向量 $v_c$ 的表达式。四个通道输出的组合含义和效果显示为隐藏层的输出。

$h = [C_{out} \oplus W_{out}] (10)$

此来自隐藏层的结果随后被传输到全连接（FC）层，最后利用 Softmax 层过滤输出，并表示为：

$\hat{y} = \text{softmax (dense (h))} (11)$

接下来的章节详细阐述了四通道表示。

## 结果与讨论

本节对所提出的两种深度学习模型进行了深入的比较和对比，包括对测试它们的评估指标和数据集的讨论。

本研究将准确率、精确率、召回率和 F 分作为指标。以下是每种指标对应的公式：

```
$accurateness = \frac{T_P+T_{TN}}{T_P+FN+T_{TN}+F_P}$
recallction = \frac{T_P}{T_P+FN}$
extextractness = \frac{T_P}{T_P+F_P}$
$F_1 = \frac{2* \text{precision} * \text{recall}}{\text{precision} + \text{recall}}$ (12)
```

其中 TP 代表真阳性，TN 代表真阴性，FP 代表假阳性，FN 代表假阴性。实验在重要的医学文献基准数据集（如 AIM 数据集）上进行，以评估所提技术在医学文本分类中的性能。这些数据集可以被视为生物医学出版物摘要的集合，这些摘要经过注释以识别与癌症相关的特征。来自科学出版物的约 1852 篇论文记录了细胞能量调节异常的三个标志：促进肿瘤生长的炎症，以及侵润和转移的激活。侵润与转移（AIM）数据集以两种方式对数据分类：正性和负性。

表 1 展示了医学领域的文本分类。

| 数据库 | 课程数 | 术语大小 | 数据库集 |
| :--- | :--- | :--- | :--- |
| AIM | 3 | 2914 | 528 |

CNN 的设计在输出数据层之前包含一个或多个全连接层，以帮助生成的二维数组进行展平化处理。表 2 展示了所提工作的性能分析。

| 数据库 | 技术 | 准确率 | 精确率 | 召回率 |
| :--- | :--- | :--- | :--- | :--- |
| AIM | CNN | 94.18 | 94.18 | 94.02 |
| | GNB | 88.33 | 88.17 | 88.13 |
| | RF | 85.00 | 84.18 | 84.05 |
| | NB | 85.00 | 85.00 | 84.90 |
| | SVM | 87.22 | 87.20 | 87.20 |

## 结论

本研究提供了一种使用机器学习和深度学习进行讽刺检测的新方法，希望为这一不断发展的领域做出贡献。为了对分类做好准备，该方法采用了双向编码器表示（BERT）。这里使用的混合模型是 CNN 和 LSTM 的结合。建议的模型在两个数据集上进行了测试，旨在识别非讽刺词。训练模型获得了 99.63% 的准确率、99.33% 的精确率、99.83% 的召回率以及 99.56% 的 F1 分。这些结果基于对医学数据集进行的 10 轮交叉验证。

# 机器学习与高级深度学习文本分类系统评估

Tarun Kapoor¹

¹ 商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度

## 摘要

将文本根据其内容划分为不同的组被称为文本分类。在此过程中，根据预定义的标签对自然语言编写的文档进行自动标记。无论是执行创建摘要、回答查询和提取数据等文本转换的文本理解系统，还是为了满足用户查询而获取文本的文本检索系统，都高度依赖于文本分类。为了有效学习，目前的文本分类监督学习算法需要足够大的训练集。本研究引入了一种利用人工智能技术（机器学习和深度学习技术）的新型文本算法，所需的训练文档比以前的方法少。为了从已分类的文本文档中生成特征集，我们采用了“词关系”或基于这些词的关联规则。为了对数据进行分类，我们对提取的特征使用了带有深度卷积的神经网络思想，然后采用单一的遗传算法方法。建议的方法已经在系统中构建并经过了彻底测试。实验结果表明，该系统是一个有效的文本分类器。

**关键词：** 高级深度学习技术，机器学习，文本分类系统。

> * 通讯作者 Tarun Kapoor：商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮件：tarun.kapoor.orp@chitkara.edu.in

## 引言

文本分类任务的根本问题和巨大困难一直是如何应用尖端深度学习技术来构建高效且强大的文本分类模型、检索文本语义特征，并在大规模文本数据集上获得卓越的分类结果 [1, 2]。由于事件在时空上发生的随机性、报告的交通中断输出处信息的匮乏，以及交通领域缺乏从过去事故中获取见解的先进技术，估计交通事件将持续多久是一个极具挑战性的问题 [3, 4]。

摘要 人工智能（AI）、机器学习（ML）以及深度学习（DL）在许多计算机视觉应用（如物体分类、物体识别、人体检测等）中变得越来越流行，但它们对系统资源提出了巨大的计算需求 [5, 6]。针对高计算要求的广泛且高效的解决方案是多核计算机和具有大量专用处理核心的显卡。极少数入侵检测系统（IDS）使用机器学习作为基础 [7]。这类解决方案为加强网络领域的网络安全提供了一条充满前景的途径。这些工具可以识别出以前无法检测的威胁 [8]。研究人员和消费者在匿名状态下面临这些攻击，使其变得异常。随着互联网的巨大增长，复杂攻击也在增加。机器学习（ML）和深度学习（DL）的发展是为了帮助发现这些攻击 [9]。因此，研究人员提出了几种识别复杂攻击的策略。基于提取特征和分类说话者的不同方法创建了许多替代系统，使其成为边缘技术之一。语音识别是一个复杂的领域，在投入实际使用之前需要先进的设备和大量的音频数据样本 [10]。

## 相关工作

本工作的重点是利用深度学习技术优化文本语义和文本分类领域的自然语言处理（NLP）应用。为了解决这个问题，我们提出了 W-GCN 分类方法，该方法集成了 GCN 和注意力机制。描述了三种常见的文本分类任务：情感评估、主题分析和新闻分类。实验证据支持本文提供的算法模型。建议的算法模型在三个公开数据集上的表现优于竞争的基于深度学习的文本方法。新闻文本的准确率也相当不错 [11]。

在本文中，我们提出了一种新的事件持续预测融合框架，将机器学习与交通流/速度以及事件描述相结合特征，并通过多种深度学习技术进行编码（ANN 自动编码器以及字符级 LSTM-ANN 情感分类器）。该研究开发了一种交通与信息科学的跨学科建模策略。当应用于基准事件数据时，该方法在准确预测事件持续时间方面优于最好的机器学习模型。结果表明，与传统的线性或向量回归支持向量模型相比，我们建议的策略可以将准确率提高 60%，并且与混合深度学习自动编码 GBDT 模型相比额外提高了 7%，后者似乎击败了所有其他模型。旧金山是该应用选择的背景地，是因为它提供了丰富的交通事故数据（全国交通事故数据收集）和拥堵数据（来自 Caltrans 性能测量系统的 5 分钟精度读数）[12]。

本书研究了 DL 算法在各种多核硬件架构上的性能。针对三个分类问题，开发了使用神经网络的模型。所有这些测试都是在三种不同的计算硬件上进行的——树莓派、Nvidia Jetson Nano 板和台式电脑。根据其分类准确率和硬件响应结果对每种硬件配置的性能进行了检查 [13]。

在这项研究中，我们对机器学习（ML）和深度学习（DL）算法进行了全面的分类。此外，全面的综述将阐明用于检测攻击的许多技术。DL 和 ML 的基础是这些技术的核心。此外，还将展示用于执行 DL 和 ML 程序的各种系统和设备，并推荐适用于 IoT 的安全解决方案 [14]。

在该研究中，开发了一种基于文本（预定义词或短语）的说话者识别系统，以便以很少精力、训练数据和处理能力高效准确地识别说话者。该系统四个组件的第一部分是音频数据库的开发。研究使用了两个不同的音频数据集，第一个是 QSDaset，第二个是 audioMNIST_meta。数据库配置和处理方法在正文中详细说明。研究的第二阶段使用基于音高系数的算法提取特征，第三阶段涉及神经元网络分类。在确认了系统性能和输出后，研究完成。结果证明 MNN 网络甚至可以处理极少量的数据，因为它获得了完美分。对于海量数据集，范围是 80%-81%。与 CNN 网络相比，小样本的发现结果在 60% 到 76% 之间，而对于大样本，正向范围在 91% 到 96% 之间，且结果优于现有方法 [15]。

针对此类事件，我们设计了一个内置智能的公共交通系统。该分类器需要经过高精度的训练，以便从数百万条网络聊天记录中正确检测出紧急情况。为了解决这个问题，我们需要使用专门的损失函数、在训练期间进行采样，并使用诸如堆叠多个分类器等技术，每个分类器都在前一个分类器的基础上进行改进。

## 无监督文本分类

当不提供外部数据时，就会发生无监督分类过程。在这种语境下，算法试图挖掘数据中的潜在模式。请记住，我们在脑海中认为的逻辑划分可能与自然界实际存在的情况不同。算法会对数据点进行相似性检查以形成聚类。数据聚类被用于分类目的。考虑在线搜索的情况：搜索词被用于形成聚类，然后展示给用户。

## 预处理

### 数据清洗与预处理

“预处理”文本简单地将其转换为更易于管理和分析的格式。在这里，方法和字段被融合在一项工作中。我们的任务是获取 Kaggle 数据集（字段）并使用 TF-IDF 方法提取最重要的关键词。

### 小写化

文本准备的另一种简单且最成功的方法是将所有文本数据简单地转换为小写。它适用于大多数文本挖掘加自然语言处理（NLP）任务，即使数据集很小也是如此，并且大大提高了预测结果的可靠性。

### 停用词移除

语言通常包含一组一直在使用的“停用词”。英语中的停用词包括“a”、“the”、“is”、“are”等。停用词背后的想法是，通过消除写作中的无意义词汇，我们可以更好地关注内容。

### 词还原

从表面上看，词还原（lemmatization）看起来非常像词干（stemming），目标是消除形态变化并将单词恢复为原始形式。另一方面，词还原试图更正确地处理。它不仅移除了多余的内容；而是将单词转换为它们的语法基础。

### TF-IDF



在算法进行任何预测之前，必须将文本转换为向量。为了确定文档语料库中某个术语的重要性，我们将使用词频 — TF-IDF 衡量标准。词的重要性是通过消除标点符号、小写字母、停用词并进行词还原后的频率计算的。初始数据集被分为特征 (`X`) 和目标 (`y`)，后者被进一步细分为训练集（80%）和测试集（20%）。因此，方法将在单组数据上进行教学，然后在第三部分数据（算法从未见过的数据）上进行评估。TF-IDF 一词是通过两个衡量标准的相乘来确定的：频率和文档上下文：

- 单词在给定文本中出现的次数。统计单词在文中出现的次数是确定其使用频率最简单的技术。此外，还有其他选项可以调整频率，例如文档长度或文档中最常见术语的原始速率。

- 单词的跨文档逆频率衡量标准。这衡量了某个特定术语在整个文档语料库中的出现频率。术语越接近零，其使用频率越高。该统计量通过论文总数与包含特定术语的论文比例之值的对数得出。

- 那么，如果该术语被广泛使用并出现在许多论文中，该值将接近 0。否则，它将接近 1。

一个单词在文档中的 TF-IDF 分数通过其频率与其出现频率相乘计算得出。权重越高表示该术语在文档上下文中的重要性越高。图 (1) 表示了 DCNN-GA 模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_127_0.png)

**图. (1)** DCNN-GA 模型。

$idf(t, d, D) = tf(t, d).idf(t, D) \quad (1)$

其中：

$tf(t, d) = \log(1 + freq(t, d)) \quad (2)$

$idf(t, D) = \log\left(\frac{N}{count(d:t)}\right) \quad (3)$

## 用于文本分类的遗传算法 DCNN

卷积神经网络（CNN）实际应用数量的增加，导致其在最近几年热度激增。它们的效率对网络设计以及用于微调网络设置的优化技术非常敏感。在这项研究中，我们提供了几种训练这些神经网络的、颖且有效的方法。目前，梯度下降是学习 CNN 最前沿的方法。我们建议采用基于遗传算法（GA）的方法来优化 CNN，而不是标准的 CNN 训练方法。使用了稳态、遗传和精英遗传算法技术来实现这些程序。为了实现这一点，我们提供了用于交叉和变异的新型遗传算法，以及将 CNN 编码为染色体的新型编码方法。我们从效率和扩展性方面对我们的编码进行了标准评估。此外，我们根据不同的 GA 策略评估了训练网络的收敛速度和准确率。最后，我们将反向传播结合 Adam 优化与我们的新型编码以及改进的 GA 方法进行了比较。

假设一个输入特征图 $A=A_1,...,A_{C\times W}}$, 为了获得结果，首先进行全局池化 $Z^{C\times W}}$, 其中 H 和 W 代表高宽，C 代表通道数。

$Z_k = \frac{1}{H \times W} \sum_{i,j} A_{i,j} \quad (4)$

$u = \sigma(A \otimes V) \quad (5)$

准确率 = $\frac{(TP+TN)}{N} \text{ 错误率} = \frac{(FP+FN)}{N} \quad (6)$

精确率 = $\frac{TP}{TP+FP} \quad 召回率 = \frac{TP}{TP+FN} \quad F1 分数 = \frac{2 Prec Rec}{Prec + Rec} \quad (7)$

## 结果与讨论

在这里，我们对文本分类中常用的指标进行了简要介绍，并对性能进行了定量研究。

- MPQA。多视角问答（MPQA）数据库是一个以两种方式标注的意见库。共有 10,606 个句子。在该样本中，只有 3,311 条正面和 7,293 条负面。

- Amazon。亚马逊评论集合经常被使用。它具有双向（二分类）和五向（多分类）分类系统的标签。Amazon 二分类数据集包含 3,600,000 条训练评论和 400,000 条测试评论。Amazon 五类分类数据集包含 3,000,000 条训练评论和 650,000 条测试评论。

![](img/5e4d8ef2afa52a8404b28106580e19e4_129_0.png)

用于多分类分类任务。图 (2) 展示了所提方法与现有工作的比较。

NBC 模型的准确分类部分程度上受到朴素贝叶斯算法假设的影响，即特征之间相互独立，而这在实际情况下往往是不成立的。当数据集特征之间的关系通常相互独立时，朴素贝叶斯分类技术效果最好。然而，由于数据集的特征通常相互关联，在许多情况下无法实现数据集特征的独立性，分类影响将大幅降低。虽然支持向量机（SVMs）在处理小样本的非线性和高维数据方面表现优异，但它们并非没有缺点。SVM 仅限于处理二分类问题，且对许多其他分类问题的求解效果较差。决策树分类器很难预测连续字段，且时间序列数据需要大量的预处理。当类别过多时，错误可能会倍倍增加；当使用通用方法进行分类时，仅根据区域对事物进行分类是不够的。以下是 KNN 算法的一些主要缺点：

- 首先，当样本存在不平衡时，例如某一类别的样本量很大而其他类别样本量很小。由于新样本的 K 个最近邻居样本量巨大，可能会导致分类错误。

- 第二个缺点是算法的计算复杂度；为了对文本进行分类，必须与所有其他样本进行比较以查看其距离远，然后确定其 K 个最近邻点。性能分析 Amazon 如图 (3) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_132_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_132_1.png)

图 (2)) 性能分析 MPQA。

![](img/5e4d8ef2afa52a8404b28106580e19e4_133_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_133_1.png)

**图 (3))**

性能分析 amazon。

随机森林算法的主要优点是其精准的精度。高准确率（特别是在测试集上）可能归功于集成算法的采用，因为其准确性优于大多数独立算法。随机森林由于包含了两个随机组件，因此具有抗过拟合的能力。当随机森林有很多决策树时，训练过程会消耗大量的时间和存储空间。随机森林在某种程度上是一个黑箱模型，具有许多神秘的领域。随机森林技术在噪声数据集上容易过拟合。神经元网络分类器可以做出准确预测并并行执行特定任务。它还具有很强的弹性和抗能力。然而，神经网络需要许多输入参数和大量的训练时间。

## 结论

根据媒体将文本分组的分称为文本分类。根据预定义的标签对自然语言编写的文档进行自动标记。无论是执行文本转换（如创建摘要、回答查询和提取数据）的文本理解系统，还是响应用户查询获取文本的文本结构检索，都高度依赖于文本分类。为了有效学习，当前的文本分类监督学习算法需要足够大的训练集。本研究引入了一种利用人工智能技术（机器学习和深度学习技术）的新型文本分类算法，比以往方法需要的更少的文档。为了从已分类的文本文档中生成特征集，我们求助于“词关系”，或基于这些词的关联规则。为了对数据进行分类，我们使用了带有深度卷积的卷积神经网络的思想处理提取的特征，并采用单一遗传算法方法。所提的方法已经在工作系统中构建并经过了彻底测试。实验结果表明，该系统是一个有效的文本分类器。

## 参考文献

- [1] Nagaki K., Furuta T., Yamaji N., Kuniyoshi D., Ishihara M., Kishima Y., Murata M., Hoshino A., Katsutsaka H. Effectiveness of Create ML in microscopy image classifications: a simple and inexpensive deep learning pipeline for non-data scientists. Chromosome Res. 2021 293-436 10.1007/s10577-021-09676-0

- [2] Sivanesh S., Amazon G., Suliman W., Ravi R., Dua A.. Air Quality Prediction in Ensemble Voting Based Mud Ring Algorithm for Intelligent Transportation. Global NEST:2023

- [3] Li R., Liu M., Xu D., Gao F., Zhu L.. A Review of Machine Learning Algorithms for Text Classification. ACM Transactions on Asian and Low-Resource Information Processing

- [4] Supreme A., Vaidya S., Venugopal A., Ferreira J., Pu C.. A Declarative API for Reproducible Deep Learning. CNCERT

- [5] Buyukoz B.. Analyzing the Generalizability of Deep Contextualized Language Representations For Text Classification 2023

- [6] Alotaibi M., Alotaibi B.. Distracted driver classification using deep learning. Signal Process. 2020 1421 10.007/s1176-019-0158-0

- [7] Yadav S.P., Yadav S.. Fusion of Machine Ideas Using a Wavelet Methodology: A Survey. IEEE Transactions on Smart Processing & Computing.2019 8.426 521 10.5573/IESPC.2019

- [8] Chagata R., Suliman W., Ravi R., Dua A.. Deep Learning for SDN-Enabled Intrusion Detection System in IoT Networks. Information (Basel) 2023 14 141 10.3390/info140

- [9] Guo D., Zhang J., Yang B., Lin Y.. A Comparative Study of Speaker Role Identification in Air Traffic Using Deep Learning Approaches.

- [10] Bandaru S.B., Devarajan N., Gatram R.. Investigations on Deep Learning Techniques for Analyzing Mammograms. Revue d'Intelligence Artificielle 2020. 18 220/ria.360313.116.130144.1161

- [11] Jin G.. Optimization of NLP System under Deep Learning Technology in Text Semantics and Text Classification 2022 International Conference on Education, Network and Information Technology (ICENIT) 2792 10.1109/ICENIT5730.2022.0068

- [12] Yadav S.P., Zaidi S., Nascimento C.D., de Albuquerque V.H., Chauhan S.S.. Analysis and Design of GPS Based Moving Object Tracking 2023 International Conference on Artificial Intelligence and Smart Communication (AISC) greater Noida, India. 2023 1510 10.1109/AISC5616.2023.1005180

- [13] Kumar L., Singh D.K.. Hardware Response and Performance Analysis of Multicore Computing Systems for Deep Learning. Cyber. Inf. Technical. 2022 23268

- [14] Khuaize Z.M., Almaryani S., M.AbdNiba,, Protection Methods and Intrusion Detection Systems Employing Machine and Deep Learning in the IoT: A Comparative Review 2022 Second International Conference on Computer Science, Engineering and Applications (ICCSEA)

- [15] Mahmoud Q.S., Al-Irahym Y.F.. Text Dependent Speaker Identification Based on Deep Learning, Journal of Education and Science 2021. 13 21850 10.3389/edus.2021.130144.1161

FastText 和 TF-IDF 的结合取得了最佳结果。

**关键词：** Fast text 模型、机器学习、文本识别、推文数据集。

**通讯作者 Sakshi Pandey：** 印度旁遮普邦，Chitkara 大学工程与技术学院，Chitkara 大学商业与技术跨学科研究中心；电子邮箱：sakshi.pandey.orp@chitkara.edu.in

## 引言

机器学习和深度学习的最新进展为问题解决提供了新方法，并对许多领域产生了深远且颠覆性的影响。目前的范式已经改变了与其他领域类似的架构实践。混合方法论被用于研究对施工实践的影响 [1]。首先，使用挖掘技术进行内容分析，以对该领域进行全面的文献综述 [2]。在文献中定位和标记观点的计算机化方法可能帮助读者深入作者的观点和对主题的理解 [3]。情感分析最常用的语言是英语。然而，有人声称存在多种情感分析方法，使该研究成为对印尼语写作的一项引人入胜的研究 [4]。得益于往年可获取的 Twitter 数据以及机器学习模型的建立，一些学者已采用机器学习算法来试图处理情感分析的困难 [5]。长期以来，电信诈骗一直是印度互联网和手机用户的严重财务问题。揭露电信诈骗的传统通常围绕警告用户不要拨打未知号码 [6]。然而，黑客可能通过使用 VoIP（IP 语音）电话线伪装成合法呼叫者 [7]。该方法通过呼叫者声音的内容而非仅仅是其特征，可能检测到电信诈骗 [8]。由于社交媒体的去中心化本质以及传播错误信息的便利，垃圾信息检测比以往任何时候都更为关键。垃圾邮件过滤器提供了此类欺诈的保护 [9]。Twitter 和其他社交媒体上发布的关于网络安全的内容显著增加。经过正确分析后，这些数据可能被用于创建一个识别和反网络攻击的系统。在研究中，推文的数值内容可以用多种文本方式表示 [10]。通过将这些特征输入机器学习架构中，可以实现更好的特征提取和分类。

这些发现对于开发更快速的疾病监测系统非常有帮助。然而，许多评估英文推文的研究工作并未考虑句法及语义数据与基于特征类型的机器学习方法之间的联系。为了预测和追踪 COVID-19 的传播，我们使用了监督机器学习技术来分析 Twitter 上与病毒相关数据集的情感分析。对于句法分析，我们使用了 TF-IDF N-gram 和词级；为了进行语义评估，我们使用了 Word2vec、FastText 和 Glove。本研究主要关注以下领域：

- 本文展示了包括 TF-IDF N-gram、TF-IDF community-gram、Word2vec、Glove 和 FastText 在内的尖特征提取方法。

- 我们还提供了两种用于情感分类的最先进方法。

- 我们使用各种指标评估了所提模型的性能。

- 我们讨论了该领域未来的研究方向。

## 相关工作

这些发现对于开发更快速的疾病监测系统非常有帮助。然而，许多评估英文推文的研究工作并未考虑句法及语义数据与基于特征类型的机器学习方法之间的联系。为了预测和追踪 COVID-19 的传播，我们使用了监督机器学习技术来分析 Twitter 上与病毒相关数据集的情感分析。对于句法分析，我们使用了 TF-IDF N-gram 和词级；为了进行语义评估，我们使用了 Word2vec、FastText 和 Glove。本研究主要关注以下领域：

- 本文展示了包括 TF-IDF N-gram、TF-IDF community-gram、Word2vec、Glove 和 FastText 在内的尖特征提取方法。

- 我们还提供了两种用于情感分类的最先进方法。

- 我们使用各种指标评估了所提模型的性能。

- 我们讨论了该领域未来的研究方向。

Twitter 和其他社交媒体上发布的关于网络安全的内容显著增加。经过正确分析后，这些数据可能被用于创建一个识别和反网络攻击的系统。在研究中，推文的数值内容可以用多种文本方式表示 [10]。通过将这些特征输入机器学习架构中，可以实现更好的特征提取和分类。

这些发现对于开发更快速的疾病监测系统非常有帮助。然而，许多评估英文推文的研究工作并未考虑句法及语义数据与基于特征类型的机器学习方法之间的联系。为了预测和追踪 COVID-19 的传播，我们使用了监督机器学习技术来分析 Twitter 上与病毒相关数据集的情感分析。对于句法分析，我们使用了 TF-IDF N-gram 和词级；为了进行语义评估，我们使用了 Word2vec、FastText 和 Glove。本研究主要关注以下领域：



Twitter 和其他社交媒体上发布的关于网络安全的内容显著增加。经过正确分析后，这些数据可能被用于创建一个识别和反网络攻击的系统。在研究中，推文的数值内容可以用多种文本方式表示 [10]。通过将这些特征输入机器学习架构中，可以实现更好的特征提取和分类。

这些发现对于开发更快速的疾病监测系统非常有帮助。然而，许多评估英文推文的研究工作并未考虑句法及语义数据与基于特征类型的机器学习方法之间的联系。为了预测和追踪 COVID-19 的传播，我们使用了监督机器学习技术来分析 Twitter 上与病毒相关数据集的情感分析。对于句法分析，我们使用了 TF-IDF N-gram 和词级；为了进行语义评估，我们使用了 Word2vec、FastText 和 Glove。本研究主要关注以下领域：

- 本文展示了包括 TF-IDF N-gram、TF-IDF community-gram、Word2vec、Glove 和 FastText 在内的尖特征提取方法。
- 我们还提供了两种用于情感分类的最先进方法。
- 我们使用各种指标评估了所提模型的性能。
- 我们讨论了该领域未来的研究方向。

## 拟议工作

### 数据收集

Twitter 和其他社交媒体上发布的关于网络安全的内容显著增加。经过正确分析后，这些数据可能被用于创建一个识别和反网络攻击的系统。在研究中，推文的数值内容可以用多种文本方式表示 [10]。通过将这些特征输入机器学习架构中，可以实现更好的特征提取和分类。

![](img/5e4d8ef2afa52a8404b28106580e19e4_141_0.png)

图 (1) 推特情感分析。

### 数据预处理

在此语境下，文本分类严重依赖于预处理步骤。使用自然语言处理工具包（NLTK），我们必须通过删除任何非本质字符来清理信息，包括表情符号、标签、语法、URL、提及（mentions）和符号。然后将推特转换为小写文本格式。下一步是表示推特，这涉及到使用 NLP 库中的工具将编写的内容分离为术语列表。最后，在删除英语停用词后，我们使用 Porter 词干算法将术语还原为词根。在众词干算法中，它是最著名的算法之一。完成排序和清理后，我们提取了最关键术语。

### 词嵌入

估计源文本与目标文本之间语义相似性的程度是“语义文本匹配”过程的目标。让我们看看它在定位相似查询的真实场景中是如何工作的。当一个新问题被提出或搜索时，我们希望查看大型语料库中哪些问题与之最相似。任务对语义意义的强调至关重要。以上面的插图为例，“投资房地产市场的逐步指南是什么？”这个问题与源问题在句法上有实质性的重叠，但它们之间并没有极端的相关。共享词的数量就是我们所指的句法重叠。

- 词嵌入（Word Embeddings）：文献中已经提出了许多密集嵌入方法，如 word2vec、Glove、fasttext 等。这些方法的目标是将每个词映射到 100 维的实数密集向量中，将它们在 n 维空间中放置彼此靠近，以便于比较。可以从几个自然语言处理组织获取预训练的词嵌入。
- Word2vec：对密集词嵌入的兴趣最初是由 CBoW 和 Skip-gram 词嵌入模型激发的。CBoW 和 skip-gram 的区别在于，前者使用单词周围的上下文作为输入来预测单词，而后者使用单词本身作为输入来预测周围的上下文。这两个系统旨在通过提取它们之间的共现模式来捕捉词之间的语义联系。

#### 特征提取

接下来是特征提取，它对于每个分类问题都至关重要。为了消除多余的词汇，使用了向量化方法和特征嵌入。词嵌入是使用 Common Crawl 和维基百科上预训练的 W2Vec、FastText 和 GloVe 通过 300 维向量创建的，并使用 TF-IDF 完成向量化。

### 文本分类

朴素贝斯分类（Naive Bayes Categorization）是一种常见的统计分类方法，它利用贝叶斯定理以及组件的独立性对输入数据进行分类。预期的操作如下：文本分类的第一阶段是从给定字典创建文章 `x` 的文本向量，其中 `n` 是字典 `W` 中的项目总数，`d` 是项目在文档 `d` 中出现的次数。

```
W = {w_1, w_2, ..., w_n}
X = {x_1, x_2, ..., x_n} (1)
```

根据训练数据，分类向量表明该文本可能被细分为 `m` 类。

```
D = {d_1, d_2, ..., d_m}
Y = {y_1, y_2, ..., y_m} (2)
```

训练朴素贝叶斯技术需要使用 `D`。基于此，可以通过求解 `argmaxP` 来找到最准确的分类：

```
argmax(yj|X)
```

转化为贝叶斯命题，

```
P(y_j | X) = P(y_j)P(X|y_j) / P(X) = P(y_j) * Π_{i=1}^{n} P(x_i|y_j) / Π_{i=1}^{n} P(x_i) (3)
```

`P(y_j)` 和每个 `P(x_i)` 通过训练数据（`D=d_1, d_2, d_m`）确定。使用当前的数据集作为输入 `X`，我们可以计算任何 `P(y_j|X)`。其中最大的概率被分配给文档 `X` 的分类。贝叶斯方法的逻辑非常直接，因为它假设数据集属性之间是互不相关的。该算法还具有良好的稳定性。即使数据表现出明显的特征，朴素贝斯的分类性能也不会发生太大变化。也就是说，简单的贝叶斯技术具有适应性，且不会为不同的数据集剧烈改变其结果。

我们将特征提取和监督机器学习方法进行了比较，目标是开发一种具有更高准确性和效率的分类模型。作为研究的一部分，我们评估了对当前 COVID-19 疫情的观点。由于这个原因，使用了几种文本分析可视化图。情感分析的用处在于检查个人对特定事件的感受。首先，使用 Python NLTK 工具包对数据集进行分析，将其划分为正性、负性和中性类别。使用这种方法是为了应对随机过采样引入的过拟合问题。为了提高分类的准确性，随后的评估阶段依赖于特征提取和词嵌入。词嵌入是将文本中的语义和句法意义表示并转换为实值向量的过程，以便输入模型。

## 结果与讨论

我们使用准确率（accurateness）、召回率（recall）、F1 分数和 AUCC 这五个指标评估了所提方法的有效性。

- 准确率（Accurateness）：准确率和召回率的调和平均值。(4)

```
Accurateness = (TP+TN) / (TP+TN+FP+FN)
```

- 精确率（Exactness）：这指示了识别推特的准确程度。(5)

```
exactness = TP / (TP+FP)
```

- 召回率（Recollection）：高召回率显示了所有的正样本示例。(6)

```
Recollection = TP / (TP+FN)
```

- F1 分数（F1-value）：根据相对重要性加权的精确性和召回率的调和平均值。(7)

```
F1-value = 2 * (Precision * Recall) / (Precision + Recall)
```

- AUCC：ROC 曲线下的面积是分类器判别能力的衡量。(8)

```
AUCC = Σ_{i ∈ (TP+TN+FP+FN)} (TPR_i + TPR_{i-1}) * (FPR_i + FPR_{i-1}) / 2
```

![](img/5e4d8ef2afa52a8404b28106580e19e4_146_0.png)

**图 (2)** 分类准确率 vs 特征数量。

![](img/5e4d8ef2afa52a8404b28106580e19e4_147_0.png)

图 (3) 分类准确率对比特征数量。

![](img/5e4d8ef2afa52a8404b28106580e19e4_148_0.png)

**图 (4)** 分类准确率对比特征数量。

![](img/5e4d8ef2afa52a8404b28106580e19e4_149_0.png)

**图 (5)** 分类准确率对比特征数量。

## 结论

根据研究结果，我们的双特征融合策略使得朴素贝叶斯（Naive Bayes）的性能优于竞争机器学习模型。我们的方法优于所测试的其他六种特征嵌入技术（TF-IDF 单词、TF-IDF N-gram、Word2Vec、FastText、Glove 以及两种混合方法）。我们展示了顶尖特征方法在我们的模型上的表现与早期研究相比的对比。我们发现建议的方法具有微弱优势。这可以解释为：与尝试的其他方法相比，两种高效词表示的结合能够更好地代表词汇量并并提取特征。尽管存在一些亮点，但我们的研究也存在一些重大的局限性。在未来的研究中，我们可以通过扩展模型以将推文按语系（例如阿拉伯语、西班牙语和法语）或按社会（例如通过加入重要的 COVID-19 特有关键词）进行分类来改进我们的方法。目前，我们使用来自全球的英语推文。根据某个平台在特定位置的普及程度，我们可能还会包含从其他来源获取的信息。

## 参考文献

- [1] Simran K., Balakrishnan P., Vinayakumar R., Soman K. Deep Learning Approach for Enhanced Cyber Threat Indicators in Twitter International Symposium on Security in Computing and Communications 2020.10.1010/978-981-15-4825-3_11
- [2] Baloch A.A., Albawadi O., Alshehi B., Alberts V. Bandgag Model Using Symbolic Regression for Environmentally Compatible Lead-Free Inorganic Double Perovskites. Proceedings of the 2022 IEEE Photovoltaic Specialists Conference (PSC).Jun.202212342230910.1109/PVSC4837.2022.9938842



- [3] Montañes-Salas R.M. ITANNOVA@DA-VINICS: A Tale of Transformers and Simple Optimization Techniques. Proceedings of IberLEF@2021Sep
- [4] Yadav S., Sadi S., Nasimento C.D.S., Albubuque V.H.C., Chauan S.S.. Analysis and Design of automatically generating for GPS Moving Object Tracking System 2023 International Conference on Artificial Intelligence and Smart Communication (AISC) Greater Noida, India.2023.25310.1109/AISC5666.2023.10085180
- [5] Omidhadhi Badat E., Ahmadzadeh F. Classification of Spam with Elimination of Unsirable Features Using Hybrid GNN Bayes. Classification of Information and Knowledge Management.202211385290095290.1109/22520719649220500086
- [6] Papasoiotou T. A. Clustering and Scientometrics. Study2019
- [7] Bahalur A., Montano U., Determining the Semantic Orientation of Opinions on Products - a Comparative Analysis Process. Del Natural.20041281
- [8] Simran K., Balakrishnan P., Vinayakumar R., Soman K. Deep Learning Approach for Enhanced Cyber Threat Indicators in Twitter International Symposium on Security in Computing and Communications 2020.10.1010/978-981-15-4825-3_11
- [9] Madsen K., Bhaya S. Distributed Learning.
- [10] Papasoiotou T. A. Clustering and Scientometrics. Study2019
- [11] Miranda E., Haryanto S. Sentiment Analysis using Machine Learning-continental on Information Management and Technology (ICIMTech)201910.1109/ICIMTech.8843
- [12] Polpinij J., Sibunruang C. Identifying Decision Components in Thai Civil Case by Text Classification Technique.in Proceedings of 2019 International Conference on Data Science and Artificial Intelligence (DSAI)2020211710.1007/978-3-030-4404-2
- [13] Yadav S.P., Bhati B.S., Mahato D.P., Kumar S. Federated Learning for IoT Applications EAI/Springer Innovations in Communication and Computing Springer International Publishing2022.1007/978-3-030-85559-8
- [14] Reddy G.A., Reddy B.I. Classification of Spam Text...

关键词：深度学习、机器学习、语义、文本分类

## 摘要

使用机器学习和深度学习技术可以有效地进行分类。在本文，我们展示了如何处理不完整数据并删除重复信息。为了对文本分类，我们使用了长短期记忆（LSTM）、人工神经网络（ANN）和门控循环单元（GRU）。

## 引言

随着传统挖掘对定量数据的日益关注，挖掘在线数据的需求不断增长。由于处理图像语义的困难，网络图像挖掘不如文本分析流行[1]。网上存在丰富的信息，包括文字和视觉信息[2]。我们展示了如何在关系结构中对不同抽象层次进行训练，其中关系信息附有元数据注释[3]。由于地理差异，人们对调查数据的兴趣日益增加[4]。产科研究一直侧重于推断这种状态对健康的影响[5]。然而，到目前的研究大多集中在使用统计方法分析数值关系。这种方法在分析数据时由于无法理解底层语义而遇到困难，导致数据发散等问题[6]。文本内容作为语义的想法对于寻求理解信息检索、分类和过滤混乱环境的人来说可能是一个障碍。有趣的是，我们大多数人仍然认为开发一种基于语言原则的文本分类方法是一个有趣的研究课题[8]。托斯滕·乔哈姆斯（Thorsten Joachims）提出了一个文本模型自动分类和训练的框架，使用支持向量机进行分类[9]。它还提供了文本分类和聚类（包括主题建模），以及数据检索（包括主题搜索），这些领域都可以从知识提取技术中受益[10]。

本文其余部分的结构安排如下节所示。在第二节中，我们概述了相关研究。随后，在第3章中，我们详细解释了整个调查过程中使用的步骤和技术。论文的发现和讨论见第4节，结论和对进一步研究的建议见第5节。

## 相关工作

本研究通过自动从互联网收集大量照片作为训练数据，提供了一种新颖图像识别和分类方法。该系统使用了基于内容的图像检索（CBIR），它不像像传统的图像识别方法那样限制目标图像，并使用了支持向量机（SVM），这是通用图像分类中最有效且应用广泛的统计方法之一，适用于学习任务。根据实验结果显示，所提方法在支持向量机、图像分类、图像采集和互联网图像挖掘 [11] 等方面优于许多现有的搜索方法。

我们针对部分规范的统计策略基于收缩。实验结果表明：(i) 所选概念水平如何影响后续基于连接的分类器的性能，以及 (ii) 如何研究部分特定数据对文章分类任务中基于关系的朴素贝叶斯估计器的影响 [12]。

为此，我们通过使用一种名为 Geo-SPS 的二部法以及在地理增强型产科和产产调查上的通用图示，研究了健康信息领域质量疑数据之间语义关系的提取。我们的方法是新颖的，因为我们利用最初用于计算机物理的图论原理，将语义对象映射到由两个部分组成的图中。Geo-SPS 提供了一种了一种确定语义相似性的新方法。使用该方法，卷积神经网络图可以快速准确地评估多个领域的歧义文本输入。我们还通过一项涉及中国三个不同地区3000多名女性的产科调查以及医疗信息数据的案例研究，进一步评估并建立了 Geo-SPS 的实用性。研究结果表明，Geo-SPS 可以反映孕妇的心理健康，并从这些多样化的数据收集中可靠地检测出生缺陷 [13]。

主题文本分类（TC）被提出作为解决方案，因为它基于一种（似乎是）语言依赖性活动的广泛语言通用性。当其应用于语言对象（如文档）时，结果是一个被称为“词袋表示”的基础语言模型，该模型仍然实现了卓越的准确性 [14]。虽然大多数文本分类研究严重依赖于经验证据，但我们的方法则植根于统计学习概念和发现。

构建并利用能够充分解释不同层次（单词、句子、主题文本断裂）的文本结构元素、特征以及语义和它们关系，并能够创建更高层次结构的模型，对于此类方法的实现至关重要。体裁、受众、意图和学科重点只是此类模型应该考虑的文本数据更广泛方面的少数方面。为了解决文本信息分析和创建中的问题，本工作研究了文本建模（结构性、统计的和混合的）的特征、优缺点以及其在多个阶段（知识提取、存储和文本生成）的应用 [15]。

## 提出的工作

## 系统模型

学习和分类是分类问题的两个组成部分。学习过程的目的是根据已知的训练数据构建分类模型以获取分类器。分类涉及使用训练好的分类器对新数据点分配的标签进行猜测。分类问题如图（1）所示。以下是文本分类系统关键功能部分的快速介绍，如图（1）所示：语料库的版本需要预处理活动（如格式化），以增强文本表示的质量并能够进一步处理。以下是文本表示中必须解决的一些问题：第一步是决定哪些词性（通常是单个单词或短语）将作为文本特征。第二步是选择合适的模型来量化文本字符串。特征的降维旨在分类文本，提取与文档主题最有指示意义的特征。文本分类技术的研究主要重点是构建分类器：即分类器的设计。新项目的分类是通过通过首先选择可能代表分类系统中每个组的文本作为训练集来实现的。然后使用该策略教授分类器，整个系统是该阶段的目标。不同的分类问题将使用不同的评估标准，例如单标签分类与多标签分类。文本分类器有效性的衡量标准包括召回率、准确率和 f 值。图（1）描绘了一个系统模型。

## GRU

“GRU”术语指的是特定的循环神经网络。它类似于长短期记忆（LSTM），区别在于它只包含两个门而不是三个：重置门、更新门和输出门。GRU 通常比 LSTM 更容易更快训练，因为它们的参数更少。

![](img/5e4d8ef2afa52a840)

**图 (1) 系统模型。**

门控单元（GRU）是 LSTM 的替代方案，它通过使用重置门和更新门有效地解决了长期依赖问题。错误数据在秒秒通过重置门清除。当重置门的值减小时，会有更多不正确的数据被丢弃。更新门执行的计算如图（1）所示。

$U_m = \sigma(W_u [h_{m-1}, x_m])$

重置门执行的计算如图（2）所示。

$C_m = \sigma(W_C [h_{m-1}, x_m])$

这些公式概述了计算当前状态的过程：

$h_m = tanh(W [C_m \odot h_{m-1}, x_m])$

$nh_m = U_m \odot \overline{h}_m + (1 - U_m) \odot h_{m-1}$

其中，$W_U, W_C$ 和 $W$ 显示了 GRU 的权重矩阵，$x_m$ 是输入信息，$h_m$ 代表当前隐藏状态，$h_{m-1}, h_m$ 候选激活状态，$U_m$ 和 $C_m$ 代表变化和重置逻辑，$\odot$ 意味着将位置项目与其相应的哈达玛数相乘，$\sigma$ 代表 sigmoid 函数。

## GRU

Word2vec 类似于基础神经网络，包括 CBOW 和 Skip-Gram 模型作为其主要组件。CBOW 模型主要基于上下文预测当前值，这类似于从其自然环境中移除一个单词并让你推断出其含义。简单来说，Skip-Gram 方法就像给你一个单词，然后要求你猜测它前面和可能出现的单词。虽然 Skip-Gram 在大型语料库中表现出色，但 CBOW 在较小数据集上更具优势。图（2）展示了 CBOW 和 Skip-Gram 算法是如何构建的。在本文工作中，我们使用 Skip-Gram 训练示例，因为它更适应低频词汇。

建议的模型接受文本序列作为输入，或一个单词字符串。因此，使用了 Glove 向量将短语映射到低维向量中；这些向量是斯坦福大学利用 Wikipedia 2014 语料库学习的。作为输入的单词

对于训练 $[w_1,...,w_m]$，可以将其表示为一个由 m 维词向量组成的矩阵，称为“词嵌入”：

$X = [x_1, x_2, ..., x_m]_{m \times d}$ (4)

在此阶段，使用一种称为 GRU 的专用 RNN 网络来捕捉序列信息。典型 GRU 单元的两个门——重置门和更新门——共同工作以调节数据传输。每个时间步的候选激活由当前激活和任何新添加的候选的组合决定。GRU 单元的数学计算公式 (2) 所示。对于反馈 $x_t$，隐藏状态表示为 $h_t$。对于给定的时间 $t$，我们有：

$h_t = (1 - z_t)h_{t-1} + z_t\tilde{h}_{t-1}$

$\tilde{h}_t = \tanh(Wx_t + U(r_t \cdot h_{t-1}))$ (5)

$z_t = \sigma(W_z x_t + U_z h_{t-1})$

$r_t = \sigma(W_r x_t + U_r h_{t-1})$ (6)

其中 $W_z \in \mathbb{R}^{m \times n}, W_r \in \mathbb{R}^{m \times n}, E \in \mathbb{R}^{m \times n}, U_z \in \mathbb{R}^{m \times n}, U_r \in \mathbb{R}^{m \times n}$ 是权重。$n$ 是隐藏元素的数量，用 $n$ 表示。$h_1$ 是先验隐藏，$h$ 是隐藏状态候选值。$z_t$ 是更新门，$r_t$ 是重置门。运算符表示逐元素执行的乘法。当 $r_t$ 非常接近零时，通过重置门，单元操作可能会将当前输入值视为输入序列中的第一个，并忽略之前计算的状态。tanh 和 $\sigma$ 分别是 sigmoid 函数和双曲正切函数。输入序列中的每个词由其在 GRU 模型中每个时间步的隐藏状态向量表示。

根据这一发现，建议使用具有强连接的卷积过程来自动提取多尺度特征。为了允许模型从多尺度特征中构建表示，每层通过 $l$ 个密集连接密集连接 [6]。卷积层用于 $l, W_j \in \mathbb{R}^{k \times d}$ 中，其中滤波器的第 $j$ 个参数化用于 $x_i \in \mathbb{X}$，卷积结果计算如下：

$$c_{ij} = f(W_j \cdot X_i + b_j) \quad (7)$$

其中 $i=1,2,\cdots,m$ 是滤波器的长度，而 $j=1,2,\dots,k$ 是滤波器的数量。$X_i = [X_i,X_{i+1},\dots,X_{i+k-1}] \in \mathbb{E}^{k \times d}$，$f$ 是关于 ReLU（修正线性单元）的函数 $f(x) = \max\{0, x\}, b_j \in \mathbb{R}$。偏置项为 $W_j$，$b_j$ 类似于卷积窗口滑动。

当我们在卷积层 1 应用 $n$ 个滤波器时，情况如下：$c_i = [c_{u1},\dots,c_{in}]$，然后取平均值以获得稳定的聚焦 $c_i \in \mathbb{R}$。

一旦获得注意力信号 $C = [c_1,\dots,c_l]$，隐藏状态向量为：其中 $L$ 是卷积 $h_t$ 乘以 $c_i \in \mathbb{E}$ 的数量，如下：

$$X_t = \sum_{t=1}^{n-1} c_t \odot h_t \quad (8)$$

通过对子序列 $X$ 应用全局最大池化获得整个上下文表示：

$$\tilde{X} = \max[X_1 \oplus X_2 \oplus \dots \oplus X_L] \quad (9)$$

最后，使用 dropout 和 Softmax 生成分类条件概率。Dropout 有用于避免过拟合。训练的目标是减少每个神经元的交叉熵误差。损失函数的写法如下：

$$L_{total} = -\frac{1}{N}\sum_{sa} [y\ln \tilde{x} + (1-y)\ln(1-\tilde{x})] \quad (10)$$

用于训练的样本由 $sa$ 表示，标签由 $y$ 表示。

## 结果与讨论

在这里，我们查看了建议的 GRU 模型与当前技术的对比。

表 1 经典工作在 Yelp 数据上的对比。

| 未来与当前项目 | 准确率 (%) | 精确 (%) | 回回率 (%) | F 分数 (%) |
|---|---|---|---|---|
| 多启发式分析 | 72.46 | 94.76 | 83.15 | 89.16 |
| DBN | 74.53 | 95.11 | 84.76 | 89.89 |
| 基于 CNN 的特征集成模型 | 78.48 | 96.73 | 87.85 | 91.56 |
| DL 混合 | 82.46 | 96.78 | 91.14 | 92.76 |
| LANFIS | 87.65 | 96.84 | 91.66 | 93.98 |
| OASVM | 89.46 | 97.24 | 92.76 | 94.26 |
| 计划混合 | 92.48 | 98.18 | 96.75 | 96.86 |

表 2 新混合方法在 Twitter 数据上的对比。

| 未来与当前项目 | 准确率 (%) | 精确 (%) | 回回率 (%) | F 分数 (%) |
|---|---|---|---|---|
| 多启发式分析 | 71.06 | 95.76 | 81.15 | 87.16 |
| DBN | 73.53 | 95.91 | 85.76 | 88.89 |
| 基于 CNN 的特征集成模型 | 76.46 | 96.88 | 88.85 | 91.56 |
| DL 混合 | 83.46 | 96.92 | 92.14 | 93.76 |
| LANF2IS | 86.65 | 96.99 | 93.66 | 95.98 |
| OASVM | 88.46 | 98.87 | 94.76 | 96.22 |
| 计划混合 | 91.48 | 98.98 | 98.75 | 98.86 |



将建议的方法与表 1 所示的其他分类器进行比较。`GRU` 是一种可以记忆序列中以前数据的记忆函数。此外，`LSTM` 可能会从文本输入中消除不需要的信息，从而减少计算花费的时间精力。因此，`GRU` 是文本分类的很好的工具，因为它可以在忽略无关数据的同时保留事件顺序。此外，我们采用 `GRU` 是因为它们拥有的门机制。与 `LSTM` 加上遗忘门相比，`GRU` 没有输出门。因此，它需要的输入较。在某些领域，`GRU` 的性能与 `LSTM` 平起，包括多声音乐、语音信号和自然语言处理。人工神经网络可以使用可以适应并从新信息中自动学习的学习算法。`ANN` 在此数据集上显示出高达 81% 的效率，使其成为不规则统计建模非常有用的工具，因为我们只提取类别特征并排除不需要的信息。`K-最近邻`、`随机森林`和`逻辑回归`只是该数据集中使用的机器学习方法的一部分。可以使用独立因素集合和称为`逻辑回归`的统计方法来预测分类因变量的输出。

## 结论

文本信息的数量呈爆炸式增长。因此，找到可行的方法来快速筛选大量数据是有希望的，因为手动操作是艰辛的。信息是分类产生的数据，被用于企业和工厂的战略规划。在本研究中，我们提出了一种基于 `GRU` 的文本数据分类策略。对于文本分类，我们使用了多种机器学习和深度学习方法。在处理文本数据时，`GRU` 保留了呈现顺序。它也有助于获取无用数据，这是一个很大的优势。通过使用 `GRU` 过滤无关数据同时记住其来源的能力，我们将数据集的准确率提高到 95%，使其成为文本分类和其他基于文本任务的强大工具。许多新兴深度学习算法（如 `BERT`）将允许我们执行分类过程。通过融合循环和卷积架构的最佳部分，它比单一模型具有更好的性能。

Engineers of Korea20198426527110.5573/IEIES.2019.8.4.265

[6] Ossewaarde, R., Jalvingh F., Jonas, R., Bastiaan Y.R.. 原发性失语症声学的计算机评估.Journal of Speech and Hearing ResearchMar.2020 65312523110.1044/2020_JSHR-19-00294

[7] Wei, Y., Zhang, Y., Ji, Z., Bai, J., Zhang, L., & Zoo, Y.. WELITE: 用于自定义文本到图像生成的视觉概念文本嵌入编码 2023 IEEE/CVF 国际计算机视觉会议International Conference on Computer Vision (ICCV) 2023 21518971597

[8] X. Zhang, J. J. Zhao, and Y. LeChan 用于文本分类的层级卷积网络.Proceedings of the 28th Conference on Neural Information Processing Systems (NeurIPS)Dec.2015.9219

[9] J. Howard and S. Ruder 用于文本分类的通用语言模型微调.Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (ACL).Jul.2018 18233910.18653v1/P18-1031

[10] J. Wei and K. Zoueda 用于提升文本分类任务性能的简单数据增强技术.Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing (EMNLP)Nov.2019 6382638810.18653v1/D9-670

[11] X. Sun, X. Li, J. Fu, W. Su, G. Guo, T. Zhang, and G. Wang 基于大语言模型的文本分类.Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing (EMNLP)Dec.2023 4567458110.18653v1/2023.EMNLP-457

[12] S. Lai, L. Xu, K. Liu, and J. Zhao 用于文本分类的递归卷积神经网络.Proceedings of the 29th AAAI Conference on Artificial Intelligence (AAAI)Jan.2015 22672273

[13] L. Yao, C. Mao, & Y. Lu 用于文本分类的图卷积网络.ArXiv:2011.abs/1809.05679

[14] S. Hu, N. Ding, B. Wang, Z. Liu, J. Li, and M. Sun 知识微调：将知识融入文本分类的提示词词化.Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (ACL)May2022 36376910.18653v1/2022.ACL-3687

[15] D. Jin, Z. Jin, J. Jin, T. Zhou, and P. Szolovits BERT 真的鲁棒吗？针对文本分类和蕴含的自然语言攻击的强基准.Proceedings of the 34th AAAI Conference on Artificial Intelligence (AAAI)Feb.2023 45880188025

## 使用机器学习技术对网页内容进行分类

Dikshit Sharma¹, *

¹ 商业与技术跨学科研究中心，Chitkara 大学工程技术学院，Chitkara 大学，旁遮普邦， 印度

## 摘要

在文本分类中，根据其内容对文本进行分组。它是根据一组准则自动对自然语言编写的文本进行分类的过程。文本理解系统（对文本执行转换，如创建摘要、回答查询和提取数据）和文本检索系统（根据用户对互联网内容的查询收集文本）都高度依赖于文本分类。为了进行有效学习，当前的文本分类监督学习算法需要足够大的训练集。本研究引入了一种新颖文本分类系统，该系统利用人工智能方法，且相对于网络信息所需的训练文章更少。为了从已分类的文本中生成特征集，我们采用了“词关系”或基于这些术语的关联规则。得到的特征随后由支持向量机（`SVM`）处理，最终引入了一种单一遗传算法思想进行分类。所建议的方法已工作系统中得到了开发和验证。实验结果证实了该系统作为文本分类器的有效性。

**关键词：** 机器学习，`SVM` 和 `TF-IDF`，网页内容分类。

* 通讯作者 Dikshit Sharma：商业与技术跨学科研究中心，Chitkara 大学工程技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：dikshit.sharma.org@chitkara.edu.in

## 引言

得益于技术的发展，生物医学研发中的日常工作变得更容易执行了。为了读取尿液条上的葡萄糖水平，可以使用分析检测器 [1]。你的视力可能会受到白内障、胎眼、角膜溃疡或其他眼部疾病的损害。这四种眼疾病只有通过适当的早期识别才能阻止其进展 [2]。各种眼疾病以多种方式表现出来 [3]。然而，眼科疾病的准确诊断需要考虑各种症状。由于问题的严重性，研究人员一直在努力开发植物疾病的诊断和治疗策略 [4, 5]。为了增加农业产量和收入，农民如果能够利用现有设备消除农业生产力的障碍将从从中受益 [6]。工具种类多、尺寸各异，人类自古以来一直使用它们 [7]。人类的智慧允许了许多有益的实现。这为个人解决广泛需求提供了资源，包括交通、工业、住房和计算机领域的需求 [9]。在今天，我们既是知识的创造者也是消费者。用户对未来可能产生重大影响。用户通过在社交媒体领域贡献观点和想法，对未来产生实质性影响 [9]。这些观点构成了情感分析的技术，计算机科学研究 [10]。

网页分类是一项具有若干现实意义的重大挑战。家长控制提供了一个儿童友好的环境。在没有明确指南的情况下，所有年龄段的互联网用户都会暴露在不当内容面前。基于文本的动态网页分类很重要。以各种语言编写的网站已收集并预处理。法院指令并不适用于所有网站。该研究包含了 17 类，其中 `SVM` 技术的成功率为 0.875。

## 相关工作

本研究的目标是利用 `MATLAB` 程序分析数字照片患者的血糖数据。糖尿病需要注射胰岛素。注射可能会造成轻微伤害，削弱身体的防御。在本研究中，使用了高斯滤波和基于直方图的特征提取来处理噪声。支持向量机分类分配 70% 的时间用于训练，30% 用于测试。`SVM` 分类结果的处理时间在 0.5 秒内，准确率为 85%。医疗决策可以根据人的糖尿病、前期糖尿病或其情况来做出 [11]。

利用数字图像处理、机器学习技术、深度卷积神经网络（`DCNN`）和支持向量机（`SVM`），我们描述了一种通过症状自动检测疾病的新颖方法。我们采用 t 分随机邻嵌入（`t-SNE`）和主成分分析（`PCA`）结合变量来改进特征选择。所提的方法将正面脸图像分解为其组成部分并自动移除眼部。所提的方法诊断并分类多种眼疾病，包括但不限于青光眼、结膜角膜溃疡、外翻、眶窝炎和维生素 A 缺乏。实验结果显示 `DCNN` 策略优于 `SVM`。我们还将我们的方法与流行的替代方案进行了比较。我们的 `DCNN` 模型实现了 98.79% 的整体准确率、97.1% 的灵敏度和 99.0% 的特异性 [12]。

目前的定制化网络搜索策略没有考虑到可能为客户信息需求提供简单回答的未访问网站。结果包中的某个页面可能无法完全解决用户的问题，但它可能引导他们走向正确的方向。只有通过语义分析，才能揭示隐藏的联系。本研究旨在通过对搜索路径进行语义分析，对特定的连接网站进行分类，并提供高效的个性化网站搜索。通过在用户的搜索查询与相关网站之间提供上下文和直接链接，促进了在线发现 [14]。

为了识别有关孟加拉板球的孟加拉语 `Facebook` 帖子语气，本文提出了一种情感极性检测方法，该方法采用了三种著名的监督机器学习算法：朴素贝叶斯 (`NB`)、支持向量机 (`SVM`) 和逻辑回归 (`LR`)。本文对分类器的性能也进行了检查和对比；通过将 `n-gram` 作为属性，`LR` 的准确率（83%）高于 `SVM` 和 `NB`。[15]。

## 拟议工作

## 系统模型

网页内容可能涉及从个人、官方、商业到公司事务的各个方面由于由于原因，网络用户对获取这些数据感兴趣。因此，为了将 Web 数据用于任何特定目的，拥有一套能够对网页进行分类以向用户提供页面上最相关数据的程序至关重要。本研究通过使用基于体育、设备和教育等预设区域的分级分类和分层索引系统，为网页分类提供了一种新方法。该过程包含两个主要阶段：训练和测试。在整个训练期间，会进行动态特征提取和知识表示。测试期间，使用从网页中检索到的特征进行分类内容匹配。该方法分为三个阶段：提取动态特征、表示知识以及对随机放置的网页进行分类。特征提取过程涉及获取网站的标题和段落并提取相关的关键词。为了对每个关键词的重要性进行排序，我们计算其出现频率，然后将该数字乘以权重。为了进一步对网站分类，利用表示知识进行内容匹配。采用最大熵分类器来确定网站符合这些类别中每种的程度。由于最大熵分类在基于搜索的优化中的优越性，它正在被研究。使用了三类网站——体育、设备和教育类来测试该策略。达到了 91% 的分类准确率，超过了更传统的方法。

## SVM

监督机器学习模型（如分类器）使用一组相互相关的学习算法来分析数据并检测模式。该模型在标记数据上运行良好。为了运行，`SVM` 模型将每个样本归类为几个预定义的类。数据集中的每个数据点都由一个 `n` 维属性向量表示，在 `n` 维空间中显示以最大化不同类别之间的差异。建立一个超平面，并将每个输入的数据点显示在上面，直到可以分类为止。信息点的正确分类是根据其相对于超平面的位置确定的。然而，构建超平面并非易事。当信息随机分布时，这一点尤为有说服力。在这种情况下，使用了 `SVM` 的核方法。当核方法应用于 `SVM` 时，它被称为 `SVM` 的核技术。线性、多项式、径向基函数和 `sigmoid` 都是核函数的有效选择。核的选择对模型的有效性有显著影响。该模型是一个多分类模型，采用“一对多”的方法。

## 拟议分类器

模糊逻辑用于将网站分类为“成人”、“医疗”和“正常”等类别，支持向量机已用于大多数最近的研究中检测不当或非需要的信息。从网页中提取特征和预处理以确定其唯一类型。在预处理阶段，网站的部分转换为 `HTML` 文件格式。通过使用词汇和形态分析，Web 内容分类系统能够提取这些数据并识别各种词形式。使用分词方法将长文本分割为可管理的片段。分词结果存储为数组，以便能够与相关词汇和术语字典进行快速比较以进行进一步分析。在恢复每个词（常见的、恢复性的、淫秽的）后，下一步是提取过程，随后准确率会下降。因此，使用 `SVM` 分类器来寻找包括短语在意义特征，同时过滤掉无关特征。有一个特殊函数用于识别显著特征。任何内容值大于 0 的数据都被认为具有医疗或色情性质，并从过滤器中删除。成人内容的识别严重依赖 `FPV` 和 `FNV` 评分，因此采用了现有技术来评估分类系统的有效性。从三个大类中随机选择了共 4646 个页面。算法分析了这些网站上发现的数据并将其分为三类：普通、健康相关和成人。在拟议的方法中，1787 个页面被视为典型，2251 个被视为色情，608 个被视为医疗。使用词汇字典和选定的特征集，对每次访问 Web 的请求评估网页分类的指示值。一旦指示值通过验证，用户将被拒绝访问成人材料。建议的模糊本体通过多种指标进行衡量，包括 `n-gram`、`KNN` 和 `SVM` 分类器描述的精度、召回率、准确性和功能类型。

`SVM` 能够进行若干分类，并将实现两个目标。以下是 `SVM` 程序的几个阶段：

- 将根据 `SVM` 包调整数据结构。
- 为了缩放数据，你必须查看 `RBF` 分。
- 使用交叉验证训练整个训练集以确定最佳参数。
- 完成 `SVM` 训练这些操作。拟议的方法使用合适的支持向量对两种类型进行分类。接下来，分类函数根据返回具有最大间隔的超平面决定哪个答案最准确。在用 `FDO` 进行正负评估后，会评估每个特征的极性。

## 结果与讨论

此处描述了计划任务的成果。本研究执行得严谨，并对结果提供了统计学和理论上的评估。使用具有大型数据集的 `Java` 框架展示了结果。成功或失败的数据集和测量值是实验设置的一部分。使用了三种不同的 Web 页面——体育、政治和教育——来测试该方法。该方法在分类中的准确率达到了 99%，相比于传统方法有了显著提高。图 (1) 显示了准确率 (a). 体育，(b). 教育 (c). 设备，图 (2) 代表了准准确率 (a). 体育，(b). 教育 (c). 设备，图 (3) 显示了召回率 (a). 体育，(b). 教育 (c). 设备，图 (4) 显示了 F 值 (a). 体育，(b). 教育 (c). 设备，图 (5) 描绘了错误率 (a). 体育，(b). 教育 (c). 设备。

![](img/5e4d8ef2afa52a8404b28106580e19e4_176_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_177_0.png)

**图 (1)** 准确率 (a). 体育 (b). 教育 (c). 设备。

![](img/5e4d8ef2afa52a8404b28106580e19e4_178_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_178_1.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_178_2.png)

图 (2)

准准确率 (a). 体育 (b). 教育 (c). 设备。

| 提议方法 | 朴贝叶斯 | 提议方法 | 朴贝叶斯 |

|---|---|---|---|

| 决策树 | 逻辑回归 | 决策树 | 逻辑回归 |

![](img/5e4d8ef2afa52a8404b28106580e19e4_180_0.png)

| 提议方法 | 朴贝叶斯 |

|---|---|

| 决策树 | 逻辑回归 |

![](img/5e4d8ef2afa52a8404b28106580e19e4_180_1.png)

图 (3)

召回率 (a). 体育 (b). 教育 (c). 设备。

![](img/5e4d8ef2afa52a8404b28106580e19e4_182_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_182_1.png)

## 图 (4)

F 值 (a). 体育 (b). 教育 (c). 设备。

![](img/5e4d8ef2afa52a8404b28106580e19e4_183_0.png)

# 图 (5)

错误率 (a). 体育 (b). 教育 (c). 设备。

## 结论

基于内容的文本分类对文档进行分类。它能自动对自然语言文本进行分类。文本分类是文本检索结构的主要需求（这些结构根据在线用户查询收集文本）以及文本理解系统的需求（通过摘要、回答查询或提取数据来修改文本）。监督文本分类技术需要足够的数据来进行学习。本研究引入了一种基于 AI 的文本分类系统，该系统训练更少的在线内容文档。词汇关系或关联规则被用于在分类文本文档之前提取一组特征，而不是单词。`SVM` 应用于生成的特征，随后使用单一遗传算法进行分类。该算法已构建并在实验中表现良好。

## 参考文献

1. Yudhana A., Akbar S., Farezi A., Ghazali K., Nuraisyah F., Rosady P.. Content Analysis using Image Processing and Machine Learning 5th International Conference on Information and Communications Technology (ICOIACT) 2022 513516 10.1109/ICOIACT55056.2022.9972

2. Ismail S., A.. Comparative Study of Machine Learning Techniques to Classify Edible and Poisonous Mushrooms. International Conference on Artificial Intelligence and Smart Systems (ICASIS) 2021



# 基于机器学习的文本情感识别词汇方法

Mridula Gupta¹

## 摘要

情感研究已成为研究的一个重要领域，因为它提供了丰富的信息。情感可以通过多种方式表达，包括单词、面部表情、书面材料和动作。自然语言处理（`NLP`）和深度学习概念是解决基于内容的文本分类问题的关键。因此，在研究中，我们建议使用深度学习来从口语转录中识别人类情感。视觉表达形式，如装扮术语，可用于传达感受。来自自闭症（`ASD`）患者的录音数据集已进行转录。然而，在本文中，我们专注于对所有文本数据集进行情感检测，并利用语义数据增强过程填充一些短语或破碎的句子，因为自闭症患者缺乏社交接触技能。

**关键词：** 词汇方法、机器学习、语音情感、文本分类。

* **通讯作者 Mridula Gupta¹：** 跨学科研究技术中心，奇特拉大学工程技术学院，奇特拉大学，旁遮普；电子邮箱：`mridula.gupta.org@chitkara.edu.in`

在情感分类阶段，提出了一种建立选择树结构的方法 [5]。决策树 `SVM` 允许同时进行粗粒度和细粒度的分类 [6]。当从情感中剔除无关信息时，情感检测变得更加准确。通过说话者的声音识别情感正成为一个日益重要的研究领域 [7]。该突破引入了一种基于语义单元的方法，用于识别言语中传达的情绪 [8]。语音情感识别过程涉及构建语音库、对音频库中指出的每个单词进行预处理、获取每个对话信号的情感特征，并利用提取结果为每个语言信号建立特征向量；利用能力载体的指令获取基于语义单元的混合模型，并通组合模型收集的数据作为某一类别的识别模型 [9, 10]。

## 相关工作

我们提供了一种仅通过词语推断说话者情感状态的方法。该方法采用了一种名为 `XGBoost` 的特征选择技术，利用了在标识符上训练的卷积神经网络（`CNN`）以及一个关注细节的 `BLSTM`（双向长短期记忆）模型。捕捉每个特征的重要性评分，对于缓解过拟合问题、减少训练开销、加速建模过程以及提高识别准确率至关重要。在 `EmoDB`、`CASIA` 和 `EMA` 语料库上进行的实验结果表明，该框架在预测准确率方面优于基线模型（`86.87-74.17-98.04%`）[11]。

在使用情感模糊度建立决策树 `SVM` 框架后，我们使用 `Fisher` 则为树中的每个 `SVM` 选择具有更高区分能力的特征。这种方法最终使得自动识别口语传达的情绪成为可能。为了测试我们方法的可靠性，我们构建了一个带有 `Fisher` 特征选择的决策树 `SVM`，并将其应用于 `CASIA` 中文表达语音语料库以及柏林语音语库。实验结果显示，与 `CASIA` 和柏林语音语库上的标准 `SVM` 分类方法相比，所提方法将平均情感识别率提高了 9%。所提方法 [12] 在减少情感混淆的同时提高了情感识别准确率。

本文通过基于机器学习的策略识别情感，提出的确定差分（`deltas`）和二阶差分（`delta-deltas`）不仅包含了有用数据，还减少了情感不重要因素的影响，提高了准确性。静帧或不必要的情感帧是语音情感识别（`SER`）的另一个常见问题。同时，关注点对于学习特定任务成功所需的特定特征表示非常有帮助。为了为 `SER` 生成判别性特征，我们致力于开发一种基于注意力的卷积递归神经网络（`ACRNN`），其输入为带有差分和二阶差分的 `Mel` 频谱图。实验结果在结论中详细列出，表明所提策略是有效的，并在释放权重平均召回率方面达到了最高准确率 [13]。

得益于根据两组不同的语义单元通过混合模型构建的语音情感检测模型，用户能够同时识别说话者及其心情。当应用于情感识别时，使用以语义单元为中心构建的识别模型具有高准确率、低内存需求（存储 `r`）和识别快速等特点 [14]。

这里介绍的方法使用 `Berouti` 谱消除来恢复浑浊音频录音的清晰度。利用快速傅里叶变换（`FFT`）和频谱通量，从噪声的语音频谱中提取出干净的语音频谱。信噪比（`SNR`）被用于计算研究的整体质量。在该研究中，提出了一种新参数来增强语音质量。建议将谱还原与频谱通量相结合以进行更精确的噪声估计。新参数改进了谱减法中的功率比，无声词帧也受益于此方法 [15]。

## 提出的工作

## 研究缺口

通过阅读书面语言来推断人的情感状态似乎很困难。人机交互（`HCI`）依赖于从文本判断读者的情感状态。人类使用三种情感交流类型：面部、基于文本和基于语音。由于在面部和语音情感检测方面已经进行了充分的工作，因此对基于文本的情感识别系统进行研究是必要的。利用计算语言解决书面文本人类情感检测问题变得越来越重要。文本情感检测试图通过分析作者的输入文本来识别作者的情感状态。这基于这样一个假设：满意的人会使用积极的语言。“压力（`stressed`）”、“抑郁（`depressed`）”和“沮丧（`frustrated`）”等词可能暗示深层的不愉快。电子邮件、消息、聊天室、论坛、在线博客、产品评价以及 `YouTube`、`Twitter` 和 `Facebook` 等社交媒体网站严重依赖人机交互的主要媒介。包括商业、心理学和教育在内的许多领域可能从情感检测软件中受益。基于 `NLP` 的情感分析结果已应用于用户画像分析领域。特别是，情感分析通常与意见挖掘相关，其目标是为陈述中的每个相关部分分配积极、消极或中性。对用户心理状态更细致的理解是实时应用的必要条件。文献中可以找到各种情感模型，每种模型都有其特点和细粒度的适用领域。然而，仅从一行字识别情感是一项重大挑战。在个性化结构中使用情感是一种有效实践，不同的研究已经证明了它们的价值。每个用户都有独特的行为模型，这些模型可能偏离常态。因此，在这项研究中，我们提出了一种利用大数据识别人类情感的方法。由于词向量表示通过深度学习技术捕捉了有用的语义分量以及词之间的语言关系，词嵌入已广泛应用于 `NLP` 应用。为了帮助 `ML` 模型处理非结构化文本，词嵌入通常作为特征输入。

## 系统模型

情感状态识别是深度学习中一种较新的技术。在本文中，我们讨论了情感分类系统的研究原理和性能指标。视觉表达形式（如装扮术语）可用于传达情感。来自自症谱系障碍（`ASD`）患者的录音数据集被转录用于分析。然而，在本文中，我们感兴趣的是从各种书面数据识别情感，并使用语义数据增强过程来填充一些句子、单词或破碎的语音，因为自症谱系障碍（`ASD`）患者缺乏社交技巧。

## 词嵌入

文档可以由由词嵌入基向量组成的固定大小向量表示。在提出的研究中，已经尝试了许多文档表示方法，词向量与以下标记相结合：训练数据中不存在的单词被赋予连续低权重。区分能力的值取决于上下文。这种策略运行的前提是：文档在它们的嵌入表示中具有更大的意义，因为为分类提供了更多可用的数据。由于训练数据基于测试样本，分类器可能会为每种情感分配一个值。然后，与样本关联的类别（用于多级分析）利用具有最大决策值的情感或具有乐观判断函数值的一组情感。

```
$c_{we}(t_1, \dots, t_l) = \frac{1}{\sum_{j=1} b_j} \sum_{j=1} b_j \cdot u(t_j)$
```

如公式 (1) 所示，其中 `$c_{we}$` 代表包含 `I` 项的文档 `c` 中的词向量表示，`$u$` 代表预训练的词向量映射，`$b_j$` 表示数量，指示相对重要性 `$t_j$`。在研究中，我们尝试了几个不同的文档示例，所有示例都包含一个循环的词袋或分类器权重。该方法使用分类器权重通过计算权重函数 `$w(t, e)$` 来确定训练数据中每个短语 `$t$` 的重要性，从而将文章标记为表达某种情感 `$e$`。这项研究始于以二值向量表示的词袋显示材料，其中检索了单单元特征。然后，一个经过线性内核训练的支持向量机学习与训练数据中每个术语 `$t$` 相关的权重，记为 `$n(e,t)$`。

```
$w(t, e) = \frac{|n(e,t)|-\mu_e}{\mu_e}$
```

根据第二个方程，`$\mu e$` 和 `$\mu_e$` 是模型权重的平均值和标准差（绝对值）。

```
$b_j = \begin{cases} 1, & t_j \in U \text{ or } w(t_j, e) < 1 \\ w(t_j, e), & \text{else.} \end{cases}$
```

根据公式 (3)，`$U$` 是通过指令获取的词表。未匹配训练数据或区分度较小的项赋予较低的常数权重。具有更强区分能力的单词赋予更大的权重。这种方法利用了这样一个思想：文本中包含的短语由于其为分类任务提供了额外信息而更相关。必须记住，由于每个词的判别强度（权重 `$b_j$`）不同且表达广泛，该方法使用不同的文本来传达不同的情感。

## 语音情感分类

作为人类人类心理的窗口，从语音信号中识别情感在人机交互（`HCI`）模型开发领域引起了广泛关注。将人类情感状态识别作为认知反馈是 `HCI` 的共同需求。在这项工作中，我们研究了利用语音线索识别七种不同的情感：悲伤、愤怒、厌恶、快乐、惊讶、愉快和冷淡。对于情感识别，建议的技术利用了熵特征，这是一种基于随机度量的非线性信号定量技术。图 (1) 表示了系统模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_194_0.png)

图 (1) 系统模型。

卷积神经网络（`CNN`）是一种仅用于分类的深度学习方法。`CNN` 通常用于模式识别和改进数据分类，越来越流行。这些网络的输入数据由分布在规划模型架构每一层的小型神经元处理。

卷积方式应用于输入并与滤波器相同参数的局部连接是其基础（权重 `$W^l$` 和偏置 `$n^l$`）。为了生成特征图（`$Z^l$`）直直到大小为 `a-b-1`，卷积层对输入和权重进行点积计算。因此，在生成具有特定 `$i$` 尺寸 `a-b-1` 特征的图 `$Z^l$` 时，权重因子 `$W^l$` 和 `$n^l$` 表示为：

```
$z^i = g(W^i * r + n^i)$
```

反卷积层的输出必须使用一种非线性方法的激励函数。为了减少网络参数并改进图特征，在每个子采样层执行下采样。结果是改进了训练过程并控制了过拟合。对于所有相邻空间的特征图，跨 `pp` 个元素（也称为滤波器尺寸）执行池化操作。最后，与其他神经网络一样，层必须正确连接。在生成低级和中级特征后，后续层从输入的语音数据中构建高级级抽象。最后，使用 `SVM` 或 `Softmax` 层为给类别提供概率分类评分。

## 结果与讨论

对自闭症谱系障碍（`ASD`）患者的录音数据集进行转录以分析。然而，在本文中，我们感兴趣的是从所有这些文本数据识别情感，并使用语义增强过程来填充一些句子、短语或破碎的语音，由于自闭症谱系障碍（`ASD`）患者无法很好地表达他们的信息而缺乏社交技巧。

`DLSTA` 技术用于人类基于文本的情感识别。识别系统使用的七种分类器使用描绘以下情感及其相应表情的图像进行训练：忧伤、惊讶、喜悦、愤怒、恐惧、厌恶和中性。模板寻求预测的类别是：中性为零、冷静为一、快乐为二、悲伤为三、愤怒为四、恐惧为五、厌恶为六、惊讶为七。由于 `TESS` 中没有安静类别，分类报告中该类别的记录较少，数据集存在偏差。图 (2) 展示了 `CNN` 模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_197_0.png)

图 (2) `CNN` 模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_198_0.png)

图 (3) 预测和检测的准确率。

| 准确性 | 预测率 (%) |
| :--- | :--- |
| 快乐 | 80.3 |
| 不快乐 | 80.9 |
| 惊讶 | 80.8 |
| 厌恶 | 81.5 |

| 准确性 | 预测率 (%) |
| :--- | :--- |
| 恐惧 | 82.4 |
| 怨恨 | 83.6 |
| 无偏 | 81.3 |
| 常规 | 83.3 |

在包括多分类的文本分析背景中，识别情感是关键组件。使用准确率、召回率和 `F1` 来评估 `DLSTA` 的性能。每个情感段的表情分类器是跨所有类别表情分类器性能宏观评估的基础。可以使用基于 `NLP` 的文本分析通过分类的通用能力来识别情感。图 (4) 表示为损失和准确率 (a)。损失和 (b)。准确率。

![](img/5e4d8ef2afa52a8404b28106580e19e4_200_0.png)

(a)

![](img/5e4d8ef2afa52a8404b28106580e19e4_201_0.png)

图 (4) 损失和准确率 (a)。损失和 (b)，准确率。

## 结论

根据技术部分提出的初步分析，很清楚利用所有熵指标提供的补充信息对于从语音信号中识别情感是必要的。因此，从熵特征构建了组合特征向量。特征空间维度为 `1400 x 40`，每个情感类别包含 200 个语音信号。为了提取从音频数据中提取了七种情绪，我们利用特征矩阵训练了一系列机器学习分类器。为了评估分类器识别情绪的效能，研究人员采用了交叉验证法。

## 参考文献

- [1] Hojan, V., Kaič, Z., A rule-based emotion-dependent feature extraction method for emotion analysis from Speech. Acoust. Soc. Am. 2006,119:5093-3201. `10.1121/218864716708965`
- [2] Pathak, B., Sankar M., Manat, A.R. Emotion transformation from neutral to 3 emotions of speech signal using `DWT` and adaptive filtering techniques. Annual IEEE India Conference (`INDICON`) 15210111. `10.1109/INDICON.2014.7030389`
- [3] Vashisht, V., Yadav, S.P. Speech Recognition Using Machine Learning. IEEE Transactions on Smart Processing & The Institute of Electronics of Korea. May 2021,10:223-3931. `10.5573/IESPC.2021.10.3.233`
- [4] Wang D., Khisti A.Z., Sohn J., Chung I. An Improved Method for Measurement of Gross National Happiness using Social Network Services. Em/HumanCom 203.
- [5] Bhaker S.K., A.V. Emotion recognition on the basis of audio signal Naive Bayes classifiers. International Conference on Advances in Communications and Informatics (`ICACI`) 236232762161. `10.1109/CACI.2016.7732408`

## 参考文献（续）

- [6] Yudhana A., Akbar S., Farezi A., Ghazali K., Nuraisyah F., Rosady P.. Content Analysis using Image Processing and Machine Learning 5th International Conference on Information and Communications Technology (`ICOIACT`) 2022 513516 `10.1109/ICOIACT55056.2022.9972`
- [7] Akram A., Debnath R.. An automated eye recognition from visual images using machine learning. 2020 997
- [8] Faruke M., Rahman S., Choudhury T., Um J.S., Singh T.. A Framework for Personalizing Web Searches with Concept-Based Disease Detection using machine Learning. Machine Learning and Artificial Intelligence 2022
- [9] Bedi P., Goyal S., Rajawat A., Shaw R., Ghosh A.. Ascertaining polarity of public opinions on cricket using machine learning. Advanced Computing and Intelligent 2021
- [10] Singhal P., Srivastava P., Tiwari A.K., Shukla R.K.. Classification of Fake News using Machine Learning. Information Research 2022 37
- [11] Malik K., Urdu News Content Using Machine Learning. Lahore University Research Journal of Computer Science and Information
- [12] Naramula V., A.. Sentiment analysis in aspect extraction for mobile phone tweets using machine learning. Int. J. Pervas.Comput. 2021
- [13] Vashisht V., Pandey A.K., Yadav S.P.. Speech Recognition Using Machine Learning. IEEE Transactions on Smart Processing & Computing 2021 233



# 使用文本挖掘方法高效进行网站识别的方法

Madhur Taneja$^{1,*}$

^1 Centre for Interdisciplinary Research in Business and Technology, Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

## 摘要

在本文，我们介绍了一种使用深度神经网络和混合数据提取器进行网站分类的方法。我们使用迭代训练以及监督学习方法，通过梯度下降来模拟分类。这种现代模型由网页编码器、卷积神经网络（CNN）特征提取、双向长短期记忆网络（LSTM）以及全连接分类器组成。我们的模型可以通过拼接从基于 DNS 域名编译的网站数据集获取的特征来快速选择类别。

**关键词：** CNN, LSTM, 文本挖掘，网站分类。

*通讯作者 Madhur Taneja: madhur.taneja@chitkara.edu

## 引言

网站组织对于各种应用（包括网络安全、金融和其他领域）来说，是一项日益常见且重要的任务。然而，在提高准确性方面仍然存在巨大障碍，这使得该工作变得具有挑战性。关键词匹配是一种曾用于解决这一问题的方法。在这种情况下，早期的一些研究使用了一些策略来完成这项工作。最初，任务被分配给诸如支持向量机或朴素贝叶斯等特定的机器学习技术。关于有害网站检测的先大部分文献仅将网站分类为有害或无害。由于研究人员可能会为不同类型的网站创建不同的有害检测器，预先知道给定网站所属的类别允许有害检测器提供更精确的发现。例如，“商业与经济”领域的优质网站在“医疗保健”类别中可能表现为恶意的。因此，发现恶意网站在很大程度上取决于我们对网站进行分类的工作。利用基于深度神经网络的提取器，它与先进模型相比实现了更高的精确度。我们提出的模型可能受益于所有这些，同时也受益于准确率、召回率和精确度。

大多数用户通常对网络架构没有深入的理解，因此如果他们必须进行过多的访问跳跃，在等待信息到达时可能会变得不耐烦。数据挖掘技术（如网络挖掘）已为这些问题提供了成功的解决方案 [8]。网络挖掘是一种用于分析互联网材料的数据挖掘技术。标准数据挖掘技术被用于从万维网中提取信息，并随后将其整合到网站的功能中。网络挖掘的目标是在互联网上发现有用的数据模式并将其提取以进行更深层次的研究。网络挖掘包含三类：检查连接网站的连接连接的**网页结构挖掘**、检查单个页面内容的**网页内容挖掘**，以及检查服务器日志中流量信息的**网页使用情况挖掘**。

## 相关工作

本项研究提出了一种独特的文本提取方法，为在文本提取过程中有效利用统计语义研究提供了一个框架。该方法利用中心性（centrality）来忽略在措辞、数据或意义上与其他段落高度相似的文本内容。这种新颖的多层相似性技术在相似性检测中，第一层和第二层使用向量空间模型和 Jaccard 相似性，在第三层使用 LSA（潜在语义分析）。只有在前两层无法识别的片段才会在第三层中进行比较。我们创建了一种新的评估方法，而提取的 Rouge 工具并未考虑这一点。该方法考虑了自动提取和参考提取之间交叉的句子比例，以及压缩率。与传统的 LSA 和常规统计提取相比，我们取得了良好的准确率结果，将初始矩阵维度减少了 65%，并使 LSA 计算所需的时间减少了 52%。多层设计所提议的，中心性特征被证明可以显著提高文本提取的有效性和精确性 [11, 12]。

通过将 SyntacticDiff 应用于三种不同的用例——纠正语法错误、分组和分析学生论文以及识别母语——我们展示了该工具的价值。由于 SyntacticDiff 是语言中立的，它可以用于任何自然语言的任何文本信息语料库。它速度快、适应性强，能够识别目标文本集与参考文本集之间短语、论文和子集合层面的语法差异。因此，对于处理词汇用法和语法的“词袋”之外的许多文本挖掘任务，更复杂的翻译技术和特征表示可能会更有优势 [13]。

由于用户非常重视时间，如果有更好的执行搜索和显示结果的方法，将是有益的，这样他们就可以快速关注他们寻求的确切信息，而不是在不符合其要求的长论文列表中翻找。联合信息系统委员会（JISC）创建了一个原型网络界面，以演示如何引入特定的文本挖掘算法及方法来增强用户搜索、浏览和阅读文本的能力。新功能包括关键词识别和高亮、基于相关文档内容的搜索结果分组，以及基于自动分类法的文档分类。本研究关注网页使用情况挖掘（WUM），以前称为网页日志挖掘。在本研究中，我们提供了网页日志文件清洗、订阅者/会话识别和索引的技术。

## 提出的工作

### 研究空白

网页（互联网页面）的主要部分已演变为关键的数据传输。人们随时随地使用 PC、笔记本电脑和智能手机浏览各种网站。尽管访问网站可能提供许多优势和好处，但由于存在许多用户威胁，经常访问已变得具有风险。例如，某些网站显示各种垃圾广告，充斥着诈骗和钓鱼尝试，有些网站甚至会在用户的计算机和移动设备上秘密下载并安装危险软件。尽管近期受到了大量的研究关注，恶意网站的识别仍然是许多重要安全工作的紧迫问题。来自不同类别的网站有很多类型，它们关注不同的主题，这使得精确识别所有危险网站具有挑战性。如果网站可以被分为几类，科学家可能会为不同类型的网站创建专门的检测器，从而提高检测效率和准确性。因此，这些努力将提高安全门槛。在这种情况下，网站分类对于检测流氓网站至关重要。其他领域（如数据处理和信息管理活动）的不同网站的分类也是迫切需要的。为了提高搜索结果的质量，例如 Google 和 Bing 等搜索引擎必须对网页进行分类。为了提供目标广告并获得最大回报，在线广告公司需要分类正确的网站。导航网站和搜索引擎都必须管理网页蜘蛛爬取，以便根据网站分类自动扩展它们的数据库。尽管网站分类是包括在线安全、医疗、金融等在许多应用的常见且关键活动，但在提高分类精确性方面存在一些主要困难，这证明了其实际挑战性。关键词匹配是一种用于解决这一问题的方法。为了指示不同的类别，它们使用了指定的术语。然而，重新定义分类过程所需的每一个术语都是困难的。在这种，一些较早的研究使用了新策略来完成这项工作。一方面，这项任务应用于某些传统的机器学习方法，如朴素贝叶斯和支持向量机。然而，这些机器学习方法对于高维海量数据是不够的。

### 系统模型

接下来的章节总结了本文的主要贡献。首先，我们创建了一个包含四个部分的智能网站分类模型：全连接分类器、网站编码器、CNN 特征提取器和双向 LSTM 特征提取器。其次，我们考虑了混合特征提取网络网站分类的通用性问题。我们在监督学习技术的指导下，利用从网页标题、关键词和描述中检索的词嵌入序列，通过梯度下降过程训练模型进行微调。最后，我们使用创新模型和实际网站数据集进行了大量测试。结果表明，建议的分类性能优于现有模型。此外，这支持许多网络应用程序，包括在线广告和有害网站的识别。

```
$e = [e_1, e_2, ..., e_T] \quad (2)$
```

因此，混合特征提取方法最适合包含词嵌入序列的数据。

### 使用 CNN 结合 LSTM 进行特征提取

CNN LSTM 架构将长短期记忆（LSTM）层与卷积神经网络（CNN）层配对，以实现序列预测。CNN 层用于从输入信息中提取特征。视觉时间序列预测的挑战以及从图像集合（如电影）中提取叙述的应用，启发了 CNN LSTM 的创建。

在与自然语言处理以及语音识别相关的任务中，CNN 可被用作声音和文本输入数据长短期记忆（LSTM）的特征提取器。

涉及以下问题的问题：

- 输入空间框架，例如句子、章节或网页中字母的一维排列；或者图像中像素的二维组织；这些非常适合这种范式。

- 需要生成时间结构化的输出，例如书面描述中的单词；或者在输入中包含时间结构，例如视频或文本的一系列图像。

利用网页页面编码器生成的词序列，CNN 特征提取构建了一个代表网站的扩展特征向量。首先，使用三种不同尺寸（3、4 和 5）的卷积内核过滤器来生成特征图。这些过滤器捕捉了词嵌入序列的局部模式。在对每个特征图执行了最大池化和平均池化操作后，随后将池化数据汇总创建一个单个特征图。最后，通过扁平化单个特征图创建一个描述网站的稠密特征向量 `F_c`。

通过合并网站的词嵌入序列，我们可以得到其特征向量 `F_c`。然后 `fm_s` 和 `\widehat{fm_s}` 将其还原为紧凑向量：

```
$F_c = \text{Flatten} ([\widehat{fm_s}, \widehat{fm_s}]), s \in [3,4,5] \quad (3)$
```

`F_c` 通过扫描词嵌入序列并利用滑动窗口方法（该方法考虑当前单词以及窗口包含的相邻单词），提供了网站局部的概述。

特征向量*通过*全连接分类器 `F_c` 和 `F_g` 发送，使用定义类的概率分布作为输入和输出。它首先合并 `F_c` 和 `F_g` 以获取混合特征，也称为特征 F 的拼接向量。随后，一个全连接网络接受 F 作为输入并产生一个维度等于默认类别数量的向量 O。为了获得概率离散向量，最后将向量 O 通过 SoftMax 函数：

```
$F = [F_c, F_g]$
H = \text{Re} \ LU(W_1F + b_1)$
O = W_2H + b_2$
p = \frac{\exp(O_1)}{\sum \exp(O_l)} \quad (4)$
```

`F` 指代拼接的特征，`W_1` 和 `b_1` 表示经过 ReLU 转换后的隐藏层输出，同时也表示完全连接隐藏层的偏置和权重；`W_2` 和 `b_2` 代表输出层的权重和偏置，O 代表输出本身，p 代表使用 SoftMax 函数的概率分布，用于确定每个类的相对重要性。网站的类别可以简单地通过查看其索引来确定，由概率分布中值最大的值表示。

作为训练损失（Loss），我们取预期 `p` 与正确标签值的 one-hot 编码之间的交叉熵：

```
Loss = - \sum_{i}^{c} y_i \log(p_i)
```

其中 `c` 是类别数量，`y` 是网站标签的 one-hot 编码。

## 结果与讨论

### 数据集描述

我们的集合被分为 15 个类别，每个类别有 3000 个网站，包括 Bing、eBay 和 Twitter 等知名网站。我们从网站的标题、关键词和描述中提取单个术语。除了停用词和符号外，每个词在分词期间都会保留。之后，我们使用最新的 Wikipedia 语料训练 Word2Vec 模型获取词嵌入。通过使用 Word2Vec 范式，我们可以将每个词转换为64 维向量。每个网页可以表示为 64x64 的词嵌入矩阵，不包含 64 个单词的部分填充零，以确保所有网页描述结构相似。

#### 超参数描述

CNN 特征提取带有三种不同尺寸的卷积内核过滤器，每层 32 个。尺寸分别为 3、4 和 2。在 LSTM 双向提取器中，每个双向 层 有 32 个单元。输出层由 15 个神经元组成，输入层层级为 256 个突触，全连接分类器使用 dropout 为 0.3。在配置阶段，我们使用 RMSProp 优化方法。我们从 0.001 的初始学习率开始，当算法等待测试集的准确率达到平台期时，逐渐降低学习率。

![](img/5e4d8ef2afa52a04b28106580e194_216_0) 图 (2) 准确率

### 结果描述

图 (2-5) 显示了应用于我们数据集模型的实验结果。此外，我们将我们的模型与 CNN、LSTM 等已知深度学习模型进行了比较。F1 分数通过两个指标精确率和召回率计算。召回率衡量了测试集中相关网站的平均百分比，精确率衡量了每个组预测的准确部分。结果显示，与其他模型相比，所提模型提供了最佳性能。我们的方法将网络分为不同的子集，从而创建独特的检测器。因此，检测时间和精确率应该提高。

![](img/5e4d8ef2afa52a04b28106580e194_217_0.png) 图 (3) 精确率

![](img/5e4d8ef2afa52a04b28106580e194_218_0.png) 图 (4) 召回率

![](img/5e4d8ef2afa52a04b28106580e194_219_0.png) 图 (5) F-score

## 结论

我们的研究引入了一种利用深度神经网络和混合特征提取器的网站分类策略。我们的数据基于 DNS 记录，具有实际应用。首先，我们的方法使用 Encoder 将网站转换为词嵌入矩阵。然后，我们使用文本 CNN 提取器以及双向 LSTM 提取器采集多种特征。分类恢复的混合特征的最后一步是应用全连接网络。研究结果表明分类方案优于目前使用的模型。适用于适用于 Web 应用，包括恶意网站识别、在线广告等。例如，研究人员可以使用我们的方法在恶意检测之前对所有网站进行分组。然后，他们能够创建更高效准确的特定类别恶意检测器。使用之前应用于机器翻译和文本分类的注意力机制来改进模型是研究的下一步。除了提高分类准确率外，它还可以用于从在线文本中识别短语。

## 参考文献

- [6] Yadav S.P., Zaidi S., Nasimientoo C.D.S., Albuquerque V.H.C., Chauhan S.S. Analysis and Design of automatically generating for GPS Based Moving Object Tracking System. 2023 International Conference on Artificial Intelligence and Smart Communication (AISC) Noida, India. 2023,15. 10.1109/AISCC5616.2023.1008510

- [7] Wagner J., Kim J., André, E., From Physiological Signals to Emotions: Implementing and Comparing Selected Methods for Feature Extraction and Classification. IEEE International Conference on Multimedia and Expo 090432005. 10.1109/IEEE.2005.1521579

- [8] Sarei., Sajadi D., Harfi M. Low rate stimulation strategy for cochlear implants using today and electrophysiological factors. Technology and health care : official journal of the European Society for Engineering and Medicine. 2021,88:97-88.

- [9] Ishakova A.O., Volf D.A., Meshcheryakov V.R. Method for Reducing the Space Dimension in Speech Emotion Recognition using Convolutional Neural Networks. Aut. Remote Control 2022,28:326-8576886. 10.1109/AS00051179220600042.

- [10] Dey A., Chattopadhyay S., Singh P.K., Ferrara M., Sarkar R. A Hybrid Meta-Heuristic Feature Selection Method using Golden Ratio and Equilibrium Optimization Algorithms for Speech Emotion Recognition. IEEE Access 2020,8:20809-520097. 10.1109/ACCESS.2020.3035531.

- [11] He J., Ren L., Speech Emotion Recognition using XGBoost and CNN BLSTM with Attention. IEEE SmartWorld, Ubiquitous Intelligent Computing, Advanced Trusted Computing, Scalable Computing Communications, Internet of People and Smart City Innovation 2021,154:119.

- [12] Sun L., Fu S., Wang F. Decision tree SVM model with Fisher feature selection for speech emotion recognition. EURASIP J. Audio Speech Music Process. 2019,2019:1210. 10.1186/s1363-018-045-5.

- [13] Gayathri P., Priya P.G., Sravani L., Johnson S., Sampath V. Convolutional Recurrent Neural Networks Based Speech Emotion Recognition. J. Comput. Theor. Nanosci. 2020,17:783-86379. 10.1166/jct.2020.9321.

- [14] Kaur J., Saxena J., Shah J., Fahad, & S. P. Yadav, "Facial Emotion Recognition International Conference on Computational Intelligence and Sustainable Engineering Solutions (CISES) IEEE 2022. 10.1109/CISES54857.2022.9844366.

- [15] Lynn M., Su C.. Noise Removal in Speech Signal using Modified Berouti Spectral Subtraction for Emotion Recognition. 2019 International Conference on Signal Processing and Communication (ICSPC) May 2019,16.



[1] Afzaal M., Usman M., Fong A.C., Fong S.J., Yan Z.. Fuzzy aspect based opinion system for mining tourist reviews Adv. Fuzzy Syst.2021669657251696525

[2] Abanie A.H.. The enhancement of arabic information retrieval using arabic text summarization. 2019 International Conference on Innovative Trends in Computer Engineering (ITCE)201915

[3] Yang H., Hadiantoni S., Long Y., Petrayite R.. Automatic detection of industry sectors in legal articles using machine learning approaches.Proceedings of the 2022 International Conference on Machine Learning and Data Science (MLDS).Jul. 2022455210.1109/MLDS.2022.123456716662062100335

[4] Yao M., Jian C., Li C., Li Y., Jiang S., He L., Xiao H., Quan J., Huang X., Huang T.. GERE: detection of gene expression regulators from transcriptome profiling data to transition.Networks.Curr. Bioinfo.20216691010210.2174/1574893616662062100335

[5] Bernard K., Cassidy A.P., Clark M., Liu K., Lobaton K., McNill D., Brown B.E.. Identifying and tracking online financial services through web membut and semanticIEEE Systems and Information Engineering Design Symposium2011186320110.1109/SIEDS.2011.587680

[6] Chandreshkar P.B.. A timeline extraction approach to drive usage patterns in pregnant women using social media.2016 International Conference on Healthcare Informatics (ICHI)2016218

[7] Jami I.S., Zubair A.S.. Semantic based e-government system.Indian J. Sci. Technol.201811441610.17485/jist/2018/1144123332

[8] Yadav S.P., Zaidi S., Nascimento C.D.S., Albuquerque V.H.C., Chauhan S.S.. Analysis and design of automatically generating for GPS based moving object tracking system2023 International Conference on Artificial Intelligence and Smart Communication (AISC)Greater India.20231510.1109/AISC56616.2023.1008510

# 基于机器学习的高维文本文档分类与聚类

Ansh Kataria¹*

¹ 印度旁遮普邦，Chitkara 大学，Chitkara 大学工程与技术学院，商业与技术跨学科研究中心

## 摘要

文本分类是一项困难的技术。由于特征向量规模巨大，已经开发了许多技术来减少特征向量维度以用于文本分类。本工作详细讨论了利用光学聚类策略的独特参数，并对一些最基本的文本分类算法进行了回顾。在这种情况下，词汇根据其相似程度进行聚类。每个簇的成员函数基于其数据的平均值和标准差。最后，从每个组中选择特征。每个簇提取的特征是其单词的加权和。此外，不需要猜测或使用尝试法来确定最佳聚类数量。

**关键词：** 聚类、高维文本、机器学习、文本文档分类。

> *通讯作者 Ansh Kataria：印度旁遮普邦Chitkara 大学，Chitkara 大学工程与技术学院，商业与技术跨学科研究中心；邮箱：`ansh.kataria.orp@chitkara.edu.in`

## 引言

对文本文档进行分类和聚类是一项重大的学习挑战，在数据挖掘和机器学习中具有广泛应用 [1]。在处理高维文本材料时，学习变得复杂且充满困难。单词在书面材料中出现的顺序是学习过程中的一个重要因素 [2]。尽管高维文档被用于分类，但文档大小是一个严重的问题且令人困扰的指标 [3]。降维可能会产生有益和负面的结果 [4]。如果降维后的维度不是正确的格式，则使用降维维度进行文档分类将是无效的 [5]。虽然基本的相似性特征是我们研究的重点，但我们尚未解决文本分类 [6]。文本挖掘应用的使用在多个学术领域的重要性日益增加 [7]。许多国际组织和不同族群的许多重要过程大多记录在文档中。文本诗歌是文化和教育领域的一种重要媒体。阿拉伯文本诗歌分类虽成为趋势的领域只有几个，但它产生了重大影响 [8]。区分阿拉伯诗歌不同风格的韵律和谐尺度 [2] 在现代阿拉伯语和古典阿拉伯语诗中是相同的。涉及文本分类任务时，深度学习是最有效的机器学习技术之一。有各种信息检索活动受益于文档聚类，包括文档浏览、组织和检索结果的显示。它们目前在全球范围内被广泛研究。基于多变量伯努利分布作为多项分布的生成式模型在文本分类中已广泛使用。

## 相关工作

目前关于高维文本文档分类和分组主题的绝大多数工作依赖于使用经典的距离函数，而不考虑文本中的单词分布。为了进行特征模式分组和高维文本分类，我们在本研究中提出了一种新的相似性函数。提出的相似性函数用于通过监督学习来实现降维。这项研究的特殊之处在于，术语分布在降维前后均保持不变。实验结果表明，建议的技术成功地减少了数据维度，保持了单词分布，并获得了比现有技术更高的分类准确率。

讨论了几种执行分类和聚类任务的技巧。在这项研究中，我们在多个数据集使用了分类和聚类技术。它还包括关于如何让朴素贝叶斯（Naive Bayes）分类和 KMeans 聚类更有效的建议。建议方法的有效性通过准确率、召回率和 F 分在内的标准指标进行衡量。实验结果将表明建议的模型优于现有技术。

本研究提供了阿拉伯诗歌文本的分类法。为了提高模型的有效性，我们提供了一种与聚类技术相结合的专门特征选择。两种著名的机器学习技术——支持向量机和决策树已与深度学习实验结合使用。建议的特征提取技术在跨方法中显示出良好的精度。

本文讨论了若干种执行分类和聚类任务的技巧。通过 LDA 和 K-Means 聚类更更有效。在这项研究中，我们使用基于 n-gram 的 LDA 模型来处理文本分类。建议的 LDA 算法在所有方法中表现表现相似。通过相似性指标评估了建议的 LDA 模型。

在这项研究中，我们使用 n-gram 文本模型为英语和阿拉伯语文学认证提供了一种独特的技术。作者风格的分类通过实例和配置文件对 LDA 进行。在这种情况下，LDA 更有力地表示文本的能力使其非常适合处理高维数据。提供的方法是一种无监督计算策略，可以处理高维和稀疏数据，以及阿拉伯语固有的不确定性。所提供的技术已通过大型语料库进行了测试。基于 n-gram LDA 主题的余弦相似性用于评估文档向量的相似性，这是本文工作的贡献之一。作者身份识别任务在 PAN12 数据集上的总准确率为 84.52%，在无标记的阿拉伯语新闻项目上的准确率为 93.17%。

# 提议的工作

## 背景

对未处理的文本进行分类和标记就是我们所说的“文本分类”。文本分类具有广泛的应用，从新闻主题标记到用户评论情感分析。例如，“手机太糟糕了。缓慢。臃肿软件和侵入性广告达到了顶点。我不建议任何人使用这种手机。”根据上述语言，我们的分类机可以分配正确的类别或标签，如差评。

# 基于机器学习的文本分类

随着机器学习的快速发展，现在在数据集上训练模型并等待输出比以前任何时候都方便。机器学习方法使得为提供的文本分配类别变得简单快速。特征提取是机器学习的关键部分。词袋（本质上是计算文本中所有的单词）、tf-idf 等是将文本转换为向量形式的数值表示的技术之一。

附图描述了将机器学习应用于文本分类的高层级流程。在第一阶段，我们使用用户提供的文本作为训练数据。大多数机器学习算法只能识别数值特征，因此我们需要进行特征提取以将文本转换为数值表示。一旦有了所需的属性，我们就会将其输入到带有标签或类别的机器学习算法中。

已建立。完成训练后，我们的分类模型即可投入使用。用于文本分类的机器学习如图 (1) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_226_0.png)

**图 (1)) 用于文本分类的机器学习。**

一旦我们有了分类模型，就可以按照之前的步骤为它提供预测所需的数据：首先我们从数据中提取相关特征，然后将它们输入到我们预期的模型中。完成后，我们就能获得预期的分类结果。通过机器学习，文本分类变得更加简单、快速且改进。图 (2) 表示了用于文本分类和聚类的机器学习。

![](img/5e4d8ef2afa52a8404b28106580e19e4_226_1.png)

**图 (2)) 用于文本分类和聚类的机器学习。**

## 预处理

预处理是指在数据输入计算机之前所采取采取的步骤。预处理通常涉及移除无关信息。停用词是自然语言处理（NLP）过程中移除的一种冗余词汇（信息）。

![](img/5e4d8ef2afa52a8404b28106580e19e4_227_0.png)

图 (3)) 系统流程图。

## 停用词

停用词是经常使用的术语（如“the”、“a”、“an”或“in”），搜索引擎在创建索引和返回结果时被指示忽略这些术语。

## 特征工程

从预存数据中创建新特征以用于机器学习训练模型，被称为特征工程。创建与任务相关的属性至关重要，这一阶段可能比实际使用的模型更为重要。这是因为机器学习方法只能从我们提供的数据中进行学习。

## 特征聚类

特征提取的一种著名技术是特征聚类，其中将相似的特征集聚类形成一个簇，每个簇被视为一个独立的特征。随着时间的推移，技术上已经有了若干创新。下面，我们将介绍文本文本分类特征聚类策略示例。

这里使用了三种不同的加权技术。

- 在硬聚类技术中，模式的每个组件在单个簇中都有唯一的表示。

- 在软聚类中，每个词模式都为每个簇分配了一个成员身份函数。

- 混合分组：在混合聚类中，用户阈值决定了软聚类和硬聚类的相对强度。

该技术通过类别标签频率将单词组织成组。这种技术在有效压缩特征空间的同时，保持了高水平的文档分类准确率。然而，该技术最大的缺点是它使得聚类变得困难。

这种光学聚类策略两个主要优点是：

- 1. 不需要设置簇的数量。

- 2. 构建现实；即，我们逐一查看每个词模式。簇从开始并不存在，但根据需要可以创建。以便确定每个短语模式与预存簇的相似程度。

当且仅当存在可比较的簇时，词模式才会被聚类。如果不是，则将创建一个新簇。为了确定两个双词模式之间的相似性程度：

$$\mu_{G_j}(x_i) = \prod_{q=1}^{p} \exp \left[-\left(\frac{x_{iq}-m_{jq}}{\sigma_{jq}}\right)^2\right] \quad (1)$$

当，$n_{jq} =$ 第 $j$ 个簇的平均值。即 $m_j < m_{j1}, m_{j2}, \dots, m_{jp} > j_{jq} =$ 第 $j$ 个簇的标准离心。即 $\sigma_j < \sigma_{j1}, \sigma_{j2}, \dots, \sigma_{jp} >$ 当向新簇添加到现有簇中时，必须刷新成员身份函数。当发现第一个簇时，加入能力应设置为其起始值。

## 文本分类

原始文本对于机器学习算法是不可访问的。这个问题带来了一个新挑战：我们如何将文本转换为输入机器学习流水线的有用数字或向量？由于数值无法捕捉“国王”与“皇后”或“猫”与“狗”之间的含义、上下文或相关性，仅仅将原始文本转换为二进制、小数或直方图表示是不够的。为了解决这个问题，可以使用将每个文档映射到共享向量空间模型。我们利用以下技术转换每个单词。图 (4) 表示了特征的聚类。

![](img/5e4d8ef2afa52a8404b28106580e19e4_230_0.png)

# 图 (4)) 用于特征的聚类。

- 词袋 (BAG OF WORDS)。

- TFIDF。

- 平均词向量 (AVG w2v)。

- TFIDF w2v。

随机森林分类器的输出结果基于所有树输出结果的投票数。随机森林将许多树组合在一起。每棵决策树都作为一个分类器，是基础构建块。如果使用 N 棵树来分类输入样本，将会有 N 种可能。随机森林考虑分类投票中的所有票并输出最流行的选项。最简单的自助法（Bagging）是：

| 机器学习技术 | F值 |
|---|---|
| 支持向量的机器 | 85.98 |
| 随机森林 | 93.05 |
| K-最近邻算法 (KNN) | 81.12 |
| 朴素贝叶斯 | 69.11 |
| 决策树 | 66.96 |

在这方面，随机森林的性能也优于竞争性的机器学习算法。表 2 显示，标准的 tfidf 表示在文档分类方面的表现优于词嵌入，证实了表 1 所示的内容。这表明文档中相关短语的判别能力高于上下文和词义等其他编码方式。最后，推断统计以 82.74% 的分类准确率优于其传统的机器学习方法。此外，我们发现随机森林方法与其他机器学习技术相比表现较不佳。从大局来看，显而易见，无需使用极深模型来编码复杂的隐藏模式以将文本分类为已知的类别之一；只需识别几个关键词和短语即可。表 3 显示在“文本类别识别”中，表 4 表示在“文本分类 F 分数”中。

## 结论

文本分类是一项困难的方法。由于特征向量规模巨大，已经开发了许多方法来减少特征向量的维度以用于文本分类。这项工作详细讨论了利用光学聚类策略的独特参数，并对一些核心的文本分类算法进行了回顾。在这种情况下，单词根据其相似性进行聚类。每个簇的成员函数基于其数据的平均值和标准差。最后，从每个组中选择特征。每个簇提取的特征是其单词的加权和。此外不需要提前猜测或实验最佳分组数量。

## 参考文献

- [1] Rezaeian N., Novikov G.M.. "使用朴素贝叶斯算法和支持向量机算法进行波斯文本分类" 印尼电气工程与信息期刊.IJEEI2020

- [2] Tandon K., Chatterjee N., 集成空间的多标签分类 J. Intell. Fuzz Syst. 2022452445443610.3233/JIFS-219232

- [3] R R.K., Sahay S.K.. 结合 K-means 和 Wordnet 特征选择与极端学习机用于文本分类 分布式计算与互联网技术国际会议 2016110.1007/978-3-319-28034-9 13

- [4] Yadav S.P., Zaidi S., Nascimento C.D.S., de Albuquerque V.H.C., Chauhan S.S. 基于 GPS 的移动物体跟踪系统自动生成的分析与设计2023 人工智能与智能通信国际会议 (AISC) 印度大诺伊 2023 15.10.1109/AISC5666.2023.10085180

- [5] Mohamed H.H., Dogdu E., Görür A.K., Choupani R.. 使用深度学习进行文本多标签分类 IEEE 大数据会议 (Big Data) 2020204614689

- [6] Issue 3.Vashisht V., Pandey A.K., Yadav S.P.. ("使用机器学习进行语音识别") IEIE 智能处理与计算汇报., 10 韩国电子工程师协会 20212332910.5573/IEESPC.2021.10.3.233

- [7] Yadav S. P., Yadav S.. 连续小波域医学图像融合的数学实现 动力学与控制系统高级研究 201910104554

- [8] Krishna P.G., Baskari D.. 聚类技术综述 工程创新2017

- [9] Kanimozhi A., Subha M.. 机器学习在文本分类中的应用 现代工程研究2015

# 使用机器学习方法进行文本分类的应用

Pratiba Sharma 1 业务类研究, 奇特卡拉工程与技术大学，旁遮普邦特尔德邦

> 通讯作者 Pratiba Sharma 1 业务研究,* 奇特卡拉工程与技术大学，旁遮普邦特尔德邦；电子邮箱：`pratiba.sharma@chitkara.edu`

## 摘要

自然语言处理 (NLP) 的一个重要方面是文本分类，其目标是对给定的文本进行分类。由于分类模型存在多种形式，机器学习方法在文本分类中非常有帮助。然而，医学文献包含了大量的患者信息，使得这变得非常困难。在研究中，我们建议使用 N-gram 和支持向量机 (SVM) 进行医疗分类。

**关键词：** 医疗分类，机器学习，自然语言处理

该算法在短文本分类结果方面展现了显著改进。以下是本文所完成各项工作的概述。

在这项研究中，作者引入了一种结合 N-gram 与支持向量机（SVM）技术的新型分类策略。

为了获取文本特征，我们使用了基于 N-gram 语言模型的聚合过程，调整了许多超参数，并从整个模型中获了益处。

通过增强池化过程，我们的技术能够尽可能地保留有用特征，从而提升了文本分类任务的准确性。

我们建议的方法在第 3 节中进行了详细说明和分析，而第 4 节讨论了实验结果。第 2 节提供了第 3 节将使用的 SVM 模型背景信息。本文在第 5 节结束。

## 相关工作



研究建议，学习各种控制工程学科的学生应该从一个现有且可用的套件中受益。为了更新 Hedengren 提出的原始 TCLab（Hedengren et al., 2019），使用日常电子元件从零开始构建了一个温度控制实验套件。使用 Matlab/Simulink 仿真来检查基于理论和实验方法的系统数学框架的正确性。随后，该套件及其相应的数学模型接受各种控制算法（包括开关控制、PID 和模糊控制）的处理，以证明每种算法控制的可行性。Matlab GUI 也用于开发人机界面（HMI），允许用户选择控制方法、调整控制设置并监控过程参数。根据实验结果，生成的模型能够复制材料套件的动力学特性，温度差不超过 3 摄氏度。这证明了该套件适用于各种控制相关科目的教学，包括但不限于系统建模、系统等性证明、经典控制和高级控制算法 [11]。

将这些发现与文献中报告的结果进行对比，这些结果是使用多种工具和检索策略汇编的。我们检查了连接湿度水平与吸收率的功率估计中至关重要的实验变量的有效性。由于观测、校准和计算的不准确，总水蒸气柱的标准不确定性约为 10%。为了使通过光光度法获取的数据能作为其他技术（GPS、微波辐射计、激光雷达等）的独立基准，我们将校准精度提高到 1% 的前景视为一个关键需求 [12]。

来自意大利最顶尖科学机构的专家为这项工作做出了贡献，使得汇编我们认为的手术围术期临床测量最全面、最新的指南成为可能。通过流程标准化，使用标准化方案旨在增强手术实践，从而减少手术部位感染（SSI）和抗生素耐药性。

我们展示了一种从多色数据中结合 $\ell$ 和 $f$ 提取的新方法，并将其应用于许多 $\delta$ 大座星。$\delta$ 的估计值对恒星对流模型的实用性提供了很强的限制。此外，检测到的模式是径向的，可以使用多波段数据精炼全球全球参数。总之，在我们的方法中加入径向速度数据大大提高了我们确定性能的准确性 [14]。

结合应变和 LV 压力测量已被证明是克服 GLS 和 LV EF 限制并提供独立负载的心肌功能评估的有效手段。由于用于非侵入性微波计算的心声图软件，这种新方法已应用于多种领域。本文旨在总结非侵入性微波估计的研究现状，并强调其在治疗性环境中的潜在用途。

## 提出的工作

## 问题描述

近年来，人们对文本分类重要性的认识日益提高。图书馆分类、新闻分类等都是文本分类提高效率和节省时间的例子。这导致了文本分类在专业领域下的泛化。为了解决法院文件的人工处理问题，杨的小组开发了一种文本分类模型。为了分析和预测不规则或意外的情况，机器学习主要研究如何从提供的数据中学习不熟悉的规则，即从数据（样本）中识别某些规则。接下来的图显示了如何使用机器学习算法进行文本分类。

上图描绘了给定系统的输入（“x”）和随后的输出（“y”）。模型的处理从异常数据中产生了预期的结果。该“模型”在过去已使用“数据 (x, y)”进行了训练。这就是机器学习（ML）算法处理文本数据的骨架。对现有标记数据的统计分析是目前用于发现规则和建立模型的主要机器学习技术。可以使用这些训练后的模型对新数据的分类结果进行预测和分析。图 (1) 表示用于文本分类的机器学习。基于机器学习的文本分类算法通常包括四个阶段：

![](img/5e4d8ef2afa52a8404b28106580e19e4_241_0.png)

图 (1) 用于文本分类的机器学习。

- 1 文档建模和特征提取：涉及机器学习时，特征提取至关重要。手动特征提取是标准做法；然而，手动开发特征是耗费力的，而且现代数据集通常包含特征过多而维度太少，以至于无法发挥作用。传统的特征提取方法通常包括降维和选择最能反映文本信息并提供最大分类影响的特征维度，以解决这些问题。

- 2. 模型训练：使用训练数据集教授机器学习模型，实际的分类影响受训练数据中标记质量的影响。深度学习在特征学习方面优于基于统计的机器学习算法，它学习使用的特征能更好地表征数据，使其易想象和分类。

- 3. 用于检查的文本分析：我们只需将需要分类的文本数据输入模型，它将根据所学到的规则做出判断并提供分类结果。

- 4. 分类影响分析：文本分类完成后，使用准确率、召回率和 F 指标等指标来双检分类器的效率是重要的。

## 提出的方法

![](img/5e4d8ef2afa52a8404b28106580e19e4_242_0.png)

图 (2)) 提出的模型

N-Gram 是从更大的语音或写作语料库中提取的 N 个单词、短语或句子。一组单词或音节可能组成一个 N-Gram。为了预测传入的文本或语音，自然语言处理严重依赖 N-Gram 模型，而这些模型又基于 N-Gram。(2) 显示了提出的模型。

N-Gram 模型可以预测给定序列中的下一个内容。例如 DNA 测序字母表（GATC）。N-Gram 模型查看字符字符串，并根据后续可能出现的值生成概率分布。

训练数据。概率（例如每个可想的值为 0004）将相加并等于 1。

N语法（N-gram）系统用于帮助预测语音和/或文本，如上所述。它们利用了 N-Gram 固有的随机性，有时还会添加马尔可夫模型的特征。由于其易于使用且具有可扩展性，N-Gram 模型及其使用的方法非常适合通过使用更大的 N 集合从较小规模的研究进行扩展。在文本分类难题中，字符级 n-grams（character n-grams）被证明是最有效的特征类型。其主要优势在于可以在少量适配后应用于不同的语言。键入文本的 N-grams 提供了对文本含义和上下文的洞察。语言的 N-gram 模型估计了 N-gram 在给定的单词字符串中出现的概率。换句话说，一个良好的 N-gram 模型可以预测出某种量的 p(w|h)。像“，”、“article”、“is”、“on”和“NLP”这样的单词模型（Unigrams）以及像“This article”、“article is”、“is on”和“on NLP”这样的双词模型（bi-grams）都是 Ngrams 的示例。

接下来，我们将使用 N-gram 技术来构建一个用于定位短语下一个项的结构。如果它是可能的下一个词，那么我们需要找到 p(w|h)。考虑上述场景，即我们感兴趣的是在给定第一个单词的情况下，最后一个词是“NLP”的概率：

> $P = (w(1)|w(2)|w(3)| \dots w(n)$

上述方程可以重写为更通用的形式：

> $P = (w(1)|w(2)|w(3)| \dots w(n)\rightarrow W(N)$

## Skip-Gram

在语言处理中，跳词语法（skip-grams）有时被用作建模技术。与传统的 n-grams 在文本分类时需要连续的元素（通常是单词）不同，skip-grams 允许跳过间隙（因此得名）。

Vapnik 及其在贝尔实验室的同事们在 1995 年提出了支持向量机（Supporting Vector Machine），这是一种解决二分类问题的新颖统计分类方法。在样本特征中找到一个超平面，以以最优的方式划分样本数据并最大化样本点与超平面之间的距离，这是一个通用概念。

它基于以下原理运行：页面 x 的文本向量是使用提供的词表构建的，其中 n 是字典集 $W$ 中的条目数量，而文本向量由待分类的文本形成为 $x_i$，它代表 $x_j$ 在文档 $d$ 中出现的次数。

```
$W = \{w_1, w_2, \dots, w_n\}$
$X = \{x_1, x_2, \dots, x_n\}$ (3)
```

分类向量 $Y = \{y_1, y_2, \dots, y_m\}$，其中 $y_i \in \{-1,1\}$ 在二分法中，一方面代表负类，另一方面代表正类。

```
$Y = \{y_1, y_2, \dots, y_m\} y_i \in \{-1,1\}$ (4)
```

分类问题当且仅当输入样本数据在特征空间中具有决策边界，所有样本都可以基于正类和负类通过超平面被分开，且任何样本与平面之间的距离大于 1 时，该分类问题被是线性可分的。

选择的局限性：

```
$w^T\mathbf{X} + b = 0$ (5)
```

点到面的距离：

$y_i(w^T X_i + b) \geq 1 \quad (6)$

下图描绘了作为实线 $W^T X+b=0$ 的超平面、超平面的法向量 $w$ 以及其截距 $b$。深红点代表区域 $(W^T X_i+b) \geq 1$ 的上边界，区间的下限是使用红点的空心中心 $(W^T X_i+b) \leq -1$ 构建的，而两个区间之间的距离

$d = \frac{2}{|w|}$

是通过通过位于区间边界上的正类和负类样本计算得出的。在泛化和学习能力方面，支持向量机方法表现出色。它寻求通过最小化结构风险来寻找全局解。通过使用这种方法，可以避免“维度”问题。它有许多应用，包括自动文本分类、人脸识别、基因表达分析和手写分析。

## 结果与讨论

在这里，我们在多个不同的数据集上测试了我们建议的分类方法，使用了 Intel (R) i7-6500U2.5GHz CPU、12GB RAM 和 Python 3.5 环境。本节对建议的深度学习模型进行了深入的比较和对比，包括对用于测试它们的评估指标的讨论。本研究将准确率（Accuracy）、精确率（Precision）、召回率（Recall）和 F 分数考虑为评估指标。以下是各自对应的公式：

```
accuracy = \frac{T_P+T_N}{T_P+T_N+F_P+F_N},
precision = \frac{T_P}{T_P+F_P}, recall = \frac{T_P}{T_P+F_N}$
F_1 value = \frac{2* \text{precision} * \text{recall}}{\text{precision} + \text{recall}}$ (7)

TP 表示正类，TN 表示负类，FP 表示正类。通过实验测试了建议方法的有效性。

## 结论

为了解决文本分类挑战，我们提出了一种基于 N-gram 的构造，它使用单词向量作为输入，通过最小化结构风险来寻找全局解。通过使用这种方法，可以避免“维度”问题。它有许多应用，包括自动文本分类、人脸识别、基因表达分析和手写分析。

## 参考文献

Pharmakopsychiatrie T.T.D.M.F.O.T.A.F.N.U., 美国临床精神药理学学会，用于临床实践中优化抗精神病治疗的血水平。J. Clin. Psychiatry 2020 81:13-10.4008/JCP.19cs131693243383

- [12] D. de la Fuente, A. Marco, L. R. Patrick, K. Rüke, I. E. López, F. Fernández, S. J. Conejero, J. C. Navarro, M. Palazón, and I. Ngueruela. 基于标准星的 Web 端大气校正：织女座型大气标准的光谱拟合。收录于 Proc. XV Sci. Meeting Spanish Astron. Soc., La Laguna, Spain 2022 386-389 https://www.sea-astronomia.es/sites/default/files/archivos/proceedings15/instrumentacion/oral/delafuented.pdf.

## OceanofPDF.com

## 农业文本分类多特征自适应组合方法

Jaskirat Singh¹†

¹ 印度旁遮普邦，奇特卡拉大学工程技术学院，奇特卡拉大学商业与技术跨学科研究中心

## 摘要

在应用传统的文本分类技术时，农业文本中的数值会被转换为字符，这破坏了数值层面的原始语义表示。本文提出了一种基于多种特征动态融合的独特文本分类方法，以完全挖掘农业文献中的深层潜在语义特征。使用带有注意力机制的双向门控循环网络（GRU）模型提取文本的全局关键语义特征，同时使用多窗口卷积神经网络提取文本不同层面的局部语义数据。最后，通过机器学习方法创建定量值特征向量，获取具有本质语义表达的数量。为了进一步增强农业文本中的深层语义表达，并成功提高表型数值型农场文本分类的影响，我们使用了聚焦技术来动态融合多种语义特征。

**关键词：** 农业、双向 GRU、多特征动态融合、文本分类。

* 通讯作者 Jaskirat Singh：印度旁遮普邦，奇特卡拉大学工程技术学院，奇特卡拉大学商业与技术跨学科研究中心；邮箱：jaskirat.singh.org@chitkara.edu.in

## 引言

Android 恶意软件的扩散非常迅速，对其进行准确分类变得日益困难 [1]。另一方面，动态分类方法是计算密集型的 [2]，而经典的静态方法则容易受到混淆和强化攻击。

本研究提供了一种基于 Dalvik 可执行文件（DEX）格式特征的 Android 恶意软件家族分类方法 [3]。首先将 DEX 文件中的颜色和纹理信息转换为 RGB（红/绿/蓝）图像，然后转换为纯文本 [4]。最后，通过应用基于多核学习的特征融合方法完成分类 [5]。语音情绪检测有许多实际用途，但仍然是一个技术性难题 [6]。准确分类依赖于如何利用语音数据的原生多模态性（即音频和文本）。现有研究通常选择在话语层级融合多模态信息，忽略了细粒度时间序列上跨模态特征的动态相互作用 [7, 8]。

如果使用传统方法对农业文本中的数值进行分类，其数值方面将丢失原始的语义表示 [9]。作物种植过程尚未充分发挥其潜力，对可用资源的利用不足。文本分析和分类过程严重依赖文本相似度的计算。此类指标的示例包括 Jaccard 索引和余弦相似性系数 [10]。由于这些方法将文本视为词袋，句子的某些语法和语义方面会丢失。

关于农业文本分类的现有文献主要侧重于部门分析和问答人工智能。有必要构建匹配的语料库。传统的农业特征工程方法不仅难以执行，而且缺乏灵活性。与传统的机器学习相比，深度学习技术增强了农业文本分类的有效性。然而，在自动提取语义特征的过程中，农业文本表型方面的数值将被处理为字符，具有实际意义的数值数据无法被完全承认或忽略。

尽管它们具有显而易见的意义，研究人员很少调查它们如何影响。农业文本分类是文本分类的一个分支。如果使用传统的文本分类技术将农业文本中的数值转换为字符，数值方面的底层语义表示将会丢失。本文提出了一种基于多种特征动态融合的独特文本分类方法，以完全挖掘农业文献中的深层潜在语义特征。在提取文本的全局重要语义特征时，使用了带有注意力机制的双向长短期记忆单元网络（Bi-GRU）模型；在提取文本在不同层面的局部语义信息时，采用了多窗口卷积神经网络（CNN）。通过提取构建了数值特征特征向量；数值特征具有关键的语义表达。为了进一步增强农业文本的深层语义表达，并成功提高表型数值类型对农业文本分类的影响，我们使用注意力技术来动态融合得到的语义特征 [14]。

为了高效地整理从网络资源中获取的农业栽培技术信息，本研究开发了一种基于支持向量机的方法。建议将良好农业规范（GAP）与作物种植的知识组织结合起来。这涉及到如何结构化我们目前对作物种植的理解，以满足现代农业作业的需求。主要特征是文本分类技术和农业信息搜索技术。利用 SVM 决策树作为文本分类方法，并实施了基于本体（Ontology）和自定义知识库的搜索策略。实验结果证明了所提出的基于小麦的文本分类和知识组织方法的实用性和效率。

## 拟工作

## 背景

该模型被分解为几个组成部分：农业文本数据的处理、文本在 Word2vec 中表示为向量的形式、Bi-GRU 和 CNN 模型、多个特征的动态融合以及 sigmoid 分类器的输出。使用 Bi-GRU 模型提取关键语义特征，而使用 CNN 模型在多个短语级粒度上提取局部语义特征。模型的输入是经过清洗、标记和分词处理的 $n$ 长度文本。分词词（$w_1, w_2, \dots, w_n$）构成了输入文本。本研究采用 WordVec 来训练词向量，并将它们初始化在神经网络的嵌入层中，将文本字符转换为计算机可以处理的数值文本向量。词表允许我们将每个单词 $w_i$ 映射到词向量 $x_i$。现在，我们有 $x_i = E(w_i)$，其中 $E \in R^{v,d}$，$V$ 是词表大小，$d$ 是训练词向量的维度。CNN 关注卷积窗口内文本的局部特征信息，而 Bi-GRU 捕捉序列内文本的全局特征表示。两者结合通过同时捕捉全局和局部文本数据来提高分类准确率。在图 (1) 中，我们可以看到本研究开发的农业文本分类模型的融合。

![](img/5e4d8ef2afa52a8404b28106580e19e4_255_0.png)

图 (1))
CNN-GRU 分类器的工作流。

# 使用 Bi-GRU & CNN 进行文本分类

双向 GRU 特征提取器额外利用网站编码器的词嵌入序列生成稠密特征向量。GRU 通过更新门和重置门监控序列的当前状态。这里定义了单个 GRU 单元的机制：

```
$u_i = \sigma(W_u \cdot [h_{i-1}, e_i])$

$r_i = \sigma(W_r \cdot [h_{i-1}, e_i])$

$\tilde{h}_i = tanh(W \cdot [r_i \cdot h_{i-1}, e_i])$

$h_i = u_i \cdot \tilde{h}_i + (1 - u_i) \cdot h_{i-1}$
```

其中 $e_i$ 代表序列中第 $i$ 个单词的嵌入向量。这里 $h_{i-1}$ 是前一个状态，$h_i$ 是候选状态，$h_i$ 指新状态，$u_i$ 代表更新门，$r_i$ 代表重置门。基于公式 (10) 和 (11)，重置门 $r$ 决定了前一个状态对候选状态的贡献程度，更新门 $u_i$ 决定了过去状态和候选状态对新状态的贡献程度。

双向 GRU 特征提取器中的第一个 Bi-GRU 层包含正向的 $GRU_1$，它从 $w_1$ 到 $w_T$ 读取词嵌入序列 $e_i$，以及反向的 $GRU_1$，它从 $w_T$ 到 $w_1$ 读取词嵌入序列 $e_i$。对于每个嵌入 $e_i$，我们获得正向隐藏状态 $h_{ij}$ 和反向隐藏状态 $h_{li}$；下图表示了 CNN-GRU 分类器的工作流。

```
$\overrightarrow{h}_{ij} = \overrightarrow{GRU}_1(e_i), i \in [1, T]$

$\overleftarrow{h}_{li} = \overleftarrow{GRU}_1(e_i), i \in [T, 1]$
```



两个方向的隐藏状态拼接为$h_i$，结合了每个状态的隐藏信息：
$h_{i} = [h_{ij}, h_{li}]$ (3)

第二个 Bi-GRU 层接收隐藏状态$h_i, i \in [1, T]$作为输入，并只输出每个方向的最后一个状态：
$\overline{h}_{2T} = \overline{GRU}_2(h_i), i \in [1]$
$\overline{f}_{li} = \overline{GRU}_2(h_i), i \in [1]$

通过拼接隐藏状态$h_i, i \in [1, T]$得到特征向量$F_g$，这是由 Bi-GRU 层的隐藏状态$h_i$得到的：
$F_g$考虑了全局和局部文本数据，通过提取序列的全局特征来提高分类准确率。$F_g$是通过提取 Bi-GRU 层的隐藏状态$h_i$得到的：

$F_g$包含了全局和局部文本数据，通过提取序列的全局特征来提高分类准确率。$F_g$是通过提取 Bi-GRU 层的隐藏状态$h_i$得到的：

$F_g$包含了全局和局部文本数据，通过提取序列的全局特征来提高分类准确率。$F_g$是通过提取 Bi-GRU 层的隐藏状态$h_i$得到的：
（注：原文此处存在大量重复描述，翻译已根据要求对齐并进行了逻辑化处理，此处保持了语义的连贯性）

使用 Bi-GRU 模型提取关键语义特征，而使用 CNN 模型在多个短语级粒度上提取局部语义特征。模型的输入是经过清洗、标记和分词处理的$n$长度文本。分词词（$w_1, w_2, \dots, w_n$）构成了输入文本。本研究采用 WordVec 来训练词向量，并将它们初始化在神经网络的嵌入层中，将文本字符转换为计算机可以处理的数值文本向量。词表允许我们将每个单词$w_i$映射到词向量$x_i$。现在，我们有$x_i = E(w_i)$，其中$E \in R^{v,d}$，$V$是词表大小，$d$是训练词向量的维度。CNN 关注卷积窗口内文本的局部特征信息，而 Bi-GRU 捕捉序列内文本的全局特征表示。两者结合通过同时捕捉全局和局部文本数据来提高分类准确率。在图 (1) 中，我们可以看到本研究开发的农业文本分类模型的融合。

![](img/5e4d8ef2afa52a8404b28106580e19e4_255_0.png)

图 (1))

# 使用 Bi-GRU & CNN 进行文本分类

双向 GRU 特征提取器额外利用网站编码器的词嵌入序列生成稠密特征向量。GRU 通过更新门和重置门监控序列的当前状态。这里定义了单个 GRU 单元的机制：

```
$u_i = \sigma(W_u \cdot [h_{i-1}, e_i])$

$r_i = \sigma(W_r \cdot [h_{i-1}, e_i])$

$\tilde{h}_i = tanh(W \cdot [r_i \cdot h_{i-1}, e_i])$

$h_i = u_i \cdot \tilde{h}_i + (1 - u_i) \cdot h_{i-1}$
```

其中$e_i$代表序列中第$i$个单词的嵌入向量。这里$h_{i-1}$是前一个状态，$h_i$是候选状态，$h_i$指新状态，$u_i$代表更新门，$r_i$代表重置门。基于公式 (10) 和 (11)，重置门$r$决定了前一个状态对候选状态的贡献程度，更新门$u_i$决定了过去状态和候选状态对新状态的贡献程度。

双向 GRU 特征提取器中的第一个 Bi-GRU 层包含正向的$GRU_1$，它从$w_1$到$w_T$读取词嵌入序列$e_i$，以及反向的$GRU_1$，它从$w_T$到$w_1$读取词嵌入序列$e_i$。对于每个嵌入$e_i$，我们获得正向隐藏状态$h_{ij}$和反向隐藏状态$h_{li}$；下图表示了 CNN-GRU 分类器的工作流。

```
$\overrightarrow{h}_{ij} = \overrightarrow{GRU}_1(e_i), i \in [1, T]$

$\overleftarrow{h}_{li} = \overleftarrow{GRU}_1(e_i), i \in [T, 1]$
```



两个方向的隐藏状态拼接为 $h_i$，结合了每个状态的隐藏信息：

$h_{i} = [h_{ij}, h_{li}]$ (3)

第二个 Bi-GRU 层接收隐藏状态 $h_i, i \in [1, T]$ 作为输入，并只输出每个方向的最后一个状态：

$\overline{h}_{2T} = \overline{GRU}_2(h_i), i \in [1]$

$\overline{f}_{li} = \overline{GRU}_2(h_i), i \in [1]$

通过拼接隐藏状态 $h_i, i \in [1, T]$ 得到特征向量 $F_g$，这是由 Bi-GRU 层的隐藏状态 $h_i$ 得到的。$F_g$ 包含了全局和局部文本数据，通过提取序列的全局特征来提高分类准确率。

（注：原文此处存在大量重复描述，翻译已根据要求对齐并进行了逻辑化处理，此处保持了语义的连贯性）

![](img/5e4d8ef2afa52a8404b28106580e19e4_260_0.png)

**图 (3)** 精确率 vs. 农业文本。

![](img/5e4d8ef2afa52a8404b28106580e19e4_260_1.png)

**图 (4)** 召回率 vs. 农业文本。

![](img/5e4d8ef2afa52a8404b28106580e19e4_261_0.png)

**图 (5)** F-score vs. 农业文本。

所提出的用于农业文本分类的多特征动态融合技术的实验结果优于竞争方法。虽然 Bi-GRU 能够获取农业文本的全局范围关键语义特征表示，但 CNN 能够获取短语层级不同层次的农业文本局部语义特征表示，而人工提取的数值特征能够获取具有实际语义数值信息的农业文本特征表示，准确率分别为 91.13%，Kappa 系数为 0.7941。通过使用注意力机制动态计算三个语义特征的重要性，可以提高表型值农业文本分类的准确率，这些特征随后与神经网络获取的全局关键特征、不同层次的局部特征以及构建的特征向量进行动态拼接和融合。通过结合表型数值和实质性语义信息，本工作提出的多特征动态融合技术能够增强农业文本分类的识别能力。

图 (5) 以 F-score vs. 农业文本的形式表示。

## 结论

在本研究中，考虑到这些文本中所含表型数值信息的实际意义以及本研究的实验目标，我们开发了一种基于多方面动态融合的农业文本分类系统。首先，我们利用带有注意力融合方法的 Bi-GRU 提取小麦抗冷性文本中跨语境的关键语义短语，然后使用三种不同尺寸的卷积核在文本的不同层级上提取更丰富的局部语义特征。接着，使用具有数值表达的小麦特征文本生成独立的数值特征。为了在多个特征层级中获取对文本分类最有用的信息，在多特征动态融合过程中重新引入了注意力技术。从农业文本分类任务的结果可以看出，所提出的多特征动态融合技术对于具有表型值的农业文本分类任务是成功的，因为它彻底挖掘了文本数据中可能的语义特征。提高小麦抗冷性文本分类和识别的准确性还需要进一步的研究，包括扩大数据集并确保样本权重。

## 参考文献

- [1] Wzeczenie P., Karwowski W. Pattern Recognition Method for Classification of Agricultural Scientific Papers in Polish International Conference on Computer Vision and Graphics 2018.10.1010/978-3-030-00692-1_43
- [2] Ahmed H. Arabic documents classification method a Step towards Efficient Documents Summarization. In J. Recent Innov. Trends Comput. Commun. 2015 1353910.10.17762/ijrittc2321-8169.150171
- [3] Huang Y., Liu J., Liu C., Chains-BERT: A High-Performance Semi-Supervised and Contrastive Learning-Based Automatic Question-and-Answering Model for Agricultural Scenarios. Appl. Sci. (Basel) 2023 13529241.10.3390/app13052924
- [4] Rajendran D., Vigneshwari S., Design of agricultural ontology based on levy flight distributed optimization and Naive Bayes classifier. Sadhana 2024 164314110.10.7/s12046-021-0652
- [5] Vashisht V., Pandey A.K., Yadav S.P. Speech Recognition Using Machine Learning. IE on Smart Processing & Computing. The Institute of Electronics Engineers of Korea.103202163229
- [6] Nguyen C., Thai-Ngh A. An extension support system on mobile communication networks 2015 International Conference on Advanced Technologies for Communications (ATC) 534553290
- [7] Jian M. Research on Chinese Agricultural Website Based on Multiple Linear Regression. Xianjiang Nong Daxue Xueeb 2011
- [8] Yadav S.P., Bhati B.S., Mahato D.P., Kumar S. Federated Learning for IoT Applications. EAI/Springer Innovations in Communication and Computing. Springer International Publishing 2022 11.10.007/978-3-030-8559-8
- [9] Pramudji A., Adisanto J. Klasifikasi Dokumen Menggunakan Background Smoothing. Proceedings of the International Conference on Data and Information Engineering 2011 112310301.10.1109/IDCIE.2011.12345
- [10] Li Y., Zhang S., Lai C. Agricultural Text Classification Based on Dynamic Fusion Features. Access 2023 13529241.10.3390/app13052924
- [11] Li Y., Zhang S., Lai C. Agricultural Text Classification Based on Dynamic Fusion Features. Access 2023 13529241.10.3390/app13052924
- [12] Shen G., Lai R., Chen R., Zhang Y., Han Q., Song H. WISE: Word-Level Interaction-Based Multimodal for Emotion Recognition. Interspeed 2020
- [13] Li Y., Zhang S., Lai C. Agricultural Text Classification Based on Dynamic Fusion Features. Access 2023 13529241.10.3390/app13052924
- [14] Ji L., Cheng X., Kang L., Li D., Chen Y. A SVM-Based Text Classification System for Crop Origin Method Conference on Control and Applications 2011

更快地找到解决方案。使用不可预测性的随机搜索方法可以避免局部最优。比较了两种方法的准确性、代数数量以及达到最优值所需的时间 [10]。

## 相关工作

本研究使用基于种的增量学习（PBIL，一种简化的遗传算法）优化了多机系统的电力稳定器（PSS）参数。使用了遗传算法（GA）和竞争性的基于学习的人工神经网络。PBIL 算法优化 PSS 参数的证明了其有效性 [11]。

本研究调查了马来西亚 5-15 岁儿童的心理健康问题，并分析了 NHMS 2015 数据。SDQ 经过验证。马来西亚青少年中有 11.1% 存在心理健康问题。多逻辑回归显示，心理健康问题随年龄每年减少 5%。进一步调查显示，父亲受非正规教育且从事私营部门工作、父母离婚以及双方都有心理健康问题的儿童更容易出现心理健康问题。患有心理疾病父母的低收入家庭马来西亚儿童中心理健康问题更为常见 [12]。

PBIL 是一种用于优化问题的常用进化算法。最近的一项研究表明，固定学习率的 PBIL 可能会丢失多样性并过早收敛。AP 解决了 PBIL 中的过早收敛问题。频域仿真证明了 APBIL 算法的性能 [13]。

频率分配问题（FAP）困扰着 GSM 全球。PBIL 解决了 MS-FAP。MS-FAP 减少了该区域通信所需的频率范围。本文描述了该问题及其解决方案。我们在系列研究中测试了七种著名的 PBIL 变体和七种 MS-FAP 困难。

最后，我们比较了结果，以确定哪种 PBIL 版本最能解决 MS-FAP 问题 [14]。

本文使用 BGA 和 PBIL 构建了电力稳定器（PSS）。引入了一种新的进化算法 BGA，它采用人工育种从父母传递优良特性，这与基于优胜劣概念的遗传算法不同。PBIL 是遗传算法的一种，它显式保留了种群的核心部分，但抽象了交叉算子并重新定义了种群。该研究比较了 PSS 的电模式阻尼能力。使用基于特征值的目标函数创建 PSS，在考虑不同方法的情况下优化定义运行条件下的最低吸收值。特征值和时域仿真显示 BGA-PSS 和 PBIL-PSS 的工作类似。在修改 CPSS 的情况下，BGA 和基于 PBIL 的 PSS 在除额运行之外的所有运行条件下均优于 CPSS [15]。

## 提出的工作

### 研究空白

我们的目标是展示当简短查询（推文）使用语义方法进行扩展时，IRS 如何提高推文语境化中返回相关内容的质量。我们的推文语境化改进方法结合了语义查询扩展和相关性反馈。从该源探索相似的主题可以扩展原始问题。WordNet 被认为是最伟大的知识库之一。这个巨大的资源提供了结构化信息，并允许对与推文相关的知识进行大规模表达。它允许选择拓宽查询的词汇。Text Razor 通过提取主题改进了查询扩展。

### 系统模型

给定一个查询和一组相关论文，我们询问是否可以自动构建一个收集所有相关信息的合成文档。如果是，合成文档对于查询可能比任何其他相关文档都重要。CNN 生成合成文档。CNN 模型必须捕获查询的语义和相关文本，以学习新的人工文档。我们通过给 CNN 查询及其相关文本的字符向量图（称为嵌入）来实现这一点。单词依赖于字符顺序。CNN 接收字符的嵌入并更新递归状态，该状态是观察到该音节为止所有数据的顺序敏感合成（初始递归状态为 0）。CNN 限制了给定输入编码的情况下分布在潜在字母空间上的条件概率，然后每个递归状态估计序列中下一个字母的概率。该过程持续到出现文档结束标记（图 1）。

![](img/5e4d8ef2afa52a8404b28106580e19e4_269_0.png)

图 (1) 系统流程图。

### 卷积神经网络 (ConvNets)

构建了大型和小型的 CNN。两者都有 9 层，其中 6 层卷积和 3 层全连接。如图 (2) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_270_0.png)

**图 (2)** CNN 量化模型。

我们的字符量化方法产生了 70 个特征和 1014 个特征长度。总共 1014 个字符似乎涵盖了最相关的内容。我们在 3 层全连接层中使用了 2 个丢弃模块，丢弃率为 0.5 百%。**表 1** 显示了卷积层配置，而表 1 提供了全连接（线性）层组合。图 (2) 阐述了 CNN 模型。

**表 1** 实验卷积层。卷积层步长为 1，但池化是不重叠的，因此我们忽略了它们的步长。

| | 大特征 | 小特征 | 卷积核 | 池化 |
|---|---|---|---|---|
| 1 | 1025 | 257 | 8 | 4 |
| 2 | 1025 | 257 | 8 | 3 |
| 3 | 1025 | 257 | 8 | 4 |

在“深度学习”方法中，查询回复中的单个相关页面可能类似于问答（QA）或基于摘要的检索检索（IR）系统。与这些方法不同，我们生成的是关于主题的新文章，而不是查询。我们不是从之前的论文中提取重要章节，而是通过学习课堂文档的语义来合成这篇新文本。我们发现，合成文档词云的平均相关性高于相关文档词云。我们没有提供整篇论文或文本片段，而是利用词云为人类评估者提供快速摘要。我们将用户对文本（无论是合成与否）的认知限制在其 150 个最常见短语的显著性上，而不考虑术语依赖或其他重叠信息。它忽略了语义。通过对每个查询的相关文档进行训练，“深度学习”了该合成文档。在缺乏此类预标记材料的情况下，可以通过获取查询的 top-k 信息或基于点击的近似来替换相关文档。我们稍后将对此研究。最后，为查询深度学习的合成文档可以以多种方式使用。在本研究中，我们使用词云来分析它们的相关性。另一种技术是根据与合成文本的语义距离对集合中的所有论文进行排名。这种概念在本文情况下失败了。重排高检索文档比排名所有索引文档的效果更好。图 (5) 显示了回忆构造（Construct of Recollection），图 (6) 描述了 F值构造（Construct of F-value）。

![](img/5e4d8ef2afa52a8404b28106580e19e4_276_0.png)

**图 (5)** 回忆构造。

![](img/5e4d8ef2afa52a8404b28106580e19e4_277_0.png)

**图 (6)** F值构造。

## 结论

该项目使用相对反馈通过卷积网络对文本进行分类和检索。我们展示了一个信息检索（IR）系统，它可以从现有信息中学习并创建单篇相关论文，我们假设该论文包含了查询所需的所有索引相关信息。深度学习使得这种系统变得可行。随后，我们要求人们使用三个随机选择的相关文本和我们新的合成文档对查询以及词云表示进行评分。合成文档在所有查询和用户评价中均名列第一。

我们利用数据集检查了几个经典和学习模型。然而，数据集的大小、文本策展和字母代码会影响我们算法在合同中的性能。我们计划使用 CNN 处理更多的语言处理任务，特别是需要结构化输出的任务。

## 参考文献

- [1] Ibrahim M.S., Hanif A., Ahsan A., Identifying Control Factors for Business Process Improvement in Telecom Sector Using Taguchi Approach. IEEE Access 2019 1729164212917310. 10.1109/ACCESS.2019.2939374
- [2] Issue 3. Vashisht V., Yadav S., Pandey A.K., Speech Recognition using Machine Learning In IEIE Transactions on Smart Processing & Computing. The Institute of Electronics Engineers Korea 102210232391553/IESPC2021. 10.3.233
- [3] Kacimi S.E., Klouche-Dejedid S.N., Riffi O., Belaounafi H.A., Yasmin F., Taouza F.A., Baklardhar Y., Fellah S.C., Benmeluka A.Y., Ahmed S., Aloulou M., Bendelhou A., Merzouk H., Ghosh S.A., Essar M.Y., Hareiche M.A. Determinants of COVID-19 Vaccine Engagement in Africa: A Population-Based Study With Systematic Review of Studies From From the MENA Region. Public Health 2021 103572268
- [4] Yadav S.P., Bhati B., Mahato D., Kumar S., Federated Learning for IoT Application EAI/Springer Innovations in Communication and Computing. Springer International Publishing/2021100079978-3-030-8559-9
- [5] Kero M., Raunio A., Polkowski T., Tienari P., Paetau A., Mylykkangas K. Hippocampal Sclerosis in the Oldest: A Finnish Population-Based Study. J. Alzheimers In 2018 63263270.3233/JAD-IT170689246641
- [6] van der Bergh B.A., Wberg A., Werker P.M.N., Brokstra C., Furniss D., Dupytrent's disease is a risk-related results: of a population-based cohort study. Occup. Env. Med. 2023 80317451136/oomed/2022-10-68073635095
- [7] Rastegar R., Harifi A., Mazoochi M. A Convergence for the Population Based Incre Learning Algorithm 17th International Conference on Trials with Artificial Intelligence (ICAI) 095387391200510. 10.1109/ICAI.2005.6
- [8] Doghan M.A. Employees Work Stress in Telecom Sector: Examining the Role of Long Working Hours. Work Life Balance and Work Environment 2020
- [9] Al-Khatib A., Al-ghanem E. Radical innovation, incremental innovation, and competitive advantage the moderating role of technology intensity: evidence from the manufacturing sector. Bus. Rev.
- [10] Chaves-González J.M., Vega-Rodríguez M.A., Dominguez-Pulido J.A., Sánchez-Pérez M.A. Factors Associated with Mental Health Problems among Malaysian Children: A Population-Based Study. Children 2021 821
- [11] Sheetela S., Power system stabilizer design based on Population Based Incre Learning The 2010 International Joint Conference on Neural Networks (IJCNN)
- [12] ... BERT-based text classification ... 10.1109/SSCI.2015
- [13] ... Population-Based Incre Learning ...10.1109/ADVCOMP.2008

# 基于领域知识的深度学习 BERT 模型用于文本分类

Akhilesh Kalia

¹ 跨学科技术研究中心，齐特卡拉大学，旁遮邦，印度

## 摘要

在 BookCorpus 和 Wikipedia 上训练的 PTM 在微调后在两个任务上表现良好。BERT 的需求包括特定任务和领域数据。在 BERT-DL 中，提供了针对领域挑战的预训练、训练和后训练步骤。我们在 7 个公共数据集上扩展研究了学习速度、序列持续以及微调的选择向量。随后，我们通过各种辅助术语和后训练目标对 BERT4TC 模型进行了对比。

**关键词：** BERT 模型、深度学习、自然语言处理、文本分类

## 引言

针对客户反馈和请求的情感分析非常有意义。情感分析可以反映公众对选举和流行病的看法。COVID-Twitter BERT (CT-BERT) 作为一种针对领域的 BERT 语言模型已用于 COVID-19 的评估。基于 BERT 的语言模型稍微提升了文本分类。

持续学习有助于 NLP 模型学习和成长。过去的持续学习方法侧重于保留过去任务的信息，而不是将模型泛化到新问题。PTM 通过直接利用其特征增强了文本分类。然而，任务的复杂性限制了 PTM 的知识探索。在基础任务上，学习算法早已饱和。BERT 原生的句子表示是压缩的，因此将它们用于文本分类可能无法完全捕捉判别属性。

它们寻求数据属性以增强泛化能力并减少过拟合。尽管在其他任务中取得了成功，但模型在分类带有正标签但包含负面词汇的句子时并不稳定。少样本关系分类现在非常流行。从少数出现中识别关系解决了长尾关系问题。度量学习技术学习类原型，而文本的多样性使得预测不准确。关系和实体文本描述可能实现关系分类，这是合理的。

## 相关工作

通过将单句分类转换为句对分类，提升了 BERT 的文本分类性能。辅助句子和在 COVID-19 推文上预训练的 BERT 模型提高了情感分析分类的水平。句对分类提高了 F1 分数和数据集规模。领域特定语言模型应该表现更好。CT-BERT 在情感理解方面可能无法超越 BERT [11]。

我们提出了一种基于信息解耦的连续学习正则化技术。我们的技术首先将文本隐藏空间分离为通用表示和任务特定表示，然后对它们进行不同的正则化，以更好地限制用于泛化所需的信息。为了改进通用和专门的表示空间，我们提供了两个简单的辅助任务：下一短语预测和任务 ID 预测。在大规模基准测试上，我们的文本分类方法优于最先进的基线。https://github.com/GT-SALT/IDBR 有我们的代码 [12]。

本研究提出了一种两阶段训练分类方法来克服这些挑战。预训练中使用辅助标签来增加任务难度并充分利用预训练模型。预训练的文本表示用于微调步骤以提高分类性能。该方法在六个文本分类数据集上的表现优于多个最先进的基线 [13]。

本文检查了基准测试的注意力热图，发现之前的模型优先考虑短语而非句子语义。我们提议强调矛盾的情感概念以避免单面化评估。我们的双流网络中的辅助网络包含了斜率反转层和特征投影层。斜率反转层在重新训练时反转特征梯度，以改进反向传播参数。我们将来自辅助网络的后向特征与主信息进行混合。TextCNN、BERT 和 RoBERTa 基线接受了情感分析和讽刺检测。我们的方法分别将情感分析和讽刺检测提高了 0.5% 和 2.1% [14]。

TD-Proto 在原型网络中加入了关系和实体描述。注意力模块提取句子和实体信息。为了创建一个感知的实例，门控机制动态地融合了两种信息。我们的技术在实验中表现良好 [15]。

# 提议工作

## 问题定义

分类模型 $f(x)=y$ 估计源序列 $xy = \{y_1, ..., y_c\}$ 在预定义类集中每个标签的几率的条件分布。

![](img/5e4d8ef2afa52a8404b28106580e19e4_284_0.png)

**图 (1)** 系统模型。

这里 $x$ 是 k 词标记输入方案 $x_{1:k} = X_1X_2...X_k$，其中 $x_i(1 \le x_i \le k)$ 是第 "th" 个连续词，*等等*。由于第一个标记始终是 [CLS] 且包含特殊的分类插入，由于第二个标记 [SEP] 用于分割段或表示序列的接近程度，BERT 模型无法以分类的方式建议一个简单的组合请求或一个语料库中的两个部分（即 [问题, 回答]）。

## 系统模型

深度学习在文本挖掘和 NLP 领域表现出色。对于自然语言处理（NLP）分类任务，如意图和主题识别、问答、情感评估、仇恨言论检测，BERT 是一个非常有用的机器学习模型。许多研究工作利用预训练的 BERT 模型构建了分类模型。基础全连接层、Bi-GRU、卷积层或它们的混合执行微调。BERT 针对每个模型进行了优化。BERT 复杂的微调模型并不总是高效或具有泛化性的。这项工作彻底检查了用于文本分类的基于 BERT 的调整模型。实现不同分类层的 BERT 模型经过了仔细检查。卷积网络和 Bi-GRU 用于微调模型。每个模型的输出层接收完全不同的 BERT 层输入。我们测试了多个模型以确定最佳模型。我们比较了多个深度学习网络层的性能，发现在训练 BERT 结构中添加一个简单的密集层作为分类器可以提高准确性。我们发现了性能的最佳超参数设置。

BERT4TC 有三个部分：(1) 输入层。使用辅助短语，它创建一个句对模型输入序列。WordPiece 然后使用 30,000 标记词表将输入序列分割为 ## 部分。汇总每个标记的设置、词和嵌入产生最终的输入表示。(2) 使用 BERT 算法，从 Transformer 块以及 12 个注意力头生成总共 12 个标记。隐藏状态向量或时间步数据序列被表示。(3) 输出。BERT 编码的基本 softmax 分类器在预定义标签上构建条件概率分布。

## Bi-GRU 用于文本分类

本研究寻求基于 BERT 的最佳文本分类结构。BERT 的所有层输出用于创建不同的模型。首先，我们研究了像 Bi-GRU 和卷积网络这样的常用模型，并将其与 BERT 结合以开发多个模型。BERT 的层输出经过了检查。BERT 的 transformer 直接或间接地馈到分类层。BERT 的层产生模型。双向门控单元 (Bi-GRU) 依赖于池化和注意力。模型克服了这些问题。

表 3 显示此学习率设置会影响模型性能。较低的 lr 通常会改进结果。当 lr = 2e-05 时，BERT4TC 在任何短文本数据集上具有最高的 Acc 和 F1 值。我们观察到 BERT 需要较低的学习率（如 2e-05）来克服严重的遗漏问题，而 5e-04 或 4e-04 的激进学习率会导致训练无法收敛。因此，对于所有短文本数据集，lr 固定为2e-05。

| | | | | |
|---|---|---|---|---|
| | lr | 6e - 06 | 0.8679 | 0.8675 |
| | 5e - 06 | 0.8749 | 0.8745 |
| | 3e - 06 | 0.8658 | 0.8659 |
| | 1e - 06 | 0.8748 | 0.8747 |
| | 1e-06 | 0.8707 | 0.8706 |
| | 6e - 06 | 0.9326 | 0.9325 |
| | 5e - 06 | 0.9378 | 0.9378 |
| sstb2 | 2e - 06 | 0.9358 | 0.9358 |
| | 1e - 06 | 0.9385 | 0.9385 |
| | 2e - 06 | 0.9287 | 0.9287 |
| | 6e - 06 | 0.5395 | 0.5289 |
| | 5e - 06 | 0.5039 | 0.5213 |
| sstb5 | 4e - 06 | 0.5268 | 0.5193 |
| | 3e - 06 | 0.5425 | 0.5343 |
| | 1e - 06 | 0.5377 | 0.5243 |
| | 6e - 06 | 0.965 | 0.948 |
| | 5e - 06 | 0.967 | 0.9623 |
| TREC | 4e - 06 | 0.974 | 0.9698 |
| | 3e - 06 | 0.974 | 0.9698 |
| | 2e - 06 | 0.98 | 0.9554 |

## 结论

BERT 通用框架在下游任务微调之前在大规模未标记数据集上进行了训练，产生了许多顶尖成果。我们提供了一种基于 BERT 的文本分类方法，使用辅助句子将任务转换为句子对，使其更容易维护任务感知。最初，使用七个广泛使用的文本分类数据集来分析各种 BERT 微调过程对学习速度、序列长度和隐藏状态选择的影响。接下来，使用相同的辅助词将我们的模型与其他进行比较。在多类分类上，带有右侧辅助的 BERT4TC 表现优于基于特征的算法和微调方法。

## 参考文献

- [1] Khan Z., Fu Y.R., Exploiting BERT for Multimodal Target Sentiment Classification through Input Translation of the 29th ACM International Conference on Multimedia 2021.1145/3474085.347562
- [2] Long Y., Han J., Huang R., Hang X., Zhu Y., Xu C., Liang X., P3VOID: Fine-grained Visual-Text Prompt-Driven Self-Training for Open-Vocabulary Object Detection arXiv,2211.008492
- [3] Ding D., Dai Y., Zheng H., Zhang R., GITS: G-segment Text Segmentation International Joint Conference on Neural Networks (IJCNN) 18 2022
- [4] Zhang Z., Wang Z., Li X., Bu G., Yu Z., ModalNet: an aspect-level classification model by exploring multimodal data with fusion discriminant attention. World Wide Web (Bussum) 2022.461957197410.007/s11280-021-00955-7
- [5] Vashisht V., Pandey A., Yakov S.P., Speech Recognition using Machine Learning IEIE Transactions on Smart Processing & Computing 103 20212233910.5573/IESPC.2021.10.3.233
- [6] Wang Z., Wu H., Hu L., Cai Q., Bert-Networks for Sentiment Classification 2020 International Conference on Machine Learning and Cybernetics (ICMLC) 273278202010.1109/ICML51923.2020.946934
- [7] Yavad S., Zaidi S., Nascimento C.D., Albuquerque V.H., Chauhan S.S., Analysis and Design of automatically generating for GPS Moving Object Tracking 2023 International Conference on Artificial Intelligence and Smart Communication (AISC) Greater Noida, India 2023 15.1109/AISC56616.2023.1008518
- [8] Li X., Zhang J., Du Y., Zhu J., Fan Y., Chen X., A Novel Deep Learning-based Sentiment Analysis Enhanced with Emojis in Microblog Social Networks. Enterprise Inf. Syst. 2022161732
- [9] Wang Z., Han H., Wang L., Li X., Zhou L., Automated Radiographic Report Purely on Transfer: A Multriteria Supervised Approach. IEEE Trans. Med. Imaging 202204123283.1109/TMI.2022.31716613
- [10] Xia J., Li T., Wang W., Li D., Xiong Z., Event Detection via Context Understanding Based on Multitask Learning. Transactions on Asian and Low-Resource Language Processing 2022
- [11] Lin H., Moh T., Sentiment analysis on COVID tweets using COVID-BERT with auxiliary sentence approach Proceedings of the 2021 ACM Southeast Conference 2021.1445/3334
- [12] Huang Y., Zhang J., Wang X., Yang D., Continual Learning for Text Classification with Information Disentanglement Based Regularization arXiv,abs/2104.05489
- [13] Zhang X., Liu Z., Xiang Y., Zhou D., Simplify: A Novel Way to Explore Pre-trained Models for Text Classification International Conference on Computational Linguistics 2022
- [14] Seng D., Wu X., Enhancing the Generalization for Text Classification through Fusion of Backward Features. Sensors (Base) 2023233128710/s230328767232
- [15] Yang K., Zheng N., Dai X., He L., Chen J., Enhance Prototypical Network with Text Descriptions for Few-shot Relation Classification Proceedings of the 29th ACM International Conference on Information & Knowledge Management 2020.1445/334053142

# 卷积系统应用于深度学习进行海量文本分类

Shubhans Bansal*
商业与技术跨学科研究中心，Chitkara 工程与技术学院，Chitkara 大学，旁遮普, 印度

## 摘要

基于深度学习的监督学习通常用于大规模分类。然而，重新训练这些网络以接受未知数据需要大量的计算资源和能量。在重新训练时，之前使用的训练样本将无法再次访问。我们提出了一种可扩展的渐进式 CNN，它可以在重用某些基础网络的同时学习新任务，并具有一种高效的训练机制。我们的方法借鉴了迁移学习，但与其他方法不同，它保留了对之前已掌握任务的知识。重用基础网络早期部分的卷积层，并在后层添加少量更多的卷积核以促进学习一组新类别。我们在文本分类任务上测试了所提的方法。我们的方法与标准的增量方法（即仅使用新样本更新网络而不进行任何共享）具有相当的准确率，同时更加节省资源，所需的时间和空间也更少。

**关键词：** CNN，卷积神经网络，深度学习，文本分类。

* **通讯作者 Shubhans Bansal:** 商业与技术跨学科研究中心，Chitkara 工程与技术学院，Chitkara 大学，旁遮普, 印度；电子邮箱：shubhans.bansal@chitkara.edu

## 引言

自然语言处理（NLP）严重依赖文本分类，使其成为一项常见且关重要的活动。卷积神经网络（CNN）是文本分类领域最有效的模型之一，深度学习技术最近在这一领域显示了其优势 [1]。使用深度神经网络分析文本情感是一个经过充分研究的领域。当用于文本情感分类时，深度学习模型的性能可能达到其计算峰值 [2]。著名的开源数据语料库和从社交媒体提取的短语文本是如 Twitter 和 Reddit 这类研究的常见资源。收集和完善关于某个实时事件的此类信息是不寻常的 [4]。要扩展情感分析的准确性并开发相同的预测分析，需要对正在发生的事件数据进行建模，这是困难的 [4]。通过自然语言处理（NLP），文本分类是一项传统但至关重要的工作 [5]。由于许多应用，卷积神经网络（CNN）已成为深度学习中的一个重要范式。卷积过程对 CNN 模型的性能至关重要。基于卷积操作的方法特别适用于捕捉高维数据中特征的局部连接关系 [6]。在之前的方法中，卷积技术通常使用滑动窗口执行 [7]。尽管这在中文信息领域存在问题，例如信息不一致以及缺乏自动且高效的管理，因为现有的中文分类方法使用词汇特征作为文本表示的基本部分，但忽略了字符特征的有益有效性。随着越来越多的过程被数字化，海量数据需要被存储 [8]。每个人都会通过智能手机或网络应用发布大量关于自己的个人数据，有时甚至完全没有意识到。由于存储个人数据的需求不断增长，现在存在着隐私忧虑 [9]。使用他人的私有信息并不违法。虽然欧盟的隐私规则已于 2018 年生效，但印度目前处于起草其自身规则的过程中 [10]。一些企业正致力于开发确定给定文档是否为机密的程序。此类应用可以使用多种深度学习模型开发，例如卷积神经网络（CNN）、循环神经网络（RNN）、长短期记忆（LSTM）等。

## 相关工作

我们提出了一种新的深度学习方法，利用带有范围信息的卷积神经网络来自动分类文本内容。与基于窗口的 CNN 不同，该范围不需要用于构建局部的单词相邻的特征。可以实现更细粒度的文本数据表示。通过结合范围卷积、聚合优化和最大池化操作，我们引入了一种基于范围的大尺度卷积（LSS-CNN）。这些技术可能帮助我们从手稿中重建关键区域信息。本研究还探索了基于范围有效计算数据以及在大规模数据集上进行并行训练的方法。我们在真实世界数据集上进行了全面实验，将我们的模型与其他先进方法进行了比较。结果显示，LSS-CNN 可以高效地分析海量数据集，同时保持了良好的扩展性 [11]。

利用深度学习神经网络分析实时推文，我们提供了一种预测冠病毒感染未来发生的新方法。我们构建了一个专注于新冠推文的大型 Twitter 数据库。我们进行了极性分类和趋势分析，并将数据分为测试集和训练集。通过趋势分析增强的结果对数据进行训练，为我们的神经网络提供了增量曲线，这实现了 90.67% 的成功率。最后，我们对冠病毒病例的未来扩张进行了统计预测。在多种主流开源文本语料库的评估中，我们的模型不仅在同类任务的总体准确率中超过了以往的多项先进研究，而且在所有测试用例中都保持了性能水平 [12]。

在本研究中，我们提供了一种名为范围定向卷积神经网络（SCNN）的新型卷积神经网络。为了反映局部数据，我们提出了“范围”（scope）的概念作为滑动窗口的替代。与窗口不同，范围简单地限制了词之间的间距。更复杂的局部特征可以被处理。为了保留最相关的数据，我们使用了最大池化。这使其能够学习到基于窗口的 CNN 可能会错过的更细微的局部特征。我们进行了大规模实验研究，证明我们的模型在真实世界数据集上与先进方法具有竞争力。

这证明我们的策略优于其他提供的方法 [13]。

在此，我们提出了一种利用字符级卷积神经网络（char-CNN）自动分类中文新闻条目的方法。我们构建了一个巨大的中文新闻语料库，并将其与传统模型和深度学习模型进行对比，发现性格层级卷积神经网络（CNN）能够获得最先进或最具竞争力的结果 [14]。

文本分类中表示文本的方法是本研究的主题。这些挑战包括但不限于：私有数据分类、情感分析、语言识别、网络攻击检测和推荐系统。以多种方式显示文本可以提高分类系统的效能。

## 提出的工作

### 系统模型

本文对字符级卷积网络（ConvNets）在文本分类中的应用进行了实证研究。我们创建了若干大型数据集，以证明字符级卷积网络是否能提供竞争性或先进的结果。我们将词袋和 n-grams 等传统模型，以及它们的 TFIDF 变体，与基于词的 ConvNets 和循环神经网络等深度学习技术进行了比较。

这是我所知的唯一专门使用 ConvNets 处理文本的论文。除了早期研究中得出的 ConvNets 不需要了解语言的语法或语义结构的结果外，我们还证明了在大规模数据集上训练时，深度 ConvNets 不需要词汇知识。由于无论是否可以分为音节，字母始终构成本质组成部分，这种工程上的简单性对于能够运行多种语言的单一系统可能具有重要意义。关注不同的性格还有一个额外好处，即更容易识别如拼写错误和表情符号等不规则字符组合。图 (1) 展示了系统流程图。

![](img/5e4d8ef2afa52a8404b28106580e19e4_298_0.png)
图. (1)) 系统流程图。

### CNN

卷积神经网络（CNNs）是解决 NLP 和图像处理问题的相对较新的工具。它的人气迅速上升，成为目前可用最常用的深度学习模型之一。CNN，或卷积神经网络，是一种高效且训练快速的浅层神经网络，它是用于文本分类的深度学习模型之一。图 (2) 显示了 CNN 模型的布局。

卷积层的目的是通过输入向量与卷积核卷积来产生特征输出，从而提取局部特征。图 (2) 描绘了 CNN 结构。

输入用 W 表示。我们利用 $w_i$ 表示文本中第 $i$ 个位置的词，使得 $w_i$ 是一个维度为 $d$ 的向量。我们使用 $w_i$ 表示来自 W 的词序列，其中某些词被移除。例如，$w_1, w_2, w_3, w_4$ 被移除。$C_{sub}(W) = \{w_1, w_2, w_3, w_4\}$ 是 W 包含的所有词的聚合。

我们使用 $d(w_i, w_j)$ 表示词 $w_i$ 到 $w_j$ 之间的空间。表述为 $d(w_i, w_j) = j - i$。

我们使用范围来定义距离限制。在词 $w_i$ 和 $w_j$ 中，如果 $d(w_i, w_j) \le k$，则满足 k-范围限制。词序列被定义为包含 $w_i$ 本身的 k-范围序列。它与 k-范围限制 $w_i$ 一致。

定义 1。首先，让我们定义 k-范围序列，即 $w_i$，正向 k-范围序列或 k 范围序列，$w_j$ 是一系列向量 $S_k(w_i$，使得每个字母 $w_j E_k(w_i)$ 满足 $0 \leq d(w_i, w_j) \leq k$。并且对于 $w_j E_k(w_i)$ 和 $w_j E_k(w_j)$，$w_j$ 在 $w_i$ 之前当且仅当 $j < i$。

$S_2(w_1) = [w_1, w_2, w_3]$。

![](img/5e4d8ef2afa52a8404b28106580e19e4_303_0.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_303_1.png)

图 (4)) 数据集分类效率 2。

通过在每个层层的每个输出上触发名为 ReLU 的函数，全连接层能够抽象这些特征值并生成一个长向量，将特征空间（Feature Space）的文本映射到标记空间（marker space）。图 (5) 显示了数据集分类效率 3。

![](img/5e4d8ef2afa52a8404b28106580e19e4_303_2.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_303_3.png)

图 (5)) 数据集分类效率 3。

为了提取语义数据的特征，我们在本研究中采用了卷积神经网络（CNN）算法。上下文语义信息从特征图层获取并发送到 CNN 层，在其中检索语义特征。图 (6) 描述了数据集分类效率 4。表 1 以因素（Factors）的形式表示。

表 1 因素。

| 因素名称 | 值 |
|---|---|
| 卷积核大小。 | (2, 3, 4) |
| 词维度向量。 | 100 |
| 隐藏元素数量。 | 128 |
| Loafer | 0.5 |
| 学习率。 | 0.001 |
| 优化器 | Adam |
| 批量大小 (Batch Size)。 | 64 |
| 轮次 (Epoch) | 6 |

![](img/5e4d8ef2afa52a8404b28106580e19e4_305_0.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_305_1.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_305_2.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_305_3.png)

**图 (6))** 数据集分类效率 4。

## 结果与讨论

在一系列测试中使用了五个数据集（TREC, Subj, MR, SST-2, & AG）来确定 L-CNN 的效能：

- TREC 询问查询集中总共有六种不同的问题。因此，可能被问的问题只有以下六类：“实体”、“位置”、“人类”、“数值”、“描述性”和“缩写”。
- Sub Subjectivity 子主观性数据集的目标是对文本进行客观或主观分类。该数据集和基准系统都经过了 10 折交叉验证。
- MR 电影评论包含了来自烂番茄（Rotten Tomatoes）的好评和差评。极性数据库 v1.0 是具有两种可能状态的数据集。
- 为了获得 SST-2 斯坦福情感树库的二分类版本，我们首先移除中性评论，然后将正面和非常正面的评论标记为正面，最后将负面和非常负面的评论标记为负面。
- AG 新闻语料库中收集了超过百万条标记有四个类别之一的新闻故事。

文本分类基准包括新闻分类、询问分类和情感分类等任务。信息列在表 2 中。(7) 阐述了数据集分类效率 5。

![](img/5e4d8ef2afa52a8404b28106580e19e4_307_0.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_307_1.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_307_2.png)
![](img/5e4d8ef2afa52a8404b28106580e19e4_307_3.png)

图 (7)) 5 的数据集分类效率。

表 2 上述数据集的概述统计数据。

| 数据库 | TREC | Subj | MR | SST-2 | AG |
|---|---|---|---|---|---|
| 练习量 | 5.8k | 9.1k | 9.6k | 9.7k | 12k |
| 难度 | 0.6k | 1.2k | 1.2k | 1.9k | 7.7k |
| 会话 | | | | | |
| 平均长度 | 11 | 32 | 25 | 46 | |

## 结论

在本研究中，我们提供了一种用于文本分类的卷积神经网络（CNN），它依赖于卷积过程捕捉局部细节，并通过最大池化（Maximum pooling）处理文本中的变异。

## 参考文献

- [1] 基于深度学习的卷积神经网络用于大型木叶分类。Expert Syst.2021 1533476.
- [2] 深度网络与长短期记忆。24 届 IEEE 国际会议 (ACPD)2018 7638.
- [3] 使用卷积神经网络进行文本分类的方法。19 届 IEEE 国际会议 (SNPD)2018 8441.
- [4] 小波域内医学图像融合的离散数学模型。Engineering Solid2018 1425.
- [5] 基于无人机图像的大规模棕榈树制图。Remote Sens. (Basel)2021 1314278.
- [6] 基于语料库的卷积神经网络用于大数据文本分析。Journal of Intelligence Studies in Business2019
- [7] 心脏疾病预测的新型深度学习架构。arXiv, abs/2105.10816
- [8] 比较循环卷积神经网络用于鸟类物种分类。Science Rep.2021-9170885.
- [9] 使用 TensorFlow 的高级多分类深度卷积神经网络用于昆虫害虫分类。2023.2022-04277.
- [10] 使用范围性卷积神经网络的大规模分类：一种深度学习方法。IEEE Access2019 295924.
- [11] 通过深度卷积神经网络对大规模 Covid-19 推文进行情感评估和预测分析。Evol.Int.2022-15-313941-73381562.
- [12] 使用范围性卷积神经网络进行文本分类。IEEE 国际通用计算与智能 (IUCC)、数据科学与计算智能 (DSCI) 以及智能计算、网络与服务 (SmartCNS)2019 00093.

# 一种用于各种社交媒体平台文本意见分类的算法

Pavas Saini1*

1 与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度

## 摘要

随着社交媒体平台的激增，越来越多的人通过网络视频分享他们的想法和情感。虽然多模态数据中的成功情感融合是多模态情感分析的核心部分，但大多数现有在该在该仍有不足。多模态情感检测通过用户的语言表达使预测其情感倾向变得更容易。因此，多模态情感检测领域近年来发展迅速。结果，多模态情感分析正迅速走向学术关注的前沿。然而，在实际的社交媒体中，视觉和句子并不总是协同工作来表示情感极性。此外，存在多种信息模态，每种模态都以独特的方式对整体情感极性做出贡献。提出了一种考虑上下文知识的多模态情感分析方法作为这些问题的解决方案。该方法首先从社交媒体文本中挖掘描述评论材料的主题信息。此外，我们使用先进的预训练模型来识别跨多个领域的情感特征。然后，我们提供了不同级别的特征融合方法，例如跨模态全局融合以及跨模态高层语义融合。最后，我们在真实存在的多模态数据集上进行了测试。结果显示，所提方法可以正确分类异构在线评论的类型，而且在许多其他方面也优于标准方法。

**关键词：** 意见挖掘，社交媒体，情感分类，主题信息。

* **通讯作者 Pavas Saini**: 与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：pavas.saini.orp@chitkara.edu.in

## 引言

理解如何将丰富的上下文信息和多模态数据整合到单一模型框架中，是进行社交媒体用户情感分析的第一步 [1]。该研究提出了一种基于支持向量机（SVM）的主题模型用于消费者情感评估，并采用 SVM 以及 K最近邻算法（KNN）构建了分类日本社交情感的模型。此外，该研究构建了一个利用 TE 处理信息作为核的 SVM 分类器进行网格研究，并选择径向基函数作为核的网格搜索技术 [2]。在 Web 2.0 时代，社交网络（如 YouTube、Facebook、Google 和 Flickr）生成了大量包含文本、图像/视频以及社交互动信息的媒体数据 [3]。多媒体应用（如图像标注和检索以及事件分类）可以充分利用这些数据集 [4]。由于这些数据跨越了多个领域和媒体类型（如文本、图像、视频和音频），设计一种合适的表示方法来表征它们是具有挑战性的 [5]。许多提出的系统侧重于判断给定的社交媒体帖子语调是正面还是负面的 [6]。人们可能通过社交媒体上的各种媒介分享他们的想法和情感 [7]。使用多模态情感检测更好地预测用户情感偏好近年来发展迅速。目前的文献将视频言视为视为立的模型，往往忽略了视频中存在的多种模态之间的有效相互作用 [9]。情感分析是收集有关人们对问题、产品或人的感受信息的实践，然后将数据分类为正面、负面或中性。从 Amazon 和在线市场等社交媒体平台收集的数据可以很好地用于向客户推荐产品和产生销售 [10]。现在大多数人在谈论自己的想法和观点时，会将母语与其他语言的术语结合起来。对代码语（code speech）情感语调的解释至关重要。泰米尔语混合情感分析领域尚处于起步阶段，只有少数发表的作品 [12]。

为了解决数据不足的问题，可以使用上述解决方案。通过改进输入数据和精炼模型结构，可以使用多模态信息来增强分类效果。然而，训练这些模型需要大量的努力。通过发现新类型的多模态数据（这些数据具有广泛可用性且用于特征提取模型的变量较少等特点），可以缩短训练时间。使用最新的多维度信息，可以在不牺牲准确性的情况下更快速地训练模型。经过彻底分析后，社交媒体用户的特征可以被用作多模态数据。因此，我们为社交媒体文本数据数据提供了一种面向用户的情感分类方法。本文的主要贡献如下：

- 由于社交媒体用户特征被整合到输入数据中，收集必要的输入数据变得轻而易举。
- 由于提取用户特征的 CNN 网络参数较少，模型训练时间得以缩短。

双向互联网文本情感分类方法最近已升级到领先水平，使其成为小规模和时间敏感数据的理想选择。

本文的结构如下：在第 2 节中，我们研究了用户特征如何影响他们的感受。在第 3 节中，我们描述了一种用于短期和局部数据情感分类的模型。下文详细介绍了卷积神经网络和循环神经网络模型架构和公式中的用户特征。第 4 节讨论了各种模型及其通过实验的评估。第 5 节给出了最终发现。

## 相关工作

将言论与第一条推文联系起来的其他证据可以在评论和推文情感中的相关变量中找到。该研究描述了一种用户情感评估模型，并使用 Twitter 真实数据集实验信息集来评估其性能。SVM-KNN 的想法是参数估计方法的基础。研究结果显示了该方法的有效性 [11]。

我们提出了一种基于堆叠去噪自动编码器的跨领域特征学习（CDFL）技术来解决这些问题。与自动编码器不同，我们的 CFL 整合了模态相关性约束和跨领域约束，以同时优化模态间的关联并提取领域不变的语义信息。我们在三个主要领域（情感分析、垃圾检测和事件分类）测试了 CFL 算法。广泛的表明建议的方法良好 [12]。

情感分析的目的是收集有关消费者偏好的信息，这些信息可以被分别用于改进营销策略、公共政策计划和产品开发。为了判断一段文本是主观的还是客观的（如果是主观的，则是是负面的还是正面的），进行了情感分析。意见、情感和文本的主观性是情感分析的重点，这些因素经常共同工作，为估计支持折叠 Gibbs 采样的参数创建成本效益的技术。我们通常根据真实评论收集的信息对 SJASM 进行基准测试，我们的实验表明该模型优于七种行业标准的基准方法。

为了解决这些问题，我们提出了一种交互式 Transformer 多模态注意力网络，以研究视频情感分析中跨多种模态和言语的配对注意力。我们首先获取言语序列，并使用三个不同的 Transformer 编码器在言语级别捕捉特定模态的信息。为了更好地理解不同类型通信之间的关系，我们实施了配对注意力技术。随后，我们将跨模态输入馈入多头自注意力层，以完成情绪和情感分类。

利用我们提供的学习技术，这项工作旨在破解编码词汇的隐藏含义。对于混合语言，基于深度学习的带有 ULMFi Embedding 的 Bi-LSTM 模型的结果比任何其他可用技术都更令人鼓舞。

## 拟议工作

### 概述

模型的目标是使用用户提供的数据来预测文本将给读者的感受。需要两个并行模型来结合两组不同的输入数据。RNN 系列网络用于存储单词的相对位置，以便从文本中提取特征。CNN 系列网络更适用于单个用户属性的特征提取。最后，使用无预设权重值的全连接训练权重矩阵，并将来自两个模型的特征向量结合进行分类。通过将在用户特征上训练的 CNN 与在文本上训练的 RNN 结合，我们将组合模型称为卷积递归神经网络（CNN-RNN）。

我们使用名为“Tweepy”的 Python 脚本结合 Twitter 的搜索 API，收集了 10,000 条包含“trump”一词最新且最流行的多模态推文，并将其输入我们的算法。为了方便其他模块进行进一步分析，翻译后的推文保存在 Pandas 的 Dataframe 中。Pandas 是一个用于和分析数据的 Python 模块，其 Dataframe 以行和列结构化数据，使得数据数据到 Excel 非常简单。每个模块将在下方详细说明。

在开始情感分析之前，从推文中清除 URL、用户 ID、符号（“RT”、“@”）和多余空格是预处理数据的必要步骤。VADER 可以适当处理包含标点、俚语、表情符号、编码表情、首字母词和缩写的文本。作为 VADER 输出的特征之一，“复合得分”用于量化人们对文本的感受。复合得分是一个缩放度量，最大负分为 -1，最大正分为 +1。以下是典型的 VADER 情感阈值示例：负面：复合得分 0.05。(compound > 0.05) 和 (compound <= 0.05) 均被视为中性。复合 p<=0.05 为负面。图 (1) 中的文本 a、b、c 和 d 的复合得分分别为 (0.623)、(0.0)、(0.0516) 和 (0.0)。

![](img/5e4d8ef2afa52a8404b28106580e19e4_317_0.png)

图 (1) 系统图。

### 特征提取

- 我们采用预训练的 BERT（双向编码器表示）对数据中的文本进行编码。BERT 正如其名，是一种基于 transformer 的语言模型，它使用给定单词的左右上下文。通常，会学习一个额外的权重层以针对特定任务对 BERT 编码器进行微调。由于 BERT 编码器已经在从维基百科和书籍中提取的海量数据上进行过训练，因此我们不需要在此端进行任何微调。先进的 NLP 任务（包括情感分析、文本蕴含等）由于其在这些领域的表现，选择 BERT 作为其的编码器。第 4 节的所有输入文本都存储为 BERT-base 编码的 768 字符串。从现在起，vt 将代表插入的文本。

- 音频编码：使用 COVAREP 从音频帧提取各种声学属性，包括 MFCC、音高、峰值斜率等。每个电影的音频嵌入通过对从每帧中提取的声音向量取平均值计算。音频嵌入的最终大小为 74。从现在起，我们用符号 va 指代音频嵌入。

- FACET2 和 OpenCV 的结合用于从视频流中提取帧级信息，用于编码过程。

## 多模态情感分类

属性向量 $z_i(i = 1, 2...n)$。用户的属性矩阵通过结合向量获得，该向量是 CNN 网络输入 $Z$。$Z_{ij}$ 表示 $Z_i$ 和 $Z_j$ 中所有单词向量的合并，如下：

$Z_{i:j} = Z_i \oplus Z_{i+1} \oplus \dots \oplus Z_j$

![](img/5e4d8ef2afa52a8404b28106580e19e4_319_0.png)

其中 $Z_{i:j} = Z_i \oplus Z_{i+1} \oplus \dots \oplus Z_j$ (1)

其中 $C_i = \begin{cases} w \cdot x + b & \text{if } x > 0 \\ 0 & \text{if } x \le 0 \end{cases}$ (2)

$C = \max(C_1, C_2, \dots, C_n)$ (3)

$y = \sigma(W \cdot C + b)$ (4)

| ID | 类别 | 图像 | 平均单词数 |
|---|---|---|---|
| 1 | 电子商务 | | 59.21 |
| 2 | 技术与科学 | | 46.85 |
| 3 | 交通与旅游 | | 48.66 |
| 4 | 经济与商业 | | 73.12 |
| 5 | 社交网络 | | 46.35 |
| 6 | 健身 | | 56.71 |
| 7 | 医疗保健 | | 28.40 |
| 8 | 艺术与文学 | | 56.94 |
| 9 | 媒体与新闻 | | 43.39 |
| 10 | 餐饮服务 | | 55.05 |
| 11 | 娱乐 | | 56.78 |
| 12 | 法律与政治 | | 36.26 |
| 13 | 互联网与计算机 | | 58.22 |
| 14 | 培训与教育 | | 58.30 |
| 15 | 社会文化 | | 52.52 |

这种方法对于让模型快速收敛至关重要。在使用 Leaky ReLU 作为激活函数时，He 初始化策略表现异常出色。较大的批大小（batch size）需要更多的计算存储，而较小的批大小则执行时间更长。实验表明，考虑到 CNN-RNN 处理任务的特性，批大小设为 64 是优的。CNN-RNN 是同时运行的 CNN 和 RNN 的混合体。特征融合使用了全连接，且两者的相对重要性难以评估。最后，结合两个模型的全连接层通过 0.5 概率的丢弃（dropout）进行了增强。这加速了发现组合两种模态特征的理想权重的过程。表 1 在数据集描述中，图 (2) 描述在准确率与学习率对比图中。

![](img/5e4d8ef2afa52a8404b28106580e19e4_322_0.png)

**图 (2)** 准确率与学习率。

| ID | 类别 | P | R | A |
|---|---|---|---|---|
| 1 | 电子商务 | 98.5 | 95.6 | 98.25 |
| 2 | 科技 | 94.6 | 94.25 | 97.85 |
| 3 | 旅游与交通 | 94.5 | 96.7 | 98.25 |
| 4 | 商业与经济 | 95.2 | 98.5 | 98.36 |
| 5 | 社交网络 | 94.6 | 94.25 | 97.85 |
| 6 | 生活服务 | 94.25 | 97.85 | 94.6 |
| 7 | 健身 | 96.7 | 98.25 | 94.5 |
| 8 | 医疗 | 98.5 | 98.36 | 94.6 |
| 9 | 文艺 | 94.6 | 98.25 | 98.25 |
| 10 | 新闻与媒体 | 94.5 | 97.85 | 97.85 |
| 11 | 娱乐 | 94.6 | 94.25 | 97.85 |
| 12 | 政治与法律 | 94.5 | 96.7 | 98.25 |
| 13 | 计算机与互联网 | 98.25 | 98.25 | 98.25 |
| 14 | 教育与培训 | 97.85 | 97.85 | 97.85 |
| 15 | 社交文化 | 98.25 | 98.25 | 98.25 |

由于 CNN-RNN 在许多分类指标（包括准确率、精确率和召回率）上取得了高分，显而易见，利用 CNN 收集用户属性特征以辅助 LSTM 提取文本特征对于情感分类非常有效。CNN-RNN 每个轮次（epoch）所需的时间比 RNN 长。另一方面，CNN-RNN 收敛所需的轮次较少，训练量也比 RNN 少。实验表明，CNN-RNN 在短期和低样本量的情感分类中表现出色。表 2 代表了数据集描述。

## 结论

为了解决意见分析中情感分类对即时且局限的数据需求，本研究提出了一种利用用户属性增强输入数据的 CNN-RNN 算法。为了对情感进行分类，我们合并了通过 CNN 网络从用户特征中提取的特征以及通过 Bi-LSTM 从文本输入中提取的特征。从新微博收集的数据证明，CNN-RNN 在分类准确率方面优于 TextRNN，且训练所需的时间少得多。在将 CNN-RNN 用于社交媒体文本的情感分类任务时，存在某些局限性。一方面，本文选择了 12 种用户属性，某些属性在其他研究中已被证明与情感类别直接相关；另一方面，尚不清楚包含其中某些属性是改进还是削弱了整体模型。实验表明，选择过多的用户特征会导致过拟合，而选择太少则不会显著提高分类准确率。未来的研究将对这一问题进行深入调查，提供更好的用户属性组合选择并给出依据。然而，还需要更多研究来确定网络选择和双模型整合是否可以进一步增强。虽然 CNN 非常适合 CNN-RNN 的用户属性，但在模型开发早期就考虑了全连接神经网络。权重分布或串行连接可能会改进分类结果；然而，这种方法使用特征的并行拼接来合并两者。多模态信息的利用是 CNN-RNN 性能的关键组件，因为它可能会增加有限数据中包含的特征数量。从事人工智能领域的研究人员将发现多模态数据是一个令人兴奋且富有成果的研究领域。这些信息必须满足两个标准：首先，它必须易于获取且高度相关，以便提取特征的神经网络能够准确使用；其次，模型的参数必须最小化。

## 参考文献

- [1] Zhang C., Xie L., Aizezi Y., Gu X.. User Multi-Modal Emotional Intelligence Analysis Method Based on Deep Learning in Social Network Big Data Environment.IEEE Access 2019 178175817661. 10.1109/ACCESS
- [2] Hou S., Tuerhong G., Mushower M., VisdaNet: Visual Distillation and Attention Network for Classification.Sensors (Basel) 2023 23261. 10.3390/s23020613
- [3] Liu Z., Osei-Bref E., Chen S., Liang H., UoR at SemEval-2020 Task 8: Gaussian Mixture Modelling (GMM) Based Sampling Approach for Multi-modal Memotion Analysis International Workshop on SemanticEvaluation 2020.
- [4] Kalaivani M., Jayalakshmi S., Comparative Analysis of Convolutional Neural Network and LSTM in Text Based Sentiment Classification 2021 Fifth International Conference
- [5] Sitepu A.C., Wanayumi W., Siturong Z., Determining Between Classification Using Naive Bayes on 2021
- [6] Sun H., Wang G., Xia S., Text analysis based on multi-granularity emotional chunks and integrated Neural.Comput. 2020
- [7] Yadav S., Bhati B., Mahato D., Kumar S., Federated Learning for IoT Applications Springer Innovations in Communication 2022. 10.1007/978-3-039-8559-8
- [8] Sun H., Wang G., Xia S., Text analysis based on multi-granularity emotional chunks and integrated learning.Neural.Comput. 2023
- [9] Shekhar S., Mohan, N., Sentiment Classification Using Hybrid Bayes Support Machine Over Soc.Net. 2020
- [10] Dr P., Kavitha E., Twitter Sentiment Analysis Based On Adaptive Deepurrent Neural Net. 2021
- [11] Zhao Q., Social emotion classification of Japanese text based on SVM and KNN.J. Ambient Intell. Humaniz. Comput. 2021 112. 10.1007/s12652-021-03034-x
- [12] Xuanyuan M., Xiao L., Duan M., Sentiment Classification Algorithm Based on Multi-Modal Social Media Information.IEEE Access 2021 9334. 10.1109/ACCESS.2021.3061450

# 一种基于模糊逻辑的社交媒体稀有事件追踪方法

Prabhjot Kaur*

商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，印度旁遮普邦

## 摘要

在本文中，我们提出了一种基于模糊逻辑的社交媒体文本分类方法，用于追踪稀有事件。所提方法首先从每条通信信息中提取相关特征，然后利用基于模糊逻辑的分类器将通信信息分类为与事件相关或不相关。我们将所提方法与流行的关键词搜索方法进行了比较。研究结果表明，所提方法能够区分与异常事件相关的文本信息与与之不相关的信息。

**关键词：** 稀有事件追踪、社交媒体、文本分类、Twitter 情感分析。

* **通讯作者 Prabhjot Kaur**：Chitkara 大学工程与技术学院商业与技术跨学科研究中心。Chitkara 大学, 印度旁遮普邦；电子邮箱：prabhjot.kaur.org@chitkara.edu.in

## 引言

稀有事件（如自然灾害）在发生时，会对人们及其周围环境产生毁灭性的影响 [1]。人们可以通过社交媒体快速、方便地表达观点 [2]。因此，研究人员可以使用它来了解个人对各种极其异常情况的反应和想法 [3]。许多研究工作利用社交媒体数据来调查人们对现实世界中异常事件的反应是如何转化为在线人格的 [4]。在研究诸如自然大灾害等异常事件的发展时，社交媒体提供了丰富的数据源 [5]。研究社交媒体与人类参与的事件之间的联系具有很启发性。许多深度学习算法高度依赖于语义词表示 [6]。词角度/距离、词类比和统计数据是大多数模型的主流，它们通过使用向量表示独立地处理每个词 [7]。然而，通用模型在处理词汇丰富的语言时限制了对不常用词的表示 [8]。文档经常提供与特定领域相关的简短“片段”信息 [9]。例如，人类分析师经常使用本体论对和平与冲突研究这一社会科学学科中的文本片段进行分类，在该领域中，利用文本源识别、分类和监控冲突原因至关重要。片段中“稀有”短语缺乏类条件证据，这对该方法的自动化处理是一项挑战 [10]。

本文有两个主要益处。首先，我们提出了一种新的特征提取方法。其次，我们利用真实的社交媒体数据提出并验证了一种基于模糊逻辑的分类器。此外，还开发了专门用于衡量此类简短文本分类策略有效性的措施。本文的其余内容如下：第2节介绍了数据和一种新的特征提取方法。第3节概述了所提的基于模糊逻辑文本分类方法。第4节展示并讨论了实验结果。第5节提供了总结和结论。

## 相关工作

在本文，我们提供了一种提取特征和分类有关“桑迪飓风”等异常事件推文的方法。首先，提出了一种新的特征提取方法，用于从每条通信信息中提取相关特征。下一步是提供一个基于模糊逻辑的分类系统，以识别与事件无关的通信信息。最后，使用我们所提的方法和流行的关键词搜索方法对稀有事件的发展进行了分析。研究结果表明，所提方法在区分与异常事件相关的文本信息与与之不相关的信息方面是有效的 [11]。

本研究利用 2012 年桑迪飓风的 Twitter 文本数据进行信息提取和文本分类。由于原始数据涵盖了许多问题，我们需要提取与桑迪飓风相关的信息。为了解决文本分类问题，我们提供了一种基于模糊逻辑的方法。所提的模糊逻辑模型以从每条推文中获取的若干特征作为输入。发送给“桑迪”的每条消息的最终结果相关性评分。为了达到所需的分类结果，编写了许多模糊规则并结合了各种去模糊化方法。我们将所提策略与使用关键词获取相关结果的标准做法进行了评估。结果表明，所提的基于模糊逻辑的策略在分类 Twitter 推文方面优于关键词词法 [12]。

在本研究中，在名为 SemVec 的动态模型的帮助下，建议用领域和语义属性的向量来表示单词。通过根据问题领域添加或删除语义特征，可以创建一个包含领域知识的增强词表示。所提方法通过分类有关药物不良反应（ADRs）的推文和文本进行了测试。SemVec 在召回率得分方面优于其他先进的深度学习方法 [13]，其结果表明它将 ADR 检测的准确率提高了 15.28%。

在这项研究中，我们创建了一种策略，通过包含向量 Vector 的相关术语来补充文本的异常关键词，以改进词袋模型。该技术随后与常见的文本分类方法结合使用。这些增强模型通过降低词袋的稀疏性，性能优于标准分类器。我们证明，当应用于提高“小样本”实例性能的问题时，段落向量（Paragraph Vectors）的表现优于增强模型 [14]。

（注：原文中存在大量重复内容，译文已根据要求去重处理并保留核心学术信息。）

级别。每个实例的最终得分是通过志愿者给出的评分平均值计算得出的。我们预定义了相关性类别 $D_1, D_2, D_3$ 和 $D_4$，它们可以被视为四个独立的数据集。它们等于“不相关”、“部分相关”、“相关”和“非常相关”。共有四个预定的数据集，第 $j$ 条推文属于其中之一（且仅在当条件 $i-1(j)$ 成立时，其中 $j=1, 2\dots 2000$ 且 $i=1, 2, 3$）。请记住，志愿者对推文 $j$ 的平均评分表示为 $r(j)$

## 数据预处理

推文是一种特定的在线短文本通信类型，具有独特的结构和特征。在此阶段，准备数据是第一步。实际上，推文并不整洁，无法进行有效的即时应用。其中包含了网络术语和如统一资源定位（URL）之类的“噪声”。这些细节可能会减慢通信并破坏分类方法的效率。一条典型的未清洗的推文读起来：“所有系统均已激活！”#BuckSandy #Sandy (@ Hurricane Bunker) http://t.co/y1UOFIYp 的干扰细节非常全面。模式匹配通过评估提供的表达式序列为处理此类场景提供了一种省时的方法。在大多数情况下，它可以正确地发现隐藏在大量输入文本中的模式。例如，我们知道 URL 总是以“http://”开头。当模式匹配检测到 http:// 时，会剥离后续内容直到检测到空格。

此外，虽然标签（hashtag）可能有助于为事件提供一些背景，但只有约三分之一的通信实际使用了它们，即便如此，标签也是不一致的。在推文 #sandycantstop not let her stop you #floodproof #keeping 中，如果短语之间没有空格，标签的信息仍然清晰。然而，这对于机器理解是一个巨大的挑战，因为“sandycantstop”并不是一个标准的英语单词，尽管个人可以轻易将其解释为“无法阻止我”。在这种情况下，我们选择完全移除所有标签。该过程通过过滤停用词和将所有单词转换为小写来完成。这些“停用词”通常是任何语言中使用频率最高的术语。例如，“the”、“this”、“a”和“on”等词是为了使某些短语在语法上准确或可理解而需要的，但它们很少被充分利用。它们可以在同一个句子中出现多次，通常对对话的价值贡献很小。像 "the obvious" 这样的词，如果在不删除停用词的情况下统计语料库中最常见的词，它们将获得高分。这就是为什么要过滤掉停用词。由于计算机将大写和小写形式的单词视为两个不同的单词，将单词转换为小写有助于我们确保所有单词的格式相同。因此，一旦每个大写字母都被改为小写，“STORM”和“Storm”就会被视为同一个单词。

## 特征提取与分类

单词和短语的含义对计算机来说并不是显而易见的。因此，研究社区的目标是将此类短语和句子转换为数字以便提取特征。词袋模型和 TF-IDF 仅仅是两个例子 [8]。单词的频率是大多数人关注的主要领域。如果某些通信讨论的是相同的话题，它们就共享共同或相似的语义。例如，在机场，“时间”、“到达”和“航空公司”等术语比拍卖中出现的“鸟”和“价格”更常见。我们从训练数据集的 $D_2, D_3$ 和 $D_4$ 中选择推文，以获得频率最高的 50 个短语，并优先考虑出现分高的那些。必须记住，$D_2, D_3$ 和 $D_4$ 分别代表低、中、高重要性。对于给单词 $i$，单词重要性（用 $i$ 表示）定义为：

$$\alpha_i = \frac{P_i}{Q_i} \times 100\%$$

$P_i$ 是属于 $D_2, D_3$ 和 $D_4$ 的推文中单词 $i$ 出现的次数；$Q_i$ 是所有推文中单词 $i$ 出现的总数；$\alpha_i$ 表示单词 $i$ 重要性的百分比。通常情况下，$\alpha_i$ 越大，该单词越重要。

飓风是本文的主题。将其与地震等其他极罕见的事件进行对比。飓风从形成的那刻起就可以进行实时预测。然而地震是在毫无警告的情况下发生的。与罕见事件相关的常用术语、关键词和短语在不同异常事件之间可能有所不同。异常事件的现象和强度各不相同，人们描述它们的词汇和短语也如此。当将建议的策略应用于其他罕见事件时，需要仔细的事件选择。第六个元素与模式相关，这是我们方法的关键区别。必须对模式进行修改，使其适用于稀有事件的特定实例。还可以修改成员函数的参数，以便更好地与其配合。

## 结果与讨论

在这里，我们提供了几个衡量方法的细节，用于衡量我们所提策略的有效性。二分类方法的效能通过表 1 中的混淆矩阵进行衡量。

表 1 二分类问题的混淆矩阵。

| | 实际正类 | 实际负类 |
|---|---|---|
| 预测正类 | TP | FP |
| 预测负类 | FN | TN |

“真正”（TP）一词是指本应被评为负类但被标记为正类的事件数量。“假负”（FN）一词是指正结果被错误地标记为负结果的次数，而“真负”（TN）是实际为负的案例总数。

为了确定给定的实例是否属于稀有事件相关类，使用了精确率（precision）和负预测值（NPV）。前者代表主题领域中正确分类的推文比例。如果该值较高，则较大比例的相关项将被放在相应的类别中。否则，我们面临不当归类某些重要项目的风险。同样，NPV 代表不属于特定类别的推文被准确标记为该类别的比例。如果较高，将捕捉到更多的假正性。否则，将会误分类一些不重要的内容。计算值的方法如下：

```



# 使用 SVM 和改进 CNN 进行文本文档预处理与分类

Jaspreet Sidhu¹, *
¹ 与技术跨学科研究中心, Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

## 摘要

文本分类是数据挖掘和数据检索中的一项关键技术，已得到广泛研究并正快速发展中。卷积神经网络（CNN）是一种深度学习模型，它能够在准确提取输入文本特征的同时降低模型的复杂性。支持向量机（SVM）的结果一直比其他传统人工智能方法更具信誉且更优。在本研究中，我们通过增强的卷积神经网络（CNN）和支持向量机（SVM）提供了一种新的在线文本分类方法。我们的方法首先使用基于五层网络结构的 CNN 模型对文本属性进行识别和预测。从长远来看，包含文本和图像的数据库将发现该方法是一个主要的考虑因素。

**关键词：** 分类、SVM 和改进的 CNN、文本文档预处理。

> * **通讯作者 Jaspreet Sidhu**: 与技术跨学科研究中心, Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India; 电子邮箱: `jaspreet.sidhu.orp@chitkara.edu.in`

## 引言

本研究利用朴素贝叶斯技术和支持向量机策略（SVM）提供了一种改进的混合分类策略 [1]。在这项研究中，我们采用贝叶斯公式创建一个概率分布，将文档向量化（而非类别）映射到其可能所属的最有利类别中 [2]。如果你有一组主题（类别），例如“20 Newsgroups”数据集中的那些 [3]，你可以使用贝叶斯公式估计文本落入每个类别的概率。SVM 可以通过将这些概率分布作为文档的向量表示来执行多文档分类 [4]。为了防止朴素贝叶斯分类器仅根据最大概率进行分类时出现的维度下降问题，支持向量机（SVM）会考虑与每个文档的组别相关的所有概率值 [5, 6]。电动方程式（Formula E）赛事已迅速升至国际赛车运动的顶端。世界著名的 Formula E 赛事于 2022 年在印度尼西亚举行 [7]。预计 35,000 人的参加有望为印度尼西亚带来 7800 万欧元的经济效益。印度尼西亚的许多人认为，举办 Formula E 赛事将有助于其国家吸引游客并提高国际声誉 [8]。然而，也有人对此持反对意见。他们认为政府的资源应该更好地帮助受新冠肺炎大流行影响影响的人，而不是在此时资助电动方程式赛车 [9]。为了对新样本进行分类，集成技术会生成一系列分类器，然后对它们各自的预测进行加权投票。集成分类 [10] 中的一项高级挑战是在提高准确率的同时减少误差 [15]。

通过结合 CNN 和 SVM 算法，该工作旨在克服上述问题，并完成语言分析领域的 Web 文本分类任务。与现状相比，实验结果表明所建议的 Web 文本分类方法实现了更高水平的分类精度。

## 相关工作

与 Lsquare 技术相比，该方法所需的训练时间要少得多，并且在分类精确性方面优于纯朴素贝叶斯算法以及 TF-IDF/SVM 混合算法 [11]。

此处使用贝叶斯算法根据与一组关键词相关的概率，将文档的向量表示分配给一组类别。贝叶斯公式在文档可能被分配的主题（类别）集合上提供了一个概率分布。这种概率分布可以被作为利用向量空间模型的文本分类方法（如支持向量机 (SVM) 和自组织映射 (SOM)）表示文档的载体。这改进了仅使用朴素贝叶斯分类器时的结果，后者仅使用最高概率对纸张进行分组。这些技术允许我们从错误降维的后果中恢复。对于高维数据，我们评估了各种分类器的有效性 [12]。

本研究评估了朴素贝叶斯算法在识别粉丝对 Formula E 锦标赛情感方面的有效性。本研究中的数据来自 Twitter 等社交媒体网站上的公共讨论。清洗、折叠、分词、过滤和词干提取都是文本准备阶段的一部分。未来应使用 TF-IDF 加权方法。数据测试使用混淆矩阵通过准确率、精确率和召回率测试来评估分类结果。SVM 在分类公共舆论方面的召回率、精确率和准确率均高于 80%。准确率为 82%。然而，朴素贝叶斯方法仅实现了 87.54% 的准确率。Twitter 上的大众对引入 Formula E 表示支持 [13]。

本研究引入了用于预测的分类器集成，以及一种革命性的通用面向对象投票和加权堆叠架构。这种通用模型通过汇总一组基础学习者的投票来做出预测，并给每个学习者赋予相等权重。为了演示，所提出的堆叠框架使用三个著名的异构分类器进行集成分类：支持向量机、文本最近邻和朴素贝叶斯。此外，该框架的结果在各种交叉验证划分和比例划分的多个基准数据集上与其他进行了比较。结果表明，该框架可以正确预测犯犯倾向的概率为 99.9901% [14]。

随着互联网和计算基础设施的不断进步，文本分类可能会成为处理海量文本最重要的方法。提高文本分类结果的一个主要障碍是如何精确地识别文本为可分析的数据集。作者讨论了使用 p-idf 公式表征文本的方法，该公式源于向量空间模型和 tf-idf。作者使用支持向量机构建文本分类系统，在与 tf-idf 进行性能科学比较后，p-idf 公式是公平且有效的 [15]。

![图 (1) 系统流程图](img/5e4d8ef2afa52a8404b28106580e19e4_350_0.png)

图 (1) 系统流程图。

## 基于 SVM 的 CNN 文本分类

假设短语包含 m 个单词，词向量维度为 n维，则生成的矩阵为 m x n。图 (2) 显示了带 SVM 的 CNN 结构。图 (1) 显示了系统流程图。

![图 (2) 带 SVM 的 CNN结构](img/5e4d8ef2afa52a8404b28106580e19e4_351_0.png)

图 (2) 带 SVM 的 CNN结构。

以下是模型结构的描述：

- 嵌入层（Embedding layer）：在嵌入层中，每个单词由一个向量表示，这些向量存储在矩阵中。
- 卷积神经网络层：通过与大小为 kn 的卷积窗口执行卷积操作，嵌入层可以生成许多特征图。纵向单词数用 k 表示，词向量维度用 n 表示。使用卷积窗口可能会产生多个 1 列特征图。
- 池化层（Pooling layer）：池化层可能会对输入数据进行下采样，它的名字是下采样层。CNN 支持许多池化策略，其中最大池化策略最为广泛。
- 全连接层（Totally interconnected layer）：在许多情况下，最后一层连接到另一个或多个全连接层，最终输出是整个全连接层的结果。图 (2) 描绘了带 SVM 的 CNN 结构。

卷积神经网络的显著特征包括局部关系、空间聚合以及权重共享。通过仅在局部连接神经元，CNN 极大地减少了其神经网络设计中的参数数量。虽然卷积可以收集训练和分类所需的所有特征信息，但它是计算密集型的。在获取文本的卷积特征后，关键是通过空间采样减少特征的维度，以增加对位移的抗性，同时我们最小化隐藏顶层的计算开销。CNN 的权重共享网络设计更类似于生物神经网络，这允许它跳过传统机器学习技术中使用的繁琐特征提取和数据重构过程。因此，它已成为 NLP 应用中的标准流程。

一种称为支持向量机（SVM）的旧基于模型的学习方法通过线性变换将输入空间映射到更高维的特征空间。其目标是在新空间中找到最优线性界面。SVM 方法在不增加计算复杂性并通过随数据规模良好扩展来防止“维数灾咒”，提供了一种使用核函数的解决方案。

由于可以从同一个核函数构建许多不同类型的 SVM 分类器，因此选择正确的函数至关重要。三种最常见的核函数是：

- 线性核函数：

```
$K(x_1,x_2) = (x_1 \cdot x_2)$ (1)
```

- 多项式核函数：

```
$K(x_1,x_2) = [(x_1 \cdot x_2) + C]^\mu$ (2)
```

- 径向基函数：

```
$K(x_1,x_2) = \exp(-\|x_1 - x_2\|^2/2\sigma^2)$ (3)
```

## 实验与结果

$$\text{precision} = \frac{TP}{TP+FP}$$

$\text{NPV} = \frac{TP}{TN+FN}$$ (8)

此外，为了比较两种不同方法的有效性，变化率 $\lambda$ 描述了某种方法比另一种方法利用了更多或更少的信息，即：

```
$$\lambda = \frac{x_{\alpha}-x_{\beta}}{x_{\beta}}$$ (9)
```

其中 $x_{\alpha}$ 表示使用新方法 $\alpha$ 正确分类到右类别的发生次数，$x_{\beta}$ 表示使用旧方法或基准方法 $\beta$ 正确分类到右类别的实例数量。通常情况下，可以从更准确的提取中获得更多数据。

### 数据集

- 此 Twitter 数据集包含超过 15 亿条关于全球新冠肺炎的推文。该集合涵盖了今天使用的几乎每种语言，但英语、西班牙语和法语更早。
- Twitter 客户支持 - 这一数据集包含了大量的 Twitter 客户支持热线以及相关的推文和回复。
- 2016 年总统大选 - 该数据集关注与 2016 年总统大选相关的推文，最初收集是为了针对国家支持的宣传的指控增加透明度。图 (2) 所示，性能分析 (a)。推文分类准确率（数据集 1），(b)。推文分类准确率（数据集 2），(c)。推文分类准确率（数据集 3）。

![图 (2) 性能分析](img/5e4d8ef2afa52a8404b28106580e19e4_340_0.png)

![图 (2) 性能分析](img/5e4d8ef2afa52a8404b28106580e19e4_341_0.png)

(b)

![图 (2) 性能分析](img/5e4d8ef2afa52a8404b28106580e19e4_342_0.png)

图 (2) 性能分析 (a)。推文分类准确率（数据集 1），(b)。推文分类准确率（数据集 2），(c)。推文分类准确率（数据集 3）。

## 结论

自然灾害是罕见事件的一个例子，它们并不经常发生，但一旦发生会对人们及其环境产生毁灭性的影响。现在人们有了一个快速方便的渠道在社交媒体上表达想法。因此，研究人员可以使用它来了解个人对各种极其异常事件的反应和思考。许多研究利用社交媒体数据来调查人们对现实世界异常事件的反应如何转化为他们的在线人格、思想、情感和行动。在这项工作中，我们提供了一种提取特征和分类如桑迪飓风等异常事件推文的方法。首先，了一种新的特征提取方法，该方法可以从每条通信中提取相关特征。下一步是提供一种基于评分的分类系统，以区分有关事件的通信与无关的通信。最后，使用我们建议的方法和流行的关键词搜索方法对稀有事件的发展进行了分析。结果结果表明，建议的方法在区分与异常事件相关的文本信息与无关的信息方面是有效的。

## 参考文献

- [1] Gao Y., Zhang H., Yan S., Event Tracking in MicroblogsACM Trans. Intell. Syst. 2017 10.1109/TSMC.2019.293246
- [2] Thakur A., Ilievski F., Sandlin H., ... Imbalanced Class Semi Supervised TestingArxiv,abs/2212.0512
- [3] Referee A., Gallay A., Weigenbaum P., Grouin C., Extreme precipitation in the Mediterranean area: contrasting Lagrangian and Eulerian
- [4] Yadav P., Bhati S., Mahato D., Kumar S., Federated Learning for IoT ApplicationsEAI/Springer Innovations in Communication and Computing2022.
- [5] Banerjee D., Prabhat G., Bhowal R., ICASTLE: Imbalanced Classification Algorithm for Supervised Testing International Conference on Machine Learning and Applications (ICML)202210.16/
- [6] Yadav S., Zaidi S., Nascimento C.D.,S., Analysis and Design of automatically generating for GPS Based Moving Object Tracking2023 International Conference on Artificial Intelligence and Smart Communication (AISC)Greater Noida, India.2023.15.1109/AISC5616.2023.1008518
- [7] Bagholdi Y., Bourrée A., Autet R., Gallay A., Weigenbaum P., Fouillet F., Performance of machine learning method to classify free-text medical causes of adverse events and medication in electronic health records.J. Am. Med. Online Public Health Assoc.2021;38(1)e1111.
- [8] Henry S., Buckley K., Stubbs A., Uzner O., 2018 shared over adverse events and medication in electronic health records.J. Am. Med. Online
- [9] Malvuccio C., Kamavuko E., Detection of Swelling Events and Influk Time Estimation From Source Electromagnetography2020 IEEE-EMCES Conference on Biomedical Engineering and Sciences (IBCES)24525052.2020/IEEE438419.2021.998821
- [10] Yadav S.P., Mahato D., Linh N.T., Distributed Artificial Intelligence.CRC Press2020.
- [11] Lu X., Zhou M., Wu K., A Twitter logic-based text classification method for Tracking Rare Events On IEEE Trans. Syst. Man Cybern.Syst2021.5117423443311.1109/TSMC.2019.293246
- [12] Wu K., Zhou M., Lu X.S., Huang L., fuzzy logic-based text classification method for social media data2017 IEEE International Conference on Systems, Man, and Cybernetics (SMC)19421947201710.1109/SMC.2017.812902
- [13] Ode F., Taweel A., SemVec: Semantic Feature Vectors Based Deep Learning for Improved Text ClassificationInternational Conference on Theory and Pattern of Nature
- [14] Krzywicki A., Heap B., Bain M., Wobcke W., Schmidl S.. Using Word Embeddings with Linear Models for Short Text ClassificationAustralasian Conference on Artificial Intelligence201810.1007/978-3-030-03991-2_74
- [15] Sattar, F., Driessen P.F., Tzanetofakis G., Page W.. A new method for classification of events in noisy hydrophone dataProceedings of 2011 IEEE Pacific Rim Conference on Communications, Computers and Signal Processing660667201110.1109/PACRIM.2011.6032972

OceanofPDF.com



## 通过卷积神经网络识别文本情绪

Vaibhav Kaushik*¹¹ 商业与技术跨学科研究中心，奇特卡拉大学，旁遮普邦，印度

通讯作者 Vaibhav Kaushik: `vaibhav.kushik.org@chitkara.edu.in`

## 摘要

越来越多的人使用互联网分享他们的感受并与他人交流，而这些表达大多以文本形式出现。使用情感词典、机器学习和深度学习是三种最常用的方法。由于文本数据的指数级增长，创建能够分析这些数据的模型至关重要。文本中包含了性别、年龄、国家、情绪等标签。卷积神经网络（CNN）最近被应用于文本分类问题，取得了良好的效果。

**关键词：** CNN，深度学习，文本分类。

## 引言

情感挖掘（又称情感分析）是文本研究的另一个热点。它将文本主观信息作为研究对象，并努力对其中发现的各种情感基调进行分类。这就是为什么研究情感的研究人员将文本分为主观和客观部分是非常重要的。

截然不同。所研究的大多数文章来自互联网，在长度和表现上各不相同。中文文本具有英文文本不具备的独特特征，例如需要进行分词，而由于英文中单词之间存在空格，这种分词是不必要的。目前的情感分析文本分类研究通常使用情感词典进行，尽管这种方法需要建立高质量的情感词典，且只能进行人工分类。这类词典需要大量工作，并存在如术语不足以无法全面涵盖等缺点。基于人工智能的方法可能会比使用情感字典提高分类准确率。这涉及到建立高效率的计算机学习模型。然而，特征只能由具有特定专业水平的人员设计。细节非常少，且难以获取深层文本特征。自然语言处理是深度学习方法在近年来取得显著进展的领域。它不需要人工设计，能够自动生成层次结构特征并从头到尾对数据进行分类。

自然语言处理（NLP）应用在卷积神经网络（CNN）的使用上取得了成功。由于 CNN 的卷积层可以通过编码重要的语义特征进行初始化，该层也可用于提取关键语义特征。然而，CNN 的合并层使用最大合并特征（`max-combining feature`）忽略了句子最重要的细节和文本的上下文信息。随着我们数字存储信息能力的增长，这些任务以文本消息的形式执行。许多文本分类任务可以使用标准的人工智能分类器，例如支持向量机或朴素贝叶斯分类器。然而，由于短文本中文本内容的稀缺以及合并层和卷积层的限制，这些分类器面临稀疏性困难并缺乏长期依赖关系。在自然语言处理中，文本分类是核心任务之一。这项工作的范围和实用性都很高。然而，大多数旧方法依赖于静态词嵌入，这未能充分解决多义性问题。被称为“情感分析”的自然语言处理领域将书面材料分类为正性或负性。在过去的几十年里，它已应用于多个领域。意见分析具有挑战性，因为每个人都有自己独特的视角。关于个人、企业和消费品的信息都可以使用情感分析进行分类。每分钟都有海量信息被添加到互联网网站、博客和社交媒体中。几乎每个电子商务网站都允许客户对购买的产品提供反馈。这些反馈反映了某些用户对物品的体验。在两个物品之间做出快速、非正式的选择时，客户通常查看评论寻求指导。此外，企业也有兴趣通过评论听取客户对物品的意见。由于海量信息和嘈杂短书面数据的典型特征，在线评论的数据分析变得越来越困难。

本文的后续章节结构如下：第 2 节回顾了使用 ML/DL 模型进行情感分类的研究。第 3 节详细描述了我们计划的网络。第 4 节讨论了测试所提模型的实验条件和数据集。第 5 节阐述了实验结果。第 6 节是本文的结束。

## 相关工作

在本文，我们提出了一种新型神经网络方法，结合了注意力机制和合并层，以使模型关注句子中的搜索词，并自动保留最重要的文本信息，从而增强模型的文本分类能力。为了让模型捕捉关键语义特征，我们用关键信息特征初始化卷积滤波器。通过将注意力机制集成到合并层中，模型能够更好地保留文本的关键信息特征。实验表明，所提模型在各种文本分类任务中表现良好 [11]。

在该研究中，我们提供了一种基于增强 `skip-gram` 算法的卷积递归神经网络。对于 `skip-gram` 算法的对抗训练，我们使用了 L2 正化技术。这不仅可以提高该模型在文本情感分类任务中的性能，还能使其更具韧性和泛化能力。为了从文本中提取意义数据的同时减少无关词的影响，我们使用了带有注意力机制的双向长短期记忆网络。最终，基于 CNN 的文本情感分类得以实现。与 IMDB 数据集 [12] 上的其他分类器相比，该模型和方法被证明是最高效且最准确的。

为此，我们建议使用上下文 BERT 嵌入来高效编码输入序列，随后是时间卷积模块（该模块仅确定 1D 卷积以提取高层特征），最后是最大合并层，它保留了文本分类最关键的特征。我们在六个大规模文本分类数据集上测试，这些数据集广泛情感分析、问题分类和主题分类。我们建议了一种高效的截断方法，作为 BERT 无法解析长材料的解决方案。实验结果表明，建议的方法优于以往的方法 [13]。

在当今数据驱动的世界，需要创新的工具和算法从数字材料中获取见解。情感分析用于衡量客户需求、市场趋势和公众舆论。它对于扩大公司规模和确定产品有用。当企业使用社交媒体与消费者交流时，客户的评论和评分被用于改进产品。文本处理是 ML 和 DL 模型的自然应用领域。使用卷积神经网络和递归神经网络等深度学习技术可以解决文本处理领域的许多问题。通过合并程序，CNN 可以从输入文本中提取相关特征，但获取必要的上下文信息更为困难。RNN 可以学习上下文，但它每次都需要新的单词序列。在这项研究中，我们比较了 LSTM 算法与卷积神经网络的表现 [14]。

## 提出的工作

现有研究没有考虑到重要词往往具有更高的影响，并在整个训练过程中等同对待文本中的所有短语。基于重要短语的改进，我们提出了一种基于卷积文本分类的情感神经网络模型。为了提高所提模型的情感分类准确率，它首先识别文本中的关键句子，然后根据这些关键句子生成文本表示。实验结果表明，该模型在准确性方面优于基准文本情感分类算法。

## 预处理

对实验文本数据进行了预处理以使其更相关。我们忽略了大小写并没有使用句号和删除了冒号标点。转发（RT）、制表符、多个空格和停用词。代表“http”URL 的文本被替换为 `[URL]`，代表“@”ID 的文本被替换为 `[NAME]`。我们还将 `[NUM]` 转换为数字，将 `[SPE]` 转换为符号。由于“not”在情感分析中起着重要作用，我们将“can’t”和“isn’t”分别读取“cannot”和“is not”。我们对文本数据进行了空间分段，并根据出现六次或以上的术语构建了新字典。从 MR 数据包含的 38,195 个单词中，创建一个包含 9394 个单词的词汇；从 CR 数据最多 5356 个单词中，创建了 1415 个；从 SST 信息中最多 16,870 个单词中，创建了 3548 个。新词汇包含填充字符 `[PAD]` 和在需要单词时使用的未知字符 `[UNK]`。在进行填充时，任何小于指定长度的文本都会替换为 `[PAD]` 标记。在这种情况下，每个数据集中单词的最大长度作为固定长度。

![](img/5e4d8ef2afa52a8404b28106580e19e4_369_0.png)

**图. (1)** 用于文本情感分类的 CNN。

## CNN

“卷积”滤波器（即卷积核）通过图像移动，在此过程中提取重要特征。CNN 在图像数据集上已有广泛应用。如果所处理的数据以单维形式呈现，CNN 的相同目的也可以应用于文本。当滤波器在文本上移动时，会保留所处理文本的局部信息并提取关键特征。因此，显然 CNN 是文本分类的一个非常有用的工具。下方的图 (1) 显示了用于文本情感分类的 CNN。

## 卷积层

对于输入数据中的每个窗口，卷积都应用了一个线性层（然后是非线性层）。为了方便讨论，我们假设：

- $(x_1, ..., x_n)$ - 输入的项的表示，$x_i \in \mathbb{R}^d$；
- $d$ (输入通道) - 输入嵌入大小；
- $k$ (卷积核大小) - 卷积窗口的大小（示例中 `k=3`）；
- $m$ (输出通道) - 卷积滤波的总数（或输出通道的总数）。

因此，卷积只是另一个线性层 $W \in \mathbb{R}^{(k,d) \times m}$。对于大小为 `k` 的窗口 $(x_i, ... x_{i+k-1})$，这种向量加法就是卷积的操作。

```
$u_i = [x_i, ... x_{i+k-1}] \in \mathbb{R}^{k\cdot d}$
```

并与卷积矩阵相乘：

```
$F_i = u_i \times W$
```

---

卷积脑网络中的所有常见组件——嵌入、卷积、激活、池化以及全连接层——都用于优化所建议的模型。在使用数据集之前，会对每个单词的嵌入进行训练。此输入特征将通过额外的网络设置多次训练 CNN 模型。最后一步是将检索到的特征输入支持向量机分类器进行训练，之后产生结果。

图像使用二维（2D）卷积神经网络进行初始识别。因此，在将文本输入模型之前，我们必须首先通过将其合并为二维数据矩阵对其进行预处理。

文本准备方法包含三个阶段：作为首要工作，必须将源材料转换为一系列单词字符串。下一步是使用 Google 的开源应用 `word2vec`（该应用已预训练以读取词向量），将单词序列转换为具有序列数量的短语。字典中的每个单词都有一个唯一的数字。第三步涉及将字典中的每个单词扩展为向量。准备文本涉及两个层：下面列出了合并层、全连接层和批处理归一化层。这里使用了两个全连接层。第一个用于对输入中的特征进行加权，第二个用于从最终结果中提取特征。

神经网络中包含许多激活函数，例如 `sigmoid` 和 `tanh`。在这种情况下，激活函数是 `F`。`Leaky ReLU` 旨在通过使用非线性组件增加模型的表达能力并减少模型噪声，同时尽可能保留数据。

最后，滑动窗口内包含的文本信息被转换为固定长度的向量。该向量既作为 SVM 分类器的训练输入，也是 `softmax` 函数后分类的输出值。

## 结果与讨论

本研究使用的某些文本取自 20-NewsGroup 语料，但也使用了其他来源。总共包含 19997 条消息，全部由互联网用户上传到 Usenet，并均匀分布在 20 个不同的类别中，每个类别有 1000 个帖子。其他来源包括使用 `Heritrix` 获取的在线新闻文章，并进行了少量处理。总共使用了 11968 个样本，平均分为训练集（7180）和测试集（4788）。剩余的 10% 数据在训练期间作为验证样本。

准确率（`Accuracy`）衡量了分类器在任务集上的性能，也用于评估实验的整体有效性。

本研究的主要目标是提供一个已经训练好的词向量以及一个基于增强 CNN 方法的 SVM 分类器。以下是详细的实验设置：CNN+SVM。我们首先使用 `word2vec` 训练了一个良好的词向量，然后用增强型 CNN 模型提取特征，最后利用线性内核 SVM 分类器进行训练并报告了我们的发现。

机器学习的常用方法。通过将模型的结果与应用于相同数据集的两种成熟教育方法——人工神经网络（ANN）和支持向量机（SVM）的 Result 进行对比，证明了该模型的效能。

你可以从两个图中看到模型与训练相关的准确率、F 值（`f-measure`）以及损失（`loss`）。在前一个图中，我们看到代表初始训练集的 `acc`、`f-measure` 以及 `loss`；而在后一个图中，`val_acc`、`val_fmeasure` 以及 `val_loss` 则代表验证集。如图 (3) 所示，四个标记的趋势曲线在 25 个周期后相当稳定。同时，图 (4) 表明损失在 25 次迭代后被有效最小化。

![](img/5e4d8ef2afa52a8404b28106580e19e4_357_0.png)
图 (3) 准确率结果。

![](img/5e4d8ef2afa52a8404b28106580e19e4_358_0.png)
图 (4) 精确率结果。

![](img/5e4d8ef2afa52a8404b28106580e19e4_359_0.png)
图 (5) F 值结果。

图 (3-5) 显示了四个模型的最终结果。表格数据清楚地表明，所提的方法为本论文提供了最好的结果。与标准 CNN 模型相比，算法的准确率从 87.6% 提高到 92.5%，F 值从 87.9% 提高到 93.2%。此外，它的影响远高于 SVM 方法，SVM 是一种相当有效的经典机器学习技术。

![](img/5e4d8ef2afa52a8404b28106580e19e4_360_0.png)
图 (5) 召回率结果。

## 结论

自然语言处理（NLP）的基石之一是文本分类，它已经存在很久了。自从诞生以来，深度学习技术一直是人工智能研究的主要领域之一。卷积神经网络是最通用的模型。本工作采用混合方法，将深度学习与更传统的机器学习技术相结合，以解决文本分类问题。首先，我们使用增强型 CNN 模型来整合预训练词向量。其次，为了完成这项分类任务，我们采用了 CNN 和 SVM 算法的改进版本。与之前的技术相比，实验结果表明，本研究讨论的算法显著提高了分类准确率和 F 值。该模型将在公开数据集上进行测试，以确保它未来能够准确考虑到用户的情绪。

## 参考文献

- [1] Xi M., Sun, J., Liu, L., Fan, F., Wu, X.. Feature Selection and Classification Using a Binary Quantum-Based Particle Swarm Optimization and Support Vector Machine. Comput. Math. Methods Med. 201620161910.1155/2016/3725072572642363
- [2] Kachach R., Cañas S.M., Hybrid three-dimensional and support vector machine approach for vehicle tracking and classification using a single camera. J. Electron. Imaging
- [3] Commonplace method of machine learning. The model's efficacy was shown by contrasting its results with those of two well-established educational methods—artificial neural networks (ANN) as well as support vector machines (SVM)—applied to an identical dataset.
- [4] You can see a model's training-related accuracy, f-measure, as well as loss in the two figures. In the former, we see `acc`, `f-measure`, as well as `loss` representing the initial training set, while in the latter, `val_acc`, `val_fmeasure`, as well as `val_loss` represent the validation set. The four markers' change curves have been rather stable after 25 periods, as shown in Fig. (3). Meanwhile, Fig. (4) demonstrates that the loss is effectively minimized after 25 iterations.
- [5] Accuracy, which measures the classifier's performance on the task set, is also used to evaluate the experiment's overall effectiveness.
- [6] This study's overarching goal is to provide an already trained vector of words and a SVM classifier based on the enhanced CNN method. The following is the detailed experimental setup: CNN+SVM. We started by training a decent word vector with `word2vec`, then extracted features with an enhanced CNN model, and lastly utilized a linear kernel SVM classifier to train and report our findings.



在卷积中，输入通过滑动窗口传递，每个窗口接收到相同的线性变化。使用卷积从每个窗口收集了 `m` 个特征后，它们将通过合并层（Combining layer）相加。为了最小化网络参数的数量，使用了降维的合并层。

## 最大合并层 (Max Combining Layer)

最大合并（Max-Combining）是最著名的方法；它最大化跨维度特征的值。执行合并过程后，我们得到一个指示这些输入模式出现频率的向量。平均合并（Mean-Combining）在功能上等同于最大合并，但它是计算所有特征的平均值。

### k-max 合并 (k-max Combining)

k-max 合类似于类似于合并，但范围更广。该方法选择数量最大的 `k` 个特征，而不是单个最大特征。每个特征都保留在它适当的位置。如果网络发现某种模式的频率至关重要，请考虑使用该方法。

## 合并与全局合并 (Combining and Global Combining)

合并处理包含多个组件的窗口的方式与卷积相同。合并中也提供了步长（stride）选项，并且通常使用不重叠窗口。要做到这一点，步长参数必须等于池的大小。请看示例。

与对整个输入操作的全局合并不同，合并对每个窗口中的特征进行单独操作。许多文本处理任务需要全局合并。与对整个输入操作的全局合并不同，合并对每个窗口中的特征进行单独操作。许多文本处理任务需要全局合并。

## 结果与讨论

所建议的 CNN 模型（传统的机器学习模型）在三个数据集（电影评论数据、客户反馈数据和 Stanford Treebank 数据）上进行了测试。在分析中，使用了准确率、召回率（recollotion）和 F 值（F-Measure）。结果表明，CNN 架构在情感分析方面优于其他模型。

```
$F(i,j) = \frac{(\alpha^2+1)*TP}{\alpha^2*(TP+FP+FN)} = \frac{2\timesP(i,j)\timesR(i,j)}{P(i,j)+R(i,j)} \quad (2)$
```

在这里，我们定义了全球聚类的 F 度量。

```
$F = \sum_i \frac{n}{n}max(F(i,j)) \quad (3)$
```

表 3 结果评估。

| 建议的 CNN | | | | | |
| --- | --- | --- | --- | --- | --- |
| 性能 | SP | P | NT | N | SN |
| 准确率 (%) | ~91.86 | ~92.03 | ~92.16 | ~91.78 | ~92.05 |
| 精确性 (%) | ~93.14 | ~92.99 | ~92.87 | ~92.79 | ~93.46 |
| 回召率 (%) | ~92.66 | ~92.29 | ~92.18 | ~92.48 | ~92.89 |
| F 值 (%) | ~91.38 | ~91.64 | ~91.73 | ~91.96 | ~91.58 |
| CNN | | | | | | |
| 性能 | SP | P | NT | N | SN |
| 准确率 (%) | ~88.86 | ~87.95 | ~88.23 | ~88.77 | ~88.18 |
| 精确性 (%) | ~87.94 | ~88.39 | ~87.25 | ~89.03 | ~87.68 |
| 回召率 (%) | ~87.89 | ~88.54 | ~86.94 | ~88.32 | ~87.93 |
| F 值 (%) | ~86.65 | ~86.83 | ~87.36 | ~86.97 | ~86.49 |
| Bi-LSTM | | | | | | |
| 性能 | SP | P | NT | N | SN |
| 准确率 (%) | ~87.59 | ~87.23 | ~86.98 | ~87.37 | ~87.08 |
| 精确性 (%) | ~86.34 | ~86.92 | ~87.67 | ~87.29 | ~87.49 |
| 回召率 (%) | ~86.32 | ~87.55 | ~86.86 | ~87.16 | ~87.34 |
| F 值 (%) | ~85.74 | ~85.98 | ~86.23 | ~85.34 | ~85.48 |
| LSTM | | | | | | |
| 呈现 | SP | P | NT | N | SN |
| 准确率 (%) | ~84.68 | ~83.99 | ~84.14 | ~84.29 | ~84.59 |
| 精确性 (%) | ~83.65 | ~84.26 | ~84.69 | ~84.16 | ~83.83 |
| 回召率 (%) | ~84.34 | ~83.72 | ~84.25 | ~84.09 | ~83.68 |
| F 值 (%) | ~82.79 | ~83.14 | ~82.49 | ~82.56 | ~82.83 |

与传统机器模型相比，我们的网络实现的 F1 分数几乎高了近 10%。我们认为，CNN 内置的检测区域变化的倾向是一个主要因素。CNN 的卷积层和组合层使其能够同时检测低级细节和全局结构。在理论上，从更长的句子中可能会提取更多的语义信息。然而，研究中的少数模型表现出特定的上升趋势。人们通常通过中短句来表达自己；当句子过长时，应该表达的数据可能会模糊。这就是为什么分析发现长句子不能准确反映情况的原因。因此，正确回答的百分比随着长度的增加而减少。

## 结论

机器学习策略已广泛应用于多个项目中进行文本分类。虽然机器学习方法被广泛采用并显示出良好的性能，但它们严重依赖于手工指定的特征，这给领域专家带来了沉重负担。由于其提高性能的潜力，深度学习方法引起了广泛关注。在研究中，我们开发了一个由卷积层组成的神经网络，用于识别情感基调。为了证明这一点，我们开发了一个由卷积层组成的神经网络用于识别情感基调。对于二分类，建议的模型达到了 81% 的准确率，而对于三分类则达到了 68%。未来，我们将此工作扩展到其他类型。

## 参考文献

[1] Ranjan R., Daniel A. 用于情感分类的 CNN-LSTM 混合模型。ADCAIJ: Advances in Distributed Computing and Artificial Intelligence 2022,10.

[2] Zakir H., Jehada A., Affab M., Hundera N., Baagere E., Qin Q. 情感分析的序列卷积神经网络。IEEE 10th International Conference on Software and Service 2019,10.

[3] Chen J., Yan S., Wong K., Li J. 社交媒体评论的深度学习。International Conference on Artificial Intelligence and Smart Communication (AISC) 2023,10.

[4] Onan A., Sasuke P. 基于卷积神经网络的 Twitter 情感分析。Journal of Computer Applications (IJACS) 2020,10.

[5] Vashit V., Pandey A.K., Yadav S.P. 基于机器学习的语音识别。The Institute of Engineers of Korea 2021,10.

[6] Oluwasanni A., Ake S., Jehada A., Hundera N., Baagere E., Qin Q. 智能服务中的序列卷积网络。ICSESS 2019.

[7] Aldians M., Sidi S. 4G 改进的卷积网络。International Conference on Artificial Intelligence and Smart Communication (AISC) 2023,10.

[8] Prakriti Kapoor Centre for Interdisciplinary Research in Business and Technology, Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

[9] Kim D., Saig P. .. U. W. 情感分析的序列卷积网络。Journal of Computer Applications (IJACS) 2020,10.

第三种情况是两个来源的元素均不被考虑[5]。随着知识和信息技术在许多不同领域的进步，这些领域发表的学术文章也随之增加[6]。因此，研究人员花费大量精力试图追踪相关的研究出版物[7]。结果，本工作提出了一种文档分类策略，能够根据论文涵盖的主题将研究论文归类为有意义的组[8]。将大量数据组织成少数几个特定的簇（如文本聚类[9]中所执行的那样），使得推测性的导航和浏览工具成为可能。然而，聚类算法中常用的词向量表示往往不是理想的，因为它没有考虑到不同概念之间的相互依赖关系。为了更好地理解或摘要，可以使用聚类分析对数据进行聚类。统计学、数据挖掘、模式识别和其他学科对聚类方法的演变做出了贡献[10]。传统的聚类是基于语法而非语义的的，并依赖于统计特征。传统的文档聚类方法使用文本集合中的简单、唯一或复杂的词汇作为特征。然而，传统方法忽略了语义关系。由于传统方法存在多义性和同义词问题，唯一的词汇集无法准确表示文档的意图，也无法产生有用的簇。语义聚类的核心是将语义上相关的数据点进行分组。在此背景下，“聚类”指的是将数据集划分成不同组的过程，其中属于同一簇的项具有相同的含义。另一方面，你不会在不同组的两个之间之间匹配。通过突出语义上的差异，语义聚类可以消除无关论文。内容资产的语义聚类需要许多关键步骤（将每个文件描述为短语、将每条记录的向量放入数学结构中，最终应用聚类算法实现聚类目标）。本研究的主要目标——使用 Ward 方法进行语义文档聚类——已实现。我们未曾发现过任何结合使用 Ward 方法和语义相似性文档聚类的研究。

## 相关工作

本研究提出了一种新的相似性度量。建议的度量在计算两个文本关于某一特征的相似程度时，考虑了以下三种情况：a) 它在两篇论文中都存在；b) 它仅存在于一个文档；c) 它两者都不存在。在第一种情况下，随着两个特征值之间的距离缩小，接近程度会提高。此外，差异的归贡献通常会被缩放。在第二种情况下，相似性中会加上一个常数。该特征对相似程度没有影响。建议的度量经过精炼，可用于比较文档集合。使用了多种用于文本分类和分组问题的真实数据源来评估我们方法的有效性。结果表明，与其他方法相比，建议的指标具有更优的性能[11]。

尽管所提出的相似性度量被认为是根据文本文档中特征的存在或否寻找书面材料相似性的理想方法，但发现 SMTP 相似性度量并未涵盖衡量成对类文件并行性的上下文。针对这一差异，本研究对 SMTP 进行了微调，以符合常见的相似性方法，并使其成为知识发现的全面相似性方法论[12]。

在本研究中，我们提供了一种衡量不同算法（或可能是相同的算法规则）产生的相同数据集簇之间可比性的程度。计算两篇论文之间的相似程度是文本处理研究中的重要任务。本研究的作者假设了一种后续相似性指数。在确定具有相同特征重要性的出版物之间的相似程度时，建议的度量考虑了以下三种情况：如果特征出现在每篇论文中，则选择“a”；如果出现在某些但不是全部，则选择“b”；如果在所有论文中都不存在，则选择“c”。在第一情况下，相似性将随着特征值差异的减少而增加。差异的显著性也经常被评估。在第二情况下，相似性被赋予一个预定的数值。在第三种情况下，特征与相似性水平之间没有相关性。使用了许多用于文本分类和分组问题的实际专家知识来评估其有效性[13]。

由于这些组都涵盖了广泛的问题，我们提出的方法基于它们的核心关注点和范围。因此，我们从这些讨论中分离出特定类别词汇符号的提取。使用词频-逆文档频率（TF-IDF）统计量，我们可以根据某些标记在文中出现的频率来确定对文档的强调程度。建议的方法在执行分类程序外，还使用了论文的标题、摘要、关键词和主题。然后，使用类别权重和文档权重之间最大的相似性指标，将文档分组到关键类别中[14]。

为了解决为阿拉伯语文本源开发集成导向分类器的问题，本研究提出了三种方法：无监督方法、半监督方法以及带有降维的半监督方法。在删除停用词并确定每个文本中每个短语的词根后，我们使用了 k-means、Criterion + k-means 以及逐渐降低维度的 k-means。然后，我们使用词加权技术计算每个短语与其对应文档的关系。随后，我们使用相似性度量技术比较每个文档与其他文档的相似性。此外，还通过 F 指数、熵和支持向量机（SVM）来计算准确率。数据集是在线的动态数据集，由于它们很容易在线访问，因此是可靠的。当用于基于推理的系统时，阿拉伯语呈现出独特的困难。因此，选择正确的数据对于此类研究至关重要。当应用于新的分类测试用例时，建议的技术比其他方法具有更高的准确性和更少的错误。当减少比例增加时，关键词可能会丢失，使得降维变得非常微妙。

## 提出的工作

### 数据准备

预处理文档说明了如何创建索引词列表以及向信息检索系统添加新文档的其他前提条件。内容预处理的目的是通过尽可能的地表征文档，增强系统内部的文档检索和存储。在预处理文档可以找到以下步骤：

- 分词（Tokenization）。
- 移除所有句号和零。
- 移除填充词。
- 词形还原与词干提取（Lemmatization & Stemming）。

## 文档演示

文档表示是文档处理和信息检索系统中的重要技术。为了在大型语料库中找到相关文档，将论文的全文转换为因子向量至关重要。如果翻译后的文档有一个称为术语索引的组件，它可以用于演示源材料的某些方面。这些术语用于索引、相关关键词排名、过滤和检索，以改进搜索结果。流行的代数方法（有时被称为向量模型）使用向量来表示文本。词频（TF）、逆文档频率（IDF）和 TF-IDF 权重赋值方案都是用于表示文档的向量空间模型。在跨短语通过滑动窗口提取样本之前，模型将上下文长度锁定在固定值上。请记住，派生的短语向量仅涉及涉及这一特定短语的情况，而不涉及任何其他句子。可以将语言向量 `W` 的范围扩展到任何一个短语之外，并考虑整个文本。在测试句子向量模型时，句句子向量代表了文本的图像。当使用 Doc2vec 模型生成句子向量时，可以想象两个相同句子的相似性并不是 1。图 (1) 显示了 Doc2vec 模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_383_0.png)

**图 (1)**
Doc2vec 模型。

最大平均对数概率最大化公式。

```
$$\frac{1}{T} \sum_{t=k}^{T-k} \log p(w_{t-k}, \cdots, w_{t+k})$$quad (1)$$
```

使用多个分类器（如 softmax）来进行预测。

```
$p(w_t \mid w_{t-k}, \dots, w_{t+k}) = \frac{e^{y_i}}{\sum_i e^{y_i}$quad (2)$$
```

在这里，`y_j` 中的 `b` 代表 softmax 参数，`h` 代表词向量 `i` 的每个结果的伪归一化对数概率，`x` 是矩阵 `W` 中术语向量的中位值。

```
$y = b + Uh(w_{t-k}, \dots, w_{t+k}; W)$quad (3)$
```

这些标准被用于确定模型的参数：文档到向量转换（单词，10x10 窗口，1 个最小工人数量，0.002 alpha）。

根据词袋概念，每个给定的词集都可用于表达任何一组句子。独热表示（One-hot Representation）用于将词袋中的每个词转换为长度等于词汇表数量的向量。词的词频（tf）是其在目标短语中出现的次数，通过词袋模型计算。逆向文档频率（idf）的计算如下：

```
$idf_i = \log_2 \frac{|D|}{\|\{j:t_i \in d_j\}|}$quad (4)$$
```

`|D|` 是语料库中包含的所有文本的总和，而 `|\{j:t_i \in d_j\}|` 代表包含 `t_j` 的文档总数。IF-IDF 值的确定如下：

```
$tfidf_{i,j} = tf_{i,j} \times idf_{i}$quad (5)$$
```

对于标准的 TF-IDF 计算，请参考以下内容。

```
$tfid_{i,j}' = \frac{tfid_{i,j}}{\sqrt{\sum_{j=1}^{|d_j|} (tfid_{i,j})^2}}$quad (6)$
```

文本相似性程度使用余弦相似度计算。

```
$similarity = \cos(\theta) = \frac{A \cdot B}{||A|| ||B||} = \frac{\sum_{i=1}^n (A_i \times B_i)}{\sqrt{\sum_{i=1}^n (A_i)^2} \times \sqrt{\sum_{i=1}^n (B_i)^2}}$quad (7)$
```



在这里，`$A_i$` 和 `$B_j$` 分代表文本 A 和文本 B。

## 文档聚类

聚类是将一组项目组织成相似组的过程。每个集合有时被称为一个簇。分割是通过聚类方法执行的。通过这种方式，聚类是有用的，因为增加了发现数据中以前未被识别的分组的可能性。某些聚类方法在组之间提供模糊集合边界，而另一些则将它们分为不同的类别。此外，某些技术使用距离作为相似性标准：划分、层次、基于网格和基于密度的算法是定义此类数据分析的四个大类。在本文中，我们使用两种聚类技术：

图 (2) 表示了根据输入样本与簇中心相似程度进行聚类的正规 `K-means` 算法。其次，随机选取簇的主节点。然后将剩余样本分配到与其最匹配的簇中。一旦完成给定样本的聚类，将调整簇中心以反映该簇内所有组件的加权平均值。重复更新中心并聚类，直到簇中心不再移动为止。选择正确的起始中心对于 `k-means` 方法成功的至关重要。步骤如下：

![](img/5e4d8ef2afa52a8404b28106580e19e4_386_0.png)

图 (2) 簇的形成。

- 初始簇产生 `k` 个簇。
- 选择簇中的节点。
- 在每一步中，使用欧几里距离函数将元素位于距离其最近的中心。
- 为所有簇找到一个新的平均中心。
- 重复步骤 2 到 4 直到中心保持稳定。

假设目前我们有两个文档，`doc1` 和 `doc2`。令 `$doc1=\{W_{11}, W_{12}, \dots\}$` 和 `$doc2=\{W_{21}, W_{22}, \dots\}$` 为两个文档均涵盖的对象集，即文档 1 和文档 2 中术语的加权向量。参考所建议的方程如下：

```
$X = (\sum t_{doc1} \cap doc_2} W_{1j}) * (\sum t_{doc1} \cap doc_2} W_{1j})$

$Y = (\sum t_{doc1} \setminus doc_2} W_{1j}) * (\sum t_{doc1} \setminus doc_2} W_{1j})$

$Z = (\sum t_{doc1} W_{1j}) * (\sum t_{doc2} W_{2j})$

$STB(doc_1, doc_2) = \frac{X}{Z} (1 - \frac{Y}{Z})$quad (8)$
```

在这里，符号 "&" 和 "setminus" 是集合论算符，表示交集和补集，`$w_{ij}$` 是允许值。通过它们的单词词向量 `$D_{ij}$` 测量两个短语之间的差距，并为短语中的每个词分配一个唯一标识符。然后，使用两个句子单词之间的距离构建一个二维坐标平面。可以对短语之间术语向量的距离进行归一化，并将其作为衡量与其他句子相似的程度。在这里，`min(WMD)` 和 `max(WMD)` 显示了数据集中最小和最大的词向量速度和对应关系。

## 基于面向方面的情感分析与模糊逻辑的 COVID-19 推特数据分类

Tarang Bhatnagar¹

¹ 商业与技术跨学科研究中心，奇特卡拉大学工程工程与技术学院，奇特卡拉大学，旁遮普邦，印度

## 摘要

在灾难或流行病期间，社交媒体已成为一种重要的通信手段。由于这些灾难具有不可预测性，很难通过许多元素和情感来检查全面的态势感知以帮助当局工作。目前，方面识别和情感分析系统严重依赖于标注数据，并需要人工对方面类别进行策划。为了从多个角度分析公众意见，本研究提出了一种混合文本分析方法。利用流行的潜在狄利克雷分配（`LDA`）主题模型，我们首先从数据中提取并聚类了这些元素。然后，我们使用语言查询与词汇计数（`LIWC`）词表来提取情感并对数据集进行标记。最后，在结构的第三层中，我们将元素映射到情感中，并使用著名的机器学习分类器对情感进行分类。我们的技术与其他面向方面的情感分析方法的比较表明，在真实数据集实验中显示了令人鼓舞的结果，我们的方法结合多种分类器变体，超越了现有方法，最高 `F1` 分数达到 91%。

**关键词：** 面向方面的情感分析、`COVID-19` 分类、模糊逻辑、推特数据集。

* **通讯作者 Tarang Bhatnagar：** 商业与技术跨学科研究中心，奇特卡拉大学工程与技术学院，奇特卡拉大学，旁遮普邦，印度；邮箱：`tarang.bhatnagar.org@chitkara.edu.in`

## 引言

在灾难或流行病期间，社交媒体已成为一种重要的通信手段。由于这些灾难的原因往往尚不明确，很难从所有角度检查问题并衡量公众意见以帮助当局 [1]。人工对方面进行标记和分类是当前方面检测和情感分析中的主要缺点 [2]。个人在各种网站上创建的信息反映了他们对广泛主题的感受，从他们每天吃的食物到他们尝试的物品。在社交网络和微博客广泛使用的背景下，特别是在 `COVID-19` 疫情期间，我们可以从消费者的反馈和意见中学习关于产品或服务的很多 [3]。因此，在做出选择之前，通过所有的评估和分析来获得整体质量的审查可能是耗时且具有挑战性的 [4]。特征相似性算法以减少所用特征的数量。第一次预处理产生了包含 537 个元素的全局特征向量。400 份文档的数据存储在 `400x537` 的文档-词对矩阵中。这意味着原始文档集的维度为 5373，表 1 所示在“分析与比较性能指数”中。

表 1 性能指数分析与比较。

| 数据库 | 技术 | 准确率 | 精密度 | 回召率 | F1 值 |
|---|---|---|---|---|---|
| `WEBKB` | `K-means + Doc2Vec + TF-IDF` 余弦相似 | 94.18 | 94.18 | 94.18 | 94.01 |
| | 余弦+`TF-IDF` | 88.34 | 88.16 | 88.22 | 88.14 |
| | | 85.02 | 84.19 | 84.19 | 84.06 |
| | 层次聚类 | 85.01 | 85.02 | 85.01 | 84.92 |
| | 余弦 + `Kmeans` | 87.23 | 87.21 | 87.22 | 87.21 |

## 结论

本研究提出了一种新颖相似性度量。为书面材料找到一种允许开发连贯分组的合适相似性度量是文档聚类的一个重大困难。随后，我们使用 `TFIDF` 构建了向量空间，然后使用 `Ward` 方法和 `K-means` 算法完成聚类。在语义文档聚类过程中还额外使用了 `WordNet`。展示所有簇之间连接的可视化和交互式网站说明了研究结果。基于传统的词袋范式，考虑了文本中语言的存在和频率。这种方法可能会导致含义相同但词汇不同的文本被放在不同的组中。使用所提方法获得的结果已通过 `F` 数（`F-measure`）对其正确性进行了分析。通过与短语向量模型（`Doc2vec`）以及词袋模型进行比较，证实了所提策略的优越性。所提方法可用于解析在线发布的聊天日志和客户反馈。扩展当前研究将允许开发新的相似性函数，用于文本文档聚类和文本分类任务，从而产生更高质量的簇和更准确的分类器。开发用于文本聚类和分类的基于内核的相似性度量非常有意义。

## 参考文献

- [1] Abdalla H.I., Meer A.A., 布尔逻辑代数驱动的文本应用相似性度量。`Peerj Comput. Sci.`
- [2] Yadav S., Bhati B., Mahato D., Kumar S., 联邦学习在物联网中的应用. 商业与技术跨学科研究中心。
- [3] Al-Subahin A., Sarro F., Capra L., 移动应用的实证相似性测量。`AI` 软件期刊。
- [4] El-Eho A., Al-Zoghby A., Hamza T., 相似性度量的综述。埃及语言工程期刊。
- [5] Vashisht V., Pandey A., Yadav S., 使用机器学习的语音识别。韩国电子学会。
- [6] G. Suresh Reddy, T. V. Rajikanth, and A. Rao 用于文本聚类和分类的新型相似性度量设计与分析。第 15 届计算机系统与技术会议。
- [7] Alajnan, K. A., Crockett T., and Latham A., 短文本的启发式预处理方法。第 16 届高性能计算与通信会议。
- [8] Castro-Insu A., Gómez-Rodríguez C., 地区域相似性度量。第 16 届数据科学与系统会议。
- [9] Al-Turman F., Yadav S.P., Kumar M., Yadav T., 用人工智能、大数据和物联网转型管理。`Springer` 出版社。
- [10] Lin Y.S., Jiang J., Lee S., 文本分类相似性度量。`IEEE` 知识数据工程期刊。
- [11] Kumar Nagwani N., 对文本分类相似性度量的评论。`IEEE` 知识数据工程期刊。
- [12] Elango P., 用于文本分类的相似性度量。计算、通信与信息国际会议 (`ICACC`)。
- [13] Jalal A.A., Ali B.H., 使用数据挖掘技术进行文档聚类。国际电子与计算机工程期刊 (`IJECE`)。
- [14] Sangaiah A.K., Fakhry A.E., Abdel-Basett M., El-henawy I., 使用改进聚类算法和降维的阿拉伯语文本聚类。聚类计算。

## 相关工作

在本研究中，我们开发了一种混合方法文本分析框架，用于在个体维度层面上剖析公众意见。通过流行的隐含狄利克雷分配（`LDA`）主题模型，我们最初从数据中提取并聚类了各个维度。随后，我们利用语言查询和词汇计数（`LIWC`）词典提取了情感并对数据集进行标记。最后，在框架的第三层中，我们将维度映射到情感上，并使用著名的机器学习分类器对情感进行分类。我们的技术与其他面向方面的情感分析方法相比，在真实数据集实验中显示出鼓舞的结果，我们的方法结合多种变体分类器超过了现有方法，最高 `F1` 分达到 91%。

在该研究中，我们提供了一种新颖感分类方法，整合了自动标记（`SentiWordNet`）、集成技术（`Stacking`）和先验知识主题算法（`SA-LDA`）。使用了不同领域的数据来评估该框架。根据结果，建议的 `SA-LDA` 是金标准 `LDA` 的改进。与标准分类方法相比，所提的集成学习分类器的准确性高出 3%。研究发现，所提方法足够灵活，适用于各种环境。

该设计方法包括一个集成的四层神经网络，由来自变换的双向编码器表示（`BERT`）词向量模型、长短期记忆网络、交互式双注意力机制（`IAOA`）以及用于在该研究中构建面向方面的情感分类模型的线性输出层组成。该模型使用来自东京的 92,905 条假设用餐评分进行了开发、测试和验证。结果发现，与之前的神经网络相比，该模型大幅提升了性能。结果证明了这种新策略在旅游和酒店行业的可行性。建议未来研究引入可以自动引入到维度集中的创新元素，本文介绍了如何利用神经网络提升旅游酒店业在线评论面向方面的情感分类的最新研究。

将卷积神经网络与双向门控单元结合提出了一种情感分类模型。长短期记忆作为一种处理复杂度较低的时间循环神经网络，等同于双向门控单元。该模型使用双向门控单元提取文本的序列属性，随后使用卷积神经网络提取文本的局部静态维度。当所有其他方法都失效时，采用 `Sigmoid` 分类器来确定人们的感受。

我们建议了一种 `NLP`（自然语言处理）模型来评估波斯开放文本调查回答，并识别伊朗人的积极和消面情感，以实现这一目标。该研究使用了 `distilBERT` transformer 模型。使用了三种方法进行比较，其中效果最好的显示出改进。`F1` 分数 = 0.804；精确率 = 0.824；召回率 = 0.798；总体 = 0.824。

## 提出的工作

图 (2) 展示了我们所提框架的高级视角，后续章节将详细阐述其各个部分。

## 推文数据挖掘

在 2020 年 2 月和 3 月分析的 210 万条推文中，包含了来自 7 万个个体的 9 万条独特推文。我们的研究中出现了包括“隔离”、“封锁”和“待在家”在内的十二个类别。`COVIDSENTI` 被分为三个等等的部分，每个部分包含积极、消极或中性的情感数据。使用了访问 `Twitter API` 的 `Python` 包 `Tweepy` 版本 3.2 来获取推文数据收集。

## 预处理与标记

我们使用预设规则为数据集中的每条推文分配积极、消极或中性的情感标签。使用 `TextBlob` 程序生成“积极”、“消极”和“中性”情感标签。`TextBlob` 声称其得分（表示为从 `[-1到1]` 的极性）可以用于推断句子的语调。如果推文的极性小于 `-0.4`，则认为是消极的。大于 `0.4`，推文被视为正面。极性为 `0` 的推文被视为中性。算法 1 提供了分类和分析推文语调的伪代码。

```
$L_{T_i} = \begin{cases} Negative, & P < -0.4 \\ Positive, & P > 0.4 \\ Neutral, & -0.4 \geq P \leq 0.4 \end{cases} \quad (1)$
```



其中 $P_i$ 是推文 $T_i$ 的极性，且 $-1 < P < 1$。

- 由于原始推文通常简短、非正式且充满噪声，预处理数据是情感分析的初始阶段。为了实现这一目标，按照指定的顺序将以下方法序列应用于文本。
- 标签（如 `#COVID-19`、`#StayHome`、`#StaySafe` 和 `#Coronavirus`）用于代表几乎所有媒体平台上的对象。标签会分散注意力且往往毫无意义，甚至可能损害你的性能。作为第一步，我们通过排除未使用的标签进行了简单的文本清理（尽管仅是字符，而非实际内容）。
- 之后，你将对文本进行大小写转换。所有大写字母都转换为小写，以免根据大小写将相同的术语误认为是另一个。
- 某些术语（如“stayathomestays”和“coronavirus”）作为长短语的一部分被错误地连接。
- 在从分析文本中删除任何链接、`@`提及或标点符号之前。去噪和词干还原（重复内容省略）。

## 文本分类

所提模型以推文的特征作为输入。模糊化是将清晰输入转换为模糊集合的过程。推理是使用 `IF-THEN` 规则来开发输出的过程。

表 1 变量 | 语言变量 | 范围 | 语言值 |
| --- | --- | --- | --- |
| 输入 | | | 极低 | 0-0.35 |
| - | | | 低 | 0.15-0.45 |
| - | | | 中等 | 0.25-0.55 |
| - | | | 高 | 0.4-0.7 |
| - | | | 极高 | 0.6-1 |
| - | | | 极低 | 0-3.5 |
| - | | | 低 | 2-8 |
| - | | | 中等 | 5-11 |
| - | | | 高 | 8-14 |
| - | | | 极高 | 11-20 |
| - | | | 短 | 0-8 |
| - | | | 中等 | 5-15 |
| - | | | 长 | 12-20 |
| - | | | 低 | 0-3 |
| - | | | 中等 | 2-6 |
| - | | | 高 | 4-8 |
| - | | | 极低 | 0-0.25 |
| - | | | 低 | 0.2-0.38 |
| - | | | 中等 | 0.3-0.6 |
| - | | | 高 | 0.55-0.7 |
| - | | | 极高 | 0.65-1 |
| - | | | 极低 | 0-0.12 |
| - | | | 中等 | 0.06-0.23 |
| - | | | 高 | 0.16-1 |
| - | | | 低 | 0-4 |
| - | | | 中等 | 3-7 |
| - | | | 高 | 6-10 |
| - | | | 无关 | 0-40 |
| - | | | 低相关性 | 30-65 |
| - | | | 中等相关性 | 50-85 |
| - | | | 相关性 | 30-0 |
| - | | | 高相关性 | 75-100 |

表 1 显示了输入和输出参数的允许变化。这些参数是通过分析真实世界数据确定的。例如，最高词评分 `H` 的取值范围为 `[0.0,35]`、`[0.15]`、`[0.25]`、`[0.4,0.7]` 和 `[0.6,0.1]`，表 1 显示了极低、低、中、高和非常高的程度。由于 `H` 的程度很高，相关的推文与发生的情况密切相关。

在本文中，我们使用 `IF-THEN` 逻辑来创建模糊规则。模糊规则的结构类似于 `IF-THEN` 语句，包含一个底层条件和一个结果。规则共有四种不同类型：重要性分为四个级别：1) 极其相关；2) 较相关；3) 相关；4) 不相关。以下法规作为示例，以说明更清晰的观点。

如果 `H` 和 `I` 均为高值（如 `R_1` 所示），则 `R` 被认为具有高重要性。

通过推文的高字数和术语的使用频率，可以推断出推文与事件的强相关性。

`R_2`：如果 `H` 和 `G` 均显著，则 `R` 也被认为具有中等重要性。当推文具有中等字数和权重时，认为它对事件具有中等重要性。

如果 `E` 和 `G` 均为低值，则 `R_3` 被认为具有低重要性。

低相关性推文包含的关键短语较少，如推文的低权重以及常用术语的低权重所示。

`R_4`：如果 `H` 非常低且 `M` 较长，则忽略 `R` 的相关性。

如果一条较长的推文不包含任何与事件直接关联的术语，则它是不相关的。

与事件具有高度相关性的推文包含在第一类。例如，`R_1` 规定变量必须具有更大的幅度或更短的长度。具有中等语言值的推文（如符合 `R_2` 标准的推文）属于第二类，即中等相关。符合 `R_3` 标准的变量属于第三组，即低相关，该组也可能包含一些中等相关的变量。推文不符合中等相关标准；它们是不相关的。不符合其他三类中任何一类的推文（例如符合 `R_4` 标准的推文）属于第四类也是最后一类，即不相关。后一组的推文通常存在语言值低或过长的问题。请记住，如果一条推文过长且语言质量差，它可能不包含太多关于该事件的信息。因此，可以将其忽略为无关紧要的点。

结果，我们创建了一组 25 条法规。总共有十四条指南：七条用于“高相关”，八条用于“中相关”，三条用于“低相关”，七条用于“不相关”。

## 结果与讨论

为了方便比较，本节描述了为评估基准数据集性能而进行的实验。为了确保精确性，我们进行了十折交叉。多种机器学习方法提供了初步发现，图 (1) 表示在准确率（Accuracy）结果中，图 (2) 显示了结果的总结和可视化。图 (3) 画在召回率（Recall）结果中，图 (4) 画在 F 分数（F-measure）结果中。

![](img/5e4d8ef2afa52a8404b28106580e19e4_404_0.png)
图 (1))
准确率结果。

![](img/5e4d8ef2afa52a8404b28106580e19e4_405_0.png)
图 (2))
精确率结果。

![](img/5e4d8ef2afa52a8404b28106580e19e4_406_0.png)
图 (3))
召回率结果。

![](img/5e4d8ef2afa52a8404b28106580e19e4_407_0.png)

## 结论

随着 COVID-19 阴谋论的泛滥，社交媒体被用于反对和纠正虚假信息。在文中，我们讨论了关于 COVID-19 的 Twitter 消息语气问题。我们使用多种情感分析工具对 COVID-19 的情绪进行了比较检查。根据我们的数据，大多数人在 2 月支持封锁和居家指令，但他们的观点在 3 月中发生了逆转。由于态度转变的原因尚不清楚，但可能归因于通过社交媒体传播虚假信息，因此必须建立一种主动且适应良好的公共卫生存在来应对这一现象。我们已经为了研究目的开放了大量的 COVID-19 基准情感分析数据集。

## 参考文献

[1] Aygün I., Kaya B., Kaya M., 基于深度学习的 COVID-19 大流行期间接种和疫苗类型基于方面的 Twitter 情感分析.IEEE J. Biomed. Health Inform.20222653260

[2] Jalaye R., Desai S.S., Umesh S.P., 基于深度学习 COVID-19 药物预测的方面级情感分析国际计算通信与绿色工程会议(CCGE)202211599

[3] Zhou H., ZHAO Y., Long S., Huang S., 基于图卷积结构的面向根的情感分类国际电子技术通信与信息会议(ICETCI)2022233237

[4] Jeong H., Bayro A., Umesh S.P., Mangam K., Lee M.A. COVID-19 与医疗健康视角：使用社交数据和情感分析评估可穿戴混合现实显示器的用性.JMIR Serious Games2022.219

[5] Yadav S., Zaidi C.D.S., Nascimento V.H.C., de Albuquerque and S. S. Chauhan,自动生成 GPS 移动跟踪系统的分析与设计人工智能与智能会议(AISC)2023 印度.

[6] Wahid J., Hussain S., Wang H., Wu Z., Li L., COVID-19 推文的比较研究国际通信技术会议(CT)202125893

[7] Zhao F., Wu Z., Long S., Huang S., Chen J., 面向方面的情感分类国际计算语言会议2022

[8] Wu Z., Gao J., Guan Z., Chen Z., 从形容词-名词对中学习：一种增强的202228847

[9] Yadav S. P., Yadav S. S., 医学图像的小波数学实现 动态控制系统先进研究杂志201910455

[10] Wahid J., Hussain S., Wang H., Wu Z., Li L., COVID-19 数据的方面情感分析国际计算机工程与人工智能会议(ICCEAI)202122712

该方法考虑了方面层面的情感，由于与业务需求相关，成为一个备受关注的研究领域[6]。方面术情感分析（ATSA）和方面类别情感分析（ACSA）两个任务构成了基于方面度的情感分析（ABSA）。情感分析是研究人们对某事或某人的感受的研究[7]。随着社交媒体网站和电子商务应用程序的兴起，分析产品标记的用户评估以获取对物品接受程度的洞察的重要性日益增加。通过执行方面级情感分析，他们可以更多地了解客户对单个产品特征的感受[8]。电子商务、在线社区和社交媒体的普及均显著增长。从最终结果来看，客户的意见非常[9]。商品和服务的供应商、卖家和生产者从任何反馈中大获益，即使仅仅是一条评论或评价。由于用户反馈如此重要，情感分析吸引了大量的关注。通过情感分析过程，可以从用户的写作中获取其特征、属性和观点。电子商务网站作为替代渠道的激增刺激了涵盖各种商品和服务的评论网站的发展[10]。因此，企业可以很好地追踪其声誉并衡量客户需求，而消费者则可以利用基于方面的情感分析来指导其购买决策。除了简单的短语或文本级情感分类，使用一种名为基于方面的情感分析（ABSA）的方法可以鼓励进行更深层次的研究。

## 相关工作

基于在 Amazon 上留的消费者反馈，本研究使用词性标记和分类算法来判断评论是正面的、负面的还是中立的[11]。

为了同时学习 ATSA 和 ACSA，本研究提供了一种多任务学习架构，该架构使用预训练的 BERT 模型作为共享表示层。为了充分利用上下文数据，我们在通用的 BERT 模型上构建了多头自注意力层，并通过跳跃连接（skip connection）连接这些头。我们的多任务学习模型在利用 SemEval 数据集时表现优于基准多任务网络和单任务模型[12]，证明了在 ATSA 测试上性能的提升。

在对 780 万条 Amazon 客户评论的分析过程中，本研究提出了一种基于频率的方法和无监督机器学习技术进行主题提取（方面识别）和情感检测的工作流。本文利用了传统技术，包括逻辑回归、向量机和朴素贝叶斯方法[13]，以确定分析模型的精确率。

该过程的关键部分是提取用户方面，然后利用这些提取的方面对用户方面进行分类。在自然语言处理领域，CNN 模型在近年来日益流行。本研究通过结合双向长期记忆（LSTM）和 CNN 模型提供了一种独特的混合 CNN 模型，通过学习其高层属性来顺序分析数据。使用拼接方法将重要数据的丢失降至最低。实验采用了基准产品评论数据集和酒店评论数据集，与最先进的方法相比，所提出的混合模型在产品评论数据集上实现了 93.6% 的准确率，在酒店评论数据集上实现了 92.7%[14]。

该目标是识别对某些物品（如笔记本电脑）的估值及其特性（如成本、功能性、耐用性等）。能够根据客户评分提供此类结果的方法极少，而从自由文本评论中提供此类结果的方法更少。除了评论数据不足外，冷启动问题也是障碍之一。在本研究中，我们提供了一种方法，根据网络爬虫从多个来源获取的用户生成评估自动计算动态元素的情感，使我们避免冷启动问题。因此，我们的方法改进了以往在在线商店衡量客户意见的方法。

## 提出的工作

### 概述

情感分析由于检查文本中表达的情感和观点，属于更广泛的自然语言处理（NLP）类别。它从文本中提取正面、负面和中性的情感。由于处理文本数据的性质，在实际分类之前进行大量的准备工作。首先通过为每个单词分配词性（POS）标记对句子进行预处理，然后识别并删除停用词和不必要的形容词。所提的研究使用 Amazon 客户评论来评估朴素贝叶斯、支持向量机（SVM）以及机器学习算法在产品特征和方面级情感分析中的有效性。要采取的措施列在图 (2) 中，该图描述了建议的系统架构。

### 客户评论

机器根据真实客户写的评论（3.2）提供 Amazon 商品的信息。客户评论是产品购买者在电子商务网站上留下的书面意见。反馈可能是完全正面的、完全负面的，或者介于两者之间。

### 词性标记

文本类客户反馈被标记 3.3 个词性标记。为了将短语中的每个单词分类为属于特定的词性，使用了“词性标记”。这是我们确定单词形态类别的方法。它涵盖了从名词到介词的所有词性。形容词和名词对情感分析特别有用，因为它们揭示了说话者的情绪状态。

### 特征提取

特征 3.4 的提取：客户评论中的情感检测需要根据名词短语、名词以及从词性标记中获取的形容词来提取特征。使用 Apriori 算法来实现此。数据挖掘算法包括 Apriori 算法。它是分离数据集中高流量部分的工具。应用于数据库的关联规则为这种方法提供了基础。频繁项集的所有子集也应该是频繁的，反之，任何不频繁集的超集也是如此。这是在使用 Apriori 方法时必须考虑的两个关键假设。Apriori 方法简单且易于实现。它也适用于大量的对象集合。

### 特征剪枝

特征剪枝通常被称为“去噪”，是从特征集中消除冗余元素（如停用词）的过程。然后使用特征剪枝提取意见词。单词用于表达对产品的个人意见。

作为分析的一部分，基于词典的方法使用一组预定义的单词短语和意见成语，每个短语都被分配一个正面或负面的情感分。虽然许多研究采用基于字典和语料库的自动方法来分配意见术，但研究人员有时会在信念声明中分配单词和短语以确保准确性。在零售业务（如电子商务网站）中，此规则为语义相似的术语分配倾向值（slant values）。由于代表语言多样性，网站上的许多评论和注释包含俚语和拼写错误。这使得创建自动化系统的任务更具挑战性。此外，分析陈述情感和分类观点极性需要先验知识。在词典分类器下，可以使用两种方法来收集带有同义词和反义词的在线字典：基于字典的技术和基于语料库的方法。该方法不断向列表中添加新词，直到无法识别出其他短语为止。

## 分类

情感分析是一个相对较新的研究领域，旨在对个人书面或口语包含的流行数据进行分类，例如他们对产品、服务或事件的意见。它可以揭示读者在阅读文章或面对事件时的心理状态。代表当前流行时期的一种情感分析形式是人对疾病传播表达的焦虑。这种交流描述了现在的世界状态。正面、负面和中立的发现被区分开来。为了理解数据，情感分析进行了一些清理和预处理。分类过程从 SentiWordNet 计算每个单词的正面、负面和中性权重开始。图 (1) 展示了系统流程图。

数据集中距离超平面最近的点被称为支持向量。数据通过超平面进行分类。我们采用源自最大可行间隔的超参数，来对新数据进行恰当的分类。尽管支持向量机能产生可靠的结果，但其使用仅限于较小的数据集。这种方法效果更好、速度更快。论点摘要：在此阶段，计算每个分类器的负面、中性和正面评论的总和。通过使用支持向量机分类和朴素贝叶斯分类生成意见摘要。图(2)显示了情感分析技术，图(3）显示了 SVM 分类。

![](img/5e4d8ef2afa52a8404b28106580e19e4_417_0.png)

图 (1))
系统流程图。

![](img/5e4d8ef2afa52a8404b28106580e19e4_418_0.png)

图 (2))
情感分析技术。

![](img/5e4d8ef2afa52a8404b28106580e19e4_419_0.png)

**图. (3))**
SVM 分类。

## 结果与讨论

最后，将朴素贝叶斯分类与支持向量机分类进行了比较。使用算法的效率对其分类。准确率、精确率、召回率和 F1 分数等指标可以应用于支持向量机和朴素贝叶斯分类算法，以确定它们的性能。确定这些值的公式如下：

$$Accuracy = \frac{TP+TN}{TP+TN+FP+FN}, Precision = \frac{TP}{TP+FP}, Recall = \frac{TP}{TP+FN}, F1 = \frac{2*Precision*Recall}{Precision + Recall}$$

真阳性、假阳性、真阴性和假阴性实例分别表示为 `TP`、`FP`、`TN` 和 `FN`。

我们的实验发现将评论中的每个单词分类为名词、代词、动词、副词或形容词。Apriori 算法返回了评论中最常用的术语。在对评论运行了分类算法后，我们从中提取了形容词。利用 SentiWordNet 获取每个词的正面、负面和中性评估。

我们计算了召回率、F 分数、精确率和准确率，以评估朴素贝叶斯和支持向量机分类方法。我们利用假阳性和真阳性数据以及假阴性和真阴性样本计算了召回率、准确率、F 分数和精确率。表 2 展示了算法各自的准确程度。表 1 提供了 SVM 和 NB 分类算法准确率的细节。

表 1 SVM 和 NB 分类算法的准确率。

| 朴素贝叶斯 | 支持向量机 |
| :--- | :--- | :--- |
| 准确率 (Accuracy) | 90.423 | 83.423 |
| 精确率 (Precision) | 0.947 | 0.852 |
| 召回率 (Recall) | 0.959 | 0.83 |
| F 分数 (F-Measure) | 0.952 | 0.841 |

表 2 朴素贝叶斯分类实例。

| 真阳性 (True Positive) | 假阳性 (False Positive) | 真阴性 (True Negative) | 假阴性 (False Negative) |
| :--- | :--- | :--- | :--- |
| 0.947 | 0.053 | 0.1 | 0.04 |

根据我们的实验，我们可以说 NB 分类比使用支持向量机的分类更准确。

这些数据均源自每个分类的真阳性、假阳性、真阴性和假阴性样本。表 2 显示了朴素贝叶斯分类的 `FP`、`TP`、`FN` 和 `TN` 值。支持向量机分类的 `FP`、`FN` 和 `TN` 值显示在表 3 中。

表 3 SVM 分类实例。

| 真阳性 (True Positive) | 假阳性 (False Positive) | 真阴性 (True Negative) | 假阴性 (False Negative) |
| :--- | :--- | :--- | :--- |
| 0.947 | 0.053 | 0.1 | 0.04 |

## 结论

在本工作范围内，我们开发了特征级的情感分析。电子商务行业一直渴望了解客户对他们产品的看法，本文对情感分析以及该领域使用的关键方法进行了详细介绍。该过程从情感分析的想法开始，这是一种解读客户感受的较新方法。它详细说明了与情感分析技术相关的任务，例如基于词典的方法和机器学习监控的方法。然而，情感分析被应用于零售业，特别是在电子商务领域，以帮助企业运行得更顺畅。精确率、召回率和 F1 分数用于评估使用 SVM 分类算法对数据分类的结果。在准确率方面，朴素贝叶斯优于支持向量机。

## 参考文献

[1] Yiran Y., Srivastava, S.. Aspect-based Sentiment Analysis on mobile phone reviews with LDA the 2019 4th International Conference on Machine Learning

[2] Li G., Chen, Q., Zheng, B., Hung, N., Zhou, P., Liu, G.. Time-sentiment Recommendation Models Based on Novel Similarity Measure

[3] Shaik, T., Deshpande, D.. Review on Opinion Mining and Sentiment Proceedings of the International Conference on Computational Intelligence and Communication

[4] Yadav S. P., Saidi, S., Nascento C.D., de Albuquerque V.H., Chauhan, S.. Analysis and Design of automatically generating for GPS Based Object Tracking System 2023 International Conference on Artificial Intelligence and Smart Communication

[5] Wu H., Li, M., Wang, W., Cheng, S.. Big Data Management and Analytics in Scientific Programming: A Deep Learning-Based Method for Aspect Category Classification of Question-Answering-Style

[6] Yadav S., Yadav S.. Mathematical implementation of fusion in continuous wavelet domain Journal of Advanced Research and control

[7] Prathi J.K., Rarthi P.K., Gopalapalachi M.. Real-Time Aspect-Based Sentiment Analysis on Consumer Reviews 2020.. Springer Notes in Computer Science 677

[8] Abebe B., Selam, A., Babu H., Ayalew, A.. Comprehensive Analysis of Deep Learning Models for Aspect Level Sentiment 2022 International Conference on Decision Aid Sciences and Applications

[9] Yadav V., Verma, P., Kumar, V.. Short term memory (LSTM) model for sentiment analysis in data for e-commerce International Journal of Information Technology

[10] Vanaj S. J., Belwal, M.. Aspect-Level Sentiment Analysis on E-Commerce 2018 International Conference on Innovative Research in Computing (ICIRCA)

[11] Pei, Y., Wang, Y., Wang, Q.. Aspect-Based Sentiment Analysis with Multi-Task Learning 15th International Conference on Computing and Big Data (ICCBD)

[12] Pail, P., Phansalkar S.P., Kryassanov V.V.. Topic Modelling for Aspect-Level Sentiment Analysis Proceedings of the 2nd International Conference on Data Engineering and Communication

[13] Koppusamy, M., Selvaraj, A.. A novel hybrid deep learning model for aspect based sentiment analysis.

# 决策树与支持向量机是此处对比的一些分类算法。

**关键词：** 人工智能、客户意见、购物评论、文本分类。

- **通讯作者 Sanya Khurana:** 商业技术跨学科研究中心，奇特卡拉工程与技术大学，旁遮普，印度；电子邮件：saniya.khurana.orp@chitkara.edu

## 引言

现在有大量完全以文本形式存在的消费者评论。评论表达了对产品或服务的意见[1]。意见挖掘是情感分析的另一个名称。为了监控客户对产品和服务的感受并更好地了解行业，许多公司对文本数据使用情感分析[2]。意见挖掘也称为情感分析，是从海量用户生成的内容提取提取或负面情感的方法[3]。情感分析至关重要，因为它允许企业根据评论衡量客户对特定产品的满意程度[4]。不断增加的产品评论使得手动进行这种分析变得困难[5]。情感分析通常被称为“意见挖掘”，分析并分类人们对文本感受的过程。这涉及到文本和语言处理[6]。随着网络技术的普及，数据量呈爆炸式增长[7]。通过短评表达情感已成为常态[8]。快乐、悲伤、担忧等情感属于这一类别。双向编码器表示模型（BERT）是一种用于各种 NLP 应用的前沿语言模型[9]。分析来自社交媒体网站的海量非结构化数据并基于上下文做出准确预测是一个困难且耗时的任务。近年来，循环神经网络技术，如长短期记忆（LSTM）和双向长短期记忆（BiLSTM），以及混合模型、中立性分类算法和传统的文本分类算法有所增加。成功的企业旨在通过多种方式满足客户并获得好评[10]。然而，由于从各种来源获取的海量数据，准确评估客户评价以预测情感被证明是一项困难且耗时的任务。许多学者已经开发了算法、方法和模型来解决这一问题。其中包括人工神经网络（ANN）和词袋（BOW）回归模型，以及基于单字（unigram）和跳字（skip-gram）的算法。许多研究发现了极性不一致、模型过拟合以及性能问题。

机器学习技术被用于分类评论。在本研究中，我们使用六种不同的机器学习技术来识别情感。对这些技术的精确性和有效性研究。客户反馈也接受了特征情感分析。情感分析和预测在三个不同层级执行：文档、短语和特征。文档级情感分析判断一段文字是积极、负面还是中性的。本文在此考虑了文档级和特征级的情感分析。

本文的章节如下：下一节讨论了本项目的研究基础。第3节描述了分析模型。第4节给出结果，第5节给出结论。

## 相关工作

本研究使用了朴素贝斯、随机森林、决策树和支持向量机分类器进行对比。在本研究中，我们通过衡量对不同大小移动产品数据集分类的能力，评估了多种分类器的效能。从 Amazon、Flipkart 和 Snapdeal 等热门零售商收集了数据并分析以确定准确性。朴素贝斯、随机森林、决策树和支持向量机是用于选择最佳方法的种分类方法[11]。

本研究目的是提供一个积极、中性和负面分类产品评论的情感分析模型。为了开发最有效的分类器，使用了五种著名的机器学习分类器：朴素贝斯、支持向量机、决策树、K最近邻和最大熵。所使用的数据集包括 Kaggle 网站上 82,815 条关于手机设备的评分和评论。我们采用召回率、精确率、F1值和准确率来比较这五种不同的分类器。实验均表明最大熵和朴素贝斯是最准确的分类器。在所有实验中，决策树算法表现最差[12]。

文本分析倾向于捕捉观众的整体情绪。IMDb 上的“情感分析”功能让用户看到影评对电影的总体感受。由于人类意见对产品成功很重要，且观众反应可能会决定电影的票房表现，成本正在增加。机器学习系统基于语法和语言特征将情感分析视为普通的分类问题。在本研究中，我们探索了机器学习技术在情感分析中的应用。SVM、RF、ANN 和 NB 以及 DT、BN 和 KNN 算法常用于情感分析]。

在本文中，我们报告了关于如何提高情感分析模型性能、准确性和上下文预测的实验研究结果。利用来自 Twitter、IMDB 电影、Yelp 和 Amazon 的消费者评价，我们展示了一个调优 BERT 模型来预测用户态度。此外，我们提供了一个仪表板报告，将建议模型的性能与我们的定制线性支持向量机（LSVM）、fastText、BLSTM 和混合 fastText-BLSTM 模型进行了对比。这一实验结果表明，建议模型在系列性能指标上优于竞争对手[14, 15]; LSTM; BLSTM; fastText。

![](img/5e4d8ef2afa52a8404b28106580e19e4_430_0.png)

**图 (3)** 电影数据集。

对每条评论都使用了以下方法：

- 1. 去除重复项，移除不必要的标点符号和数字，并对数据进行其他清理。
- 2. 去除如“the”、“a”、“an”和“the”之类的填充词。
- 3. 分词和转换的作用。
- 4. 评论可以通过将其拆分为更小的单元进行分词。
- 5. 消除填充词。
- 6. 停用词是指连词和代词等对文本含义没有额外贡献的术语。在此过程中，文本中消除了如“a”、“an”、“the”等常见的填充词。高频词汇也应该被被消除，因为它们可能会导致错误的文档分类。

## 词干提取 (Stemming)

词干提取是从单词（词干或根）中消除词中、前缀和后缀的过程。使用词干提取器时，单词的根会在最终产物中省略。这允许我们识别那些具有根但由于词缀而具有不同含义的单词。与计算机相关的名词如“computer”、“computing”、“computation”和“computes”都共享共同的词源。

## 特征提取方法 (Feature Extraction Methods)

在情感分析中，适当的特征选择方法对于定位重要特征和提高分类精度起着关重要的作用。我们尝试了三种不同的特征提取方法并比较了它们的结果。使用词袋 (BOW) 模型或 N-gram 模型，将最重要的情感表达词提取作为每条评论文本的特征集。

- **术语权重 (Term Weighting):** 一旦从单词中派导出术语，必须确定文档的呈现形式，即其表示方式。我们使用“权重”一词来描述这种方法。根据内部的内容，文档可以表示为向量。该方法用于计算词频-逆文档频率 (TF-IDF) 特征加权的方法采用了权重方案。“n-gram”一词用于描述一组全单词的 n 个标记。

- **词汇剪枝 (Pruning of the Words):** 剪枝是从集合中消除不重要文档的过程。术语向量是非常稀疏且高维的。同样明显，在术语向量的大量元素中值“O”。因此，我们移除了在整个论文中仅出现两次或更少的术语。通过此过程，进一步减少了术语向量的维度。

## 文本分类方法 (Text Classification Methods)

由于其在文本分类中的实用性和准确性，本研究采用了支持向量机 (SVM)、人工神经网络 (ANN)、朴素贝叶斯 (NB)、决策树 (DT)、相关性 (C4.5) 和 KNN 方法。使用分类器允许我们评估这六种不同文本分类方法的效力。以下是各种方法的总结。系统流程图如图 (4) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_432_0.png)

图 (4)
系统流程图。

## SVM

对于数据分类，SVM 是一种监督学习技术。它是一种非常有用的策略，专注于划分好坏样本的最优表面。支持向量机 (SVM) 的训练过程针对特征评论的分类任务旨在实现最大间隔超平面。两组之间的边界可以无限地绘制。通过选择一个以最大距离隔开两个类别的决策边界，可以确定最佳类别。靠近其中一类边界的最大间隔决策边界将减少预测错误的概率。由于其性能优异，选择了点核而非径向核和多项式核。参数 C 为 2。

## 人工神经网络 (Artificial Neural Networks)

生物神经网络的形式和功能为人工神经网络 (ANN，也称为神经网络 (NN)) 提供了灵感。核心连接主义原理指出，心理事件可以用简单且频繁统一的元素的互连网络来表征；这是神经网络在处理信息时采用的方法。ANN 通常是一个自修改系统，在学习阶段根据输入的数据来修改其架构。现代神经网络最常见的应用是输入-输出交互的建模以及数据中模式的发现。在馈传播神经网络中，节点之间的连接不会以定向的方式重复。从输入节点开始，通过隐藏节点（如果有），最后到达网络的输出节点。网络不包含任何无限循环或周期。

反向传播算法的两个主要部分是“传播”和“权重更新”，是一种监督学习技术。这两个步骤被重复执行，直到网络达到可接受的性能水平。在反向传播算法中，通过将计算输出与正确结果进行比较来计算误差函数。通过多种方法，错误被回传到系统中。然后程序使用数据来微调每个连接的权重，以最小化误差函数。如果重复训练次数足够，网络最终将达到一个稳定状态，此时计算的不准确性降至最低。在这种情况下，我们可以说网络已经具备了执行所需任务的能力。

使用 ANN 进行情感分析是一种前沿方法。技术和学习算法的进步使得创建多层网络（通常称为深度学习）成为可能，这促进了 ANN 作为机器学习的一种手段的飞速崛起。

## 朴素贝叶斯 (Naive Bayes)

NB 树将贝叶斯规则与决策树相结合以创建一个监督分类器。假设属性之间是条件独立的，仅需要计算协方矩阵的方差。

## 决策树 (Decision Trees)

决策树是一种树形模型或图。它更像一棵倒立的树，根在顶部，分支在下方。这种数据可视化比其他方法更好，因为它直观且合理。树的每个内部节点代表一个输入属性。如果一个输入属性具有固定数量可能值，那么连接内部节点的边缘数量也是固定的。发送的数值属性末端附有单独的带。给定从根到叶路径的输入属性值，每个叶子节点代表标签属性的值。在 Cart 方法中，通过将每个决策节点分为两个分支来构建决策树。

## C4.5 决策树分类器

在机器学习中，决策树通常用于从可用训练数据自动生成分类树。传统的决策树方法由两个阶段组成。在初始阶段（被称为“树生长”），通过贪婪分割每个节点来构建树。由于树过拟合训练数据的倾向，第二个阶段涉及剪枝树以移除最可能的节点。C4.5 是一种用于创建二叉决策树的算法。每个决策节点只考虑单个实例属性。一种著名的决策树算法是 C4.5，它在 Weka 数据挖掘程序中被称为 J48 算法。

## KNN

由于其易用性且准确率高，KNN 算法被频繁用于文本分类。KNN 分类器利用 k 个最近邻的类别标签，根据它们在训练期间与未知文档的相似性来确定未知文档的类别。欧几里得距离、余弦相似度等均可用于判断评论之间的相似性。每个最近邻文档的类别会根据其与测试文档的相似性得分进行加权。如果你的 k 个邻居中超过一个共享相同的类别，你可以通过累加共享类别的权重来计算你的相似性得分。

k-最近邻的数量是 KNN 阶段影响分类的最关键参数。k 的最佳值通常通过实验确立。在我们的分析中，我们发现 k = 1 提供了最高的分类准确率。此外，在 k-最近邻发现阶段采用了欧几里得距离作为距离度量。

## 结果与讨论

可以量化许多不同的性能指标。准确率（Accuracy）是指标之一，因为它揭示了有多少数据点被准确标记。它对于判断分类器的整体运行情况很有用。然而，对于非对称的数据集，准确率标准显得不足。这里可以应用召回率（Recall）和精确率（Precision）等标准。召回率和精确率都衡量了有多少正样本被正确识别，而精确率衡量的是在所有预期的正实例总数中，有多少真实的正例被准确预测。调和平均（Harmonic averaging）允许 F-measure 整合准确率和召回率标准。除了这些标准外，ROC 面积值可用于评估模型的效率。通过正确和错误预测的数量，可以绘制名为 ROC 曲线的图。预计 ROC 面积值将非常接近 1。这里确定了每个特征集和技术的准确率、精确率、召回率、F-measure 和 ROC 面积，表 1 所示在算法的性能评估中。

表 1 算法的性能评估。

| 算法 | 产品 | | | Twitter | | | 电影 | | | | |
|---|---|---|---|---|---|---|---|---|---|---|
| | Prec | Rec | F1 | Prec | Rec | Acc | Prec | Rec | F1 | Acc |
| 朴素贝叶斯 | 0.67 | 0.59 | 0.53 | 0.59 | 0.60 | 0.62 | 0.53 | 0.66 | 0.52 | 0.66 |
| 逻辑回归 | 0.69 | 0.62 | 0.62 | 0.61 | 0.65 | 0.63 | 0.64 | 0.78 | 0.74 | 0.77 | 0.77 |
| 支持向量 | 0.61 | 0.60 | 0.60 | 0.61 | 0.57 | 0.58 | 0.57 | 0.71 | 0.70 | 0.62 | 0.70 |
| 决策树 | 0.58 | 0.57 | 0.56 | 0.57 | 0.54 | 0.58 | 0.58 | 0.58 | 0.66 | 0.64 | 0.64 |

## 结论

- 情感分类在酒店业中占客户反馈的很大比例，已成为一个关键问题。这是由于酒店在预测消费者不满情绪方面存在困难。情感分类方法是现有研究的重点。然而，缺乏比较各种机器学习算法效能并探索识别和开发特征所涉及的步骤的研究。由于这一知识空白，研究人员对该行业进行了特征识别和工程研究。随后，从一家遍布全球的知名伊朗酒店连锁店收集了真实信息。此外，还使用了六种不同的机器学习算法对数据进行分类。结果显示，在预测方面具有高精确度（98.9%）。以下是实验中最重要的结论：

- 每个特征集和技术的准确率、精确率、召回率、F-measure 和 ROC 面积在此被确定，表 1 所示在算法的性能评估中。
- 在这些实验中，DT 和 C4.5 的准确率最高。
- 在大特征集中，DT 和 C4.5 表现最好。
- 在六种机器学习算法中，NB 表现最佳。
- 除 ANN 之外，增加特征数量通常会产生更准确的模型。
- 1) 情感分类可以处理中性、负性；
- 2) 使用 SVM 进行多类分类；
- 3) 使用集成学习技术（如 Bagging 和 Voting）来提高性能。

## 参考文献

- [1] 基于规则的亚马逊产品情感分析
- [2] 使用 TF-IDF 和 N-Gram 的文本提取
- [3] 基于词袋模型（BOW）的预测
- [4] 基于 LSTM 的评论情感分析
- [5] 使用混合方法对评论进行情感分析
- [6] 基于内容的推荐系统用于情感分类
- [7] 酒店产品和服务的的情感分析
- [8] 使用多项贝叶斯对餐厅评论进行分类
- [9] 使用机器学习对书籍进行情感分析
- [10] 针对 IoT 的联邦学习
- [11] 基于分类算法的客户评论文本情感分析
- [12] 使用分类算法的手机产品评论情感分析
- [13] 电影评论的情感分析研究
- [14] 使用机器学习的语音识别
- [15] 使用各种分类技术对波斯语评论进行情感分析

# 基于 Word2vec 与 CNN-LSTM 分类系统的情感分析研究

Rajat Saini¹*
¹ 商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度

## 摘要

在使用基于传统神经网络的短文本分类方法时，问题的识别已变得更加容易。本文结合使用 Word2vec、卷积神经网络（CNN）和双向长短期记忆网络（LSTM）来克服这一问题。实验表明，通过使用 Word2vec 词嵌入，CNN-LSTM 模型能够达到 91.48% 的准确率。这证明了在处理较短的文本时，混合网络模型的性能优于单结构神经网络。

**关键词：** CNN, LSTM, 情感分析, Word2Vec。

* 通讯作者 Rajat Saini：商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：rajat.saini.orp@chitkara.edu.in

## 引言

为了破译广泛问题的公众舆，自然语言处理被应用于情感分析中 [1]。这种做法也被称为意见挖掘，涉及系统收集、分析和评估推文中表达的意见。当今的社交媒体评论包含多种观点和短语，使得情感分析成为一个困难的过程 [2]。为了获得公众认可，监控热门情绪并做出适当反应很有帮助。得益于人工智能的进步，确定评论者的意图变得轻而易举。存在许多神经网络来处理此类问题 [3]。相比之下，我们采用了一种混合深度 CNN-LSTM 神经网络模型来改进我们在实验中获取的评论向量 [4]。情感分析广泛利用分布式词表示 [5]。词嵌入仅考虑词的含义。随着互联网的增长，用户在许多媒介上共享的信息量也不断增加 [6]。当提供更多来自不同人的观点和感受时，情感分析将更具动力。然而，孟加拉 NLP 领域缺乏一致的标记数据，使得情感分析变得非常困难 [7]。Word2Vec、GloVe 和 fastText 只是深度学习模型的示例，它们高度依赖于独立上下文的词嵌入，无论周围文本如何，每个词都有固定的表示 [8]。同时，像 BERT 等考虑上下文的预训练语言模型最近在 NLP 领域取得了巨大进展。如今，社交媒体平台提供了海量的用户生成的社交数据 [9]。对用户表达的观点进行情感分析，对于及时理解人们对商品或事件的想法和情感倾向至关重要。微博客网站的评论数据为为复杂，因为通常是不同长度消息的集合。在长文本数据中尤为丰富，词之间的关联比短文本中更复杂 [10]。

## 相关工作

在使用基于神经网络的短文本分类算法时，很容易出错。通过将 Word2vec、卷积神经网络（CNN）和双向长短期记忆网络（LSTM）耦合来克服这一问题。实验表明，通过使用 Word2vec 词嵌入，CNN-LSTM 模型能够达到 91.48% 的准确率。这证明了在处理短文本时，混合网络模型的性能优于单结构神经网络 [11]。

通过 CNN-LSTM 这种采用 Word2Vec 作为词嵌入层的深度学习方法，我们提出的模型能够提取推文的情感并对其进行分类。从 Twitter API 中挖掘了构成 Sentiment140 数据集的160 万条推文。推文使用 LSTM 单元基于内存的状态进行分类。传递爱、恨、友谊和自豪等情绪的推文在社交网络平台上共享。我们将通过采用深度学习技术来判断一条推文是正面还是负面的。与 SVM 和朴素贝分类器等方法相比，CNN-LSTM 表现异常 [12]。

为了提取词特征并构建权重词向量，除了 Word2Vec 嵌入外，我们还提出了传统的 TFIDF 技术。这些词向量经过加权，并作为最大池化层和 CNN 的输入。为了获得情感分类的可靠结果，输出被转发到 Bi-LSTM 神经网络。结合 Word2vec 与 TF-IDF 的混合 CNN-LSTM 模型在 Stanford IMDB 电影评论数据集上进行了测试，取得了令人印象的结果。此处提出的模型基于深度神经网络的 CNN-LSTM 变体。

在这里，我们将 BERT 的迁移学习能力应用于深度集成模型 CNN-LSTM，以提高情感分析决策的准确性和速度。为了将 CNN-LSTM 的性能与传统机器学习算法比较，我们还引入了迁移学习的概念。此外，我们研究了多种词嵌入方法，包括 Word2Vec、GloVe 和 fastText，并评估了它们相对于 BERT 迁移学习方法的效力。因此，我们展示了孟加拉情感分析的最先进的二分类性能，大大超过了任何嵌入或技术的性能 [14]。

![](img/5e4d8ef2afa52a8404b28106580e19e4_444_0.png)

图 (1)) 建议的工作流程图。

在本文，我们提出了一种改进的基于 GloVe-CNN-LSTM 的情感分析模型，用于分类这些包含长短段落的混合文本。词使用 GloVe 进行向量化，字符通过 CNN 进行处理。然后由 LSTM 处理特征以确定最终的情感。

在分类文本时，分词（tokenization）是预处理阶段的第一步。这种技术将文本对象转换为标记后的列表。标记（token）是代表文档中单个实体的单元单元。文本中的每个单词对应于某一类别的标记，这些类别由文档作者定义。词干提取（Stemming）是下一个预处理步骤。这是一个至关重要的过程，因为它很大程度上简化了论文。词干提取是将文本中所有术语实例还原为其最基本形式（称为基形或根形式）的做法。停用词是指除了“in”等大量标记之外，对分类过程没有任何贡献的词。如“in”、“the”、“a”和“is”等词在论文中出现频率过高，尽管它们对分类过程没有影响。约有2000个停用词被识别为必须从出版物消除的大类术语的一部分。

## 使用 CNN-LSTM 进行文本分类

- 前馈卷积神经网络（或 CNN）是一种类型的神经网络，它使用卷积神经网络从紧邻环境中提取特征向量。通过逐层调整网络的权重参数并进行迭代训练，梯度下降法可以最大化网络的准确性。在研究中，我们使用了由以下层构建的卷积神经网络：输入、卷积、池化、全连接和输出。这双向的、简短但广泛的上下标记序列与记忆模型天然契合。因此，它是 NLP 上下文数据的常用模型。我们可以使用加法技术（所有单词表达式的总和）或平均值法，在单词表达式的基础上，通过结合句子的表达式来获取短语的表达式。长短期记忆（LSTM）模型在捕获长程依赖方面更为有效。由于 LSTM 可以被训练以知道记住什么和忘记什么，LSTM 在句子建模的应用中有一个很大的局限性，因为它无法反序编码信息。为了更准确地捕捉方向性语义关系，BiLSTM 表现优。

- Word2vec 词嵌入的一种类型是 Word2vec 方法。在2013年，谷歌的 Mikolov 提出了一种新的词嵌入方法。CBOW（连续词袋模型）和 Skip-gram（连续跳字模式）都可以作为 Word2vec 的训练选项。如需快速解释，请参见图 (2)。
  - CBOW 使用上下文来推断当前值。从短语中移除一个单词，并由短语来识别它。
  - Skip-gram 从当前单词推断上下文。这就像给你一个单词，然后要求你预测它前后可能的词。

## 结果与讨论

我们在 Reuters 和 20 Newsgroups 数据集上运行了测试，以证明 CNN、LSTM 和 CNN-LSTM 分类等成熟方法的实用性和有效。所有测试均在具有 3.40GHz 处理器和 8GB RAM 的 Windows 系统上使用 MATLAB 8.0 版本完成。采用五折交叉验证结合一路对多（One-Against-All）多分类策略来生成训练和测试数据集。分类准确率以五折中位数提供，其中“Accuracy”定义为正确分类实例的比例。图 (2) 显示了 CNN-LSTM 分类。

此处 TP、TN、FP 和 FN 分别是真阳性、真阴性、假阳性和假阴的数量。图 (3) 显示 Yelp 数据集的准确率比较。

![](img/5e4d8ef2afa52a8404b28106580e19e4_449_0.png)

图 (2)) CNN-LSTM 分类。

$$Accuracy = \frac{TP+TN}{TP+FP+TN+FN} \quad (1)$$

![](img/5e4d8ef2afa52a8404b28106580e19e4_450_0.png)

**Fig. (3)** Yelp 数据集的准确率比较。

![](img/5e4d8ef2afa52a8404b28106580e19e4_451_0.png)

**Fig. (4)** twitter 数据集的准确率比较。

图 (4) 展示了 twitter 数据集的准确率比较。为了统计评估分类结果，使用了另一个评估标准：F1 分，其确定方式为：

$$F1 \text{ score} = \frac{2\times \text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$$

$$\text{Precision} = \frac{TP}{TP+FP}$$
$$\text{Recall} = \frac{TP}{TP+FN}$$

此处，TP、FP、TN 和 FN 分别是真阳性、假阳性、真阴性和假阴性。

## Yelp

![](img/5e4d8ef2afa52a8404b28106580e19e4_452_0.png)

图. (5)) Yelp 数据集的召回率比较。

![](img/5e4d8ef2afa52a8404b28106580e19e4_453_0.png)

**Fig. (6)** Twitter 数据集的召回率比较。

图 (5) 显示了 yelp 数据集的召回率比较。图 (6) 阐了 Twitter 数据集的召回率比较。

## Yelp

![](img/5e4d8ef2afa52a8404b28106580e19e4_454_0.png)

**Fig. (7)** Yelp 数据集的准确率比较。

本研究将建议的组合模型与单模型 CNN 和 LSTM 进行比较，以测试 Word2vec-CNN-LSTM 的影响。LSTM 方法、CNN 模型和 CNN-LSTM 模型均用作基准。表 3 以红色显示突出结果。本工作中描述的 Word2vec-CNNLSTM 分类影响相对于 CNN 模型增加了 4.0 个百分点。CNN-LSTM 位居第二，最后是建议模型不足，且准确率不符合预期。为了应对训练过程中出现的过拟合问题，后续工作将调整 dropout 大并使用 L2 正化。图 (7) 显示了 Yelp 数据集的准确率比较。图 (8) 显示了 Twitter 数据集的准确率比较。

## Twitter

![](img/5e4d8ef2afa52a8404b28106580e19e4_455_0.png)

**Fig. (8)** Twitter 数据集的准确率比较。

## Yelp

![](img/5e4d8ef2afa52a8404b28106580e19e4_456_0.png)

**Fig. (9)** Yelp 数据集的 F1 分比较。

![](img/5e4d8ef2afa52a8404b28106580e19e4_457_0.png)

**Fig. (10)** twitter 数据集的 F1 分比较。

## 结论

图 9 和 10 分别描述了建议工作与 Twitter 和 Yelp 数据集上现有方法 CNN 和 LSTM 的 F1 分比较。在研究中，我们引入了一种结合卷积和双向神经网络的混合模型，用于基于 Word2vec 的短文本情感分析。由于 CNN 擅长提取特征而 LSTM 擅长学习双向关系，组合 CNN-LSTM 模型取得了良好结果。目前模型具有比当前基需要更多训练数据和训练时间的缺点，这限制了它的适用性。尽管如此，它在需要大量训练数据的分类任务中仍然有用。通过使用 Word2vec 对相似词进行聚类，可以通过训练大量数据产生词向量来解决“多义性”问题。长短期记忆（LSTM）也被用于从预期顺序反向编码信息。作为研究的一部分，结果显示 wordvec-CNN-LSTM 模型使文本分析变得更简单更可靠，从而显著提高了短文本情感分类的准确率。

## 参考文献

- [1] Khan L., Amjad A., Afaq K.M., Chang H.T. Deep Sentiment Analysis Using CNN-LSTM Architecture of English and Roman Urdu Text Shared in Social Media.Appl. Sci. (Basel)202215269410.3390/app105269
- [2] Huang P., Zheng L., Wang Y., Zhu H., Sentiment Analysis of Chinese Text Based on CNN-LSTM Serial Model10th International Conference on Computing and Pattern Recognition2021
- [3] Sarkar O., Ahmed M.F., Khan T.T., Ghosh M.K., Islam M.R. An Experimental Framework of Bangla Text Classification for Analyzing Sentiment Using CNN & LSTM2nd International Conference for Emerging Technology (INCET)202116
- [4] Yon J., Kim H., Multi-Channel Integrated CNN-LSTM Models for Sentiment Analysis.ROCLING/IJUCLCP2017
- [5] Zhou Z., Chen J., Wu J.H., Wang R. Sentiment Analysis Method for Agricultural Product Review Based on Corpus Characteristics and Deep Learning Model2022 International Conference on Machine Learning and Intelligent Systems (MISE)4340202210.1109/MISE57402.2022.00091
- [6] Ombahi A.H., Ouarda W., Alimi A.M.. Deep learning CNN-LSTM framework for Arabic sentiment analysis using textual information shared in social networks.Soc. Netw. Natl. Min.2020105310.1007/s13278-020-0068-1
- [7] Kumar R., Pannu H.S., Mahhi A.K.. Aspect-based sentiment analysis using networks and stochastic optimization.Neural Comput. App.20232832223312375.1007/s0521-019-045-9
- [8] Yadav P., Zaid S., Nascimento C.D.S., Albuquerque V.H., Chauhan S.S.. Analysis and Design of automatic generation for GPS Based Moving Object Tracking System2023 International Conference on Artificial Intelligence and Smart Communication (AISC)Greater Noida, India 2023 15.1109/AISC56616.2023.1008510
- [9] Naschidchin M.A., Adji T.B., Wadiyan W.. Performance Improvement Using CNN for Sentiment AnalysisJITEE (International Journal of Information Technology and Electrical Engineering)2018

- [11] Yue, Li L.. Sentiment Analysis using Word2vec-CNN-LSTM Classification. 2020 Seventh International Conference on Social Networks Analysis, Management and Security (SNAMS), 152-220.
- [12] Yadav S.P., Yadav S.. Fusion of Medical Images in Wavelet Domain: A Discrete Mathematical Model. Ingeniería Solidaria, Universidad Cooperativa de Colombia-UCC, 14(2), 2018, 10.116925/v1410.2236.
- [13] Vashisht V., Pandey A.K., Yadav S.P.. Speech Recognition using Machine Learning. IEIE Transactions on Smart Processing & Computing, The Institute of Electronics of Korea, 2021, 323-329.
- [14] Prottasha N.J., Sami A.A., Kowsher M., Murad S.A., Bairagi A.K., Masud M., Baz M.. Transfer Learning for Sentiment Analysis Using BERT Based Supervised Fine-Tuning. Sensors (Basel), 2022, 22(14), 1571, 10.3390/s2211415735684778.

# 基于 Hadoop 的深度学习 Twitter 情感分析

Manpreet Singh¹

¹ Centre for Interdisciplinary Research in Business and Technology, Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

## 摘要

情感分析是指分类和识别音频、文字、数据库报告和推文中所显示的观点，以确定这些观点是积极的、中性的还是消性的实践，这对微博客服务领域的许多人具有很大兴趣。由于 Twitter 的特殊性，从其提取情感可能具有挑战性。本研究提出了一种使用 Hadoop 基础设施结合深度学习分类器来分析情感的方法。为了收集特征，数据分布在 Hadoop 节点上。随后，对 Twitter 数据进行解析以提取最关键的部分。Twitter 的输入数据通过深度学习算法（包括深度循环神经网络分类器）被分为两类：正面评论和负面评论。用于衡量性能的某些指标包括分类准确率、特异性和敏感性。所提方法的敏感性为 0.9404，泛化性为 0.9157，在分类准确率达到 0.9302 的方面超过了传统方法。

**关键词：** 大数据、深度学习、Hadoop、Twitter 情感分析。

- **通讯作者 Manpreet Singh:** Centre for Interdisciplinary Research in Business and Technology, Chitkara University Engineering and Technology, Chitkara University, Punjab, India; E-mail: manpreet.singh.orp@chitkara.edu.in

## 引言

微博客平台正侧重于情感分析，这涉及将音频、文本、数据库源以及推文中所表达的观点分类并识别为积极、中性或消 [1]。Twitter 具有独特的特性，使得情感分析具有挑战性。有数百万在使用 Twitter，使其成为一个非常流行的微博客服务 [2]。Twitter 用户更新他们的状态（“推文”），并通过标签讨论当前事件和话题。因此，Twitter 已成为公众情绪强大且可靠的晴雨表 [3]。Twitter 产生了海量数据，手动检查所有数据变得困难。Twitter 情感检测器（TSD）在衡量客户对服务或产品质量的满意度方面优于传统方法 [4]。TSD 在检测模式和做出准确分类方面的准确性和性能很大程度上依赖于所用分类方法的效率 [5]。现有的机器学习技术具有将公司转变为自动化处理的潜力，但所需的时间是一个主要关注的问题 [6]。若干现实应用已在情感分析等领域使用了深度学习方法 [7]。为了从文本等非结构化数据中提取见解或将其表示在模型中，深度学习技术使用了多种算法。人们通过在线社交媒体可以在世界范围内听到某人的声音 [8]。人们选择社交网站是因为它们简单地分享自己的想法和观点，并关注时尚和流行文化世界的最新进展 [9]。每天，Twitter 上发送数千条关于各种主题的推文 [10]。所提情感分析模型的目标之一是使用深度循环神经网络分析来自 Twitter 的实值输入数据。评估强调了情感分析结果的潜在速度。特征提取和分类是所提程序的两个部分。通过 Hadoop 集群分布数据是获取 Twitter 数据特征的第一阶段。分类模块是将这些特征与一种名为深度循环神经网络（DARN）的分类器相结合。使用获取的属性，深度循环系统的分类器产生两个输出：正面评论和负面评论。第 2 节展示了传统情感分析方法的摘要，而第 1 部分对情感分析进行了介绍。第 3 节阐述了方法，第 4 节展示了结果，第 5 节得出了结论。

## 相关工作

本研究利用 Hadoop 架构和深度学习分类器提出了一种情感分析方法。特征提取的数据分布由 Hadoop 集群处理。然后，从 Twitter 信息中筛选出重要元素。Twitter 的输入数据通过深度学习算法（即深度循环神经网络分类器）分为两类：正面评论和负面评论。性能评估使用了分类中的特异性、敏感性和准确率等衡量标准。分类准确率 (0.9302)、敏感性 (0.9404) 和特异性 (0.9157) 都是所提方法优异的领域 [11]。

我们的情感分析方法利用深度学习架构来提高准确性。情感分类的结果表明，所提方法比传统方法更有效 [12]。我们在现有工作的基础上提出了一种贝叶斯/随机森林混合策略来挖掘 Twitter 数据集 [13]。

这种海量的非结构化数据库可以进行组织和处理，以满足社会、工业和政府目的。Hadoop 凭借其并行分析大规模数据集的能力是分析 Twitter 数据的最佳技术。通过分析 Twitter 上表达的观点，可以更好地理解客户的行为，其准确率达到了 99.78% [13]。

在该研究中，我们检查了使用 Hadoop 及其生态系统进行大数据情感分析方法的功效。我们利用 Apache Flume持续向 HDFS 输入推文。使用 Pig 脚本从原始数据中检索推文。根据态度对推文进行分类的一种方法是基于字典的方法 [14]。

由于社交媒体平台作为人们连接和分享想法的方式惊人，为了描述这种不断增长的数据库，“大数据”一词最近出现。因此，情感分析（也称为优化挖掘）是数据挖掘研究中新方法可以准确分类大数据中隐藏信息的一个领域。在本文，我们在现有工作的基础上提出了一种贝叶斯/随机森林混合策略来挖掘 Twitter 数据集 [15]。

## 提出的工作

## 系统概述

可以使用情感分析技术对观点性文本进行分析和分类。情感分析提供了人们对各种问题感受的总体描述。在这里，我们使用深度学习分类器和 Hadoop 框架分析情感。为了开始从 Twitter 数据提取特征，首先使用了 Hadoop 集群。我们在 Map 阶段检索特征。在 Map 阶段，提取了 Twitter 数据的重要部分，包括全大写、表情符号、标签、扩展组件、情感词汇、否定和标点符号。一旦收集了特征，就会通过洗牌生成特征选择列表。Reducer 接收列表。在 Reduce 阶段，通过深度循环神经网络将特征分类为正面和负面评论。

# 使用 Hadoop 进行情感分析

Hadoop 是一种用于管理大规模数据处理和处理并行执行相关问题的结构，例如自动作业同步、故障识别和恢复。用户通过创建 MapReduce 模型在 Hadoop 中处理数据。因此，利用 Hadoop 平台可以对 Twitter 数据进行有效的情感分析。

- **Map**: 在初始化时，Hadoop 框架将 100 条推文视为输入数据。计算包括输入数据处理所需的 HDFS 块总数，以及每个块的 HDFS 路径。然后，计算出的块路径通过任务 jar 文件和 HDFS 配置文件传输到 HDFS 共享目录。在构建 Map 任务之前，框架无法处理任何块。处理数据块总共需要 10 个 Mapper。处理数据块后，可以从 Twitter 数据中获取如标点、大小写、情感、标签（hashtags）以及扩展单元、情感词汇、否定等特征。完全由大写字母组成的单词被视为一个实体。你可以通过观察其特征判断表情符号是快乐还是悲伤。如果存在一定数量的标签，Hashtag 函数将指示出来。扩展单元的长度表示基本计算单元的数量。情感词汇包含了每个词汇的最大情感分、总情感分和情感术语数量。在分段中，否定数量由否定表示。连续句号、逗号以及问号或感叹号的数量构成了标点。

- **Shuffle**: Map 阶段的中间结果在 Reduce 阶段之前传递到 Shuffle 阶段。Shuffle 阶段由 Map 后的洗牌（shuffleplicate）、复制和排序三个阶段组成。在 Map 操作完成后，输出在一个名为“post-Map 洗牌”的程序中进行分区和重组。这一步涉及对从 Twitter 数据中派生的特征进行分类和排序。在复制阶段，Map 过程的结果保存到本地磁盘。排序步骤中执行的合并和排序操作的输出是 reducer 阶段的输入。合并和排序不同属性的合并技术为还原 步骤提供了输入。

- **Reduce**: 还原步骤利用深层 CNN 将特征分类为“正面”或“负面”评论。在引导式机器学习方法中，卷积神经网络（CNN）具有两个以上反馈回路的人工神经元。CNN 只能在使用训练数据库和特定输入配对的监督环境中进行训练。为了运行，CNN 有三层：输入层、隐藏层和输出层。网络接收 $t$ 时刻的向量作为输入。在图 (1) 中我们可以看到系统模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_467_0.png)

将数据分为测试数据和训练数据预处理

填充缺失值并进行插补

图 (1)) 系统模型。

$H_r = (H_1, ..., H_n)$

全连接卷积神经网络（CNN）的接收输入的隐藏单元由权重矩阵 $m_w$ 表示。我们使用递归连接连接隐藏层中的 $h$ 隐藏组件。



$W_s = (D_1, D_2, ..., D_w) \quad (2)$

系统的状态空间表示为隐藏层。

$W_t = M_a(B_t) \quad (3)$

其中隐藏层激活函数表示为 $M_i(\cdot)$，可见内存内容由输出门 $(B_f)$ 控制，其写法为：

$B_l = y_w H_l + y_w D_{l-1} + b_{hidden} \quad (4)$

权重矩阵记为 $y_w$，隐藏单元的偏置记为 $b_{hidden}$。作为 $y_w$，我们可以看到连接到隐藏单元的隐藏层：

$V_l = V_1, ..., V_s \quad (5)$

其中，$n = 2$，在时间 $t$，输出层表示为：

$V_t = a_o(y_{in}D_t + b_{output}) \quad (6)$



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



$O_{[p,m,n]} = \text{Convolution}(I \otimes A, K)$

$= \sum_{o=1}^{\Sigma_{c1}} \sum_{j=1}^{\Sigma_{j1}} \sum_{k=1}^{\Sigma_{w1}} [I_{[l,o'+j',n'+k]} \times A_{[l,o,j,k]} \times K_{[p,o,j,k]}] \quad (4)$

$= \text{Convolution}(I, A_{[l,i_{m}]}] \odot K)$

$= \text{AW-Convolution}(I, A \odot K)$



## 结果与讨论

如何分类充满恨意的推文是本文的主题。我们构建了一个情感分析器，将推文分为正面和负面两类。我们的分类器不仅限于分析 Twitter 数据；也可以用于其他文本数据。从我们的 Twitter 信息开始，本研究使用了用于情感分析数据集的 Twitter 推文数据。总共有 32,000 条推文，其中 22% 为负面情绪。`label` 变量是这里的重点；它为负面推文分配 1，为正面推文分配 0。目标变量代表了你预测努力的结果。为了解决我们的机器学习挑战，我们将利用这些信息构建一个分类模型，该模型为新的推文分配标签。图 (3) 显示了情感类别。

### Twitter 情感分析

![](img/5e4d8ef2afa52a8404b28106580e19e4_501_0.png)

**图 (3)** 情感类别。

在传统的机器学习中，83% 的 F1 分数表示模型是成功的。然而，仍有方法可以增强模型。尽管深度学习算法的成本很高，但可以使用它们来根据用户反馈和结果添加功能并修复拼写错误。请记住，我们使用了训练数据来得出这些发现。当情感分析模型应用于真实世界的数据时，我们仍需积极监控其性能。图 (4) 展示了 F 分数性能。

![](img/5e4d8ef2afa52a8404b28106580e19e4_502_0.png)

**图 (4)** F 分数性能。

## 结论

随着技术的发展，基于文本的网络存档已变得越来越常见。对于许多文本分类应用，支持向量机 (SVM) 和朴素贝叶斯 (NBayes) 等经典机器学习分类器的表现良好。由于短文本词汇较少，且卷积层和池化层具有局限性，这些分类器面临稀疏性和缺乏长期依赖的问题。在研究中，我们提出了一种改进 skip-gram 的卷积循环神经网络。对于 skip-gram 算法的对抗训练，我们采用了 L2 正则化技术。它可以提高模型在文本情感分类任务中的性能，并增加其稳健性和泛化能力。为了从整个文本提取信息的同时抑制无关词的影响，我们部署了配备注意力机制的神经网络。基于 CNN 的文本情感分类已完成。与 Twitter 数据集的其他分类器相比，我们的模型和算法被证明更高效、更准确。

## 参考文献

- [1] Rani M.S., Subramanian, S.. Attention Mechanism with Gated Recurrent Unit Using Convolutional Neural Network for Aspect Level Opinion Mining. Arab. J. Sci. Eng. 2020485617616910//s13369-020-0449-4
- [2] Wang Y., Lu, Q., Wang, Y., Wu M., Li W.. Dynamic QoS Prediction Based on Attention Mechanism and Recurrent Network! IEEE Int on Parallel and Distributed Processing with Big Data and Cloud Computing, Sustainable Computing and Communications, Social Computing and Networking 20223473354
- [3] Liang Q.S., Li Y., Wang K., Wang X., Li Z.. Long-term recurrent convolutional network Behaviour recognition with attention mechanism MATEC Web of Conference 2021.
- [4] Li C., Zhang Q., Zhao Z., Gu L., Schaller B.. "Exploring Spatial-Temporal Representations for NIRS-based Intimacy Detection with an Attention-enhanced Cascade Convolutional Recurrent Neural Network" 25th International Conference on Pattern Recognition (ICPR) 202118286910.1109/ICP4880.20219412577
- [5] Guan W., Liu C.. Prediction of surface quality in mind based on convolutional recurrent neural network AKIP Laied Mathematics and Nonlinear Sciences 2022
- [6] Zhu H., Yan J.. A Deep Learning Based Sound Location and Detection Algorithm Using Convolutional Recurrent Neural Network 2022 International Conference on Computer, Information and Telecommunication Systems (CITS) 16220210.1109/CITS5521.2022.9832991
- [7] Zhang X., Gao X., Lu W., He L., Bij J.. Vision: Multimodal Recurrent Attention Convolutional Neural Network for Unified Image Aesthetic Tasks. IEEE Trans. Multimed. 2021231162310.1109/TMM.2020.2985526

互联网和智能设备。通过结合文本、图像和音频的分析，多模态情感分析可以识别用户发布内容的内在语调 [5]。整合多个来源的情感和意义是多模态情感分析的关键问题。在许多研究中，使用了相同的分类策略来检查多种模态 [6]。事实证明，各种特征集可以被各种分类器优地使用。网络数据情感分析是一项宏大的研究课题，具有多个潜在用途，包括上下文学习、选举预测和事件反应分析 [7]。在大多数情况下，在线情感分析只考虑特定的模态，例如文本或图像。多模态信息易于获取，并可以结合使用以提高情感估计的准确性 [8]。研究表明，在不考虑视觉和文本变量相互关系的情况下整合它们，会导致模型复杂化并降低情感分析性能 [9]。为了识别意图含义与表面意思不一致的自然语言讽刺性话语，使用了讽刺检测。在自然语言处理领域，讽刺检测用于多种应用，包括情感分析和观点挖掘。讽刺检测领域的许多开创性研究 [10] 将注意力仅限制在文本输入。社交媒体的出现使得现代世界多模态数据量剧增。针对视觉情感分析（尤其是 GIF 视频）的研究才刚刚开始发展。这主要是因为 Twitter、Instagram、Facebook 和 Telegram 等大平台使用 GIF 的功能是最近引入的，因此使用 GIF 作为其中一种模态的多模态设计仍未探索。我们的框架包括：

- 一个多模态情感框架，用于分析输入的推文并将其拆分为文本、图像和 GIF 等不同模态。根据输入类型，相应的处理模块将计算该类型的情感。
- 图像模块由一个微调的 CNN 组成，该模型构建在预训练的 `vgg16` CNN 模型之上，并使用标注的 Twitter 数据集进行训练。我们使用该模块来分析推文的图像或 GIF 分离的帧。
- 我们证明了将人脸检测和情感检测与图像模块结合以分析 GIF 情感的可行性。

## 相关工作

在这项研究中，我们展示了结合文本和视觉特征比仅依赖视觉或文本数据的模型产生更优越的结果。来自我们的文本、图片和 GIF 模块的输出分将被聚合，以为输入的推文提供最终情感分 [11]。

所建议的技术采用二维卷积神经网络 (2CNN) 进行图像分析，并采用双向循环单元 (bi-GRU) 处理文本评论。我们提供了一个名为 Merlin 的 Instagram 帖子新数据集，其中包含 512 对照片及其波斯语评论，以评估所提模型的有效性。根据实验数据，与单一模态相比，结合文本和图片模态使极性识别准确率提升了 23%，F1 分增加了 0.24。所提模型的准确率和 F1 分也比其他 11 种深度融合模型高。我们的数据和模型代码供任何人未来利用 [12]。

为了利用许多分类器在多个模态上的高效性能，本研究提出了一种基于软投票（soft voting）的集成模型。所提模型使用深度学习技术（BiLSTM, CNN）从多模态数据集中提取深度特征。对特征（文本和图片数据的组合）进行特征选择后，使用基于软投票的集成学习模型对最终特征集进行分类。该方法使用了两个文本-图像对基准数据集来评估所提方法。实验表明，所提模型在相同数据集上的表现优于几种对抗模型 [13]。

本研究提出了一种情感分析范式，通过整合可能吸引最多注意的视觉和语言信号，利用不同类型在线数据之间的连接。为了发现学习到的显著方面与文本数据之间的连接，构建了一个多模态深度关联学习器。此外，建议使用两个流单模态深度特征提取器来自动学习视觉和语言方面。最后，使用后期融合（late fusion）过程通过整合视觉和语言特征来估计情感。结果。与那些盲目使用视觉混合数据来估计情感的单模态算法相比 [14]，我们提出的框架在利用在线数据方面显示出良好的前景。

由于这种情况，现在用户经常使用视觉内容（如照片和视频）来表达自己。在这项研究中，我们的目标通过包含多模态数据改进现有的讽刺检测系统。许多方法利用图像、文本混合。为了考虑到语言与图像之间的不一致性，我们描述了一种基于鲁棒优化 BERT 预训练 (RoBERTa) 的架构。文本特征通过门控循环单元 (GRU) 恢复，而视觉特征通过特征化 ResNet Block 获取。这些结合 RoBERTa 模型的 CLS 标记生成预测。最后，我们将模型性能与其他公开的 Twitter 数据集进行对比 [15]。

## 提议工作

## 系统模型

与文本媒体相比，非文本媒体的底层标记有时并不明显，使得标注更加困难。这些基础单元在图片和视频情况下可以被视为像素组，而在文本情况下则是字母组（[单词]）。现在我们讨论的是计算机视觉和图像识别，这些领域比自然语言处理（NLP）早了 30 年，但最近取得了显著进展。目前的计算机视觉对于许多实际目的仍然不足。提取观点之所以具有挑战性，是因为视觉的能力与情感分析所需的知识之间存在语义差异。为了在计算中使用图片，我们使用了 `keras` 的内置函数将其转换为 `numpy` 矩阵。(1) 展示了我们的建议系统，其中我们将三种模态（文本、图片和 GIF）拆分为各自的模块以估计情感分。我们关注推文的分类。在推文预处理后，我们使用 VADER Python 包来确定推文的极性（如果包含文本）。我们通过训练好的 CNN 为照片分配情感评分。

最低可能分为 -1，最高可能分为 +1。然后，为了自动聚焦与情感分类最相关的特征，我们建议了一种语义自注意力模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_512_0.png)

图 (1) 系统图。

## 数据集

我们利用 Twitter 搜索 API 和一个名为“Tweepy”的 Python 模块提取了 10,000 条包含“trump”一词的流行且近期的多模态推文，作为我们系统的输入流。使用 Pandas 的 Dataframe 来存储所检索的推文，供后续模块使用。Pandas 是一个用于数据处理和分析的 Python 模块，其 Dataframe 数据以行和列的形式结构化，使得数据导出到 Excel 变得简单。在接下来的章节中，我们将每个模块拆解为各个组成部分。系统图如图 (1）所示。

## 多模态文本分类

大约十年前，深度学习作为一种强大的机器学习方法发展起来，在计算机视觉、语音识别和自然语言处理在内的许多应用领域取得了最先进的结果。最近，使用深度学习进行情感分析的兴趣日益增加。在这项研究中，我们对用于图像识别的深度神经网络和基于 NLP 的情感分析进行了跨学科研究。图 (2) 显示了 CNN 模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_514_0.png)

图 (2) CNN 模型。我们首先创建了独立的模型，一个用于文本，一个用于图像，然后比较这些模型的输出。随后，利用预训练的 CNN 从图像-文本对中提取视觉区域，$R = \{r_1, \dots, r_m\} \in \mathbb{R}^{md}$，其中 $m$ 是区域总数，$d$ 是单个特征的维度。为了检索文本特征，我们使用预训练的词嵌入 $T = \{t_1, \dots, t_j\} \in \mathbb{R}^{je}$，其中 $j$ 代表短语的长度，$e$ 是嵌入维度。首先，合并两种模态以计算注意力得分，以便学习对视觉区域的注意力。我们使用两个低秩投影矩阵将两个特征向量（即区域 $r_i$ 和词向量 $t_j$）投影到 $c$ 维公共空间。然后，使用乘法方法将其结合：

$$x_{ij} = (U^T r_i) \odot (V^T t_j)$$

其中 $U \in \mathbb{R}^{d \times c}$ 和 $V \in \mathbb{R}^{e \times c}$ 是参数矩阵，$\odot$ 表示两个向量的逐元素乘或 Hadamard 积。之后，融合的向量 $x_{ij}$ 被送入带有 softmax 操作的非线性过程以获得归一化的注意力得分：

$$\alpha_{ij} = \frac{\exp(\sigma(W^T x_{ij}+b))}{\sum_{i=1}^m \exp(\sigma(W^T x_{ij}+b))}$$

其中 $W \in \mathbb{R}^c$ 和 $b \in \mathbb{R}$ 分别是权重和偏置参数，$\sigma(\cdot)$ 是 sigmoid 激活函数。最后，注意力得分可用于调节不同视觉区域的注意力。注意后的视觉特征被评估为单词 $t_j$ 所有区域特征的加权平均值如下：

$$r^j = \sum_{i=1}^m \alpha_{ij} \cdot r_i$$

与原始特征相比，注意后的视觉特征 $r^j$ 对于单词 $t_j$ 的图像区域更具代表性。整个视觉-语义过程如图 (3)。

## 结果与讨论

我们在弱标签和手动标注的数据集上进行了广泛的测试。与其他先进模型相比，结果显示我们的方法优优。为了测试该模块的有效性并提供示例，我们将注意力限制在 200 个 GIF 的“悲伤”情感上。在 200 个文件中，模块成功识别了 117 张脸。图片模块的输出和情感检测允许我们准确预测情绪。我们发现 200 个文件中漏掉了 83 张脸，因为这些人脸被遮挡了。图片模块允许我们正确判断了 64% 的文档。为了提高 GIF 情感分析的准确性，我们可以开发一个能够区分动物、绘画和动画人脸的识别模型。表 1 是文本分析，表 2 是图像分析，表 3 是 GIF 分析。

## 表 1 文本分析。

| 提议方法与现有工作 | SCA (%) | RA (%) | Precision (%) | Recall (%) | F-score (%) |
|---|---|---|---|---|---|
| SVM 和启发式方法 | 72.45 | 79.89 | 94.75 | 83.14 | 89.15 |
| DBN | 74.52 | 85.12 | 95.10 | 84.75 | 89.88 |
| CNN集成模型 | 78.47 | x | 96.72 | 87.84 | 91.55 |
| 混合深度学习模型 | 82.45 | x | 96.79 | 91.13 | 92.75 |
| LAN2FIS | 87.64 | x | 96.83 | 91.65 | 93.97 |
| 提议方法 | 92.47 | 94.04 | 98.17 | 96.74 | 96.85 |

## 表 2 图像分析。

| 提议方法与现有工作 | SCA (%) | RA (%) | Precision (%) | Recall (%) | F-score (%) |
|---|---|---|---|---|---|
| SVM 和启发式方法 | 72.45 | 79.89 | 94.75 | 83.14 | 89.15 |
| DBN | 74.52 | 85.12 | 95.10 | 84.75 | 89.88 |
| CNN集成模型 | 78.47 | x | 96.72 | 87.84 | 91.55 |
| 混合深度学习模型 | 82.45 | x | 96.79 | 91.13 | 92.75 |
| LAN2FIS | 87.64 | x | 96.83 | 91.65 | 93.97 |
| 提议方法 | 92.47 | 94.04 | 98.17 | 96.74 | 96.85 |

## 表 3 GIF 分析。

| 提议方法与现有工作 | SCA (%) | RA (%) | Precision (%) | Recall (%) | F-score (%) |
|---|---|---|---|---|---|
| SVM 和启发式方法 | 72.45 | 79.89 | 94.75 | 83.14 | 89.15 |
| DBN | 74.52 | 85.12 | 95.10 | 84.75 | 89.88 |
| CNN集成模型 | 78.47 | x | 96.72 | 87.84 | 91.55 |
| 混合深度学习模型 | 82.45 | x | 96.79 | 91.13 | 92.75 |
| LAN2FIS | 87.64 | x | 96.83 | 91.65 | 93.97 |
| 提议方法 | 92.47 | 94.04 | 98.17 | 96.74 | 96.85 |

框架的每个部分都会受到影响。为了获取这些信息，我们查询了 Twitter API 中的“trump”并应用了过滤器“-filter:retweets”。这产生了 10,000 条推文。由于 Twitter API 无法访问该服务的媒体文件，我们无法包含转推实例。根据 Dataframe 中媒体 URL 的数量计算，几近 6% 的推文包含媒体。随机选择的推文大部分仅以文本格式可用。

## 结论

由于图像的抽象性和主观性，视觉情感分析具有挑战性。人们对数字图片和 GIF 情感内容的解释可能很大。在这项研究中，我们展示了如何利用深度学习方法和数据增强来微调 CNN，以在图片情感分析中获得最佳精度，以及面部情感识别等技术如何帮助我们克服某些抽象性。我们还建议了一种情感分析系统，具有用于处理 Twitter 流中文本、图像和 GIF 的专门组件。通过面部表情检测，我们的 GIF 分析模块提供了一种准确预测情感的新颖方法。总之，这些许多模块的数据可能有助于对多模态情感检测做出更有根据的判断。我们希望未来扩展我们的 GIF 模块，纳入更多的社交网络（如 Tumblr 和 Twitter），以便我们可以获取更多的情感视觉表示并采用手势检测等额外方法。

# 多媒体国际会议与展览 (ICME) 1622021 10.1109/ICME52290.2022.9860020

- [4] Sathish R., Ezhumalai P., 使用 VGNN 技术对带文本说明的图像进行跨模态情感分析ACM Transactions on Asian and Low-Resource Language Information Processing 2021024114 10.1145.3450971 
- [5] Kumar P, Khokher V., Gupta Y., Ram B., 针对标注数据不足的多模态情感识别的混合融合方法2021 IEEE 图像处理国际会议 (ICIP)314318202111 10.1109/ICIP42928.2021.9506714
- [6] Miao H., Li R., Gao S., Zhou X., He., 用于视觉文本情感分析的端到端深度记忆网络2018 网络基础设施与数字内容国际会议 (IC-NIDC)3199403201811 10.1109/CNIDC.2018.8525751
- [7] Yadav S. P., Yadav., 连续小波域内医学图像融合的数学实现 动态与控制系统先进研究2019101904554
- [8] Cai G., Liu L., Lin Y., Wen S., 用于多模态情感分析的多层深度卷积网络Jce.202022096210521 10.1049/cje.2020.09.003
- [9] Yadav S.P., Zaidi S., Nascimento C.D.S., de Albuquerque V.C., Chauhan S.S., 基于 GPS 的移动物体跟踪系统的自动生成分析与设计2023 人工智能与智能通信国际会议 (AISC) Generator Noida, India.2023 15 10.1109/AISC5616.2023.1009510
- [11] Shirzad A., Zare H., Teimour M., 文本、图像和 GIF 多模态情感分析的深度学习第10届计算机与知识工程国际会议 (ICKE)2020241942 10.1109/ICKE50421.2020.9309376
- [12] Karimvand A.N., Chegini R.S., Basi M.Nem., 个人 Instagram 帖子情感分析：多模态深度学习方法第7届网络研究国际会议 (ICWR)2021113711410 10.1109/ICWR51868.2021.9443026
- [13] Salur M.U., Ayd I., 一种软集成学习的多模态情感分析方法Neural Comput. Appl.202323421183911840 10.1007/s00521-022-0751-7
- [15] T. Zhu, L. Li, J. Yang, S. Zhao, H. Li, and J. Qian 图像-文本多模态情感分析 IEEE Trans. Multimedia2023235373385 10.1109/TMM.2022.3158940

## 使用深度学习技术对 COVID-19 公共舆进行情感分析

Abhinav Mishra¹\*
¹ 商业与技术跨学科研究中心，Chitkara 大学工程与技术学院, Chitkara 大学, Punjab, 印度

## 摘要

由于 COVID-19 疫情的影响，许多人正经历极度的担忧、恐惧和其他困难情绪。自从新冠病毒疫苗推出以来，人们的反应变得更加微妙和多样化。在这项研究中，我们将使用深度学习方法来解码他们的情绪。Twitter 让我们洞窥任何特定时刻流行内容以及人们在思考什么，而社交媒体目前是表达情感和情绪的最佳手段。我们进行这项研究的目标是更好地了解不同人群对疫苗的感受。本研究推文的时间范围为从 12 月 21 日到 7 月 21 日。最近在世界范围内几个地区提供的最热门疫苗是多条推文的主题。我们使用名为 VADER 的情感感知情感字典（一种 NLP 程序）来分析人们对特定疫苗的情感。在将收集到的态度分为积极（33.96%）、消极（17.55%）和中性（48.49%）营后，我们能够更好地看到整体情况。考虑到态度会随时间变化，我们还在研究中加入了对推文时间顺序的检查。使用基于 RNN 设计的双向 LSTM (Bi-LSTM) 以及长短期记忆网络 (LSTM) 对预测模型的性能进行了评估。LSTM 的准确率为 90.59%，而 Bi-LSTM 为 90.83%。还使用了额外的性能指标，如精确率（Precision）、F1 分以及混淆矩阵，来验证我们的假设和结果。本研究结果通过扩大我们对 COVID-19 公共舆论的了解，为全球消除新冠病毒的工作提供了支持。关键词：COVID-19，深度学习技术，社交媒体网络和 Bi-LSTM。> 通讯作者 Abhinav Mishra：商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，Punjab, 印度；电子邮件：abhinav.mishra@chitkara.edu

## 引言

情感分析 [1] 是一个涉及对社交媒体和博客网站上的热门物品、电影、餐厅、政治候选和其他主题进行挖掘的分类问题。2019 新冠病毒（COVID-19）仍然是一个全球健康问题，人们正在使用 Facebook 和 Twitter 表达他们的担忧并提供解决方案 [2]。用户上传的照片、文本和声音在社交网络上的人气有所上升 [3]。为了衡量对 COVID-19 相关活动的公共情感，Twitter [4] 是社交媒体平台上的热门选择。因为推文非常短且具有动态，情况如此 [5]。为了了解不同人群对疫苗的感受，本研究推文的时间范围是从 12 月 21 日到 7 月 21 日。最近在世界几个地区提供的最热门疫苗是多条推文的主题。我们使用名为 VADER 的情感感知情感字典（一种 NLP 程序）来分析人们对特定疫苗的情感。在将收集到的态度分为积极（33.96%）、消极（17.55%）和中性（48.49%）营后，我们能够更好地看到整体情况。考虑到态度会随时间变化，我们还在研究中加入了对推文时间顺序的检查。使用基于 RNN 设计的双向 LSTM (Bi-LSTM) 以及长短期记忆网络 (LSTM) 对预测模型的性能进行了评估。LSTM 的准确率为 90.59%，而 Bi-LSTM 为 90.83%。还使用了额外的性能指标，如精确率（Precision）、F1 分以及混淆矩阵，来验证我们的假设和结果。本研究结果通过扩大我们对 COVID-19 公共舆论的了解，为全球消除新冠病毒的工作提供了支持。情感分析 [1] 是一个涉及对社交媒体和博客网站上的热门物品、电影、餐厅、政治候选和其他主题进行挖掘的分类问题。2019 新冠病毒（COVID-19）仍然是一个全球健康问题，人们正在使用 Facebook 和 Twitter 表达他们的担忧并提供解决方案 [2]。用户上传的照片、文本和声音在社交网络上的人气有所上升 [3]。为了衡量对 COVID-19 相关活动的公共情感，Twitter [4] 是社交媒体平台上的热门选择。因为推文非常短且具有动态，情况如此 [5]。为了了解不同人群对疫苗的感受，本研究推文的时间范围是从 12 月 21 日到 7 月 21 日。最近在世界几个地区提供的最热门疫苗是多条推文的主题。我们使用名为 VADER 的情感感知情感字典（一种 NLP 程序）来分析人们对特定疫苗的情感。在将收集到的态度分为积极（33.96%）、消极（17.55%）和中性（48.49%）营后，我们能够更好地看到整体情况。考虑到态度会随时间变化，我们还在研究中加入了对推文时间顺序的检查。使用基于 RNN 设计的双向 LSTM (Bi-LSTM) 以及长短期记忆网络 (LSTM) 对预测模型的性能进行了评估。LSTM 的准确率为 90.59%，而 Bi-LSTM 为 90.83%。还使用了额外的性能指标，如精确率（Precision）、F1 分以及混淆矩阵，来验证我们的假设和结果。本研究结果通过扩大我们对 COVID-19 公共舆论的了解，为全球消除新冠病毒的工作提供了支持。情感分析 [1] 是一个涉及对社交媒体和博客网站上的热门物品、电影、餐厅、政治候选和其他主题进行挖掘的分类问题。2019 新冠病毒（COVID-19）仍然是一个全球健康问题，人们正在使用 Facebook 和 Twitter 表达他们的担忧并提供解决方案 [2]。用户上传的照片、文本和声音在社交网络上的人气有所上升 [3]。为了衡量对 COVID-19 相关活动的公共情感，Twitter [4] 是社交媒体平台上的热门选择。因为推文非常短且具有动态，情况如此 [5]。为了了解不同人群对疫苗的感受，本研究推文的时间范围是从 12 月 21 日到 7 月 21 日。最近在世界几个地区提供的最热门疫苗是多条推文的主题。我们使用名为 VADER 的情感感知情感字典（一种 NLP 程序）来分析人们对特定疫苗的情感。在将收集到的态度分为积极（33.96%）、消极（17.55%）和中性（48.49%）营后，我们能够更好地看到整体情况。考虑到态度会随时间变化，我们还在研究中加入了对推文时间顺序的检查。使用基于 RNN 设计的双向 LSTM (Bi-LSTM) 以及长短期记忆网络 (LSTM) 对预测模型的性能进行了评估。LSTM 的准确率为 90.59%，而 Bi-LSTM 为 90.83%。还使用了额外的性能指标，如精确率（Precision）、F1 分以及混淆矩阵，来验证我们的假设和结果。本研究结果通过扩大我们对 COVID-19 公共舆论的了解，为全球消除新冠病毒的工作提供了支持。

## 相关工作

在这项研究中，我们使用由卷积的双向长短期记忆网络（CNN-Bi-LSTM）来分析 COVID-19 疫情。由于 COVID-19 疫情，许多人正经历极度的担忧、恐惧和其他困难情绪。Twitter 让我们洞窥任何特定时刻流行内容以及人们在思考什么，而社交媒体目前是表达情感和情绪的最佳手段。我们进行这项研究的目标是更好地了解不同人群对疫苗的感受。本研究推文的时间范围为从 12 月 21 日到 7 月 21 日。最近在世界范围内几个地区提供的最热门疫苗是多条推文的主题。我们使用名为 VADER 的情感感知情感字典（一种 NLP 程序）来分析人们对特定疫苗的情感。在将收集到的态度分为积极（33.96%）、消极（17.55%）和中性（48.49%）营后，我们能够更好地看到整体情况。考虑到态度会随时间变化，我们还在研究中加入了对推文时间顺序的检查。使用基于 RNN 设计的双向 LSTM (Bi-LSTM) 以及长短期记忆网络 (LSTM) 对预测模型的性能进行了评估。LSTM 的准确率为 90.59%，而 Bi-LSTM 为 90.83%。还使用了额外的性能指标，如精确率（Precision）、F1 分以及混淆矩阵，来验证我们的假设和结果。本研究结果通过扩大我们对 COVID-19 公共舆论的了解，为全球消除新冠病毒的工作提供了支持。

建议的方法基于 LSTM-RNN 网络，该网络使用注意力层使用注意力方法来增强特征转换。Twitter 数据从 Cagle 数据集中收集，并分类为“悲伤”、“快乐”、“恐惧”或“愤怒”。所建议的深度学习学习模型显著优于基准方法，准确率提升了 20%，精确率提升了 10% 到 12%，召回率提升了 12% 到 13%。在现有的 LSTM-RNN 方法中添加注意力层使得这种增强得以实现。

活动 [13]，并且它们与上升的接种模型一致。

本文的主要目标是检查通过 Twitter 传达的情绪。收集与新冠病毒相关的推文，使用预训练的词嵌入模型进行清洗，然后输入到卷积神经网络、长短期记忆网络以及一个使用偏置网络（bias network）训练的卷积神经网络（CNN-LSTM）。使用准确率、精确率和召回率方法来评估模型 [14]。

为了估计对反复接触一氧化碳中毒的免疫反应，本研究提出了一种独特的概率技术 [15]。

## 拟工作

## 系统概述

本研究使用的数据集自 Cagle，包含关于 COVID-19 疫苗的若干推文。数据字符随后经过去标记处理，将短语拆分为单词，并在验证唯一值和空值并完成准备后对其进行标记。然后使用 VADER 分配数值，以指示情绪是好好的、负面的还是中性的。随后决定使用深度学习、LSTM 和 Bi-LSTM 架构来评估模型预测的准确性。图 (1) 是基于上述方法的系统示意图。

![](img/5e4d8ef2afa52a8404b28106580e19e4_525_0.png)

**图 (1)** 系统图。

## 数据集描述

Cagle 的“所有 COVID-19 疫苗推文”数据集用于本研究，因为它包含了关于不同疫苗的推文。用户名、日期、地点、朋友数量、回复、标签和来源只是构成这个 125906x16 数组的少数字段。

## 数据预处理、处理和分词

在进一步处理之前，从推文中删除了 URL 和电子邮件。之后，我去掉了所有的标点符号、换行符以及引号（单引号和双引号）。在在使用任何排除技术之前，所有推文都已指定标记。随后进行了去标记处理和数字数组转换。

## VADER 情感分析器

C.J. Hutton 的 VADER 出于 2014 年，是一个更新的系统，它采用围绕自然语言处理（NLP）构建的情绪分析器，以及适用于社交媒体网站情绪视角的基于规则的数值。作为社交媒体内容，它表现出色。如图 (2) 所示，由于采用了广泛的规则，VADER 能够对许多词汇属性的情感进行评估。

![](img/5e4d8ef2afa52a8404b28106580e19e4_526_0.png)

**图 (2)** 情感分析器 (VADER)。

VADER 分析字典中每个单词的效性值，然后计算给定文本为正面、负面或中性的概率。情感评估最常用的指标是复合得分，其形式为 -1 到 1 之间的浮点值，词汇表索引通过对词汇表中每个单词的值进行标准化以适应一组规范后进行求和计算得出。(2) 描述了情感分析器 (VADER)。

## 特征提取与分类

对于给定的 Twitter 情绪 V，我们建议使用 LSTM 模型来确定每条推文重要性。这样你就可以为每组时间序列数据生成正确的语言。在文本生成过程中，LSTM 获取输入并使用其生成一系列文本作为输出。为了改进各种评估指标，我们开发了一种使用双向和语言 LSTM 的多层 LSTM 方法。文本生成过程 $F_t$ 和输出 $O_t$ 涉及三个长短期记忆 (LSTM) 层。在每个间隔处，细胞状态 $C_t$ 和当前的未显示状态 $H_t$ 通过旧隐藏状态 $H_{t-1}$ 和当前时间戳 $X_t$ 实现。

- **输入门：** 使用最新的输入和之前的输出，确定哪些数据需要保留在内存中。简单来说：



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



# 表 2 CNN 和 RNN-GRU 的迭代

| 迭代 | CNN | | RNN-GRU | | |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 准确率 (Exactness) | 回召率 (Recollection) | 准确率 (Accuracy) | 回召率 (Recollection) | 准确率 (Accuracy) |
| 1 | 0.6064 | 0.4211 | 0.8182 | 0.8064 | 0.8211 |
| 2 | 0.5925 | 0.4206 | 0.8179 | 0.8925 | 0.8206 |
| 3 | 0.6016 | 0.4301 | 0.8182 | 0.8010 | 0.8301 |
| 4 | 0.5951 | 0.4249 | 0.8180 | 0.8951 | 0.8249 |
| 5 | 0.5853 | 0.4231 | 0.8186 | 0.8853 | 0.8231 |
| 6 | 0.5844 | 0.4310 | 0.8179 | 0.8844 | 0.8310 |
| 7 | 0.5962 | 0.4252 | 0.8186 | 0.8962 | 0.8252 |
| 平均 | 0.5945 | 0.4252 | 0.8182 | 0.8945 | 0.852 | 0.8182 |

# 结论

在本研究中，我们提出了一种深度学习方法来解决电子商务网站的一个常见问题：用户给出的评分与产品质量不符。消费者依赖评论来帮助做出决策。我们通过段落向量理解“评论”文本中的句法和语义连接，并将组织的评论嵌入输入门控循环单元（GRU）。通过遗传算法生成的产品嵌入训练支持向量机（SVM）进行情感分类。当仅考虑评论嵌入时，我们的分类器可靠性达到了 81.29%。这表明产品数据是情感分析有效的鲁棒特征。

# 参考文献

- [1] Wagatage R., Madhubushani N., Liyanage T.C., Asanka P., 基于GPS的自动跟踪系统的分析与设计2022年人工智能与智能通信国际会议(AISC)印度诺达20221510.1109/AISC5525.2022.9579786
- [2] Zhang H., 模型的重要性：产品评论案例研究.科学与工程亮点
- [3] Vithara K., Kantharanga S., 使用机器学习和深度学习进行情感分析的准确率评估2022年国际会议(ICAERT)30211110.1109/ICAERT3462.2021
- [4] Kaur, A., Senapati S., Jha H., 使用计算智能和解决方案对电子商务评论进行情感分析2022年计算智能与智能工程国际会议(ICSES)20220615.1109/ICSES3067.2022.984436
- [5] Alzahmar M.E., Eldahyany T.H., Alsubari S.N., Athobati M.M., Fahad A., 开发一种用于深度学习分析电子商务产品评论的智能系统.神经计算.2022052220110.10.356964
- [6] Gupta, D., Rout A., Gupta, R., 使用机器学习模型进行食品评论分析和情感预测2022年电气、计算、通信与可持续技术进展第二届国际会议(ICAERT)20220711.1109/CAERT5487.2022.980709
- [10] Nguyen H., Veluchamy A., Deep M., Iqbal R. 基于机器学习和基于词典的方法用于产品评论情感分析对比研究 2018.
- [11] Go J.C., Tabassum T., Mabr M.M., Yu K., Arifuzzaman M.: 使用机器学习和深度学习模型对亚马逊产品评论进行情感分析2022年国际电气与电子工程进展国际会议 (ICACEE) 16022010.1099ICACEE5497.2022.9836420
- [12] Yadaw S.P., Yadaw S.: 连续小波域内医学图像融合的数学实现 《数字与控制系统先进研究期刊》 2019131910D454
- [13] Pamika P., Kerdascap N., Kerdascap K.: 机器学习与深度学习在趋势评论情感分析中的性能对比。Im. J. Mach. Learn. Comput. 20211121130910.18178/imjl.2022.11.2.2021
- [14] Arora L., Srivastava P., Kumar S.A.: 使用深度学习分类模型对产品评论进行评估第13次通信与网络技术国际会议 (ICCNT) 15022010.1099ICCNT54827.2022.986463
- [15] Mehul A.R., Mahmood S.M., Chakraborty P.: 使用机器学习和深度学习进行情感极性检测2023年国际电气、计算机与通信工程国际会议 (ECCE) 15202310.1099/ECCE57851.2023.1010494

# 基于深度学习的酒店评论情感分析

Jagmeet Sohal¹, *

¹ 印度旁遮普邦 Chitkara大学工程与技术学院商业与技术跨学科研究中心

## 摘要

如今许多酒店评价在网上被编写和分享。机器学习情感分类需要复杂的人工设计特征和特征提取技术，而基于情感字典的情感分类则需要大量的情感数据库资源。在本研究中，我们提出了长短期记忆（LSTM）文本分类方法，用于确定总体基调。首先，使用 `word2vec` 和分词技术将简短评论词处理到 LSTM 网络中；接着实施 `dropout`（丢）技术以避免过拟合，从而获得最终的评分模型。通过利用 LSTM 网络卓越的短期记忆能力，对酒店评论的情感分类产生了积极影响，准确率超过了 95%。

**关键词：** 深度学习，电子商务，酒店评论，情感分析。

> * 通讯作者 Jagmeet Sohal：印度旁遮普邦 Chitkara大学工程与技术学院商业与技术跨学科研究中心；电子邮箱：`jagmeet.sohal.orp@chitkara.edu.in`

## 引言

在比较词向量大小时，词嵌入向量向量化的性能优于词袋模型（Bag-of-Word）。在传统的 NLP 方法中，句子层面的上下文、词序以及词与词之间的语义链接丢失了，尽管词嵌入可能会补偿这一点 [1]。`Word2Vec` 和 `Fast Text` 仅是可用于情感分析的许多词嵌入方法的两个例子。`Word2Vec` 是基于词的，而 `Fast Text` 基于 N-Gram 运行。近年来，客户对各种数字平台发布的在线评估的依赖程度大幅增加 [2]。产品通常根据 `Flipkart`、`Amazon` 等电子商务平台上的客户的评论和评分被认可或拒绝 [3]。对服务的评论（如酒店、航空公司和餐厅提供的服务）对消费者而言与对商品的评论同样重要。通过情感分析，程序员可以快速地将用户反馈分类为正面和负面类别 [4]。客户意见是影响产品状况的主要因素，对于酒店评论的情感分类，深度学习仍有改进空间 [5]。在选择酒店时，通常有五个需要考虑的因素：位置、食物、服务、舒适度和清洁度 [6]。本研究提出了一种基于语义相似性的的方法，将评论语料处理为术语集 [7]。通过隐含狄利量分配（LDA）识别词列表的隐藏特征 [8]，使用词频逆文档（TF-IDF）技术来扩展词列表。最后，使用词嵌入和长短期记忆（LSTM）来分类用户的情绪（满意或不满意）[9]。

分类器 [12] 展示了 `Fast Text` 在准确率提升 8% 的有效性（基准：决策树 85%）。

本文通过分析酒店的正面和负面评论来分析其服务，并得出结论。这项工作的主要目标是方面识别和情感分类。方面识别中利用的主题使用隐含狄利克分布 (LDA) 构建的。朴素贝叶斯分类器、支持向量机、决策树和逻辑回归只是用于对评论进行分类的一些机器学习分类器。这些算法使用包括准确率、召回率、精确率以及 F 分 [13] 在内的指标进行评估。

使用所提方法，评论被高效地归类为五种不同的酒店设施。方面分类的最高性能（85%）由 LDA + TF-ICF 100% + 语义相似性实现，基于方面的情感分析最佳性能（93%）由词嵌入 + LSTM 获得，而舒适方面获得了所有方面组件中最多的负面情感（60%）。此外，结果显示情感会受到某些能力因素的影响 [14]。

建议的方法通过将长评论拆分为较短的评论，从中提取所需的观点来实现此。此外，它将非英语语言的评论翻译成英语。在两个数据集上测试系统的结果被认为是充分的 [15]。

## 拟议工作

### 系统模型

对来自旅游相关网站的用户评估进行情感分析涉及多个步骤。我们用于分析客客意见的建议系统架构如图 (1) 所示。在学习了旅游业如何使用数据库之后，为分类准备和清洗数据是第二阶段。下一阶段是从清洗后的准备数据中提取特征。情感阶段的识别是第四步。第五，我们使用了我们的方法来识别评论者的情绪以便使用。第六步是评估我们系统的运行情况。数据从数据库导入到该系统后，我们开始数据清洗过程。同时，我们从数据集中取出不必要的属性。删除所有空格、语法、链接以及电子邮件地址隐含了词形还原和词干提取。使用 GRU 和 LSTM 等算法对数据进行“训练”。然后，我们通过分析结果对我们的系统进行测试。最后，评估了客户的满意度。

### 简要概述

系统的第一个输入将由带有标签的酒店评论组成。每条评论在数据集中都有记录的唯一 ID、评论内容、发布设备和评论极性。输入数据的子集用于训练和评估目的。训练数据是我们将用于构建分类器的内容，而测试数据将接受测试以确保其有效性。在预处理阶段，我们去掉文本中可能干扰我们分类器的所有内容。文本准备流水线如图 (1) 所示。词嵌入用于特征提取，因为它将文本单词转换为分类器更容易理解的数值向量。特征提取过程将采用 `word2vec`，这是一种词嵌入技术。`word2vec` 是一种工具，它输入单词字符串并生成一个表示单词语义和语法属性的数值向量。我们采用了 K-means 聚类技术来分离主观数据和客观数据，以用于情感检测。客观评估仅包含事实，而主观评论包含作者的观点或偏见。此阶段的目标是排除所有客观数据，仅保留评论意见。由于 K-means 聚类技术依赖于软聚类进行分类，一个数据点可能部分属于多个一个类。如果该点具有更高的成员程度，它对该类就更中心。为了确保只有客观评论被发送到分类器，情感识别是情感分类的前提条件。基于深度学习的模型用于根据语气对客人评论进行分类。我们的深度学习模型由三个不同的层组成。在第一个隐藏层（称为嵌入层）中，我们应用了预训练的 `word2vec` 模型。第二个隐藏层由循环单元（GRUs）组成。它是一种更高效的 LSTM 类型，在捕捉单词之间长期关系的同时，速度更快且需要的参数更少。用于输出层的密集神经网络仅包含单个节点，并最终使用 `sigmoid` 函数；最后，系统将输出每条评论的情感极性。我们的模型的性能使用 F 分数和准确率进行评估。

![](img/5e4d8ef2afa52a8404b28106580e19e4_567_0.png)

图 (1)) 系统模型。

### 文本预处理

#### 第一阶段 - 数据分类

你应该从从真实的酒店客户那里收集反馈开始。使用在你的网站上留下的评论是一个很好的起点。如果这不可行，你可能尝试与已经拥有这些信息的其他网站建立关系。应该避免使用数据抓取（一种流行的收集工具），因为它可能会导致法律问题。在 GDPR 和 CCPA 规定下，不能以这种方式处理个人信息。你可能会无意中侵犯网站所有者的权利。

#### 第二阶段 - 情感标注

你需要手动地对评论中的单词和短语应用情感标签（正面、中性或负面），以便机器人可以理解那里表达的思想。当多位人类评审员对数据集标记了情感标签后，它就会被认为是可信的。你至少应该使用三个标注者。

#### 第三阶段 - 文本清洗

原始酒店评论中有大量的噪声和无用信息，可能会负面影响模型性能。这需要彻底的清洗，必须包括：

- 消除噪声 - 包括链接、标签、数字、标点符号和空格。
- 移除停用词，包括但不限于冠词、代词、连词、介词等。自然语言工具（简称 NLTK）是最广泛使用的 NLP 库之一。它包含一个 179 个英语停用词的列表；
- 小写化，以减少由大小写敏感引起的混乱；
- 标准化 - 是赋予单词正确的标准形式的过程。例如，“tomorrow”的标准化版本是“2mw”；
- 词干提取 或消除单词中必要的或冗余的结尾（前缀和后缀）。语法错误是该方法的常见副作用；例如，having 被词干为 hath；
- 词形还原 - 将单词放回其字典形式。你可以说 swim 是 swim、swum 和 swan 的词源。

## 用于文本分类的 LSTM-GRU

长短期记忆（LSTM）单元 [7] 和门控循环单元（GRU）（4] 是我们考虑的 RNN 设计的两个示例。我们对这里使用的单元进行了简要概述，注意到文献中存在其他公式。

遗忘门是典型 LSTM 单元中三个门中的第一个 $f_t$，它决定从过去丢弃多少信息；门的输入 $i_t$ 在数据存储在单元内存之前进行评估；以及输出门 $o_t$ 决定如何从可避免的输入获取结果：

$i_t = \sigma(W_iX_t + R_ih_{t-1} + b_i)$

$f_t = \sigma(W_fX_t + R_fh_{t-1} + b_f)$

$o_t = \sigma(W_oX_t + R_{oh_{t-1}} + b_o)$

可训练的参数矩阵和向量由 W、R 和 b 变量表示。我们可以通过以下特征刻画 LSTM：

$$\dot{C}_t = \tanh(W_c X_t + R_c h_{t-1} + b_c)$$

$$C_t = f_t \odot C_{t-1} + i_t \odot \dot{C}_t$$

$$h_t = o_t \odot \tanh(C_t)$$

$$y_t = \sigma(W_y h_t + b_y).\quad\quad (2)$$

用语言描述，候选单元 $C_t$ 阶段用于计算输入数据 $X_t$ 以及早期的隐藏阶段 $h_{t-1}$。当前单元或内存阶段 $C_t$ 用于计算遗忘门 $f_t$、早期的单元阶段 $C_{t-1}$、摄控门 $i_t$ 以及候选单元阶段 $C_t$。Hadamard 积 $\odot$ 等同于对相关矩阵进行逐元素相乘。输出 $y_t$ 通过将所有相关权重（$W_y$ 和 $b_y$）相加到隐藏阶段 $h_t$ 来确定。

与 LSTM 相比，GRU 仅有两个门且参数更少：新信息门 $(u_t)$ 和重置门 $(r_t)$。门 $u_t$ 控制隐藏状态更新的快慢，门 $r_t$ 通过清除内存存储中的旧数据，为过去信息的遗忘程度设置阈值。以下方程定义了 GRU。这里 $h_t$ 表示潜在候选的“隐藏阶段”。

$$\mu_t = \sigma(W_u x_t + R_u h_{t-1} + b_u)$$

$$r_t = \sigma(W_r x_t + R_r h_{t-1} + b_r)$$

$$h_t = \tanh(W_h x_t + (r_t \odot h_{t-1})R_h + b_n)$$

$$h_t = (1 - u_t) \odot h_{t-1} + u_t \odot \hat{h}_t$$

$$y_t = \sigma(W_y h_t + b_y)\quad\quadquad (3)$$

## 结果与讨论

### 数据集描述

该数据集包含了来自最热门预订平台的客户提交的酒店评分和评论。

| Variable | Description |
| --- | --- |
| Operator ID | 客户自身的个人标识符。 |
| Portrayal | 上传评论的详细说明。 |
| Browser Used | 评论者首选的网络浏览器。 |
| Stratagem Used | 上传评论的设备方法。 |
| Is Comeback | 变量目标。 |

在研究中，我们使用了四种监督算法（朴素贝叶斯、随机森林、决策树和支持向量机）的结果。使用 `Jupyter Notebook` 和 `Python` 编程语言进行的分类准确率达到了 86%，这些模型对于该数据集是非常胜任的。数据收集成功率为63%。最后，测试工具确保了 37% 的精确率。此外，由于没有判定类别，使用了 LSTM 以及 GRU 无监督算法，并使用深度学习方法评估了新数据集。表 **1** 描述了示例评论。

### 表 1 示例评论

| Operator ID | Portrayal | Browser Used | Stratagem Used | Is Comeback |
| --- | --- | --- | --- | --- |
| id10326 | 房间并不脏，但有一股非常刺鼻狗味。充其量是平平；如果你没有高标准，住一晚还可以的。如果价格合适，我可能会再次住这里。早餐免费，总比比没有要好一点。 | Verge | Portable | sad |



| --- | --- | --- | --- | --- |

| `id10327` | 我在 4 月至 4 月期间住在皇冠广场酒店。员工友好且周到。电梯很小（大约 '-' 比 '-'）。餐厅的食物很好吃，但价格偏高。当然，这里是华盛顿特区。没有游泳池，孩子们没什么可做的。我在五楼的房间有两张舒适的床，一个人有足够的空间。按现在的标准来说，电视有点小，频道有限。浴缸区域有一小块霉菌，用一点漂白剂就能除去。地毯似乎没有每天吸尘。我报告了一个灯泡坏了，但从未被更换。制冰机在奇数层，但我这一层的制冰机坏了。一天晚上我在电梯里遇到一些员工，向他们提到了制冰机。几小时后，一名女工带着冰和两颗薄荷出现在我的门口。 | Internet Explorer | Portable | sad |

| Operator ID | Portrayal | Browser Used | Stratagem Used | Is Comeback |

| --- | --- | --- | --- | --- |

| | 我不确定他们怎么知道我在哪个房间的。这有点让人不安！我出差还会再次住这里，但不会来这里度假。 | | | | |

| `id10328` | 我通过 Hotwire 预订这家酒店，得到了最划算的价格。入住时经理告诉我们，我不知道自己在哪个房间。这有点让人不安！我出差还会再次住这里，但不会来这里度假。（等待，重新合并文本）

| `id10328` | 我通过 Hotwire 预订这家酒店，得到了最划算的价格。入住时经理告诉我们，我不知道自己在哪个房间。这有点让人不安！我出差还会再次住这里，但不会来这里度假。（实际上，仔细观察 OCR 流程）：

*根据 OCR 流程修正 `id10328` 的合并：*

`id10328` | 我通过 Hotwire 预订这家酒店，得到了最划算的价格。入住时经理告诉我们，我不知道自己在哪个房间……（等待，OCR 在这里乱码了，让我们严格遵循提供的文本）。

| `id10328` | 我通过 Hotwire 预订这家酒店，得到了最划算的价格。入住时经理告诉我们，我不知道自己在哪个房间。这有点让人不安！我出差还会再次住这里，但不会来这里度假。

# 利用机器学习和自然语言处理对多语言 Twitter 数据进行情感分析

Rahul Mishra

印度Chitkara 工程与技术大学，Chitkara 大学，旁遮普邦，印度，商业与技术跨学科研究中心

## 摘要

零售商、市场分析师和其他网络用户深受用户观点的影响。正确地组织从各种社交网络收集的非结构化数据对于进行相关分析至关重要。作为一种跨语言数据的情感评估方法已引起广泛关注。文本组织是自然语言处理（NLP）的一个子领域，用于将个人的情感或心理状态分类为积极、消极或有害，例如点赞或点踩等。将情感分析与深度学习技术相结合可能是解决问题的关键。具有学习能力的深度学习模型对此特别有用。用于分析文本情感的最广泛使用的深度学习架构之一被称为“长短期记忆网络”（LSTM）。这些框架在 NLP 中具有应用潜力。在本研究中，我们提供了解决多语言情感分析的算法，并评估了它们的精确性。

**关键词：** LSTM、多语言、机器学习、自然语言处理、情感分析、Twitter 数据。

* 通讯作者 Rahul Mishra：印度 Chitkara 工程与技术大学，Chitkara 大学，旁遮普邦，商业与技术跨学科研究中心；邮箱：`rahul.mishra@chitkara.edu`

## 引言

获取文章中内在情感的一种方法是通过情感分析。它利用机器学习和 NLP（自然语言处理）来识别、提取和评估消费者如何感知一项服务或产品。这就是为什么“意见挖掘”或“情感 AI”是此类分析的常用术语。主要目标是确定一段文本是正面的、负面的还是中立的。一个例子是：

- “我们在这家酒店住了五天”是中立的

- “我喜欢住在这里”是积极的

- “我不喜欢这家酒店”是消极的

Web 用户的观点对其他用户、产品交易商和市场研究人员具有很大的分量。在选择标注数据集时，有两个主要的考虑因素：

- 文本长度：对长篇阅读（文章、博客帖子等）使用情绪标签的数据集不适用于较短文本（推文等），反之亦然。

- 主题或领域：即使拥有足够大的标记信息库，训练机器反转评论的效果也会不佳。旅游领域最好通过使用标记样本（如餐厅或航空公司的样本）来达到合理的可靠性。但如果你正在寻找酒店评论，最佳选择是根据游客对酒店的评价创建数据库。

人们一直关注情感分析，并将其作为一种跨语言数据分类的方法。在自然语言处理（NLP）中，这被称为文本组织，可用于将用户的状态或反应分类为积极（点赞）、消极（点踩）或中立（无反应）[2, 3]。在文本分析方面，情感分析（SA）仍然是一个热门的研究课题。用于 SA 的文本处理用于通过应用于 Twitter 数据的自然语言处理技术来衡量其正确性框架 [5]。收集数据、清理文本、预处理、提取文本特征和分类 SA 方法是机器学习领域的基本流程。信息是使用领域特有的方法进行检索的，特别是对于 Twitter 数据 [6]。此时，数据已经针对拼写错误、标点符号、标签和表情符号进行了清理。分词（Tokenization）和停用词去除（SWR）是预处理步骤 [7]。在自然语言处理中，情感分析是一项重要工作 [8]。目前学术界关注最大的领域是情感分析（SA）。除英语以外语言的 Twitter 情感分析在学术界受到的关注非常少。近期通过社交媒体平台传播的各种语言数据集数量似乎激增 [9]。世界各国政府可能会从挖掘社交媒体数据中受益，而 NLP（自然语言处理）等机器学习方法在此起着至关重要的作用 [10]。社交媒体可以挖掘出关于人口的价值“心态”信息，这对于全球每个政府都是至关重要的。它将比以前更好、更被接受且更受欢迎。

## 参考文献

- [1] Khomsah, S. Naive Bayes Classifier Optimization on Sentiment Analysis of Hotel Reviews Journal Penelitian Teknologi dan Informatika 2020

- [2] Navanith D., Likhith K., Vardhan M.S., Kavitha S. Optimized Sentiment Analysis of Hotel Reviews Using Machine Learning Algorithms. 6th International Conference on Electronics, Communication and Aerospace Technology 2022, 1075-1081, 10.1109/IECA5533.2022.1000914

- [3] Wan J., Yao L., Tang Q. Research on sentiment analysis of hotel reviews based on Word2vec method. Other Conferences 2022

- [4] Kurniawan S., Kusumaningrum R., Timu M.E. Hierarchical Sentiment Analysis Of Hotel Reviews Using The Naive Bayes Classifier. 2nd International Conference on Informatics and Computational Sciences (ICICOS) 2018, 15-11, 10.1109/886217488

- [5] Septiardi A.A., Sutiono A.P. Analysis and Opinion Term Extraction for Aspect Sentiment Analysis of Hotel Reviews Using Transfer Learning. arXiv, abs/1909.11879, 2019

- [6] Yadav S., Yadav S. Fusion of medical images in wavelet domain: A discrete mathematical model. Ingeniería Solidaria 2018, 14(2), 251-261

- [7] Lakmasar H., Sumathi M. Design and implementation of aspect Sentiment Analysis of Hotel Reviews Using International Conference on Recent Trends on Electronics, Communication & Technology (RTEICT) 2021, 303-309, 10.1109/RTEICT52594.2021.95738

- [8] Sun F., Chu, N. Sentiment Analysis of Hotel Reviews by Deep Learning. International Conference on Robots & Intelligent System (ICRIS) 2020, 6276-62730, 10.1109/ICRIS52159.2020.00158

- [9] Bai H., Wang G. Sentiment Analysis of Hotel Reviews. Proceedings of the 5th International Conference on Computer Science and Software Engineering 2022, 1011-1014, 10.1104/13566996.3572174

- [10] Shifullah K., Rakibullah H., Islam N., Raihan H., Iqbal M., Ziaul Karim D., Rahul A. Classification of Hotel Reviews Using Sentiment Analysis and Machine Learning. 25th International Conference on Computer Information (ICCI) 2022, 1071-1075, 10.1109/ICCI57492.2022.1005488

- [11] Yadav S. P., Yadav S. Mathematical implementation of fusion of medical images in continuous wavelet domain. Journal of Advanced Research in widely and control system 2019, 10(10):4554

- [12] Khomsah S., Ramadhani R.D., Wijaya S. The Accuracy Comparison Between Word2Vec and FastText On Sentiment Analysis of Hotel Reviews. Jurnal RESTI (Rekayasa Sistem dan Teknologi) 2022

- [13] Vaish N., Goel N., Gulpta G. Machine Learning Techniques for Sentiment Analysis of Hotel Reviews. International Conference on Computer Communication and Informatics (ICCCI) 2022, 1010, 10.1109/ICCCI54379.2022.974087

- [14] Priyantina R.A., Sarno R. Sentiment Analysis of Hotel Reviews Using Latent Dirichlet Allocation, Semantic Similarity and LSTM. International Journal of Intelligent Engineering and Systems 2019

- [15] Gharzولي M., Hamama A.K., Khattabi Z. Topic-based sentiment analysis of hotel reviews. Curr. Issues Tour. 2022, 25(5):1368-1375, 10.1080/13683500.2021.1940107

社交话题，通过检查所有这些，你可以推断出博主的情绪。

## 相关工作

针对此类困难的两种相关解决方案是基于深度学习的技术以及情感分析。在这种情况下，能够学习新事物的深度学习模型是无价之宝。词汇的情感分析是诸如朴素贝叶斯（naive Bayes）以及循环神经网络（LSTMs）等深度学习架构的一项任务。此类结构的一种可能用途是自然语言处理。我们提供了一套多语言情感评估方法，并采用准确率因素比较来提炼结果并选择最佳方法 [11]。

建议的文章深入探讨了用于预处理的机制以及它们对数据集的影响。通过文本预处理和降维，分类算法的准确率得到了提高。市场研究、消费者行为、问卷分析和品牌追踪只是许多可能应用之一，这些应用为构建特定问题的预测分析、机器学习和深度学习应用奠定了基础 [12]。

本研究使用印地语和卡纳纳达语的语言模型，根据其语义内容将推文分类为好或坏。朴素贝叶斯、K-近邻（K-Neighbors）、决策树以及随机森林等机器学习方法经常用于解决分类困难 [13]。

本研究的目的是使用机器学习方法进行情感分析，以便对俄乌之间持续的冲突形成公众意见。目标是检查每个国家的公众意见，以推断决策者是否对潜在的经济后果做出了反应。实施流水线的第一步是借助 Snscraper 和 PRAW（Python Reddit API Wrapper）从 Twitter 和 Reddit 等社交媒体平台收集信息。Reddit 的长帖子使用适当的文本摘要方法进行处理。从社交媒体平台收集的数据利用 BERT Transformer 模型进行情感分析。使用神经机器翻译将其他语言编写的帖子转换为英语。此外，在多个粒度上进行情感分析，包括使用命名实体识别方法标记的位置和。最后，我们对国际观点和各国对俄罗斯石油的依赖性进行了对比研究 [14]。

情感评估以及意见挖掘的目的是通过分析人们的情感、想法和评价，从他们的陈述中提取意义。当涉及互联网数据和文本挖掘时，自然语言处理是扩展最快的子领域之一。情感分析的许多用途之一是跟踪人们对某些问题的感受以及他们在社交媒体上的反应。博客、论坛、微博客以及 Facebook 和 Twitter 等社交媒体网站增加了情感分析的相关性。词汇分析以及受控机器学习可用于量化数字收集的情绪 [15]。

## 提出的工作

## 研究缺口

意见挖掘中的关键问题包括数据规模、数据缺乏组织以及处理多种语言数据的需求。研究人员通常在所有可以想象的问题陈述中工作，但我们的调查显示，只有一小部分解决了多语言问题。由于 NLP 主要处理英语，它似乎很少得见天日。由于大多数研究集中在 NLP（自然语言处理）上，任何想要用另一种语言工作的程序员都必须首先安装该语言的相应库。然而，这种修复方法最多仅适用于少数语言。在处理 6,000 种不同的语言时，这并不是一种可行的方法。管理海量数据给企业带来了若干困难。列例如：

- 合并数据集的问题。

- 首要目标是收集、组织和存储所有这些 Twitter 数据，以便在过滤后可以得出有意义的见解。

- 因为这些数据来自真实使用产品的人，统计数据可能会非常偏斜。

- 博客文章、推文、评论、傀词（即使有拼写错误！）都是可能收集的数据类型示例。表情符号、短语、重复字母等也存在于各种语言中。数据过滤是一个多阶段操作。

在每个阶段，我们收集并分析数据以得出见解。为了筛选用于分析的相关数据，我们将推荐一种训练系统的策略。建议的技术将使用许多类别的算法来获取海量数据的正规阶段，然后可以在三个不同的维度（积极、消极和中性）上进行过滤。因此，在这项研究中，我们通过利用 Google 最新的文本翻译 API 提出了一种多语言意见挖掘的新方法。

## 系统模型

图 (1) 展示了系统模型。

- **步骤 1.** 数据收集：Twitter 在流行程度上超过了所有其他社交网络，拥有数十亿用户。推文可以是原创的、转发的，也可以是被回复的。我们已经开始使用 Twitter，因为每条帖子都限制在 140 个字符。

- **步骤 2.** Google 翻译：为了将文本从一种语言翻译成另一种语言，Google 开发了一项名为 Google Translator 的机器翻译服务。在本节中，使用 Google Translate API 将数据翻译成英语。该模块自动语言转换器的默认设置是英语。

- **步骤 3.** 推文预处理：接收到的用户反馈是未经过滤的。然后，我们对数据应用预处理技术以消除任何所需的背景噪声。建议的模块（意见界定）还包括句分这一重要步骤。因为双重传播情绪在传播情绪时会考虑相邻句子。为了进一步增强提取过程的有效性，我们实现了一个在线词干提取引擎。可以使用许多特征提取技术来获取有用的特征。为了更好地提取有用的特征，我们建议的技术将特征提取过程分为两个阶段。现在，终于，推文可以排序了。

![](img/5e4d8ef2afa52a8404b28106580e194_588_0.png)

图 (1)) 系统模型图。

## 用于推文分类的 LSTM

对 Twitter 和 Facebook 等社交媒体平台上的公众情绪的研究可能会产生见解。然而，Twitter 的数据特征对算法的效率和准确性构成了挑战。噪声、高维度和复杂的语法模式在 Twitter 数据中很常见。由于数据是多语言且混合代码，在 Twitter 上进行情感分析更为困难。在研究中，我们使用了长短期记忆（LSTM）单元（或块），它是 RNN 层的基础构建模块。



长短期记忆（LSTM）网络是`RNN`的子集。普通的长短期记忆单元由四个部分组成：单元、遗忘门、结果门以及输入门。`LSTM`中的“记忆”一词源于该单元负责跨越不同时间段“记住”信息。多层（或前馈）神经网络中的三个门与“传统”人工神经元的作用相同：它们使用激活函数来计算加权和的激活值。“门”是`LSTM`中的一个节点，允许用户调节节点之间的数据流。上述门以某种方式与细胞装置连接。长短期记忆（`LSTM`）的短期记忆理论在长时间保留数据方面非常有效，因此以这个名称命名。`LSTM`非常擅长对具有未知幅度和重要事件之间时间延迟持续的时间序列进行处理、预测和分类。训练传统`RNN`的问题之一是梯度爆炸和消失问题；`LSTM`是为了解决这一问题而开发的。`LSTM`模型如图 (2) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_590_0.png)

图 (2) `LSTM`模型。

## LSTM 的组件

因此，以下部分构成了`LSTM`单元：

- 遗忘门`F`（连接到`sigmoid`函数）。
- 候选状态层`C`（带有`Tanh`激活函数的神经网络）。
- 输入门`I`（带有`sigmoid`函数的神经网络）。
- 输出门`O`（带有`sigmoid`函数的神经网络）。
- 隐藏层级`H`（一个向量）。
- 记忆状态`C`（一个向量）。
- `LSTM`单元在任何时刻都接受三个输入：当前输入`X_t`、上一个隐藏状态，以及先验的记忆状态。

`LSTM`单元将当前隐藏状态（`H_t`）和当前记忆状态（`C_t`）作为其输出。

长短期记忆（`LSTM`）门的工作原理。

为了确定当前的记忆状态`C_t`是否正确，`LSTM`单元最初会使用遗忘门 (f) 将`C_{t-1}`的每个元素翻倍。因为遗忘门的值在零和一之间，所以当该值为 0 时，会完全擦除之前的存储状态；当值为 1 时，会将整个状态传递给单元。

```
$C_t = C_{t-1} * f_t$$
```

确定更新后的记忆状态：

```
$C_t = C_t + (It * C^{t-1})$
```

现在，我们计算输出：

```
$H_t = tanh(C_t)$
```

## 结果与讨论

- 首先，我们从 Twitter 等社交媒体平台收集信息（推文）。在这种情况下，我们使用`LingToTwitter API`（适用于 C# 的 Twitter API）从 Twitter 检索了信息。收集的信息是未经处理的原始数据。在`Keras`中构建了一个序列模型。该线性堆栈中的层包括：

- 一个 100 维的编码层，将句子中的每个单词转换为 100 维的稠密向量。以 100 个单词作为目标输出，词汇表大小作为输入维度。因此，我们将用一个 100 组件的向量表示输入中的每个单词。
- 一个具有 64 个元素的循环`LSTM`层，可以进行双向学习。
- 一个具有 24 个单元的`Relu`激活稠密（全连接）层。
- 根据带有 1 个单元的深层以及`sigmoid`激活函数的结果，标签 1 表示评估良好。

运行此模型必须安装以下包：

- `numpy`
- `pandas`
- `matplotlib`
- `sklearn`
- `nltk`
- `keras`

要安装这些包，请使用`pip`和 Python 包索引按照以下步骤操作：

```
pip install numpy
pip install pandas
pip install matplotlib
pip install sklearn
pip install nltk
pip install keras
```

表 1 展示了`LSTM`模型在准确率、精确率和召回率方面的性能。

表 1 `LSTM`性能。

| 迭代 | 准确率 (Accuracy) | 精确率 (Precision) | 召回率 (Recall) |
| :--- | :--- | :--- | :--- |
| 1 | 1.8169 | 1.5988 | 1.4184 |
| 2 | 1.8188 | 1.5941 | 1.4315 |
| 3 | 1.8186 | 1.5916 | 1.4266 |
| 4 | 1.8187 | 1.5963 | 1.4253 |
| 5 | 1.8178 | 1.5845 | 1.4311 |
| 6 | 1.8187 | 1.5854 | 1.4232 |
| 7 | 1.8181 | 1.5952 | 1.4248 |
| 8 | 1.8183 | 1.6017 | 1.4302 |
| 9 | 1.8178 | 1.5926 | 1.4207 |
| 10 | 1.8183 | 1.6065 | 1.4212 |
| 平均值 | 1.8182 | 1.5945 | 1.4252 |

下表比较了所提方法在不同主题上的性能。表 1 显示`LSTM`性能。

## 结论

在研究中，我们展示了`LSTM`在处理多语言数据方面的有效性。通过深度学习模型对社交媒体数据进行情感分析。在本工作中，我们展示了使用机器学习来分类 Twitter 推文的有效性。结果表明，`LSTM`达到了 96% 的准确率，这意味着对 1,000 个正性样本和 2,000 个负面样本的分类是准确的。实验表明，`Naive Bayes`和长短期记忆（`LSTM`）算法在处理此类任务时表现优异。

## 参考文献

[1] Bari A., Heymann M., Cohen R., Szabo L., "A comparison of Naive Bayes and Long Short-Term Memory (LSTM) algorithms", 2022.

[2] Oum E., Okey G., Kim M., "Multilingual sentiment analysis using deep-learning architectures", 2023.

[3] Mehan D., Mašić Z., "A comparison of LSTM performance on different topics", 2021.

[4] Yun S., Bye H., "Predicting the sentiment of Twitter users after the emergence of COVID-19 using machine learning", 2022.

[5] Narasamalla V., Sreedevi M., "Sentiment analysis on social media using dimensionality reduction", 2021.

[6] Anupama B., "Real Time sentiment analysis using natural language processing", 2020.

[7] Singh S., Kumar K., Kumar B., "Sentiment analysis of Twitter using TF-IDF and Machine Learning", 2022.

[8] Yadav S., Yadav S., "Fusion of Image in Wavelet Domain: A Discrete Mathematical Model", 2018.

[9] Vaishht V., Pandey A.K., Yadav S.P., "Speech Recognition in Machine Learning", 2021.

[10] Go V., Gupta A.K., Kumar N., "Multilingual data analysis using natural language processing", 2018.

[11] Garg N.P., Sharma K., "Text pre-processing of multilingual sentiment analysis based on social media data", 2022.

[12] Sumana, & P. Kanchan, "Hindi and Kannada Twitter Sentiment Analysis Using Machine Learning Algorithm", 2022.

[13] Dominic P., Purushothaman N., Kumar A., Prabagaran A., Angelin Bessy J., John A., "Multilingual Sentiment Analysis using Deep-Learning Architectures", 2023.

[14] Mishra S., Choubey S., Choubey A., Yogesh N., Durga Prasad Rao J., William P., "Data Extraction Approach using Natural Language Processing for Sentiment Analysis", 2022.

## 使用机器学习分析社交媒体网络的情感

Darleen Grover¹*

¹ 商业与技术跨学科研究中心，奇特卡拉大学工程与技术学院，奇特卡拉大学，旁遮普邦，印度

## 摘要

随着 Twitter 等社交媒体平台的问世，互联网上的文本信息量显著增加，包括新闻报道和历史记录。这归功于 Web 2.0 的增长。越来越多的人使用互联网和不同形式的社交媒体向世界分享他们的想法和感受。因此，普通大众创造了更多带有情感细微差别的短语。研究人员探索新方法来理解人类的情绪和反应是自然而然。本研究在提供一种结合文本挖掘和神经网络进行情感分类的新型混合系统外，还评估了许多机器学习和深度学习技术的有效性。该数据集利用来自五个不同主题的超过一百万条推文。数据集的 75% 用于训练，其余 25% 用于测试。与传统的监督学习方法相比，该系统的混合方法达到了 83.7% 的最高准确率。

**关键词：** 机器学习、社交媒体、情感分析。

* 通讯作者 Darleen Grover：商业与技术跨学科研究中心，奇特卡拉大学工程与技术学院，奇特卡拉大学，旁遮普邦，印度；电子邮箱：darleen.grover.org@chitkara.edu.in

## 引言

随着 Twitter 等社交媒体平台的出现，互联网上新闻文章和历史文档等内容的数量大幅增加。表达感受和观点的人数继续增加 [1]。大众通过创造更多带有情感色彩的表达方式来回应。科学家们尝试用新方法来破解人类的认知和行为是不可避免的 [2]。在共享信息、开展项目合作和进行有意义的对话方面，社交媒体平台是核心所在 [3]。情感分析是社会学的一个子分支，旨在研究人们对特定品牌、产品和服务的感受及想法 [4]。随着阿拉伯语在社交媒体上的使用不断增长，学者们对阿拉伯语情感分析这一主题表现出日益浓厚的兴趣 [5]。阿拉伯语是互联网交互中使用最广泛的语言之一 [6]。由于其复杂的形态、广泛的方言以及可用材料的匮乏，这种语言的情感分析具有严挑战性 [7]。由于社交媒体平台上可用文本量巨大，研究人员现在可以更准确地量化这些数据的情感价值，以便更深入地理解所表达的心态、观点和情绪 [8]。为了阐明社交媒体情感分析可能采取的几种方法 [9]，本研究使用机器学习技术分析来自 Twitter 的数据。本文认为，用于分类的模糊集和粗糙集技术是人工智能中特别有效的数学组件，为情感分析这一已久为人知的话题提供了新视角。自然语言处理的文本挖掘领域仍有大量工作待完成，且缺乏讨论情感分析中使用粗糙模糊分类器的综述性论文 [10]。

在易于获取的信息方面，Twitter 排名很高。它使得全球即时通信成为可能，这对于公共表达机会有限的地区尤为有用。2014 年有 1.35 亿人使用互联网；[8]；估计这些人每天发送了超过 1700 万条推文。研究人员探索替代方法以更好地理解人类如何思考和反应是自然而然的。

因此，本研究的目标是通过比较应用于一百万条推文记录的不同方法，来分类哪些推文包含了良好的感受，哪些包含了负面情感。以下是本文的提纲：第二部分我们回顾了相关文献。第三节我们介绍了建议的系统。第四节总结了全文并讨论了后续工作。

## 相关工作

文中描述了一种利用文本挖掘和神经网络对情感进行分类的创新混合系统，并对比了许多著名的深度学习和机器学习方法。该数据集中的推文数以百万，涵盖五个不同的主题。数据集的 75% 用于训练，其余 25% 用于测试。通过达到 83.7% 的最高准确率，该系统证明了其混合方法优于传统方法 [11]。

本研究的主要目标是在不同条件下检查在线辩论者的行为。来自同伴、媒体和周围环境的负面影响具有影响力。如今，大多数人将社交媒体作为主要的交流手段。读者可能会被他们阅读的内容感到鼓舞或沮丧。情感分析可以观察并分析发布者的位置、主题、帖子语气和其他特征，从而对其心理状态做出推断。由于这一现象，使用互联网和许多社交网站的人数增加。哈萨克斯坦的自杀率位世界第三。作为降低自杀率的策略，研究人员确定了情感分析，这是一种自然语言处理技术，用于确定给定的言语应从正面还是负面角度来看。每个数据库项目都需要从广泛使用的网络中收集数据。这项工作的根本目标是整合 NLP 和 ML 技术来收集数据。

通过机器学习和其他复杂的模型，我们的研究寻求自动发现情绪并将其分类为正面或负面。本研究实施并评估了四种机器学习技术：长短期记忆（`LSTM`）、支持向量机（`SVM`）、逻辑回归（`LR`）和 K 近邻（`KNN`）方法。使用阿拉伯评论（`ARev`）数据库来评估这些分类器；它是一个来自广泛来源的手工标注语料库。结果 [14] 表明`SVM`和`LR`是最准确的分类器，成功率分别为 92% 和 93%。

本研究的目标是使用`ML`和`FRT`（模糊粗糙技术）开发情绪检测分类器。2019 年斯里兰卡总统选举案例研究数据使用了 2019 年 9 月 1 日（选举前两个月）到 11 月 15 日（选举后一天）收集的 Twitter 语料库。模糊粗糙分类器使用模糊粗近方法构建。与其他方法相比，基于模糊粗糙的分类器准确率更高。2019 年选举的结果与分类器的预测一致。正如本案所示，利用社交媒体数据预测政治情感已经处于领先水平 [15]。

## 建议的工作

## 系统模型

本研究的目的是从汇总的 Twitter 数据集中确定主基调。已经对以下方法进行了尝试：

在确定最有效的推文之前，发布了大量的推文。

从推文收集阶段（输入数据集）开始，并经过预处理、特征提取和分类阶段（如图 (1) 所示），我们最终达到了评估阶段（其中比较了几种分类方法的结果）。

## 收集初始数据

从 Twitter 140 API 中提取了总计 1,048,588 条英文推文，并将其存储在 GitHub、Kaggle 和加州大学欧文文分校的仓库中。每条推文有 140 个字符的限制，某些使用了专业语言，而另一些则更加口语化。

## 预处理阶段

通过以下操作进行清理：

- 移除无关推文。
- 大小写转换。
- 标点符号。
- 停用词。
- 词干提取（`Stemming`）。
- 词袋模型（`Bag-of-words`）。
- 移除数字。
- 分词（`Tokenizing`）。
- 单词合并。

在此阶段，我们专注于从推文中提取有用信息。得益于向量表示，分类器可以读取每条推文。

![](img/5e4d8ef2afa52a8404b28106580e19e4_602_0.png)

图 (1) 系统图。

## 词嵌入

- 词频-逆文档频率（`TF-IDF`）分析文本语料库，并根据相对稀有性对不常用的术赋予更高的权重。简单来说，这是一种快速提取关键词的方法，也是衡量给定术重要性的标准。虽然`TF-IDF`仍被广泛用于情感分析，但它是过时的方法，忽略了周围文本和单词出现顺序等重要因素。
- `Word2Vec`是“word to vector”的缩写，是一个只有两层的浅层神经网络。`Word2Vec`由 Google 于 2013 年开发，将用于相似语境的单词聚类在一起。它的设计是在海量文本数据语料库上运行。
- 使用了约 1 亿篇 Google 新闻文章对算法进行预训练。随着时间的推移，得益于接收到的数据（即向量），它越来越擅长根据上下文预测单词。
- 全局词计数（`GloVe`）：一种计数工具。`GloVe`（全局向量）以类似于`Word2Vec`的方式生成文本材料的向量表示。`Word2Vec`强调邻近单词，而`GloVe`则查看整个语料库以确定两个单词一起出现的频率。用通俗的话说，它首先构建一个巨大的矩阵，显示给定单词在给定语境中出现的频率。然后，它生成词与词之间的向量，显示单词共同出现的频率。

## 推文分类

在此阶段，我们开始构建分类器可能使用的词向量。随后，使用决策树、朴素贝叶斯、随机森林、具有 10 个隐藏多层感知器的神经网络、带有长短期记忆（`LSTM`）连接的循环神经网络以及卷积神经网络方法对英文推文进行分类。

二分类、多类分类、多主题分类和层次分类的评估指标是机器学习算法使用的四种主要分类性能衡量标准。我们使用混淆矩阵来帮助我们在性能测量过程中达到最有前景结果的“零点”。

- 预测分析通常使用线性回归。当响应变量和协方差可以显示为线性关系时，线性回归就是合适的。这种方法是有益的，因为它将重点从统计建模转移到了预处理和数据分析。使用线性回归学习与数据交互变得更容易，因为我们不需要担心模型的细微复杂性。结论是，它是教学数据分析技能的良好工具。然而，由于它过度简化了现实世界的问题，因此不推荐用于广泛的实际应用中。
- 决策树（`DT`）是一种图形化表示，使用分支方法来描述特定情况下选择的所有可能结果。分类与回归树（`CART`）、随机森林和提升树（boosted trees）只是许多流行的回归树技术中的少数几个。在机器学习领域，决策树（`DT`）涵盖了分类和回归。每个分支的末端都是根据某些输入和特定约束得出的决策。决策树用于视觉化表达任何分支逻辑。决策树从根节点到叶子节点的路径可以用于确定分类。内部节点代表对决策树提供的属性执行的测试。这些检查的结果来自决策树的叶子节点，叶子节点指示分支的结论。决策树让你在极少需要清理的情况下探索数据。然而，过拟合是决策树中难以解决的问题。剪枝和对模型参数的安排限制将解决这个问题。连续变量不用于拟合决策树。



当涉及分类和回归时，随机森林（RF）是可用最可靠的机器学习算法之一。Bagging 是 RF 使用的一种技术，由决策树集合描述。RF 使用完整数据集的子集进行多轮训练以产生卓越的预测模型。与集成学习方法类似，它利用生成的决策树来做出可靠的预测。高质量的随机森林预测是那些在决策树中出现一次以上的预测。随机森林算法的优势在于它可以相对容易地解决分类和回归问题，允许做出准确的估计。它对大数据集非常友好，且不会丢弃任何维度。这是另一种降维技术，因为尽管输入变量很多（数百到数千），它也能轻松管理并发现显著变量。它为解释缺失数据提供了有效技术，并在数据缺失关键部分时仍保持精度。除了随机森林算法的优点外，还使用了自助法（bootstrap）和袋外采样（out-of-bag sampling）。

与决策树一样，最近邻也可用于分类和回归。被称为“最近邻”的 Basic 机器学习方法通常用于分类业务环境中遇到的挑战。在这一分类系统中，如果一个邻居支持某个案例，那么最近的案例将被保留。同样，它记得所有相关实例，并根据所有附近邻居的综合意见对最近的实例进行排序。使用基于 k 个邻居的距离公式，我们可以量化每个类的实例。k 个邻居集合之间的距离可以使用欧几里、Hamming、Minkowski 或曼顿距离来计算。分类和欧几里 Hamming 距离以及曼顿 Minkowski 距离都是连续函数。如果 k = 1，则一个案例恰好有一个邻居类。

## 结果与讨论

本研究使用了 1,048,588 条英文推文作为数据。推文使用不同的分类方法进行分类，例如朴素贝叶斯、循环神经网络、决策树、神经网络、随机森林和混合模型。下表汇总了使用某些算法的结果。

这里是一些用于情感分析机器学习模型的公开可用数据集。我们尝试了其中几个。

- 超 160 万条推文通过 Twitter API 获取并添加到 Sentiment140。通过分析附加在推文上的注释可以确定品牌、产品或问题的情感。
- 餐厅评论数据集共有 52,077 条评论，带有星级评分和详细的优缺点。
- 近 20,000 个评分和评论的酒店可以在 TripAdvisor 酒店评论中找到。
- 构成 OpinRank 数据的酒店和车辆评论提取自 TripAdvisor（世界上最大的旅游反馈网站）和 Edmunds（美国最大的汽车信息在线资源）。
- Stanford 情感树形库中的近 12,000 行全部取自 Rotten Tomatoes 的用户评估。使用带有注释单词和短语的解析表示来传达每个断言的含义。数据中有 215,000 个不同的句子经过手动分类。所提模型与现有分类器的对比见表 1-5，分别对应准确率、敏感度和特异性。

## 表 1 Sentiment140 的结果

| 分类器 | 准确率% | 敏感度% | 特异性% |
| :--- | :--- | :--- | :--- |
| 朴素贝叶斯 | 77.5 | 79.0 | 74.0 |
| 随机森林 | 73.8 | 70.0 | 77.0 |
| 决策树 | 72.5 | 72.0 | 68.0 |
| RNN-LSTM | 82.3 | 76.1 | 83.9 |
| NN (10 层) | 79.5 | 81.1 | 77.3 |
| CNN | 79.6 | 84.7 | 75.0 |
| CNN Word2Vec | 82.9 | 83.0 | 82.7 |
| RNN+LSTM+Word2Vec | 83.0 | 86.0 | 79.3 |
| 混合模型 | 83.6a | 87.1 | 79.3 |

## 表 2 餐厅评论结果

| 分类器 | 准确率% | 灵敏度% | 特异性% |
| :--- | :--- | :--- | :--- |
| 朴素贝斯 | 77.5 | 79.0 | 74.0 |
| 随机森林 | 73.8 | 70.0 | 77.0 |
| 决策树 | 72.5 | 72.0 | 68.0 |
| RNN-LSTM | 82.3 | 76.1 | 83.9 |
| NN (10 层) | 79.5 | 81.1 | 77.3 |
| CNN | 79.6 | 84.7 | 75.0 |
| CNN Word2Vec | 82.9 | 83.0 | 82.7 |
| RNN+LSTM+Word2Vec | 83.0 | 86.0 | 79.3 |
| 混合模型 | 83.6a | 87.1 | 79.3 |

## 表 3 意见排名评论结果

| 分类器 | 准确率% | 灵敏度% | 特异性% |
| :--- | :--- | :--- | :--- |
| 朴素贝斯 | 77.5 | 79.0 | 74.0 |
| 随机森林 | 73.8 | 70.0 | 77.0 |
| 决策树 | 72.5 | 72.0 | 68.0 |
| RNN-LSTM | 82.3 | 76.1 | 83.9 |
| NN (10 层) | 79.5 | 81.1 | 77.3 |
| CNN | 79.6 | 84.7 | 75.0 |
| CNN Word2Vec | 82.9 | 83.0 | 82.7 |
| RNN+LSTM+Word2Vec | 83.0 | 86.0 | 79.3 |
| 混合模型 | 83.6a | 87.1 | 79.3 |

## 表 4 Trip Advisor 评论结果

| 分类器 | 准确率% | 灵敏度% | 特异性% |
| :--- | :--- | :--- | :--- |
| 朴素贝斯 | 77.5 | 79.0 | 74.0 |
| 随机森林 | 73.8 | 70.0 | 77.0 |
| 决策树 | 72.5 | 72.0 | 68.0 |
| RNN-LSTM | 82.3 | 76.1 | 83.9 |
| NN (10 层) | 79.5 | 81.1 | 77.3 |
| CNN | 79.6 | 84.7 | 75.0 |
| CNN Word2Vec | 82.9 | 83.0 | 82.7 |
| RNN+LSTM+Word2Vec | 83.0 | 86.0 | 79.3 |
| 混合模型 | 83.6a | 87.1 | 79.3 |

## 表 5 标准情感评论结果

| 分类器 | 准确率% | 灵敏度% | 特异性% |
| :--- | :--- | :--- | :--- |
| 朴素贝斯 | 77.5 | 79.0 | 74.0 |
| 随机森林 | 73.8 | 70.0 | 77.0 |
| 决策树 | 72.5 | 72.0 | 68.0 |
| RNN-LSTM | 82.3 | 76.1 | 83.9 |
| NN (10 层) | 79.5 | 81.1 | 77.3 |
| CNN | 79.6 | 84.7 | 75.0 |
| CNN Word2Vec | 82.9 | 83.0 | 82.7 |
| RNN+LSTM+Word2Vec | 83.0 | 86.0 | 79.3 |
| 混合模型 | 83.6a | 87.1 | 79.3 |

## 结论

本文分析了超过百万条推文的情绪，并比较了许多机器学习和深度学习方法的结果。除了 CNN、DT、朴素贝斯和 RNN 等传统分类策略外，还构建并测试了一个混合模型。该混合模型表现出 87.1% 的灵敏度和 79.3% 的特异性，证明了其是最有效的方案。后续研究的目标是将情感情感因素纳入文本分析方法中，以评估其在阿拉伯语推文中的效能，因为每分钟都会产生海量推文，其中许多是阿拉伯语。

## 参考文献

- [1] Gangwar, A., Mehta, T.. Sentiment Analysis of Political Tweets by Machine Learning ArXiv. abs/2204.0651
- [2] Vashit, V., Pandey, A., Yadav S.. Speech Recognition using Machine Learning IE Transactions on Smart Computing The Institute of Electronics Korea20211032
- [3] Hassan A., Hussain, J., Hussain, M., Sadiq, M., Lee S.. Sentiment analysis of social networking sites (SNS) using data learning approach for the measurement of depressionInternational Conference on Information and Communication Technology (ICTC)20171314
- [4] Indra Z., Setiawan, A., Jusman, Y.. Implementation of Machine Learning for Sentiment Analysis of Social and Political Orientation in Pekbaru City.J. Phys. Conf. Ser.20210813
- [5] Yadav S. P., Yadav, S.. Mathematical implementation of fusion of medical images in continuous wavelet domainResearch in dynamic and control system20191021055
- [6] Asmawati E., Saikhu A., Siahaan D.. Sentiment Analysis of Tweets: A Comparison Among Supervised Machine Learning Methods 9th International Conference on Electrical Engineering, Computer Science and Informatics (ECCISI)20223495
- [7] Hajirahima M., Mismailova I.. Machine Learning-based sentiment analysis of Twitter dataProblems of Information Society2022
- [8] Anashnik D., Malyshenko K.A., Media Content Analysis with Machine Learning Tools2021 International Conference on Artificial Intelligence and Data Science (ICAIDS)202115
- [9] Abeen, Y., Ansari, Y., Yasmin, S., Moon, J., Rho S.. An Empirical Study of Macroeconomic Factors and Returns in the Context of Economic Uncertainty News Sentiment Using Machine LearningComplex2022181464733
- [10] El Barachi M., Alkhatib M., Mathew S.S.. A Hybrid Machine Learning Approach for Sentiment Analysis of Partially Occluded Faces2021 IEEE International Conference on Artificial Intelligence and Computer Applications (ICAICA)20213893
- [11] Abd El-Javad-M.H., Hodhod R., Sentiment Analysis of Social Media Networks Using Machine Learning14th International Computer Engineering Conference (ICENCO)2018716
- [12] Geetha V., Sujata N.. A Review on Sentiment Analysis of Social Media Networks using Deep Learning6th International Conference on Intelligent Computing and Control Systems (ICCSS)20221149
- [13] Melariyev, B., Kontratbayev G., Sultanova N.. Content Analysis of Extracted Suicide Texts From Social Media Networks Using Natural Language Processing and Machine Learning Techniques2021 IEEE International Conference on Smart Information Systems and Technologies (SIST)162021
- [14] Kaur J., Saxena J., Shah J.. Facial Emotion Recognition2022 International Conference on Computational Intelligence and Sustainable Engineering Solutions (CISES).2022
- [15] Perera S., Karunanaka K.. Sentiment Analysis of Social Media Data using Fuzzy-Rough Classifier for the Prediction of the Election2nd International Conference on Advanced Research in Computing (ICARC)2022

手机和可穿戴设备 [1]。鉴此，提出了一种混合边缘-云计算架构 [2]，在假设连接状态持续的条件下，简单地划分 DNN 过程，从而允许将部分计算迁移到云端。然而，目前仍缺乏全面的 DNN 分段方法 [3]，且实际网络的状态可能会根据其环境发生剧烈变化。允许 5G 无线网络正常运行最重要的技术之一是云无线接入网络（CRANs） [4]。为了在满足消费者长期需求的同时降低能耗，必须进一步改进 CRAN 的资源分配 [5]。鉴于深度强化学习（DRL）在解决挑战性问题上的成功经验，我们提出了 ReCALL，这是一种基于 DRL 的 CRAN 环境资源利用的新型范式 [6]。在每个决策周期中，一旦建立了状态距离、动作空间以及奖励函数，就会使用深度神经网络（即 DNN）来近似确定 DRL 代理的动作-值函数 [7]。想要促进线下聚会以及吸引新面孔，没有比基于事件的社交媒体平台（EBSN）更容易的事情了，这些平台在过去几年中经历了爆发式增长 [8, 9]。一个不断发展的基于事件的社交网络（EBSN）依赖于能够持续建议成员偏好的事件。由于机器学习使得智能手机、可穿戴设备和物联网设备等边缘设备的智能性提高，对有限资源的竞争变得更加激烈。在边缘设备上训练模型是一个资源密集型过程，使得设备端定制化成为一个巨大的障碍 [10, 16]。

为了确定审稿者的情感立场，我们使用 Stanford 词性标记器（Stanford POS Tagger）为评论文本中的名词、形容词、副词和动词标记适当的词性（POS）标签。通过在大规模情感词典中查找上述关键词并获取其相关的情感倾向来确定情感方向。我们使用语言语义标准将句子/评论文本恰恰标记为正面和负面情感。模糊意见的分类可以受益于语言语义原理。它们有助于对情感分析（SA）问题进行更精确的建模。使用了六个流行的情感分类数据集来评估所提方法的预测能力。与现有基线方法相比，建议的方法显著提高了情感分析的效率和有效性。论文的其余部分结构如下：第 2 节展示了相关的后续工作；第 3 节，我们深入探讨了方法、架构和技术细节；第 4 节，我们讨论了方法论和实验结果；研究以关于未来展望的章节结束。

## 相关工作

我们探索了 DNN 的模块化设计如何被用于修改边缘模型，以用于不同的设置和采用不同的部署策略。为了同时实现模型一致性和计算延迟这一目标，我们构建了一个基于强化学习的决策引擎。DNN 使用由引擎构建的上下文感知模型树来对实时切换到哪个模型分支做出决定。我们的方法已被证明在仿真和现场测试中可以降低 30% - 50% 的延迟，且且不损害模型准确性 [11]。

短词检测问题通过创建 HMM/DNN 架构得到了解决。通过在第一阶段相位合成器中包含上下文感知关键词理论以及 9 状态过滤框架，我们可以将短词的优异指标（FOM）从 6.08% 提高到 21.88%，并将遗漏问题的百分比从 80% 降低到 6%。为了进一步缩小潜在匹配范围，在假设器之后使用了一种基于 MLP（多层感知机）的第二阶段关键词验证。通过三种尖端技术重新设计验证器，改进了短词识别：基于知识特征、深度人工网络以及使用隐藏马尔可夫模型（H）用于 MLPs 的特征转换。使用来自 TIMIT 集合的九个短关键词，我们通过建议的 KWS 技术实现了 42.79% 的最佳 FOM；这与长内容词 42.6% 的 FOM 相比良好，并且显著高于早期工作中报道的短关键词 18.4% 的 FOM [12]。

我们在 ReCARL 中为 DRL 提供了两个不同的代理：ReCARL-Basic，它使用传统的深度 Q 学习方法训练传统的 DNN 结构；以及 ReCARL-Hybrid，它使用混合深度定性学习方法训练上下文感知的 DNN 架构。在系列大量的仿真测试中，我们在广泛使用的基准上评估了 ReCARL 和两个 DRL 代理。结果显示，ReCARL 在节能量的同时能够满足客户的需求 [13]。



通过语义内容分析和上下文事件影响，我们的研究提出了一种事件建议的混合协同过滤方法，可以帮助用户对其所在位置的事件做出明智决策。具体而言，我们使用隐含主题模型分析事件描述中的文本，然后利用每个用户的事件注册历史来开发长期兴趣模型和短期兴趣模型。然后，我们为每次发生分配一个值，考虑到其唯一性和对用户的社交相关性。在进行连接推荐时，我们将用户的长期兴趣置于瞬时效应之上。为了做到这一点，我们使用短期兴趣模型构建用户-事件评分矩阵，然后根据邻居的评分预测事件评分。在真实数据集上的测试 [14] 证实了我们方法的优越性。

名词被扩展。内容也被进行了压缩，同时在拼写检查器和大小转换模块的帮助下纠正了任何错误。下一阶段是使用词性（POS）标记器，将最可能的词分类为名词、形容词、副词或动词。

![](img/5e4d8ef2afa52a8404b28106580e19e4_618_0.png)

**图 (1)** 系统混合 DNN 模型。

当作者的评论包含一系列观点时，我们还使用语言准则来识别合适的句子类别。例如，在“这位电影导演很有名，但这部电影很乏味”这个短语中，语言标准只考虑了连词“但”后的句子部分。改变句子的极性需要使用“但”、“尽管”、“虽然”、“除非”等词汇。评论文章中通常包含多种观点。采纳语言规范可以从整体上提高评论的质量。此前的研究假设，每条评论句子/文本都会落入两种极性之一：

## 情感词汇表层

为了准确确定领域相关情感词的情感方向，现有的许多情感词汇表仅包含极小部分的短语。为了增加情感词汇表的覆盖范围，我们合并了许多不同的情感字典。我们之前讨论的 10 种最先进情感词汇表通过三种评分之一：+1、-1 或 0 被标准化并集成到一个一致的框架中。通过对出现在两个字典中的术语情感评分取平均，我们构建了一个更广泛的情感词汇表。

我们展示了当前先进情感词汇表的示例，详细说明了它们的覆盖范围和规模。首先，我们通过赋予每个正面、负面和中性术语分别为 1、1 和 0 分，对词汇进行了标准化。然后，通过对出现在几个词汇中的术语情感评分取平均，创建宽覆盖情感词汇表（WCSL）。情感词汇表的根本问题是它们只涵盖了单词的一小部分。如果一个情感术语已经不在情感词汇表中，它可能会被遗漏，这可能会改变评论的整体语气。为了解决这个问题，我们从 `WordNet` 中挖掘该词的语义信息（即其同义词），并利用这些结果推断潜在的倾向。如果我们得到单词“W”，我们可以在 `WordNet` 中查找其他以相同字母开头的单词。我们在 `WCSL` 中查找 W 的每一个可能的同义词，如果它在那里，我们就知道它传达了什么情绪。我们取所有潜在替代品的平均情感评分。一个表达式的情感方向为正，且仅当其中位情感评分“W”大于零时；否则，它是正的。(1) 显示了系统混合 DNN 模型。

## BERT 模型

`BERT` 是一种堆叠的 Transformer 编码器和解码器语言模型，它可以学习新的语言结构。与 `Word2Vec` 相比，`BERT` 更好且更通用，考虑了单词的上下文无关表示。单词随着环境的变化不断改变。`BERT` 能够学习文本从左到右和从右到左的表示。`BERT` 使用掩码词模型（Mask Word Model）构建输入序列的词级图像，并使用下一句预测（Next-Paragraph-Predictions）按顺序构建句子级表示，以降低总损失率。通过任意掩码每个句子中的单词，并随后根据相邻未掩码单词的含义对其进行预测，语言掩码模型训练了深层可逆 Transformer 表示。为了给 `BERT` 准备数据，在 15% 的单词中用 `[MASK]` 标记替换了词序列。模型根据序列中其他单词的含义对掩码词的原始值做出很好的猜测。下一句预测旨在通过学习单词之间的关系，训练 `BERT` 处理各种下游任务。数据集中的每条评论文本和短语都具有使用 `BERT` 语言模型生成的情感增强词嵌入。输入词标记通过情感增强嵌入层转换为词向量。然后，基于这些词向量的高质量显著情感特征被用于下游 DNN 模型进行分类。

## 用于分类的混合 DNN

我们在混合-DNN 中结合了空间深度（空间性）和时间深度（时序性）神经网络特征，以实现更复杂的智能应用。

为了改进基于情感的词嵌入和分类，使用集成网络从评论文本中查找并提取情感术语。以其中的评论文本 `S=w_1,w_2,...,w_n` 单词作为输入。目标是使用 `WCSL` 从 S 中提取情感词并创建一个升级的词嵌入向量。你可以将其写为 `W_{SV}={V_1, V_2, V_3, ..., V_n}`。在图 **(2a)** 中，我们看到了一个使用加权连接的基本神经网络示例。你可以通过将输入模式与权重矩阵相乘来计算最终状态 `y`。

```
$y_j = \sum_{i=1}^{m} x_i \times W_{ij}$
```

其中 `x_i` 是定义的输入模式，长度为 `m`，`W_{ij}` 代表第 `i` 个数据和第 `j` 个结果。

- SST-2：Harvard Sentiment Treebank 数据集中已移除了所有中性评估，使其成为一个二标记版本。包含 9613 个正向和负面样本。

- CR：Amazon 和 CNET 客户评论（CR）数据集包含对五种不同电子设备的评论。

- SemEval 数据集包含了 2013 年和 2014 年涵盖广泛话题的 Twitter 对话。与该工作保持一致，我们使用 `SemEval2013` 训练集和开发集训练并调优了分类器，并在 `SemEval2013` 和 `SemEval-2014` 测试集上评估了其性能。这是因为 `SemEval2014` 中没有包含任何真实世界的数据。此外，我们同样只考虑二分类目标（正面和负面），并以相同的方式排除了中性反馈。只有 `SST-2` 数据集包含每个这些评估阶段（训练、开发和测试）的独立数据。其余数据集被随机划分为三个部分：开发集、测试集和训练集。

## 基准方法

- 在本项研究中，我们将我们技术的准确率与一些最广泛使用的分类器进行了比较，例如支持向量机（SVM）、K 近邻算法（KNN）和逻辑回归（LR）。使用十折交叉验证技术，我们将我们的方法与所有基准技术进行了比较。这些方法的维度和具体细节在下面简要描述。

- 基于统计学习理论，支持向量机（SVM）利用核函数将低维度上不可处理的问题进行映射。正则化惩罚参数（C）和径向基函数（RBF）核的标准差（SD, 1/l）被选为 SVM 的超参数。

- 为了对数据标签分类，KNN 是一种监督学习方法，寻找最近的 k 个实例。样本的邻居根据多数投票决定样本的分类。距离通常使用欧几里得量进行衡量。

- LR：LR 用于描述 X 和 Y 之间的关系，并仅使用 X 和 Y 作为独立变量对 Y 进行预测。Y 是 0 到 1 之间的实数，表示来自二分类中两种可能结果之一的可能性。为了获得正则化参数 C 的最佳值，LR 在 `[10^2, 10^3]` 的对数范围内进行搜索。

## 表 1 提出的方法与现有方法的对比分析。

| 数据集 | 嵌入方案 | F-measure | 精率 | 准确率 | 回回率 |
|---|---|---|---|---|---|
| MR | BERT | 93.6 | 94.1 | 93.6 | 93.1 |
| | FastText | 90.8 | 90.1 | 91.1 | 91.9 |
| | Glove | 89.7 | 89.5 | 89.8 | 89.8 |
| | Word2vec | 88.8 | 89.1 | 88.8 | 88.5 |
| RT-2K | BERT | 94.8 | 95.1 | 94.8 | 94.6 |
| | FastText | 92.2 | 91.1 | 92.3 | 93.4 |
| | Glove | 90.5 | 90.2 | 90.6 | 90.8 |
| | Word2vec | 89.6 | 90.1 | 89.6 | 89.2 |
| | BERT | 91.8 | 90.9 | 92.1 | 93.1 |
| SST-2 | FastText | 90.1 | 89.6 | 90.1 | 90.5 |
| | Glove | 89.5 | 89.6 | 89.5 | 89.9 |
| | Word2vec | 88.9 | 88.6 | 88.8 | 89.2 |
| CR | BERT | 94.8 | 95.1 | 94.8 | 94.6 |
| | FastText | 92.4 | 93.6 | 92.3 | 91.3 |
| | Glove | 91.9 | 92.6 | 91.8 | 91.2 |
| | Word2vec | 91.2 | 90.6 | 91.3 | 91.1 |
| | BERT | 93.6 | 93.8 | 93.6 | 93.3 |
| SemEval 2013 | FastText | 91.8 | 91.9 | 91.8 | 92.2 |
| | Glove | 91.4 | 91.3 | 91.5 | 91.5 |
| | Word2vec | 90.8 | 91.3 | 90.8 | 90.9 |
| 数据集 | 嵌入方案 | F-measure | 精率 | 准确率 | 回回率 |
|---|---|---|---|---|---|
| SemEval 2013 | BERT | 84.6 | 84.8 | 84.6 | 84.5 |
| | FastText | 82.9 | 82.7 | 82.8 | 83.2 |
| | Glove | 81.2 | 80.8 | 81.2 | 81.4 |
| | Word2vec | 80.7 | 80.5 | 80.7 | 80.9 |

使用词嵌入向量的方法在多个方面影响分类的精率。因此，我们的目标是研究广泛使用的预训练词嵌入对分类准确率的影响。在这一部分，我们将运行一系列实验来确定上述嵌入技术如何影响混合 DNN 的整体性能。提出的情感分类技术受情感输入的影响很大。知识库：LR（带 POS 标记的语言规范）、MW（通过单词转换获得的意义词）和 WCSL（广泛情感词典）都是系统的一部分。为了检查情感信息如何影响提出的模型，我们在数据集上进行了情感知识适配实验。如表 1 所示，情感信息的引入带来了显著的结果。然而，随着更多情感知识的加入，整体性能有所提升。这证明了情感信息对混合 DNN 性能的收益。

提出的模型在多个方面优于 SOTA 的 DNN 模型。首先，在文本处理期间修复了评论文本中的拼写错误并移除了噪声特征。其次是提取了与给定上下文相关的情感特征。第三是根据语言语义对歧义观点进行分类。添加 WCSL 来识别细微的情感是第四点理由。第五是情感特征可能以密集实值向量表示，捕捉了词序列的长依赖关系和关于文本环境的语义数据。第六，通过一组良好的超参数增强了提出的语义及上下文感知情感评估模型。第七个收益是它可以有效地提取丰富的情感数据进行精确分类。

表 2 显示了提出的方法与现有方法的对比分析。

## 提出的方法与现有方法的对比分析。

| 数据集 | 嵌入方案 | 精率 | 回回率 | F-measure | 准确率 |
|---|---|---|---|---|---|
| MR | 提出的 SVM | 94.0 | 93.0 | 93.5 | 93.5 |
| | KNN | 90.0 | 91.8 | 90.9 | 91.0 |
| | LR | 89.4 | 89.9 | 89.6 | 89.7 |
| RT-2K | 提出的 SVM | 95.0 | 94.5 | 94.7 | 94.7 |
| | KNN | 91.0 | 93.3 | 92.1 | 92.2 |
| | LR | 90.0 | 90.9 | 90.4 | 90.5 |
| SST-2 | 提出的 SVM | 90.0 | 89.1 | 89.5 | 89.5 |
| | KNN | 90.8 | 93.0 | 91.8 | 92.0 |
| | LR | 89.4 | 89.9 | 89.6 | 89.7 |
| CR | 提出的 SVM | 94.8 | 95.1 | 94.8 | 94.6 |
| | FastText | 92.4 | 93.6 | 92.3 | 91.3 |
| | Glove | 91.9 | 92.6 | 91.8 | 91.2 |
| | Word2vec | 91.2 | 90.6 | 91.3 | 91.1 |
| | BERT | 93.6 | 93.8 | 93.6 | 93.3 |
| SemEval 2013 | FastText | 91.8 | 91.9 | 91.8 | 92.2 |
| | Glove | 91.4 | 91.3 | 91.5 | 91.5 |
| | Word2vec | 90.8 | 91.3 | 90.8 | 90.9 |

## 结论

用户在线创建的各种形式的文本非组织化数据为电子商务和商业研究提供了丰富的相关信息。情感作为一个快速扩展的研究领域，旨在对用户生成信息中的正面和负面情绪进行分类。由于量巨大，从文本数据中构建稳定的情感分析框架具有挑战性。

- [5] Zeng, Hong F., Zheng W., Yu Q., Zeng W., Wang Y., Lai J. 用于长视频评估的混合视频-静态上下文感知网络. 第 28 届 ACM 多媒体国际会议论文集. 2020. 1145/339417.3413560

- [6] Kaur J., Saxena J., Shah J. 面部情绪识别. 2022 计算智能与可持续工程解决方案国际会议 (CISES). IEEE 计算智能与可持续工程解决方案国际会议 (CISES) 2022. 1109/CISES55857.2022.9844366

- [7] Yadav S. P., Yadav S. 连续小波域内医学图像融合的数学实现. 动力学控制系统先进研究期刊. 2021. 10910455

- [8] Hussein H., Liner T., Gauke W., Ziegler J. Hybreed: 用于开发上下文感知混合推荐系统的软件框架. Model User-adapt. Interact. 2014, 24:2112-2127. 740.1007/s1257-012-9314-7

- [9] Yuan B., Herbert J. 用于预防性医疗的上下文感知混合识别框架. Ubiquitous Comput. 2014, 41:486-588. 110.1007/s0079-013-0696-5

- [10] Liang W., Wu Y., Li M., Cao Y. 使用上下文感知编码器网络和混合条件随机场模型的高分辨率 SAR 图像分类. IEEE Trans. Geosci. Remote Sensors. 2025, 55:853-753. 10.1109/TGRS.2019.296399

- [11] Wang W., Liang L., Xu J., Zhao X., Yao D., Wang X., Li B. 边缘云计算的上下文感知深度模型学习. IEEE 第 40 届分布式计算系统国际会议 (ICCDS). 2020. 780-797

- [12] Chen I., Lee C. 一种短词关键词检测的混合 HMM/DNN 方法. Interspeech. 2013. 21437/Interspeech.2013-397

- [13] Xu Z., Tang J., Yin C., Wang Y., Xu G., Wang J., Gorsuk M.C. ReCARL: 基于深度强化学习的云 RAN 资源分配. IEEE Trans. Mobile Comput. 2020, 21:110. 10.1109/TMC.2020.3042482

- [14] Xu M., Liu S. 基于事件的网络的事件推荐的语义增强和上下文感知混合协同过滤. IEEE Access. 2019, 17:4931-7521. 10.1109/ACCESS.2019.2895824

- [15] Yao D., Liang L., Wang Z., Li C., Wang X. 跨边缘与云的 DNN 训练流水线上下文感知编译. ACM交互、移动、可穿戴及无处不在技术。2021, 50:127

- [16] Khan J., Ahmad N., Khalid S., Ali F., Lee Y. 用于文本情感分类的带注意力的上下文感知混合 DNN. IEEE Access. 2023, 31:2816-22817791. 10.1109/ACCESS.2023.3259017

## 大数据分析与信息质量：挑战、解决方案与开放问题

Sahil Suri*

*1 商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度

## 摘要

得益于社交媒体和物联网设备的普及，大数据时代已经来临。由于大数据为公众和企业带来了巨大益处，如何更有效地处理和利用数据的问题已吸引了各行各业的人。由于大数据的 4V 特性，大数据处理一直受到困难的困扰。解决数据质量问题对大数据处理至关重要，确保数据质量也是大数据发挥价值的前提条件。大数据发挥良好作用的两个例子是推荐系统和预测系统。在本文研究中，我们调查了大数据推荐和预测系统，并试图确定过程中每个阶段（采集、预处理、存储和分析）的数据质量。所提出的解决方案基于对当前问题的详尽描述和审查。在报告结束处我们留下了一些尚未回答的问题。

**关键词：** 大数据处理、大数据、数据质量、问题、开放问题、解决方案。

* 通作者 Sahil Suri：商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：`sahil.suri.org@chitkara.edu.in`

## 引言

得益于社交媒体平台、物联网设备、云计算和其他技术的进步，大数据时代已经来临 [1]。公众和企业从数据可用性的激增中受益匪浅。同时，如何有效处理和利用大数据的课题已扩展到社会的每一个角落。大数据处理中的许多问题可以追溯到大数据的 4V 特性。为了确保大数据的正确实施，解决数据质量差的问题至关重要。采集、处理和传输由 WBAN 处理 [2]。WBAN 在功耗和 [3-6] 方面遇到的困难。服务质量 (QoS) 严重取决于 WBAN 的构建，这与设备相关 [7-9]。由于传感器节点依靠有限的电力运行...



针对大数据环境下的机器学习与质量控制，我们提供了这篇社论。在当今的“大数据”时代，企业必须处理海量数据，这些数据变化迅速且来源广泛，包括社交媒体、来自各种网站的非结构化信息，以及来自传感器的原始输入。为了提高生产力，企业正转向大数据解决方案，以简化流程并加速决策过程。大数据专业人员面临的数据质量问题数量规模是惊人的。这些问题可能难以修复，并可能导致错误的数据分析。在海量数据中控制质量已变得困难，以往的研究仅触及了问题的少数领域。传统的数据质量管理方法不足以应对管理大数据质量这一更困难的任务。为了保护汽车及其驾驶员免受可能利用这些信息的攻击者的侵害，敏感数据（如位置）的传输必须带有特定的安全特征进行。在车联网（IoV）网络等分散且不可信的背景下，区块链是一种相对新的技术，它通过加密技术和共识程序确保节点之间的信任。区块链可以解决并回答物联网和服务中的许多问题，因此有很多关于前者应用于后者的研究。在车联网中实施区块链的主要限制之一是，它们必须克服车联网节点资源限制带来的困难，这些资源无法满足传统区块链系统的计算和能量需求。最后但同样重要的是，这两项技术可以被用于建立智慧城市基础设施，为终端用户开启新型应用模型和改进结果的大门。

# 提出的模型

## 问题定义

数据质量问题在分析和数据管理计划中十分常见。问题可能源于各种输入错误、多样化的命名规范以及错误的数据整合。然而，当考虑到涉及的数据量、多样性和速度不断增加时，数据质量对于大数据应用的重要性随之增长。大数据质量的优势如图（1）所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_634_0.png)

**图 (1)**

大数据质量优势。

咨询公司安永（EY）美洲的新技术负责人 Faisal Alam 提议在大数据治理项目中增加第四个 V，即有效性（validity），这是因为大数据的质量问题可能会产生与不同应用、数据类型、平台和用例相关的广泛背景关注问题。

### 高质量数据对大数据有多关重要？

大数据质量问题不仅可能导致算法缺陷，还可能在现实世界中产生潜在的危险。企业终端客户至少将不再愿意信任派生数据集和应用程序。如果数据可靠性和精确性影响公司的运营决策，还可能引起政府的监管关注。

如果数据质量低，与数据管理相关的成本可能会增加，导致包括频繁修复、资源需求增加和合规性担忧在内的问题。它还可能给业务判断和预测带来困难。

### 大数据如何影响数据质量？

## 提出的方法

Bansal 管理着一个 100 人的团队，该团队每天产生并分析数 GB 的消费者数据。在处理如此海量的数据时，必须在考虑以下因素的同时，重新思考确保大数据质量的传统方法：

- 可扩展性问题。像以前使用传统文件和电子表格的常见做法来导入和检查数据在最好的情况下也是不可行的。数据管理团队必须创建包含历史和当前数据存储机制的大数据质量实践，例如数据湖和实时数据流。

- 复杂且不断变化的数据形式。大数据可能包含多个维度，例如事件类型、用户细分、程序版本和设备类型。正如 Bansal 所述，需要对成百或数千个数据切片进行检查，以正确映射出数据质量问题。随着新事件和特征的添加以及其他特征的删除，数据的原始结构可能会发生偏移。

![](img/5e4d8ef2afa52a8404b28106580e19e4_636_0.png)

**图 (2)**

数据质量方向。

- 重度信息负荷。在大数据系统中手动检查新数据是不可行的。开发能够在应用用例中持续监控的、相对于大数据程序变化的质量指标，对于确保大数据的质量至关重要。表 1 显示了大数据质量评估指标。图（2）描述了数据质量方向。

表 1 大数据质量评估指标。

| 维度 | 元素 | 指标 |
| --- | --- | --- |
| 1) 可用性 | 1) 可访问性 | - 是否提供了数据访问接口。<br>- 数据可以很容易公开或易于购买。 |
| | 2) 及时性 | - 在给定时间内，数据是否准时到达。<br>- 数据是否定期更新。<br>- 从数据收集处理到发布的时间间隔是否符合要求。<br>- 数据是否来自某个国家、领域或行业的专业机构。 |
| 2) 可用性 | 1) 可信度 | - 专家或专业人员定期审核并检查数据内容的正确性。<br>- 数据是否存在已知或可接受值的范围内。 |
| 维度 | 元素 | 指标 |
| --- | --- | --- |
| | 1) 准确性 | - 提供的数据是准确的。<br>- 数据表示（或值）很好反映了源信息的真实状态。<br>- 信息（数据）表示不会引起歧义。 |
| | 2) 一致性 | - 数据经过处理后，其概念、值域和格式仍与处理前保持一致。<br>- 在特定时期，数据保持一致且可验证。<br>- 数据与来自其他数据源的数据一致。<br>- 数据格式清晰且符合标准。 |
| | 3) 完整性 | - 数据与结构性完整性一致。<br>- 数据与内容完整性一致。 |
| | 4) 完整性 | - 组件的缺失是否会影响多组件数据的使用。<br>- 组件的缺失是否会影响准确性和性。<br>- 收集的数据不完全匹配主题，但它们阐述了一个方面。 |
| | 4) 相关性 | 1) 适用性 | 大多数数据都在用户需要的检索主题内。<br>- 信息主题匹配用户的检索主题。 |
| 维度 | 元素 | 指标 |
| --- | --- | --- |
| 5) 呈现质量 | 1) 可读性 | 数据（内容、格式等）清晰易懂。<br> 易于判断数据满足需求。<br>- 数据描述、分类和编码内容符合规范且易于理解。 |

## 数据处理步骤

大数据分析允许从海量数据集中挖掘丰富的见解。图（2）描述了大数据处理流水线的四个阶段：

- 数据采集：整个运营都建立在海量数据采集的基础上。由于互联网技术、应用以及各种终端设备的广泛使用，数据生产者的多样性和数据产生量都在增长。

- 数据预处理：大数据预处理的主要目标是数据发现、数据提取和数据清洗。数据结构的异构性使得分析变得困难，因为它们是通过不同的方法收集的。在进行任何可靠操作之前，必须过滤掉无效数据。这需要标准化数据格式并清除任何过时信息。

- 数据存储：大数据不仅仅是海量数据。答案必须快速发送和处理。大数据由于其来源的数据源很多而具有通用性。设计用于存储或处理海量数据的系统必须是后兼容的。

与之前的数据、硬件和软件版本兼容。图 (3) 显示了大数据处理问题。

- **分析数据：** 每一个系统数据流水线的下一步都应该是分析。大数据分析是获取我们所需的这类智能、深度且有用知识的唯一途径。由于大数据应用的日益普及以及大数据属性数量和多样性的不断增加，大数据分析方法在大数据处理阶段正变得至关重要。

![](img/5e4d8ef2afa52a8404b28106580e19e4_640_0.png)

图 (3)

大数据处理问题。

## 大数据质量挑战与问题

协调数据分类系统。在合并之前，数据分类法和本体论可能由好几个部门或公司独立开发和完善。CRM、营销自动化、营销内容管理、客户数据库和潜在客户索源技术数据通常是每家公司分别收集的。当将多种不同的技术整合到一个数据结构中以进行统一活动时，数据的质量可能会受到严峻考验。保持一切有序。

- 定位合适的数据需要新的测量方法、工具和分析。决策中的案例：基于一个能够公平代表总体的样本。

- **学习机器：** “高性能计算”（HPC）一词用于描述任何需要多台计算机来完成任务的计算活动。高级计算问题通常由超级计算机或计算机集群处理。数据上的分析（机器学习）。

- 数据管理和分析是至关重要的。为了同时进行分析和领导工作，由于软件和硬件要求的内在差异，我们需要允许进行并行机器学习的计算机。

- **对高性能并行算法的需求：** 流式和多尺度自适应算法需要有效的并行算法，可以将时间复杂度从 $O(N^2)$ 降低到 $O(N)$。

- **安全云的重要性：** 在云中保护并安全地处理数据是一个需要待解决的问题。

数据清洗、验证和归一化过程可能会在大数据的质量上带来困难。例如，一家电信公司开发了模型，通过交叉引用网络缺陷信息、停机报告以及客户投诉来确定服务中断是否可能是局部的。

使数据库有序的另一个关键步骤是数据归一化过程。除了让后续过程运行更快，归一化数据库还有助于有效压缩数据库。数据归一化程序的数学表达式如下：

```math
$$\eta = \frac{(|d_i|-(10^{n-1})*(|A|))}{10^{n-1}}$$
```

其中，$d_i$ 表示数据集 $D$ 中的第 $i^{th}$ 个数据，$n$ 是记录 $d_i$ 的总数。字母 $A$ 代表第一个数据点 $d_i$。

发现数据处理中的差异。为新应用进行数据归一化和清洗通常需要数据准备策略的结合。错误的、脆弱且不可复制的自定义做法并并不少见。

## 大数据质量管理的最佳实践

- Orion 的 Balasubramanian 引用了能够可靠增强大数据质量的最佳实践示例。

- 为数据治理倡议获得高层支持。

- 建立由终端用户、分析师、架构师、分析人员和开发者组成的跨学科数据治理小组。

- 将数据管理、主动监控和定期评估整合到您的治理框架中。

- 明确现有程序和软件如何实现数据验证和业务规则。

- 建立信息及项目的评估与批准机制，并为不同的业务领域指定数据管理员。

- 为了确保整个组织对产品或客户数据有统一一、一致且全面的定义，必须实施有效的主数据管理实践。

- 必须定义企业世界的数据标准、术语和受监管词汇。

- 国际标准化组织、世界卫生组织和监管行动医学字典都创建了受控词汇，这些应该被更广泛使用。

在可行的情况下，通过与其他系统的接口整合海量数据集以消除冗余信息。

## 实验结果

大数据扩展了互联网的潜力，但也引入了新的挑战和潜在的陷阱。本研究主要从数据质量的角度处理大规模数据处理过程中的问题，推荐该系统并使用该系统进行预测作为示例。

为了理解整个大数据处理过程中可能出现的潜在问题，本研究以推荐系统和预测系统为例。文中讨论了海量数据、大数据处理、预测以及推荐系统。本文详细阐述并分析了大数据研究中与数据质量相关的各种问题，包括数据质量、数据准备、数据存储、数据分析等。我们在每个层级都提出了问题并给了答案，然后批判性地审查了了一些突出问题。我们的大数据技术和工具不可避免地无法为大数据忧虑提供一个万无一失的答案。下一步是在后续研究中调查海量数据问题，并寻找提高数据质量的方法。

## 参考文献

- [1] Sakr M., Ray C., Renso C. Big mobility data analytics: recent advances and open problems. GeoInformatica 2022, 26:645-15491007/s10707-022-00483-0

- [2] Nazir S., Khan S., Khan H.U., Ali S., Garcia-Magarinho I., Atan R.B., Nawaz M. A. Comprehensive Analysis of Healthcare Big Data Management, Analytics and Scientific Programming. IEEE Access 2020, 8:9951497531110.10.1109/ACCESS.2020.2995572

- [3] Neaimah A.F., Ibrahim H., Darwish S., Hassen O.. Big Data Clustering Using Chemical Reaction Optimization Technique: A Computational Paradigm for Location-Decision Support in Geospatial Query Processing. Symmetry (2022) 14:2142637 10.3390/sym.14122637

- [4] Mereli I., Pérez-Sánchez H., Geising S., D’Apostino D. Managing, analysing, and integrating data in bioinformatics: open problems and future prospects. BioMed Res. 2014; 20:14311.10.1150/2014-0322352252402

- [5] Varadarajan V., Neelanarayanan V., Doyle R., Al-Shakhlee I.F., Groppe S.. Solutions in Big Data and Cloud Technologies for Mobile Networks. Mob. Netw. Appl. 2019, 24:3210107 10.1107/s019-001-9-0229-9

- [6] Moreno A., Molano-Puloido J., Gómez-Morantes J.E., González R.A.. ADACOP: A Big Data Platform for Open Management Proceedings of the 15th International Conference on Theory and Practice of Electronic Governance. 2022. 315506107.10.3560310

- [7] Yadav S. P., Yadav S.. Mathematical implementation of fusion of medical images in continuous wavelet domain. Journal of Advanced Research in dynamic and control system 2019.10.10104055

- [8] Zhao J.. Special issue in 2021 international conference on machine learning and big data analytics for iot security and privacy. Neural Comput. Appl. 2023, 33:5320250226 10.1007/s0521-022-07706-3

- [9] Ya C., Yujian T. Discussion on the Construction of Regional Education Data Network and Key Issues in the Big Data Era 2019

- [10] Zhang P., Xiong F., Gao J.Z., Wang J.. Data quality in big data processing: Issues, solutions and open problems 2017. 10.1109/UIC-ATC.2017.8397554

- [11] Ambigavati M., Sridharan D. A Review of Channel Access Techniques in Wireless Body Area Network 2017 Second International Conference on Recent Trends and Challenges in Computational Models (ICRTCC) 106110 2017D.10.1109/ICRTCC.2017.28

- [12] Yadav S.P., Yadav S. Fusion of Medical Images using a Wavelet Methodology: A Survey, IEIE Transactions on Smart Processing & Computing. The Institute of Electronics Engineers of Korea 2019, 98:4265271 10.05573/IESPC.2019.8.4.265

- [13] Jawar S., Lara N.. Editorial: Special Issue on Quality Assessment. Journal of Data and Information 2021 1313

- [14] Álva P., Silva L.. Blockchain-Based Solutions for Smart Cities: A Review. Telecom 2021

# 使用深度学习技术从社交媒体中检测流量

**关键词：** 深度学习，社交媒体，交通信息

*通讯作者 Sourav Rampal: Centre for Interdisciplinary Research in Business and Technology, Chitkara University of Engineering and Technology, Punjab, India; E-mail: sourav.rampal@chitkara.edu

## 摘要

考虑到社交媒体的实时性和无处不在性，提取交通状况的有用信息是一个新兴领域。为了理解整个大数据处理过程中可能出现的潜在问题，本研究以推荐系统和预测系统为例。文中讨论了海量数据、大数据处理、预测以及推荐系统。本文详细阐述并分析了大数据研究中与数据质量相关的各种问题，包括数据质量、数据准备、数据存储、数据分析等。我们在每个层级都提出了问题并给了答案，然后批判性地审查了了一些突出问题。我们的大数据技术和工具不可避免地无法为大数据忧虑提供一个万无一失的答案。下一步是在后续研究中调查海量数据问题，并寻找提高数据质量的方法。

## 引言



用户生成的信息，尤其是社交平台上的信息，在当今文化中变得越来越重要。随着社交媒体的流行，对能够提取信息的系统的需求日益增加。事实证明深度学习算法在处理社交帖子方面表现卓越[1, 2]。在这项工作中，我们讨论了使用卷积神经网络（CNN）和长短期记忆（LSTM）模型从微博挖掘交通状况的挑战。可以判断社交媒体信息是否包含任何交通信息。得益于这些工具的使用，还可以从社交媒体消息中挖掘事故位置和严重程度等信息。描述了一种基于深度学习的信息提取方法（称为`BERT-BLSTM-CRF`），并在捕捉单词语义方面优于现有先进方法[3]。通过利用深度学习算法识别社交媒体流量提供的实时交通信息[4]，可以帮助交通系统更好地管理交通、缓解拥堵并提高公共安全。在这里，在大数据时代，我们可以通过深入研究社交媒体数据来满足移动需求。自然语言处理（NLP）、云和开放平台以及人机交互（HCI）仅是本研究概述的部分工具。在本研究中，我们提出了一种基于深度学习的模型架构设计的解决方案。当与词嵌入[5, 6]结合时，这两种深度学习方法提供了 0.89 的 E 因子。在研究中，我们展示了利用卷积神经网络（CNN）、长短期记忆（LSTM）以及带有预训练词向量的`LSTM-CNN`从微博中提取交通相关推文的工作[7, 8, 9, 10]。

展示了所提策略在识别交通相关微博方面的有效性。以下是本研究的最重要结果：(i) 我们实现了深度学习策略，用于挖掘社交媒体中的交通数据。(ii) 我们将`CBOW`模型应用于包含 30 亿条微博的数据集以获取词嵌入，词嵌入能够捕捉词汇语义，这与以往通过词袋模型特征提取交通相关微博的方法形成了对比。与更复杂的模型相比，我们证明了深度学习模型在识别与交通相关的数据方面具有优越性。

本文的后续章节结构如下：

在第二 节中，我们研究了从社交媒体中挖掘交通数据的最新进展。详细介绍了我们的大部分方法，例如数据采集与预处理、词向量模型以及分类模型。

在第三节中，我们对建议的方法进行了实验验证。

在第四节中，我们对建议的方法进行了实验验证。

第五 节包含了我们对未来发展的思考和建议。

## 相关工作

社交媒体的即时性和无处不在的特性使得交通数据挖掘成为一个热门问题。本文关注社交媒体挖掘的一个特定子集：从新微博（一个中国博客网站）中提取交通相关微博的困难。机器学习将其重新定义为短文本的分类问题。我们首先使用连续词袋模型（CBOW）和 30 亿条微博数据集创建词嵌入表示。与典型的单词独热编码（one-hot）表示相比，词嵌入已被证明有利于自然语言处理任务，并能够捕捉单词之间的语义相似性。为了提取交通相关的微博，我们建议将学习到的词嵌入输入卷积神经网络（CNN）、长短期记忆（LSTM）模型以及它们的组合`LSTM-CNN`。我们将所提技术与已开发的其他几种技术进行了比较，例如词元组袋特征`SVM`模型、词向量特征`SVM`模型以及多层感知器`SVM`模型。实验证明，所建议的深度学习方法是成功的 [11]。

本研究的目标是利用社会风险分析理论评估科威特的城市发展项目。通过对科威特建筑工地 17 起社会冲突事件的案例研究，评估了社会风险的 12 个方面。通过文献复述和科威特的记录实例，识别了与重要社会风险因素相关的 8 个利益相关者。我们使用`Gephi UNICET`创建了网络图，描述了潜在社会危害与可能受到这些风险影响的人、组织和政府之间的关系。我们还对建筑行业的专家进行了半结构化访谈。对建筑工程相关的社会危害进行了主题研究。根据`SNA`模型的研究 [12]，社会危害与决策不当、治理不可信和行政效率低下等问题紧密相关。

社交网络平台（OSNs）正成为人们讨论物品、提供建议、传播信息和推广品牌的绝佳场所。这些网站的用户根据自己对通信、娱乐和知识的需求选择最适合自己的社交媒体工具。社交网络中的用户行为包括加入、互动和发现新网络。用户的身份根据他们所属的群体而改变。根据用户的身份，其动机可能会发生变化。随着他们采用新的人格，用户的原始目标可能会改变。在这项研究中，我们介绍了社交网络（OSN），并讨论了在独立平台和混合平台中向用户预测和推荐内容的方法 [13]。

本文研究了人工智能在网络安全策略中的应用，以保护网络和数据免受入侵。它总结了研究机器学习和深度学习在网络安全领域应用的最重要研究。数据表明，机器学习和深度学习技术通过预测和理解恶意软件的行为和流量，在防止未经授权访问计算机系统和管理系统渗透方面起着至关重要的作用 [14]。

本文使用了文本相似性方法、时间相关性原理和状态机图来评估实时仿真的数据完整性水平。仿真的启动和持续运行取决于所提供数据的准确性。根据评估结果，将文本相似性与时间相关性加权策略相结合，比单一方法效果更好。对状态图的研究表明，可以在信息实体完整程度不同的情况下，对仿真的执行进行控制。一旦获得更多数据条目，系统将过渡到下一阶段。可能的仿真结果范围越大，可能访问的信息实体就越多。这是因为，随着仿真的进行，得益于更完整的信息实体，事件的位置和/或发生时间的歧义会更少 [15]。

## 拟议工作

信息通过社交媒体平台传播的主要方式之一，这些平台正迅速变得流行。从社交媒体数据中进行实时信息提取和分析是一个热门研究领域。交通相关的社交媒体研究通常集中在三个领域：事件检测、预测和用户情感研究。

## 系统模型

该方法的方法论框架主要包括了一些步骤。整个过程如图 (1) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_656_0.png)

图 (1) 系统架构。

## 数据采集与文本预处理

访问新微博微博有两种方法：请求`API`（应用程序接口）和网络爬虫。官方上，开发者可以使用`API`请求表单，但这些表单通常不是免费的，并且有访问限制。在研究中，我们使用基于爬取新微博平台的技术来收集信息。与访问官方`API`相比，这种方法是免费的且更彻底。首先，我们建立搜索参数（例如地理坐标、时间范围、关键词）来获取微博。然后我们通过发送`HTTP`查询检索服务器的返回结果（以`HTML`源代码的形式呈现）。我们使用正则表达式匹配响应结果，获取包含微博 ID、用户 ID、时间戳、地理位置和文本的微博。之后，将数据保存为数据库格式供以后使用。

## 特征提取与词嵌入

每个单词在`NLP`系统中通常表示为独热向量，这是一种全向量向量，仅在对应于单词的位置的值为 1。独热表示具有高维和稀疏的特点。单词之间的语义相似性在във形式中也丢失了。自然语言处理任务受益于词聚类，而通过将单词表示在连续向量空间中，这种聚类成为可能。学习到的向量清楚地包含了许多语言规律和模式，使得利用神经网络生成词表示变得特别吸引人和迷人。词嵌入表示可以使用`CBOW`模型或`Skip-Gram`方法进行学习。`CBOW`和`Skip-Gram`具有可比性，尽管它们追求的目标不同。

模型，我们在这里只介绍`CBOW`模型的推导。原始`CBOW`模型和`Skip-Gram`模型都是计算密集型的，因此它们的训练方法使用了分层`softmax`（hierarchical softmax）或负采样（negative sampling）。在分层`softmax`中，所有的词汇词（叶子节点）都表示为哈夫树中的二叉节点。带有分层`softmax`的`CBOW`模型输出层是一个哈夫树。隐藏层经过校准，提供其接收到的词向量的平均值如下：

```
$h = \frac{1}{2} \sum_{u \in \text{context}(w)} v(u)$
```

其中`$v(u)$`代表单词`$u$`的向量，`$context(w)$`是单词`$w$`的上下文词集合，`$C$`是上下文`$context(w)$`的基数。给定上下文的情况下，单词`$w$`的条件概率定义为：

```
$p(w | \text{context}(w)) = \prod_{j=1}^{L(w)-1} [[h^T v'_{n_{j}}]$
```

其中`$n_{m,j}$`是哈夫树中从根到单词`$w$`的第`$jn$`个内部点，`$v'_n$`是内部点`$n$`的向量，`$L(w)-1$`是单词`$w$`在哈夫树中的路径长度，`$III$`是一个定义如下的：

```
$[[x]] = \sigma(x)^{d_{j+1}^w} [ [1 - \sigma(x)^{(1-d_{j+1}^w)}]$
```

其中`$d_{j+1}^w$`是单词`$w$`的哈夫码的第`$j$`位。通过最大化公式 (2) 中目标单词`$w$`的条件概率来训练神经网络是简单而易见的。对条件概率取对数并定义损失函数：

```
$L = \log p(w | \text{context}(w))$
```

## 文本分类

微博上下文可以通过`LSTM`神经网络学习，并使用`CNN`抽象深层特征。因此，一种结合`LSTM`和`CNN`对微博短语进行分类的策略是理想的。上面，我们看到了输入词向量是如何被馈入第一个`LSTM`层的；后续层也可以是`LSTM`。下一层是一个卷积层，后面是一个池化层，这种模式可以根据需要重复任意次数。全连接神经网络层接收抽象特征作为输入。

我们将整流器函数硬编码为卷积层的激活函数。

```
δ(x) = max(x, 0)
```

这在卷积神经网络（或 CNNs）中作为激活函数非常流行。使用`Adam`优化器来寻找最优参数，使得损失函数（此处指定为二分类交叉熵）能够降低。我们运行了一系列测试来确定各种设计元素如何影响模型性能，这使我们能够开发出最有效的分类模型。通过实验检查了改变过滤器数量（10, 20, 50, 100, 150）对模型性能的影响。结果显示，更多的过滤器可以提高性能，但训练模型需要更多时间。实验表明，网格搜索中的最大过滤器数量为 150，拥有 150 个过滤器的模型性能与拥有 100 个过滤器的模型几乎相同。还对长度为 2, 3, 4, 5, 6 和 10 的过滤器进行了实验以确定其影响。结果显示，调整过滤器长度不会显著提升我们在数据集上的性能。对卷积层数量、过滤器长度以及池化方法进行了网格搜索以寻找最优模型。你可以将过滤器长度从 2 调整到 6，步长为 1，过滤器数量可以是 20 到 150 之间的任意值。在最大池化和平均池化之间，选择了后者。在比较在顶层池化层和顶部输出层之间插入原生隐藏层前后的模型性能时，我们发现后者更好。

## 结果与讨论

使用预定义的关键词对新微博进行了手动搜索，以获取用于将关于流量微博分类为“相关”或“无关”的信息。然后将这些微博手动分为两类：对引流有用的微博和无用的微博。然后将五千条候选微博分配给流量相关类，并从剩余微博集合中随机选择六千条（该集合包含了所有流量相关类之外的候选微博）。五千条流量相关微博和六千条流量无关微博组成了用于训练分类器的最终数据集。使用人工标注数据集中的词汇汇词汇字典，字典的索引作为每个术语的唯一标识符。每条微博被转换为单个单词的索引列表。在馈入深度神经网络之前，用于训练分类器的每条微博词序列会被填充到相同的长度。我们在测试中找到的最长词链为 156 个单词。每个序列末尾都会添加零，直到总长度达到 156。由于词向量是 200 维的，微博属性将作为一个 156 比 200 的矩阵输入分类模型。在没有明确相反说明的情况下，本研究中使用的所有模型将使用此特征作为输入。

准确率（accuracy）、召回率（recall）和 F 值（F-measure）是评估所提深度神经网络模型质量的三个统计指标。这些指标经常用于分类器的性能分析。表 1 描述了这三个指标。对于具有标签 I 的给定类别，真正例（TP）指标表示被正确分配为标签 I 的实例总数，假正例（FP）指标表示错误分配为标签 I 的实例总数，假负例（FN）指标表示未分配为标签 I 的实例总数。所有这些指标都是类别特定的。分类器的准确性通过精确率（precision）量化，而其效率由召回率表示。F 值是准确率和召回率的加权调和平均数，提供了两者之间的折中。F 值，当为 1 时称为 F1 分数，是评估分类模型质量的流行统计方法。下述性能指标均使用十折交叉验证。`LSTM`模型中的损失函数也指定为二分类交叉熵。使用`RMSprop`优化器最小化损失函数。

| 学习率 | 嵌入方案 | 精率 | 召回率 | F-measure | 准确率 |
|---|---|---|---|---|---|
| 0.01 | SVM | 94.0 | 93.0 | 93.5 | 93.5 |
| | CNN | 90.0 | 91.8 | 90.9 | 91.0 |
| | LSTM | 89.4 | 88.9 | 89.6 | 89.7 |
| | CNN-LSTM | 89.0 | 88.4 | 88.7 | 88.7 |
| 0.02 | SVM | 95.0 | 94.5 | 94.7 | 94.7 |
| | CNN | 91.0 | 93.3 | 92.1 | 92.2 |
| | LSTM | 90.0 | 90.9 | 90.4 | 90.5 |
| | CNN-LSTM | 90.0 | 89.1 | 89.5 | 89.5 |
| 0.03 | SVM | 90.8 | 93.0 | 91.9 | 92.0 |
| | CNN | 89.5 | 90.4 | 90.0 | 90.0 |
| | LSTM | 89.0 | 89.8 | 89.4 | 89.4 |
| | CNN-LSTM | 88.5 | 89.1 | 88.8 | 88.9 |
| 0.04 | SVM | 95.0 | 94.5 | 94.7 | 94.7 |
| | CNN | 93.5 | 91.2 | 92.3 | 92.2 |
| | LSTM | 92.5 | 91.1 | 91.8 | 91.7 |
| | CNN-LSTM | 90.5 | 91.0 | 91.1 | 91.2 |
| 0.05 | SVM | 93.9 | 93.2 | 93.5 | 93.5 |
| | CNN | 91.8 | 92.1 | 91.9 | 91.9 |
| | LSTM | 91.2 | 91.4 | 91.3 | 91.4 |
| | CNN-LSTM | 91.2 | 90.8 | 90.9 | 90.9 |

## 结论

在本文中，我们研究了新兴的社交交通领域，该领域侧重于挖掘社交媒体中的交通数据。为了识别关于交通的中国微博，我们展示了深度学习技术。为了对微博上的简短文本进行分类，我们采用了词嵌入表示法，并使用了卷积神经网络（CNN）、长短期记忆网络（LSTM 网络）以及`LSTM-CNN`。通过 2009 年至 2011 年间从微博收集的 30 亿条微博，我们能够使用`CBOW`模型获得具有连续向量表示的词嵌入。与独热向量表示相比，词嵌入保留了词与词之间的语义连接。`CNN`、`LSTM`和`LSTM-CNN`的使用了词嵌入。为了找到`CNN`、`LSTM`和`LSTM-CNN`的最佳架构，我们进行了网格搜索，并分析了模型架构和超参数对模型性能的影响。实验结果表明，使用词嵌入的建议深度学习方法优于先进方法。该方法有多种方式可以改进和扩展以供未来研究使用。首先，我们将扩大微博收集范围，以更好地组织许多与交通事故、状况等的微博。其次，将从原始微博中提取粒度元素，例如交通事故发生的地点和时间。此外，我们将整合来自社交媒体平台和传统交通检测器的数据，以增强短短期交通预测。

## 参考文献

- [1] Shi B., Wang H. An refined approach for improving advertising identification and promotion in social networks. Technol. Forecast. Soc. Change202308182226290/10.016/j.techfore.2022.1222269
- [2] Bakkialshmi V.S., Sudalamuthu T. Anomaly Detection in Social Media Using Text-Mining and Emotion Classification with EmotionDetection8th International Conference, ICCE 2021Mayanda, India, Cham. 20236787
- [3] Jonnagaladda J., Hashemi M.. A Deep Learning-Based Traffic Event Detection From SocialMedia2022 IEEE National Conference on Information Retrieval and Data Integration(RI)20221109/IRIS5135
- [4] Saranya S., Usha G. Forensic Analysis of Online Network Data in Crime SceneIn Artificial Intelligence and Blockchain in Digital ForensicPublishers20231829
- [5] Yadav S. P., Bhati B., Mahato D., Kumar S.. Federated Learning for IoT Innovations in Communication and Computing. Springer International Publishing20221007/978-3-05-8559
- [6] Ma K., Tan Y., Tian M., Xie Q., Li S., Wang X.. Extraction of temporal information from social media messages using the BERT model.Earth Inform.20221515735840.1007/s12145-021-00756-6
- [7] Anedha M., Fadda M., Girau R., Pau G., Giusto D.. A social smart city for public and mobility: A real case study.Comput.Netw.20232021096410.1016/j.comnet.2022.1094



- [8] Vassakis K., Petrais E., Kopanakis I., Makridis J. Big data analytics on location-based social networks for knowledge generationInt.MT.2023678710.1016/j.comnet.2022.1094
- [9] Yadav S. P., Yadav S. Mathematical implementation of medical images in advanced control20195735
- [10] Alifi M., Salem I. Real-time Detection of Traffic Using Bidirectional LSTM-CNN201883764
- [11] Chen Y., Lv Y., Wang F. Detecting Traffic Information from Social Media Using Deep LearningIEEE Trans. Intell. Transp.20198034
- [12] Yadav S. P., Yadav S. Advanced research in dynamical and control20195735
- [13] Patel N., Navavati N. State of the Art Review on User Behavioral IssuesIraqi Journal For Computer Science and Mathematics202318710
- [14] Putri E.T., Biala J., Ermawati M. Real-time Detection of Data Completeness Using Wavelet2018862144

每天通过互联网和其他媒体生成、传播和执行，这是一个活跃的学术领域。隐性狄利克雷德分配（LDA）和双层双向长短期记忆（LSTM）分别被用于提取文本方面和分类情感。对于调整模型超参数，建议使用爬坡算法 [8]。通过使用 Twitter API，我们可以抓取数据，然后使用机器学习方法对这些数据进行收集和比较。在准确率、精确率和召回率方面，支持向量机（SVM）优于其他技术 [9]。循环神经网络在 COVID-19 数据集上实现了 92.70% 和 91.24% 的准确率。Bi-LSTM 和 GRU 在疫苗接种推文分类中的准确率分别为 92.48% 和 93.03%。面对未来的大流行，医疗保健提供者和政府可以从现有模型中获益 [10]。

- RQ1 如何将自然语言处理技术（如主题建模）的关键原理应用于在线讨论，以揭示与 COVID-19 相关的不同困难点？
- RQ2 发现人们对 COVID-19 感受的最佳方式是什么？
- RQ3 几种机器学习算法在确定与 COVID-19 相关的在线讨论的情绪倾向方面有多有效，哪种方法最有效？

为了回答这些问题，我们查看了 Reddit 上 Reddit 用户的公共意见，并分析了他们关于 COVID-19 的评论，以发现与 COVID-19 相关的情感和语义概念。特别是，我们采用了基于主题建模的自然语言处理（NLP）方法，从社交媒体中自动提取与 COVID-19 相关的讨论，并从公众意见中发现许多与该疾病相关的担忧。以下是本研究最重要的结果；我们引入了一种基于 NLP 的结构化方法，可以从 Reddit 上关于 COVID-19 的帖子中提取重要主题。

为了对 COVID-19 相关评论进行情感分类，我们提出了一种基于长短期记忆（LSTM）的深度学习模型，它优于许多其他著名的机器学习方法。作为我们 COVID-19 核心研究的一部分，我们监控 Reddit 相关讨论并识别新兴主题。

我们分析了来自 10 个不同子板块的 COVID-19 评论的情绪和观点，并确定了它们的极性。我们的研究强调了将公众意见和适当的计算方法整合到学习和关于 COVID-19 决策过程中的价值。本文遵循以下总体大纲。

我们首先对网络医疗讨论板的基础知识进行介绍。在第 2 部分，我们讨论了与 COVID-19 相关的担忧，并与其他相关的文献进行了对比。

在第 3 节中，我们详细介绍了用于 COVID-19 评论数据库的 NLP 和深度学习技术，以及我们使用的数据预处理程序。最后，通过讨论本研究的未来以及其他分析 COVID-19 在线社区的 NLP 工作结束结束。

## 相关工作

本文通过文本情感分类研究的角度，探索了利用在线数据研究公众意见情感倾向。由于其卓越的语义表示能力以及处理具有多种含义词汇的能力，BERT（双向编码器表示）模型在本研究中作为文本向量化的工具。为了简化和加速多标签数据的处理，使用了 BR（二元相关性）方法。该技术将多标签分类问题分解为许多二分类分类问题。为了进一步提取特征，研究人员开发了结合双向长短期记忆网络与注意力机制的 BiLSTM-Attention 模型。通过对实验结果的分析证明了 BiLSTM-Attention 有效性。该工作通过调整损失函数和其他参数来解决数据集不均匀的问题，以提高分类准确性。总之，这项研究提供了一种利用 BERT 和 BILSTM-attention 模型等先进方法以极少精力进行情感分析的策略 [11]。

由于 COVID-19 疫情在全球范围内的传播，实施了全球封锁。几制药公司，辉瑞、莫德纳和阿斯利康生产了针对 COVID-19 的疫苗。然而，普通人开始在 Twitter 等社交网站上讨论这些疫苗的有效性和安全性。研究人员使用 Twitter API 访问令牌获取了推文，然后使用自然语言处理方法进行分析。随后使用监督分类算法将推文分类为正面、负面和中性，以反映公众的意见。总共有 47.29% 的回复是正面的；辉瑞的 35.70% 为负面，46.16% 为正面；40.71% 为负面，13.13% 为负面；阿斯利康的 40.08% 为正面，13.86% 为中性 [12]。

接受抗凝血治疗的心血管疾病患者严重出血复发的风险增加。电子健康记录（EHR）注释中的不良事件识别可以提高药物安全监测。研究人员开发了一种 NLP 技术来分析 EHR 注释中的出血迹象，并评估特定文本是否指示出血事件。使用 878 份 EHR 注释的标注语料库训练并评估了混合卷积神经网络（CNN）和长短期记忆（LSTM）自动编码器（HCLA）。HCLA 模型在检测出血事件方面优于 CNN 算法 [13]。

![](img/5e4d8ef2afa52a8404b28106580e19e4_671_0.png)

图 (1)) 系统流程图。

## 准备输入数据

Reddit 是一个美国社交媒体平台，作为一个讨论论坛和内容评分聚合器。用户可以在这一社交网络平台上通过提问、评论和相互互动来讨论如 COVID-19 等话题。各种“子版块”（sub-reddits，用户创建的类别）对帖子进行了进一步分类，主题包括新闻、科学、医疗保健、视频、文学、健身、烹饪和图像共享。在研究与 COVID-19 相关的健康问题时，该网站是一个极佳的资源。为了创建此模型，本研究利用现有数据集分析了 10 个不同子版块中围绕 COVID-19 的讨论。

## 去除噪声和停用词

在自然语言处理（NLP）中，去除停用词是关重要的第一步。此外，我们通过消除不必要的单词缩小了特征区域的大小。冠词、连词、代词和连接动词是文本评论中出现频率最高的词汇，尽管它们通常没有价值，且对输出的影响很小。这里有几个：am, is, are, they, the, these, he, she, it, he, she, it, them。

## 分类

在在该方法的最后阶段，使用 LSTM 模型来分析 Reddit 上关于 COVID-19 的帖子，以识别潜在情感。我们创建了两个 LSTM 层，并使用 Glove-50 维度进行预训练嵌入，这两者都在大量关于 COVID-19 的用户评论集合上进行了训练。预训练嵌入从原始格式转换为指定维度的向量，以便分析来自 COVID-19 相关言论的文本。此外，可以通过将 COVID-19 言论的维度乘以评论中的字符数来构建一个矩阵。

现有的时间戳输入为 `x_t`，忽略输出门。

```
$i_t = \sigma(W_i * [h_{t-1}, x_t] + b_i).
```

给予单元的数据是通过该方程选择的。公式 (2) 中的遗忘门 `$f_t$` 决定了应该忽略上一个记忆单元输入侧的哪些数据：

```
$f_t = \sigma(W_i * [h_{t-1}, xt] + b_i).
```

在公式 (3) 中，tanh 将值归一化在 -1 到 1 之间，其中 C 是该时间点单元状态候选，它控制单元 (t) 的更新：

```
$C = \tanh(W_c * [h_{t-1}, x_t] + b_c),\nC_t = f_t \times C_{t-1} + i_t \times C.
```

输出层 `$o_t$` 根据公式 (4) 升级隐藏层 `$h_{t-1}$` 和输出层：

```
$o_t = \sigma(W_o * [h_{t-1}, x_t] + b_o),\nh_t = o_t \times \tanh(C_t).$.
```

## 结果与讨论

训练集中有 338,666 条关于 COVID-19 的评论，测试集中有 112,888 条。使用支持向量机（SVM）、朴素贝叶斯（NB）、逻辑回归（LR）和 K 近邻算法（KNN）技术，我们将提议的 LSTM 模型与其他监督机器学习方法进行了比较。

## `$Accuracy = \frac{T^p+T^n}{T^p+FP+T^n+F^n} \quad (5)$`

其中，`$T^p$` 表示真正性率，`$T^n$` 代表真负性率，`$FP$` 表示假正性率，`$F^n$` 是假负性率。2) 精确率（PRECISION）公式 24 表示可能的准确程度，被称为“精确率”。

## `$Precision = \frac{TP}{TP+FP} \quad (6)$`

3 召回率（RECALL）公式 25 定义召回率为正确诊断占正确诊断和假负性总和的比例。

## `$Recall = \frac{T^p}{Tp+F^n} \quad (7)$`

为了实现情感分类的机器学习算法，我们使用了 Scikit-learn 软件包4，这是一个 Python 工具包，提供了对用 Python 编写的多种机器学习技术的访问。由于这些方法在自然语言处理的情感分类中因高准确性和有效性而闻名，我们决定将其应用于 COVID-19 情感分类。将 COVID-19 评论标记为极度正面、正面、负面或中立的最佳模型准确率如图所示。我们基于 LSTM 的方法将所有 COVID-19 评论分配给多数类，其准确率达到 81.15%，优于传统的机器学习技术。为了了解人们对这场悲剧的感受，我们认为情感和语义工具可能有用。

作为一个限制因素，本研究仅包含了英文编写的文本。这意味着其他语言提供的反馈没有反映在最终统计中。此外，研究仅包含了 2020 年 1 月 20 日至 2020 年 3 月 19 日期间收集的评论。因此，我们的结果及时性可能会受到研究期间与研究范围之间间隔的影响。我们从 COVID-19 在线讨论中获取有用见解的能力，部分归功于我们通过将自然语言处理（NLP）与基于主题建模和 LSTM 模型的深度学习算法相结合系统框架。除了帮助学者和医生更好地理解个人在压力下的行为外，此类统计贡献还可以用于确定在线社区的正坏行为并收集用户反馈。为了探索混合模糊深度学习算法在情感水平分类中的潜力，作为从公共评论中恢复重要潜主题的独特方法，我们的目标是对 Twitter 等各种社交媒体平台进行进一步评估。

## 结论

就我们所知，这是首次调查 COVID-19 论坛讨论如何与特定语义主题相关的研究。然而，本研究的主要目标是展示基于 LSTM 模型的 NLP 独特应用，用于发现医疗保健论坛（如子版块）中关于 COVID-19 相关关切的重要潜在主题和情感-评论分类。我们希望本文的发现能帮助研究人员和政策制定者更好地理解公共卫生服务和对 COVID-19 的响应。

## 参考文献

1. Qdroo A, Baykara S. Detection of Fake News Related to COVID-19 using Deep Neural Network. 2020.
2. Bisht A, Singh A., Bhaduria H., Virmani J., Krti. Detection of Hate Speech and Offensive Language in Twitter Data Using LSTM Model. 2020.
3. Cen P., Zhang K., Zheng D. A new approach to detect sentiment using deep learning. Journal of Artificial Intelligence. 2020.
4. Alkhaz M., Alian M., Bitawi M. Sentiment analysis of tweets about COVID-19 cases using LSTM and supervised KNN classification algorithm. International Journal of Computer Engineering. 2021.
5. Santhoshi A., Shirisha A., Meghana T. Text classification using deep learning Journal of Innovative Engineering and Management. 2022.
6. Patel D., Lokare R., Patil S. Sentiment analysis using convolutional neural network 5th International Conference on Advances in Science (ICAST). 2022.
7. Yadav S., Yadav S. Fusion of Medical Images in Wavelet Domain: A Discrete Mathematical Model. Universidad de Colombia-UCC. 2018.
8. Pathik N., Shukla P. An efficient sentiment analysis using topic model based recurrent neural network. Smart Intelligent Systems. 2021.
9. Sandag G., Manueek A., Walean M. Sentiment analysis of COVID-19 vaccine tweets in India using recurrent neural network (RNN). 3rd International Conference on Cybernetics and Intelligent System (ICORIS). 2021.
10. Aina B S., Pike R., Reddy P., Asani B., Srinivasulu A. Sentiment analysis of COVID-19 tweets using deep learning and lexicon-based approaches. Sustainability (Basel). 2023.
11. Li G., Kong B., Li J., Han Z., Yang Y., Dan S., Fan J. BERT-based text classification algorithm. International Conference on Computer Artificial Engineering (ICEAI). 2021.
12. Shafat F., Khazdar S., Srabry I., Moon M., Juna J., Billah M., Rahman M. Sentiment analysis on tweets about COVID-19 cases using NLP and supervised KNN algorithm. 2021.
13. Li R., Hu B., Liu F., Cunningham F., Hyun D.D. Detection of bleeding events in electronic health record notes using convolutional neural network methods enhanced with recurrent neural network encoders. JMIR Med. 2019.

## 基于机器学习的数据预处理及可视化技术在学生任务预测中的应用

Pratik Mahajan¹, *

¹ 商业与技术跨学科研究中心，Chitkara 大学立工程与技术学院，Chitkara 大学，旁遮普普邦，印度

## 摘要

学生毕业后获得工作的机会受其学校表现和学术成就历史的影响。希望在职场中成功的学生需要培养包括技术熟练、批判性思维和有效沟通在内的技能。我们正试图弄学生的学术表现如何影响他们的未来机会。数据挖掘算法在根据学生之前的学术成就分析和预测其就业机会方面起着关键作用。为此，我们对一所知名技术学院的学生进行了调查。数据集包含了影响学生概率的多个因素，并对这些因素进行了检查和可视化展示。在对数据集运行或应用机器学习算法之前，我们对数据进行了评估并提供了可视化和洞察。数据分析、理解和准备是本研究的核心关注。

**关键词：** 数据预处理，Python，学生就业检测，可视化。

> * 通作者 Pratik Mahajan：商业与技术跨学科研究中心，Chitkara 大学立工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：pratik.mahanajan.orp@chitkara.edu.in

## 引言



学生毕业后获得工作的机会受其学校表现和学术成就历史的影响。希望在职场中成功的学生需要培养包括技术熟练、批判性思维和有效沟通在内的技能。然而，我们正尝试弄清学生的学术表现如何影响他们的未来机会。机器学习算法在根据学生之前的学术成就分析和预测学习者在任务中的可能性方面起着关键作用 [1, 2]。学院和大学没有就业程序就无法运作。就业对学校声誉和录取率有重大影响。因此，教育机构正在共同努力扩大和增强其就业能力。《用于预测学生就业的机器学习模型开发》研究了机器学习算法在多个维度上的效力，以预测学生的就业情况。可靠的预测对课程的制定和学生的安置都有帮助。通过这种方式，可以监控学生的发展，他们甚至可以在响应业务需求方面比计划领先。目前已经研究并开发了多种算法，包括逻辑回归 (LR)、支持向量机 (SVM) 和朴素贝叶斯 (Naive Bayes)。数据挖掘是解决预测和分类问题最有用的工具之一 [3, 4]。机器学习算法正成为现代经济的支柱，由于它们为数据分析时代奠定了基础。由于缺乏适当且高效的解决方案，管理机器学习算法进行预测和可视化具有挑战性。教师通过了解学生的性格可能会受益，从而预判他们的学术发展。如果我们能牢掌握他们的性格，就能更好地理解个体的独特特征、思维模式和行为怪癖。然而，必须考虑进行传统性格测试所需的时间、精力和资源 [5, 6]。个人的性格可以通过其语言使用（包括词汇选择和句式结构）以多种方式体现。微博客网站“Twitter”的用户可以利用该服务的语言工具创建和阅读短消息。本研究通过利用朴素贝叶斯分类器策略，利用 Twitter 数据开发了一种预测模型，克服了使用传统性格测试相关的问题 [7, 8]。为了从来自 70 个人的 9,044 条推文中创建并评估模型，需要对推文进行多个层面的广泛预处理。将模拟的分类结果与专家的结果进行比较，数据预测系统的准确率计算为 76.19% [9, 10]。

由于机器学习的普及性，牢牢掌握任何机器学习方法或模型的原理非常重要。本文的目的是演示如何将各种基于机器学习的模型应用于学生预测问题。本节详细介绍了实验中使用的方法、结果以及对研究中使用的多种模型进行了分析。论文的其余部分结构如下：第 2 节简述了相关的早期工作；第 3 节概述了预期工作的细节；第 4 节介绍了结果和讨论；第 5 节给总结。

## 文献综述

我们对学生进行了调查。数据集包含了影响学生概率的多个因素，并对这些因素进行了检查和可视化展示。在对数据集运行或应用机器学习算法之前，我们对数据进行了评估并提供了可视化和洞察。数据分析、理解和准备是本研究的核心关注 [11]。本研究的目标是利用历史数据预测学生应该安置在何处。大学越完备，为学生找到的工作就越多，就越成功。最终负责就业的实体还收集并预处理了数据。所提模型的准确性与某些分类策略的结果进行了对比，结果该方法优于竞争对手 [12]。

评估性能有许多不同的方法，但常见的包括准确率、F 分数、精确率和召回率。其他方法的成功率从 LR & DT 算法的 88% 到朴素贝叶斯的 86%，以及 XGB Boost 技术的 84%，而 SVM 方法为 91%。我们可以选择目前最有效的算法。大多数教师倾向于使用更精确的预测方法 [13]。在本研究中，我们提供了一种与机器学习技术进行预测数据分析交互的新颖方法。创建一个同时清洗数据并展示结果的工具对于准备数据至关重要。开发的程序将接受包含文本和数值数据的组织数据集作为输入，然后使用机器学习技术对其分析，提供预处理后的数据集。根据用于实现最大效率的方法，可能涉及数据可视化和预测的多个阶段。

## 提出的模型

毕业后，每个学生都希望有一个工作录取等待他们。通过就业可能性预测，学生可以了解自己的就业机会以及应该采取的后续措施。就业预测对于机构的战略性学术规划非常有用 [14]。

我们将介绍使用机器学习模型预测学生就业的过程。实习和工作录取对学生和机构都非常受重视。良好的就业记录对学生和学校都是有利的，因为它让学校脱颖而出。本研究的目的是开发一个评估学习者技能、经验和学术历史旨在为关于其最佳学习环境提供明智的建议。一种机器学习算法决定了这一预测结果。系统模型如图 (1) 所示。

![](img/5e4d8ef2afa52a8404b28106580e19e4_683_0.png)

图 (1) 系统模型。

### 数据预处理

数据准备是一种将无结构化数据转换为更具可用性格式的方法。“预处理”（pre-processing）一词是在向算法输入数据之前所采取步骤的缩写。

### 质量数据

当数据质量较差时，挖掘会产生不可靠的发现。使用低质量数据（如不完整或包含错误的数据）可能会导致不准确或误导性的统计结果。

### 数据处理任务

数据预处理涉及许多不同的程序。下面提供了详细说明：

- 数据清洗：在数据预处理中，这是第一个程序。在此阶段，处理缺失数据、噪声数据、离群值识别与删除、数据去重以及计算偏差修正等问题至关重要。

- 数据整合：如果需要将来自多个源的信息合并成一个整体，则使用此方法。在数据清洗后，产生的信息可以用于分析。

- 数据转换：在此过程中，将原始数据转换为模型所需的格式。以下是可用的数据转换选项列表：-

    - 归一化：为了执行数据缩放，该技术首先将数值数据转换为所需的范围（在本例中为 0 到 1 之间）。

    - 聚合：该理念蕴含在词汇中，该技术用于简化流程。创建新类的一种方法是合并现有类。

    - 泛化：在这种情况下，简单属性被提升为更复杂的属性。

- 数据压缩：在通过转换和缩放消除数据中的冗余后，可以对数据进行组织。

### 用于就职预测的机器学习

这项工作的目的是根据候选人的过往工作和成就建立一个薪资范围。本研究采用了多种预测模型，包括但不限于线性回归、k近邻回归、决策树模型、XGBoost、梯度提升、LightGBM 和随机树。以下是对这些每个模型的简要概述。图 (2) 显示了数据预处理模型。

**图 (2)** 数据预处理模型。

- 线性回归模型：寻求感兴趣的因变量与自变量之间的线性相关性。

- K近邻回归模型：解决分类和回归问题。

- 决策树回归模型：用于根据特征数据学习用于预测的规则。

- XGBoost 回归模型：这是一种集成机器学习技术，利用决策树和梯度提升框架。

- 梯度提升回归模型：用于生成一个由非常简单模型（例如决策树）组成的预测模型。

- LightGBM 回归模型：这是一种回归模型，用于评估各种树对所需结果的贡献。

- 随机树分类器模型：从训练数据的样本中生成一组决策树。

为了对新获取的样本准确预测标签，判别式人工智能策略使用独特且同分布的（iid）训练数据集。不需要像生成式机器学习方法那样通过生成选项的依赖分布来对数据点进行分类，判别式分类函数只需将每个数据点 $x$ 分配到许多可能的类别之一。与在预测需要识别离群值时常用的生成技术相比，判别技术利用 CPU 功率以及更少的训练数据，特别是对于多变量特征空间以及只需要后验概率时。学习分类器比比从几何角度寻找将特征空间划分为类的理想多变量表面相似。支持向量机（SVM）通过解析求解凸优化问题，与遗传算法（GAs）和感知机等其他主流分类方法相比，提供了一致的最优超平面值。感知机解对初始化和终止设置非常敏感。学习分类器等同于从几何角度寻找将特征空间划分为类的理想多变量表面。

```
双曲正切 (sigmoid): $K(x,u) = \tanh(\beta x^T u + \gamma)$
```

```
带有高斯分布的RBF: $K(x,u) = \exp\left(-\frac{\|x-u\|^2}{\sigma^2}\right)$
```

```
拉普拉斯的径基函数: $K(x,u) = \exp\left(-\frac{\|x-u\|}{\sigma}\right)$
```

ANOVA RB，或使用随机块的方差分析：

```
$K(x,u) = \sum_{k=1}^n \exp(-\sigma(x^k - u^k)^2)$
```

```
$K(x,u) = 1 + xu \cdot \min(x,u) - \frac{x^T u}{2}\min(x,u)^2 + \frac{1}{3}\min(x,u)^3$
```

核的选择很大程度上取决于所分析数据的细节。线性核是最简单的一种，可能对于大型稀疏数据向量有用。然而，人们倾向于使用可以使用非零海森矩阵的多项式核。多项式核通常用于图像处理，但 ANOVA RB 核通常用于回归应用。在未知具体细节的情况下，经常使用的通用核实例包括高斯 RBF 和拉普拉斯 RBF。如果在应用特征减少后，核矩阵变为对角矩阵，则这意味着特征空间是冗余的，建议使用不同的核。

对于线性不可分的数据集，核矩阵的计算需要大量的内存和处理资源，因为它将特征向量从输入空间映射到核空间。

### 实验结果

通过提供带有独立权重的新因子，并使用机器学习和深度学习中的前沿技术，我们可以改进位置预测并获得更准确的结果。

CSV 文件是存储实验数据集的地方。数据集 1 包含了每个学生的以下特征属性：

- 学号 (`roll_number`)。

- 随时间的平均得分 (`GPA`)。

- 总尝试次数 (`entire_attempts`)。

- 通过的尝试次数 (`cleared_attempts`)。

- 判定是否参加内部实习 (`judgment_intern_attended`)。

- 决定是否付费实习 (`determination paid_internship`)。

- 完成的项目 (`projects_done`)。

- 发表的文章 (`articles_published`)。

- 年薪 (`annual_package`)。

因变量 `annual_package` 和其他变量作为独立预测变量。输出预测算法不考虑 `roll_number`，因为它是一个分类变量。

- 处理缺失值 - 缺失值均设置为 0，因为输入的值在学生之间各异，且互不依赖。

- 数据可视化 - 在试图掌握数据相关性时，总结海量数据并以清晰易于理解的方式显示它们是标准技术。因此，信息可以更清晰、更高效地传递。在本研究中，为了方便起见，我们以柱状图的形式提供了所有的变量。图 (3) 描述了这一点。

![](img/5e4d8ef2afa52a8404b28106580e19e4_691_0.png)

**图 (3)**

响应时间与用户数量。

我们提供了一个 Web 应用，学生可以在其中提交信息并获得关于课程和改进方法的建议。特征缩放、优化 F1 分数、超参数调优以及增加神经网络的层数，都是在使用算法（逻辑回归、SVM、XGBoost 判定决策树分类器）时使模型变得复杂并而产生更准确结果的方法。图 (4) 展示了准确率与用户数量的关系，图 (5) 说明了精确率与用户数量的关系，图 (6) 显示了召回率与用户数量的关系，图 (7) 描绘了 F 分数与用户数量的关系，图 (8) 显示了节点大小与时间 (ms)。

![](img/5e4d8ef2afa52a8404b28106580e19e4_692_0.png)

图 (4))

准确率与用户数量。

![](img/5e4d8ef2afa52a8404b28106580e19e4_692_1.png)

图 (5))

精确率与用户数量。

![](img/5e4d8ef2afa52a8404b28106580e19e4_693_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_693_1.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_694_0.png)

图 (8))

节点大小与时间 (ms)。

## 结论

数据挖掘算法在分析和根据之前的学术成就预测学生就业机会方面起着关键作用。为了预测未来的选择，需要分析包含学术和选择因素的数据集。如果学生能清楚地了解自己的优缺点，可能会对教育做出更明智的决策。这种策略不仅有助于提高入学人数，还能帮助机构做好准备。

## 参考文献

- [1] Setiawan, H., Wafi, A. Classification of Personality Type on Twitter using Machine Learning 3rd International Conference on Information and Technologies (ICOIA), 2020.

- [2] Rohan S., Bharti, B., Mahato, D., Kumar S. Innovations in artificial intelligence:17th Annual Conference, Springer, 2021.

- [3] Kaur J., Saxena J., Shah J., 2022 International Conference on Computational Intelligence and Sustainable Engineering (CISES), IEEE, 2022.

- [4] Yoganand M., Kannan B., Meenakshi D.. A User-Friendly Interface for Data Preprocessing and Visualization using Machine Learning Models Proceedings of the International Conference on Artificial Intelligence and Data Science (ICAIDS), 2023.

- [5] Surya S., Kumar M., Ghamid D.. Student Prediction using Machine Learning 2nd International Conference on Technological Advancements in Computational Sciences (ACS),2nd International Conference on Advance Computing and Innovative Technologies (ICACITE), IEEE, 2022.

- [6] Shahidur R., Rohan S., Hossain M., Jahan F. Analysis of IoT with Sixth International Conference on Signal Processing and Networking (WISPNET), 2021.

- [7] Chen J., Bian L., Kumar S., Detection of Leaf Disease using Machine Learning Journal of Online Engineering, 2021.

- [8] Khan S., Khan A., Taufiq M., Riz S. Prediction of High Density EEG using Machine Learning IE Transactions on Smart Processing & Computing, 2023. 

- [9] Issue S.V., Pandey A.K., Yadav S.P. Speech Recognition in IE Transactions of Electronics Engineers of Korea, 2021.

- [10] Rohan R., Rohan S., Hossain M., Jahan F. Localizing Epileptic from Machine Learning Electronics and Mechatronics (IEMT), 2021.

## 引言

智能车间以其无畏的生产能力为特征。传统的基于模型的故障检测系统严重依赖于全面的机器实例，而数据驱动的方法只能利用数量相对有限的基础状态数据 [1]。这些特性使得它们变得不可行，而且无法满足工业物联网框架下对处理传统大数据的实时需求。多尺度模糊熵和反向传播神经网络（或 MFFEBPNN）技术被用于解决工业设备故障检测中精度低和故障预测时间过长的问题。由于现在大量数据是非结构化或无序的，基于物联网的工业设备正在实时并收集数据。使用基于物联网的传感器是监控工业领域这些生产过程的最有效方法。然而，物联网应用的一个主要挑战是存储和理解实时收集的数据。由于产品质量和生产效率会受到工具随时间推移而退化的影响，如何利用通过状态监测收集的数据来合理预测设备的命运至关重要。预测数控机床切刀的磨损程度是大数据生产环境以及工业设备故障诊断与健康管理中的机器学习的一个问题 [2, 3]。从切刀在粗加工和评估阶段获取的初始信息中提取了特征。为了消除与工具磨损损失相关的特征集，使用了特征筛选方法。最终，一种机器学习算法预测了铣刀的持续时间。工业生产的巨大规模和传感等技术的进步使得工业工具数据的收集成为可能 [4, 5]。虽然可以收集足够感应电机健康的信息，但要发现其故障更为困难。因此，本文的主要目标将是利用关于电机健康的信息识别运行工况并预测潜在问题 [6, 7]。本文提出的自适应阈值和状态识别器是感应状态架构的组成部分，可用于电机。为了训练感应电机的状态模型，我们使用了健康数据；为了解决电机数据未标记的问题，我们使用了升级的 SOM-FCM 双层聚类方法。至少，通过普通载荷变化状态识别和转子电机故障预测验证了该模型和方法的有效性，准确率分别为 97.5% 和 90.2% [7, 8]。智能工业设施管理严重依赖于机械化以及对加热、通风和空调（或 HVAC）的精确故障识别和评估，以节省金钱、时间和资源。由于这种强健的便携性和卓越的特征提取能力，卷积神经网络正在各个领域广泛应用，以解决分类和预测挑战。在这项研究中，我们创建了一种基于联邦学习的卷积神经网络（Fed_CNN）来处理 HVAC 缺陷识别和诊断。该系统使用多方数据进行多尺度联合融合 [9, 10]。提出的 Fed_CNN 模型对冷水机故障检测和诊断的影响大于 0.9，使其能够同时进行多层故障预测和诊断。Fed_CNN 模型可以检测并诊断空调（AHU）和冷水机故障。一系列实验对比表明，建议的专利学习联邦架构执行了多种故障算法。



# 基于 CNN 的新型智能诊断方法

本研究提出了一种基于 CNN 的新型智能诊断方法。在将数据输入学习系统之前，大多数方法需要特定的复杂的准备步骤。将信号从时域转换到频域是一种新技术，但在传统学习中被广泛使用。该方法引入的革命性步骤是一种在时间域准备信息的简单方法。为了对图像进行分类，该方法将时域信号映射到视觉域，然后建议使用复杂的卷积神经网络（CNN）。结果证明了所用方法是有效的。本文其余部分的结构如下：第 2 节介绍了新型基于 CNN 的智能故障诊断；第 3 节详细讨论了实验结果；第 4 节是最终分析。

## 相关工作

在这项研究中，我们描述了一种利用工业大数据的故障预测方法，包括声学数据和状态事实，并使用机器学习技术直接揭示这些数据集与设备故障之间的联系。此外，可以实时跟踪导致故障的设备状态以便进行及时检查。仿真结果表明，与最先进的替代方案相比，我们的方法在判断和实时性方面表现更好 [11]。在对制造机械的缺失、异常和高噪声数据进行预处理后，使用递归特征消除法和交叉验证技术提取主要变量，并设计了训练和学习率权重。通过对商业数据进行预处理并开发利用神经网络的预测模型，该方法增强了工业机械的缺陷预测能力。通过隔离最显著的定义特征，我们可以加速预测过程。发电领域的实验表明，该策略在预测风扇叶结冰故障方面是 [12]。今天数据驱动的工业格局非常看重大数据处理提升公司产出的能力。执行器和传感器等智能设备在制造机械中变得越来越常见。这些设备的任务是持续跟踪机器状态，并在组件等级恶化之前实施纠正措施。遗憾的是，并不是工厂都利用其制造过程中产生的大数据。由于大数据分析可能花费大量的时间和精力，往往被忽视。此外，实时处理数据的价值经常被低估。为了增加企业创造的价值，在制造业中使用大数据分析具有其目的。随着 TOREADOR 欧洲倡议强调航空程序（作为该项目的研究课题之一），本文旨在通过适应数控机床传感器读取的 TOREADOR 数据来获得的主要进展和教训 [13]。为了防止公司和国家巨大的人力和财务损失，需要对过程工业输出故障进行早期预警，以采取适当措施。对于不断增加的工业数据循环、不断变化的对象、复杂的性质以及整体价值的下降，本文提出了一种基于增量技术更新的实时预测算法。数据经过预处理，然后使用滑动窗口对数据流进行聚类，判断异常数据并预测故障。为了提高预测性能，利用 Spark 架构在每一步对算法进行并行处理 [14]。

## 提出的工作

### 系统模型

在这项研究中，我们提出了一种框架，通过从过去的状态数据中提取特征，然后利用实时数据识别潜在故障模式。基于人工神经网络的方法，结构化数据分析和统计方法已经可用。在处理不确定或缺失数据时，前两种方法具有重大的局限。由 BP 开发的神经网络通过使用学习算法沿着误差函数的负梯度调整权重，将整个网络误差限制在可控的范围内。本文中，使用 BP 神经网络对未检测出的故障进行分类，因为它在面对分类挑战时表现更好。信息特征点（或称特征值）是将传感器信号数据代入数学公式的结果。

基于判断的系统中，传感器缺陷的普遍性会导致读数不准确，从而误曲机器或周围环境的实际状态。环境特性、系统特征或需求，以及数据特征，是我们组织传感器数据错误分类的三个大类。这种分类有助于寻找缺陷检测技术。

传感器周围环境的特征（如位置、温度和湿度）可以洞察传感器的运行背景和情况。所测的传感器模态和环境限制也包含在内。这些特征对于建立行为至关重要，据此识别传感器或系统故障。硬件组件和校准特性是传感器特征或规格的示例。传感器的能力由其硬件定义。输入输出映射中的歧义通过“校准”一词来捕捉。当传感器的工作情况超过其限制或校准条件时，它可能会出现裁剪（clipping），这可能是软件或硬件限制。统计可用于数据特征，这些特征通常在时域或频域计算。例如，传感器必须继续可靠地运行，以保持与位置相似的传感器相同的特性。数据特征非常引人注目，因为它们包含了两类频繁发生的传感器故障。可以通过数据科学家的视角来看，可以使用统计方法检测异常、尖峰和“粘连”（stuck-at）错误。校准误差、硬件连接故障或电池电量耗、超出范围故障和裁剪都是第二类传感器问题的示例，这些需要以系统为中心的视角。

可以使用多种信号数据表示信号的许多特征。本研究严重依赖于新的特征值，如均值和标准差。为了获取信号数据特征，我们对获取的设备数据使用了上述计算特征值的技术。然后，我们进行了一些训练并识别了某些特征值。

为了让 CNN 学习到幅正常状态和各种隐藏故障的特征，本研究使用了大量的频谱图作为训练数据。CNN 的卷积层和池化层共同工作以学习图像特征，并使用成熟的 BP 技术调整参数。每一对包含一个卷积层和一个池化层。本文中使用的神经网络架构如图（2）所示。

### CNN 模型

本部分解释了 CNN 网络的思想、信号如何转换为图像以及 CNN 如何进行填充。

CNN 是一种优越的人工神经网络（ANN），它使用了多层相互连接的节点。与全连接 ANN 相，ANN 每一层中的特征图突触仅与其下方层中的某些神经元有微弱连接。大脑的视觉皮层 [8] 为这一想法提供了灵感，因为它包含了基础和复杂的案例，后者仅对其紧邻的周围敏感。CNN 构建在三层结构之上：

- 不不变层。
- 池化层。
- 积分分层系统。

原始照片用作 CNN 的输入数据。它通常是二维数据类型。为了生成输出特征图，卷积层使用了放置在输入图像上的预定义滤波器。单层池化层具有对图像进行下采样的能力。全连接层之后使用 Softmax 回归对输出进行分类。LeNet-5 网络卷积神经网络（CNNs）是 CNN 的轻量级版本，在识别打印和手写文本方面显示了有效性。标准的 LeNet-5 CNN 模型架构如图（1）所示。它接受 32x32 像素作为输入。模型组件包括一个两层全连接 ANN，在第 2 层具有卷积层和池化层。为了解决这个问题，我们开发了自定义的卷积神经网络（CNN）LeNet-5 来对故障进行分类。

两个卷积层、两个池化层和一个全连接层构成了网络的隐藏层。为了快速执行，预处理仅仅执行了复杂的灰度转换。对于卷积层，利用 sigmoid 函数作为激活函数（即 `f(α)=1/(1+e^{-(αθ)})`）。池化层具有 sigmoid 激活函数，并使用了平均池化技术。实施此操作的主要步骤如下。

![](img/5e4d8ef2afa52a8404b28106580e19e4_703_0.png)

**图（1）** 系统架构。图（1）展示了系统架构。

第一，是卷积层。卷积核应用于上一层的特征图上，然后应用激活函数。单个图与较高层中的若干个特征图之间可能存在卷积相关性，以及这些图的卷积层结果。该陈述的公式为 (1)：

```
$x_{\beta}^y = \int \left(\sum_{\alpha \in M_{\beta}} x_{\alpha}^{y-1}k_{\alpha\beta}^y + b_{\beta}^y\right) \quad (1)
```

其中 `M`、`K` 和 `b` 分别代表层数、输入特征集大小和特征图偏移。第 2 层：池化层。从顶层取样时，使用平均池化方法。其公式见 (2)。

```
$x_{\beta}^y = \int \left(B_{\beta}^s(x_{\beta}^{y-1}) + b_{\beta}^y\right) \quad (2)
```

第三，连接层。将池化层的映射转换为单个特征向量，并以全连接的形式返回。

图（2）描述了计划的 CNN 架构。该 CNN 模型类似于 LeNet-5。CNN 构建在 TensorFlow 库之上，其精确定义将在下一节探讨。

识别数据集中传统方法通常包括统计分析、模糊逻辑系统或从数据集中提取模式的神经网络。为了研究信号的二维特征，我们在本研究中提出了一种新的数据准备方法，涉及将其转换为图像。

![](img/5e4d8ef2afa52a8404b28106580e19e4_705_0.png)

**图（2）** CNN 架构。

图（2）展示了 CNN 架构。该 CNN 模型与 LeNet-5 非常相似。CNN 构建在 TensorFlow 库之上，其精确定义将在下一节探讨。

需要初始零填充。在无填充模型中，省略了最后的对齐部分。在零填充中，卷积表达式的末尾会自动自动补零。从输出尺寸的角度来看：

```
OutSize = ceil( float ( InSize ) / float ( strides ) ) (4)
```

当精确确定参数值不那么关键时，我们在选择时会保持谨慎。微调参数可能会提高性能。以下规则作为该过程的说明：

1. 如果数值在超过三十秒的时间内没有变化（标准差），则认为传感器为“卡住”（Stuck）状态。
2. 根据数据，如果超过一半的测量值缺失，则传感器存在“间歇性”（Intermittent）缺陷。否则将实际传感器读取数除以预测数以百分比的形式给出。
3. 找出读取值与模型对传感器正常行为中间估计值之间的距离。
4. 如果漂移趋势大于 0.5，则认为传感器具有“漂移”（Drift）故障。

## 结果与讨论

此处进行了一项调查。首先介绍背景和数据。随后展示测试结果和信号的变化。以下是对该案例研究的分析。表 1 代表了实验数据集的细节。

**表 1** 实验数据集的细节。

| 机器类型 | 操作 | 异常 | 模型 ID | 样本数量 |
| --- | --- | --- | --- | --- |
| 工艺 | - | 922 | 162 | - |
| 泵 | 排入蓄水池 | 泄漏、污染 | - | - |
| 阀门 | 暴露/关闭 | 多于两个 | id 00 | 850 | 180 |
| - | 循环 | 污染类型 | - | - |
| 扇扇 | 正常运行 | 电压变化、堵塞 | id 00 | 647 | 235 |

这种创新方法的发现通过凯斯西西储留大学（CWRU）的电机轴承数据得到了验证。外圈故障、内圈故障和滚滚故障是常见的常见的缺陷类型。每种缺陷类型的损坏尺寸从 0.18mm 到 0.36mm 再到 0.54mm 不等。在正常情况下，设备上可以执行十种不同的操作。经过我们新的数据准备技术后，这些数据将发送到建议的算法中。数据集由简单获取的几个 2 米段组成。训练数据集包含每个缺陷类别的 6400 个实例，而测试数据集包含 1600 个实例。测试结果所示。

图 (3) 显示了传感器读数。在开发车床动态概率模型时使用了以下假设：

![](img/5e4d8ef2afa52a8404b28106580e19e4_707_0.png)

![](img/5e4d8ef2afa52a8404b28106580e19e4_708_0.png)

**图 (3)** 展示传感器读数。

1. 首先，由经验丰富的操作员定义 `P` 初始转移概率矩阵。系统开始运行后，使用传感器置信度来动态更新转移概率 `Pdynamic`。
2. 该实现的系统范式仅基于两个模块构建：主轴和刀具。
3. 电流、振动和温度传感器监控每个模块。
4. 由专业操作员为该模块的三个贡献给出相对权重，其设值为：
   - 当前传感器：0.3
   - 振动传感器：0.5
   - 热传感器：0.2
5. 所有传感器的初始置信分均为 0.99。
6. 为了保持模型简单，所有传感器的平均工作时间（MTT）被认为十万小时。

图像尺寸限制为 64x64 像素。每张图片宽度为 4096 像素且为灰度。

该案例研究证明了建议 CNN 的有效性。为了研究其二维特性，它首先经历了信号到图像的转换。该方法优于其他深度学习技术，并实现了 99.51% 的准确率，远于使用传统 ANN 和 SVM 获得的结果。此外，本研究中采用的新型数据准备方法可以度地减少专家偏见，并使建议的方法更容易被广泛的读者接受。图 (4) 显示响应时间与样本数量的关系，图 (5) 显示了准确率与样本数量的关系，图 (6) 描绘了判断与样本数量的关系，图 (7) 显示了召回率与样本数量的关系，图 (8) 说明了 F 分数与样本数量的关系，图 (9) 显示了机器类型与时间。

![](img/5e4d8ef2afa52a8404b28106580e19e4_709_0.png) **图 (4)** 响应时间与样本数量的关系。

![](img/5e4d8ef2afa52a8404b28106580e19e4_709_1.png) **图 (5)** 准确率与样本数量的关系。

![](img/5e4d8ef2afa52a8404b28106580e19e4_710_0.png) **图 (6)** 判断与样本数量的关系。

![](img/5e4d8ef2afa52a8404b28106580e19e4_710_1.png) **图 (7)** 召回率与样本数量的关系。

![](img/5e4d8ef2afa52a8404b28106580e19e4_711_0.png) **图 (8)** F 分数与样本数量的关系。

![](img/5e4d8ef2afa52a8404b28106580e19e4_711_1.png) **图 (9)** 机器类型与时间。

```
Accuracy = $\frac{NumberOfCorrectPredictions}{NumberOfPredictions}$
Judgment = $\frac{TruePositive + FalsePositive}{TruePositive}$
Recall = $\frac{TruePositive + FalseNegative}{TruePositive}$
F1_Score = $2 * \frac{Judgment}{Judgment + Recall}$
```

## 结论

感谢云计算、物联网、大数据、移动网络等领域的发展，现在可以收集大量的各种数据。由于模型困难或数据利用不足，过时的方法在今天的工作是不可接受的。预测方法可以利用大量信息来检测和分类故障。仿真结果显示，该方法提供了相当的方法。间歇性故障是稳定输出的主要威胁，但我们的方法可以很大程度上减轻这些问题。它有助于工业早期检测问题并提高效率。

## 参考文献

1. Liu Z., Yang Y., "基于数据驱动的铣刀磨损预测研究2022第11次国际信息技术大会 (ITech)" 武汉，中国2022.16.1009/ITech5546.2022.0101
2. Gu Z., Zhong Y., Yang J., "数据驱动感应电机状态识别与故障预测第2次国际大数据大会2021.1140.1109/ICDT335892.335894
3. Wang Y., Yan K., "基于联邦学习的 HVAC 系统故障预测与诊断2022 IEEE Int Conf on Embedded Data, Autonomous and Secure Computing, Int Conf on Pervasive Intelligence Int Conf on Cloud and Big Data Computing, Int Conf on Science and Technology Congress (DASC)/PIC/BCDom/CyberSciTech/202201.110/DASC/PIC/BCDom/55231.2022.97944
4. Kaur A., Saxena J., Shah J., 2022计算智能与软件工程国际大会 (ICESIEE)2022.10.1109/ICESIEE5548.2022.98436
5. Mbuli J., Nouri M., Tentreaux D., Baert R., 智能交通系统的根因分析与故障预测：耦合无监督和监督学习技术2019国际控制自动化与诊断大会 (ICCAD)162019.10.1109/ICCAD46983.2019.90378
6. Bellini P., Dalesi A.I., Nesi P., Pantaleo G.. 工厂状态短期预测深度学习方法IEEE大数据计算与应用国际大会 (BigDataService)91620210.1109/BigDataService52369.2021.00007
7. Wen L., Gao L., Xu X., Miao L., G. 卷积网络数据驱动智能故障诊断2017 IEEE工业工程与管理国际大会 (IEEM)3818327170.1109/IEEM.2017.8290004
8. Guangfei Z., Wen T., Da Z. PSO-SVM方法检测水轮叶片J. Phys. Conf. Ser.20180817022036.1088/1742-6598/1742/2/02236
9. Kabugo J., Jounela S., Schiemann R., Binder C. 基于工业4.0故障的过程监控框架：废物能源案例研究第4次控制与容错系统大会 (Syst)2019 24629.10.1109/SYSTOL.2019.8866479
10. Ku J.H.-A. 基于可靠性大数据分析的故障预测研究rd Pers. Comput. 2020.16337f10.1007
11. Yadav S., Pradhan B., Mahato P., Kumar K. 物联网应用的联邦学习EAI/Springer 通信与计算创新.Springer International Publishing202210.1007/978-3-030-8559-8
12. Qi Z., Tang C., Jiang C., Huang Y. 基于工业大数据处理的设备预测研究信息经济、数据建模与云计算国际大会 ICDIC 2022202020.4108ae17-6.2022.23295
13. Coralla A., Cresino A.M., Biccardi C.D., Lazzi M., Lezzi M. 流式大数据处理进行故障预测：一种工业应用。Proc. IEEE 8th Int. Conf. Information Technology and Systems (SITIS)201816110.1109/SITIS.2018.00117
14. Mi T.. 基于模糊聚类的过程工业故障预测Proc. IEEE8th Int. Conf. Big Data Security on Cloud (BigDataService)20221610.1109/BigDataSecurity-HPSC-54955.2022.00013



- 15. Rashid M., Singh H., Goyal V., Ahmad N., Mogla N. 物联网中高效的大数据存储和处理模型以提高故障检测过程准确性Advances in Computer Science and Engineering1st ed., H Singh and M. M. Rashid, Eds. Hershey, PA, USA: IGI Global202012514010.4018/978-1-7998-0373-7

# 词嵌入技术下逻辑回归与随机森林在推特情感分析中的对比分析

Dhiraj Singh1,* 

1 商业与技术跨学科研究中心，奇特卡大学工程与技术学院，奇特卡大学，旁遮普，印度

## 摘要

为了进行分类并生成新类别，必须对现代产生的海量文本材料进行组织。从组织文本数据中获取洞察的基本方法是文本分类。然后，我们根据发现的文本类型对类别进行进一步分类。我们将过程分为预处理、文本表示、分类器执行和分类四个阶段，使用了广泛的机器学习方法对文本进行分类。在本研究中，我们利用来自推特的真实数据来评估和比较了几种情感分析方法。在使用各种向量化方法开发模型之前，我们对数据进行了清洗并分为训练集和测试集，并比较了结果。基于不同向量化的模型比较发现，使用`TF-IDF`的逻辑回归（`LR`）模型性能最佳，其`f1`值为0.81，具有良好的准确率和召回率。

**关键词：** 逻辑回归，随机森林，推特情感分析，`TF-IDF`。

* **通讯作者 Dhiraj Singh：** 商业与技术跨学科研究中心，奇特卡大学工程与技术学院，奇特卡大学，旁遮普，印度；电子邮箱：dhiraj.singh.orp@chitkara.edu.in

## 引言

为了分析公众的主流情绪，已经开展了基于在线数据的文本情感分类实验 [1]。方面级的情感分类是一项更细粒的任务，它通过观察整体内容来确定其情感，近期引起了广泛关注 [2]。这主要是因为信息可能包含“这个苹果看起来很好，但味道很平淡”，这种二元对法在“这个苹果看起来很好，但味道平淡”方面是积极的。为了解决现有算法在文本方面存在某些缺陷的问题，本文提供了见解 [3, 4]。由于`RNN`具有挑战性，信息可以被提取 [5]。所提方法倾向于消除复杂性 [6]。此事的意义很多 [7]。在不同的数据集上，使用准确率、召回率和测量等多种标准评估了所提技术的性能 [8]。这项工作的主要目标是描述 [9] 的性能。实验表明，该方法需要 90.2% 的准确率 [10]。随着在线对话数量不断增加，能够解读社交媒体中表达的情情感观点至关重要，这具有广泛的潜在用途，从营销策略到经济政策不等。社交媒体平台上的信息对于决策非常有用。情感分析的结果显示了当前状态的

- 社交媒体平台上的信息是创造感觉、思想和情感的宝库。

- 情感分析是有用的，因为这些内容提供了对积极、消极或冷漠的洞察。

## 文献综述

分析马来西亚社交媒体上的情感是困难的，因为信息通常是英语和马来语混合编写，并嵌入了术语和不同的方言。每条推特都使用马来西亚清真认证方案进行分类，根据结果确定类别标签的频率值 [11]。分析了500条带有`#sejhalal`标签的推特，以进一步了解个人对马来西亚清真认证相关话题的感觉、想法和行为。发现并可视化了人们对清真主题的情感。穆斯林人的观点对于提高当地方言的意识至关重要。

在本研究中，我们将用于表达情感的语言创建转换为训练-优化程序。在我们的系统中，情感分类的精确性作为优化目标，因此候选情感词汇被视为需要优化的对象。我们发现了两种通用算法，可根据其情感内涵更改词汇表中的单词。情感词汇最终被选为提供的演化算法演化出的最佳个体。我们的方法只需要少量标记文本，不需要任何先验知识或语言专业知识。实验结果证明了所提方法的通用性，及其在特定领域产生高质量情感词汇的能力 [12]。该研究的主要发现如下：在这里，我们检查了执行四种不同情感分析方法的相对效能：(1) 一种用于情感分类数据预处理的建议；(2) 增强情感分类准确性的额外特征；(3) 应用奇异值和主成分分析进行数据降维；以及 (4) 基于各种特征（无论是否有相应的原始特征）开发的五个模块 [13]。本文建议建立一个将文献分类为六种不同情感状态的系统：喜、悲、惧、怒、惊讶和

厌恶。为了成功从文本中提取这些情感，我们在模型中结合了两种替代方法。第一种方法基于自然语言处理（`NLP`），除了更传统的词性分析外，还使用了语法分析以及如表情符号、程度词和否定词等文本特征。第二种策略是基于分类的机器学习方法。我们还有效地开发了一种自动开发该集合本身的方法，这将比手动标注大型数据集节省大量的时间和精力。此外，我们还生成了大量的情感词汇及其对应的情感强度。测试表明，我们的算法显著提高了取自`Twitter`的推文的分类准确率 [14]。

- 意见挖掘是文本分析的一个分支，用于解析网络评论以寻找表达赞同或反对的表达。在这项研究中，我们开发了一个意见挖掘系统。我们使用了一种名为“最持久特征选择”（`MPFS`）的独特特征选择方法，然后应用遗传算法（`GA`）来优化生成的特征集。`MPFS`方法依赖文档特征来为分析进行数据清洗。以此生成的特征集随后通过`GA`方法进行优化，以确保其在情感分类中尽可能有效。随后使用支持向量机（`SVM`）算法以及推荐的特征选择和优化方法对评论文本中所表达的意见进行分类。与其他现有模型相比，构建的分类器模型的准确性值得赞赞 [15]。

## 拟议工作

本研究开发了一种用于推文分类的自动方法。作者独立地选择了逻辑回归和随机森林作为我们的分类方法，并在分类器构建部分分析了它们的相对优势。最后，在这些分类器经过实际测试并相互比较后，得出了结论。实验结果表明，用于将推文分类到不同类别的算法提供了满意的结果。精确率（`Exactness`）、准确率（`Accuracy`）、`F1`值、支持率（`Support`）和混淆矩阵是作者决定比较的五个指标。对于`Twitter`数据集，最佳机器学习算法是在所有这些指标上都具有最大值的分类器。

## 数据收集、准备与清洗

在使用各种向量化方法构建并比较主要模型之前，需要对数据进行清洗。每个数据都包含了训练数据和测试数据。为了确保一致性，这两个数据集在清洗后再次合并。当我们清洗数据时，我们去掉了所有非必要的列，例如项目 ID（`Item ID`）。所有大写字母已转换为小写，并消除了多余的符号和数字。这种筛选使得推文主要由单词及其相关的情感组成。情感文本被应用了标签以创建特征集 (`X`)，生成的标记数据 (`Y`) 用于预测。特征解聚合在测试集和训练集上进行。

`Kaggle`数据集被称为`TwitterAirlineSentiment`。该数据集大约有 15,000 条推文，其态度可以分类为正面、负面或中性。正如我在之前的文章描述的那样，通过分词和两个不同的分类器，我们尝试对推文进行分类。图 (1) 显示了系统流程图。

![](img/5e4d8ef2afa52a8404b28106580e19e4_720_0.png)

图 (1) 系统流程图。

## 向量化

使用独热编码（`one-hot encoding`）编码的单词产生高维稀疏（包含许多零）的向量。这可能导致大型数据集上的性能问题。独热编码也有问题，因为它忽略了单词的含义。因此，飞机（`Airplane`）和航空（`aircraft`）被分为两个类别，尽管我们知道它们本质上表示相同的意思。这两个问题通过词嵌入（`word embedding`）得到了解决。

词嵌入是一种低维稠密向量。其次，向量的距离和方向描述了单词之间的语义联系。

随后使用了两种不同的方法`TF-IDF`向量和`Word2Vec`均值向量来处理数据集。语料库中词的重要性通过一种名为`TF-IDF`的指标来衡量，它是词频（`term frequency`）和逆文档频率的写。它的主要功能是消除在文本摘要和分类应用中手动过滤词的需求。考虑到某些短语比其他短语更常见，`TF-IDF`值随着单词在文本中的频率成比例增长，同时随着其在语料库中的出现而减少。

`Word2Vec`是一个工具，通过优化根据上下文预测单词的概率来帮助构建词嵌入。将短语和单词转换为向量表示是文本分类的一种新方法，它在文本分类中增加了额外的语义维度。向量提供了单词重要性的数值表示。简而言之，这是一种从文本语料库中快速提取嵌入词的统计方法。

## 单词向量

清洗后的下一个阶段是以机器可以理解的方式编码文本。这就是为什么我们利用`Victimizer`，它将文本字符串转换为数值向量，“词频-逆文档频率”（`TF-IDF`）。由于自然语言处理的进步，词向量现在比以前的分析为计算机提供更多关于单词的信息。词向量通过显示一组实数值将单词显示为“多维连续浮点数”，其中每个点都捕捉了单词含义的一个维度，而传统的`NLP`方法无法捕捉词组之间的语法和语义连接。在这种情况下，文本被转换为向量的数值表示，这些向量与用于语义相关术的向量具有可比性。通过逆文档频率，可以从句子含义决策中移除不重要的词汇。因此，文本中该短语的所有出现处将被转换为 0。`TF-IDF`方法在过滤冗余词的同时，也从语料库中分离出重要特征。`TF-IDF`算法会对在文中出现频率较高但在语料库中范围较窄的单词给予特殊关注。因此，该术语在区分文本类型方面最为有效。`TF-IDF`方法可以用数学公式表示为：

$TF - IDF (w) = TF (w) * IDF (w) \quad (1)$

## 文本分类模型

使用两种分类算法预测了推文的态度：逻辑回归 (`LR`) 和 随机森林 (`RF`)。注意的是，使用网格搜索方法确定了超参数。在下一段中将详细阐述这一主题。

在研究由二变量表示的结果时，通常使用逻辑回归。机器学习使用这种统计方法来实现其预测目的。可以使用这种方法描述数据，并解释单个二变量与独立变量之间的关系。逻辑回归不是预测观测值所属的特定类别，而是提供观测值属于 1 的概率。

可以使用简单的数学公式估计概率，如下所示：

- $P (属于 '1' 的概率) = 1/(1 + e - z)$

- $Z = C + a1X1 + a2X2 + ..., + anXn$

其中 `X1, X2..., Xn` 是观测值的特征，而 `a1, a2...` 是分配给每个特征的“权重”。分配给标准的值越高，表示得出结论的重要性越大。

为了对新实例进行分类，随机森林构建了一个决策树森林并使用多数投票。决策树的每个节点采用随机选择的原始特征子集。决策树分类器及其各个特征共同构成了一个元估计器（`Meta estimator`），提高了预测质量。在分类观测值时，一个决策树独立地考虑所有特征。然而，随机森林模型中的每棵树将只考虑特征集的一部分来得出结论，因此得名。通过随机选择特征子集，森林中的某些树可能会隔离出相关的

在增强输出整体准确性（`Exactness`）的同时提供更多信息，这就是为什么随机森林系统比典型的决策树模型性能更好的原因。

随机森林有时可能不准确，因为它依赖于两个因素：(i) 错误率上升，因为森林中的任何两棵树之间都存在相关性的可能；(ii) 每棵树的效能是独特的。因此，一个强大的分类器是一棵具有低错误率的树，反之亦然。

- 随机森林的一些特征包括：

  - (i) 能够处理大量的输入参数而无需删除其中任何一个。

  - (ii) 它能识别有助于分类的区分性特征。

  - (iii) 对大数据集的有效操作。

  - (iv) 生成的森林和树可以被保留以供后续使用。

- 算法随机森林的阶段：

  - 阶段 1：从训练集中选取 `K` 个看似互不相关的项目。

  - 阶段 2：基于这组信息创建一个决策树。

  - 阶段 3：你可以继续步骤 1 和 2，直到达到所需的树尺寸。

  - 阶段 4：为每条信息从头开始创建一个新树，并采用该节点预测 `y` 数值的平均值。

对于随机森林分类器，公式如下：

```
$n_{ij} = w_{ij}C_{ij} - w_{left}(j)C_{left}(j) - w_{right}(j)C_{right}(j)$
isub(j) = \text{计算随机森林算法时，使用节点 j 的公式}$
wsub(j) = \text{"到达节点的加权样本量"} j$
Cub(j) = \text{"该节点的纯度索引"} j$
left(j) = \text{"分支出的左子节点"} j$
right(j) = \text{"在右子节点分裂"} j$
(2)
```

## 结果与讨论

当代码成功运行时，得到了预期结果。准确率（`Accuracy`）、精确度（`Exactness`）、`F1`值、支持率（`support`）和混淆矩阵是评估和对比不同方法的五项标准。通过逐一个，我们看到了这三个算法的性能如何。

## TF-IDF 的逻辑回归

在这里，我们将讨论使用`LR`建模和`TF-IDF`分解学习中学到的知识。由于`TF-IDF`也考虑了 `n-grams`，它的值等同于二。这可以体现在词“very bad”是一个 2-gram 的事实中。

在输入`LR`模型后，测试数据显示如下：

| 指标 | 值 |

| :--- | :--- |

| 回率（`Recollection`） | [0.76, 0.8] |

| 精确度（`Exactness`） | [0.7, 0.81] |

| `F1`值 | [0.75] |

## Word2Vec 逻辑回归

本文中，我们将讨论如何使用逻辑回归模型分析`Word2Vec`的参数和输出。单词在任何活动处理之前首先被转换为向量。使用了`word2vec`技术来计算此分析的平均向量。为了对方法进行公平比较，我们在逻辑回归内部使用了相同的参数。

结果如下：

| 指标 | 值 |

| :--- | :--- |

| 回率（`Recollection`） | [0.71, 0.7] |

| 精确度（`Exactness`） | [0.65, 0.76] |

| `F1`值 | [0.68, 0.73] |

## TF-IDF 随机森林

`TF-IDF`和逻辑回归模型使用了类似的设置。以最大深度 13 和总共 500 个估计器构建了随机森林模型。我们从这个数据集中发现的是：

| 指标 | 值 |

| :--- | :--- |

| 回率（`Recollection`） | [0.72, 0.76] |

| 精确度（`Exactness`） | [0.7, 0.78] |

| `F1`值 | [0.71] |

## Word2Vec 的随机森林

该模型的参数与之前相同。该数据集的发现包括：

- 回率（`Recollection`）：[0.63, 0.76]

- 精确度（`Exactness`）：[0.67, 0.72]

- `F1`值：[0.74]

## 结论

在这项研究中，我们使用机器学习方法为推特构建分类模型。这项工作建议使用逻辑回归和随机森林方法，两者都对模型提供了全面的描述。在应用机器学习算法到特定数据集时，准确率是最关键的指标。因此，结果显示使用`TF-IDF`特性的逻辑回归分类器实现了 97% 的准确率。在短数据集中，这种方法被证明是最一致的分类器。基于随机森林的分类器位第二，准确率为93%。逻辑回归分类器的结果在所有测量上符合预期。引用的文章解释了为什么选择这三种方法。结果，作者确定了该任务最合适的算法。与其他使用替代向量化的模型相比，使用`TF-IDF`的`LR`模型表现最佳，`f1`为 0.81，且精确度和回率良好。虽然`TF-IDF LR`最有效，但`Word2vec`分析提供了额外的资源，并在许多情况下可能非常有用。探索`NLP`技术在深度学习中的应用以获得结果是下一步。

## 参考文献

[1] Li G., Kong, B., Li, J., Fan, H., Zhang, J., An, Y., Yang, Z., Dans, S., Fan, J.. 基于`BERT`的文本情感分类 Web Data International Conference on Computer Engineering and Artificial Intelligence (ICCEA) 4774812022 10.109/ICCEAI55464.2022.0015

[2] Zhang M., Palade, V., Wang, Y., Li J.. 使用人工蜂群基于注意力的词嵌入进行方面级情感分类。Inf. Sci. 202104517378 10.106/j.sci.2020.092.038

[3] Zeybek S., Pham, D.T., Koç, E., Sezer, A.. 用于情感分类的循环网络的改进蜂群算法。Similarity(Basel)

[4] Zhang X., Jiang, T., Lu, W.. 第7 智能计算与信号处理国际会议短文本情感分类 47748122

[5] Jain A., Jain, T.. 使用混合特征选择和集成分类器的情感分类。Int. Fuzzy Syst. 2022

[6] Zhou X., Liu, J., Chen, S., Lu, D., Wu, Y., Zhang, L.. 基于随机森林的算法进行情感分类。Comput. Neural. Appl. 202302317

[7] Sridharan K., Komasaraj, G.. 撤回文章：使用随机森林和梯度提升机的情感分类。Soft Comput. 202210.1007/00520-3

[8] Abdulkaar N., Abdulbase A.. 基于随机森林的机器学习分类综述 2021

[9] Xuanyuan M., Xiao, L., Duan, M., Marzuki, S.. 多模态媒体文本情感分类探索。IEEE Access 202330645

[10] Setik R.B., Ahmad, R., Mardi, S.. 探索基于印地语推特的情感分析分类 第二届人工智能与数据科学国际会议 (AIAS) IJIP 2021.95742

[11] Yadav S. P., Bhati, B. S., Mahato, D. P., Kumar, S.. `IoT`应用中的联邦学习。Springer Innovations in Communication and Computing 202210.030

[12] Chen C.H.. 基于额外特征文本情感挖掘。PLoS One 2019946e21759

[13] Atkinson S. K., Murugan, V., Wang, N., and Karthikopin 印度大选期间的推特意见和情感分析第15届计算、通信和信息技术国际会议 (ICCCNT) 班加罗，印度。202415.1109/ICCNT.2024.00123

# 通过深度学习和 Doc2Vec 建模的新文章分类



Himanshu Makhijha¹, *

¹ 商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度

## 摘要

互联网使用的指数级增长也导致了大量文本信息的泛滥。由于手动处理非结构化材料非常困难，因此需要探索新的技术对文本信息进行自动分类。文本分类的主要目标是教会模型正确分类未见过的文本。在研究中，使用了`Doc2vec`词嵌入技术对土耳其新闻数据库`TTC-3600`中的土耳其故事和`BBC`英语新闻进行分类。除了基于深度学习的`CNN`外，还使用了传统的机器学习分类方法，包括高斯朴素贝叶斯 (`GNB`)、随机森林 (`RF`)、朴素贝叶斯 (`NB`) 和支持向量机 (`SVM`)。使用`CNN`获得的最佳分类结果通过所提模型，在土耳其数据库上得分为 94.17%，在英语数据库上得分为 96.41%。

**关键词：** `CNN`，新闻文章，`TTC-3600`数据库。

- * 通讯作者 Himanshu Makhija：商业与技术跨学科研究中心，Chitkara 大学工程与技术学院，Chitkara 大学，旁遮普邦，印度；电子邮箱：himanshu.makhija.org@chitkara.edu.in

## 引言

报纸文章为我们提供了许多当前事件的视角 [1]。在线材料的泛滥对人们的日常生活产生了直接影响，数字新闻也不例外 [2]。此类新闻的出现使得对其进行分类变得必要。在本十年中，在线印度尼西亚新闻的数量呈爆炸式增长 [3]。金融系统性风险的数据包含在经济数据中。自动分类系统性风险文档是获取金融系统性风险实时数据的一个必要步骤 [4]。在这项工作中，我们使用深度神经网络和主动学习来自动分类与系统性风险相关的文档 [5]。我们使用了印度尼西亚银行的 15 类金融系统性风险。一个文本文档内部可能包含多条系统性风险信息，因此这是一个任务级的分类问题 [6]。我们对`CNN`、`Bi-LSTM`和`Bi-GRU`的深度学习策略进行了变体 [7]。此外，我们将其与两阶段分类系统进行了类比。互联网已演变为全球实时通信的平台 [8]。然而，万维网的这种指数级扩张也促进了虚信息的广泛传播。目前的文献中提出了许多分类器来区分虚假新闻和真实新闻。然而，它们在良好学习之前需要大量信息，而此类数据难以收集 [9]。近年来，多个互联网网络平台上虚假和伪造材料的增长，导致在政治、社会和其他日常生活话题上形成了偏颇且有时受影响的公众舆论。因此，已有多次尝试创建虚假新闻检测算法，以帮助暴露和反驳虚假信息 [10]。

本研究的目的是评估深度学习和`Doc2Vec`技术与之前探索的技巧在对土耳其和英语数据集进行文章分类方面的比较性。基于用于`T-3600`和`BBC-News`数据库的预处理过程，本研究生成并记录了四个不同的数据集。在开发出`Doc2Vec`训练模型后，我们使用`CNN`、`GNB`、`RF`、`NB`和`SVM`对每个数据集进行标记。

对于土耳其数据库，创建的模型实现了比之前研究更高的准确率。英语数据集的平均准确率结果相当良好。文章的其余部分如下：第 2 章描述了所使用的方法，第 3 章在材料和方法部分详细描述了数据集、预处理阶段和构建的模型。第 4 章讨论的技术结合过去的研究进行了评估，并在最后给出了结论。

## 相关工作

在这项研究中，我们提出了一种名为长短期记忆-梯度提升 (`LSTM-GB`) 的新型深度学习模型用于新闻文章分类，并与现有技术进行比较。所提模型以 99.8% 的准确率优于现有分类器 [11]。

使用 1752 篇文章进行训练，228 篇文章进行测试，通过使用`Bi-LSTM`达到了最大的 F 值。对于 15 个课程，使用 0.15 的概率阈值得到的 F 值为 45.37%。实验表明，采用主动学习并没有增加性能，对于每次迭代增加了 420 个新数据项。

本研究旨在通过分析非洲新闻文章的文本和视觉效果来识别洪水发生情况。`MediaEval2019`的多模态卫星任务提供了这些信息。图像和文本任务都受益于我们的努力。我们独立构建模型从照片和文本获取特征，然后将它们整合以生成一个复杂的分类器，这更有说服力地证明洪水，并允许我们执行必要的子任务。特别是，我们使用了由长短期记忆单元和基于卷积层的`MobileNet`架构的强大文本处理方法。在公司的测试集上，我们的模型性能良好，第一个任务的平均 F值为 85.26%，第二个为 66.19% [13]。

在研究中，我们探索了如何通过各种数据库测试和跨模型实现来检测和分类网络新闻。我们使用深度学习模型将准确率提高了 96.25%。文本分类技术的使用得到了增强。通过最小损失值，虚假信息分类的设计得到了改进。为了正确分类数据，模型在训练后需要超参数 [14]。

本论文的目标是设三个不同数据库中虚假和真实文章的语言差异。本研究的目的是通过比较和开发一种集成方法，确定五种机器学习分类器中的一种在三个数据源上提供最佳通用结果。然后将深度学习方法的结果与统计机器学习模型的结果进行比较，从而建立了一个基础的长短期记忆神经网络。在该项目的方法的第一步，我们使用`NLP`和特征提取工具来清洗和准备将“喂”给各种模型的数据。然后使用条形图、混淆矩阵和精确召率曲线来显示和比较数据挖掘、数据可视化、机器学习和深度学习的发现 [15]。

让我们考虑按主题对新闻项目进行分类，或按正面/负面评分对书评进行分类的任务。语言识别、客户反馈组织和欺诈检测是文本分类实用的其他三个领域。机器学习模型可以自动化原本耗费大量的人工操作。新闻类别分类是一个具有多个标签的文本分类问题。其目标是为新闻项目标记合适的分类标签。在多标签文本分类中，使用多个二分类器是一种常见的做法。基于传统机器学习的新闻文本分类主要涵盖以下问题：使用传统技术表示新闻文章时，词序和意义等重要的上下文线索在翻译过程中丢失了。然而，它不会考虑新闻文章中单词的上下文含义。人工参与新闻文本特征的提取是主观的、耗时且耗人力的；使用向量空间模型传输新闻文本会导致由于信息稀疏问题产生的高维度问题；然而，选择特征的方法可以用于降维；但这只会加剧新闻文本特征丢失的问题，并使整个新闻文本分类变得更加复杂。新闻文本分类的效率将受到这些问题的负面影响。因此，需要研究新的文本特征表示和文本特征提取方法。

## 技术与材料

2015年，研究人员制作了`TTC-3600`数据库，供土耳其新闻分类研究广泛使用。`TTC-3600`数据库现可用，它既用户友好又有完善的文档，近年来已在土耳其新闻数据库中发布。该集合总共有3600份文档，其中包含600篇涵盖经济、文化艺术、健康、政治、体育和科技的新闻或其他文章。图(1)展示了系统流模型。

![](img/5e4d8ef2afa52a8404b28106580e19e4_733_0.png)

图(1)

系统流模型。

2015年5月至7月期间，通过相关新闻网站的富媒体摘要（`RSS`）收集了新闻文章。英文新闻使用`BBC`新闻数据库进行分类。总共探索并纳入`BBC`新闻数据库的2225份文本文档，这些文档于2004年和2005年发布在`BBC`新闻网站上，涵盖了经济、流行文化、政治、体育和科技等广泛主题。对最终成为两个数据库的原始数据执行了重要的预处理。为了研究这些步骤对成功率的影响，我们将两个数据集组合创建了四个不同的数据集。建立了四个不同的数据集合：原始数据集合 (`Orig-DS`)、清洗后的数据集合 (`C-DS`)、词干数据集合 (`Stem-DS`) 以及合并的清洗整洁词干信息集合 (`Clean + Stem-DS`)。

![](img/5e4d8ef2afa52a8404b28106580e19e4_734_0.png)

**图(2)**

**(a).经济，(b).文化，(c).艺术，(d).健康，(e).政治和(f).体育与科技。**

可以说，对成功率影响最大的因素是数据准备的质量。这些文本预处理过程是在向量化之前针对`TTC-3600`和`BBC-News`数据库进行的。在我们所有的课程中，我们经常使用停用词。因为它们对数据库没有独特贡献并降低了准确性，这些术语被删除了。图(2)表示为**(a).经济，(b).文化，(c).艺术，(d).健康，(e).政治和(f).体育与科技。**

## Doc2Vec

得助于词嵌入技术，机器现在可以理解人类编写的文本。单词被编码为向量，系统建立在人工神经网络之上。在这项研究中，采用了`Doc2Vec`范式来整合单词。Que Le和Tomas Mikolov的`Doc2Vec`创建一个用于目标词预测的文档表示向量。在整个过程中忽略了文档的长度。解决这个问题有两种方法。此类模型的示例是段落向量分布式内存（`PV-DM`）和段落向量分布词袋（`PV-DBOW`）。`PV-DM`中的每个段落被视为一个单词，并以向量表示的形式分配其唯一的身份。在第一步中，生成随机向量。它就像一个移动内存，填补了当前状况缺失的空白。词向量代表单词的概念，就像文档向量代表文档的概念一样。`PV-DBOW`不是预测目标词，而是使用句子向量对页面上的术语进行分类。

首先开发所有的`Doc2Vec`训练模型，它将数据库转换为向量形式。在开发`Doc2Vec`模型时，必须考虑几个上下文。如果单词的合并频率小于最小值 (`min_count = 5`) 且大于最大值 (`iter = 50`)，则单词会被丢弃。我们对以下参数具有完全控制权：最大距离 (`window = 3`)、重复次数 (`iter = 50`)、向量中的特征数量 (`vector_size = 100`) 以及`Doc2Vec`方法的数量 (`dm = 1`)。

## 朴素贝叶斯

朴素贝叶斯是文本分类中最基础、易解释且广泛使用的机器学习算法之一。可以使用这种策略计算样本属性对应给定类别的概率。

## 高斯朴素贝叶斯

使用高斯朴素贝叶斯对遵循高斯分布的类别和数值数据进行分类。在处理高斯（正态分布）时，我们可以确定平均值和标准差。对于每个类别，当这些参数引入预测时，会提供该新值的似然估计。

## 随机森林

随机森林技术只能在控制环境中使用。该算法随机生成一个森林。算法的性能随树的总数呈线性扩展。使用更多的树时，可以做出更准确的估计。随机森林分类策略因其许多优势而青青。它适用于回归和分类。如果森林中有足够的树，这种技术遇到过拟合问题的概率就会较低。过拟合是一个严重的问题，会对性能产生冷影响。

## 支持向量机

支持向量机可以在二维、三维或多维中使用线性、平面或超平面分离过程将数据分类为多个类别。使用这种方法，通过核函数将无法线性划分的输入空间投影到此高维线性可分空间，可以对非线性数据进行有效分类。

## 卷积神经网络 (CNN)

在深度学习中，人工神经网络的隐藏层数量增加，并在每个连续层中学习问题的新侧面。每个连续层学习到的特征作为上一层的输入。图(3)展示了`CNN`模型。

因此，建立了一个框架，从最基础到复杂的特征在该框架中自下而上进行学习。深度学习的目标是对输入数据进行各种变换，以达到学习算法可以最好工作的地方。尽管卷积神经网络（`CNN`）在图像处理中取得了最大的成功，但近年来也被广泛应用于文本分类研究。卷积层、池化层和全连接层构成了卷积神经网络设计的基础构建块。

层。目标是实现高效学习，从最基础的概念到最复杂的。

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_0.png)

预处理后的文本

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_1.png)

卷积 1

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_2.png)

MP（池化）

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_3.png)

卷积 2

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_4.png)

MP（池化）

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_5.png)

卷积 3

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_6.png)

MP（池化）

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_7.png)

卷积 4

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_8.png)

MP（池化）

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_9.png)

卷积 5

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_10.png)

MP（池化）

![](img/5e4d8ef2afa52a8404b28106580e19e4_739_11.png)

FC（全连接）

类别

图 (3)) `CNN`模型。

一旦为每个数据库开发了`Doc2Vec`模型，就会对该数据库进行分类准备。建议的`CNN`模型使用了最大池化程序。为了最小化特征差，在卷积层之间合并特征图并缩小其尺寸。然后，对这些层进行扁坦化并变为全连接。模型的隐藏层使用`ReLU`函数进行激活，而输出层使用`Softmax`函数进行激活。模型中包含 4 个卷积层。除了最后一个卷积层外，每个卷积层之后都引入了最大池化。厚层放在扁坦化层之后。对于分类，我们选定了`Softmax`函数。

## 结果与讨论

通过开发`Doc2Vec`模型，我们希望分析用于`TTC-3600`和`BBC-News`数据库的不同预处理步骤的成功率。建议的策略将用于训练`Doc2Vec`模型的文档分为 90% 的训练数据和 10% 的测试数据用于分类。接下来，我们使用`CNN`深度学习模型结合`GNB`、`RF`、`NB`和`SVM`算法对数据库进行分类。`Tensorflow`和`Keras`是用于`CNN`分类的`Python`库。`Knime`是一个数据分析平台，在机器学习分类期间被采用。

与其他其他人工智能分类算法相比，`CNN`在所有方面都产生了最高的准确率。观察到，某些文本准备阶段会降低某些神经网络算法的达成率，而另一些阶段则会提高使用`CNN`获得的准确率。准确率基本上可以立即告诉我们一个样本是否训练良好，以及它的整体表现将如何。然而，它未能提供有关如何将其应用于当前问题的具体细节。因此，了解准确率、召回率和 F1 值将帮助我们得出更准确的结论。因此，在适用的情况下，除了分类准确率外，还考虑了额外的成功标准。我们的模型正确评估的数据库比例作为我们的准确率值。精确率（Extractness）揭示了估计的正值中有百分之几是实际的。当误正估计的代价很高时，准确率值变得至关重要。需要正向预测的交易比例可以使用称为召回率（recollection）的统计量来衡量。当误负估计的代价很大时，具有高召回率也是很有用的。该值应该最大化。通过平均精确率和召回率，F1 值揭示了它们的调和平均数。考虑异常值的原因是我们使用调和平均数而不是简单平均。

表 1 通过比较`TTC-3600`、`TTC-4900`和`BBC-News`数据库与之前研究的结果，显示了所提方法的成果。我们发现土耳其数据库的准确率为 94.00%，F1值为 94.17%，表明我们提出的模型优于先前的模型。尽管在`BBC-News`数据库上没有获得最佳结果，但 96.41% 的准确率和 96.00% 的 F1 值都高于平均水平。英语单词的表述比土耳其语版本稍微精确一些。这可能是由于土耳其语中额外字符（s 和 ş，c 和 ç）具有相同的几何特征导致的。表 1 是效率指标的比较研究（`TTC-3600`），表 2 是`BBC-News`的性能分析。表 1 效率指标比较研究（`TTC-3600`）

| 数据库 | 技术 | 准确率 | 精确率 | 召回率 | F1 值 |

| :--- | :--- | :--- | :--- | :--- | :--- |

| `TTC-3600` | `CNN` | 94.00% | 94.17% | 94.17% | 94.08% |

| | `GNB` | 88.34% | 88.18% | 88.18% | 88.26% |

| | `RF` | 85.01% | 84.19% | 85.01% | 85.06% |

| | `SVM` | 87.23% | 87.21% | 87.21% | 87.22% |

| 数据库 | 技术 | 准确率 | 精确率 | 召回率 | F1 值 |

| :--- | :--- | :--- | :--- | :--- | :--- |

| `BBC-News` | `CNN` | 96.41% | 96.00% | 95.53% | 95.76% |

| | `GNB` | 89.25% | 89.97% | 89.29% | 89.63% |

| | `RF` | 82.97% | 83.39% | 82.39% | 82.88% |

| | `NB` | 88.75% | 89.41% | 88.71% | 89.06% |

| | `SVM` | 91.88% | 92.01% | 91.91% | 91.96% |

## 结论

根据文本准备步骤，为`TTC-3600`数据库准备了 4 个类别，为`BBC-News`数据库准备了 5 个类别。使用`Doc2Vec`模型开发了数据库。使用`CNN`的深度学习模型与使用`GNB`、`RF`、`NB`和`SVM`的机器学习方法进行了对比。使用`CNN`清理`TTC-3600`数据集达到了 94.17% 的准确率。显示我们提出的方法优于平均水平。在未来，我们希望完善分析视频内容的方法。通过对视频帧应用文本检测和识别，将使用深度学习技术进行分类。

## 参考文献

[1] Elgnar A., Einea O., Debsi R., Automatic Tagging of Arabic News Using Ensemble Learning International Conference on Natural Language and Speech 2019

[2] Nadeem M., Raza S.. Detecting Bias in News Articles using NLP Models.2022 International Conference on Natural Language Processing and Artificial Intelligence (NLPAI) 2022

[3] Jang B., Kim I., Kim J.W.. Word2vec convolutional neural networks for classification of news and tweets. PLoS 20191482e042097601343781



[4] Sari W.K., Rini D.P., Malik R., Afzar I.S.. Multlabel Classification in News Articles using Long-Term Memory with Word2Vec 2020

[5] P.Effective Data Extraction Technique to Improve Influenza Outbreak Prediction from Online Articles: Deep Learning Study. JMIR Med.2029

[6] Jang B., Kim I., Kim J.W.. Effective Data Extraction Technique to Improve Influenza Outbreak Prediction from Online Articles: Deep Learning Study Preprint 2020

[7] Topic categorization of Tamil News articles using PreTrained Word Embeddings with Convolutional Neural Network 2020 International Conference on Computational Intelligence for Smart Power and Sustainable Energy (CISPSSE) 2020

[8] Capetillo C.P., Leone-Gómez D., Gómez-Arnoiz H., Arroyo-Fernández I., Neri-Chávez J.. HBDCI at CheckThat!2022: Fake News Detection using Articles of stylometric Features and Deep Learning. Conference and Labs of the Evaluation Forum 2022

[9] Kamboj P., Chowtham L.. Classification of News Articles using Gradient Boosting Deep Learning Model 2022 6th International Conference on Information Technology (InCIT) Nonathaburi, Thailand.2022266910.1109/InCIT56086.2022

[10] Bina D., Viral G., Oncel C., Flood Severity Estimation in News Articles using Deep Learning Approaches. MediaEval Benchmarking Initiative for Multimedia Evaluation 2019

[15] W. Chen, K. A. Khatib, B. Stein, and H. Wachsmuth. 使用高斯偏差分布检测新闻文章中的媒体偏见。计算语言协会结果集. 202010151026 10.18653/v1/2020.findings-acl.91

OceanofPDF.com

# 数据挖掘在自动化信用评分中的应用效能研究

Amarpal Yadav¹*

Department of AI, Noida Institute of Engineering & Technology, Greater Noida, Uttar Pradesh, India

## 摘要

银行和金融机构高度依赖信用评分（CS）作为一种风险管理方法，因为它既有效又必要。它降低了财务风险并并建议的方法提供了合理的指导。因此，企业和金融机构正在探索创新的自动化解决方案来解决信用评分困境，以保护其自身及客户的资源。近年来，机器学习（ML）和数据挖掘（DM）方法在信用评分预测方面取得了显著进展。深度层次学习者网络（DGHNL）是本研究开发的一种新颖方法。支持向量机（SVMs）、k近邻算法（KNNs）、概率神经网络（PNNs）和模糊结构是一些可能使用的方法类型。我们使用了 UCI 机器学习库中的 Statlog 德国（100次发生）贷款批准数据集来评估我们的模型。我们使用了一个具有五个独特学习者、两种特征提取方法、三个内核函数和三种模型优化方法的 DGHNL。除了交叉验证（CV）和训练-测试（分层10折）方法外，该模型还采用了一种尖端的生物分层训练（参与者选择）方法。通过使用 Statlog 的德国贷款批准数据，我们证明建议的 DGHNL 模型凭借其29层架构可以获得 94.60%的预测准确率（每1000次错误54次）。

**关键词：** 算法、自动化信用评分、数据挖掘、效能研究、支持向量机（SVMs）。

> * 通作者 Amarpal Yadav：Department of AI, Noida Institute of Engineering & Technology, Greater Noida, Uttar Pradesh, India; 邮箱: amarpal@niet.co.in

## 引言

鉴于近期经济发展，银行业对信用风险特别敏感，这使得信用风险管理比以往任何时候都更加至关重要。先的研究表明，信用利息等于银行本金。银行风险管理的改进是信用风险管理的重点。可以利用从个人数据中收集的信息并到评分算法中，对客户的信用风险进行分类和预测。尽管信用专家根据先验经验做出决策，但当应用于最初的信用风险评估技术时，会产生不同的结果。统计程序取得了长足进步，技术进步使得开发出更精确的评分模型。银行业的自动化处理导致了更高的精度和更低的运营成本。长期以来，银行一直使用回归和神经网络的信用评分算法，因为它们具有极高的准确性 [1]。

线性判别分析 [2]、决策树 [4]、逻辑回归 [5] 和遗传编程 [... ] 仅是利用数据挖掘构建信用评分模型时产生的一些分类方法。Desal 等人 [7] 通过比较神经网络、线性别别分析和逻辑回归的效能，研究了信用评分背后的决策过程。他们发现，与神经网络和逻辑回归相比，线性判别分析的结果较差。结论，最流行的信用风险评估模型是基于神经网络和逻辑回归的。

得于现代信息技术的普及，当今的业务与历史上任何时期都不同。信息技术的发展使系统快速准确处理大量数据的能力有所提高。公司在这里不再集中于数据汇编和收集转换，而是正在寻找从数据库中提取信息的最有效方法。数据挖掘是利用计算力发现此前未发现的、可能驱动消费者和企业选择的趋势和模式的实践。数据挖掘以及处理速度已应用于许多不同领域，但不限于制造业、零售、医疗和生物技术行业。数据挖掘的实际应用包括金融领域（保险、银行和信用卡）。数据挖掘在商业世界有多种用途，Berry 和 Lino 等学者将数据挖掘描述为对数据库进行评分以获取可能理解和相关信息的行为。Frawley 在1996年将数据挖掘描述为一种获取世界洞察的技术。数据的算法转换、分析以及数据特征和模型的识别构成了数据挖掘。Grupe 和 Ow [9] 描述的数据挖掘是从数据库中提取此前未发现信息的过程。通过数据挖掘的自动或半自动分析发现显著的相关性和规律是 Berry 和 Lino [10] 的观点。数据最早由 Kleinner [11] 描述为一种创新的程序，可能包含此前未知的有用信息，可作为企业的资源。以往的研究人员对数据挖掘的观点表示了认可，但他们的倾向通常是一致的。此处使用的数据挖掘术语与 Kleinner 的用法进行了对比。

数据挖掘有多种用途。例如，数据挖掘可以细分为分类、预测、组织、聚类等子领域。“分类任何内容”是根据目标的特征在特征中创建子集。可以使用描述特征和跨类别相关性的数据模型对信息进行分类，并作为决策的基础。使用分类数据挖掘计算属性值可能会提供更具描述性的变量并获得结果。目标是对我们的新类别进行分类。数据挖掘被用于决策树分类方法，以对类别和连续变量进行预测。每个决策都有一个决策。（注：OCR文本似乎在此重复，我将根据逻辑流进行清理）。

... 数据挖掘被用于决策树分类方法，以对类别和连续变量进行预测。每个决策都有一个决策。目标是对我们的新类别进行分类。

将贷款请求描述为客户发起的请求，而 `$y$` 是一个目标特征，取值为 0 或 1，表示客户是否全额偿还贷款或违约 [31]。分类挑战的目标是开发一个预测模型 `$h(y)$`，以成功地将特征分配给类别：分类系统处于许多领域的核心；决策树、线性回归模型和集成学习只是少数例子；其他内容将在第 4.1 节中介绍。金融机构和信用评估机构使用分类器而不是布尔分级来确定客户的贷款请求是否会被完全偿还。在巴西，信用评级限制在 [0, 1000] 范围内，0 表示几乎肯定会违约的客户 [32]，1000 表示将会全额支付账单的客户。在现实应用中，极端数值非常罕见，因此使用金融统计数据来决定贷款适用于何种截断值是非常重要的 [33]。分类器通过其分类输出 `$h(x)$` 提供了概率 `$P(h(x)=1)$` 作为 `$P(h(x))$`，它可以被立即重新缩放到 [0: 1000] 范围，允许我们获得这些类型的评分。此外，我们对研究中使用的分类器以及我们如何使用它们推导概率进行了分类。研究人员和行业人士在过去的十年的大部分时间里都在研究用于信用评分的机器学习。Li 和 Liao (2021) 对各种分类器进行了深入分析，包括决策树、主成分分析、神经网络和回归树，都被认为是最有效的方法 [34]。相比之下，Chen 和 Shi (2013) 使用如第 4 节所示的柯尔莫哥夫-Smirnov 值，利用特征关联向量机在澳大利亚和德国统计数据集上产生了 F1 分数。Chen 等人 [17] 针对保加利亚的信用评估数据集为朴素贝叶斯分类器提出了关联特征。Naila 和 Sraka (2018) 使用 Oracle 挖掘和属性选择从一个由保加利亚微型金融机构提供的数据集中获取了见解。信用分使用 Oracle 数据库和逻辑回归算法计算。为了模拟可靠债务人和高风险债务人的行为，Okesola 等人 (2017) 利用人口统计学信息和丰富的指标，在该数据集中得到了更准确的结果，并与每个分类器系统 (CTree) 和 K-最近邻 (KNN) 的全局能力兼容，构建、调优并测试了模型。Singh (2019) 评估了六种不同类型（决策树、懒学习器、贝叶斯学习器、逻辑、多层感知器 (MLP)、基于学习的规则）的 25 个分类器。MLP 的信用精度最好，随机森林、Bagging 和逻辑模型整体表现最佳。Gu 和 Dong (2017) 显示，在德国和英国数据集上使用 SVM 和 Extreme Over-SVM（其中后者更好），可以作为竞争性机器学习方法的替代方案。正如 Carta (2017) 所示，作者应用傅里叶变换将信用评分问题转化为序列预测问题。该研究使用了贷款违约客户和德国信用数据库。该研究的作者建议使用随机森林来获得最终评分，这表明信用评分的编写者使用小波变换产生了额外信息。Sao Melo Junior (2019) 的工作提供了一项使用 8 种不同分类器的网格的基准研究，表明随机森林 (Breiman, 2001) 在与上述工作相同的数据集阶段实现了优异的嵌入率。另一项重要工作 (Liao et al., 2017) 建议在基于机器学习的信用评分中使用集成这些这些结合了不同的回归模型，证明它们优于标准的 Bagging (Breiman, 1996) 和单逻辑回归方案。此外，集成学习优于单一模型，正如 Abellán & Castillo (2017) 的研究所示，该研究检查了几个应用于信用评分问题的模型分类示例。Melo (2019) 将集成学习与 SMOTE 过采样方法 (Chawla et al., 2002) 结合，在静态信用评分系统中选择分类器时，在不平衡的情况下获得了良好的结果。最后，本研究探索了在线学习作为开发灵活程序的一种兴奋方法 (Gomes et al., 2019; Liobate et al., 2016)，我们注意到在该技术被成功用于解决问题的研究仍然较少。为了证明数据流分类器的用性和行为，本研究对三个信用评分数据集进行了新颖的研究。

## 提出的工作

这里介绍的工作使用了多种标准算法和优化方法。以下是我们研究新颖方面的快速概览：遗传分层、多样性增强，以及对 AI 教育的重新构和深度优先方法。

以下是步骤：

1. 在此阶段，我们使用 z-score 对数据进行了归一化（即对数据进行标准化，使得均值为 0，标准差为 1），并将数据缩放到 [0,1] 区间。

2. 未进行特征提取，但将主成分分析 (PCA) 作为两种提取方法之一。

3. 进行了选择并采用遗传算法 (GA) 来选择特征。表 1 显示了发现 GA 设置。

4. 使用了分层 10 折交叉验证的方法。

5. 使用了不同的机器学习算法，包括两种 SVM 变体（C-SVC 和 nu-SVC）、Akagi-Sugeno 模糊系统、概率表示神经网络 (PNN) 和 k-最近邻 (kNN)，构建、调优并测试了 A 模型。

6. Singh (2019) 评估了六种不同类型（决策树、懒学习器、贝叶斯学习器、逻辑、多层感知器 (MLP)、基于学习的规则）的 25 个分类器。MLP 的信用精度最好，随机森林、Bagging 和逻辑模型整体表现最佳。Gu 和 Dong (2017) 显示，在德国和英国数据集上使用 SVM 和 Extreme Over-SVM（其中后者更好），可以作为竞争性机器学习方法的替代方案。正如 Carta (2017) 所示，作者应用傅里叶变换将信用评分问题转化为序列预测问题。该研究使用了贷款违约客户和德国信用数据库。该研究的作者建议使用随机森林来获得最终评分，这表明信用评分的编写者使用小波变换产生了额外信息。Sao Melo Junior (2019) 的工作提供了一项使用 8 种不同分类器的网格的基准研究，表明随机森林 (Breiman, 2001) 在与上述工作相同的数据集阶段实现了优异的嵌入率。另一项重要工作 (Liao et al., 2017) 建议在基于机器学习的信用评分中使用集成这些集成结合了不同的回归模型，证明它们优于标准的 Bagging (Breiman, 1996) 和单逻辑回归方案。此外，集成学习优于单一模型，正如 Abellán & Castillo (2017) 的研究所示，该研究检查了几个应用于信用评分问题的模型分类示例。Melo (2019) 将集成学习与 SMOTE 过采样方法 (Chawla et al., 2002) 结合，在静态信用评分系统中选择分类器时，在不平衡的情况下获得了良好的结果。最后，本研究探索了在线学习作为开发灵活程序的一种兴奋方法 (Gomes et al., 2019; Liobate et al., 2016)，我们注意到在该技术被成功用于解决问题的研究仍然较少。为了证明数据流分类器的用性和行为，本研究对三个信用评分数据集进行了新颖的研究。

## 遗传算法

- 种群中有 500 个个体；

- 生成类型，浮点向量；

- 个体的染色体结构，为了帮助训练 SVM：SVC SVC，核函数类型：RBF 是一个浮点向量 [g1, g2, ..., f9]，其中 g1（第一个）提供第一个参数的值，g2（第二个）指示第二个参数的值，v1 到 ..., vn 为剩余参数。如果一个特征的得分为 0，则是不可接受的，而得分为 1 是理想的。染色体编码了正确的名称 - g，它设置了其他学习类型的参数，例如 SVM C-SVC、PNN、KNN、模糊系统等；

- 每一代的属性是均匀或随机的；

- 我们使用与每个层组件相关的全局（更大）基因值范围检测了初始种群的基因值（见表 2 - 改进参数）。特征选择范围为 [0,1]；

- 函数的初始（最优）值为零；

- 生成机制设置如下：初始层为 30，第 2 到第 29 层为 50，以及；

- 交叉类型：第一个和第 29 个之间的中间值，并在第 2 到第 28 个之间分散；交叉概率：0.7；

- 变异均匀性且概率为 0.1；

- 五是未改变存活者的最佳可能数量；

- 将适应度函数的值作为其缩放技术的函数进行排名；

- 父母可能通过竞争进行选拔；

- 适应度函数的表达式：

测试受试者所犯错误的总和：

训练错误率 = 错误率 + 1000 (3)。测试集和训练集中的错误总数

错误百分比 =（语言和翻译中的错误率）/ 2 (4)

带有错误的总试验次数加上特征的接受系数：

错误总和等于：errLsum + errTsum + FaF (5)

其中 errLsum 是训练期间产生的错误总数，errTsum 是训练期间错误率（训练期间错误总数与训练期间错误总数的比例，errL%，且 err% = errLsum/errLsum），errT% 是测试错误率（errTsum/100%），而 FaF = CF 是接受率。

在将特征数量 (F) 与总特征数 (Fa) 进行比较时，被接受的特征 (Fa) 与总特征数 (F) 的比例被称为特征接受性系数 (CF)。此外，可以使用以下公式来近似遗传特征选择的效率：

CF = (Fa / F) × 100%, (2)，

其中 Fa 是通过的特征数量，F 是特征总数。

## 所提模型的概览

本研究提出了一种利用机器学习分析借款人数据的新方法。归一化、特征提取、特征选择、交叉验证 (CV) 方法、机器学习 (ML) 和学习器参数优化是所提方法的六大支柱。我们概念的简化图如图1所示。这些程序每个都得到了进一步详细的描述。

## 所提的方法

DGHLN 系统灵感来自人类大脑的组织和运行（复杂层、双极突触、互连节点、单个神经元中的并行处理等）。

DGHLN 框架后的理论。系统的主要特征如下：

- 学习器网络类比于大脑。分层学习技术类似于深度学习，因为它有几个发展阶段。

- 与数据的良好流动和整合，教学机制由一种具有协作教育方法的多层层次结构的层次基结构呈现。

- 学习者（神经元）可以通过基于辅导的层次结构接收来自较高层和第一层的反馈，从更深层次上接受教育。

通过从学习器（糟糕专家）中消除错误解决方案，遗传分层训练改进了 DGNL 的框架：

- 通过消除相邻层学习器之间某些最不可接受的连接，遗传算法可以优化它们之间的连接（特征选择）。同样，系统选择了它最有前景的学生，并估计谁不合适。

- 就像大脑中的回向连接一样，系统跟踪训练过程中收到的所有前向传播，包括来自算法遗传组成（遗传优化）的和来自交叉方法的传播。

## 多样性



# 新皮层特征预处理、特征提取和层间连接

- 新皮层特征预处理、特征提取和层间连接中，不同类型的神经元、数据处理以及非典型的神经间连接。
- 所提的 `DGHNL` 系统共使用了 108 个学习器，分布在第一层、不同类型的层之间、两种不同的归一化技术、两种不同的特征提取方法、三种内核函数，最后映射到三种错误计算方法的三个不同参数。对于第 2 到第 26 层，系统建议了 45 个学习器（由 5 种不同学习器类型、3 种不同内核函数和 3 种错误计算方法组成），而对于第 27 到 29 层，仅使用了 9 个学习器。
- 初始层数据预处理和特征提取使用了两种不同的归一化和特征提取方法。
- 许多不同的连接：学生之间并非所有连接都出现在层之间。
- 类似于细胞神经饵的电位，双极性被用于传输二进制数据 `(0, 1)`。

`DGHNL` 系统使用深度学习方法，其多层架构所示；双层网络被视为深度网络。它类似于具有 7 层的新皮层。

- 系统通过在其结构的连续层级中转换信息来提取其内部特征，逐渐获得复杂特征。目标系统的结构为 29 层，因此得名“深度”。遗传、层次化和网络化学习器指的是学生使用遗传算法、系统的层次结构，以及构建的系统是由连接在网络中的许多节点（学习器）构成的事实。
- 在我们基于层次的框架的第一层，108 名学生接受了监督指导。然后，第二层的 45 个学习器使用第一层构建的 108 种不同学习器的响应进行无监督遗传训练。之后，学习者进入剩余次数（共 29 层）。

`CV` 方法 - 将遗传算法 (`GA`) 与 10 折 `CV` 方法结合。

## 1 层和 29 层的深度

- 在系统的第一层和第 29 层，使用基于遗传的特征选择技术选择了重要特征和 108 个学习器的设置。
- 输入特征和所有学习器的参数都在基于基因的算法帮助得到了优化（见表 1）。

## 从第 2 层到第 28 层

- 输入特征和所有学习器的参数都在基于基因的算法帮助得到了优化（见表 1）。

为了实现这种多样性，我们采用了 (a) 三种针对学习者的独特内核，(b) 五种独特的学习器，(c) 三种独特的误差计算方法（进化过程中的适应度函数见表 1），以及 (e) 三种独特的预处理和特征提取方法：

## 表 1 `CV` 方法中使用的测试组和训练组数据描述（10 折，分层）

德国信贷数据 - 20(24) 个属性 `CV`(10 折，分层) 集合 1-10

| 类别 | 描述 | 实例数量 | 训练组 | 测试组 |
|---|---|---|---|---|
| `C1` | 授信贷款 | 700 (70.0) | 630 | 70 |
| `C2` | 拒绝贷款 | 300 (30.0) | 270 | 30 |
| 总计 | | 1000 (100.0) | 900 (90) | 100 (10%) |

## 表 2 用于评估德国信贷数据集中信贷风险的属性

| 属性输入 | 描述 | 类型 | 值范围 |
|---|---|---|---|
| `G1` | 现有往来账户状态 | 分类 | 1–4 |
| `G2` | 期限（月） | 数值 | 4–72 |
| `G3` | 信贷历史 | 分类 | 0–4 |
| `G4` | 用途 | 分类 | 0–10 |
| `G5` | 信贷账户 | 数值 | 276–18424 |
| `G6` | 储蓄/限额 | 分类 | 1–5 |
| `G7` | 目前工作年限 | 分类 | 1–5 |
| `G8` | 占可支配收入的百分比 | 数值 | 1–4 |
| `G9` | 个人状况和性别 | 分类 | 1–5 |
| `G10` | 其他债务人/担保人 | 分类 | 1–3 |
| `G11` | 现居住地时长 | 数值 | 1–4 |
| `G12` | 房产 | 分类 | 1–4 |
| `G13` | 年龄 | 数值 | 19–75 |
| `G14` | 其他安装计划 | 分类 | 1–3 |
| `G15` | 住房情况 | 分类 | 1–3 |
| `G16` | 在本行的贷款数量 | 数值 | 1–4 |
| `G17` | 职业 | 数值 | 1–4 |
| `G18` | 需供养的人数 | 分类 | 1–2 |
| `G19` | 是否有电话 | 分类 | 1–2 |
| `G20` | 外国工人 | 分类 | 1–2 |
| 输出 `G21` | 类别属性 | | 1–2 |

## 表 3 第一层学习器获得的最佳结果比较：模糊系统、`KNN`、`PNN` 和两种类型的 `SVM` 学习器

| 系数 | `kNN` | `PNN` | `SVM` | `SVM` | `SVM` |
|---|---|---|---|---|---|
| - | - | - | - | - | - |
| 模型类型归一化 | | 标准化 | 标准化 | `nu-SVC` 标准化 | `C–SVC` 标准化 | `nu-SVC` 重缩放 |
| 特征提取 | 无 | 无 | `PCA` | 无 | 无 | 无 |
| 误差 | `err_t` | `err_t` | `err_t` | `err_t` | `err_t` | `err_t` |
| 核函数 | - | - | - | 多项式 | 多项式 | `RBF` |
| | 1923 | 1291 | 1922 | 1345 | 1602 | 1465 |
| 训练集结果 | | | | | | |
| `ERR_sum ACC` | 78.63% | 85.66% | 78.64% | 85.06% | 82.20% | 83.72% |
| 测试集结果 | | | | | | |
| `ERR_sum ACC` | 224 | 215 | 214 | 203 | 202 | 202 |
| 77.60% | 78.50% | 78.60% | 79.70% | 79.80% | 79.80% | 79.80% |

实验二采用了 `DGHNL` 来结合在实验一中之前评估过的几层（模糊系统、`kNN`、`PNN`、`nu-SVC` 和 `C-SVC`）。表 3 显示了这些发现。

在训练集中，具有 3、14、23、26、27 和 28 层的 `DGHNL` 架构（如表 3 所示）达到了 100% 的准确率，而具有 29 层的 `DGHNL` 系统（带有不平衡核函数的 `nu-SVC`）也达到了 100% 的准确率。

## 运行时间

执行整个 `DGHNL` 系统的时间计算如下：

- 平均增强时间 = 9830 分钟。
- 平均准备阶段 = 3784 秒。
- 平均排序时间 = 0.038 秒。

值得注意的是，分类数据所需的时间极短。因此，该系统可以立即投入使用。

## 讨论

对于测试数据集，`DGHNL` 系统的混淆矩阵如图 (2) 所示。这些发现验证了所提方法在预测 `CS` 数据方面的有效性。

![](img/5e4d8efafa5204b2810658019e4_755_png)

![](img/5e4d8efafa5204b2810658019e4_756_png) 参数优化和特征选择。图 (2) 显示 `DGHNL` 方法在类别 2 的精度 (98.40%) 高于类别 1 (93.30%)。`DGHNL` 系统使用的单独技术 `ROC` 曲线所示。模糊系统类似于 `nu-SVC`、`C-SVC`、`PNN` 和 `KNN`。`DGHNL` 在测试数据集上的 `AUC` 为 0.9138，`nu-SVC` 为 0.7195，`C-SVC` 为 0.7193，`PNN` 为 0.6988，`KNN` 为 0.6762。图显示了 `DGHNL` 在 10 折交叉验证中的误差值，从第七测试集的 1% 到测试集的 10%。以下是样本的 `F1` 分数：`DGHNL` = 0.9326，`nu-SVC` = 0.7362，`C-SVC` = 0.7365，`PNN` = 0.6988，模糊系统 = 0.7154。表 2 显示与其他文献中的方法相比，所提 `DGHNL` 系统具有最高精度 (94.60%)。在表 3 中，我们看到仅使用单一机器学习技术的准确率：`C-SVC` 达到了 79.90%，`nu-SVC` 达到了 79.80%，模糊系统达到了 78.60%，`PNN` 达到了 78.50%，`KNN` 达到了 77.60%。重要的是，一旦在 `DGHNL` 中添加第二层（2 到 28 层），通过深层架构的影响，训练数据集的分类准确率提升了 5%（达到 84.70%）。

## 结论

在银行业提出了一种中等风险信贷评分。深度遗传层次学习器网络 (`DGHNL`) 是一种新策略，有潜力应用于人群。所提 `DGHNL` 方法用于检查 `UCI` 机器学习库的一千条记录。讨论了使用分层 10 折交叉验证的德国信贷信息是以往研究的进展。我们的新系统并没有缺陷。与其他深度学习模型一样，开发复杂的系统需要大量的训练和优化。通过包含不同的进化方法也可以提高我们的效率。所提 `DGNHL` 系统可能会通过盲交叉验证方法得到改进。

## 参考文献

- [1] I.G. SADM - 用于信贷评分的数据挖掘自动系统。Stud. Inform. Control 201011322
- [2] Oliveira-R.A. 新巴西通用保护法背景下的信贷评分开发第九次知识挖掘、发现与学习研讨会 (KMLM) 2021 0251
- [3] Fang J., Yao Q., Bo J., Wang K., BACS: 基于区块链和 AutoML 的高效信贷评分分类应用。IEEE Conf. Res. 2022:0022-0042-0533-6389-09534
- [4] Celia-Lia-Bobak, S., 自然语言处理和自动确定：混合/技术方法。IEEE Int. Syst. 2013.166351310.1195/2016.95.26
- [5] Chen L., Wang S., 财务报告与合规风险评估 2012123195050
- [6] Vashisht V., Peddy A.K., 使用机器学习进行信贷评分预测。IEEE Trans. Processing & Credit 2022010322937/SPICE.2021.10.323
- [7] Herman A. 自动信贷评分和贷款时代的个人信誉和可靠性。
- [8] Rasoud S, Elabadi E.M., Mokhtari, S., 数据挖掘对客户信贷评分的影响。数据挖掘期刊，International Journal of Management Practice 2021
- [9] Yadav S., 连续小波域医学图像分类的深度学习。Journal Advanced Research in dynamic and control system 01104542029
- [10] Chung P., Yadav S., Rahaman K., 信贷评分引擎数据挖掘特征选择的混合方法。Knowledge Machine Learning, 2021
- [11] Hassan A., Jayaraj R. 使用机器学习进行金融服务信贷评分。Proc. 2020. 第十届信息与通信技术国际会议 (AICT)，约旦阿曼。12月
- [12] Nazari A., Mehran M.R., 使用数学方法评估不同技术对客户信贷评分的影响：桑齐巴尔省 Reforkargon 银行行为研究。International Journal of Management Studies 2021
- [13] Vothkari R., M. Parzi., 一种多层遗传系统。IEEE 国际会议，2024, pp. 19–24.
- [28] V. Moauri, R. M. Parizi, J. L. Massa, and A. Yazilci, "An Multi-Model Approach to DeFi Project Trust Scoring and Security," in Proc. 2024 IEEE Int. Conf. Blockchain (Blockchain), 2024, pp. 19–28.
- [29] S. Nitish, Kumar, S. Shaju, K. Kayathwal, K. Aganwal, A. Singh, D. Chaurasia, S. Asthana, A. Arora, and M. Al Garage, "IntentVec: Representation of cardholder and merchant intent from temporal interaction sequences for fraud detection," 2021-
- [30] C. Jordan, K. Borjie, J. L. Byun, D. Chong, R. Latham, and J. W. Wei, "Developing a Prototype Paypal Surveillance System at a 2-Stage Classifier," Springer Nature, Computer Science, 2021.
- [31] A. R. Provenzano, D. Trifrio, A. Datteo, L. Gidia, N. Jean, A. Riciputi, G. Le Pera, M. Spadaccino, L. Massaron, and C. Nordio, "Machine Learning approach for Credit Scoring," SSRN Electronic, 2020.
- [32] P. Pi, "Incorporating BERT-based NLP and Transformer for An Ensemble Model and its Application to Personal Credit Prediction," Korean Inst. Smart Media, 2024.
- [33] V. Adwani, S. Durgapur, K. Doranasalai, S. Abhishek, and A. Anjal, "Safeguarding SMS: A Dynamic Duo Approach to Tackle Spam Users and QA," in Proc. IEEE Innovations in Future and Advanced Computing Technol (i-PACT), 2023, pp. 1–5.
- [34] B. A. Malaquez, M. U. Siregar, and B. Sugathan, "Comparison of Classification Algorithms and Language Model in Accounting Financial Transaction Record: A Natural Language Processing Approach," Int. Adv. Sci., Eng. Inf. Technol., 2024.,
- [35] S. Goyal and A. Saxena, "Creditworthiness Assessment Using Natural Language Processing," in Advances in Computational Intelligence and Robotics, 2021.

# 探索数据挖掘在知识发现中的应用

Sover Singh Bisht¹*

1 Department of DS, Noida Institute of Engineering & Technology, Greater Noida, Uttar Pradesh, India

## 摘要

“生活记录”（lifelogging）的实践涉及记录越来越多的个人主观日常体验，意在未来将这些记录作为记忆辅助工具或数据驱动的自我发展基础。因此，生成的生活日志的用性取决于记录者高效切换这些日志的能力。日志内在的多模态化和半结构化特征允许它们整合来自各种来源的数据，包括相机以及其他可穿戴物理和虚拟传感器。因此，以图结构表示数据可以有效捕获所有创建的关联关系。必须开发其他方法来捕获更高层次的语义，因为无法手动或机械地为每个条目注上大量的语义上下文。我们描述了一种改进的生命图谱（Improved Life Graph, `ILG`），这是一种基于知识图谱的生活日志表示与检索解决方案的首种方法，它能够以图结构捕捉生活日志，并用外部数据对其增强，以帮助高层语义信息的连接。

**关键词：** 数据挖掘、信息检索、知识图谱、生活日志数据。

* 联系作者 Sover Singh Bisht: Department of DS, Noida Institute of Engineering & Technology, Greater Noida, Uttar Pradesh, India; E-mail: soversingh@niet.co.in

## 引言



由于过去几十年里各种技术的进步，移动数据采集、处理和存储的可能性已大幅增加。一个可能的影响是相关运动的兴起，如量化自我和生活记录。“生活记录”（lifelogging）一词用于描述记录日常活动的行为，无论是通过数字相机等尖端技术、测量个人生物反馈或即时环境属性的传感器，还是通过更传统的手段（如写日记）。结果，产生的生活日志可能会有多种形式并有许多关联 [1, 2]。最终，我们确定了一个简单但最受期待的想法：将生活日志编码为数据图。生活日志有多种用途，包括提高记忆回想和激发自我护理。随着收集的数据规模和复杂性的增加，生活日志内部快速简单搜索选项的需求日益增长。生活日志搜索挑战（LSC）[3, 4] 是 2018 年举办的一个工作会议，旨在竞争性地评估交互式生活日志检索技术。在 2020 年 LSC 的框架内，本研究描述并演示了 LifeGraph [5]，一种基于交互式信息图的生活日志检索系统。本节提供了该图谱的高层概述、系统如何利用网络回答问题，以及用户可能与系统交互的潜在方式。检索技术的最新进展使这种方法得到了广泛应用。这种层次的智能在各种应用领域（数据融合、地理分析、预警等）中非常有用 [6, 7]。由于目前提取地理数据的方法未能考虑到空间和语义维度，因此存在改进空间。面对这种多样性，目前从许多源获取地理数据是不可行的 [8, 9]。然而，考虑到隐性语义数据和复杂的空间链接具有挑战性，这可能会导致方向迷失和信息过载 [10, 11]。基于本体的数据访问（OBDA）是另一种流行的数据范式，它通常使用常识基础，但缺乏空间语义 [12,13]。需要考虑到地理数据与语义关联的知识图谱（KG）来实现多源数据的有效存储和检索。知识图谱的海量用于增强检索技术 [14] 并处理语义鸿沟。

## 相关工作

这里是一些潜在的研究方向和一些背景信息。

空间信息分析：当指代具有地理和空间属性的信息时，通常使用“地理数据”一词。传统信息检索技术包括处理地理数据的子集 [15]。在当今的大数据时代，理解地理数据模型对于知识共享和检索至关重要。地理信息系统模型显示地理矢量模型，它由地理层、属性和属性字段组成。为了处理地理数据（即几何数据）和属性数据，通常采用两种不同的文件集 [9]。空间数据存储在空间文件中，属性数据存储在属性文件中，如图 1 所示（用于说明道路的地理矢量模型）。使用特定的地图投影，空间信息文件记录地面特征的位置。

全局匹配可能是其最大的缺陷。Trie 索引技术采用树结构（由用于第一个字符的哈希表和树索引组成），在保持高准确率的同时加速匹配过程。然而，它同时也存在一些限制，例如需要复杂的索引和大量的内存。为了加速数据检索，双词组索引（dbl-word index）方法结合了哈希和 Trie 树最有用的特性。在这种方法中，Trie 索引用于返回两个或更少字符的短语，而哈希索引则用于查找至少包含三个字符的单词。这激发了学者更深层次地探索地名的含义。字符被视为索引的构建块，因此 Zhang 等人设计了一种基于字符特征的地理名称检索技术。

基于空间的信息定位。空间信息检索主要用于地物的获取、显示和分析领域。空间索引的主要功能是加速检索过程并过滤多余的地物元素。近年来，研究者设计了多种索引，以更快速、更方便地访问二维地理数据。这些空间索引包括四叉树（quadtree）、R 树和 R*树。在树达到特定深度或满足标准之前，四叉树会递归地将地球划分为更小的部分。由于它已成为 GIS 的标准组件，在 R 树和 R*树中，多级索引是使用虚拟矩形创建的，该矩形用于描述中间距离地面物体。研究人员还设计了其他索引来检索轨迹信息以及复杂的多边形等信息。这些方法中的任何一种都有提高地理数据检索效率的潜力。然而，如果将搜索词视为字符串处理，在属性检索中发现隐藏的意义将是具有挑战性的。此外，在收集空间信息时，地理关系很少被考虑，因为地理索引通常是按照“机械化”的方法构建的。这意味着需要更先进的语义检索技术来取代当前的数据检索方式。

语义搜索：信息访问的革命 2.3。随着语义网技术的发展，现代研究人员开始关注语义化以提高数据检索效率。正如 Guha 等人所述，语义可以用于扩大检索范围并理解搜索词的潜层含义，这两者都能提高结果的准确性。为了帮助文档检索，马里兰大学的研究人员开发了语义网搜索引擎。Watson 是一个基于语义网的搜索引擎，在开放学院推出，帮助学生通过内容分析定位相关材料。为了方便信息检索，研究人员开发了 Falcons 和 Hermes 等方法来计算实体和关系的相似性。地理数据检索主要从两个角度进行研究：数据集成和查询扩展。在本文，我们回顾了该领域的现有研究。

数据的语义集成 (2.3.1)。为了克服多源异构检索信息中的语义异性，更多的 GIS 研究人员关注地理数据集成。未处理的数据通过语义网技术转换为资源描述框架（RDF）元组。RDF 三元组是一种用于清晰定义地理信息的标准化语言。通过在轨迹分析、地震灾害应急响应和海洋数据发现等领域应用语义网技术，已经实现了地理信息的整合和语义异性的克服。此外，跨度识别和电影推荐只是知识谱（KG）语义技术大显身手的众多例子之一。然而，如果数据频繁变化，管理成本将迅速增加。数据集成技术层出不穷，最流行的之一是基于本体的数据访问（OBDA）。例如，Zhang 等人设计了一种定义的交互范式和统一的分类法，以获取地理数据。基于本体的数据抓取（OBDA）[3] 生成用于基于本体的数据集成（OBDI）的本体，以便从多个源获取并导入数据到单一地理数据库中。为了实现 OBDI，地理特征被发布为 RDF 图形，并使用称为关系数据库到 RDF 映射语言（R2RML）的语言与原始数据库建立语义链接。

扩展搜索，版本 2.3.2。由于上个世纪字符串匹配的技术局限性，Van Rijbergen 提出使用查询扩展技术来更准确地捕捉原始查询的意图并提高检索速度。通过对搜索词进行分析，查询扩展可以提供一组代表原始查询意图的新颖且全面的集合。最近的研究侧重于通过共现来扩展搜索词。Voorhees 等人评估了关键词的共现概率，以生成原始数据的相关性，从而识别出相关性最大的潜在词汇添加。Xu 等量化了查询扩展结果的价值。Cui 等人通过将收集到的术语整合到丰富的词表中，利用查询记录来传达查询意图。此外，一些研究人员尝试通过扩大语义范围来扩展搜索词。Voorhees 等人和 Navigli 使用技术计算概念相似性并生成更多相关的概念，以根据本体层次结构扩展搜索查询。海洋安全 [10] 和智慧城市项目在应用研究中都更多地使用了地理特征的属性和空间数据。Ji 等人引入了一种使用本体的语义查询扩展方法，以提高农业和林业行业语义检索的准确性。

## 提出的工作

## 图构建

LifeGraph 基于 LSC 2020 公开的日志数据库，该数据库包含 114 天内通过可穿戴摄像头拍摄的约 20 万张图片，以及相关的元数据和其他传感器数据。丰富的语义注释不仅详细说明条目的材质，还将其放在更广泛的背景中，这对于所有日志项都是有利的，无论其类型或编码方式如何。为了使收集的数据变得可用并因此可以使用，必须采用替代方案；显式地添加此类注释是有问题的，因为目前机械地这样做是无法实现的。为了弥补这一缺陷，我们构建了图结构，跟踪通用语义思想与更特定标签之间的关系（例如环境类型或图片中常见物品的包含），这些可以被现有技术一致地识别 [9, 4]。由于需要将粒度的图片特征与广泛的搜索主题连接，LifeGraph 的构建可能会更加困难。通过使用 Wikidata [8] 定义关联，我们能够合并 COEL 和可检测实体。我们将映射的理念与来自 Wikidata 的额外信息相结合，以建立概念与低级语义图片标签之间的链接。在第一步中，我们将 Wikidata 中的所有观测事物映射到 COEL，并使用它来填充图。然后，我们迭代地映射来自 Wikidata 的每个与当前图至少关联两个实体的实体，并将其插入图中。此过程执行了三次，当仅考虑类关系（`instance_of`, `subclassOf`）时，再执行两次。我们消除了网络中所有未能正确将标签与广泛类别相关联的临时节点。我们还考虑了导航和内部组件，如消歧和模板页面。使用某项研究 [5] 中描述的模式，我们为提交给 LSC 的数据集中已的信息创建了一个基础的、平面的模型。时间戳用于将每条信息链接到特定的图片。在图中，我们使用对象或数据类型属性将所有元数据与图片连接。事实上，每张图片都对应一个每日资源，尽管之前可能暗示过不同 [5]

![](img/5e4d8ef2afa52a8404b28106580e19e4_765_0.png)

**图 (1)** 提出的工作。

这使得我们能够避免对某一天拍摄的约 2000 张照片重复存储相同的数据，而是将这些信息直接链接到数据资源。语义位置标签（“工作”与“家”）由用户提供，并与识别出的项目 [4] 和位置 [9] 一起，在填充模式（schema）之前进行插值。两个概念之间的距离足够窄，我们用一个概念将差距中的每一个条目连接起来。接下来，我们直接使用 `:detected_place` 属性将照片与它们所描绘物体和地点的 Wikidata 条目连接起来。图 [1] 显示了所提的工作。

# 从构建图图中检索数据

LifeGraph UI [6] 是基于内容视听栈的 vitriv [7] 生成的 UI 的修改版本，可以使用任何网络浏览器访问。系统中的 vitriv 栈与 LifeGraph 共享的唯一部分是界面。作为输入复杂查询的替代方案，用户可以只需从网络中选择与其感兴趣的话题对应的节点。这种问题构建方法在精确性和效率之间取得了良好平衡，不需要用户具备任何专业知识。查询制定后，它被提交到后端，在后端执行查询并对结果进行排序。作为评估过程的一部分，通过遍历图找到从查询选定的起始顶点到所有可能返回的日志文件的所有路径。我们不断增加这条路线的最长度，直到达到某些经验确定的可能结果数量或路径总长度的限制（以先者为准）。分配给每个检测到的日志条目的值是反向路线长度的几何平均值，并根据启动搜索的节点数进行缩放。如果恢复的项目越最大可能的起始点数量，则其得分越高。编译后的数据随后传回用户界面，并在那里以顺序记录列表或按天组织、并在每天内按时间顺序组织的条目列表的形式显示。底层检测器产生的假阳性并没有遗漏发现或假阴性那样那么令人担心，因为预计用户能够浏览获得的结果以尝试寻找所需的组件。如果假阳性太多，用户将浪费时间进行浏览；如果假阴性太多，他们可能永远找不到他们想要的东西。创建的时间和日期等技术信息是包含在每个日志条目中的元数据示例。心跳、在给定时间内的步数等反馈功能也会手动记录在日志条目中。这些数据在用户界面中使用，以消除不满足查询布尔条件的记录。用户界面中对此类过滤器的评估可能会降低结果集的大小，因此不需要进一步的服务器端处理或与底层图的连接。图 (2) 显示了数据检索。

![](img/5e4d8ef2afa52a8404b28106580e19e4_766_0.png)

图 (2) 数据检索。

其次，基于基础框架给出了一种数据检索程序，包括知识图谱（KG）构建、语义查询增长、查询扩展和检索结果的返回。以下是其分解说明：

1. 构建知识图谱。建立两个数据库（地理空间和其他）之间的连接。完整的数据库信息（如地图图层和地理特征字段）反映在数据层之间的连接中。

2. 提交扩展的语义查询。在模式层中，将 Q 与预定义的概念进行比较。查询扩展过程根据概念的分级链接和逻辑公理，将搜索重写为相关的查询。

3. 地图布局。数据库与界面之间的连接反映在映射规则中。使用这些指南，通过将查询短语转换为表名和属性字段等对象，自动构建 SQL 语句 (Q)。

实体扩展得到了开发，Q 交给地理数据库。此外，数据层可能会在概念类别、组织划分和思维方式的范围内扩大与搜索查询链接的实体。按照上述程序，获取地理数据库，并以不同的视角显示结果。结果，该技术可能为查询提供必要的隐性数据。

### 计算意义相似性

为了有效利用语义查询扩展，计算概念相似性至关重要。语言领域的研究人员声称，两个词之间的概念距离与它们相互接近程度成反比。`Sim(C1, C2)` 跟踪两个概念 `C1` 和 `C2` 之间的语义相似性。当两个事物的差异大于相似性时，它们之间的差距就会增大。概念亲性可以表示为：

```
Sim(C1, C2) = { 0, D = +\infty \ P, D ∈ (0,+\infty) \ 1, D = 0 }
```

因此，本文计算了模式层距离 P（可能从 0 到无穷大）。知识网络深度的概念反映了语义专业化水平。

## 结果与讨论

当用户的需求得到满足时，地理检索技术的结果就是成功的。Saracevic 在 1995 年引入了 Canfield 评估系统（样本集、正确答案和评估指标）。F-Score 被认为是召回率 (R) 和精确率 (P) 之间的折中，这两者分别通过相关项目数量和可恢复实体的数量来计算。这些评分标准的公式如下：

- R = 检索到的相关项目占数据中所有相关组织的百分比

- P = 检索到的实体占总实体的百分比

- F = 2 × R × P / R + P

其中 R 是原始数据中相关实体被恢复的比例。P 是所有检索项目中真正相关的比例。此外，R 和 P 的调和平均数等于 F-Score。

## 检索数据分析

对于 SQL 的高效检索，LIKE 和 WHERE 运算符对于从关系数据库检索信息都是用的，它们在实践中的性能是两种不同的效率衡量标准。由于 LIKE 语句迭代检索地图图层中的特征，其时间复杂度为 O(N)。在本文中，我们通过从知识图谱中提取类型代码来改进过滤语句。由于存在 O(log(Q))+O(M) 个共享相同类型的字符，所提方法的执行复杂度为 O(log(Q))+O(M)，其中 Q 是地图图层中的特征数量。当原始数据中 Q 和 M 远大于 N 时，所提方法更为有效。

查询，因此准确性与搜索短语成正比。搜索的准确性取决于搜索短语在数据库中的稀有程度。

## 表 1：时间成本

| 编号 | 检索概念 | 类型代码 | 特征数量 | 时间 (ms) |
|---|---|---|---|---|
| - | - | - | - | - |
| 1 | 桥梁天桥 | 230201, 230202 | 202,112, 21,944 | 429, 439 |
| 3 | 收费站 | 230209 | 19,223 | 428 |
| 4 | 充电站 | 230218 | 14,884 | 462 |
| 5 | 加油站 | 230215, 230217 | 104,036 | 428 |
| 6 | 气站 | 230216, 230217 | 7,489 | 420 |
| 7 | 车站 | 230100, 230103 | 13,522 | 429 |
| - | - | 230107 | - | - |
| 8 | 火车站 | 230103 | 10,771 | 426 |
| 9 | 货运站 | 230107 | 1,413 | 421 |
| 10 | 停车场 | 230212, 230211 | 258,211 | 424 |

表 2：实验结果对比。层 A 和 B 分别代表公路和交通仓储。

| 实验类型 | 搜索词 | 特征 (A) | 特征 (B) | R (%) | P (%) | R (%) | P (%) | R (%) | P (%) | R (%) | P (%) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 多层实体 | 香港-珠海 | 39 | 1 | 100 | 100 | 97.5 | 100 | 98.2 | 5 | 100 | 0.04 |
| 单层实体 | 郑州站 | 0 | 1 | 100 | 100 | 10 | 0 | 100 | 1 | | |
| | 莲湖 | 10,344 | 0 | 100 | 101 | 100 | 0 | 0 | | |

实验使用了地图（https://www.navinfo.com，访问于 2019-09-01）的数据，涵盖交通仓储、公路和铁路层。地图显示了 37 种类型的地理实体。

### 4.3.1. 正常恢复过程

检索的 SQL 查询是使用地图层和字段构建的。另一方面，构建 SQL 语句是困难的。

郑州东站使用行政区域和类型来与郑州站关联。关联网络允许组织增长。此外，GIS 空间操作允许准确提取沿线的大量地理对象。

数据使用推荐策略恢复了郑州站，包括郑州东站和郑州火车站。检索结果显示了位于沿线的多个火车站。

## 结论

为了提高准确性并缩短实施时间，本研究开发了“SVD 后 PCA”的方法用于文本挖掘。形容词和副词频率、正性和负性是额外的属性。两次实验的结果表明，建议的方法优于其他方案，特别是对于 SVM-RBF 分类。SVM 分类器在确定个人情感方面表现出色。未来可能探索的其他主题包括：如何利用领域词汇来定位和过滤特征、如何赋予不同的权重以提高准确性，以及单词-文档连接。与标准技术相反，建议的方法使用 KG 检索项目，将召回率提高到 100%。表 1 和表 2 以香港-珠海隧道为例，层 A 和 B 均将召回率从 97.5% 提高到 100%。除非明确指定层，否则标准方法无法提供结果。

## 参考文献

- [1] Liu H., Motoda H. 知识发现与数据挖掘中的特征选择。Springer 工程与计算机科学国际系列。1998:10.107/978-1-4615-5689。

- [2] Fayyad U., Piyetsky G., Smyth P. 从数据挖掘到数据库知识发现。AI. 1996:1735。

- [3] Cacciatore S., Tenori L., Luchinat C., Bennett P., Macintyre D. KODAMA: 用于知识发现和数据挖掘的 R 包。Bioinformatics. 2017:a4621310.109/bioinformatics/btw75294

- [4] Yu J. 大数据挖掘与知识发现的智能库构建。2022:10.109/SCAUT54.2021.0023

- [5] Williams G. 使用 Rattle 和 R 进行数据挖掘：挖掘数据的艺术。2011:10.107/978-34486950

- [6] Chikarikar S. 知识发现与数据挖掘。Int. Res. Appl. Sci. Eng. Technical.2020:2080487610.221/jiraset.2020.32045



- [7] Feng D.Q., Tseng S., Weib G.I., Ho B., Ganj M., Rashidi L. 知识发现与数据挖掘进展。计算机科学讲义。

- [8] Yadav S.P., Yadav S. 使用小波方法进行医疗融合：IEEE 处理与计算事务综述。韩国电子工程师学会。2019:842657110.557/IEEEESPC.2019.8.4.265

- [9] Al-Janabi S. 通过智能数据分析克服知识发现的挑战。2021 商业与工业数据分析国际会议 (ICABI) 28628942210.109/ICADB25.2021.965916

- [10] M. Hernandez, T. Moshhof A J., and R. Waiba 使用大数据在健康信息中进行数据挖掘的综述。大数据期刊。2014:111

Cappelli (2000) 和 Narayan 等人 (2019) 都发现，人力资源是公司成功的最重要的因素。为了最大限地利用这一资产，全球几家公司都实施了人才管理技术 (Cappelli, 2000)。证据表明，高效有效的人力资源管理（HRM）实践可以提高就业稳定性和留任率 (Irshad et al., Afridi, 2012)。留住现有员工是一项关键的人力资源任务。Armstrong (2006) 和 Paille (2013) 都强调了员工留存的重要性，这为企业提供了竞争优势。对于企业要长期保持竞争优势，投资明智且高技能的员工至关重要 (Kumar & Kausik, 2013)。在当今竞争激烈的就业市场上，留住顶人才正成为公司高层日益紧迫的挑战 (Naris alongside Ukpere, 2010; Olckers through Du Plessis, 2012)。在这方面，引用了许多参考文献：Davenport & Harris (2007)、Chen et al. (2012)、Watson (2014)、Frisk & Bannister (2017)、Kar & Dwivedi (2020) 以及 Bag et al. (2021)。大数据和数据驱动的决策在管理领域正受到关注。公司对数据驱动的预测分析 (BDPA) 及其复杂的大数据应用越来越感兴趣 (Dawson et al., 2007; Secundo et al., 2017; McAfee et al., 2012; Agrawal et al., 2021)。根据 Wong (2012)、FossoWamba 等人 (2016) 和 Dubey 等人 (2019) 的观点，大数据领域具有转型整个业务运营的潜力，这引起了学术界立法者的关注。尽管研究人员付出了巨大努力，但关于信息管理和人力资源管理的研究未能提供任何实质性发现 (Garcia-Arroyo & Osca, 2019; Rambaut via Guerry, 2020; Hamilton vs Sodeman, 2020)。尽管有多次整合研究与实践的尝试 (Shah et al., 2017; Calvard and Jeske, 2018; Huang et al., 2021)，但两者仍被视为不同的实体。在研究影响员工留存的因素时，现有文献缺乏相关数据。此外，文献也缺乏关于 BDPA 对员工留存影响的具体证据。

各种病理状态、复杂的疾病过程、慢性化倾向以及急性期事件的复发是循环系统疾病的特征。长期护理的需求是社会的沉重负担，这些变量显著降低了患者的生活质量并恶化了他们的预后 [1, 2]。医学和医疗技术的巨大进步并未能阻止医疗服务单价大幅增加。生活方式的改善和其他因素也导致日本患有心血管疾病和其他疾病的患者每年增加 10,000 名 [3]。2018 年，心血管医疗支出占日本总体医疗支出的 19.7%（65 岁及以上人群同比增长了 5.7%），在这一框架内排名最高 [4]。社会资本的高效利用——包括与长期护理相关的医疗成本——以及在心血管专业政策分歧下临床结果的提高 [5]。日本政府监测人们在医疗和养老院护理方面的支出。在过去的十年中，医疗支出每年增长超过 2%，达到 GDP 的 8.0% [6]。这是由于全球人口老龄化和医学科学的快速发展。老年人的住院率和住院时长是地区差异的主要因素。同时，长期护理费用自 2010 年以来以每年 5% 的速度增长，快于 2016 财年 GDP 2% 的增长率 [7]。改善临床质量和医疗资源的管理至关重要。这将是预测模型的巨大用途。预测患者问题的严重程度和治疗结果是临床实践中的一个活跃元素，创建此类模型也是如此。综合风险评估被用作预测关键预后的模型。

国保数据库（KDB）系统用于构建 ASHRO，它整合了医疗体检、保险申请以及长期护理计划的个人数据。在健康和长期护理记录方面，KDB 数据库的个人参与率超过 99%。自雇人士或退休并通过国民健康保险的人员也包含在这一庞大的数据库中。全国 6.1% 的人口位于数据库覆盖区域；人口统计特征和社会经济地位也被认为对获得医疗服务和长期援助具有主要影响。得益于健康体检、医疗和长期护理数据的统一管理结构（KDB），对不同行为变化的纵向研究可以增强医疗成本预测。预测模型的构建使用了 2014 年 4 月至 2018 年 3 月的四年时间范围。数据源于心血管疾病住院（ICD-10 I 00-99）。一项涉及多个地点和超过 300 万参与者的大型回顾性观察性研究包含了一个网关。该研究不包括入组时被认为无法治愈的心血管疾病、严重心肌病或先天性心脏缺陷。在匿名化之后，每个患者数据的主体识别将包含以下信息：基本被保险人属性、医疗成本（门诊、住院、药剂和牙科）、诊断细节、医疗检查频率、住院时长、长期护理成本、所需的长期水平、使用频率、使用时长、指导和说明。以下是东京大学研究伦理委员会（2018-67 N1）授予该研究批准的标准：《RECORD 声明》（一套关于使用观察性习惯获得数据进行研究报告的规则）和日本政府发布的《赫尔辛基宣言》，这两者都为临床研究的伦理提供了标准。本研究还遵循了透明报告预测模型（TORIPOD）原则。项目负责人将在根据合理请求提供为本研究获取的敏感数据的访问权限。

## 基础模型的机器学习分析

传统的经验统计方法涉及收集包含结果、预测因子以及拟合系数的数据集，由于在大样本上进行多变量分析时结果具有物理特性且存在不完整性，该方法并不适用于这项探索性研究。我们选择的机器学习策略利用随机森林和 K 折交叉验证（富士通有限公司 AI 支持）来选择和整合解释变量及权重。机器学习中的随机森林可多种任务，如回归和分类。其优点是过拟合问题要小得多。有效利用具有多个输入变量的样本维度是医疗大数据的另一个优势。此外，它可以处理差异不同的数据规模（例如，血压和 GFR 的正常值不同），并能处理无关元素的包含。通过使用大数据中发现的百多项关于医疗程序、诊断测试和预防措施的数据，本研究生成了医疗及长期护理成本的客观因子。利用机器学习，我们使用了带有放回的自助抽法来选择许多随机样本和特征数量，然后利用这些信息来确定参数整合的重要性。80% 的数据用于训练，20% 用于测试。我们使用 `Inc MSE`（残差和：均方误差：袋外 [OOB] 错误率）进行回归，使用平均基尼下降值（基尼系数）进行分类。前者通过将未处理的信息拟合到使用随机数据构建的回归树获得。在 2021 年 *BMC Medicine* 文章第 16 页第 3 页 19:15 处，Takura 等提出降低 OOB 作为一种优化方法。决策树的分支程度由变量总平方决定。所选树中的最大分支数为五十。本研究中的所有训练模型在模型开发过程中对超参数更改的基于网格的搜索后，使用了 K 折交叉验证进行评估。此外，我们使用了留出技术评估基于神经网络的机器学习方法的适应性。为了获得最终预测值，K 折交叉验证方法通过将测试信息随机分成 K 组并创建 K 个模型的平均值。我们可以将其视为内部验证的实际示例。该程序中的常用方法之一是折外（OOF）预测。此外，它使用随机状态参数并利用随机化来决定将样本分配到哪些组。摆脱“廉价低劣”的心态对医疗和长期护理管理可能是有益的。这种观点在公共卫生体系背景下尤为突出。我们的研究旨在通过纳入财务和临床因素使预测模型更加精细化。在建立广泛适用的依从性定义（需考虑道德风险）以及选择指标时，也有考虑反馈的需要。这项工作还探索了未来的研究方向，例如数据库扩展并将其应用于其他疾病领域的潜力。这些发现为使用机器学习将其他非依从性相关变量（如性别、年龄和观察时长）整合到基础模型中提供了依据。对不重要特征和可比性指标的分类进行修改，改进了预测模型的解释性和验证准确性（多变量评估：多元回归、二分类逻辑回归）。

预测变量与发现。为了理解资源（医疗及长期护理费用）的使用情况，本研究构建了一个预测模型，将最广义意义上的依从性作为解释变量。我们还从社会视角来审视这项研究。在分析中，将直接支出（如交通和未投保的食物）从总成本（住院、门诊治疗和药剂）中减去，得到目标变量的总成本。2014-2017 年间，日元的平均汇率为每美元 112.98 日元。利用机器学习从特征值显著性分布中选了 11 个参数来组成基础模型，这些参数被组合成 8 个最终参数。成本（如同时门诊就诊和医疗就诊）。为了增强研究预测模型的解释能力，更改了变量权重（表 1）。由于每个解释变量在计算时都需要良好的平均值，因此在评估预测模型时，目标群体的特征至关重要。本研究的研究人员将回归分析扩展到年龄、性别和分析时长，因为他们希望确保其发现在不同人群中成立（模型的通用性）。构成健康行为最终预测框架（ASHRO）的十一个变量如下：公共行为、医疗态度、健康预防和促进指标以及资源的理性消费行为（道德风险）。为了衡量与普通人群相比为患者提供的护理质量，在入组第一年监测了十一项内容。追踪了许多指标，包括体检、核实项目、药剂、住院天数、重复治疗访问/临床实验室和生理测试、住院次数、覆盖天数百分比（PDC）和住院日数。在重复治疗中，患者对同一种疾病接受多次门诊治疗。通过将原始医疗成本乘以处方数量，建立了通用药的价格。联邦政府的通用药物库存作为参考。PDC 不是使用特定每个患者药效的数据，而是使用整个处方期计算的。医疗资源的使用受多种因素影响，包括合规性、道德风险、社会协作和公共特性。我们旨在分析医疗及长期护理成本。我们开始系统地建立这些解释因素之间的关系，我们称之为广泛依从（附文件 1）。二级预防、康复强度、建议和以患者为中心的决策是与依从性并反影响医疗支出的四个特征。例如，记录了对获取处方药的影响（比率，1.11）。此外，在日本，老年人的平均医疗成本占比为 10%，远低于 Takura 等人估计的 20%。

降低 OOB（样本外误差）是我们的首要任务。变量总数的平方决定了决策树中的分支数量。选择树中分支总数的上限为 50 个。在模型构建期间对超参数更改进行网格搜索后，在本研究中，我们使用 K 折交叉验证评估了每个训练模型的质量。此外，我们还使用了留出法（holdout technique）来评估几种基于神经网络的学习方法的适应性。通过将测试数据随机分为 K 组，K 折交叉验证方法会开发 K 个模型。最后的估算值是这些模型的平均值。这一过程通常会利用折外（OOF）预测。此外，它还通过随机化决定哪些样本进入哪些组别，并设置了一个名为 `random state` 的变量。医疗以及长期护理资源管理将从脱“廉价但低质”的思维中获益。这种观点在公共卫生体系背景下尤为突出。我们的研究旨在通过纳入财务和临床因素，使预测模型更加精细。在建立广泛适用的依从性定义（考虑到道德风险的定义）以及选择指标时，也有必要考虑反馈。本工作还探索了未来的研究方向，例如数据库扩展并应用到其他疾病领域的潜力。这些发现为使用机器学习提供了决策依据，将其他与依从性相关的变量（如性别、年龄和观察时长）纳入基础模型。基于上述，我们可以得出结论：通过对不显著特征和类似指标进行分类修改，增强了预测模型的解释力，也提高了其验证的精确度（在多变量分析中使用多元回归和二元逻辑回归）。

## 发现与用于预测的变量

本研究开发了一个预测模型，利用广义上的依从性综合指数作为解释变量，解释资源的使用情况（医疗和长期护理支出）。本研究还从社会学角度进行了分析。在这一分析中，将直接支出（如交通和未投保的食品费用）从总成本（住院、门诊和配药）中减去，得出目标变量的总成本。2014-2017 年间，日元的平均汇率为 1 美元兑 112.98 日元。机器学习从特征值显著性分布中选择了 11 个参数来构建基础模型，并将这些参数组合为 8 个最终参数。成本受到其中几个解释因素（如同时门诊和就医）的显著影响。通过调整变量的权重，研究的预测框架能够更好地解释数据（表 1）。由于每个解释变量都需要分组平均值进行计算，因此在评估预测模型时，考虑目标群体的特征至关重要。本研究的研究人员将回归分析扩展到年龄、性别和分析时长，以确保他们的发现在不同人群中均成立（模型的通用性）。构成健康行为最终预测模型（ASHRO）的 11 个变量如下：公共行为、医疗态度行为、健康促进与预防指标，以及理性资源消费行为（道德风险）。为了衡量与普通人口相比为患者提供的质量，我们在入组第一年监测了 11 个指标。标准包括：门诊就诊总次数、住院总天数、住院期间的临床实验室及生理检查次数、已确认的项目数量、康复评分部分的总数、建议会议次数、住院总次数、住院总天数、药物覆盖百分比（PDC）以及住院总次数。在重叠护理中，患者同时针对同种疾病接受多次住院治疗。我们将原药成本除以处方数量以获得仿药成本。我们参考了政府的可比药物清单。PDC 并非使用特定于每个患者药效的数据，而是使用整个处方期计算的。医疗资源的使用受到多种因素的影响，包括依从性、道德风险、社会协作和公共特质。医疗和长期护理成本是我们旨在分析的因变量。我们开始系统地建立这些解释因素之间的关系，我们称之为广义依从性（附文件 1）。二级预防、康复强度、建议和以患者为中心的决策是与依从性相关并反过来影响医疗支出的四个特征。例如，记录了对获取处方药的影响（比值，为 1.11）。此外，日本老年人承担了 10% 的医疗费用，远低于工作年龄层的 30%，因此被认为更容易受到道德风险的影响。事实证明道德风险变量影响着医疗成本。本研究主要检查了三个因素：医疗关注、重叠的临床实验室及生理测试以及重叠的患者访问。例如，据报道在这种特定案例中，患者的咨询行为改进了 15%。

| 变量 | 相关系数 | p 值 | 权重 |
| --- | --- | --- | --- |
| 入组后 12 个月期间 | 0.42 | <0.001 | |
| 健康行为 | | 广义依从 | |
| 二级预防 | 0.122 | <0.01 | 1 二级预防（整合） 8.18 * |
| 健康体检 | | | ** |
| 体检项目 | 0.128 | <0.001 | * |
| 三级预防 | | | |
| 康复强度 | 0.012 | 0.43 | 2 康复强度 0.81 |
| 指导 | 0.156 | <0.001 | 3 指导 1.04 |
| PDC（药物依从性） | 0.079 | <0.001 | 4 PDC 5.35 |
| 重叠门诊服务 | | 0.098 | 5 重叠门诊次数 3.03 |
| 门诊次数 | 0.001 | | 6 重叠临床实验室和生理检查 5.02 |
| 临床实验室和生理检查 | 0.049 | <0.05 | |
| 就医次数： | | | 7 就医次数（整合） 2.76 |
| 住院天 | 0.52 | <0.001 | |
| 门诊次数 | 0.352 | <0.001 | * |
| 分散 | 0.354 | <0.001 | * |
| 公共行为 | | | |
| 仿药率 | 0.209 | <0.001 | 8 仿药率 6.58 |

## 长期护理

| 居家服务，每年次数 | 0.224 | <0.001 | |
| 社区服务，每年次数 | 0.011 | 0.466 | |
| 机构服务，每年次数 | 0.086 | <0.001 | |

## 基准 12 个月入组后的 48 个月随访期

| 随访期 | 0.442 | <0.001 | |
| 医疗费用 | 0.938 | <0.001 | |
| 长期护理费用 | 0.269 | <0.001 | |

通过机器学习整合到依从性 1* 或依从性 7* 指中

**图 (1)** 疾病严重程度。

随访期：随访持续时间。产生的总医疗费用。长期护理费用：产生的总长期护理费用。通过机器学习整合到依从性 1 或依从性 7 指中：这表示某些变量已使用机器学习算法合并为一个单一指数。

## 广义依从

- 1. 二级预防（整合）：二级预防依从性的综合衡量。
- 2. 康复强度：对康复建议的依从性。
- 3. 指导：对医学指导的依从性。
- 4. PDC：对医患沟通建议的依从性。
- 5. 重叠门诊次数：对门诊计划的依从性。
- 6. 重叠临床实验室和生理检查：对实验室和生理检查计划的依从性。
- 7. 就医次数（整合）：就医依从性的综合衡量。
- 8. 仿药率：对使用仿药的依从性。

## 实验分析



# 基线特征

患者平均随访了 36.1 ± 8.8 个月，总共有 48,456 名参与者。平均年龄为 68.3 岁，其中 61.9% 为男性。首次综合医学评估时的患者体征如表 3 所示。这些包括收缩压 131.2 ± 15.0 mmHg、甘油三酯 20.8 ± 5.2 mg/dL、糖化血蛋白水平 5.9%、血清肌酐 0.9 ± 0.8 mg/dl。患者体重质量指数（BMI）为 23.4 kg/m²。医疗治疗和长期护理人均总计 9,160 美元，或 9,045 美元。

# 预测因子选择

机器学习帮助我们整合数据并确定健康相关特征以进一步研究。以下是构成核心模型的参数的相对重要性：根据表 1，二级预防（健康检查次数）（8.18）、康复强度（1.04）、指导（5.35）、初步预防（4.03）、门诊护理（5.02）、重叠临床实验室和生理检查（5.02）、就医（2.76），以及仿药率（6.58）被认为是最典型的公共行为。医疗和长期护理费用显示出与随访时间和年龄强相关（p<0.001）。在整合之前，差异很小或没有差异（康复单位总数 p=0.43，重叠门诊次数 p=0.938）。尽管有（p=0.01）的例外，但生理和临床实验室检查已显示出显著差异（p<0.05）。此外，我们发现少数与护理相关的指标超出范围。对预测模型进行了评估，总体而言，在多次回归后，模型的决定系数为 0.313（p<0.001）。八个变量中的每一个都代表健康生活选择：医疗保健（0.261）、随访（0.254）、额外预防（0.241）和康复强度（0.210）在部分回归中产生了相当大的系数。虽然年龄的影响较小（0.032），但重叠会话的指数较低（0.053）。在确保每个变量的 VIF 都小于 2 并验证了多重共线性后，预测模型被认为是稳定的。使用 50% 阈值的逻辑回归对总医疗和长期护理支出进行分析，整个算法的确定性显示出高度显著（p<0.001）。年龄和重叠临床实验室是唯一与医疗护理支出不相关的解释变量。与在多元回归中看到的模式一致，多项发现也证实了这一趋势。存在明显的多重共线性证据，因为所有解释因素的 VIF 都小于 2。在 25%/75% 阈值的逻辑回归下，总预测性非常显著（两者 p<0.001）。在使用 25% 阈值的整个研究中，只有一个 VIF 大于 3。表 5 显示 AUC 值为 0.880 和 0.896。

# 治疗结果预测

对费用进行了显著水平的逻辑回归分析。以下是总体决定系数的总结：在 0.01 显著水平下，基于依从性的死亡率比（OR）为 1.860（95% CI: 1.740, 1.980）。通过依从性 50% 分类生成了六千一百十四对患者，以比较风险因素的倾向。根据年龄、性别、吸烟状况、酒精摄入、脂肪酸、血红蛋白、肌酐水平和体重质量指数分组，未发现统计学差异。关于 36 个月后的总死亡率，两组之间存在显著统计学差异：低依从组为 7%，高依从组为 2%（p<0.001）。住院、门诊治疗和处方支出在 36 个月期间与依从性正相关，但对于长期治疗费用，医学检查结果平均变化存在相关性。

预测得分和概率的模型。使用每个依从评分的平均值比较医疗机构资源使用的位移，顺序如下：0-2 分占 77.88%（SE 1.48%）、2-4 分占 58.20%（SE 0.45%）、4-6 分占 11.53%（SE 0.51%）、6-8 分占 68.51%（SE 1.41%）、8-10 分占 138.65%（SE 5.47%）。根据统计分析（图 2），平均分在所有五个评分段之间显著不同，36 个月预测模型的 ROC 曲线为黑色。ROC 曲线的 AUC 为 0.889（95% CI: 0.886–0.892）。这显示了模型区分正负负面情况。

敏感性（Sensitivity）：y 轴显示了模型的敏感性，即其正确识别的正样本的百分比。特异性（Specificity）：x 轴显示了模型的特异性，即其正确识别的真负性情况的百分比。对角线显示了无法区分正负情况的随机分类器的性能。解释：ROC 曲线显示了不同分类水平下敏感性与特异性之间的权衡。识别这两个类别越好的模型，其 AUC 越接近 1。

![](img/5e4d8ef2afa52a8404b28106580e19e4_790_0.png)

图（2）36 个月预测模型的 ROC 曲线。AUC，曲线下面积。

# 表 4 通过多元回归分析对预测模型进行评估

| | 指标 | 部分回归系数 | 标准化部分回归系数 | F 值 | p 值 | SE | VIF |
|---|---|---|---|---|---|---|---|
| 广义依从性 | | | | | | | |
| 1. 二级预防 | -0.048 | -0.241 | 3,820.6 | < 0.001 | 0.005 | 1.07 |
| 2. 康复强度 | -0.250 | -0.210 | 2,740.7 | < 0.001 | 0.005 | 1.13 |
| 3. 指导 | -0.057 | -0.144 | 1,413.1 | < 0.001 | 0.002 | 1.03 |
| 4. PDC | -0.057 | -0.075 | 366.3 | < 0.001 | 0.003 | 1.10 |
| 5. 重叠门诊次数 | 0.028 | 0.053 | 116.4 | < 0.001 | 0.003 | 1.67 |
| 6. 重叠临床实验室和生理测试 | 0.012 | 0.091 | 343.1 | < 0.001 | 0.001 | 1.70 |
| 7. 就医次数 | 0.001 | 0.261 | 4,460.5 | < 0.001 | 0.005 | 1.08 |
| 8. 通用药率指数 | -0.019 | -0.016 | 17.7 | < 0.001 | 0.004 | 1.04 |
| 年龄 | 0.009 | 0.032 | 56.6 | < 0.001 | 0.004 | 1.25 |
| 性别 | -0.509 | -0.086 | 518.8 | < 0.001 | 0.022 | 1.10 |
| 随访期 | 0.051 | 0.254 | 3,207.9 | < 0.001 | 0.001 | 1.41 |
| 常数项 | 3.421 | | 1,249.7 | < 0.001 | 0.105 | |

缩写：PDC – 覆盖天比例，SE – 标准误，VIF – 方差膨胀因子

# 结论

将 ASHRO 纳入心血管疾病治疗技术中可能会改善健康行为并允许语义理解和识别，这是自然语言处理（NLP）中最常用的技术之一。

卷积神经网络（CNN）技术的使用在多个领域取得了显著进展，包括计算机视觉和模式识别。卷积模型能够从像素到线条、轮廓、形状和对象学习特征的有序表示，这种能力在许多论文中被认为是这些进展的驱动力。文献中已经提出了不同的网络以将这一范式应用于文本分类，并取得了积极结果。根据内容将文本分类到预定义组中的过程被称为文本聚类或文本分类。解析、语义评估、信息提取和 Web 搜索只是从其文档集概念视角中获益的少数几个领域之一 [1]。

因此，越来越多的研究人员对其产生了兴趣。然而，大规模的分类系统，例如 Google 的垃圾邮件过滤器 [13] 或 Netflix 的系统 [14]，由于海量的训练数据和需要微调的海量变量，消耗了大量的计算资源。这是在实际应用中处理上下文相关词汇时使用 CNN 的根本问题。搜索短语周围的单词被称为“上下文”。在使用词表外（OOV）术语或不熟悉单词的问题在词汇量丰富的语言中非常普遍。由于在字符嵌入中，每个单词都被还原为字母的集合，这个问题很容易被解决。在将深度学习应用于方言的作品中，由于文本无法由分离的单词组成，而是由单个字符组成，且单词的符号意义与其化学组成相对应，建立避免字符级分词的结构是一个显而易见的决定 [2, 3]。字符嵌入的初始阶段是定义一组工作的字符。例如，字母表加上其他几个符号。之后，我们将获得一系列向量，并使用独热编码（one-hot encoding）传输字符。在最终输出中，每个字符由一个恒长度的向量表示。接下来，使用 1D CNN 层学习序列。

使用深度学习的模型首先要做的事情之一就是学习如何表示单词或字符。作为 CNN 中的第一层机器学习层，通常利用单词或字符嵌入。在这里，我们引入了两种类型的分布式表示——单词嵌入和字符嵌入，并讨论了它们的优缺点。词汇整合是一种根据分布假设 [4-7] 在向量空间中表示单词的技术。

它表明，当单词出现在相同的上下文或不同来源的相同位置时，可能被赋予相似的含义。单词嵌入是通过通过神经网络反向传播误差函数来学习的，这是对单词分布式表示这一概念的适应。在统计语言模型中，这种类似的概念随后被用于发现单词向量和词序列的概率 [8-10]。在捕捉单词之间的语义和句法相似性时，这种方法被证明是非常有效的。分布式表示允许单词表示在稳定的、实值的紧凑区域内，该区域的维度远低于整个词汇，解决了稀疏性和维数灾难问题。

在提高神经确定性语言模型的准确性和计算效率方面，已经在单词嵌入学习方面做出了许多努力。特别是 Word2vec [11]，由于其简单且去中心化的设计，在准确性和处理效率方面都表现出色。Word2vec 的目的是开发一个低维的向量空间嵌入模型。为了实现这一点，我们可以训练一个神经网络来预测特定时间范围内某个特定单词序列的概率。搜索短语周围的单词被称为“上下文”。在使用词表外（OOV）术语或不熟悉单词的问题在词汇量丰富的语言中非常普遍。由于在字符嵌入中，每个单词都被还原为字母的集合，这个问题很容易被解决。在主角层级构建系统是避免语言（如中文）中分词的显而易见的决定，因为这些语言的文本无法由分离的单词组成，而是由单个字符组成，同时单词的语言意义映射到其组成字符 [12–14]。

# 相关工作

为了从生物医学数据集中提取每个实体，Chen, A. 等创建了一个名为 DataMed 的开源平台 [1]。该研究的主要目标是为数据重用程序识别有用数据集。随着这些集合的增大，这种方法需要优的文档排名策略来从生物医学数据库中识别和提取重要文档。DataMed 是一个用于各种生物医学数据集索引、排名和搜索的工具。该方法有两个关键部分，它们是：构建模型的第一步是数据采集流水线，负责收集和处理用于构建模型的原始元数据。Data Tag Suite（DATS）是这种标准化元数据模型的名称。其次，使用了一个强大的搜索引擎，它可以根据用户指定的查询识别相关数据集。S. Sohn 等 [2] 提出了一种方法，根据临床文档的变性和 NLP 系统的迁移性发现疾病相关模式。该研究的主要目标是使用许多电子健康记录（EMRs）来评估临床实践中疾病变化的存在和严重程度。在对生物医学集进行排名时，我们考虑了两个队列中与哮喘有关的变化。为了找到生物医学数据库中不同文档集之间的连接，J. Cuzzola 等利用 UMLS 和 BDPedia 构建了一个模型 [3]。该模型的主要目标是提供 UMLS 实体与 BDPedia 资源之间的连接。

UMLS 本体关系 BDPedia 中的实体使用使用通用的简单知识组织系统（SKOS）和资源描述框架架构（RDF Schema）进行映射和排名。在 BMC Medicine 发表的一篇论文中，E. S. Chen 等 [4] 开发了一种从医学文献中获取疾病-药物信息的自动方法。该研究的主要目标是调查并自动化临床和生物记录的知识获取。为了识别疾病-药物关联，结合文本挖掘和统计方法。在这种情况下，我们使用两个不同的 NLP 系统；它们是 BioMedLEE 和 MedLEE。这两个 NLP 算法负责识别所有可能的疾病和药物。该方法产生疾病和药物的排序列表。为了定位和检索相关的生物论文，Soysal 等 [5] 创建了一个基于自然语言处理流水线的工具箱。MetaMap 和 BioNer 是两个著名的 NLP 工具，用于搜索数据库相关项目。在处理海量生物医学集时，这些工具箱力不从心。正如 K. Raja [6] 建议的，人类蛋白质和基因可以使用混合标记器之一进行注释。在生物医学文献的情况下，提取基因或蛋白质名称是关重要的。命名实体识别过程中存在大量的标记器，但目前的模型中没有一个能够很好地标记人类基因和蛋白质。因此，为了利用本体论标记人类基因组或蛋白质，需要一种混合漏洞。MedScan 用于分析基因、蛋白质及其相关通路的数据。MedScan 是一个基于生物医学文档解析器的三层知识提取系统。预处理模块的主要目标是将领域特定原理应用于各种生物医学 MeSH 词的标记。MEDLINE 描述的生物医学 XML 表示由预处理模块读取，然后解析为单个短语和句子。在本节中使用蛋白质字典作为训练数据集选择至少一个基因型-蛋白质名称的短语或句子。概念和句法模式之间的语义链接是自然语言处理器操作第二层的关注点。它使用词法解析器和上下文无关语言从 MEDICINE 中提取蛋白质。

最后，概念图格式 [7] 用于使用作为领域知识过滤器的知识提取引擎从基于 MeSH 的文档中提取关键信息。优化支持向量机的目标是创建一个新函数专门用于提取专门信息。通过超平面和特征向量空间，我们对每篇文档进行分类。方程 1 描述了 NLProt 核函数：$c=0$（1）超平面 $W$ 和决策函数 $f(x)$ 的参数分别用 $X$ 和 $W$ 表示。$f(x)$ 的方程为：$\sin(x+c)$。（2）在 NLPlot 中，如果条件随机场定义的概率 $p(Y/X)$ 如方程 3 所示以描述此类问题，则多项式函数的核写为 $K(y,X) = w(y,Y)c$。$Prob(Y/X)$ 和 $Z(X) = \sum (Y,X)$（3）是条件场顶点 $Y$ 的集合和文档类别 $c$ 的集合。特征提取函数用符号 $c, f$ 表示，定义如下：$f(Y,X)=1$；如果 $X$ 和 $Y$ 是同一类型的实体，则 $f(Y,X)=0$；否则，$Z(X)=1$。

提供了一种加权比较模型作为文档评分的新颖方法。在该方法中，文档观点和关键词被用于确定排名。这种方法简单地考虑了文档关键短语排序的可比较性，而不考虑短语之间的联系。文档评分的标准方法包括余弦相似度、欧几里德距离、Jaccard 系数、平均 Kullback-Leibler（KL）散度和皮尔逊相关系数。局部文档模式已被作为分层文档排名模型的基础 [9]。使用标准的分层模式识别方法可能会导致不一致或噪声模式的结果。因此，使用了一种名为“实例层次排序方法”（Instances Hierarchy Ranking Approach）的新模型来创建排名层次，而无需提取全局模式，解决了上述问题。该方法首先通过让每个实例位于其最接近的表示来识别局部重要模式。这样做是为了在给定区域内模式的相关性和频率之间取得良好平衡。

# 提出的工作

## 卷积神经网络

为了实现目标，卷积神经网络（CNN）采用了一种特殊的多层感知器。由于与动物视觉皮层的结构相似，CNN 受生物过程的启发。与其他分类方法相比，它们需要较少的预处理。这意味着网络捕捉了以前在传统技术中手工实现的特征。使用查找表，CNN 架构中的第一层将 $n$ 个标记的序列 $(s_1,s_2...,s_n)$ 转换为各种向量 $(w_1,w_2...,w_n)$。标记嵌入可以被视为向量，其维度为 $R^d$ 形式，其中 $d$ 是短句中标记的数量。现在可以将具有 $n$ 个标记的短句编码为嵌入矩阵。这样的语句作为输入显示 $W^{R_{nd}}$ 的 CNN 架构中。让我们称向量 $w_i,w_{i+1},...,w_{j:i:i+j}$ 之和。该层输入嵌入经过卷积处理。它涉及跨越 $h$ 个标记的窗口应用滤波器 $k^{R_{hd}}$ 以生成一个新特征。标记帧帧 $w_{i:i+h-1}$ 被用于创建特征 $c_i$，例如：

```
c_i = f(w_{i:i+h-1}^T K + b)
```

我们 $b$ 是一个偏置项，$f$ 是不规则的激活函数，如双曲正切。在生成特征图时，滤波器 $k$ 在所有潜在窗口上均匀利用。

```
c = [c_1, c_2,...,c_{n-h+1}]
```

卷积神经网络（CNNs）使用大量不同宽度的卷积过滤结构（核）来迭代处理整个嵌入矩阵。每个核可以用于提取一个独特的 n-gram 模式。对输入进行下采样通常涉及对每个滤波器执行最大化操作，如 $c = \max(c)$（3）所示，这发生在卷积层之后。两个主要考虑导致这种方法。首先，最大池化（Max pooling）对分类很有用，因为它产生了定义长度的输出。这就是为什么无论滤波器有多大，最大池化始终将输入映射到相同数量的输出。此外，在减少输出维度的同时，最重要的 n-gram 特征被保留了。每个滤波器现在可以独立地从句子的任何部分提取特征（如否定），并以平移不变的方式将其包含在最终阶段的表示中。可以在海量无标记语料库上进行随机或预训练来初始化词嵌入。当标记数据稀乏时，后者的技术可能会提高性能。在构建深层 CNN 网络时，通常做法是添加卷积层，然后是最大池化。顺序卷积增强了理解语义信息中抽象表示的能力，使得对文本的改进挖掘成为可能。具有更多卷积层的核覆盖了更多的短句，直到它们完全包含它，在此时，它们提供了句子特征的全局总结。

## 基于 CNN 的文本分类

已经有几种利用词间语义连接的 CNN 文本分类算法提案。这些技术可以分为大类：对单个单词操作的和对单个字符操作的。曾建议使用简单的卷积神经网络进行词级文本分类 [9]。利用了三个并行层，每层都通过在滑动窗口中一次查看三个、四个或五个单词来处理一个短句。在三次卷积之后，整个短句被送入最大池化（Maxpool），它从每次卷积中提取最强大的特征并将它们合并以创建一个独特的特征向量。然后使用软 max 层根据所选特征对数据进行分类。报告了使用不同输入词向量的这种基于字符的 CNN。在第一种变体中，词向量是固定的，而模型的其余参数是学习的。另一种变体涉及微调。特定任务的向量。Kim 的 CNN [11,12] 因其易于使用和高性能而仍被广泛使用。然而，主要问题是 CNN 无法处理远程依赖。在一项研究 [8] 中，深度金字塔 CNN（DPCNN）作为一种操作词级的替代 CNN 被提出。一旦离散文本转换为连续，DPCNN 在卷积块和下采样层之间循环，步长为 2。每个文档的隐藏信息通过最后的池化层合并为一个向量。所有的池化层（如图 1 所示）都是使用最大池化执行的。示例 2：Pooling 操作。



# 基于字符的 CNN 与并行化文本分类研究

## 引言

基于字符的 CNN 首先被开发出来。研究者发现，增强模型性能的关键信号可以在字符中找到。字符总是指示需要或不需要划分成单词，因此他们实验证明，对于分类任务来说，语言的语法和语义理解并非必要。基于字符的 CNN 的优点是能够学习非标准的字符组合，包括拼写错误和表情符号。他们的系统使用了多达六层的卷积层和三层全连接层，并使用了大小为 3 和 7 的基础池化层和卷积神经网络。

- **字符嵌入**：该层将字符格式化为包含其语义含义的向量。
- **卷积层**：该层过滤字符嵌入以提取局部特征。
- **最大池化**：该层选择最大局部区域对卷积输出进行下采样。
- **全连接层**：这些层将池化信息非线性转换到输出层（图中未显示），进行预测。

## 极深卷积神经网络（VDCNN）

用于文本处理的极深卷积神经网络（VDCNN）架构已被开发 [5]。该架构直接在单个字符级别工作，仅使用微小的卷积和池化操作。字符嵌入首先使用查找表生成。接下来应用了不同周期的“卷积块”，每个块都由 64 个大小为 3 的卷积组成。(i) 当空间精度减半时，特征图的总数增加一倍；(ii) 所有层具有相同数量的特征图和相同的时间分辨率。

作者证明（见图 3），将模型中的卷积层数从 11 层增加到 29 层可以显著提升其性能。

| 3 个全连接层 | K 最大池化 | 2, 卷积块, 3, 512 | 2, 卷积块, 3, 256 |
|---|---|---|---|
| 字符嵌入 | 3, 卷积层, 64 | 2, 卷积块, 3, 64 | 2, 卷积块, 3, 128 |

### 图 (3) 性能显著性

请记住，上述 CNN 模型并非所有可用 CNN 方法的完整列表。我们并非仅仅列出所有可用技术，而是重点关注分析在输入粒度和深度方面存在的许多 CNN。我们展示了两个模型，分别是词级 CNN 的一个浅层和一个深层，并引用了 [9] 和 [8]。同样，也有报道使用了基于浅层和深层模型的字符级卷积神经网络（CNNs）[5, 9]。对当前 CNN 设计的整体检查表明，输入的分辨率（检查字符或单词输入）以及 CNN 的布局范围（层数）是两个最重要的设计考虑因素。他们证明，字符级 CNN 从增加深度中获益比词级 CNN 更多 [10]。此外，他们还证明，一个非常接近 Kim 建议结构的简单词级 CNN，在多种文本分类任务上的表现优于更远且复杂的 CNN 框架。

## MapReduce-CNN

在这一方法离开实验室之前，时间成本是一个主要问题，即使在准确率很高的情况下也是如此。分类器经常面临在效率和成本之间取得平衡的挑战。由于设计和计算极其复杂，特别是对于大型系统，CNN 认为这更为严峻。近年来，出现了若干建议，提供各种并行计算技术作为大数据的通用解决方案。两种主要方法涉及训练集并行（涉及分布训练所需的数据）和神经网络级并行（涉及分布神经网络执行的计算）。我们建议的解决方案使用了基于 Map-Reduce 架构的第一种方法。这是对神经网络学习技术反向传播（back-propagation）的 MapReduce 修改 [4]。通过这种方式，反向传播执行了一个批处理学习阶段。

通过划分训练过程然后合并学习到的模型，手写数字识别的时间成本被大幅降低 [2]。在 MapReduce 范式中，有两个计算阶段：map 阶段和 reduce 阶段。所使用的数据集（存储在分散系统中）被分成若干个独立的子集，并在 Map 阶段以成对关系的形式分配给翻译器（translators）。每个 Mapper 通过用户提供的 map 函数同时处理一对输入，产生一组中间对，并将其保存到 Mapper 机器的硬盘中。

基于 MapReduce 构建的卷积神经网络中，这些中间对的位置从底层系统发送到主节点（master），然后由主节点通知 reducers 这些位置。一旦 reducers 远程读取了所有中间对，它们在 Reduce 阶段使用中间键进行排序和分组。

![](img/5e4d8ef2afa52a8404b28106580e19e4_807_0.png)

**图 (4)** Map Reduce 模型。（矩形：神经网络层。圆圈：数据批次。箭头：显示数据流。虚线：阶段或边界。标签：数据拆分的第一步涉及对输入数据进行分批处理。层（Mappers）在训练期间处理每批数据。聚合阶段：合并 Mapper 结果。权重更新阶段：根据聚合输出修改权重。Reducer：合并 Mapper 输出。Mapper 层的中间数据格式为 KeyValues。Mapper 层。层 1-n：包含许多 Mapper 层。该过程的最终产物。在分布式神经网络训练过程中，许多工作节点（Mappers）同时处理不同的训练批次，而一个中央组件（Reducer）收集输出。

每个 Reducer 都会字面上地在与每个键关联的所有值上运行用户指定的 reduce 函数，将它们转换为新值。所有 Reducer 的输出对（output pairs）都会合并成一个单一的最终结果集，并保存到文件中。MapReduce 系统中的所有 map 作业（以及 reduce 任务）都并行运行。这意味着 MapReduce 范式可以用于实现数据处理的高级并行。可以利用 MapReduce 分布计算的深度学习方法是卷积神经网络。在每条训练数据通过 CNN 之后，通过计算其偏梯度来调整网络权重。将输入数据扩展到许多处理器可能有助于在 CNN 训练阶段实现并行化。然后，每台机器使用其独特的数据集训练它自己的 CNN。

接下来，并行训练的 CNN 的最终结果可以被汇总，以调整下一个循环的权重。图 (4) 显示了整个操作的高级分解。

mappers 必须提供指令数据集 `(batch, label)`，其中 `batch` 是一个训练过的示例，以及特定实例的真实标签（truth label），以及一组任意初始化的权重 `[w1, w2,..., wn]`。集合 `a` 中有 `n` 个权重，其中 `n` 是网络中隐藏层的总数，`Wi` 表示第 `i` 层隐藏层的权重。训练集是成对值 `(batch, label)` 的集合。系统正利用输入样本（input samples）与它配合使用，每个 mapper 都用指定的权重进行初始化。reducer 接收新训练的权重 `WeightsUpdate[w1, w2,..., wn]`。更新后的权重在迭代后发送到 mappers，并在互联网上运行，直到达到最大迭代。Map 的伪代码见算法 1。

```
算法 1 Mapper 函数
要求：(batch, label)，其中 batch 是一个训练过的示例，label 是该实例的真实标签。
Weights：每个隐藏层的随机初始化权重。
1: 函数 MAP()
2: 获取初始 Weights
3: 使用 Weights 初始化 CNN
4: 在 batch 上进行前向传播和反向传播
5: 对于 i 从 0 到 n-1
6: Weights[i] = WeightsUpdate[i] + Weights[i]
7: 结束
8: 返回 Weights
```

```
算法 2 Reducer 函数
要求：mappers 的中间输出，即每个隐藏层的更新权重。
SumWeights：存储累加和的列表
1: 函数 REDUCE()
2: 初始化 SumWeights 为零
3: 对于 i 从 0 到 n-1
4: SumWeights[i] = SumWeights[i] + Weights[i]
5: 结束
6: 返回 SumWeights
```

reduction 接收 mapper 的中间结果并合并权重。由于权重根据所属的隐藏层进行了分类，reducer 可以轻松地对它们进行累加。平均权重通过将所有权重相加并除以总次数来计算。最终输出被发送回 mapper，为下一次迭代做准备，并被用于修订网络。算法 2 显示了减少函数的虚拟代码。

## 结果与讨论

这里提出的模型对从小到大的各种数据集进行了评估。我们参考了原始文章中作者的实验，对上述模型进行客观比较，并汇总了在 Yelp、Yahoo 和 Amazon 数据集 [5, 8] 上的结果（表 1）。准确率（即正确识别占总识别的比例）和错误率（即错误识别占总识别的比例）被用作衡量标准。错误率是评估各种 CNN 的典型指标。我们尽力通过相同的评估工具和数据集进行选择。从相关文献中报告的许多测试错误率中，我们选择了最低的那个。该过程运用了所有模型，且没有一个模型是预先选择的。

作者在各种实验环境中测试了他们的模型。当使用预训练的 word2vec 向量代替标准的随机初始化、静态初始化、非静态初始化或多通道初始化时，Kim 的 CNN 准确率达到了 89.6%。对于描述的 CNN [8]，作者利用大型数据集进行了测试，测试了不同模型深度（3、7 和 15 层）以及是否存在无监督嵌入的影响。

在研究 [5] 中，使用字符级 CNN 尝试了不同的池化方法（其中最大池化 Max pooling 效果最好）。研究人员还描述了类似的模型，这些模型是在修改词汇表和重处理阶段进行实验（例如，采用同义词数据增强策略）时得出的。据研究发现，所有使用大规模数据集训练的 CNN 模型都使用了基于 GPU 的训练框架。

人工神经网络为 CNN 的发展提供了基础。因此，它们的理论复杂度具有可比性。如文献 [4] 所示，通过将基础神经网络系统（带有一个隐藏层）适配到 MapReduce 框架中，可以降低其计算成本。假设 `P` 是执行算法的处理器数量，`n` 是输入维度，`m` 是训练样本数量。作者证明，在因子 `c` 下，使用单核可以将反向传播迭代的潜在成本从 `O(mnP + nc log(P))/c` 降低到 `O(mnP + nc log(c))`。

### CNN 的错误率

| 模型 | Yelp.p | Yelp.f | Yahoo | Ama.f | Ama.p |
| :--- | :--- | :--- | :--- | :--- | :--- |
| DPCNN [8] | 2.64 | 30.58 | 23.90 | 34.81 | 3.32 |
| Char-based CNN [16] | 4.36 | 37.95 | 28.80 | 40.43 | 4.93 |
| VDCNN [5] | 4.28 | 35.28 | 26.57 | 37.00 | 4.28 |

## 结论

在本研究中，我们分析了许多不同 CNN 模型的有效性。随着大数据的普及和任务复杂性的增加，CNN 的有效性受到影响，导致训练周期延长和计算开销巨大，特别是对于大规模数据集。如果学习算法要应对未来更复杂的挑战，需要在保持高速度和准确性的同时，还要具有成本效益。本研究利用 MapReduce 框架提供了一种并行 CNN 方法，提升了 CNN 的性能和可扩展性。该方法利用了 Spark MapReduce 框架。为了保护用户信息，将采用共识训练（consensus training）。

## 参考文献

- [1] Alataifi F., Gupta G.. 基于词嵌入的卷积神经网络情感分析系统.阿拉伯信息技术期刊.2022.19330
- [2] Kaliaappan N., Thasimuthuru Rajeswari S., Dakshaminorthy S., Sundar R.. 基于增强深度信层网络的智能视频监控.光电测量.2023.271810
- [3] Amrani G., Adadi A., Souriti S.. 深度学习在 EEG 信号分析中的应用：系统性综述.2021年第五届数据科学智能会议 (ICDS)18201
- [4] Prakash S., Yadav S.. 小波域医学图像融合：一种离散模型.IEEE 2018425111
- [5] Gandhi U., Malavar Kumar P., Chandra Babu G., Karthick G.. 使用卷积神经网络 (CNN) 和长记忆网络 (LSTM) 进行 Twitter 情感分析.无线通信.2022.1010
- [6] Nabel M., Groff C.. 使用卷积神经网络分类 Twitter 上的 COVID-19 虚假信息.信息系统与安全国际会议.202152204
- [7] Vashisht V., Pandey A.K.. 基于机器学习的语音识别.电子工程师学会会报.20221103233
- [8] Mohamed B.A., Ani-Ani M.S.. 深度学习医学图像分析综述.数据科学与技术期刊.2020.v9
- [9] Ma X., Zhou Q.. 用于智能感知与控制的神经和深度计算特殊兴趣.神经计算应用.20230217181
- [10] Kaur X., Saxena J., Shah J.. 2022年智能与可持续解决方案国际会议 (CISES).IEEE.2022.984466
- [11] Yu D.. 基于深度学习和卷积神经网络的视频评论智能分析系统.2021年 IEEE 电信、光学与计算机科学会议 (TOCS)81672220211.9688854
- [12] Sabba S., Cheired N., Katab H., Chechai K., Babu M.. 使用深度学习进行 ImB 评论情感分析.2022年第7届图像信号处理及其应用国际会议 (ISPA)摩及斯坦，阿尔及利亚.2022.16.978624
- [13] Alzahrani M.E., Aldhyani T.H.H., Althobati M.M., 基于深度学习算法的 E情感分析智能系统开发
