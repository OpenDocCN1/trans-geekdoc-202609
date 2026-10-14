
Shilpa Mangesh [Pande et al. (2021](#ch7.xhtml#ref7_4)) 为农民提供了一个简单的产量预测工具。农民使用智能手机应用连接互联网。GPS 定位用户。输入位置和土壤类型。机器学习系统可以识别最有利可图的作物，并预测用户选择的作物的农业产量。SVM、RF、MLR、ANN 和 KNN 用于预测农业产量。研究 (A et al., 2021) 建议通过考虑种植时间、土壤特性（包括土壤类型、pH 值、养分含量）以及气象因素（如降雨量、温度和地理位置）来帮助农民选择作物。该系统采用线性回归以及神经网络开发。另一项研究 ([Gosai et al., 2021](#ch7.xhtml#ref7_17)) 根据土壤的 N、P、K、pH 值、湿度、温度和降雨量预测最佳作物。决策树、SVM、Naive Bayes、支持向量机、LR、RF 和 XGBoost 被用于开发建议系统，其中 XGBoost 的准确率最高。通过 [Kulkarni et al., 2018](#ch7.xhtml#ref7_15) 的分布分析、多数投票、相关分析和集成，生成了 22 种作物推荐。[Chhikara et al. (2022](#ch7.xhtml#ref7_19)) 提出了一种基于机器学习的作物推荐系统，能够准确预测 22 种不同作物的产量，解决农民的作物管理问题，如作物选择、产量和利润。研究人员使用决策树、Naive Bayes、SVM、LR、RF 和 Xgboost。Pradeepa Bandara 等人开发了斯里兰卡的作物推荐系统 ([Bandara et al., 2020](#ch7.xhtml#ref7_20))。该研究提供了基于 Arduino 微控制器、Naive Bayes（多项式）和 SVM 以及无监督机器学习算法 K-Means Clustering 和自然语言处理（NLP）（情感分析）的推荐系统理论与概念平台。Avinash [Kumar et al. (2019](#ch7.xhtml#ref7_21)) 解决了作物选择和病害问题。使用 SVM 分类模型、决策树模型和逻辑回归模型构建了该推荐系统。

## III. Objectives

本研究的目标是实现基于土壤化学性质和气象条件的作物推荐系统的机器学习算法实现，并对该系统进行评估。

## IV. Background techniques

### A. Logistic regression

Logistic regression 是一种主要用于分类问题的机器学习算法，基于概率预测分析 ([Rymarczyk et al., 2019](#ch7.xhtml#ref7_10))。值得注意的是，LR 模型的代价函数比线性回归更为复杂。该代价函数，通常称为“Sigmoid 函数”或“Logistic 函数”，取代了线性函数。由于逻辑回归的基本前提，代价函数的输出范围天然限制在 \[0, 1\] 区间。这一限制源于逻辑回归本质上模型事件发生的概率，线性函数无法捕捉其细微特征。

### B. Decision tree

决策树是代表数据分类模型的常用方法 ([Jijo and Abdulazeez, 2021](#ch7.xhtml#ref7_9))。决策树在机器学习、图像处理和模式识别等多个领域都具有多功能性，其核心任务是分类，因此在数据挖掘领域被广泛用作分类器。这些决策树由相互连接的节点和分支组成，每个节点表示离散分类类别中的属性集合，每条分支代表节点对应的可能取值。决策树因其能够快速准确地处理大规模数据集而受到广泛青睐。

### C. Random forest

随机森林是一种监督学习技术，在机器学习领域展现出显著成功，能够处理分类和预测等多种任务。其独特之处在于它像一个由多个决策树组成的团队协作解决问题。它不依赖单一决策树，而是结合许多树的结果，每棵树在不同的数据子集上训练。这种协作方式提高了准确性。树的数量越多，性能越好，错误率越低 ([Dabiri et al., 2022](#ch7.xhtml#ref7_11); [Gera et al., 2021](#ch7.xhtml#ref7_2))。

### D. LightGBM

LightGBM 是一种基于树的学习算法的梯度提升框架 ([Tang et al., 2020](#ch7.xhtml#ref7_12))。它因分布式高效的设计而拥有诸多优势，如训练时间加快、内存占用更少，支持多 GPU 和分布式学习。LightGBM 能够处理大量数据并提供更高的精度。

## V. Methodology

如 [Figure 7.1](#ch7.xhtml#fig7_1) 所示，所提方法在第一阶段从 GitHub 仓库 [https://github.com/gabbygab1233/Crop-Recommender/blob/main/Crop\_recommendation.csv](https://github.com/gabbygab1233/Crop-Recommender/blob/main/Crop\_recommendation.csv) 获取用于拟议方法的数据集。该数据集结合了印度农业部门收集的降雨、气候和肥料数据。[Table 7.1](#ch7.xhtml#tab7_1) 展示了所用特征的描述。数据集包含 8 个特征和 2200 条记录。

[Table 7.1 Feature description](#ch7.xhtml#R_tab7_1)

| Attribute || Attribute description |
| --- | --- |
| **Nitrogen** || 土壤中氮含量的比例 |
| **Phosphorus** || 土壤中磷含量的比例 |
| **Potassium** || 土壤中钾含量的比例 |
| **Rainfall** || 降雨量 (mm) |
| **Humidity** || 相对湿度 (%) |
| **pH level** || 土壤 pH 值 |
| **Temperature** || 温度 (摄氏度) |

对收集的原始数据进行准备，以使其适合构建机器学习模型，这是创建机器学习模型的第一步和最关键的一步。数据来源各异，往往不够清洁。数据必须在进行任何操作之前进行清洗和格式化。数据预处理对于此目的至关重要。

## VI. Results

[Table 7.2](#ch7.xhtml#tab7_2) 显示了用于开发作物推荐系统的机器学习方法的性能，包括 LR、DT、RF 和 LightGBM。所使用的算法通过精确率、召回率、F1 分数和支持度等评估指标进行了评估。

### Precision

