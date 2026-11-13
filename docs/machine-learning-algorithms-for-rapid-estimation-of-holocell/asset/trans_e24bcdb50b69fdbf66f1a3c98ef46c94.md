

![](img/e15c3a13b491ae6ef05b67702b1cf3da_6_0.png)

图 5. 正则化 HCP 模型中的测量值和预测值。

![](img/e15c3a13b491ae6ef05b67702b1cf3da_6_1.png)

图 6. 经典机器学习 HCP 模型中的测量值和预测值。

![](img/e15c3a13b491ae6ef05b67702b1cf3da_6_2.png)

图 7. 高级 GBM HCP 模型中的测量值和预测值。

在树生长过程中寻找分割点，显著提升了建模效率。但是，效率的普遍提高伴随着特征数量的减少以及对小梯度实例的随机丢弃，这在开发 LightGBM 模型时可能会略微降低预测精度（Ke et al., 2017）。由于本研究中的数据集数量与机器学习任务中常用的数据集相比并不大，因此建模效率不如预测精度重要。因此，在本研究中，由于上述优势，获得了更高预测精度的 XGBoost 算法被赋予最高优先级。此外，CatBoost 构建的 HCP 模型的预测精度与 XGBoost 相近，但在木质素含量预测模型中略低于 XGBoost。这可能是由于从拉曼光谱中提取的特征具有不同的数学特性。因为与木质素相关峰相比，全纤维素相关峰的位置和强度差异很大，发现与全纤维素相关的提取特征所包含的标注输入变量数量多于与木质素相关的特征。CatBoost 算法的特点是引入了有序增强，该方法擅长避免由目标泄漏引起的过拟合，从而随之提升模型的预测精度（Prokhorenkova et al., 2018）。因此，CatBoost 的这一有利特性将有助于提高定量模型的预测精度。综上所述，基于拉曼特征估算全纤维素含量时，XGBoost 和 CatBoost 均优于所有其他模型。在经典机器学习算法组中，为构建相应预测模型而选择最优算法的结果不受两个数据集差异的影响，即提取的与木质素相关的拉曼特征或与全纤维素相关的拉曼特征。然而，在高级 GBM 算法组中，预测全纤维素含量和木质素含量时最优算法的选择结果不一致，这是由于建模数据特性各异所致。因此，在执行 GBM 算法组中最优算法的选择时，不应忽略数据矩阵之间的差异。

因此，拉曼特征与高级 GBM 算法相结合，可以开发出更鲁棒、更精确的模型，用于预测杨树木材的全纤维素含量。然而，可能还会遇到其他木质纤维素资源，包括其他被子植物和裸子植物，如竹子、藤类以及全纤维素化学结构和含量不同的农业残余物，这些尚未被研究过。但本研究描绘了通用方法论，当面对不同类型的材料时，模型需要进行调整和修改，以分别适应不同的木质纤维素资源。

## 4. 结论

由正则化算法、经典机器学习算法和高级 GBM 算法构建的全部九个模型均已成功预测了全纤维素含量。高级 GBM 算法在训练和测试过程中均优于所有模型。特别是，CatBoost 和 XGBoost 模型的测试 R<sup>2</sup> 预测精度为 0.93，测试 RMSE 约为 0.28%，在全部九个算法中居于首位。因此，很明显，傅里叶变换拉曼光谱结合机器学习算法是一种有前景的方法，可以在无需复杂繁琐的化学实验的情况下，准确且环保地预测全纤维素含量。

## CRediT 作者贡献声明

Wenli Gao: 撰写-原始草稿和审阅，形式分析，方法学，软件；Liang Zhou: 撰写-审阅和编辑，概念化，方法学，监督；Shengquan Liu: 监督，资金获取；Ying Guan: 概念化，方法学；Hui Gao: 概念化，方法学；Jianjun Hu: 撰写-审阅和编辑。

## 竞争利益声明

作者声明，他们没有已知的竞争性财务利益或个人关系，这些利益或关系可能会影响本文所报告的工作。

## 致谢

