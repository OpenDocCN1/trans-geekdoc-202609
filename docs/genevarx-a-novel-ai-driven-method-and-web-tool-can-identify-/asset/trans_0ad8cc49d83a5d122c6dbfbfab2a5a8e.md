

![](img/5167e39db543350967ce62ea50022e12_16_0.png)

![](img/5167e39db543350967ce62ea50022e12_16_1.png)

![](img/5167e39db543350967ce62ea50022e12_16_2.png)

![](img/5167e39db543350967ce62ea50022e12_16_3.png)

![](img/5167e39db543350967ce62ea50022e12_16_4.png)

图 18. 使用 Dataset3 时，关于健康对照组和 LP 的预测结果。箱线图和散点图（a–d）分别显示了 ssvm1、ssvm2、ssvm3 和 lasso 中健康个体与 LP 个体的预测 LP 差异。（e）通过沿 y 轴显示真阳性率、沿 x 轴显示假阳性率，演示了每个模型的 ROC 曲线。

控制组或 LP）。我们随后将输入数据集提供给三种基于机器学习的方法。所有方法均为 SVM 的新型稀疏版本。每种方法的输出均为权重向量 w。我们根据 w 中对应的前 p 个权重选择了前 p 个基因，并将我们的方法和其他基线方法所选基因输入到富集分析工具 Enrichr 和 Metascape 中。结果表明，我们的方法在疾病识别方面优于基线方法，显示出更多的表达基因，并能更好地识别具有更多表达基因的组织类型。通过进一步的富集分析，我们鉴定出 5 种药物（例如，地塞米松、维甲酸和槲皮素）、23 个独特的转录因子（例如，NFKB1、p65、HDAC1、STAT1、STAT3）和 45 个独特基因（例如，PSMB8、PSMB10、PSMB9、KRT31、KRT16、KRT19、KRT17、KRT15、COL3A1、LCE2D、LCE2A），这些基因已被报道与 T 细胞介导的自身免疫性炎症机制、治疗靶点以及 LP 的治疗相关。我们的方法可在 GENEvaRX 网络服务器上公开获取，网址为 https://aibio.shinyapps.io/GENEvaRX/。

未来工作包括：
- (1) 将我们的计算框架应用于识别银屑病、特应性皮炎和狼疮等不同皮肤疾病中的重要表达基因、治疗靶点和药物；
- (2) 与医院合作，在临床试验中使用我们的工具；
- (3) 使用我们的方法从基因表达数据中识别基因签名；
- (4) 比较通过不同高通量技术生成的基因表达数据，并从生物学角度进行评估；以及
- (5) 研究 LP 变异体之间的共享分子机制及其参与情况。

## 资助

本项目由沙特阿拉伯吉达国王阿卜杜勒阿齐兹大学科学研究院（DSR）资助，资助编号为（D-087-611-1440）。因此，作者谨向 DSR 提供的技术和财务支持表示衷心感谢。

## CRediT 作者贡献声明

Turki Turki：概念化，形式分析，方法学，数据整理，软件，监督，撰写 – 原始草稿，可视化，调查。Y.-h. Taguchi：概念化，形式分析，方法学，数据整理，验证，撰写 – 原始草稿。

![](img/5167e39db543350967ce62ea50022e12_17_0.png)

图 19. 通过 ssvm1 (a)、ssvm2 (b)、ssvm3 (c) 和 lasso (d) 生成的与 Dataset3 相关的所有基因的基因重要性。

## 利益冲突声明

作者声明，他们没有已知的可能影响本文所报告工作的竞争性财务利益或个人关系。

## 数据可用性

在补充文件 GENEvaRX_Screenshots.docx 中，我们演示了网络工具的使用。本研究中使用的所有数据均在手稿中引用，并可从 GEO 获取，登录号为

- GSE63741
- GSE193351
- GSE52130

## 附录 A. 补充数据

与本文相关的补充材料可在线查阅，网址为 https://doi.org/10.1016/j.engappai.2023.106607。

## 参考文献

