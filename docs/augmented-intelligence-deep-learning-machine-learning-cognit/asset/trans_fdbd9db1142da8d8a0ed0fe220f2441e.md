
可能对消费者健康产生负面影响 [63]。另一方面，低于 50 ppb 的值被认为是可以接受的。我们有兴趣将样品分类为可食用（泰乐菌素浓度 < 50 ppb）或不可食用（泰乐菌素浓度 ≥ 50 ppb）。为此，使用了多层感知器神经网络（MLP）技术。

MLP 以多起点模式运行，使用由两个隐藏层（6,3）组成的网络架构，采用逻辑激活函数，获得了更好的拟合。由于与基质复杂性相关的效应（包括诸如糖、蛋白质、脂肪、尿素和其他可溶性固体等干扰），数据集中包含一个对应于牛奶来源的多类因子，以及其他 16 个感兴趣的波数（cm⁻¹）。下面将几种机器学习算法——逻辑回归（LogR）、偏最小二乘判别分析（PLS-DA）、CART、GBT 和 RF 在真实牛奶样品判别分析中的性能与先前开发的 MLP 参考进行比较（表 3.3）。

## 表 3.3. 通过逻辑回归模型（LogR）、PLS-DA、CART、GBT、RF 和 MLP 对包含 33 个牛奶样品的测试子集进行判别分析的质量参数。

| 模型 | 真阳性 | 假阳性 | 真阴性 | 假阴性 | 精确度 | CI - | CI + | Kappa | 灵敏度 | 特异度 | p |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LogR | 8 | 7 | 6 | 12 | 0.424 | 0.255 | 0.608 | -0.13 | 0.461 | 0.400 | 0.989 |
| PLS-DA | 17 | 11 | 2 | 3 | 0.576 | 0.392 | 0.745 | 0.004 | 0.154 | 0.850 | 0.706 |
| CART | 20 | 13 | 0 | 0 | 0.606 | 0.421 | 0.771 | 0 | 0 | 1.000 | 0.575 |
| GBT | 18 | 2 | 11 | 2 | 0.878 | 0.718 | 0.966 | 0.746 | 0.846 | 0.900 | 6.02E-4 |
| RF | 18 | 1 | 12 | 2 | 0.909 | 0.757 | 0.981 | 0.812 | 0.923 | 0.900 | 1.16E-4 |
| MLP [28] | 20 | 0 | 13 | 0 | 1.000 | 0.894 | 1.000 | 1.000 | 1.000 | 1.000 | 6.65E-8 |

考虑到污染物的低浓度，预计基质效应会变得非常普遍。出于前一节讨论的相同原因，与其他算法相比，GBT 和 RF 在预测类别方面获得了令人满意的结果，仅有两次假阴性，预测准确率 > 0.85，其置信区间 CI 包含了 MLP 所获得的准确率水平。另一方面，分类树对阴性类别（C < 50 ppb）不敏感，而参数算法（LogR 和 PLS-DA）则获得了无关紧要的结果。这强烈表明响应呈非线性分布的趋势。只有最后三种模型，包括基于具有重采样机制的决策树集成技术的两种技术，产生了统计学显著的结果（p <0.05）。

## 结论

光谱学与多元校准方法的结合使得多组分系统的复杂光谱分析成为可能，因此在本章中，我们介绍了某些基于树的工具，并突出了与其他机器学习算法相比的有趣特征。基于随机森林的包装算法 Boruta 对属性子集的选择证明与专家中非常流行的进化算法一样有效地选择变量。在高维空间的回归问题中，诸如随机森林和梯度提升树之类的树集成被证明比文献中已确立的化学计量技术更具预测性，特别是随机森林在噪声水平等于或高于 35% 时被证明具有鲁棒性。在复杂基质中痕量污染物的判别分析中，RF 和 GBT 被证明与多层感知器神经网络一样具有预测性，其优势在于前两者计算成本更低。

## 注释

还介绍了基于遗传回归（GR）的方法。然而，由于作者选择呈现遗传表达而不是纯属性，我们选择在此抑制这些发现。

## 发表同意书

不适用。

## 利益冲突

作者声明不存在任何利益冲突，无论是财务上的还是其他方面的。

## 致谢

未声明。

## 参考文献

