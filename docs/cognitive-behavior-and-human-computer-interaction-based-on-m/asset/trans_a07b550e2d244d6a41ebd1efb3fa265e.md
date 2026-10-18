

表格展示了不同分类器对增强多层感知机的展示相关性。基于 [表 8.1](#c08.xhtml#tab8-1)，绘制了不同图表来说明各种分类器的类似调查。在 [图 8.2](#c08.xhtml#fig8-2) 中，以图形方式介绍了 AI 结构的展示检查。[图 8.2a](#c08.xhtml#fig8-2) 描述了各种分类器的精度。目前，它在所有分类器中具有最高精度，因为它旨在选择。

最可接受的子集类型，这是一个重要的，是由目标组件充分关联。[图 8.2b](#c08.xhtml#fig8-2) 描述了误差曲线，它意味着分类器的整体表现。如果它们最小值，它清楚地表达了模型的精度。目前，Bagging 在特征选择后误差突然下降，具有最小值。[图 8.2c](#c08.xhtml#fig8-2) 描述了 TP 率，它意味着准确表征的发生。Multilayer Perception、Bagging、Random Committee 和 J48 执行发生。Multilayer Perception、Bagging、Random Committee 和 J48 很好地执行以准确分类示例。[图 8.2d](#c08.xhtml#fig8-2) 描述了 FP 率，它意味着不诚实安排的案例。Multilayer Perception、Bagging 和 Random Committee 执行一个形式以错误地排序所有事件，因为这个基于图表的模型利用概率分布和概率假设的概念进行预测 \[20\]。但是，J48 在包含选择前具有较低的 FP 率，但在特征选择后 FP 增加。这些测量在各种分类器上执行，如 Multilayer Perception、Bagging、Random Committee 和 J48 \[2\]。在这些分类器中，可以看出 Multilayer Perception 给出最高精度，而 Random Committee 和 J48 具有最低，即 84.61%。如果我们谈论 TP 率，Multilayer Perception 和 Bagging 具有最高 TP 率，而 Random Committee 和 J48 具有最低，即 0.846。如果我们谈论 FP 率，Multilayer Perception、Random Committee 和 Bagging 完成了出色的工作，它们具有最低 FP 率，但 J48 具有最独特的 FP 率。

**[Table 8.1](#c08.xhtml#tab8_1)** 不同分类器对增强多层感知机的展示相关性。

| **Classifier** || **Multilayer perception** || **Bagging** || **Random committee** || **J48** |

| --- | --- | --- | --- | --- |

| Accuracy || 93.30% || 92.4% || 84.66% || 84.77% |

| --- | --- | --- | --- | --- |

| Error || 7.79% || 7.91% || 15.38% || 15.38% |

| TP Rate || 0.943% || 0.932% || 0.816% || 0.851% |

| FP Rate || 0.413% || 0.460% || 0.433% || 0.853% |

![Figure 8.2 Comparison of machine learning structure with classifiers using accuracy, error, TP rate, and FP rate.](images/fig8_2a.jpg)

**[Figure 8.2](#c08.xhtml#fig8_2)** Comparison of machine learning structure with classifiers using accuracy, error, TP rate, and FP rate.

## 8.6 Conclusion

提出了一种高效的集成 AI 系统，用于训练元素维度和高度平衡的隐性筛选生物测定信息。一种领先的著名元素确定排序器，主要是 Gini 指数，被用来定位用于训练计算模型的基本特征。此外，Class Balancer 计算被执行以调整训练信息中的动态和惰性类。通过所提议模型的实现和使用标准数据集，精度、TP 率、FP 率和错误分别被观察为 92.30%、0.923%、0.423% 和 7.69%。这种基于集成 AI 计算的高效结构也可以作为动态和惰性混合物外推的决策系统。未来，AI 结构将通过应用于各种数据策略（如 Hadoop 和 Spark）来改进。

## References

1.  Alix-Panabieres, C. and Pantel, K., Clinical applications of circulating tumor cells and circulating tumor DNA as liquid biopsy. *Cancer Discov*., 6, 5, 479491, May 2016.

2.  Hooda, N., Bawa, S., Rana, P.S., B2FSE framework for high dimensional imbalanced data: A case study for toxicity prediction. *Neurocomputing*, 276, 31–41, [https://doi.org/10.1016Zj.neucom.2017.04.081](https://doi.org/10.1016Zj.neucom.2017.04.081), 2018.

3.  Pankratz, D.G., Choi, Y., Imtiaz, U., Usual interstitial pneumonia can be detected in transbronchial biopsies using machine learning. *Ann. Am. Thorac. Soc*., 14, 11, 1646–1654, 2017.

4.  Ohl, F., Jung, M., Xu, C., Stephan, C., Rabien, A., Gene expression studies in prostate cancer tissue. *J. Mol. Med*., 83, 1014–1024, 2005.

5.  Hooda, N., Bawa, S., Rana, P.S., Optimizing fraudulent firm prediction using ensemble machine-learning: A case study of an external audit. *Appl. Artif. Intell*., 34, 1, 20–30, [https://doi.org/10.1080Z08839514.2019.1680182](https://doi.org/10.1080Z08839514.2019.1680182), 2019.

6.  Schierz, A.C., Virtual screening of bioassay data. *J. Cheminf*., 1, 1, 1–21, [https://doi.org/10.1186/1758–2946-1–21](https://doi.org/10.1186/1758–2946-1–21), 2009.

7.  Chakrabarti, P. and Satpathy, B., Class balancing using class balance. *Adv. Comput. Data Sci*., 1045, 13–21, 2019.

8.  Tabari, H. and Talaee, P.H., Multilayer perceptron for reference evapotranspira-tion estimation in a semiarid region. *Neural Comput. Appl*., 23, 341–348, 2013.

9.  Xu, M. and Wang, J.J., *Smote algorithm with locally linear embedding*, US 2009/0097741 A1, 2009.

10.  Ko, J., Baldassano, S.N., Loh, P.L., Kording, K., Machine learning to detect signatures of disease in liquid biopsies - a user’s guide. *Lab Chip*., 18, 395405, 2018.

11.  Kowal, M., Filipczuk, P., Obuchowicz, A., Korbicz, J., Computer-aided diagnosis of breast cancer based on fine needle biopsy microscopic images. *Comput. Biol. Med*., 43, 10, 1563–1572, 2013.

12.  Kuusisto, F., Dutra, I., Nassif, H., Using machine learning to identify benign cases with non-definitive biopsy. *IEEE 15th International Conference on e-Health Networking, Applications and Services*, pp. 283–285, 2013.

13.  iGuiu, J.G., iRibe, E.G., iMansilla, E.B., Automatic classification of mammary biopsy images with machine learning techniques, 1999.

14.  Wang, Y., Xiao, J., Suzek, T.O., Zhang, J., Wang, J., Zhou, Z.G., Han, L.Y., Karapetyan, K., Dracheva, S., Shoemaker, B.A., Bolton, E., Gindulyte, A., Bryant, S.H., PubChem’s BioAssay database. *Nucleic Acids Res*., 40, D1, D400-D412, [https://doi.org/10.1093/nar/gkr1132](https://doi.org/10.1093/nar/gkr1132), 2011.

15.  Stork, C., Wagner, J., Friedrich, N.O., de Bruyn Kops, C., Sicho, M., Kirchmair, J., Hit dexter: A machine learning model for the prediction of frequent hitters. *ChemMedChem*, 13, 6, 564–571, [https://doi.org/10.1002/cmdc.201700673](https://doi.org/10.1002/cmdc.201700673), 2018.

16.  Dash, M. and Liu, H., Feature selection for classification. *Intell. Data Anal*., 1, 1–4, 131–156, 1997.

17.  Agid, R., Sklair-Levy, M., Bloom, A.I., Lieberman, S., CT-guided biopsy with cutting-edge needle for the diagnosis of malign antlymphoma: The experience of 267 biopsies. *Clin. Radiol*., 58, 2, 143–147, 2003.

18.  Snoek, J., Larochelle, H., Adams, R.P., Practical bayesian optimization of machine learning algorithms. *Adv. Neural Inf. Process. Syst*., 25, 29602968, 2012.

19.  Dietterich, T.G., Ensemble methods in machine learning. *Multiple Classifier Systems*, pp. 1–15, 2000.

20.  Alfaro, E., Gamez, M., Garcia, N., Adabag: An R package for classification with boosting and bagging. *J. Stat. Software*, 54, 2, 1–35, 2013.

21.  Bhargava, N., Sharma, G., Bhargava, R., Mathuria, M., Decision tree analysis on j48 algorithm for data mining. *Proc. Int. J. Adv. Res. Comput. Sci. Software Eng*., 3, 6, 1114–1119, 2013.

