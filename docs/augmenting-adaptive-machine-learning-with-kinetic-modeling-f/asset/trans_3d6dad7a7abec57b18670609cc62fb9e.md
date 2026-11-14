
v/v 乙酸乙酯/正己烷)。1H NMR (300 MHz, CD3OD): δ 8.34 (d, J = 8.7 Hz, 1H), 8.18 (dd, J = 8.6, 0.8 Hz, 1H), 8.05 (ddt, J = 8.5, 1.4, 0.7 Hz, 1H), 7.82–7.77 (m, 1H), 7.69 (ddd, J = 8.5, 6.9, 1.5 Hz, 1H), 7.51 (ddd, J = 8.1, 6.9, 1.2 Hz, 1H), 7.18 (d, J = 1.1 Hz, 1H), 7.02 (d, J = 1.1 Hz, 1H), 4.30 (s, 3H). 13C{1H} NMR (75 MHz, CD3OD) δ 150.6, 147.3, 145.0, 136.3, 129.5, 129.4, 128.6, 127.6, 127.2, 126.5, 125.2, 120.6, 36.6.

机器学习。我们采用了随机森林回归器，并探测了多个超参数[树的数量（100–1000），树深度（无，2，4）以及特征数量（自动或平方根）]来构建预测模型。采用了10倍交叉验证，将数据集分为包含90%数据的训练组和剩余10%的测试组。最佳超参数的选择由平均绝对误差（MAE）的计算指导。使用这些参数，模型预测了其余可能反应条件的产物产率，然后选择了下一个反应。对前三次迭代应用了勘探方法以允许模型改进。对于后续迭代，通过选择预测中前5个高产反应中方差最低的反应，应用了开发方法。模型随着每个新增数据点的加入而通过改进其预测模型来发展。该模型和数据分析完全使用Python 3.7.3以及NumPy 1.16.4、Pandas 0.24.2和Scikit-learn 0.21.2库实现，并在HP ProBook G3（2.40 GHz 2核处理器，4 Gb RAM）上运行（5–10 min）。为初始化，并行进行了20个随机反应（表 S1），并通过HPLC分析以创建第一个训练数据集。使用校准曲线，可以量化每个反应中获得的产物产率。基于这些数据，机器学习例程一次选择一组额外条件用于实验验证。所选实验的输出被添加到训练集中，并进行了涉及设计–制造–测试的迭代过程，共五次迭代。优化例程的代码可在 https://github.com/tcorodrigues/LabMate 获取。ML.

机器学习对照。为评估该方法的鲁棒性，计算了其他模型，如线性回归、岭回归和套索回归。与此同时，我们进行了y随机化研究，以排除随机森林决策过程中的伪效应。计算了根均方误差（RMSE）、平均绝对误差（MAE）和决定系数（r2）等误差指标，并用于不同方法之间的比较。

动力学方法。使用DynoChem软件（Scale-Up Systems；构建：1.3.20b340，数据版本：1.0）进行反应建模。该软件包含模型模板，并提供模拟器、拟合和优化插件选项来运行模型。在这项工作中，我们使用单一模型模板来拟合所有实验并计算动力学参数。我们采用Levenberg–Marquardt算法进行拟合，在最小化SSQ期间，并使用Backward Euler（BE）积分方法求解与反应相关的物料平衡微分和代数方程。动力学参数在定义的参考温度（78 °C）下计算。所有反应运行了360 min，并在指定时间点收集分析样品。分析通过HPLC进行，并基于校准曲线。

## 相关内容

### 支持信息

支持信息可免费获取，网址为 https://pubs.acs.org/doi/10.1021/acs.joc.1c01038。

所有化合物的1H和13C NMR光谱，所有化合物的UPLC-QDa色谱图，机器学习模型和动力学模型使用的数据和条件（PDF）

## 作者信息

通讯作者 Filipe A. P. Ataide – 研发，工艺化学开发，Hovione FarmaCiência S.A，1649-038 Lisboa，葡萄牙；orcid.org/0000-0002-8288-2152；电子邮件：fataide@hovione.com Tiago Rodrigues – 药物研究所（iMed.ULisboa），里斯本大学药学院，1649-003 Lisboa，葡萄牙；orcid.org/0000-0002-1581-5654；电子邮件：tiago.rodrigues@ff.ulisboa.pt

