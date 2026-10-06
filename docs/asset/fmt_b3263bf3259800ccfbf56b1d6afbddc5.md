
• 2015–2016、2014–2015 和 2013–2014 财政年度的信用卡持有人数量分别为 2450 万、2111 万和 1918 万 [7]。

• 2009–2010 财政年度的住房贷款账户总数为 57.38 万 [8]。

![Figure 6.1 Rise in issuing of credit cards during 2012–2016.](img/fig6-1.jpg)

**Figure 6.1** Rise in issuing of credit cards during 2012–2016.

除了信用卡，各类贷款、抵押贷款、小额和微额融资等信用产品也由各金融机构提供。由于新申请人数量庞大且现有客户众多，手动进行信用评分极为困难，或需要大量具备领域知识和客户行为专业能力的管理人员。目前，“信用评分不仅限于银行或信用行业，电信、房地产等其他领域也采用信用评分模型来评估客户行为”。因此，“人工智能可能解决手动信用评分的问题”。提升模型预测性能，特别是针对可信度低的申请人群体，对金融机构具有重要意义 [9, 10]。本文旨在通过剔除冗余和噪声特征，提升模型的分类性能。

文章其余部分组织如下：`Section 6.2` 简要回顾相关文献；`Section 6.3` 介绍“拟议信用评分模型”；`Section 6.4` 展示拟议方法的实验结果，并据此给出结论性 remarks。

## 6.2 Literature Survey

大多数学者将信用风险估计视为二分类问题（信用 worthy 或 non-creditworthy），并发现其能够可靠地发现信用评分数据中的隐藏模式。这些系统帮助专家提升对信用风险的认知。在此背景下，多种机器学习（ML）方法被用于构建风险估计系统。诸如“人工神经网络（ANN）”和“支持向量机（SVM）”等分类方法已成功应用于信用风险预测模型。

`SVM` [11] 具有“优越的泛化能力”和“全局优化”特性，因此被广泛用作分类工具，不仅在信用评分领域，也在其他领域中被大量研究。`Li et al.` [12] 通过数据预处理，以 `SVM` 为分类手段构建信用风险评估模型，用于区分消费者抵押贷款的可能申请人。`Gestel et al.` [13] 采用“最小二步支持向量机（LS-SVM）”评估企业客户的信用 worthiness。`West` [14] 发表了一篇关于各类分类方法的综述，并评估了分类器在信用评分数据集上的表现。`Xiao and Fei` [15] 提出一种基于“SVM 与最优参数值”的方法。`Kuppili et al.` [16] 利用极端学习机器（Extreme Learning Machine）对信用评分数据进行分析，并结合脉冲神经元模型进行聚合。同样，`Zhou et al.` [17] 采用“加权 SVM”构建信用评分模型。

将多种方法结合形成混合模型是一种动态的、综合不同步骤的方案，旨在提升特定结论的质量。在信用评分数据集中，包含诸如申请人社会与财务状况等异构特征（如类别型、小范围数值型、大范围数值型），这些特征可能存在冗余或无关，从而降低模型性能。因此，许多研究者提出了数据预处理步骤，如“特征选择”和“异常值检测”，以增强预测性能，相关方法描述如下。

混合信用评分模型将聚合 `SVM` 与“多变量自适应回归分段（MARS）”和“F-score”特征选择方法相结合，在文章 [18] 中进行评估。类似地，文章 [19] 和 [20] 分别将“逐步回归（SR）”和“MARS”与人工神经网络（ANN）相结合，用于信用评分。`Oreski 和 Oreski` [21] 提出一种基于“遗传算法（GA）”的特征选择方法，并与分类方法混合。`Wang et al.` [22] 和 `Huang and Dun` [23] 分别采用“模糊集与禁搜索”以及“二进制粒子群优化（BPSO）”对有价值特征集进行优化，并与 `SVM` 结合进行分类。

`Section 6.3` 节提出的信用评分模型如图 6.2 所示。该模型在第一阶段采用进化特征选择，第二阶段采用集成分类，具体细节如下小节讨论。在特征选择前，数据集需进行预处理，因为信用评分数据集包含异构数据类型。本文使用神经网络作为分类工具，该工具以向量形式处理数据。因此，数据预处理包括数据清洗（消除缺失值）、数据转换（将类别值转换为数值）以及数据离散化（将长尾数值转换为小范围值）。

![Figure 6.2 Proposed two-stage credit scoring model.](img/fig6-2.jpg)

