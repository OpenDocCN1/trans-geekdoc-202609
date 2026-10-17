
| MAE | MSE | RMSE | R2-score |
|---|---|---|---|---|
| 人工神经网络 | 0.16 | 0.7 | 0.340 | 0.86 |
| 多输出 | 0.19 | 0.6 | 0.230 | 0.84 |
| TensorFlow-Keras | 0.12 | 0.54 | 0.210 | 0.87 |

![](img/081dc7f102a3793cb08980a6e19b8f17_81_0.png)
![](img/081dc7f102a3793cb08980a6e19b8f17_81_1.png)
![](img/081dc7f102a3793cb08980a6e19b8f17_81_2.png)
![](img/081dc7f102a3793cb08980a6e19b8f17_81_3.png)
![](img/081dc7f102a3793cb08980a6e19b8f17_81_4.png)
![](img/081dc7f102a3793cb08980a6e19b8f17_81_5.png)

**图 2.23** 分类任务中机器学习方法的精确率和召回率得分。(a) 逻辑回归。(b) K-最近邻算法。(c) 决策树。(d) 支持向量分类。(e) 随机森林。(f) 朴素贝叶斯。

从图 2.23 可以看出，与其他类别相比，类别 1 的准确率和召回率更高。这可能是因为类别 1 的样本量比其他类别多。其他性能参数列在表 2.4 中。

# 表 2.4 分类机器学习模型的性能参数。

| 准确率 | Cohen kappa 分 | 马修斯系数 | 平均精确率 | 平均召回率 | F1 分 |
|---|---|---|---|---|---|
| 逻辑回归 | 76.54 | 51.74 | 54.78 | 61.54 | 78.32 | 68.92 |
| K-最近邻 | 81.33 | 43.56 | 44.80 | 64.42 | 51.19 | 57.04 |
| 决策树 | 84.76 | 60.58 | 60.62 | 68.50 | 67.44 | 67.97 |
| 支持向量分类 | 85.27 | 61.08 | 61.09 | 71.41 | 69.48 | 70.43 |
| 随机森林 | 89.21 | 68.79 | 69.61 | 83.75 | 67.75 | 74.90 |
| 朴素贝叶斯 | 74.82 | 50.68 | 52.64 | 59.44 | 78.12 | 67.81 |

根据表 2.4 列出的性能衡量标准，在比较上述机器学习模型时，显然随机森林优于其他模型。本研究采用了三种深度学习网络：前馈网络、LSTM 和基于 CNN 的。所有模型均使用稀疏交叉熵损失、SGD 优化器和准确率指标。所有模型训练了 200 个 epoch，三个模型的性能指标列于表 2.5，观察到与其他分类模型相比，前馈网络表现良好。

## 2.6 建议

本文有助于读者理解机器学习和深度学习算法。为了方便起见，建议读者使用同一数据集同时进行分类任务和回归任务的操作。此外，如果我们的数据集包含缺失值或类别不平衡，结果可能会有所不同。

## 2.7 结论

我们使用房价数据集，尝试评估机器学习模型和深度学习模型的性能。本工作的主要目标是使用各种性能指标对模型进行评估，因此模型得到了优化以获得更好的结果。在评估 MAE、MSE 和 R2 分等性能指标时，发现随机森林算法在机器学习模型中表现更好，基于 Tensorflow-Keras 的模型在深度学习模型中表现更好。计算了准确率、Cohen kappa 分、马修斯相关系数、平均精确率和平均召回率六项性能参数，前馈神经网络在机器学习（ML）和深度学习（DL）模型中表现良好。

## 表 2.5 分类深度学习模型的性能参数。

| | Cohen kappa 分 | 马修斯系数 | 平均精确率 | 平均召回率 | F1 分 |
|---|---|---|---|---|---|
| 前馈神经网络 | 89.52 | 69.54 | 70.68 | 83.39 | 68.64 | 75.23 |
| LSTM | 82.02 | 44.64 | 46.20 | 68.75 | 48.50 | 56.87 |
| CNN | 84.76 | 60.58 | 60.62 | 68.50 | 67.44 | 67.97 |

# 深度学习在网络物联网系统与安全中的收敛

还发现深度学习模型在回归和分类测试中均优于机器学习模型。

## 参考文献

1. Sewak, M., Sahay, S.K., Rathore, H., 恶意软件检测深度学习与经典机器学习算法比较，in：19th IEEE/ACIS International Conference on Software Engineering, Artificial Intelligence, Networking and Parallel/Distributed Computing (SNPD), pp. 293–296, 2018.

2. Doleck, T., Lemay, D.J., Basnet, R.B., Bazelis, P., 教育预测分析：深度学习框架比较。Educ. Inf. Technol., 25, 3, 1951–1963, 2020.

