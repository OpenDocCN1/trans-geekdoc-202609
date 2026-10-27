

![](img/7831497378234ae52d1984f43fb0c693_4_0.png)

图4. 特征重要性：(a) C=O；(b) 吡啶氮；以及SHAP值：(c) C=O；(d) 吡啶氮。

![](img/7831497378234ae52d1984f43fb0c693_4_1.png)

图5. C=O和吡啶氮活性位点的部分依赖图：(a) C=O与热解温度；(b) C=O与升温速率；(c) C=O与保温时间；(d) 吡啶氮与热解温度；(e) 吡啶氮与升温速率；(f) 吡啶氮与保温时间。

吡啶氮活性位点含量对热解时间的部分依赖在约150 min前持续增加，之后略有下降并趋于稳定（图5f）。这表明，约150 min的最佳热解时间可提高吡啶氮活性位点含量，继续延长时间不会带来进一步的显著提升。因此，约400–600 °C的热解温度、5–10 °C/min的升温速率和约150 min的热解时间有利于吡啶氮活性位点的形成。所开发的ML模型展示了预测活性位点含量的能力。在不同热解条件下制备了四种SC（补充材料Text S1），并分析了SC样品的元素组成和活性位点分布。SC的制备和表征详情见补充材料中的表S3和表S4。通过XPS测量对SC样品的化学组成和活性位点分布进行了分析（补充材料图S1）。高分辨率C1s谱峰被解卷积为284.7、285.5、286.5和288.8 eV处的四个峰，分别对应C–C/C=C、C–N/C–O、C=O和O–C=O [47]。类似地，高分辨率N1s谱峰被解卷积为398.5、399.8和400.8 eV处的三个峰，分别对应吡啶氮、吡咯氮和石墨氮 [48]。测得的 C=O

![](img/7831497378234ae52d1984f43fb0c693_5_0.png)

![](img/7831497378234ae52d1984f43fb0c693_5_1.png)

图6. 活性位点的实测与ML预测含量：(a) C=O，(b) 吡啶氮。

含量在四个样品中分别为9.51%（SC1）、9.82%（SC2）、8.19%（SC3）和9.31%（SC4）。吡啶氮含量分别为23.90%（SC1）、29.91%（SC2）、21.22%（SC3）和27.79%（SC4）。使用ML模型预测四个样品中的活性位点含量，所有样品C=O位点的预测误差均低于10%，平均误差小于5.1%（图6a）。对于吡啶氮，预测误差分别为5.1%（SC1）、7.2%（SC2）、8.9%（SC3）和4.6%（SC4），平均误差为6.38%（图6b）。显然，该模型能够准确预测污泥衍生生物炭催化剂中的活性位点。

本研究开发了一种XGB模型来预测C=O活性位点的反应活性，并提出了一种结合Extra Trees和XGB的集成机器学习模型来预测吡啶氮。提出了一种新描述符，整合了与原料组成（包括铁）相关的内在因素和与制备参数相关的外在因素。模型结合该描述符，能够有效预测污泥（SS）衍生碳催化剂表面的C=O（R²=0.79，RMSE=0.0812）和吡啶氮（R²=0.80，RMSE=0.1386）活性位点。实验验证表明，C=O和吡啶氮活性位点的平均预测误差分别为5.1%和4.6%。此外，实现了对C=O和吡啶氮活性位点制备参数的高通量筛选。对于C=O活性位点，O%和升温速率作用最为显著，其次是N%和热解温度。同时，C%和Fe%影响中等，热解时间对总体影响的贡献最小。此外，C=O活性位点的最佳热解条件确定为热解温度500–800 °C、升温速率10–20 °C/min、加热时间120–200 min。对于吡啶氮活性位点，C%和热解温度起主导作用，其次是N%和保温时间。同时，O%和Fe%影响中等，升温速率贡献最小。吡啶氮的最佳热解条件确定为热解温度400–600 °C、升温速率5–10 °C/min、热解时间约150 min。为精确制备高活性污泥衍生碳催化剂奠定了坚实基础。

## 利益冲突声明

作者声明，他们不存在任何已知的、可能影响本文所报告工作的竞争性经济利益或个人关系。

## CRediT作者贡献声明

Xu He：写作—审阅与编辑、写作—初稿、方法论、形式分析、概念化。Wenjie Gao：写作—初稿、形式分析。Jinglei Xu：写作—审阅与编辑、写作—初稿。Zhanjun Cheng：写作—审阅与编辑。Wenchao Peng：写作—初稿。Beibei Yan：写作—审阅与编辑。Guanyi Chen：写作—初稿、概念化。Ning Li：写作—审阅与编辑、写作—初稿、形式分析。

## 致谢

