

动力学与声学中的问题。构建了一个基于PINN的深度学习框架，用于研究浅水中打桩运动和声波传播。详细分析了所提PINN方法的超参数敏感性。发现：1）神经网络中少量神经元即可获得满意结果；2）浅层平坦神经网络足以拟合，但增加层数可使训练和测试损失稳步降低；3）作为非线性算子，激活函数在将输入映射到输出方面起着重要作用，正弦函数是我们研究中打桩问题的最佳选择；4）建议使用较小学习率，因其稳定性良好。此外，我们建议采用一种新技术，即非零边界条件，以帮助神经网络避免懒惰学习。

在构建和优化PINN框架后，我们测试其从偏微分方程和实数据中学习的能力，以求解打桩的正问题和反问题。在我们的研究中，基于出色的前馈网络，PINN求解未知参数的能力相当出色。最后，为了将所提PINN方法与其他方法区分开来并探索所提PINN方法的可能性，我们主要在频率域和几何域开展了一些数值实验。PINN方法给出的位移和水下声压结果在宽频率和距离范围内与精确值吻合良好。

## CRediT 作者贡献声明

Quanzhou Jiang: 概念化，方法学，验证，正式分析，撰写 – 原稿。Xianzhong Wang: 方法学，撰写 – 审阅与编辑。Min Yu: 调查，监督。Min Tang: 监督。Bixin Zhan: 资源，可视化。Shuai Dong: 资源，可视化。

## 竞争利益声明

作者声明，他们没有已知的竞争性财务利益或个人关系，这些关系可能会对本文所报道的工作产生影响。

## 数据可用性

数据将根据要求提供。

## 致谢

本工作得到中国国家自然科学基金会（编号：52271291）和湖北省自然科学基金会（ZRMS2020000207）的资助。

## 参考文献

