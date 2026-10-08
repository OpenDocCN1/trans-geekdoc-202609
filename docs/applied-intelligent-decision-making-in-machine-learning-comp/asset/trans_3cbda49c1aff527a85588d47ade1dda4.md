

## 机器学习中的类智能决策应用

## DT（决策树）

## RF（随机森林）

## XGBoost

## SVR（支持向量回归）

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_198_0.png)

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_198_1.png)

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_198_2.png)

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_198_3.png)

图 9.9 实际与预测 CO2 排放量的散点图。

## 表 9.2：机器学习模型性能评估

| 模型 | MAPE (%) | RMSE² | R² | 耗时 | 准确率 | 排名 |
|---|---|---|---|---|---|---|
| DT | 1.1076 | 5145.3328 | 0.9971 | 1250 次命中用时 2.2 s | 第1 | 第1 | |
| RF | 1.4812 | 8834.8885 | 0.9914 | 1250 次命中用时 1.9 m | 第2 | 第4 | |
| XGBoost | 1.6228 | 9948.4937 | 0.9888 | 1250 次命中用时 39.2 s | 第3 | 第3 | |
| SVR | 4.8045 | 15823.5338 | 0.9742 | 1260 次命中用时 2.6 s | 第4 | 第2 | |

> CO2 排放量（人均吨）。

## 9.4 结论

开发一个稳健、高质量且准确的碳排放预测模型，是为实现《巴黎气候协定》提供环境政策见解的前提。对比不同机器学习算法的预测能力，重点关注碳排放，特别是澳大利亚的碳排放，这一研究值得进一步探讨。本研究应用了许多机器学习技术，如 DT、RF、XGBoost 和 SVR，对澳大利亚的碳排放进行建模。结果显示，DT 的决定系数（R²）高达 99.71%，其次是 RF（R² 为 99.14%）、XGBoost（R² 为 98.88%）和 SVR（R² 为 97.42%）。总体，基于树模型的 MAPE 和 RMSE 最低。总体，DT 模型产生的预测最准确。另一方面，基于核的模型 RBF-SVR 误差相对较高。从计算效率来看，DT 和 SVR 模型比 XGBoost 和 RF 更高效。根据性能评估指标，DT 在本研究利用的其他机器学习技术中排名第一。这意味着，为了准确预测和规划缓解气候变化的政策，澳大利亚的环境规划者应该将决策树作为建模和预测碳排放的技术之一。虽然某些机器学习算法在计算效率方面本可以表现得更好，但在网格搜索过程中，此类算法的组合和参数选择通常计算量非常耗时，因此在某种程度上限制了我们在这些方面的结果。可以使用稳健且新颖的算法来解释数据100% 的变异。本研究针对回归问题，未来的研究可以调查与澳大利亚碳排放相关的分类问题。

## 参考文献