- Abé, T., Kitagawa, N., Yoshimoto, S., Maruyama, S., Yamazaki, M., Inai, T., Hashimoto, S., Saku, T., 2020. 口腔扁平苔藓中角蛋白 17 阳性 Civatte 小体——分布多样性、诊断意义及组织发生学。Sci. Rep. 10, 14586.
- Ah Kioon, M.D., Pierides, M., Pannellini, T., Lin, G., Nathan, C.F., Barrat, F.J., 2021. 非细胞毒性抑制免疫蛋白酶体可调节体外人类免疫细胞并抑制小鼠皮肤炎症。J. Immunol. 206, 1631–1641.
- Ahn, S.J., Kwon, H., Yang, J.-J., Park, M., Cha, Y.J., Suh, S.H., Lee, J.-M., 2020. 脑转移增强 T1 加权像放射组学可能预测原发性肺癌的 EGFR 突变状态。Sci. Rep. 10, 1–9.
- Ahn, S.S., Yeo, H., Jung, E., Lim, Y., Lee, Y.H., Shin, S.Y., 2022. FRA1: C-JUN: HDAC1 复合物在角质细胞中 TNFα 和 IFNγ 刺激下下调丝聚蛋白表达。Proc. Natl. Acad. Sci. 119, e2121451119.
- Alabdulally, L., Villa, A., Chen, T., Kerr, A., Ross, N., Alves, F.A., Guollo, A., Woo, S.-B., 2022. 增生性白斑初期/早期组织学特征的表征及其与恶性转变的相关性：一项多中心研究。Mod. Pathol. 35, 1034–1044.
- Anderton, H., Alqudah, S., 2022. 皮肤功能、炎症和疾病中的细胞死亡。Biochem. J. 479, 1621–1651.
- Astudillo, M.G., Hoang, M.P., Nazarian, R.M., Foreman, R.K., 2021. 增生性扁平苔藓与鳞状细胞癌的鉴别在困难病例中需要临床病理相关性。Am. J. Dermatopathol. 43, 349–355.
- Baek, K., Lee, J., Lee, A., Lee, J., Yoon, H.-J., Park, H.K., Chun, J., Choi, Y., 2020. 口腔扁平苔藓病变中组织内细菌群落的表征及大肠埃希菌分离。Sci. Rep. 10 (3495).
- Barrett, T., Wilhite, S.E., Ledoux, P., Evangelista, C., Kim, I.F., Tomashevsky, M., Marshall, K.A., Phillamy, K.H., Sherman, P.M., Holko, M., Yefanov, A., Lee, H., Zhang, N., Robertson, C.L., Serova, N., Davis, S., Soboleva, A., 2012. NCBI GEO：功能基因组学数据集档案——更新。Nucleic Acids Res. 41, D991–D995.
- Bi, M., Zhang, Z., Jiang, Y.-Z., Xue, P., Wang, H., Lai, Z., Fu, X., De Angelis, C., Gong, Y., Gao, Z., 2020. 由转录因子高阶组装驱动的增强子重编程促进表型可塑性和乳腺癌内分泌耐药性。Nature Cell Biol. 22, 701–715.
- Boudreaux, B., Bhullar, P., Brumfiel, C., 2022. 34004 外用鲁索替尼阻断皮肤扁平苔藓中的干扰素伽马信号传导。J. Am. Acad. Dermatol. 87, AB121.
- Braegel, C., Fetter, T., Niebel, D., Dietz, L., Bieber, T., Wenzel, J., 2021. 具有免疫刺激作用的内源性核酸使界面性皮炎持续存在——将致病基础转化为体外模型。Front. Immunol. 11, 622511.
- Brehm, F., Haenssle, H.A., Schön, M.P., Emmert, S., 2011. 3 例难治性扁平苔藓对阿利雷汀的反应。J. Am. Acad. Dermatol. 65, e58–e60.
- Budimir, J., Mravak-Stipetić, M., Bulat, V., Jerčec, I., Japundžić, L., Ugičević-Mihić, L., 2019. 口腔及口周疾病中的过敏反应——过敏皮肤测试结果显示什么？Oral surgery. Oral Med. Oral Pathol. Oral Radiol. 127, 40–48.
- Burgess, J., 1941. 维生素 B 复合物治疗扁平苔藓。Can. Med. Assoc. J. 44 (120).
- Chen, J., Du, G., Wang, Y., Shi, L., Mi, J., Tang, G., 2017. 口腔扁平苔藓中 mRNA 和 miRNA 表达谱的整合分析：初步结果。Oral Surg. Oral Med. Oral Pathol. Oral Radiol. 124, 390–402. e317.
- Chen, Z., Shi, T., Zhang, X., Jia, K., Jiang, H., Yuan, B., 2022a. 基于哨兵-2 植被指数的薯蓣叶面积指数混合估计方法。IEEE Trans. Geosci. Remote Sens. 60, 1–13.
- Chen, J.F., Zhang, X.M., Sanjel, K., Zhang, J., Ma, C., 2022b. 皮肤扁平苔藓中 TNF-α 和 NF-κB/p65 的表达及其意义。Clin. Cosmet. Investig. Dermatol. 1509–1516.
- Cosgarea, R., Pollmann, R., Sharifi, J., Schmidt, T., Stein, R., Bodea, A., Ausschill, T., Sculean, A., Emling, R., Greene, B., 2020. 口腔扁平苔藓的光动力疗法：一项前瞻性病例对照试点研究。Sci. Rep. 10, 1–11.
- Crow, Y.J., Stetson, D.B., 2022. 1 型干扰素病：10 年回顾。Nat. Rev. Immunol. 22, 471–483.
- Davis, S., Meltzer, P.S., 2007. GEOquery：基因表达 omnibus (GEO) 与 BioConductor 之间的桥梁。Bioinformatics 23, 1846–1847.
- de Lanna, C.A., da Silva, B.N.M., de Melo, A.C., Bonamino, M.H., Alves, L.D.B., Pinto, L.F.R., Cardoso, A.S., Antunes, H.S., Boroni, M., Cohen Goldberg, D., 2022. 口腔扁平苔藓与口腔鳞状细胞癌共享关键致癌特征。Sci. Rep. 12 (20645).
- Deng, S., Xu, Y., Wang, X., Liu, M., Li, L., Yu, X., Wang, Y., Wu, Y., Wang, W., Gao, M., 2020. 唾液菌群和 NF-κB 炎症信号通路在口腔扁平苔藓中的作用研究。Inflammation 43, 994–1008.
- D’Erme, A.M., Wilhelm-Thiess, D., Wagenpfeil, J., Hölzel, M., Ferring-Schmitt, S., Sternberg, S., Wittmann, M., Peters, B., Bosio, A., Bieber, T., 2015. IL-36γ (IL-1F9) 是银屑病皮损的生物标志物。J. Invest. Dermatol. 135, 1025–1032.
- Didona, D., Caro, R.D.C., Santos, A.M.S., Solimani, F., Hertl, M., 2022. 口腔扁平苔藓的治疗策略：现状与新见解。Front. Med. 9.
- Du, J., Gao, R., Wang, Y., Nguyen, T., Yang, F., Shi, Y., Liu, T., Liao, W., Li, R., Zhang, F., 2020. MicroRNA-26a/b 在口腔扁平苔藓中具有保护作用。Cell Death Dis. 11 (15).
- Du, Y., Yang, Y., Zhang, W., Yang, C., Xu, P., 2023. 人类 β-防御素-3 和核因子-κB p65 协同促进口腔鳞状细胞癌细胞增殖和侵袭。Transl. Oncol. 27, 101582.
- Durinck, S., Spellman, P.T., Birney, E., Huber, W., 2009. 使用 R/Bioconductor 包 biomaRt 进行基因组数据集整合的标识符映射。Nat. Protoc. 4, 1184–1191.
- Dussoyer, M., Page, A., Delolme, F., Rousselle, P., Nyström, A., Moali, C., 2022. 用于改进质谱法皮肤基质组表征的细胞外基质富集方案比较。J. Proteomics 251, 104397.
- Evert, K., Kocher, T., Schnidler, A., Müller, M., Müller, K., Pink, C., Holtfreter, B., Schmidt, A., Dombrowski, F., Schubert, A., 2021. 12 个月内反复用冷等离子体暴露口腔黏膜在小鼠中不致癌。Sci. Rep. 11 (20672).
- Farah, C.S., Fox, S., Shearston, K., Newman, L., Babic, S., Vacher, M., 2021. 苔藓样发育不良不是独立的病理实体。Oral Oncol. 119, 105362.
- Feng, W., Dauphin, G., Huang, W., Quan, Y., Liao, W., 2019. 用于分类的修正随机森林中新的基于边界的子采样迭代技术。Knowl.-Based Syst. 182, 104845.
- Friedman, J., Hastie, T., Tibshirani, R., 2010. 通过坐标下降法对广义线性模型进行正则化路径分析。J. Stat. Softw. 33 (1).
- Fu, A., Narasimhan, B., Boyd, S., 2020. CVXR：一种用于规范凸优化的 R 包。J. Stat. Softw. 94, 1–34.
- Hassanandani, T., 2020. 15346 面部色素性扁平苔藓的皮肤镜与组织病理学相关性：一项观察性研究。J. Am. Acad. Dermatol. 83, AB37.
- Huang, J., Heng, S., Zhang, W., Liu, Y., Xia, T., Ji, C., Zhang, 2022. 皮肤发育、稳态、伤口再生和疾病中的真皮细胞外基质分子。Sem. Cell Dev. Biol. 128, 137–144.
- Huber, W., Carey, V.J., Gentleman, R., Anders, S., Carlson, M., Carvalho, B.S., Bravo, H.C., Davis, S., Gatto, L., Girke, T., 2015. 使用 Bioconductor 进行高通量基因组学分析的协调。Nature Methods 12, 115–121.
- Jiao, L., Liu, Y., Yu, X.-Y., Pan, X., Zhang, Y., Tu, J., Song, Y.-H., Li, Y., 2023. 疾病中的核糖体生物发生：新参与者和治疗靶点。Signal Transduct. Target. Ther. 8 (15).
- Keeley, A., Petri, L., Ábrányi-Balogh, P., Keserű, G.M., 2020. 药物发现中的共价片段库。Drug Discov. Today 25, 983–996.
- Kuleshov, M.V., Jones, M.R., Rouillard, A.D., Fernandez, N.F., Duan, Q., Wang, Z., Koplev, S., Jenkins, S.L., Jagodnik, K.M., Lachmann, A., Lafta-Navarro, M.C., Conac-Sorell, M., 2023. 核仁应激：从发育到癌症。Sem. Cell Dev. Biol. 136, 64–74.
- Laurence Le Cleach, M., Chosidow, O., 2012. 扁平苔藓。N. Engl. J. Med. 366, 723–732.
- Lee, T.A., Han, H., Polish, A., Cho, S.K., Lee, J.W., Ra, E.A., Lee, E., Park, A., Kang, S., Choi, J.J., 2022. 感染期间核仁是炎症性 RNA 降解的场所。Nature Commun. 13 (5203).
- Lee, J.Y., Hong, J.S., Lee, S.H., Ayy, Y., 2019. 用阿利雷汀成功治疗额部纤维化脱发。Dermatol. Ther. 32, e13037.
- Li, C., Tang, X., Zheng, X., Ge, S., Wen, H., Lin, X., Chen, Z., Lu, L., 2020. 口腔扁平苔藓的全球患病率和发病率估计：系统评价和荟萃分析。JAMA Dermatol. 156, 172–181.
- Li, Q., Wang, F., Shi, Y., Zhong, L., Duan, S., Kuang, W., Liu, N., Luo, E., Zhou, Y., Jiang, L., 2023. 单细胞免疫谱分析揭示口腔扁平苔藓中的免疫反应。Front. Immunol. 14.
- Masle-Farquhar, E., Jackson, K.J.L., Peters, T.J., Al-Eryani, G., Singh, M., Payne, K.J., Rao, G., Avery, D.T., Apps, G., Kingham, J., Jara, C.J., Skvotrsova, K., Swarbrick, A., Ma, C.S., Suan, D., Uzel, G., Chua, I., Leiding, J.W., Heiskanen, K., Preece, K., Kainulainen, L., O'Sullivan, M., Cooper, M.A., Seppänen, M.R.J., Mustjoki, S., Brothers, S., Vogel, T.P., Brink, R., Tangye, S.G., Reed, J.H., Goodnow, C.C., 2022. STAT3 功能获得性突变通过病理性 NKG2Dhi CD8+ T 细胞失调和积累将白血病与自身免疫性疾病联系起来。Immunity 55, 2386–2404. e2388.
- Meng, Z., Zhang, H., Li, L., Wang, K., 2021. miR-142-3p 在口腔扁平苔藓中的临床意义及其在角质细胞增殖中的调节作用。Oral Surg. Oral Med. Oral Pathol. Oral Radiol. 132, 441–447.
- Moitinho-Silva, L., Degenhardt, F., Rodriguez, E., Emmert, H., Juzenas, S., Môbus, L., Uellendahl-Werth, F., Sander, N., Baurecht, H., Tittmann, L., 2022. 与先天免疫、环境感知和细胞功能相关的宿主遗传因素与人类皮肤微生物群相关。Nature Commun. 13, 6204.
- Muradova, E., Negrieni, E., Berke, A., 2022. 35283 接种 Moderna COVID-19 疫苗后出现的皮肤黏膜扁平苔藓。J. Am. Acad. Dermatol. 87, AB83.
- Pattil, S., Hosmani, J., Khan, Z.A., Yadalam, P.K., Ahmed, Z.H., Bhandi, S., Awan, K.H., 2023. 免疫介导口腔疾病治疗策略的进展。Disease-A-Month 69, 101352.
- Pattil, S., Yadalam, P.K., Hosmani, J., Khan, Z.A., Ahmed, Z.H., Shankar, V.G., Awan, K.H., 2022. 具有恶性潜能/关联的口腔免疫介导性疾病：概述。Disease-A-Month 101349.
- Phatale, V., Vaipehi, K.K., Jha, S., Pattil, D., Agrawal, M., Alexander, A., 2022. 通过先进的经皮给药方法克服皮肤屏障。J. Control. Release 351, 361–380.
- Pitak-Arnnop, P., Subalekha, K., Sirintawat, N., Tangmanee, C., Aychai, P., Muangchan, C., Sukhopetch, P., Mengaud, J.-P., Neff, A., 2022. 口腔扁平苔藓患者是否有丙型肝炎高风险？一项病例对照研究。J. Stomatol. Oral Maxillofac. Surg. 123, e37–e42.
- Povey, S., Lovering, R., Bruford, E., Wright, M., Lush, M., Wain, H., 2001. HUGO 基因命名委员会 (HGNC)。Human Genet. 109, 678–680.
- Qian, Y.-T., Liu, X.-Y., Sun, H.-D., Xu, J.-Y., Sun, J.-M., Liu, W., Chen, T., Liu, J.-W., Tan, Y., Sun, W., 2022. 活动性白癜风患者的尿蛋白组学分析：用于类固醇治疗疗效预测和监测的生物标志物。Front. Mol. Biosci. 9 (92).
- Qiao, Y., Liu, B., Bai, R., Cai, J., Peng, Q., 2022. 由角蛋白 4 基因突变引起的白色海绵状痣：一例病例报告。Genes 13 (2184).
- Ramos-García, P., Gonzalez-Moles, M.A., Warnakulasuriya, S., 2022. p53 过表达在口腔潜在恶性疾病恶性转变风险预测中的意义：系统评价和荟萃分析。Oral Oncol. 126, 105734.
- Reimann, J.D., Moynihan, S.P., Horn, T.D., 2021. 皮肤直接免疫荧光试验的临床和实验室应用评估。JAMA Dermatol. 157, 1343–1348.
- Ritchie, M.E., Phipson, B., Wu, D., Hu, Y., Law, C.W., Shi, W., Smyth, G.K., 2015. limma 为 RNA 测序和芯片研究中的差异表达分析提供支持。Nucleic Acids Res. 43, e47.
- Rivera, C., Crisóstomo, M.F., Peña, C., González-Díaz, P., González-Arriagada, W.A., 2020. 口腔扁平苔藓相互作用组揭示 CXCR4 和 CXCL12 作为候选治疗靶点。Sci. Rep. 10, 1–8.
- Sahoo, A., Jena, A.K., Panda, M., 2022. 植物提取物、植物化学物质和植物制剂在口腔扁平苔藓治疗中的实验和临床试验研究：系统评价。J. Ethnopharmacol. 115591.
- Salazar, J., Carmona, T., Zaccori, F.C., Venegas-Yazigi, D., Cabello-Verrugio, C., Il Choi, W., Vilos, C., 2022. 人类真皮作为治疗皮肤疾病的纳米靶点。Pharmaceutics 15 (10).
- Sandhu, S., Klein, B.A., Al-Hadlaq, M., Chiravuri, P., Bajonaid, A., Xu, Y., Intini, R., Hussein, M., Vacharotayangul, P., Sroussi, H., 2022. 口腔扁平苔藓：比较疗效和治疗成本——系统评价。BMC Oral Health 22, 1–21.
- Schreurs, O., Karatsaidis, A., Balta, M.G., Grung, B., Hals, E.K., Schenck, K., 2020. 萎缩性口腔扁平苔藓上皮中角蛋白 8、18 和 19 的表达。Eur. J. Oral Sci. 128, 7–17.