[1] J.B. Ghasemi, and H. Tavakoli, "光谱多元校准中随机森林回归的应用", Anal. Methods, vol. 5, no. 7, pp. 1863-1871, 2013. [http://dx.doi.org/10.1039/c3ay26338j]

[2] A.M. Jiménez-Carvelo, A. González-Casado, M.G. Bagur-González, and L. Cuadros-Rodríguez, "用于食品质量和真实性分析评价的替代数据挖掘/机器学习方法 - 综述", Food Res. Int., vol. 122, pp. 25-39, 2019. [http://dx.doi.org/10.1016/j.foodres.2019.03.063] [PMID: 31229078]

[3] V. Svetnik, A. Liaw, C. Tong, J.C. Culberson, R.P. Sheridan, and B.P. Feuston, "随机森林：化合物分类和 QSAR 建模的分类和回归工具", J. Chem. Inf. Comput. Sci., vol. 43, no. 6, pp. 1947-1958, 2003. [http://dx.doi.org/10.1021/ci034160g] [PMID: 14632445]

[4] F.A. Vega, J.M. Matías, M.L. Andrade, M.J. Reigosa, and E.F. Covelo, "用于模拟土壤对重金属吸附和滞留的分类和回归树（CARTs）", J. Hazard. Mater., vol. 167, no. 1-3, pp. 615-624, 2009. [http://dx.doi.org/10.1016/j.jhazmat.2009.01.016] [PMID: 19200658]

[5] S.M. Tan, J. Jiao, X-L. Zhu, Y-P. Zhou, D-D. Song, H. Gong, and R-Q. Yu, "通过分类和回归树对一系列抗念珠菌抗菌剂的 QSAR 研究", Chemom. Intell. Lab. Syst., vol. 103, no. 2, pp. 184-190, 2010. [http://dx.doi.org/10.1016/j.chemolab.2010.07.005]

[6] D. Custers, T. Cauwenbergh, J.L. Bothy, P. Courselle, J.O. De Beer, S. Apers, and E. Deconinck, "ATR-FTIR 光谱学和化学计量学：鉴别和表征假药的有趣工具", J. Pharm. Biomed. Anal., vol. 112, pp. 181-189, 2015. [http://dx.doi.org/10.1016/j.jpba.2014.11.007] [PMID: 25476739]

[7] L. Rokach, "决策森林：二十年研究", Inf. Fusion, vol. 27, pp. 111-125, 2016. [http://dx.doi.org/10.1016/j.inffus.2015.06.005]

[8] F.B. de Santana, W. Borges Neto, and R.J. Poppi, "随机森林作为单类分类器和红外光谱用于食品掺假检测", Food Chem., vol. 293, pp. 323-332, 2019. [http://dx.doi.org/10.1016/j.foodchem.2019.04.073] [PMID: 31151619]

[9] X. Jin, S. Li, W. Zhang, J. Zhu, and J. Sun, "利用提升算法通过不同预处理变换的可见近红外光谱预测土壤有效钾含量", Appl. Sci. (Basel), vol. 10, no. 4, p. 1520, 2020. [http://dx.doi.org/10.3390/app10041520]

[10] J. Xiu, Z. Xianzhi, L. Shaowen, W. Wencai, and Q. Haijun, "基于梯度提升决策树的超光谱回归方法预测土壤有效磷", Jiguang Yu Guangdianzixue Jinzhan, vol. 56, no. 13, p. 131102, 2019. [http://dx.doi.org/10.3788/LOP56.131102]

[11] G. James, D. Witten, T. Hastie, and R. Tibshirani, 统计学习导论. vol. 103. Springer New York: New York, NY, 2013. [http://dx.doi.org/10.1007/978-1-4614-7138-7]

[12] L. Rokach, and O. Maimon, 决策树. Data mining and knowledge discovery handbook. Springer: Boston, MA, 2005, pp. 165-192. [http://dx.doi.org/10.1007/0-387-25465-X_9]

[13] R.S. DeFries, M. Hansen, J.R.G. Townshend, and R. Sohlberg, "8 km 空间分辨率的全球土地覆盖分类：Landsat 影像衍生训练数据在决策树分类器中的使用", Int. J. Remote Sens., vol. 19, no. 16, pp. 3141-3168, 1998. [http://dx.doi.org/10.1080/014311698212435]

[14] K. Zhang, X. Wu, R. Niu, K. Yang, and L. Zhao, "中国三峡水库区使用随机森林和决策树方法进行滑坡易发性制图的评估", Environ. Earth Sci., vol. 76, no. 11, pp. 404-424, 2017. [http://dx.doi.org/10.1007/s12665-017-6731-5]

[15] E. Pekel, M.C. Akkoyunlu, M.T. Akkoyunlu, and S. Pusat, "用于预测对流干燥过程中低阶煤水分含量的决策树回归模型", Int. J. Coal Prep. Util., vol. 40, no. 8, pp. 505-512, 2020. [http://dx.doi.org/10.1080/19392699.2020.1737527]

[16] O.F. Althuwaynee, A. Balogun, and W. Al Madhoun, "使用决策树算法和双变量概率聚类极坐标函数进行空气污染危害评估：评估 PM10 与其他空气污染物之间的相关性聚类", GISci. Remote Sens., vol. 57, no. 2, pp. 207-226, 2020. [http://dx.doi.org/10.1080/15481603.2020.1712064]