- Acheampong, A. O. (2018). Economic growth, CO$_2$ emissions and energy consumption: What causes when and where? Energy Economics, 74, 677–692. doi:https://doi.org/10.1016/j.eneco.2018.07.022
- Acheampong, A. O. (2019). Modelling for insight: Does development improve environmental quality? Energy Economics, 83, 156–179. doi:https://doi.org/10.1016/j.eneco.2019.06.025
- Acheampong, A. O., & Boatingeng, E. B. (2019). Modelling carbon emission intensity: Application of neural network journal. Journal of Cleaner Production, 225, 833–856. doi:https://doi.org/10.1016/j.jpro.2019.03.353
- Acheampong, A. O., Adams, S., & Boatingeng, E. (2020). Do globalization and renewable energy contribute to carbon emissions in Sub-Saharan Africa? Science of the Total Environment, 677, 436–446. doi:https://doi.org/10.1016/j.scitenv.2019.04.353
- Acheampong, A. O., Amansong, M., & Boatingeng, E. (2020). Financial development mitigate carbon emissions? Evidence from heterogeneous financial economics. Energy Economics, 88, 104768. doi:https://doi.org/10.1016/j.eneco.2020.104768
- Adams, S., & Acheampong, A. (2019). Reducing carbon emissions: The role of renewable energy and democracy. Journal of Cleaner Production, 240, 11845. doi:https://doi.org/10.1016/j.jpro.2019.11845
- Awad, M., & Khanna, R. (2015). Support vector regression. In: Awad & R. Khanna (Eds.), Efficient learning: Theories, concepts, and applications for machine learning systems (pp. 67–80). Berkeley: Springer. [注：OCR 文本碎片]
- Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. In Proceedings of 22nd ACM SIGDD International Conference on Knowledge Discovery and Data Mining (pp. 539–549).
- Climate Council. (2019). Compound cost: How climate change is damaging Australia's economy. Retrieved from https://climatecouncil.org/resources/compound-costs-how-climate-change-damages-australia-economy/
- Das, H., Naik, B., & Behera, H. S. (2018). Classification of diabetes mellitus (DM): A data mining (DM) approach. In: P. Pattnaik, S. Rautaray, H. Das, & J. Nayak, Computing in analytics, and networking (pp. 285–315).
- Das, H., Naik, B., & Behera, H. S. (2020a). An experimental analysis of machine learning algorithms on biomedical data. In: S. Kundu, U. Acharya, & S. Mukherjee, Proceedings of 2nd international conference on communication, devices and computing (pp. 525–539).
- Das, H., Naik, B., & Behera, H. S. (2020b). A hybrid neuro-fuzzy and feature reduction model for classification. In Advances in Fuzzy Systems, 2020, 1–15.
- Das, H., Naik, B., & Behera, H. S. (2020c). Medical disease analysis using neuro-fuzzy with feature extraction method for classification. Informatics in Medicine Unlocked, 18, 10028.
- Das, H., Naik, B., Behera, H., Jaiswal, S., Mahesh, P., & Rout, M. (2020). Biomedical data analysis using neuro-fuzzy model with post-feature reduction. Journal of King Saud University-Computer and Informatics Sciences.
- De, N., Das, H., & Behera, S. (Eds.). (2019). Big data analytics for intelligent healthcare. London: Academic Press.
- Ducker, H. C., Kaufman, L., Smola, A. J., & Vapnik, V. (1997). Support vector regression machine. Presented at the Advances in Neural Processing Systems, Denver, CO.
- Falla, L., & Pukainc, L. (2015). Quantitative modelling in economics with artificial financial networks. Economics of Finance and Commerce, 34, 194–201. doi:https://doi.org/10.1016/S2222-5621(15)01619-6
- Gallo, C., Conte, F., & Fiore, M. (2014). A neural network model for CO2 emissions. Agris On-line Papers in Economics and Informatics, 6(2), 31.
- Lam, K.-C., Yu, Y., & Lam, K. Y. (2008). An artificial neural network and entropy model for residential property forecasting in Hong Kong. Journal of Property Research, 25(4), 321–342.
- Morano, P., Tajani, F., & Torre, C. (2015). Artificial intelligence in property values application of artificial neural networks for housing appraisal. Advances in Environmental Science and Energy, Planning, 23–29.
- Ndev. (2019). Training 2019 Q3 report. Retrieved from https://ndvironment.com.au/training-2-degrees-fy19-q3/
- O'Neill, B. C., & Desai, M. (2005). Accuracy of predictions of US energy consumption. Energy Policy, 33(8), 979–993.
- Rodriguez-Galian, V., Sanchez-Castillo, M., Chica-Olmo, M., & Chica-Rivas, M. (2015). Machine learning predictive methods for mineral prospecting: An evaluation of neural networks, random forest, regression trees and support vector machines. Ore Reviews, 71, 804–818.
- Rout, M., Jena, A. K., Rout, J. K., & Das, H. (2020). Teaching-learning optimization based caseload low-complexity neural network model for exchange rates forecasting. In: S. Sathyapat, V. Bhatgey, J. Mohanty, & S. Udga (Eds.), Smart intelligent computing and applications (pp. 635–645). Springer: Springer.
- Stamenkovic, L. J., Atanasjevic, J. D., Risti, M. Đ., Perić-Grujić, A. A., & Pocajt, V. V. (2015). Modeling of methane emissions using artificial neural network approach. Journal of the Serbian Chemical Society, 80(3), 421–433.
- Tsai, C.-F., & Chiou, Y.-J. (2009). Earnings management prediction: A pilot study of combining neural networks and decision trees. Expert Systems with Applications, 36(3), 7183–7191.