3. Dong, B. and Wang, X., 网络入侵检测深度学习与传统方法的比较，in：8th International Conference on Communication Softw and Networks Comparison, pp. 581–585, 2016.

4. Liu, Y. et al., 航空图像鸟类识别深度学习技术性能比较，in：Proceedings -2018 IEEE 3rd International Conference on Data Science in Cyberspace, DSC 2018, pp. 317–324.

5. Delany, S.J., Chen, H., McKeever, S., 社交媒体垃圾内容经典深度学习技术比较，in：Social Informatics, pp. 117–133, 2018.

6. Turkoglu, I. and Alakus, T.B., 预测 COVID-19 感染深度学习方法比较。Chaos Solitons Fractals, 140, 1–8, November 2020.

7. Ghosarkar, N.N. and Dhage, S.N., 使用线性回归预测房地产价值，in：2018 4th International Conference on Computing, Communication and Automation, ICCUBA 2018, pp. 1–5, 2018.

8. Phan, T.D., 使用机器学习算法进行房价预测：墨尔本市案例，in：International Conference on Machine Learning and Data Engineering. ICMLDE 2018, pp. 8–13, 2019.

9. Nahib, I., Suryanta, J., Analysis, R., Daoud, J., II, 使用多元回归模型预测房地产价值。IOP Conf. Ser. Mater. Sci. Eng., 4, 1–7, 2017.

10. Varma, A., 使用机器学习和神经网络进行房价预测，in：第二届创新通信与计算技术会议 (ICCICCT), pp. 1936–1939, 2020.

11. Madhuri, C.H.R., Anuradha, G., Pujitha, M.V., 使用回归技术进行房价预测：比较研究，in：IEEE 6th International Conference on smart structures and systems ICCSS 2019, pp. 1–5, 2019.

12. Kashyap, I., Panda, S.P., Bansal, U., Narang, A., Sachdeva, A., 回归技术与销售预测的实证分析 Empirical

# ML 和 DL 技术的性能评估 63

基于房价和薪资预测的回归技术分析。IOP Conf. Ser. Mater. Sci. Eng., 1022, 43, 1–13, 2021.

- 13. Rawool, A.G., Rogey, D.V., Rane, S.G., Vinayak, A., 使用机器学习进行房价预测。IRE Journals, 4, 29–33, 2021.

- 14. Kaggle, 房价预测 - 高级回归技术。https://www.kaggle.com/house-prices-advanced-regression-techniques/data (访问于 2021 年 6 月 10 日)。

- 15. Bold Bi, 数据可视化：重要性和收益。https://www.bodldbi.com/blog/data-visualization-importance-and-benefits (访问于 2021 年 6 月 10 日)。

- 16. Analytiks, 数据可视化的重要性。https://analytiks.com/importance-of-data-visualization/ (访问于 2021 年 6 月 10 日)。

- 17. 直方图定义。https://www.investopedia.com/terms/h/histogram (访问于 2021 年 6 月 10 日)。

- 18. Statistics How To, 箱线图（箱体和须线）：如何读取以及在 excel、TI-83 中如何制作，https://www.statisticshowto.com/probability-and-statistics/descriptive-statistics/box-plot/ (访问于 2021 年 6 月 10 日)。

- 19. 分位数分位数图，https://www.nist.gov/div988/handbook/eda/section3qqqplot (访问于 2021 年 6 月 10 日)。

- 20. 散点图 - 概述。https://corporatefinanceinstitute.com/resources/knowledge/scatter-plot/ (访问于 2021 年 6 月 10 日)。

- 21. 计数点图。https://seaborn.pydata.org/generated/seaborn.countplot.html (访问于 2021 年 6 月 10 日)。

- 22. 机器学习的数据准备。https://www.datarobot.com/wiki/data-preparation/ (访问于 2021 年 6 月 10 日)。

- 23. Al-Helali, B., Chen, Q., Xue, Zhang, M., 一种用于缺失值符号回归的混合 GP-KNN 填补，在 AI: 2018: 人工智能进展，页码 345–357，2018。

- 24. Santurkar, S., Tsipras, D., Ilyas, A., Madry, A., 归一化是如何优化的？在第 32 次神经信息处理系统会议 (NeurIPS 2018)，2018 年 5 月，43，页码 1–26，可用：https://arxiv.org/abs/1805.11604。

- 25. Podkar, K., Parwala, T.S., Pai, C.D., 神经网络分类器中类别编码技术的比较研究。Int. J. Comput. Appl., 175, 4–7, 2019。