该项工作得到国家重点研发计划（2017YFD0600201）；中国国家自然科学基金（编号：31770596）；生物纤维与环保纺织品国家重点实验室（资助编号：K2019-13）的支持。

## 参考文献

- Adler, J., & Parmryd, I. (2010). 基于相关性量化共定位：Pearson 相关系数优于 Mander 重合系数。细胞计量学 Part A, 77(8), 733–742. https://doi.org/10.1002/CYTO.A.20896

- Agarwal, U. P. (2009). 木材和木浆纤维的拉曼光谱表征。木质纤维素材料表征，17–35. https://doi.org/10.1002/9781444305425.ch2

- Agarwal, U. P. (2019). 基于拉曼光谱的纤维素和木质素含量分析：现状综述。分子，24(9). https://doi.org/10.3390/MOLECULES24091659

- Agarwal, U. P., & Atalla, R. H. (2010). 在线振动光谱。振动光谱，1(1), 103–136. https://doi.org/10.1016/0924-2031(90)80020-5

- Agarwal, U. P., & Ralph, S. A. (1997). 木材的 FT-Raman 光谱：识别黑云杉（Picea mariana）光谱中木质素和碳水化合物聚合物的贡献。应用光谱学，51(11), 1648–1655. https://doi.org/10.1366/000370297779399316

- Agarwal, U. P., & Ralph, S. A. (2012). 基于近红外 FT-Raman 光谱的禾本科植物木质素定量。载于《美国化学学会论文分析》（第 243 页）。

- Agarwal, U. P., Ralph, S. A., Reiner, R. S., & Baez, C. (2018). 一种区分有序相与结晶相的新纤维素结晶度估计方法。碳水化合物聚合物，190(2 月), 262–270. https://doi.org/10.1016/j.carbpol.2018.03.003

- Agarwal, U. P., Reiner, R. S., & Ralph, S. A. (2010). 基于 FT-Raman 光谱的纤维素 I 结晶度测定：一元法和多元法。纤维素，17(4), 721–733. https://doi.org/10.1007/s10570-010-9420-2

- Awad, M., & Khanna, R. (2015). 支持向量回归。载于 M. Awad & R. Khanna (编), 《高效学习机器：工程师和系统设计师的理论、概念与应用》（第 67–80 页）。Apress. https://doi.org/10.1007/978-1-4302-5990-9_4

- Basu, P. (2018). 第 14 章 - 分析技术。载于 P. Basu (编), 《生物质气化、热解与焙烧》（第 3 版, 第 479–495 页）。Academic Press. https://doi.org/10.1016/B978-0-12-811992-0.00023-6.

- Chen, T., & Guestrin, C. (2016). XGBoost：一种可扩展的树提升系统。知识发现与数据挖掘，785–794. https://doi.org/10.1145/2939672.2939785

- Dassi-Gnaba, H., Oussar, Y., Merlan, M., Ditchi, T., Géron, E., & Holé, S. (2018). 基于监督分类的堆放木片含水率识别。木材科学与技术，52(5), 1195–1211. https://doi.org/10.1007/s00226-018-1020-3

- Dorogush, A. V., Ershov, V., & Gulin, A. (2018). CatBoost：支持类别特征的梯度提升。https://arxiv.org/pdf/1810.11363.pdf。LK - https://academic.microsoft.com/paper/2898227265.

- Ehrhart, T., Palma, P., Schubert, M., Steiger, R., & Frangi, A. (2021). 基于图像局部纤维方向数据预测欧洲山毛榉（Fagus sylvatica L.）板材的强度。木材科学与技术。https://doi.org/10.1007/s00226-021-01347-w

- Gao, W., Shu, T., Guan, Y., Ling, S., Liu, S., Zhou, L., Shu, T., & Guan, Y. (2022). 建立基于 FT-Raman 光谱的杨树全纤维素含量测定定量模型的新策略。碳水化合物聚合物，277，文章 118793，118793。/j.carbpol.2021.118793.

- Gao, W., Shu, T., Liu, Q., Ling, S., Guan, Y., Liu, S., & Zhou, L. (2021). 基于傅里叶变换-拉曼光谱法的适宜杨树基因型筛选木质素含量预测建模。ACS Omega, 6(12), 8578–8587. https://doi.org/10.1021/acsomega.1c00400