作者 A. Filipa Almeida – 研发，工艺化学开发，Hovione FarmaCiência S.A，1649-038 Lisboa，葡萄牙；药物研究所（iMed.ULisboa），里斯本大学药学院，1649-003 Lisboa，葡萄牙 Rui M. S. Loureiro – 研发，工艺化学开发，Hovione FarmaCiência S.A，1649-038 Lisboa，葡萄牙 Rui Moreira – 药物研究所（iMed.ULisboa），里斯本大学药学院，1649-003 Lisboa，葡萄牙

完整联系信息可于以下网址查阅：https://pubs.acs.org/10.1021/acs.joc.1c01038

作者贡献 A.F.A. 进行了化学和建模工作。所有作者设计了实验并分析了数据。A.F.A 和 T.R. 撰写了手稿，其余作者提供了贡献。F.A.P.A.、R.M.S.L.、R.M. 和 T.R. 监督了研究。F.A.P.A. 和 T.R. 协调了研究。所有作者均已批准最终版本的手稿。

备注 作者声明存在以下竞争性财务利益：T.R. 是 TargTex S.A. 的联合创始人和股东。

## 致谢

A.F.A. 和 T.R. 承认葡萄牙科学技术基金会（FCT）分别通过 PD/BD/143125/2019 和 CEECIND/00684/2018 提供财务支持。该研究通过COMPETE计划—里斯本区域运作计划—拨款 LISBOA-01-0145-FEDER-016405 获得欧洲结构与投资基金资助，并通过葡萄牙科学技术基金会（FCT）—拨款 SAICTPAC/0019/2015 获得国家基金资助。还承认 FCT 对 MedChemTrain 博士项目（PD147-2013-AA）的支持。作者感谢 Ricardo Gonçalves（Hovione）在设计定量所有物种的分析方法方面提供的大力支持。

## 参考文献