-   Alkhadh, Shaikhah, Mohamed, Almjekawy, 2021. 结合深度神经网络与物理学以求解Burger方程的反问题。载于：年度国际IEEE工程医学与生物学会议，第4465-4468页。
-   Amaral, Jennifer L., Miller, James H., Potty, Gopu R., Vigness-Raposa, Kathleen J., Lin, Ying-Tsong, Frankel, Adam S., Newhall, Arthur E., Wilkes, Daniel R., Gavrilov, Alexander N., 2022. 布洛克岛风电场冲击打桩水下声音分析。J. Acoust. Soc. Am. 151 (4), A239.
-   Bailey, Helen, Senior Dale Simmons, Bridget, Jan, Rusin, Gordon, Pickenc, Paul, M., Thompson, 2010. 评估海上风电场打桩期间水下噪声水平及其对海洋哺乳动物的潜在影响。Mar. Pollut. Bull. 60, 888-897.
-   Chen, Cheng, Meng, Hao, Yong-Zheng, Li, Zhang, Guang-Tao, 2021. 基于PINN的深度学习法求解圆柱2自由度涡激振动。Ocean. Eng. 240, 109932.
-   Cuomo, Salvatore, Schiano di Cola, Vincenzo, Giampaolo, Fabio, et al., 2022. 基于物理信息神经网络的科学机器学习：我们身处何处及未来何方 arXiv: 2201.056243.
-   Ellis, Dale D., Chapmain, D.M.F., 1985. 包含剪切波效应的简单浅水传播模型。J. Acoust. Soc. Am. 78 (6), 2087-2095.
-   Hall, Marshall V., 2013. 海上打桩水下声脉冲非马赫峰压的半解析模型。Acoust Austral. 41 (1), 42-51.
-   He, QiZhi, Barajas-Solano David, Guzel, Tartakovsky, Tartakovsky, Alexandre, M., 2020. 多物理场数据同化的物理信息神经网络及其在地下输运中的应用。Adv. Water Resour. 141, 103610.
-   Junger, Miguel C., Feit, David, 1986. 声音、结构及其相互作用。MIT出版社，剑桥。
-   Karmadikaris, George Em, Kevrekidis, Ioannis G., Lu, Lu, Paris, Perdikaris, Wang, Sifan, Liu, Yang, 2021. 物理信息机器学习。Nat. Rev. Phys. 3 (6), 422-440.
-   Kwok, Moon K., 2010. 接触无界外流体的有限圆柱壳自由振动分析。J. Fluid Struct. 26 (3), 377-392.
-   Lee, Soo Young, Chang, Jiho, Lee, Seungchul, 2021. 基于深度学习的多声源高精度高分辨率定位方法。Mech. Syst. Signal Process. 161.
-   Lippert, Tristan, Otto von Estorff, 2014. 参数不确定性对海上打桩噪声预测的重要性。J. Acoust. Soc. Am. 136 (5), 2463-2471.
-   Lippert, Stephan, Nijhof, Marten, Lippert, Tristan, Wildes, Daniel, 2016. COMPILE—一种用于海洋打桩噪声预测的通用基准代码。IEEE J. Ocean. Eng. 41 (4), 1061-1071.
-   Lu, Meng, Xuhui, Mao, Zhiping, Karmadikaris, George Em, 2021. DeepXDE：求解微分方程的深度学习库。Soc. Ind. Appl. Math. 63 (1), 208-228.
-   MacGillivray, Alexander O., 2013. 海洋冲击打桩产生的水下声级模型。J. Acoust. Soc. Am. 134 (5), 4024.
-   Madsen, P.T., Wahlberg, M., Tougaard, J., Lucke, K., Tyack, P., 2006. 风力涡轮机水下噪声与海洋哺乳动物：当前知识与数据需求的启示。Mar. Ecol. Prog. Ser. 309, 279-295.
-   Mao, Zhiping, Jagtap, Ameya D., Karmadikaris, George Em., 2020. 高速流动的物理信息神经网络。Comput. Methods Appl. Mech. Eng. 360, 112789.
-   Pang, Guofei, Lu, Lu, Karmadikaris, George Em., 2019. fPINNs：分数阶物理信息神经网络。SIAM J. Sci. Comput. 41 (4), 2603-2626.
-   Popper, A.N., Hastings, M.C., 2009. 人为声源对鱼类的影响。J. Fish. Biol. 75, 455-489.
-   Pye Henninger, Heidi, Watson, Winsor H., 2005. 美国龙虾（Homarus americanus）甲壳振动及相关水传声产生机制研究。J. Exp. Biol. 208, 3421-3429.
-   Raissi, M., Perdikaris, P., Karniadakis, G.E., 2019. 物理信息神经网络：求解涉及非线性偏微分方程的正问题与反问题的深度学习框架。J. Comput. Phys. 378, 686-707.
-   Raissi, Maziar, Yazdani, Alireza, Karmadikaris, George Em, 2020. 隐藏流体力学：从流场可视化中学习速度和压力场。Science 367 (6481), 1026-1030.
-   Reinhold, Per G., Dahl, Peter H., 2011. 冲击打桩水下马赫波辐射：理论与观测。J. Acoust. Soc. Am. 130 (3), 1209-1216.
-   Ryan Wilkes, Daniel, Tim, Gourlay, Alexander, Gavrilov, 2014. 近场打桩噪声时域建模数值方法比较。载于：INTER-NOISE和NOISE-CON大会及会议论文集，第2169-2178页。
-   Sacchetti, Andrea, Bachmann, Benjamin, Löffler, Kaspar, Kinzi, Urs-Martin, Paoli, Beatrice, 2022. 求解偏微分方程的神经网络：与有限元法的比较。IEEE Access 10, 32271-32279.
-   Tartakovsky, A.M., Ortiz Marrero, C., Paris, Perdikaris, Tartakovsky, G.D., Barajas-Solano, D., 2020. 用于学习地下流动问题中参数和本构关系的物理信息深度神经网络。Water Resour. Res. 56 (5), e2019WR026731.
-   Van der Kraan P. Inge, Hans, Slabbekoorn, Tom, Moens, Van den Eynde Dries, Jan, Reubens, 2022. 打桩声对比利时北海野生大西洋鳕鱼局部移动的影响。Environ. Pollut. 300.
-   Wight, Colby L., Jia, Zhao, 2021. 使用自适应物理信息神经网络求解Allen-Cahn和Cahn-Hilliard方程。Commun. Comput. Phys. 29, 930-954.
-   Yuan, Xue, Li, Yong, Zhang, Kai, Yang, Fuqian, 2022. 求解偏微分方程的物理启发神经网络——应用：扩散诱导应力。Phys. Chem. Chem. Phys. 24 (13), 7937-7949.
-   Zhang, Dongkun, Lu, Lu, Guo, Ling, Karmadikaris, George Em, 2019. 物理信息神经网络中求解正随机问题与反随机问题的总不确定性量化。J. Comput. Phys. 397, 108850.
-   Zhang, Dongkun, Guo, Ling, Karmadikaris, George Em, 2020. 模态空间中的学习：使用物理信息神经网络求解时变随机偏微分方程。SIAM J. Sci. Comput. 42 (2), 639-665.

