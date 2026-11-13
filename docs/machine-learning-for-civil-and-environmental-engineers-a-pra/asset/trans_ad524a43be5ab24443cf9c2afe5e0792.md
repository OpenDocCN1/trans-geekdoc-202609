

## 表 5.6（续）

| 序号 指标 | Python 代码/包 | R 代码/包 |
| :--- | :--- | :--- |
| 聚类 | | |
| 1 肘法 [55, 56] | ```
#K-means using Euclidean distance/distortion.
distortions = []

#Total number of clusters.
K = range(1,10)

#Calculate distortion per cluster.
for k in K:
    kmeanModel = KMeans(n_clusters=k).fit(X)
    kmeanModel.fit(X)
    distortions.append(sum(np.min(cdist(X, kmeanModel.cluster_centers_, 'euclidean'), axis=1)) / X.shape[0])

#Plotting.
plt.plot(K, distortions, 'bx-')
plt.xlabel('k-clusters')
plt.ylabel('Distortion')
plt.xlim([0, 10])
``` | ```
#Package for Plotting Number of Cluster calculation:
> install.packages("NbClust")
> library("NbClust")
> set.seed(1234)
c <- NbClust(df, min.nc=2, max.nc=15, method="kmeans")
``` |
| 2 轮廓系数 | ```
from sklearn.metrics import silhouette_samples, silhouette_score

#Compute the silhouette scores for each sample.
sample_silhouette_values = silhouette_samples(X, cluster_labels)

#The silhouette_score gives the average value for all the samples.
silhouette_avg = silhouette_score(X, cluster_labels)
``` | ```
#Package for Plotting clustering quality in Dataframe:
> install.packages("cluster")
> install.packages("vegan")
> library("cluster")
> library("vegan")
dis = vegdist(data)
res = pam(dis, 5) # or whatever your choice of clustering algorithm is
sil = silhouette(res$clustering, dis) # or use your cluster vector of yours
plot(sil)
``` |

- 从 SciKitLearn.org、cran.r-project.org、rdocumentation.org 以及 https://github.com/mfrasc60/Metrics/blob/master/R/regression.R 等开源资源整理而成。在 Python 中应用指标时，在指标后紧跟插入 (actual, predicted)。例如，metric (actual, predicted)。你还可以使用 print ("Root Mean Square Error:", RMSE) 打印指标的值。

## 参考文献