- (1) Hayashi, Y. 全合成中的时间经济学. J. Org. Chem. 2021, 86 (1), 1–23.
- (2) Peiretti, F.; Brunel, J. M. 人工智能：有机化学的未来？. ACS Omega 2018, 3 (10), 13263–13266.
- (3) Pflüger, P. M.; Glorius, F. 分子机器学习：合成化学的未来？. Angew. Chem., Int. Ed. 2020, 59 (43), 18860–18865.
- (4) Harvey, A. L. 药物发现中的天然产物. Drug Discovery Today 2008, 13 (19–20), 894–901.
- (5) Atanasov, A. G.; Zotchev, S. B.; Dirsch, V. M.; Orhan, I. E.; Banach, M.; Rollinger, J. M.; Barreca, D.; Weckworth, W.; Bauer, R.; Bayer, E. A.; Majeed, M.; Bishayee, A.; Bochkov, V.; Bonn, G. K.; Braidy, N.; Bucar, F.; Cifuentes, A.; D'Onofrio, G.; Bodkin, M.; Diederich, M.; Dinkova-Kostova, A. T.; Erffth, T.; El Bairi, K.; Arkells, N.; Fan, T.-P.; Fiebich, B. L.; Freissmuth, M.; Georgiev, M. I.; Gibbons, S.; Godfrey, K. M.; Gruber, C. W.; Heer, J.; Huber, L. A.; Ibanez, E.; Kijioa, A.; Kiss, A. K.; Lu, A.; Macías, F. A.; Miller, M. J. S.; Mocan, A.; Müller, R.; Nicoletti, F.; Perry, G.; Pittala, V.; Rastralli, L.; Ristow, M.; Russo, G. L.; Silva, A. S.; Schuster, D.; Sheridan, H.; Skalicka-Woźniak, K.; Skaltsounis, L.; Sobarzo-Sánchez, E.; Bredt, D. S.; Stüppner, H.; Sureda, A.; Tzvetkov, N. T.; Vaccà, R. A.; Aqgrawal, B. B.; Battino, M.; Giampieri, F.; Wink, M.; Wolfender, J.-L.; Xiao, J.; Yeung, A. W. K.; Lizard, G.; Popp, M. A.; Heinrich, M.; Berindan-Nagoe, I.; Stadler, M.; Daglia, M.; Verpoorte, R.; Supuran, C. T. Taskforce, the I. N. P. S. 天然产物在药物发现中的应用：进展与机遇. Nat. Rev. Drug Discovery 2021, 20, 200–216.
- (6) Karageorgis, G.; Foley, D. J.; Larraia, L.; Waldmann, H. 拟天然产物的原理与设计. Nat. Chem. 2020, 12 (3), 227–235.
- (7) Newman, D. J.; Cragg, G. M. 1981年1月至2019年9月近四十年间作为新药来源的天然产物. J. Nat. Prod. 2020, 83 (3), 770–803.
- (8) Over, B.; Wetzel, S.; Güttler, C.; Nakai, Y.; Renner, S.; Rauh, D.; Waldmann, H. 用于碎片化配体发现的天然产物衍生片段. Nat. Chem. 2013, 5 (1), 21–28.
- (9) Rodrigues, T.; Reker, D.; Schneider, P.; Schneider, G. 药物设计中依赖天然产物. Nat. Chem. 2016, 8 (6), 531–541.
- (10) Arndt, R. R.; Jordaan, A.; Joynvt, V. P. Macrorongia Longistrobus C.B. Cl. 的生物碱. J. Chem. Soc. 1964, 5969–5975.
- (11) Rodrigues, T.; Reker, D.; Kunze, J.; Schneider, P.; Schneider, G. 揭示片段状天然产物的大分子靶点. Angew. Chem., Int. Ed. 2015, 54, 10516–10520.
- (12) Reker, D.; Rodrigues, T.; Schneider, P.; Schneider, G. 通过自组织图共识识别重新设计化学实体的大分子靶点. Proc. Natl. Acad. Sci. U. S. A. 2014, 111 (11), 4067–4072.
- (13) Hicken, E. J.; Marnsater, F. P.; Munson, M. C.; Schlachter, S. T.; Robinson, J. E.; Allen, S.; Burgess, L. E.; DeLisle, R. K.; Rizzi, J. P.; Topolov, G. T.; Zhao, Q.; Hicks, J. M.; Kallan, N. C.; Tartlon, E.; Allen, A.; Callejo, M.; Cox, A.; Rana, S.; Klopfenstein, N.; Woessner, R.; Lysskatos, J. P. 发现一类具有强效PDGFR活性和口服生物利用度的新型咪唑[1,2-a]吡啶. ACS Med. Chem. Lett. 2014, 5 (1), 78–83.
- (14) Effendi, N.; Mishiro, K.; Takarada, T.; Yamada, D.; Nishii, R.; Shiba, K.; Kinuya, S.; Odani, A.; Ogawa, K. 设计、合成和生物学评价用于血小板衍生生长因子受体β（PDGFRβ）成像的放射碘化苯并[d]咪唑唑-喹啉衍生物. Bioorg. Med. Chem. 2019, 27 (2), 383–393.
- (15) Cushing, T. D.; Baichwal, V.; Berry, K.; Billedeau, R.; Bordonun, V.; Broka, C.; Cardozo, M.; Cheng, P.; Clark, D.; Dalrymple, S.; DeGraffenreid, M.; Gill, A.; Hao, X.; Hawley, R. C.; He, X.; Jaen, J. C.; Labadie, S. S.; Labelle, M.; Lehel, C.; Lu, P.-P.; McIntosh, J.; Miao, S.; Parast, C.; Shin, Y.; Sjogren, E. B.; Smith, M.-L.; Talamas, F. X.; Tonn, G.; Walker, K. M.; Walker, N. P. C.; Wesch, H.; Whitehead, C.; Wright, M.; Brownen, M. F. IKKβ抑制剂的新系列 第I部分：HTS命中化合物的初始SAR研究. Bioorg. Med. Chem. Lett. 2011, 21 (1), 417–422.
- (16) Cushing, T. D.; Baichwal, V.; Berry, K.; Billedeau, R.; Bordonun, V.; Broka, C.; Brownen, M. F.; Cardozo, M.; Cheng, P.; Clark, D.; Dalrymple, S.; DeGraffenreid, M.; Gill, A.; Hao, X.; Hawley, R. C.; He, X.; Labadie, S. S.; Labelle, M.; Lehel, C.; Lu, P.-P.; McIntosh, J.; Miao, S.; Parast, C.; Shin, Y.; Sjogren, E. B.; Smith, M.-L.; Talamas, F. X.; Tonn, G.; Walker, K. M.; Walker, N. P. C.; Wesch, H.; Whitehead, C.; Wright, M.; Jaen, J. C. IKKβ抑制剂的新系列 第II部分：一系列强效且具有药理学活性的类似物的描述. Bioorg. Med. Chem. Lett. 2011, 21 (1), 423–426.
- (17) Rodrigues, T.; Reker, D.; Welin, M.; Caldera, M.; Brunner, C.; Gabernet, G.; Schneider, P.; Walse, B.; Schneider, G. 用于药物发现和化学生物学的重新设计片段设计. Angew. Chem., Int. Ed. 2015, 54 (50), 15079–15083.
- (18) Reker, D.; Hoyt, E. A.; Bernardes, G. J. L.; Rodrigues, T. 基于最小实验信息的化学反应自适应优化. Cell Reports Phys. Sci. 2020, 1 (11), 100247.
- (19) Häse, F.; Roch, L. M.; Kreisbeck, C.; Aspuru-Guzik, A. Phoenics：一种用于化学的贝叶斯优化器. ACS Cent. Sci. 2018, 4 (9), 1134–1145.
- (20) Streith-Kalthoff, F.; Sandfort, F.; Segler, M. H. S.; Glorius, F. 合成化学中机器学习的原理、应用和方向. Chem. Soc. Rev. 2020, 49 (17), 6154–6168.
- (21) Shields, B. J.; Stevens, J.; Li, J.; Parasram, M.; Damani, F.; Alvarez, J. I. M.; Janey, J. M.; Adams, R. P.; Doyle, A. G. 贝叶斯反应优化作为化学合成的工具. Nature 2021, 590 (7844), 89–96.
- (22) Blackmond, D. G. 反应进程动力学分析：复杂催化反应机理研究的强大方法. Angew. Chem., Int. Ed. 2005, 44 (28), 4302–4320.
- (23) Wang, K.; Han, L.; Mustakis, J.; Li, B.; Magano, J.; Damon, D. B.; Dion, A.; Maloney, M. T.; Mustakis, J.; Post, R.; Li, R. 药物工艺开发中的动力学和数据驱动反应分析. Ind. Eng. Chem. Res. 2020, 59 (6), 2409–2421.
- (24) Nielsen, C. D.-T.; Bures, J. 可视动力学分析. Chem. Sci. 2019, 10 (2), 348–353.
- (25) Marco-Contelles, J.; Pérez-Mayoral, E.; Samadi, A.; Carreiras, M.; do, C.; Soriano, E. 弗里德兰反应的最新进展. Chem. Rev. 2009, 109 (6), 2652–2671.
- (26) Lan, X.-B.; Ye, Z.; Huang, M.; Liu, J.; Liu, Y.; Ke, Z. 基于N-杂环卡宾锰的非官能团外层球策略实现酮与醇的高活性α-烷基化. Org. Lett. 2019, 21 (19), 8065–8070.
- (27) Kumar, P.; Garg, V.; Kumar, M.; Verma, A. K. Rh(III)催化炔基化：从氨基偶氮烯合成官能化喹啉. Chem. Commun. 2019, 55 (81), 12168–12171.
- (28) Martinez, R.; Ramón, D. J.; Yus, M. 从醇间接无过渡金属弗里德兰合成喹啉. J. Org. Chem. 2008, 73 (24), 9778–9780.
- (29) Harry, N. A.; Ujwalde, S. M.; Anilkumar, G. 无金属喹啉合成的最新进展与前景. Org. Biomol. Chem. 2020, 18 (48), 9775–9790.
- (30) Ghobadi, N.; Nazari, N.; Gholamzadeh, P. 弗里德兰反应：杂环合成的强大策略; Scriven, E. F. V. Ramsden, C. A. B. T.-A. H. C., Eds.; Academic Press, 2020; Vol. 132, Chapter 2, pp 85–134.
- (31) Chen, Y.; Stork, C.; Hirte, S.; Kirchmair, J. NP-Scout：小分子天然产物相似度定量与可视化的机器学习方法. Biomolecules 2019, 9 (2), 43.
- (32) Reker, D.; Schneider, P.; Schneider, G. 多目标主动机器学习可迅速改进构效关系模型并揭示新的蛋白质-蛋白质相互作用抑制剂. Chem. Sci. 2016, 7 (6), 3919–3927.
- (33) Herrera, V. M.; Khoshgoftaar, T. M.; Villanustre, F.; Furht, B. 用于LexisNexis高性能计算集群平台大数据分析的随机森林实现与优化. J. Big Data 2019, 6 (1), 68.
- (34) Ao, Y.; Li, H.; Zhu, L.; Ali, S.; Yang, Z. 线性随机森林算法及其在机器学习辅助测井回归建模中的优势. J. Pet. Sci. Eng. 2019, 174, 776–789.
- (35) Rodrigues, T. 机器学习中化学和生物数据的好、坏和丑. Drug Discovery Today: Technol. 2019, 32–33, 3–8.
- (36) Kanehko, H. 使用Y随机化估计适用性域中测试数据的预测性能. J. Chemon. 2019, 33 (9), 1–12.
