# 2021首届人工智能与数据分析国际会议 (CAIDA) (沙特阿拉伯利雅得 2021.4.6-2021.4.7) 2021首届人工智能与数据分析












**摘要**—心力衰竭（CHF）是医疗保健系统负担沉重的疾病之一。患者在诊所的就诊和随访与直接间接成本有关并影响治疗结果。本研究旨在使用机器学习模型预测心力衰竭患者的风险水平和分类，以有信心地延长患者下次门诊的时间。使用 Waikato Enrichment Knowledge Analysis Version 3.4（Weka）通过不同的学习模型对数据进行统计分析。在测试的最佳模型中，随机森林（Random Forest）和逻辑回归（Logistic Regression）表现出最佳性能。模型在这些优秀指标（精确率、召回率、F 值和 ROC）上的整体准确率达到了 0.89 左右。未来需要更多平衡的数据集和记录来测试此类模型，这将有助于医疗保健系统避免直接和间接成本并改善患者的预后。

**关键词：** 心力衰竭（CHF）；随机森林；机器学习；预测模型

# I. 引言

心血管疾病（CVD）是首要死因。2017 年，有 1780 万人死于 CVD。预计到 2030 年，每年死亡人数将跃至 2220 万以上。据报道，2014 年至2015 年间与 CVD 和中风相关的直接和间接成本在美国为 351 亿美元。心力衰竭（CHF）是最常见的 CVD 之一，可以描述为一种以心脏泵血和充血能力下降为特征的临床综合征。生理上，它是心脏输出量不足以满足身体代谢需求。其患病率为 1-2%，在老年人群中高达 10%。最近的一项研究显示，出院心衰竭患者的 60 天死亡率约为 8.6%，死亡/住院合并率为 36.2% [5]。在当地，一项沙特多中心研究显示，12 个月内全因死亡率约为 9%，再住院率为 39%。报告显示，心力衰竭的 30 天入院率仍需改进 [7]。住院后的早期随访与心力衰竭患者较低的 30 天入院率有关 [8]。因此，指南建议出院后进行密切随访（7-14 天）[9]。机器学习和深度学习的最新进展使其被应用于各种医疗状况；因此，不同的机器学习技术已被用于改善心力衰竭的预后。在本研究中，我们旨在使用机器学习对心力衰竭患者进行分类。这种分类有助于预测我们能够延长心力衰竭患者出院后下次就诊的时间。主要研究问题是——我们如何延长心力衰竭患者下次就诊的时间？

# II. 文献综述

我们目前有不同人员研究的可用机器学习技术。Moloud 等（2015）通过使用不同的模型识别心力衰竭，证实了 CHF 的准确率达到了 93%。在这些数据集上，具有这些优秀指标（精确率、召回率、F 值和 ROC）的模型整体准确率达到了 0.89。Fais（2019）显示，决策树（DT）的准确率达到了 92% [23]。相比之下，朴叶贝叶斯（Naive Bayes）准确率为 90%。

# III. 方法

我们的研究使用了多种可用的机器学习技术。

### A. 数据管理

数据使用 Waikato Enrichment Knowledge Analysis Version 3.4（Weka）进行统计分析。在应用模型之前，对数据进行了清理和处理。

### B. 模型验证

我们使用了 10 折交叉验证来测试模型 [18]。未来需要更多平衡的数据集和记录来测试此类模型，这将有助于医疗保健系统避免直接和间接成本并改善患者的预后。





### 表 2：精确率、F 值和 ROC（基于类别）

| 模型 | 精确率 | F 值 | ROC | |
|---|---|---|---|---|
| 逻辑回归 | 0.807 | 0.805 | 0.805 | 0.885 |
| 随机森林 | 0.811 | 0.800 | 0.799 | 0.877 |
| AdaBoost | 0.710 | 0.738 | 0.726 | 0.865 |
| 朴素贝斯 | 0.747 | 0.709 | 0.698 | 0.860 |
| 多层感知器 | 0.763 | 0.747 | 0.743 | 0.820 |
| 决策树 | 0.775 | 0.767 | 0.766 | 0.792 |
| IBK | 0.726 | 0.722 | 0.712 | 0.772 |
| ZeroR | 0.487 | 0.487 | 0.487 | 0.451 |