- 26. Vining, G., Montgomery, D.C., Peck, E.A., 线性回归分析导论，John Wiley & Sons，2012。

- 27. Caramaux

- 28. Li, L., Chen, S., Yang, C., Meng, F., Sigirmis, N., 使用随机森林算法根据环境参数和相对面积指数预测植物蒸腾作用。J. Clean. Prod., 261, 44, 1–13, 2020. doi: https://doi.org/10.1016/j.jclepro.2020.121136

# DL 在网络-IoT 系统与安全中的收敛

- 29. Sarkar, A., Sai, K.K., Prakash, A., Veera, G., Sai, V., Kaur, M., 关于贷款逾期预测的研究论文。Int. Res. Eng. Technol. 8, 4, 715–722, 2021。

- 30. Taherkhani, A., Cosma, G., McGinnity, T.M., AdaBoost-CNN: 一种用于通过迁移学习分类多类不平衡数据集的卷积神经网络自适应提升算法。Neurocomputing, 404, 351–366, 2020。

- 31. 提升算法。https://towardsdatascience.com/boosting-algorithms-explained-d38f5e6f30 (访问于 2021 年 6 月 10 日)。

- 32. Cai, J., Xu, K., Zhu, Y., Hu, F, Li, L., 基于梯度提升回归和随机森林的生态碳交换预测与分析。Appl. Energy, 262, 114566, 2020。

- 33. 梯度提升回归。http://deepnote.me/2019/08/25/datascience-machine-learning-with-tree-models-in-python/ (访问于 2021 年 6 月 11 日)。

- 34. Jitta, S, Sajeev M, Haribaabu, V., Arun, S., 用于情绪预测的 ECG 信号分析。Adv. Res. Dyn. Control. Syst., 12, 896–902, 2020。

- 35. medium.com, 支持向量回归。https://medium.com/essence-of-regression/intuition-behind-support-vector-regression-3601f67 (访问于 2021 年 6 月 11 日)。

- 36. Pujari, S., Ramakrishna, A., Padal, K., 黄麻增强复合材料吸水性的线性回归比较。Mater Today., 4, 2, 1626–1633, 2017. doi:https://doi.org/10.1016/j.matpr.2017.0201。

- 37. 神经网络。https://www.javatpoint.com/artificial-neural-network (访问于 2021 年 6 月 11 日)。

- 38. Bilgil, M., Tosun, E., Aydin, K., 生物柴油发动机的线性回归与神经网络模型比较。Alex. Eng. J., 5, 4, 3081–3089, 2016。

- 39. Xu, D., Shi, Y., Tsang, I.W., Ong, Y.S., Gong, C., 多输出学习。IEEE Net. Learn., 31, 7, 2409–2429, 2020。

- 40. 多输出回归。https://towardsdatascience.com/chained-multioutput-regression-with-scikit-learn-31b5a259c4 (访问于 2021 年 6 月 12 日)。

- 41. Géron, A., Scikit-Learn, Keras 和 TensorFlow 机器学习：构建智能系统的概念、工具和技术。O'Reilly, 美国，2019。

- 42. Basis, R., Classifier, F., Mapping, S., 核逻辑回归、径基函数、多项贝叶斯和逻辑树闪电敏感性的比较研究。Water, 12, 239–260, 2020。

- 43. 逻辑回归。https://towardsdatascience.com/binary-classification-with-logistic-regression-31b5a259c4 (访问于 2021 年 6 月 12 日)。

# ML 和 DL 技术的性能评估

- 44. Rao, C.S. 等，使用决策树分类器的孤立性网膜下出血患者死亡率预测：基于损伤系统的回顾性分析。Int. Environ. Public Health, 14, 11–10, 2017。

- 45. 决策树算法。https://www.kndgets.com/2020/01/decision-tree-implemented.html (访问于 2021 年 6 月 12 日)。

- 46. Mursalin, Zhang, Y., Chen, Y., Chawla, N.V., 使用改进的相关性特征选择随机森林分类器自动检测癫痫发作。Neurocomputing, 241, 204–214, 2017。

- 47. 随机森林分类。https://medium.com/random-forest-classification-and-implementation-d5d4dead0 (访问于 2021 年 6 月 12 日)。

- 48. Feng, X., Li, S., Yuan, C., Zheng, P., Sun, Y., 使用朴素贝叶斯分类器的坡稳定性预测。KSCE J. Civ. Eng., 22, 3, 941–950, 2018。

- 49. Singh, A., Halalgume, M.N., Lakshmanathan, R., 不同类型对随机森林、朴素贝叶斯和近邻算法分类器性能的影响。Int. Adv. Comput. Sci. Appl., 8, 12–1–11, 2017。
