
## 微流控平台数据分析
检测过程涉及以下步骤：1) 信号采集：使用 635 nm 激光通道扫描生物芯片，并使用 GenePix Pro 软件对每个条形码的荧光信号进行定量，并获得检测区域的平均荧光强度。2) 数据归一化：在机器学习模型输入之前，对原始荧光强度值进行 log10 转换，以归一化数据分布并增强模型性能。

## 诊断预测建模
使用 R version 4.4.2 为 ESCC 开发了诊断预测模型，采用集成机器学习方法进行多维分析。在方法学上，系统性地实施了多个 R 包：randomForest 用于随机森林建模，caret 用于数据预处理和模型调优，pROC 用于性能评估，randomForestExplainer 用于特征重要性分析，ggplot2 用于可视化，以及 Rtsne 用于高维数据降维。在模型构建期间：首先使用 caret 包进行数据标准化和分层抽样（70% 训练集/30% 测试集），以确保数据分布均衡。随机森林模型使用 randomForest 中实现的自助聚合算法开发，最初纳入 14 种血浆蛋白作为预测变量。通过 caret 指导的网格搜索验证，模型参数优化为：ntree = 145 棵决策树，mtry = 14（每次节点分裂考虑的特征数），nodesize = 5（每个末端节点的最小样本数）。参数优化由 pROC 计算的 AUC 值和 caret 生成的混淆矩阵指标共同指导。使用 randomForestExplainer 进行了特征重要性分析，其提供了三种互补的评估方法：1) 最小深度分析（min_depth_distribution）以识别最关键的分类特征；2) 节点纯度提升（measure_importance）以量化每个特征对模型精度的贡献；3) 根节点分裂频率以反映全局特征重要性。基于这些分析，从最初的 14 个特征中选出 9 个最具预测性的蛋白生物标志物用于最终模型。验证阶段采用多维评估策略：caret 生成的混淆矩阵提供了包括准确率、敏感性和特异性在内的关键指标；pROC 从 ROC 曲线计算 AUC 值；ggplot2 生成校准曲线；Rtsne 可视化展示了 ESCC 患者与健康对照在蛋白生物标志物空间中的分离模式。模型通过 randomForest 的 predict 函数输出个体化预测概率（范围 0–1），诊断阈值设为 0.5（概率 > 0.5 分类为 ESCC，≤0.5 为健康对照）。所有可视化均使用 ggplot2 创建，包括 ROC 曲线、多维特征重要性热图、t-SNE 降维散点图和模型校准曲线。

## 免疫荧光染色
福尔马林固定石蜡包埋切片经二甲苯和梯度乙醇系列脱蜡，随后在柠檬酸缓冲液（pH 6.0）中采用微波加热进行抗原 retrieval。经 10% 与二抗宿主种属匹配的血清封闭后，载玻片在 4 °C 下过夜孵育以下一抗：anti-FST（1:400, Proteintech #60060-1-Ig）、anti-PTX3（1:200, Proteintech #13797-1-AP）和 anti-EIF2S2（1:500, Servicebio #GB111135）。Alexa Fluor 偶联二抗（1:200）在室温下作用 50 min，随后进行 DAPI 复染和自发荧光淬灭。切片用抗淬灭封片剂封固并使用数字切片扫描仪成像。所有步骤之间均进行 PBS 洗涤（3 min × 5 min）。

## 统计方法
采用 Kolmogorov–Smirnov 检验评估所有数据的正态性，而分类数据则使用卡方检验进行分析。对于呈正态分布的数据，采用非配对双尾 t 检验进行比较，而非正态分布数据则使用 Mann–Whitney 非参数检验。荧光强度或光密度（O.D.）值与目标抗原浓度之间的线性关系使用 R-squared（R²）统计量进行评估。p 值低于 0.05 被认为具有统计学意义。检测限（LOD）由方程确定：LOD = 3 × δ / S，其中 δ 为空白值的相对标准偏差，S 表示由线性回归方程得出的斜率。

诊断效率使用准确率、ROC 曲线和其他相关指标进行评估。分析使用 GraphPad Prism（v.9.5）、R software（v.4.4.1）（可获取于 https://www.r-project.org/）和 Origin（v.2021）进行。

## 支持信息
支持信息可从 Wiley Online Library 或作者处获取。

