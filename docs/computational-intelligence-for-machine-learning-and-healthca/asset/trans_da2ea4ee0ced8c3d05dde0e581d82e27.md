

Ivan S., Ershova K., Kurdyumova N., Ershova O., Khomenko O., Danilov G., Shifrin M., and Zelman V. 神经重症监护室中与医疗相关的脑室炎和脑膜炎：机器学习方法选择的发病率和危险因素. Journal of Critical Care, (2018), 45, 95–104. [→](#bodymatter-014.xhtml#xref_d69967e56402)

Johnson A.E.W., Ghassemi M.M., Nemati S., Niehaus K.E., Clifton D.A., and Clifford G.D. 关键护理中的机器学习与决策支持. Proceedings of the IEEE. Institute of Electrical and Electronics Engineers, (2016), 104 (2), 444–466. [→](#bodymatter-014.xhtml#xref_d69967e55928)

Mbarek M., Kartit A., and Ouahmane H. 使用机器学习增强医疗云的安全性. Procedia Computer Science, (2018), 127, 388–397. [→](#bodymatter-014.xhtml#xref_d69967e56313)

Murdoch Travis B. and Detsky A.S. 大数据在医疗保健中不可避免的应用. JAMA, (2013), 309 (13), 1351–1352. [→](#bodymatter-014.xhtml#xref_d69967e56600)

Orphanidou C. and Wong D. 多维临床数据的机器学习模型. In: Handbook of Large-Scale Distributed Computing in Smart Healthcare, (2017), Springer, Cham, 177–216. [→](#bodymatter-014.xhtml#xref_d69967e56521)

Pratik S., Kendall F., Khozin S., Goosen R., Hu J., Laramie J., Ringel M., and Schork N. 临床开发中的人工智能和机器学习：转化视角. NPJ Digital Medicine, (2019), 2 (1), 1–5. [→](#bodymatter-014.xhtml#xref_d69967e55849)

Prerna D. and Bais S. 医疗保险欺诈检测中的监督学习方法. In: Machine Learning in Healthcare Informatics, (2014), Springer, Berlin, Heidelberg, 261–285. [→](#bodymatter-014.xhtml#xref_d69967e56079)

Rohan B., Nambiar A.R., and Dutta D., 机器学习在医疗保健中的研究, In 2017 IEEE 41st Annual Computer Software and Applications Conference (COMPSAC), Vol. 2, pp. 236–241, 2017. [→](#bodymatter-014.xhtml#xref_d69967e55511)

Sabyasachi D., Shakyawar S.K., Sharma M., and Kaushik S. 医疗保健中的大数据：管理、分析及未来展望. Journal of Big Data, (2019), 6 (1), 54–61. [→](#bodymatter-014.xhtml#xref_d69967e56640)

Scheeder C., Heigwer F., and Boutros M. 药物发现中的机器学习和基于图像的分析. Current Opinion in Systems Biology, (2018), 10, 43–52. [→](#bodymatter-014.xhtml#xref_d69967e56699)

Yichuan W., Kung L.A., and Byrd T.A. 大数据分析：理解其能力及对医疗机构的潜在益处. Technological Forecasting And Social Change, (2018), 126, 3–13. [→](#bodymatter-014.xhtml#xref_d69967e55741)

Yuvaraj N.R., and SriPreetha K.R. 使用 Hadoop 集群上的机器学习算法进行医疗系统中的糖尿病预测, (2017)

# 15 基于进化特征选择的计算健康信息学

Vanaja Ramaswamy Department of Information Science and Technology, College of Engineering Guindy, Anna University, Chennai, Tamil Nadu, India Saswati Mukherjee Department of Information Science and Technology, College of Engineering Guindy, Anna University, Chennai, Tamil Nadu, India

## Abstract

本章是对基于进化计算（EC）的特征选择（FS）技术的最新综述，其主要目标是提高机器学习算法的准确性并减少计算时间。其思路是突出 EC 作为机器学习过程中 FS 的一种自然启发式优化技术的优势。生物和自然智能的建模在最近十年取得了稳步进展，这促使我们回顾最先进的 FS 技术，以为计算智能领域增添更多内容。鉴于其重要性，还展示了在支持健康信息学方面的用例。

关键词：进化计算，特征选择，机器学习，计算智能，

## 15.1 Introduction

本章介绍机器学习技术，重点关注特征选择（FS），并回顾了最新的 FS 机制及其类型。FS 作为机器学习中的一个重要子过程，允许学习算法更快地训练，并通过选择合适的特征子集来提高模型的准确性（[Dash and Liu, 1997](#bodymatter-015.xhtml#b_9783110648195-015_ref_012)）。它还带来了对数据的更好理解并具有良好的泛化能力。当机器学习任务之前采用有效的 FS 方法时，预测性能会得到显著提高。本章解释了基于过滤器的方法和基于包装器的方法的 FS 的一般概念，以及它们各自方法上的差异。只要数据集中可用的特征数量较少，一般的 FS（过滤器/包装器）即可直接应用。随着我们逐步访问大数据，无论是样本大小还是特征大小，搜索空间非常大，[Xue et al., 2015](#bodymatter-015.xhtml#b_9783110648195-015_ref_048))，不再有通用方法能做得很好。迫切需要一种机制，它可以随机地从启发式开始，并在搜索全局最优位置时进行有效的移动。因此，本章的兴趣在于提供 FS 机制的进化范式的概述及其在计算智能中的重要性。由于其在搜索中的全局探索能力，进化 FS 方法即遗传算法（GA）、遗传编程（GP）、粒子群优化（PSO）、蚁群优化（ACO）等在最近的研究中变得流行（[De La Iglesia, 2013](#bodymatter-015.xhtml#b_9783110648195-015_ref_013)）。本章将 FS 分类为基于过滤器的进化方法（FBEM）、基于包装器的进化方法（WBEM）和基于混合的进化方法（HBEM）。它根据应用的相关性和实施需求，解释了这三类 FS 与上述进化方法的特定组合。考虑到行业的时效性，医疗保健被视为一个应用领域，其中针对 FBEM 和 WBEM 讨论了特定的用例。

## 15.2 Machine learning techniques with a focus on feature selection

“机器学习是一种人工智能，它通过利用过去获得的经验为系统提供自动学习能力。” 如同无关和冗余特征会负面影响模型的性能（[https://towardsdatascience.com/feature-selection-techniques-in-machine-learning-with-python-f24e7da3f36e](https://towardsdatascience.com/feature-selection-techniques-in-machine-learning-with-python-f24e7da3f36e)），它们可以在机器学习周期的学习阶段之前被移除。

FS 作为一个高效的预处理器，可以作为一个重要范式来做到这一点，以在时间和空间复杂度上带来改进。

### 15.2.1 Terminologies involved with machine learning

以下是在机器学习范式中涉及的术语：

* *Model*

  模型是使用机器学习技术从数据中学习某些概念的假设性表示。

* *Dataset*

  文件包含“n”个实例（待训练的记录）表示为行和“f”个特征表示为列。

* *Feature Vector and features*

  数据集的单个记录将构成一个特征向量，特征向量中的每个实体代表一个特征。

* *Target (Label)*

  记录关联的输出标签称为目标。这适用于监督学习方法。

* *Training*

  使用机器学习算法生成学习模型产生的模式。

* *Prediction*

  新数据可以应用于模型，根据数据的特征做出预测。