本工作得到了天津市青年科技人才（第二层次）（No. QN20230214）、天津大学攀登计划（No. 2023XPD-0006）、国家自然科学基金（No. 52100156）和城市轨道交通数字化建设与测评技术国家工程研究中心（No. 2023HJ02）的资助。

## 补充材料

与本文相关的补充材料可在在线版本中找到，doi:10.1016/j.cclet.2025.111019。

## 参考文献

- [1] Y. Duan, N. Gao, A.T. Sipra, et al., J. Hazard. Mater. 424 (2022) 127293.
- [2] Y. Li, H. Yu, L. Liu, et al., J. Hazard. Mater. 420 (2021) 126655.
- [3] W. Zheng, Y. Shao, S. Qin, Sustainability 16 (2024) 6710.
- [4] S.S.A. Syd-Hassan, Y. Wang, S. Hu, S. Su, et al., Renew. Sustain. Energy. Rev. 80 (2017) 888-913.
- [5] E. Agrafioti, G. Bouras, D. Kalderis, et al., J. Anal. Appl. Pyrolysis 101 (2013) 72-78.
- [6] J. Lu, Q. Lu, L. Di, et al., Chin. Chem. Lett. 34 (2023) 108357.
- [7] J. Xu, Y. Yu, K. Ding, et al., Water Sci. Technol. 77 (2018) 1410-1417.
- [8] Z.X. Xu, H. Song, P.J. Li, et al., J. Hazard. Mater. 398 (2020) 122833.
- [9] W. Hu, J. Tan, G. Pan, et al., Sci. Total Environ. 728 (2020) 138853.
- [10] Y. Wang, W. Peng, J. Wang, Appl. Catal. B 310 (2022) 121342.
- [11] P. Zhang, Y. Yang, X. Duan, ACS Catal. 11 (2021) 11129-11159.
- [12] H. Zhang, Z. Yan, J. Wan, Colloids Surf. A: Eng. Asp. 654 (2022) 130174.
- [13] N. Li, Y. Ye, H. Dai, Water Res. 235 (2023) 119926.
- [14] C. Zhang, N. Ding, Y. Pan, et al., Chin. Chem. Lett. 35 (2024) 109579.
- [15] J. Wang, Z. Liao, J. Ifthikar, et al., Chemosphere 185 (2017) 754-763.
- [16] S. Singh, V. Kumar, D.S. Dhanjal, et al., J. Clean. Prod. 269 (2020) 122259.
- [17] X. Pei, X. Peng, X. Jia, et al., J. Hazard. Mater. 419 (2021) 126446.
- [18] L. Kou, Y. Wang, L. Zhao, et al., Chem. Eng. J. 411 (2021) 128459.
- [19] M.M. Mian, G. Liu, H. Zhou, et al., Sci. Total Environ. 744 (2020) 140862.
- [20] Z. Liu, S. Singer, Y. Tong, et al., Renew. Sustain. Energy. Rev. 90 (2018) 151174.
- [21] Y. Liu, S. Yang, S. Liu, et al., J. Anal. Appl. Pyrolysis 182 (2024) 106696.
- [22] Y. Liu, S. He, B. Huang, et al., J. Energy. Chem. 70 (2022) 511-520.
- [23] J.H. Kim, J.K. Shin, H. Lee, et al., Water Res. 207 (2021) 117821.
- [24] S. Russo, M.D. Besmer, F. Blumensaat, et al., Water Res. 206 (2021) 117695.
- [25] Z. Li, S. Zou, Z. Wang, et al., Chin. Chem. Lett. 35 (2024) 110526.
- [26] J. Li, X. Liu, H. Wang, et al., Chin. Chem. Lett. 35 (2024) 108596.
- [27] W. Gao, N. Li, Z. Cheng, et al., Bioresour. Technol. 408 (2024) 131156.
- [28] R. Wang, S. Zhang, H. Chen, et al., Environ. Sci. Technol. 57 (2023) 4050-4059.
- [29] M.A. Ganaie, M. Hu, A.K. Malik, et al., Eng. Appl. Artif. Intell. 115 (2022) 105151.
- [30] X. Dong, Z. Yu, W. Cao, et al., Front. Comput. Sci. 14 (2020) 241-258.
- [31] B. Deng, P. Chen, P. Xie, et al., Chem. Eng. Sci. 267 (2023) 118368.
- [32] D. Wu, D. Zhang, S. Liu, et al., J. Chem. Eng. J. 399 (2020) 125878.
- [33] A. Smith, A. Keane, J.A. Dumesic, et al., Appl. Catal. B 263 (2020) 118257.
- [34] F. Rodrigues, N. Ortelli, M. Bierlaire, et al., IEEE. Trans. Intell. Transp. Syst. 23 (2022) 3126-3136.