## 致谢
本工作得到中国国家重点研发计划（2023YFB3210400）、山东省重大科技创新项目（2022CXGC020501）、国家自然科学基金（项目号 62174101）、山东大学集成研究与培养项目（项目号 2022JC001）以及微生物技术国家重点实验室院内联合项目（项目号 SKLMTPJ-2024-05）资助。作者感谢山东大学生命与环境科学核心设施的 Xiaoju Li、Haiyan Sui 和 Xueyun Geng 在 TEM 方面的帮助。C.M. 感谢香港研究资助局研究基金（14208723）的财务支持，以及香港赛马会慈善信托基金对自然启发精准医学工程 JC STEM 实验室的资助。

## 利益冲突
作者声明无利益冲突。

## 作者贡献
L.H.、Y.Z.、J.W.、X.Z. 和 C.M. 构思了研究思路。X.Z.、Y.Z.、J.Q. 和 Y.L. 执行实验、撰写文章并制作图表。Y.Z.、C.W.、M.S. 和 X.C. 指导了本稿件的准备。Z.L. 和 Y.Z. 执行样本采集和数据获取。H.L.、L.H. 和 C.M. 进行论文修改。所有作者均阅读并批准了最终稿件。

## 数据可用性声明
支持本研究结果的数据可根据合理请求从通讯作者处获取。

## 关键词
早期诊断, 机器学习, 微流控平台, 小型细胞外囊泡蛋白

收稿：2025年4月7日
修订：2025年6月17日
在线发表：