> [2] Corason, R. F., de Groot, and J. J. van Linuis, ‘Heart failure.’ Cardiovascular, vol. 50, no. 3, pp. 419–422 (2001).

> [3] L.-H. Tan, S. G. Williams, D. K. Han, and A. Cole-Sloan, ‘Definitions of heart failure: are they universally agreed? A critical appraisal.’ Exp. Rev. Cardiology, vol. 8, pp. 212–217 (2008).

> [4] P. Ponikowski et al., ‘2006 ESC Guidelines for the diagnosis and treatment of acute heart failure. The Task Force for the diagnosis and treatment of acute heart failure of the European Society of Cardiology (ESC). Developed with the support of the European Heart Association (HFA). Eur. Heart Fail., vol. 18, no. 8, pp. 891–975, 2006).

> [5] G. C. Foster et al., ‘Association between performance and clinical outcomes in patients with heart failure.’ JAMA, vol. 298, no. 1, pp. 61–70, 2007).

我们所采用的模型均未消除不平衡数据集带来的偏差。通过使用分层折叠（Stratified Folds）对同一数据集（不平衡的），我们对模型进行了测试，结果如表3所示。

### 表 3：精确率、F 值和 ROC（分层折叠模型）

| 模型 | 精确率 | F 值 | ROC | |
|---|---|---|---|---|
| 朴素贝斯 | 0.855 | 0.829 | 0.839 | 0.861 |
| 多层感知器 | 0.803 | 0.771 | 0.785 | 0.723 |
| 随机森林 | 0.899 | 0.886 | 0.857 | 0.713 |
| IBK | 0.829 | 0.829 | 0.826 | 0.676 |
| 逻辑回归 | 0.815 | 0.809 | 0.807 | 0.667 |
| 决策树 | 0.878 | 0.866 | 0.867 | 0.526 |
| ZeroR | * | * | * | 0.451 |

> [6] R. P. Cook and E. Y. Adash, ‘Clinical characteristics and outcomes of patients with heart failure.’ J. Cardiology, vol. 306, no. 16, pp. 1794–1795 (2001).

> [7] A. M. Hernandez et al., ‘Relationship between physician-patient relationship and outcomes in heart failure.’ JAMA, vol. 303, no. 17, pp. 1716–1722 (2010).

> [8] S. J. Williams et al., ‘Management of chronic heart failure: a summary report of the American Heart Association/American Heart Association task force on practice: guidelines.’ Circulation, vol. 128, no. 16, pp. 1812–1853 (2013).

> [9] Y. Chen et al., ‘Evaluation of artificial intelligence systems for the diagnosis of diabetic disease.’ J. Int. Med Appl., vol. 99, no. 01, pp. 1–16, 2021).

机器学习模型已被用于辅助心脏力竭决策的工具。我们使用模型来预测不同的类别和风险水平，以帮助临床医生决定最佳就诊时间。机器学习模型：ZeroR、朴素贝斯、IBK、逻辑回归、决策树、AdaBoost 和随机森林；已通过 Weka 进行测试。具有这些优秀指标的模型（如随机森林和逻辑回归）的整体性能可以通过数据平衡技术进一步提升。

## 五、 讨论

在我们的研究中，我们尝试测试并使用机器学习对临床数据中的充心性心衰竭（CHF）患者的风险水平和类别进行广泛预测。我们观察到随机森林和逻辑回归模型在预测下次就诊时间方面最具可靠性，准确率约为 89%。未来需要更多的数据集和患者记录来测试此类模型，这些模型可以为医疗系统节省大量的直接和间接成本并改善患者预后。

## 六、 结论

## 参考文献

> [1] E. J. Benjamin et al., ‘Heart failure and stroke statistics–2019 update: A report from the American heart association,’ Circulation, vol. 139, no. 10, 2019.