**Figure 6.2** Proposed two-stage credit scoring model.

## 6.3.1 Stage-1: Feature Selection

本文采用进化算法 `BPSOGSA` [24] 进行有价值特征的选择。文献 [29] 中的作者提出了 `PSOGSA`，这是一种融合粒子群优化（PSO）的社会思维（gbest）能力和进化型基于重力搜索算法（GSA）的开发能力的混合方法。`PSOGSA` 在探索和开发能力方面优于 `PSO` 和 `GSA` [24]。

在 `PSOGSA` [29] 中，所有搜索代理在每次迭代中从一个位置移动到另一个位置，搜索空间为连续空间，并用位置向量表示。这里，`PSOGSA` 用于特征选择，位置向量应以二进制格式表示，其中 0 表示对应特征不存在，1 表示存在。为将连续向量转换为二进制位置向量，需要使用转移函数，该函数结合搜索代理的可能速度 [25] 进行调整。文献中有多种转移函数，属于两类，即 `S` 形和 `V` 形 [26]。`V`‑形转移函数在收敛速度上优于 `S`‑形转移函数 [27]。`V`‑形转移函数如在 Equations (6.1)–(6.4) [26] 所示。

(6.1) ![image](img/eq6-1.png) (6.2) ![image](img/eq6-2.png) (6.3) ![image](img/eq6-3.png) (6.4) ![image](img/eq6-4.png)

其中 ![images](img/eqpg104-1.png) 表示搜索代理 *i* 在迭代 *k* 时的速度。

上述所有转移函数均用于在 `BPSOGSA` 中调整搜索代理的速度，进而将其转换为位置向量元素翻转的概率。进一步，搜索代理的位置向量的概率被用于将其转换为二进制格式，并依据 Equation (6.5) 的规则更新。

(6.5) ![image](img/eq6-5.png)

其中 *X[i]* 表示第 *i* 个搜索代理的位置。

## 6.3.2 Proposed Criteria Function

相关系数（Corr）用于衡量两个变量之间的关系 [28–30]，可通过 Equation (6.6) 计算。Corr 的取值范围为 -1 到 +1，其中 +1 表示最强正相关，-1 表示最强负相关，0 表示两个特征之间不存在线性关系。拟议的标准函数如在 Equation (6.9)，其依赖于搜索代理中特征的类间相关系数（Inter[ccc]）和类内相关系数（Intra[ccc]）的比例。Inter[ccc] 表示特征与类标签之间的相关性，Intra[ccc] 表示特征之间的相关性，分别由 Equations (6.7) 和 (6.8) 计算。

(6.6) ![image](img/eq6-6.png)

其中 *P* 和 *Q* 表示特征，*n* 表示这些特征的值数量。

(6.7) ![image](img/eq6-7.png) (6.8) ![image](img/eq6-8.png)

此处 *F[i]* 表示第 *i* 个特征，*Y* 表示目标标签。

(6.9) ![image](img/eq6-9.png)

其中 fitness value[i] 表示第 *i* 个搜索代理的适应度值。

## 6.3.3 Stage-2: Ensemble Classifier

在机器学习领域，对数据分类的研究已相当丰富，文献中可得到多种分类方法。然而，并没有明确的过程来判断哪种分类器在特定数据集上表现最佳。某一特定分类器可能适合某些数据集，但在其他数据集上可能表现不佳；相反，另一种分类器可能在这些数据集上表现更好。 ensemble 方法能够在每个数据集上提供接近最优的结果。利用 ensemble 分类器的基本意图是，当多个分类器做出决策时，而不是仅依赖单一分类器的决策，不同的基学习者可能从不同角度观察同一模式，从而相互补充预测信息，结合多个分类器的决策进行最终判断。参与决策的所有分类器均称为基分类器（base classifiers）。

最常见的基分类器决策聚合方式有三种：一致投票（UV）、多数投票（MV）和加权投票（WV）。在 UV 方式下，若给定类别为 class-1，当所有分类器均将样本归类为 class-1 时，UV 将最终决策定为 class-1。在 MV 方式下，最终输出为获得最多票数的类别。WV 的最终输出是基分类器输出的加权和，权重与该基分类器的性能（如分类准确率）成正比。ensemble 可以分为同质框架（基分类器同类型）或异质框架（基分类器不同类型）。在同质或异质框架下，使用 MV 或 UV 时，预测能力对特定类别标签表现良好 [31]。