[1] N. Deboever, C. M. Jones, K. Yamashita, J. A. Ajani, W. L. Hofstetter, BMJ 2024, 385, 074962.
[2] H. Sung, J. Ferlay, R. L. Siegel, M. Laversanne, I. Soerjomataram, A. Jemal, F. Bray, CA Cancer J. Clin. 2021, 71, 209.
[3] T. L. Vaughan, R. C. Fitzgerald, Nat. Rev. Gastroenterol. Hepatol. 2015, 12, 243.
[4] R. K. Vajravelu, J. M. Kolb, S. U. Thanawala, F. I. Scott, S. Han, A. G. Singal, G. W. Falk, D. A. Katzka, S. Wani, Clin. Gastroenterol. Hepatol. 2022, 20, 1739.
[5] S. Connal, J. M. Cameron, A. Sala, P. M. Brennan, D. S. Palmer, J. D. Palmer, H. Perlow, M. J. Baker, J. Transl. Med. 2023, 21, 118.
[6] J. J. Hao, D. C. Lin, H. Q. Dinh, A. Mayakonda, Y. Y. Jiang, C. Chang, Y. Jiang, C. C. Lu, Z. Z. Shi, X. Xu, Y. Zhang, Y. Cai, J. W. Wang, Q. M. Zhan, W. Q. Wei, B. P. Berman, M. R. Wang, H. P. Koeffler, Nat. Genet. 2016, 48, 1500.
[7] Z. Yuan, X. Wang, X. Geng, Y. Li, J. Mu, F. Tan, Q. Xue, S. Gao, J. He, Cancer Commun. 2021, 41, 3.
[8] R. B. Corcoran, B. A. Chabner, N. Engl. J. Med. 2018, 379, 1754.
[9] S. N. Lone, S. Nisar, T. Masoodi, M. Singh, A. Rizwan, S. Hashem, W. El-Rifai, D. Bedognetti, S. K. Batra, M. Haris, A. A. Bhat, M. A. Macha, Mol. Cancer 2022, 21, 79.
[10] E. A. Klein, D. Richards, A. Cohn, M. Tummala, R. Lapham, D. Cosgrove, G. Chung, J. Clement, J. Gao, N. Hunkapiller, A. Jamshidi, K. N. Kurtzman, M. V. Seiden, C. Swanton, M. C. Liu, Ann. Oncol. 2021, 32, 1167.
[11] J. D. Cohen, L. Li, Y. Wang, C. Thoburn, B. Afsari, L. Danilova, C. Douville, A. A. Javed, F. Wong, A. Mattox, R. H. Hruban, C. L. Wolfgang, M. G. Goggins, M. Dal Molin, T. L. Wang, R. Roden, A. P. Klein, J. Ptak, L. Dobbyn, J. Schaefer, N. Silliman, M. Popoli, J. T. Vogelstein, J. D. Browne, R. E. Schoen, R. E. Brand, J. Tie, P. Gibbs, H. L. Wong, A. S. Mansfield, et al., Science 2018, 359, 926.
[12] M. C. Liu, G. R. Oxnard, E. A. Klein, C. Swanton, M. V. Seiden, Ann. Oncol. 2020, 31, 745.
[13] J. A. Welsh, D. Goberdhan, L. O'Driscoll, E. I. Buzas, C. Blenkiron, B. Bussolati, H. Cai, D. Di Vizio, T. Driedonks, U. Erdbrügger, J. M. Falcon-Perez, Q. L. Fu, A. F. Hill, M. Lenassi, S. K. Lim, M. G. Mahoney, S. Mohanty, A. Möller, R. Nieuwland, T. Ochiya, S. Sahoo, A. C. Torrecillas, L. Zheng, A. Zijlstra, S. Abuelreich, R. Bagabas, P. Bergese, E. M. Bridges, M. Brucale, D. Burger, et al., J Extracell. Vesicles 2024, 13, 12404.
[14] I. A. Batista, J. C. Machado, S. A. Melo, Trends Cancer 2024, 10, 947.
[15] D. Yu, Y. Li, M. Wang, J. Gu, W. Xu, H. Cai, X. Fang, X. Zhang, Mol. Cancer 2022, 21, 56.
[16] H. Yin, J. Xie, S. Xing, X. Lu, Y. Yu, Y. Ren, J. Tao, G. He, L. Zhang, X. Yuan, Z. Yang, Cell Rep. Med. 2024, 5, 101689.
[17] Q. Zhu, J. Luo, H. P. Li, W. Ye, R. Pan, K. Q. Shi, R. Yang, H. Xu, H. Li, L. P. Lee, F. Liu, ACS Nano 2023, 17, 8564.
[18] H. K. Charles Jacob, R. Signorelli, J. L. Charles Richard, T. Kashuv, S. Lavania, A. Middleton, B. A. Gomez, A. Ferrantella, H. Amirian, J. Tao, A. B. Ergounl, M. M. Boone, M. Hadisiyura, W. A. Tao, A. Iliuk, M. K. Kashyap, M. Garcia-Buitrago, R. Dawra, A. K. Saluja, J. Exp. Clin. Cancer Res. 2022, 41, 258.
[19] B. Pang, Q. Wang, H. Chen, Z. Liu, M. Han, J. Gong, L. Yue, X. Ding, S. Wang, Z. Yan, Y. Chen, D. Malouf, J. Bucci, T. Guo, C. Zhou, J. Jiang, Y. Li, Adv. Sci. 2024, 11, 2402509.
[20] M. Quiralte, A. Barquín, M. Yagüe-Fernández, P. Navarro, T. Grazioso, E. Sevillano-Fernández, J. F. Rodríguez-Moreno, A. Balarézo-Saldívar, H. Peinado, E. Izquierdo, C. Millán, I. López-Carrasco, M. Prieto, R. Madurga, I. Fernández-Miranda, S. Ruiz-Llorente, J. García-Donas, J. Clin. Invest. 2024, 134, 176161.
[21] W. Li, C. Li, T. Zhou, X. Liu, X. Liu, X. Li, D. Chen, Mol. Cancer 2017, 16, 145.
[22] R. Kalluri, V. S. LeBleu, Science 2020, 367, aau6977.
[23] M. Haider, R. Cagliani, J. Jagal, M. N. Jayakumar, B. Fayed, S. B. Shakartalla, R. Pasricha, K. Greish, R. El-Awady, J. Colloid Interface Sci. 2023, 630, 698.
[24] C. Brosseau, L. Colas, A. Magnan, S. Brouard, Front. Immunol. 2018, 9, 2316.
[25] S. Gurunathan, M. H. Kang, M. Jeyaraj, M. Qasim, J. H. Kim, Cells 2019, 8, 307.
[26] M. Mathieu, N. Névo, M. Jouve, J. I. Valenzuela, M. Maurin, F. J. Verweij, R. Palmulli, D. Lankar, F. Dingli, D. Loew, E. Rubinstein, G. Boncompain, F. Perez, C. Théry, Nat. Commun. 2021, 12, 4389.
[27] C. Wang, C. Wang, Y. Wu, J. Gao, Y. Han, Y. Chu, L. Qiang, J. Qiu, Y. Gao, Y. Wang, F. Song, Y. Wang, X. Shao, Y. Zhang, L. Han, Adv. Healthcare Mater. 2022, 11, 2102800.
[28] V. S. Wang, J. L. Hornick, J. A. Sepulveda, R. Mauer, J. M. Poneros, Gastrointest. Endosc. 2009, 69, 777.
[29] E. L. Bird-Lieberman, R. C. Fitzgerald, Br. J. Cancer 2009, 101, 1.
[30] Y. Gao, L. Qiang, Y. Chu, Y. Han, Y. Zhang, L. Han, AIP Adv. 2020, 10, 045022.
[31] C. Wang, Y. Zhang, W. Tang, C. Wang, Y. Han, L. Qiang, J. Gao, H. Liu, L. Han, Anal. Chim. Acta 2021, 1178, 338791.
[32] J. W. Yang, L. L. Yuan, Y. Gao, X. S. Liu, Y. J. Wang, L. M. Zhou, X. Y. Kui, X. H. Li, C. B. Ke, Z. J. Pei, J. Cancer 2021, 12, 5838.
[33] L. Dreikhausen, S. Blank, L. Sisic, U. Heger, W. Weichert, D. Jäger, T. Bruckner, N. Giese, L. Grenacher, C. Falk, K. Ott, T. Schmidt, BMC Cancer 2015, 15, 121.
[34] Z. Fan, Y. Zheng, X. Li, X. Deng, Y. Ba, K. Feng, J. Su, H. Wang, Z. Suo, L. Li, Mol. Ther. Oncolytics 2022, 24, 772.
[35] S. K. Bhat, D. T. McManus, H. G. Coleman, B. T. Johnston, C. R. Cardwell, U. McMenamin, F. Bannon, B. Hicks, G. Kennedy, A. T. Gavin, L. J. Murray, Gut 2015, 64, 20.
[36] Y. Wang, X. Li, X. Wei, L. Li, H. Bai, X. Yan, H. Zhang, L. Zhao, W. Zhou, L. Zhao, MedComm 2023, 4, 377.
[37] K. Li, Y. Lin, Y. Zhou, X. Xiong, L. Wang, J. Li, F. Zhou, Y. Guo, S. Chen, Y. Chen, H. Tang, X. Qiu, S. Cai, D. Zhang, E. Bremer, S. C. Jim Yeung, H. Zhang, Gastroenterology 2023, 165, 932.
[38] I. H. Chen, L. Xue, C. C. Hsu, J. S. Paez, L. Pan, H. Andaluz, M. K. Wendt, A. B. Iliuk, J. K. Zhu, W. A. Tao, Proc. Natl. Acad. Sci. USA 2017, 114, 3175.
[39] L. Dimitrakopoulos, I. Prassas, E. P. Diamandis, G. S. Charames, Crit. Rev. Clin. Lab. Sci. 2017, 54, 414.
[40] Z. Ding, N. Wang, N. Ji, Z. S. Chen, Mol. Cancer 2022, 21, 53.
[41] M. Binnewies, E. W. Roberts, K. Kersten, V. Chan, D. F. Fearon, M. Merad, L. M. Coussens, D. I. Gabrilovich, S. Ostrand-Rosenberg, C. C. Hedrick, R. H. Vonderheide, M. J. Pittet, R. K. Jain, W. Zou, T. K. Howcroft, E. C. Woodhouse, R. A. Weinberg, M. F. Krummel, Nat. Med. 2018, 24, 541.
[42] K. E. de Visser, J. A. Joyce, Cancer Cell 2023, 41, 374.
[43] Y. Chen, B. Wang, Y. Zhao, X. Shao, M. Wang, F. Ma, L. Yang, M. Nie, P. Jin, K. Yao, H. Song, S. Lou, H. Wang, T. Yang, Y. Tian, P. Han, Z. Hu, Nat. Commun. 2024, 15, 1657.
[44] Z. Huang, C. Deng, C. Ma, G. He, J. Tao, L. Zhang, X. Hu, Y. Mo, L. Qiu, N. Zhang, C. Luo, S. Xing, J. Xie, H. Yin, Int. J. Surg. 2024, 110, 4672.
[45] Y. Chen, G. Cai, J. Jiang, C. He, Y. Chen, Y. Ding, J. Lu, W. Zhao, Y. Yang, Y. Zhang, G. Wu, H. Wang, Z. Zhou, L. Teng, Gastric Cancer 2023, 26, 504.
[46] B. Li, F. G. Kugeratski, R. Kalluri, Elife 2024, 12, RP90390.
[47] J. Zhang, Z. Gao, W. Xiao, N. Jin, J. Zeng, F. Wang, X. Jin, L. Dong, J. Lin, J. Gu, C. Wang, Chem. Sci. 2024, 15, 18419.