- 1 Kodur, V.K.R., Garlock, M., and Iwankiw, N. (2011). 火灾中的结构：现状、研究与培训需求. Fire Technol. 48: 825–839. doi: 10.1007/s10694-011-0247-4.
- 2 Naser, M.Z. (2019). 基于人工智能的耐火性能评估——以木结构为例. Fire Saf. J. 105: 1–18. doi: 10.1016/j.firesaf.2019.02.002.
- 3 Domingos, P. (2012). 关于机器学习需要知道的几件有用的事情. Commun. ACM. doi: 10.1145/2347736.2347755.
- 4 Schmidt, M.D. and Lipson, H. (2010). 年龄-适应度帕累托优化. doi: 10.1145/1830483.1830584.
- 5 Cremonesi, P., Koren, Y., and Turrin, R. (2010). 推荐算法在 Top-N 推荐任务中的性能：类别和主题描述符. RecSys '10: 第四届 ACM 推荐系统会议论文集.
- 6 Laszczyk, M. and Myszkowski, P.B. (2019). 多目标优化质量度量调查：构建多目标质量度量的互补集. Swarm Evol. Comput. 48: 109–133. doi: 10.1016/j.swevo.2019.04.001.
- 7 Willmott, C.J. and Matsuura, K. (2005). 在评估平均模型性能时，平均绝对误差（MAE）相对于均方根误差（RMSE）的优势. Clim. Res. 30. doi: 10.3354/cr030079.
- 8 Makridakis, S. (1993). 精度度量：理论与实际问题. Int. J. Forecast. 9. doi: 10.1016/0169-2070(93)90079-3.
- 9 Ferreira, C. (2001). 基因表达编程：一种用于求解问题的新自适应算法. Gene Expr. Program. a New Adapt. Algorithm Solving Probl. Complex Syst. 13. https://www.semanticscholar.org/paper/Gene-Expression-Programming-%3A-a-New-Adaptive-for-Ferreira/323b2a24c2584ca8e81c5b5bf655ae3f40fae (访问于 2019 年 3 月 16 日).
- 10 D. Pollock (1999). 时间序列分析、信号处理与动力学手册. 地质学、计算机科学. https://www.elsevier.com/books/handbook-of-time-series-analysis-signal-processing-and-dynamics/pollock/978-0-12-560990-6. doi: 10.1016/b978-0-12-560990-6.x5000-3.
- 11 Hyndman, R.J. and Koehler, A.B. (2006). 再述预测精度度量. Int. J. Forecast. 22. doi: 10.1016/j.ijforecast.2006.03.001.
- 12 Shcherbakov, M.V., Brebels, A., Shcherbakova, N.L. 等. (2013). 预测误差度量综述. World Appl. Sci. J. 24.
- 13 Poli, A.A. and Cirillo, M.C. (1993). 关于在分散模型性能评估中使用归一化均方误差. Atmos. Environ. A-Gen. Top. 27. doi: 10.1016/0960-1686(93)90410-Z.
- 14 Armstrong, J.S. and Collopy, F. (1992). 用于推广预测方法的误差度量：实证比较. Int. J. Forecast. 8. doi: 10.1016/0169-2070(92)90008-W.
- 15 Sadat Hosseini, A., Hajikarimi, P., Gandomi, M. 等. (2021). 基于遗传规划的改性沥青结合料粘弹性行为建模. Constr. Build. Mater. 286. doi: 10.1016/j.conbuildmat.2021.122954.
- 16 Bain, L.J. (1967). 应用回归分析. Technometrics 9. doi: 10.1080/00401706.1967.10490452.
- 17 Smith, G. (1986). 土木工程概率与统计. London: Collins.
- 18 Golbraikh, A., Shen, M., Xiao, Z. 等. (2003). 为开发经过验证的 QSAR 模型而合理选择训练集和测试集. J. Comput. Aided. Mol. Des. 17: 241–253. doi: 10.1023/A:1025386326946.
- 19 Roy, P.P. and Roy, K. (2008). 关于偏最小二乘回归模型中变量选择的若干方面. QSAR Comb. Sci. 27: 302–313. doi: 10.1002/qsar.200710043.
- 20 Frank, I. and Todeschini, R. (1994). 数据分析手册. Elsevier. https://books.google.com/books?hl=en&lr=&id=SXEpB0H6L3YC&oi=fnd&pg=PP1&ots=zfmIRO_XO5&sig=dSX6KJdkuav5zRnXaUdcftGSn2k (访问于 2019 年 6 月 21 日).
- 21 Gandomi, A.H., Yun, G.J., and Alavi, A.H. (2013). 钢筋混凝土深梁抗剪承载力建模的进化方法. Mater. Struct. Constr. 46. doi: 10.1617/s11527-013-0039-z.
- 22 Cheng, M.Y., Firdausi, P.M., and Prayogo, D. (2014). 使用遗传加权金字塔运算树（GWPOT）进行高性能混凝土抗压强度预测. Eng. Appl. Artif. Intell. 29. doi: 10.1016/j.engappai.2013.11.014.
- 23 Alwanas, A.A.H., Al-Musawi, A.A., Salih, S.Q. 等. (2019). 梁柱节点连接的承载能力与失效模式模拟：自调整机器学习模型的应用. Eng. Struct. 194. 10.1016/j.engstruct.2019.05.048.
- 24 Chou, J.S., Tsai, C.F., Pham, A.D., and Lu, Y.H. (2014). 混凝土强度模拟中的机器学习：多国数据分析. Constr. Build. Mater. 73. doi: 10.1016/j.conbuildmat.2014.09.054.
- 25 Nguyen, T.T., Pham Duy, H., Pham Thanh, T., and Vu, H.H. (2020). 基于人工智能的纤维增强高强度自密实混凝土抗压强度评估. Adv. Civ. Eng. 2020. doi: 10.1155/2020/3012139.
- 26 Sultana, N., Zakir Hossain, S.M., Alam, M.S. 等. (2020). 黄麻纤维增强混凝土力学性能比较预测的软计算方法. Adv. Eng. Softw. 149. doi: 10.1016/j.advengsoft.2020.102887.
- 27 Willmott, C.J. (1981). 关于模型验证. Phys. Geogr. 2. doi: 10.1080/02723646.1981.10642213.
- 28 Nash, J.E. and Sutcliffe, J.V. (1970). 基于概念模型的河流流量预测 第一部分——原则讨论. J. Hydrol. 10. doi: 10.1016/0022-1694(70)90255-6.
- 29 Gupta, H.V., Kling, H., Yilmaz, K.K., and Martinez, G.F. (2009). 均方误差和 NSE 性能标准的分解：改进水文建模的启示. J. Hydrol. 377. doi: 10.1016/j.jhydrol.2009.08.003.
- 30 Knoben, W.J.M., Freer, J.E., and Woods, R.A. (2019). 技术说明：固有基准与否？比较 Nash-Sutcliffe 和 Kling-Gupta 效率得分. Hydrol. Earth Syst. Sci. 23. doi: 10.5194/hess-23-4323-2019.
- 31 Huang, H. and Burton, H.V. (2019). 基于机器学习的有填充墙钢筋混凝土框架面内失效模式分类. J. Build. Eng. 25. doi: 10.1016/j.jobe.2019.100767.
- 32 Bhowan, U., Johnston, M., and Zhang, M. (2011). 遗传规划中用于不平衡数据分类的新适应度函数开发. IEEE Trans. Syst. Man Cybern B: Cybern. 42. doi: 10.1109/TSMCB.2011.2167144.
- 33 Boughorbel, S., Jarray, F., and El-Anbari, M. (2017). 基于马修斯相关系数度量的不平衡数据最优分类器. PLoS One 12. doi: 10.1371/journal.pone.0177678.
- 34 Tharwat, A. (2020). 分类评估方法. Appl. Comput. Inform. 17. doi: 10.1016/j.aci.2018.08.003.
- 35 Caruana, R. and Niculescu-Mizil, A. (2004). 度量空间中的数据挖掘：监督学习性能标准的实证分析. KDD ’04: 第十届 ACM SIGKDD 知识发现与数据挖掘国际会议论文集. doi: 10.1145/1014052.1014063.
- 36 Jurman, G., Riccadonna, S., and Furlanello, C. (2012). 多类预测中 MCC 和 CEN 误差度量的比较. PLoS One 7. doi: 10.1371/journal.pone.0041882.
- 37 Powers, D.M.W. (2011). 评估：从精确率、召回率和 F 值到 ROC、知情度、显著性和相关性. J. Mach. Learn. Technol. doi: 10.48550/arXiv.2010.16061.
- 38 Bradley, A.P. (1997). 机器学习算法评估中 ROC 曲线下面积的使用. Pattern Recognit. 30. doi: 10.1016/S0031-3203(96)00142-2.
- 39 Hanley, J.A. and McNeil, B.J. (1982). 接收者操作特征（ROC）曲线下面积的含义与应用. Radiology 143. doi: 10.1148/radiology.143.1.7063747.
- 40 Zhang, Y., Burton, H.V., Sun, H., and Shokrabadi, M. (2018). 震后结构安全评估的机器学习框架. Struct. Saf. 72. doi: 10.1016/j.strunsafe.2017.12.001.
- 41 Davis, J. and Goadrich, M. (2006). Precision-Recall 曲线与 ROC 曲线的关系. ICML '06: 第 23 届国际机器学习会议论文集. doi: 10.1145/1143844.1143874.
- 42 Bi, J. and Bennett, K. (2003). 回归误差特征曲线. 2003 年第 20 届国际机器学习会议.
- 43 Zhang, M. and Smart, W. (2006). 在遗传规划中使用高斯分布构建多类对象分类的适应度函数. Pattern Recognit. Lett. 27. doi: 10.1016/j.patrec.2005.07.024.
- 44 Kocher, M. and Savoy, J. (2017). 作者画像中的距离度量. Inf. Process. Manag. 53. doi: 10.1016/j.ipm.2017.04.004.
- 45 Patel, B.V. and Meshram, B.B. (2012). 基于内容的视频检索系统. Int. J. UbiComp. 3. doi: 10.5121/iju.2012.3202.
- 46 Giusti, R. and Batista, G.E.A.P.A. (2013). 时间序列分类中差异度量的实证比较. 2013 年巴西智能系统会议. doi: 10.1109/BRACIS.2013.22.
- 47 Vuk, M. and Curk, T. (2006). ROC 曲线、升力图和校准图. Metod. Zv.
- 48 Brodersen, K.H., Ong, C.S., Stephan, K.E., and Buhmann, J.M. (2010). 平衡准确率及其后验分布. 2010 年第 20 届国际模式识别会议. doi: 10.1109/ICPR.2010.764.
- 49 Cohen, J. (1960). 名目量表的一致性系数. Educ. Psychol. Meas. 20. doi: 10.1177/001316446002000104.
- 50 Artstein, R. and Poesio, M. (2008). 计算语言学中的编码者间一致性. Comput. Linguist. 34. doi: 10.1162/coli.07-034-R2.
- 51 Destercke, S. (2014). 基于概率集的多标签预测：汉明损失情况. IPMU 2014: 基于知识系统的不确定性信息处理与管理. doi: 10.1007/978-3-319-08855-6_50.
- 52 Cząjkowski, M. and Kretowski, M. (2019). 基因表达数据挖掘中的决策树欠拟合：一种进化多测试树方法. Expert Syst. Appl. 137. doi: 10.1016/J.ESWA.2019.07.019.
- 53 Devarriya, D., Gulati, C., Mansharmani, V. 等. (2020). 使用遗传规划中新型适应度函数的不平衡乳腺癌数据分类. Expert Syst. Appl. 140: 112866. doi: 10.1016/J.ESWA.2019.112866.
- 54 Rousseeuw, P.J. (1987). 轮廓：聚类分析解释和验证的图形辅助工具. J. Comput. Appl. Math. 20. doi: 10.1016/0377-0427(87)90125-7.
- 55 Thorndike, R.L. (1953). 谁属于这个家族？ Psychometrika 18. doi: 10.1007/BF02289263.
- 56 Nainggolan, R., Perangin-angin, R., Simarmata, E., and Tarigan, A.F. (2018). 使用肘法优化的平方误差和（SSE）提高 K-均值聚类性能. J. Phys. Conf. Ser. 1361: 12015. doi: 10.1088/1742-6596/1361/1/012015.
- 57 Arbelaitz, O., Gurrutxaga, I., Muguerza, J. 等. (2013). 聚类有效性指标的广泛比较研究. Pattern Recognit. 46: 243–256. doi: 10.1016/j.patcog.2012.07.021.
- 58 Naser, M.Z. (2023 年 1 月 1 日). 我们是否需要异域模型？用于解决准确率-能耗权衡以实现绿色机器学习的工程度量. J. Clean. Prod. 382: 135334. doi: 10.1016/j.jclepro.2022.135334.