人工神经网络（ANN）是受人脑信息处理和学习能力启发的强大分类方法，因其在学习和识别输入‑输出数据的复杂非线性关联方面表现出色 [32]。在第二阶段，三个基于神经网络的异质分类器被通过 WV 方法聚合，分别是 “多层前馈神经网络（MLFN）[6, 33]”、 “时延神经网络（TDNN）[34, 35]” 和 “径向基功能神经网络（RBFN）[36, 37]”。

## 6.4 结果与讨论

This section offers the explanation of datasets together with performance measures utilized to validate the proposed approach and comprehensive outcome investigation on four credit scoring datasets.

## 6.4.1 Experimental Datasets and Performance Measures

Two-stage credit scoring model is experimented on four credit scoring datasets, *viz*., “Australian credit approval (AUS)”, “German-categorical loan approval (GCD)”, “Japanese credit screening (JPD)”, and “Germannumerical loan approval (GND)”. All aforementioned datasets are obtained from the “UCI Machine Learning Repository [38]” and comprehensive descriptions are as tabularized in Table 6.1. All datasets are binary class datasets in which positive and negative classes signify as accepted not accepted applications.

Here, accuracy and G-measure are utilized to measure and compare the performances of proposed approach with other approaches. Accuracy \as in [Equation (6.10)] shows the “predictive performance of classifier”, and it is not sufficient as a performance measure, if there is noteworthy class disproportion on the way to a class in the dataset. G-measure \as in [Equation (6.11)] is a measure which takes “both the positive and negative classes accuracies” in account to calculate the score, where specificity (Spe) and sensitivity (Sen) represent the predictive performance toward the positive and negative class, respectively.

(6.10) ![image](img/eq6-10.png) (6.11) ![image](img/eq6-11.png)

where “TP”, “FP”, “TN”, and “FN” indicate as “True Positive”, “False Positive”, “True Negative”, and “False Negative”, respectively, and ![images](img/eqpg108-1.png), ![images](img/eqpg108-2.png).

**Table 6.1** Description about experimental datasets.

| **S. no.** | **Dataset** | **Instances** | **+ve/−ve** | **No. of features** |
| --- | --- | --- | --- | --- |
| 1 | AUS | 690 | 307/383 | 14 |
| 2 | GCD | 1,000 | 700/300 | 20 |
| 3 | JPD | 690 | 307/383 | 15 |
| 4 | GND | 1,000 | 700/300 | 24 |

## 6.4.2 Classification Results With Feature Selection

Pre-processing is the initial and most significant phase in data mining. For pre-processing the data, data cleaning, transformation, and discretization processes are applied. Toward the data-cleaning, data samples with missing value are eliminated. Toward the data-transformation distinct nominal values of an attribute is replaced by a unique integer number. Because, neural network-based classifiers require the data samples as a vector of real numbers. Numerical feature value is rescaled in a predefined interval respectively. With the purpose of anticipating to the features with wide-ranging numeric values overlook the features with narrow-ranging numeric values, features are rescaled between a range using discretization procedure by applying Boolean Reasoning Algorithm [39].

**Table 6.2** Performances of MLFN, RBFN, DTNN, and ensemble approaches with features selection on Australian datasets.

| **Classifier** | **Measure** | **ALL** | **CFS** | **V1** | **V2** | **V3** | **V4** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| MLFN | ACC | 83.12 | 84.35 | 84.34 | 82.13 | 85.57 | 83.31 |
| | G-M | 83.41 | 84.93 | 84.32 | 830.1 | 85.66 | 84.41 |
| DTNN | ACC | 89.16 | 90.57 | 91.81 | 91.53 | 91.43 | 91.04 |
| | G-M | 90.39 | 91.08 | 92.11 | 92.05 | 92.09 | 91.25 |
| RBFN | ACC | 85.59 | 87.23 | 87.6 | 86.48 | 87.76 | 87.39 |
| | G-M | 86.19 | 88.36 | 87.74 | 87.59 | 88.06 | 87.96 |
| MV | ACC | 89.43 | 90.56 | 91.88 | 91.86 | 91.58 | 91.63 |
| | G-M | 89.15 | 90.93 | 92.33 | 92.48 | 92.23 | 92.29 |
| WV | ACC | 90.02 | 90.86 | 91.92 | 91.89 | 91.79 | 91.69 |
| | G-M | 90.67 | 91.26 | 92.36 | 92.54 | 92.46 | 92.61 |