- Gao, W., Zhou, L., Guan, Y., Gao, H., & Liu, S. (2022). 基于 FT-Raman 光谱的漂白木浆 Kappa 数监测。纤维素，29, 1069–1080. https://doi.org/10.1007/s10570-021-04333-4

- Gao, W., Zhou, L., Liu, S., Guan, Y., Gao, H., & Hui, B. (2022). 基于拉曼光谱的杨树木质素含量机器学习预测。生物资源技术，348(1 月), 文章 126812. https://doi.org/10.1016/j.biortech.2022.126812

- Gierlinger, N., & Schwanninger, M. (2006). 共聚焦拉曼显微镜下杨树木材细胞壁的化学成像。植物生理学，140(4), 1246–1254. https://doi.org/10.1104/pp.105.066993

- Gordobil, O., Herrera, R., Ooshnaaji, F., Sandak, J., & Sandak, A. (2021). 干燥工艺对 Kraft 木质素的影响：基于 2D 近红外相关光谱的木质素-水相互作用机制研究。材料研究与技术杂志，12, 159–169. https://doi.org/10.1016/j.jmrt.2021.02.080

- Gu, I. Y.-H., & Henrik Andersson, R. V. (2010). 基于图像分析和支持向量机的木材缺陷分类。木材科学与技术，44(4), 693–704. https://doi.org/10.1007/s00226-009-0287-9

- Hong, J. (2020). XGBoost、LightGBM 和 CatBoost 算法在房屋评估系统中的应用。住房金融研究，4, 33–64. https://doi.org/10.52534/hfr.2021.4.0.33

- Hosseinzadeh, A., Zhou, J. L., Altaee, A., & Li, D. (2022). 基于暗发酵工艺的污水生物氢生产机器学习建模与分析。生物资源技术，343(2021 年 9 月)。https://doi.org/10.1016/j.biortech.2021.126111

- Ikeuchi, K. (2021). 列车回归。载于《计算机视觉：参考指南》（第 1081 页）。Springer International Publishing. https://doi.org/10.1007/978-3-030-63416-2_300335.

- Iskigof, G. H., & Beccr, C. R. (2015). 木质纤维素生物质：生物基化学品和聚合物生产的可持续平台。聚合物化学，6(25), 4497–4559. https://doi.org/10.1039/C5PY00263J

- Jabeur, S. B., Gharbi, C., Methef-Wall, S., & Arfi, W. B. (2021). 企业失败预测的 CatBoost 模型和人工智能技术。技术预测与社会变革，166, 文章 120658. https://doi.org/10.1016/j.techfore.2021.120658

- Juanuaviani, T. M. A., Gusriani, N., Joebaeli, K., Supian, S., & Subiyanto, S. (2019). 载于第 116 卷。基于 LARS（最小角回归与收缩算法，使用 Mallow's Cp）的 LASSO 最佳模型（第 245–252 页）。

- Jermyn, M., Desroches, J., Aubertin, K., St-Arnaud, K., Madore, W.-J., De Montigny, E., Guiot, M.-C., Trudel, D., Wilson, B. C., Petrecca, K., & Leblond, F. (2016). 拉曼光谱进展综述：着重于肿瘤学临床转化中的挑战。医学与生物物理学，61(23), R370–R400. https://doi.org/10.1088/0031-9155/61/23/R370

- Ke, G., Meng, Q., Finley, T., Wang, T., Chen, W., Ma, W., Ye, Q., & Liu, T.-Y. (2017). LightGBM：一种高效的梯度提升决策树（NIP 2017）《神经信息处理系统进展》，30, 3149–3157. https://www.microsoft.com/en-us/research/publication/lightgbm-a-highly-efficient-gradient-boosting-decision-tree/.

- Liang, L., Wei, L., Fang, G., Xu, F., Deng, Y., Shen, K., Tian, Q., Wu, T., & Zhu, B. (2020). 基于近红外光谱和变量选择的木浆原料全纤维素和木质素含量预测。分光化学杂志 - 第 A 部分：分子

