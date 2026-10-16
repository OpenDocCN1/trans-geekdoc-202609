
该公式表明，修改后的位置`v[ij]`是食物源位置`x[ij]`的加权和以及两个食物源位置`x[ij]`与`x[kj]`之差的加权和，其中`A`表示目标食物源的质量，`B`表示随机分布在实数范围[-1, 1]中的`ϕ[ij]`的质量差。在基本的`ABC`中，`A`通常设为1，而`B`则随机均匀分布在[-1, 1]范围内。

- 许多研究都对`ϕ[ij]`的变化进行了探讨，以实现更好的搜索机制（Karaboga et al. 2014）。为了获得更好的输出，还需对数值和取值范围进行精细调整。
- 为提升性能，`ABC`的有效修改和实现应当被广泛采用。可以观察到，`ABC`的许多部分可以并行执行。为了评估性能和适应度，唯一的方法是对每个解进行并行实现；否则，蜜蜂会分布在不同处理器上，无法在独立求解之间获得改进。虽然蜜蜂之间存在依赖关系，但考虑到共享内存架构的实现，并行化`ABC`是必要的，以消除这些依赖。
- `ABC`的观察者蜂基本阶段采用轮盘赌选择方案，其中每个片段的适应度值直接比例于选择合适食物源的概率（Zhu and Kwong 2010）。
- `ABC`是多目标优化算法，旨在同时优化两个或多个目标（Banharnsakun et al. 2010）。随着目标数量的增加，传统的以 Pareto 为基础的方法（如 MOEA）可能表现不佳。为解决这一问题，`ABC`的多目标变体应当在其特性研究中得到扩展（Gao et al. 2014）。

- Baykaso, Adil, Lale Özbakır, and Pınar Tapkan。2007。人工蜜蜂群算法及其在广义分配问题中的应用。Swarm Intelligence: Focus on Ant and Particle Swarm Optimization。
- Beg, Mirza Samiulla, Akhilesh A. Waoo, Ritu Gautam, Prableen Kaur, Manik Sharma, Yan Song, Lidong Huang, et al. 2012。改进二进制粒子群算法用于基因表达数据的特征选择。计算生物学与化学 32 (1)，29–38。doi:[10.1016/j.compbiolchem.2007.09.005](http://dx.doi.org/10.1016/j.compbiolchem.2007.09.005)。
- Brezočnik, Lucija, Iztok Fister, and Vili Podgorelec。2018。蜂群智能算法用于特征选择：综述。应用科学（瑞士）8 (9)。doi:[10.3390/app8091521](http://dx.doi.org/10.3390/app8091521)。
- Chang, Po Chun, and Xiangjian He。2014。宏观不确定性群优化（MISO）算法用于实参数搜索。2014 IEEE 进化计算会议论文集，1571–1578。doi:[10.1109/CEC.2014.6900281](http://dx.doi.org/10.1109/CEC.2014.6900281)。
- Chuang, Li Yeh, Hsueh Wei Chang, Chung Jui Tu, and Cheng Hong Yang。2008。改进二进制粒子群算法用于基因表达数据的特征选择。计算生物学与化学 32 (1)，29–38。doi:[10.1016/j.compbiolchem.2007.09.005](http://dx.doi.org/10.1016/j.compbiolchem.2007.09.005)。
- Djaballah, Chouaib Ben, and Wahid Nouibat。2022。基于全局和局部最优的新型多种群人工蜜蜂算法用于数值优化。集群计算。doi:[10.1007/s10586-021-03507-w](http://dx.doi.org/10.1007/s10586-021-03507-w)。
- El-Abd, Mohammed。2011。对抗式人工蜜蜂群算法。遗传与进化计算会议，GECCO’11，第 1 期，109–115。doi:[10.1145/2001576.2001592](http://dx.doi.org/10.1145/2001576.2001592)。
- Gao, Wei Feng, San Yang Liu, and Ling Ling Huang。2014。通过利用更多信息基于搜索方程增强人工蜜蜂群算法。信息科学 270，112–133。doi:[10.1016/j.ins.2014.02.104](http://dx.doi.org/10.1016/j.ins.2014.02.104)。
- Garlapati, Vijay Kumar, and Rintu Banerjee。2010。基于进化和群体智能的酶提取从发酵液中的优化方法。工程生命科学 10 (3)，265–273。doi:[10.1002/elsc.200900086](http://dx.doi.org/10.1002/elsc.200900086)。
- Garoudja, Elyes, Kamel Kara, Aissa Chouder, and Santiago Silvestre。2015。使用人工蜜蜂群优化对光伏模块参数的长期预测。第 3 届控制、工程与信息技术国际会议，CEIT 2015。doi:[10.1109/CEIT.2015.7232993](http://dx.doi.org/10.1109/CEIT.2015.7232993)。
- Garro, Beatriz A., Humberto Sossa, and Roberto A. Vazquez。2011。通过人工蜜蜂群（ABC）算法进行人工神经网络合成。2011 IEEE 进化计算会议论文集，331–338。doi:[10.1109/CEC.2011.5949637](http://dx.doi.org/10.1109/CEC.2011.5949637)。
- Gautam, Ritu, Prableen Kaur, and Manik Sharma。2019。基于自然启发式计算算法的慢性人类疾病诊断综述。进展人工智能 8 (4)，401–424。doi:[10.1007/s13748-019-00191-1](http://dx.doi.org/10.1007/s13748-019-00191-1)。
- Hakli, Huseyin, and Mustafa Servet Kiran。2020。改进的人工蜜蜂群算法，以平衡连续优化中的局部和全局搜索行为。机器学习与网络学报 11 (9)，2051–2076。doi:[10.1007/s13042-020-01094-7](http://dx.doi.org/10.1007/s13042-020-01094-7)。
- Harrison, Kyle Robert, Andries P. Engelbrecht, and Beatrice M. Ombuki-Berman。2018。自适应粒子群优化：综述与收敛分析。Swarm Intelligence。第 12 卷。Springer US。doi:[10.1007/s11721-017-0150-9](http://dx.doi.org/10.1007/s11721-017-0150-9)。
- Hsieh, Tsung Jung, and Wei Chang Yeh。2011。基于正交设计蜜蜂群算法的网格方案最小二乘支持向量机用于知识发现。IEEE 系统、人、和 cybernetics 部分 B：cybernetics 41 (5)，1198–1212。doi:[10.1109/TSMCB.2011.2116007](http://dx.doi.org/10.1109/TSMCB.2011.2116007)。
- Hu, Yu, Zhensheng Sun, Lijia Cao, Yin Zhang, and Pengfei Pan。2021。基于塔布搜索人工蜜蜂群和改进遗传算法的混合方法用于涡扇发动机气路传感器配置优化。航空科学与技术 112。doi:[10.1016/j.ast.2021.106642](http://dx.doi.org/10.1016/j.ast.2021.106642)。
- Ilie, Sorin, and Costin Bădicǎ。2013。多智能体分布式框架用于群体智能。程序计算机科学 18，611–620。doi:[10.1016/j.procs.2013.05.225](http://dx.doi.org/10.1016/j.procs.2013.05.225)。
- Irani, Rasoul, and Reza Nasimi。2011。基于人工蜜蜂群神经网络的井下压力预测在下平衡钻井中的应用。石油科学与工程 78 (1)，6–12。doi:[10.1016/j.petrol.2011.05.006](http://dx.doi.org/10.1016/j.petrol.2011.05.006)。
- Karaboga, Dervis, and Bahriye Basturk。2007。人工蜜蜂群（ABC）算法：一种强大且高效的数值函数优化算法。全球优化期刊 39 (3)，459–471。doi:[10.1007/s10898-007-9149-x](http://dx.doi.org/10.1007/s10898-007-9149-x)。
- Karaboga, Dervis, Beyza Gorkemli, Celal Ozturk, and Nurhan Karaboga。2014。人工蜜蜂群（ABC）算法及其应用综合调查。人工智能评论 42 (1)，21–57。doi:[10.1007/s10462-012-9328-0](http://dx.doi.org/10.1007/s10462-012-9328-0)。
- Kashan, Mina Husseinzadeh, Nasim Nahavandi, and Ali Husseinzadeh Kashan。2012。DisABC：一种用于二进制优化的新型人工蜜蜂群算法。应用软计算期刊 12 (1)，342–352。doi:[10.1016/j.asoc.2011.08.038](http://dx.doi.org/10.1016/j.asoc.2011.08.038)。
- Kasihmuddin, Mohd Shareduwan Mohd, Mohd Asyraf Mansor, Shehab Abdulhabib Alzaeemi, and Saratha Sathasivam。2021。通过人工蜜蜂群算法的径向基函数神经网络进行满足性逻辑分析。国际交互多媒体与人工智能期刊 6 (6)，164–173。doi:[10.9781/ijimai.2020.06.002](http://dx.doi.org/10.9781/ijimai.2020.06.002)。
- Kurban, Tuba, and Erkan Beşdok。2009。RBF 神经网络训练算法在惯性传感器基于地形分类中的比较。传感器 9 (8)，6312–6329。doi:[10.3390/s90806312](http://dx.doi.org/10.3390/s90806312)。
- Leu, Min Shyang, and Ming Feng Yeh。2012。灰粒子群优化。应用软计算期刊 12 (9)，2985–2996。doi:[10.1016/j.asoc.2012.04.030](http://dx.doi.org/10.1016/j.asoc.2012.04.030)。
- 李, 白, 穆林, 乔刘, 亚李, 以及张俊周。2015。 “基于改进的人工蜜蜂群算法的 3D 离线模型蛋白折叠优化。” *Journal of Molecular Modeling* 21 (10)。doi:[10.1007/s00894-015-2806-y](http://dx.doi.org/10.1007/s00894-015-2806-y)。
- 李, 纳鲁, 华阳, 及穆·安列。 2019。 “改进的灰粒子群优化算法和新的卢斯-雅科拉混合算法优化了多种机翼振动系统的 IMC-PID 控制器。” *Complexity* 2019。doi:[10.1155/2019/8283178](http://dx.doi.org/10.1155/2019/8283178)。
- 林, 兖红, 景旺, 夏林, 李, 袁子, 张, 黄, 绍国。2021。 “改进的人工蜜蜂群算法用于 QSAR 特征选择。” *Algorithms* 14 (4)。doi:[10.3390/a14040120](http://dx.doi.org/10.3390/a14040120)。
- 刘, 江山, 玉梅, 张, 白, 绍林。2018。 “基于全局最佳指导的人工蜜蜂群算法。” *Proceedings – 13th International Conference on Computational Intelligence and Security, CIS 2017 2018-Janua*: 211–215。doi:[10.1109/CIS.2017.00053](http://dx.doi.org/10.1109/CIS.2017.00053)。
- 刘, 义, 及唐, 盛青。2018。 “人工蜜蜂群优化算法在图像边缘检测中的应用。” *ICNC-FSKD 2017 – 13th International Conference on Natural Computation, Fuzzy Systems and Knowledge Discovery*。IEEE，923–929。doi:[10.1109/FSKD.2017.8393400](http://dx.doi.org/10.1109/FSKD.2017.8393400)。
- 马哈帕特拉, 帕米塔, 安纳普纳·库马里, 维杰·古尔帕蒂, 里图·班纳吉, 及阿希纳·纳格。2009。 “通过响应面法优化的根多极体固定酶的果味酯的酶催化合成。” *Journal of Molecular Catalysis B: Enzymatic* 60 (1–2): 57–63。doi:[10.1016/j.molcatb.2009.03.010](http://dx.doi.org/10.1016/j.molcatb.2009.03.010)。
- 米尔纳斯, 马克·M. 1993。 “‘群体、相变与集体智能。’” *ArXiv: Adaptation and Self-Organizing Systems*。
- 摩哈帕特拉, 普拉布吉特, 克达尔·纳特·达斯, 及桑坦努·罗伊。2017。 “用于大规模优化问题的修改竞争群体优化算法。” *Applied Soft Computing Journal* 59。Elsevier B.V.: 340–362。doi:[10.1016/j.asoc.2017.05.060](http://dx.doi.org/10.1016/j.asoc.2017.05.060)。
- 奥马尔, S.N., 及 J. 塞斯蒂尔纳特。2009。 “人工蜜蜂群算法用于声发射信号源的分类。” *International Journal of Aerospace Innovations* 1 (3): 129–143。doi:[10.1260/175722509789685865](http://dx.doi.org/10.1260/175722509789685865)。
- 欧坎, 康斯坤, 奥兹古尔·基西, 及巴里耶·阿卡伊。2011。 “人工蜜蜂群算法用于日射参考蒸发量建模。” *Irrigation Science* 29 (6): 431–441。doi:[10.1007/s00271-010-0254-0](http://dx.doi.org/10.1007/s00271-010-0254-0)。
- 潘, 权克, M. Fatih 泰吉特伦, P. N. 斯坎森, 及 T. J. 丘, 华。2011。 “离散人工蜜蜂群算法用于批流车间调度问题。” *Information Sciences* 181 (12)。Elsevier Inc.: 2455–2468。doi:[10.1016/j.ins.2009.12.025](http://dx.doi.org/10.1016/j.ins.2009.12.025)。
- 拉奥, R. Srinivasa, S. V. L. 那拉西姆哈, 及 M. 拉马林加拉朱。2008。 “利用人工蜜蜂群算法减少配电网损耗的优化。” *International Journal of Electrical and Computer Engineering* 2 (9): 1964–1970。doi:[10.5281/zenodo.1057591](http://dx.doi.org/10.5281/zenodo.1057591)。
- 萨特什·库马尔, K., 及 M. 海拉塔。2014。 “使用模糊人工蜜蜂群算法的规则优化创新潜力。” *Research Journal of Applied Sciences, Engineering and Technology* 7 (13): 2627–2633。doi:[10.19026/rjaset.7.578](http://dx.doi.org/10.19026/rjaset.7.578)。
- 塞拉米, 普尔马克斯, 及阿尔西·穆斯塔法。2011。 “基于人工蜜蜂群算法的 CNN 基于成像传感器边缘检测的新克隆模板设计方法。” *Sensors* 11(5): 5337–5359。doi:[10.3390/s110505337](http://dx.doi.org/10.3390/s110505337)。
- 塞曼, M. N., 及 N. 塔斯平尔。2013。 “使用人工蜜蜂群算法对 MIMO-OFDM 系统的导频优化。” *Wireless Personal Communications* 71(1): 151–163。 [doi.org/10.1007/s11277-012-0807-z](https://doi.org/10.1007/s11277-012-0807-z)。
- Shah, Habib, Rozaida Ghazali, and Nazri Mohd Nawi。2012。混合蚂蚁-蜜蜂群算法用于火山温度预测。在: Chowdhry, B.S., Shaikh, F.K., Hussain, D.M.A., Uqaili, M.A. (eds) Emerging Trends and Applications in Information Communication Technologies. IMTIC 2012. Communications in Computer and Information Science, vol 281. Springer, Berlin, Heidelberg。 [doi.org/10.1007/978-3-642-28962-0_43](https://doi.org/10.1007/978-3-642-28962-0_43)。
- Sharma, Kavita, P. C. Gupta, and Nirmala Sharma。2021。 “以裂纹启发的人工蜜蜂群算法用于数值优化。” *Evolutionary Intelligence* 14 (3)。Springer Berlin Heidelberg: 1345–1353。doi:[10.1007/s12065-020-00430-8](http://dx.doi.org/10.1007/s12065-020-00430-8)。
- Singh, Alok。2009。 “人工蜜蜂群算法用于受叶约束的最小生成树问题。” *Applied Soft Computing Journal* 9 (2): 625–631。doi:[10.1016/j.asoc.2008.09.001](http://dx.doi.org/10.1016/j.asoc.2008.09.001)。
- Sonmez, Mustafa。2011。 “人工蜜蜂群算法用于三角结构的优化。” *Applied Soft Computing Journal* 11 (2)。Elsevier B.V.: 2406–2418。doi:[10.1016/j.asoc.2010.09.003](http://dx.doi.org/10.1016/j.asoc.2010.09.003)。
- Tsai, Pei Wei, Jeng Shyang Pan, Bin Yih Liao, and Shu Chuan Chu。2009。 “增强的人工蜜蜂群优化算法。” *International Journal of Innovative Computing, Information and Control* 5 (12): 5081–5092。doi:[10.1002/elps.200900194](http://dx.doi.org/10.1002/elps.200900194)。
- Wang, Juan, Xu Honglei, Kok Lay Teo, Jie Sun, and Jianxiong Ye。2020。 “混合整数极值动态优化用于甘油代谢网络的结构识别。” *Applied Mathematical Modelling* 82。Elsevier Inc.: 503–520。doi:[10.1016/j.apm.2020.01.042](http://dx.doi.org/10.1016/j.apm.2020.01.042)。
- Wang, Yajun, Wen Chen, and Chintha Tellambura。2010。 “基于人工蜜蜂群算法的 OFDM 信号 PAPR 减小方法。” *IEEE Transactions on Wireless Communications* 9 (10): 2994–2999。doi:[10.1109/TWC.2010.081610.100047](http://dx.doi.org/10.1109/TWC.2010.081610.100047)。
- Xiang, Wan Li, and Mei Qing An。2013。 “高效且稳健的人工蜜蜂群算法用于数值优化。” *Computers and Operations Research* 40 (5)。Elsevier: 1256–1265。doi:[10.1016/j.cor.2012.12.006](http://dx.doi.org/10.1016/j.cor.2012.12.006)。
- Yeh, Wei Chang, and Tsung Jung Hsieh。2012。 “人工蜜蜂群算法-神经网络用于生化网络 S 系统模型的近似。” *Neural Computing and Applications* 21 (2): 365–375。doi:[10.1007/s00521-010-0435-z](http://dx.doi.org/10.1007/s00521-010-0435-z)。
- Zhang, Changsheng, Dantong Ouyang, and Jiaxu Ning。2010。 “人工蜜蜂群方法用于聚类。” *Expert Systems with Applications* 37 (7)。Elsevier Ltd: 4761–4767。doi:[10.1016/j.eswa.2009.11.003](http://dx.doi.org/10.1016/j.eswa.2009.11.003)。
- 张建春, 李磊, 陈志伟。2021 年。“利用人工蜂群算法解决多状态系统的强度-冗余分配问题。” 可靠性工程与系统安全 209（2020 年 9 月）。Elsevier Ltd: 107494。doi:[10.1016/j.ress.2021.107494](http://dx.doi.org/10.1016/j.ress.2021.107494)。
- 张祥荣, 王文娜, 李阳阳, 焦 L. C. Jiao。2012 年。“基于粒子群的超光谱图像分类自适应相关性判定与特征选择系统。” 电子信件 48（2012 年）：1263–1265。doi:[10.1049/el.2012.0539](http://dx.doi.org/10.1049/el.2012.0539)。
- 朱国普, 沙克昂。2010 年。“用于数值函数优化的最佳引导人工蜂群算法。” 应用数学与计算 217（7 期）。Elsevier Inc.: 3166–3173。doi:[10.1016/j.amc.2010.08.049](http://dx.doi.org/10.1016/j.amc.2010.08.049)。

# 索引

## A

- 激活函数, 84, 150–152
- 自适应矩估计, 153
- 参数调整, 208
- 曝气率, 122, 133
- 农业, 122, 125, 166
- 农业副产品, 126
- AI-Ml 方法, 77
- 碱性蛋白酶, 6, 3
- 阿法-淀粉酶, 56
- Aminex HPX-87H 列, 169
- 氨基酸, 4
- 淀粉酶, 7, 10, 21, 24, 29, 30, 31, 32, 33, 34, 35, 37, 38, 40, 58, 146, 154, 157
- 方差分析, 101, 104, 110, 172, [184](ch8.xhtml#table8_4), [187](ch8.xhtml#table8_5)
- ANN, 68
- 抗真菌剂, 166
- 抗微生物活性, 166
- 抗氧化效应, 166
- 人工蜂群优化, 196
- 人工神经网络, 105, 106, 107, 111, 112, 113, 114, 122–123, 129, 133, 137, 138

## B

- B. Licheniformis, 9
- 反向传播方法, 149, 152
- 烘焙行业, 23, 24
- 最佳解决方案, 129
- 生物催化剂, 02, 08, 19, 35, 41, [122](ch6.xhtml#p122), 186
- 生物相容性, 166
- 生物量, 08, [28](ch2.xhtml#table2_1), 57, 59, 61, 64, 84, 93, 124, 136, 185
- 漂白, 21, 29, 30, 31
- Box–Behnken, 101, 104, 129, 137

## C

- 碳水化合物酶, 10
- 催化酶, 9, 23, 34
- 细胞密度, 132–133
- 细胞工厂, 123
- Cellic 酶, 8
- 纤维素酶, 7, 8, 30, 32, 35, 59, 123
- 中心复合设计, 102, 128, 129, 131, 136, 158, 160, 165, 172, [173](ch8.xhtml#table8_3), 185, 186
- 纤维素, 100, [102](ch5.xhtml#table5_1), 110, 111, [136](ch6.xhtml#table6_2), 156, 165, 166, 167, 168, 169
- 纤维素酶生产, 165, 166, 167, 184, 185, 187, 190
- 纤维素酶, 100, 101, [102](ch5.xhtml#table5_1), 110, 111, 112
- 纤糖苷酶, 166
- 纤糖寡糖, 166
- 染色体, 130, 132–133
- 封闭系统, 65, 66
- 聚类问题, 209
- 决定系数, 113
- 胶体纤维素, 102, 111, 165, 168, 169, 170, 172, [173](ch8.xhtml#table8_3), 184, 186, [187](ch8.xhtml#table8_5), 188, 190
- 计算方法, 167
- 共同体, 8
- 受限优化, 147
- 化妆品, 20, 36, 37
- 成本函数, 85, 152, 153
- 交叉, 87, 88, 90, 107, 108, 130, 133, 137, 172, 173, 174, 178, 180, 187
- 粗酶, 168
- 培养基, 77, 85

## D

- 乳制品行业, 22
- Deb’s 规则, 205, 208
- 决策变量, 147–148
- 变性, 124
- 实验设计, 100, 109, 128, 146, 170
- 洗涤剂, 20, 21, 37, 38
- 变形真菌, 166
- 差分演化, 165, 167, 172, 178, 179, 183, 187, 190
- DNase, 56
- 下游, 124, 126
- 药物递送, 166
- 动态编程, 148

## E

- Evolutionary theory, [123](ch6.xhtml#p123), [132](ch6.xhtml#p132)
- Evop, [67](ch3.xhtml#p67), [68](ch3.xhtml#p68), [71](ch3.xhtml#p71)
- Exochitinase, [86](ch4.xhtml#p86), [111](ch5.xhtml#p111), [136](ch6.xhtml#table6_2), [156](ch7.xhtml#p156), [160](ch7.xhtml#p160), [166](ch8.xhtml#p166)
- Extracellular enzymes, [55](ch3.xhtml#p55)
- Extracellular, [124](ch6.xhtml#p124)

## F

- Factorial design, [66](ch3.xhtml#p66), [67](ch3.xhtml#p67), [81](ch4.xhtml#p81), [90](ch4.xhtml#p90)
- Features, [83](ch4.xhtml#p83), [85](ch4.xhtml#p85)
- Feed industry, [20](ch2.xhtml#p20), [24](ch2.xhtml#p24), [29](ch2.xhtml#p29)
- Feed-forward neural network, [133](ch6.xhtml#p133)
- Fermentation, [2](ch1.xhtml#p2), [6](ch1.xhtml#p6), [57](ch3.xhtml#p57), [60](ch3.xhtml#p60), [63](ch3.xhtml#p63), [66](ch3.xhtml#p66), [67](ch3.xhtml#p67), [68](ch3.xhtml#p68), [70](ch3.xhtml#p70), [89](ch4.xhtml#p89), [90](ch4.xhtml#p90), [110](ch5.xhtml#p110), [112](ch5.xhtml#p112), [113](ch5.xhtml#p113), [122–127](ch6.xhtml#p122), [129–137](ch6.xhtml#p129)
- Fitness score, [87](ch4.xhtml#p87)
- Food industry, [8](ch1.xhtml#p8), [19](ch2.xhtml#p19), [22](ch2.xhtml#p22), [24](ch2.xhtml#p24), [25](ch2.xhtml#table2_1), [26](ch2.xhtml#table2_1), [28](ch2.xhtml#table2_1), [155](ch7.xhtml#p155), [156](ch7.xhtml#p156), [166](ch8.xhtml#p166)
- Food number search, [207](ch9.xhtml#p207)
- Food source amount, [207](ch9.xhtml#p207)
- Foraging processes, [199](ch9.xhtml#p199)
- Fuzzy logic method, [90](ch4.xhtml#p90)
- Fuzzy logic, [68](ch3.xhtml#p68), [71](ch3.xhtml#p71), [73](ch3.xhtml#p73), [129](ch6.xhtml#p129)
- F-value, [111](ch5.xhtml#p111), [184](ch8.xhtml#p184), [186](ch8.xhtml#p186), [187](ch8.xhtml#table8_5)

## G

- Genes, [130](ch6.xhtml#p130), [133](ch6.xhtml#p133)
- Genetic algorithm (GA), [105](ch5.xhtml#p105), [107](ch5.xhtml#p107), [108](ch5.xhtml#p108), [114](ch5.xhtml#p114), [122–123](ch6.xhtml#p122), [127](ch6.xhtml#p127), [129–138](ch6.xhtml#p129)
- Global minima, [149](ch7.xhtml#p149), [152–152](ch7.xhtml#p152)
- Global optimization, [123](ch6.xhtml#p123), [138](ch6.xhtml#p138), [178](ch8.xhtml#p178)
- Glucoamylase, [10](ch1.xhtml#p10), [24](ch2.xhtml#p24), [59](ch3.xhtml#p59)
- Glycoside hydrolase, [100](ch5.xhtml#p100)
- Glycosidic bonds, [27](ch2.xhtml#table2_1), [166](ch8.xhtml#p166)
- Glycosidic hydrolases, [166](ch8.xhtml#p166)
- Gradient descent, [152](ch7.xhtml#p152)
- Growth medium, [124](ch6.xhtml#p124), [126](ch6.xhtml#p126)

## H

- Heaviside step function, [152](ch7.xhtml#p152)
- Hidden layer, [150–152](ch7.xhtml#p150), [154–157](ch7.xhtml#p154)
- HPLC, [169](ch8.xhtml#p169)
- Hydrolases, [24](ch2.xhtml#p24), [34](ch2.xhtml#p34), [40](ch2.xhtml#p40)

## I

- Industrial biocatalysts, [19](ch2.xhtml#p19), [20](ch2.xhtml#p20)
- Industrial enzymes, [19](ch2.xhtml#p19), [20](ch2.xhtml#p20), [22](ch2.xhtml#p22)
- Industrial processes, [54](ch3.xhtml#p54)
- Industrial production, [122](ch6.xhtml#p122), [123](ch6.xhtml#p123), [127](ch6.xhtml#p127)
- Inoculum stability, [126](ch6.xhtml#p126)
- Input layer, [150](ch7.xhtml#p150)
- Intracellular, [124](ch6.xhtml#p124)
- Invertase, [8](ch1.xhtml#p8)
- Isolation, [124](ch6.xhtml#p124)
- Isomerase, [21](ch2.xhtml#p21), [24](ch2.xhtml#p24)
- Iteration number, [207](ch9.xhtml#p207)

## L

- Lab-scale studies, [136](ch6.xhtml#p136)
- Laccases, [7](ch1.xhtml#p7), [9](ch1.xhtml#p9), [31](ch2.xhtml#p31), [32](ch2.xhtml#p32), [35](ch2.xhtml#p35), [37](ch2.xhtml#p37), [39](ch2.xhtml#p39), [157](ch7.xhtml#p157)
- Leather industry, [33](ch2.xhtml#p33), [34](ch2.xhtml#p34)
- Linear activation function, [151](ch7.xhtml#p151)
- Linear function, [152](ch7.xhtml#p152), [155](ch7.xhtml#p155)
- Linear programming, [148](ch7.xhtml#p148)
- Lipases, [7](ch1.xhtml#p7), [8](ch1.xhtml#p8), [9](ch1.xhtml#p9), [21](ch2.xhtml#p21), [23](ch2.xhtml#p23), [30–35](ch2.xhtml#p30), [37](ch2.xhtml#p37), [38](ch2.xhtml#p38), [64](ch3.xhtml#p64), [86](ch4.xhtml#p86), [123](ch6.xhtml#p123), [146](ch7.xhtml#p146)
- Lipolytic enzyme, [24](ch2.xhtml#p24)
- Lysozyme, [8](ch1.xhtml#p8)

## M

- Machine learning model, [82–83](ch4.xhtml#p82), [91–93](ch4.xhtml#p91)
- Machine learning, [104](ch5.xhtml#p104), [105](ch5.xhtml#p105), [113](ch5.xhtml#p113)
- Mannanases, [7](ch1.xhtml#p7), [32](ch2.xhtml#p32), [38](ch2.xhtml#p38)
- Mathematical modelling, [122](ch6.xhtml#p122)
- Mathematical optimization, [122](ch6.xhtml#p122)
- Maximum cycle number, [201](ch9.xhtml#p201)
- Mechanistic model, [91](ch4.xhtml#p91)
- Media composition, [78–81](ch4.xhtml#p78), [89](ch4.xhtml#p89), [93](ch4.xhtml#p93)
- Media formulation, [124](ch6.xhtml#p124)
- Medical patterns, [209](ch9.xhtml#p209)
- Medium optimization, [80](ch4.xhtml#p80), [110](ch5.xhtml#p110), [121](ch6.xhtml#p121), [127](ch6.xhtml#p127), [128](ch6.xhtml#p128), [129](ch6.xhtml#p129), [136](ch6.xhtml#p136), [137](ch6.xhtml#p137)
- Metabolic branch point, [59](ch3.xhtml#p59), [60](ch3.xhtml#p60)
- Microbial enzymes, [21](ch2.xhtml#p21), [22](ch2.xhtml#p22), [23](ch2.xhtml#p23), [24](ch2.xhtml#p24)
- Microbial sources, [123](ch6.xhtml#p123)
- Midstream, [124](ch6.xhtml#p124)
- Multilayer feedforward network, [106](ch5.xhtml#p106), [112](ch5.xhtml#p112)
- Multilayer perceptron, [210](ch9.xhtml#p210)
- Multi-objective genetic algorithm (moga), [132](ch6.xhtml#p132)
- Multiobjective optimization, [211](ch9.xhtml#p211)
- Multivariate regression model, [159](ch7.xhtml#p159)
- Mutation, [87](ch4.xhtml#p87), [88](ch4.xhtml#p88), [107](ch5.xhtml#p107), [108](ch5.xhtml#p108), [129](ch6.xhtml#p129), [130](ch6.xhtml#p130), [133](ch6.xhtml#p133), [136](ch6.xhtml#p136), [137](ch6.xhtml#p137), [173](ch8.xhtml#p173), [174](ch8.xhtml#p174), [175](ch8.xhtml#p175), [176](ch8.xhtml#p176), [177](ch8.xhtml#p177)

## N

- N-acetyl-glucosamine, [166](ch8.xhtml#p166), [169](ch8.xhtml#p169)
- Natural selection, [107](ch5.xhtml#p107), [132](ch6.xhtml#p132)
- Nectar, [198](ch9.xhtml#p198), [199](ch9.xhtml#p199), [200](ch9.xhtml#p200)
- Nestmates, [203](ch9.xhtml#p203)
- Network for adversary generation (NAG), [153](ch7.xhtml#p153)
- Non-linear programming, [149](ch7.xhtml#p149)
- Nontoxicity, [166](ch8.xhtml#p166)
- Novo enzyme, [1](ch1.xhtml#p1), [8](ch1.xhtml#p8)
- Numerical optimization, [205](ch9.xhtml#p205), [209](ch9.xhtml#p209)

## O

- Objective function, [148](ch7.xhtml#p148), [152–153](ch7.xhtml#p152)
- OFAT, [101](ch5.xhtml#p101), [110](ch5.xhtml#p110), [112](ch5.xhtml#p112), [122](ch6.xhtml#p122), [127](ch6.xhtml#p127), [128](ch6.xhtml#p128), [167](ch8.xhtml#p167), [186](ch8.xhtml#p186)
- Offspring, [123](ch6.xhtml#p123), [129–132](ch6.xhtml#p129)
- Oligomers, [166](ch8.xhtml#p166)
- Open ended system, [65](ch3.xhtml#p65)
- Optimization function, [148–149](ch7.xhtml#p148), [152–153](ch7.xhtml#p152)
- Optimization techniques, [122](ch6.xhtml#p122), [123](ch6.xhtml#p123), [127–130](ch6.xhtml#p127), [136](ch6.xhtml#p136), [196](ch9.xhtml#p196), [197](ch9.xhtml#p197)
- Optimization, [100](ch5.xhtml#p100), [101](ch5.xhtml#p101), [102](ch5.xhtml#table5_1), [105](ch5.xhtml#p105), [107](ch5.xhtml#p107), [108](ch5.xhtml#p108), [109](ch5.xhtml#p109), [110](ch5.xhtml#p110), [111](ch5.xhtml#p111), [112](ch5.xhtml#p112), [113](ch5.xhtml#p113), [114](ch5.xhtml#p114)
- Optimizer, [152](ch7.xhtml#p152), [154](ch7.xhtml#fig7_3)
- Oxidoreductase, [24](ch2.xhtml#p24), [34](ch2.xhtml#p34)

## P

- Papain, [9](ch1.xhtml#p9)
- Parameters, [122–129](ch6.xhtml#p122), [131–134](ch6.xhtml#p131), [137](ch6.xhtml#p137)
- 父母, [123](ch6.xhtml#p123), [129–130](ch6.xhtml#p129)
- 部分阶乘设计, [158](ch7.xhtml#p158)
- 粒子群优化, [105](ch5.xhtml#p105), [109](ch5.xhtml#p109)
- pectinase, [7](ch1.xhtml#p7)
- pepsin, [23](ch2.xhtml#p23), [33](ch2.xhtml#p33)
- 肽键, [3](ch1.xhtml#p3)
- 单胞菌, [149](ch7.xhtml#p149), [152](ch7.xhtml#p152)
- 过氧化酶, [9](ch1.xhtml#p9), [36](ch2.xhtml#p36)
- 扰动过程, [208](ch9.xhtml#p208)
- 害虫防治, [166](ch8.xhtml#p166)
- 医药和分析工业, [29](ch2.xhtml#p29)
- 试验向量, [177](ch8.xhtml#p177), [178](ch8.xhtml#p178)
- Plackett–Burman 设计, [5](ch1.xhtml#p5), [99](ch5.xhtml#p99), [101](ch5.xhtml#p101), [102](ch5.xhtml#table5_1), [103](ch5.xhtml#p103), [104](ch5.xhtml#p104), [110](ch5.xhtml#p110), [111](ch5.xhtml#p111), [129](ch6.xhtml#p129), [137](ch6.xhtml#p137), [165](ch8.xhtml#p165), [167](ch8.xhtml#p167), [169](ch8.xhtml#p169), [183](ch8.xhtml#p183), [184](ch8.xhtml#table8_4), [190](ch8.xhtml#p190)
- 聚合物, [166](ch8.xhtml#p166)
- 人口, [122–123](ch6.xhtml#p122), [129–132](ch6.xhtml#p129), [137](ch6.xhtml#p137)
- 基于人口的方法, [210](ch9.xhtml#p210)
- 概率算法, [211](ch9.xhtml#p211)
- 过程优化, [75](ch4.xhtml#p75), [77](ch4.xhtml#p77), [79](ch4.xhtml#p79), [80](ch4.xhtml#p80), [82](ch4.xhtml#p82), [84](ch4.xhtml#p84), [85](ch4.xhtml#p85), [165](ch8.xhtml#p165)
- 生产介质, [62](ch3.xhtml#p62), [166](ch8.xhtml#p166), [167](ch8.xhtml#p167), [186](ch8.xhtml#p186), [190](ch8.xhtml#p190)
- 生产流程, [54](ch3.xhtml#p54)
- 产量, [126](ch6.xhtml#p126), [134](ch6.xhtml#p134)
- 保护酶, [5](ch1.xhtml#p5), [7](ch1.xhtml#p7), [21](ch2.xhtml#p21), [23–41](ch2.xhtml#p23), [55](ch3.xhtml#p55), [58](ch3.xhtml#p58), [59](ch3.xhtml#p59), [123](ch6.xhtml#p123), [146](ch7.xhtml#p146), [157](ch7.xhtml#p157), [166](ch8.xhtml#p166)
- p-value, [184](ch8.xhtml#p184), [186](ch8.xhtml#p186), [187](ch8.xhtml#table8_5)

## R

- 选择性选择, [208](ch9.xhtml#p208)
- 重组, [130](ch6.xhtml#p130)
- 回归方程, [172](ch8.xhtml#p172), [187](ch8.xhtml#p187)
- 回归模型, [89](ch4.xhtml#p89), [149](ch7.xhtml#p149), [159](ch7.xhtml#p159), [168](ch8.xhtml#p168)
- 强化学习, [83–84](ch4.xhtml#p83)
- Rennin, [23](ch2.xhtml#p23), [33](ch2.xhtml#p33)
- 反应面
- 反应面方法 (rsm), [67](ch3.xhtml#p67), [68](ch3.xhtml#p68), [82](ch4.xhtml#p82), [86](ch4.xhtml#p86), [101](ch5.xhtml#p101), [103](ch5.xhtml#p103), [122](ch6.xhtml#p122), [129](ch6.xhtml#p129), [133](ch6.xhtml#p133), [137](ch6.xhtml#p137)

## S

- 饱和葡萄糖琼脂, [168](ch8.xhtml#p168)
- 规模放大, [127](ch6.xhtml#p127)
- 摇瓶实验, [136](ch6.xhtml#p136)
- 摇瓶, [81](ch4.xhtml#p81), [89](ch4.xhtml#p89), [92–93](ch4.xhtml#p92)
- 虾壳, [168](ch8.xhtml#p168)
- 正态函数, [152](ch7.xhtml#p152), [155](ch7.xhtml#p155)
- 简单遗传算法 (SGA), [132](ch6.xhtml#p132)
- 社会行为, [203](ch9.xhtml#p203)
- 固态发酵, [4](ch1.xhtml#p4), [57](ch3.xhtml#p57), [58](ch3.xhtml#p58), [59](ch3.xhtml#p59), [62](ch3.xhtml#p62), [68](ch3.xhtml#p68), [78](ch4.xhtml#p78), [122](ch6.xhtml#p122), [124–126](ch6.xhtml#p124), [158](ch7.xhtml#p158)
- 统计方法, [5](ch1.xhtml#p5), [62](ch3.xhtml#p62), [81](ch4.xhtml#p81), [82](ch4.xhtml#p82), [127](ch6.xhtml#p127), [129](ch6.xhtml#p129), [146](ch7.xhtml#p146), [159](ch7.xhtml#p159), [167](ch8.xhtml#p167)
- 统计技术, [129](ch6.xhtml#p129)
- 最陡上升, [82](ch4.xhtml#p82), [157](ch7.xhtml#p157)
- 步骤, [204](ch9.xhtml#p204)
- 灭菌, [124](ch6.xhtml#p124)
- 随机梯度下降, [153](ch7.xhtml#p153)
- 随机搜索算法, [129](ch6.xhtml#p129), [132](ch6.xhtml#p132)
- 股票预测, [210](ch9.xhtml#p210)
- 计量学, [124](ch6.xhtml#p124)
- 强人工智能, [76](ch4.xhtml#p76)
- 亚埋酶发酵, [5](ch1.xhtml#p5), [57](ch3.xhtml#p57), [62](ch3.xhtml#p62), [64](ch3.xhtml#p64), [78](ch4.xhtml#p78), [122](ch6.xhtml#p122), [125–126](ch6.xhtml#p125)
- 底物的水活性, [126](ch6.xhtml#p126)
- 超氧化物歧化酶, [9](ch1.xhtml#p9)
- 监督学习, [83–84](ch4.xhtml#p83)
- 表面发酵, [78](ch4.xhtml#p78)
- 适者生存, [129](ch6.xhtml#p129)
- 群体方法, [198](ch9.xhtml#p198)

## T

- Taguchi 设计, [129](ch6.xhtml#p129)
- Taguchi 正交表, [110](ch5.xhtml#p110)
- 纺织工业, [34](ch2.xhtml#p34)
- 概率论, [129](ch6.xhtml#p129)
- Thermomyces lanuginosus, [32](ch2.xhtml#table2_4), [134](ch6.xhtml#table6_2), [156](ch7.xhtml#p156), [166](ch8.xhtml#p166), [167](ch8.xhtml#p167), [168](ch8.xhtml#p168), [184](ch8.xhtml#p184), [187](ch8.xhtml#table8_5)
- 热带性, [7](ch1.xhtml#p7), [166](ch8.xhtml#p166)
- 热带性淀粉酶, [7](ch1.xhtml#p7)
- 耐热性, [37](ch2.xhtml#p37), [166](ch8.xhtml#p166)
- 赛跑选择, [208](ch9.xhtml#p208)
- 明胶, [33](ch2.xhtml#p33)
- Tween 80, [5](ch1.xhtml#p5), [111](ch5.xhtml#p111), [173](ch8.xhtml#p173), [184](ch8.xhtml#p184), [186](ch8.xhtml#p186), [187](ch8.xhtml#table8_5), [188](ch8.xhtml#p188)
- 两水平阶乘, [157](ch7.xhtml#p157)
- 多酚酶, [29](ch2.xhtml#p29), [36](ch2.xhtml#p36)

## U

- 受约束优化, [147](ch7.xhtml#p147)
- 无监督学习, [83–84](ch4.xhtml#p83)
- 上游, [124](ch6.xhtml#p124)

## V

- 验证, [153](ch7.xhtml#p153), [154](ch7.xhtml#p154), [165](ch8.xhtml#p165), [183](ch8.xhtml#p183), [187](ch8.xhtml#p187), [188](ch8.xhtml#p188), [190](ch8.xhtml#p190)
- 向量适应性遗传算法, [132](ch6.xhtml#p132)

## W

- 摇摆舞, [199](ch9.xhtml#p199), [203](ch9.xhtml#p203)
- 浪费管理, [40](ch2.xhtml#p40), [146](ch7.xhtml#p146), [166](ch8.xhtml#p166)
- 浪费处理, [34](ch2.xhtml#p34), [39](ch2.xhtml#p39), [40](ch2.xhtml#p40)
- 弱人工智能, [76](ch4.xhtml#p76)

## X

- 谷蛋白酶, [7](ch1.xhtml#p7), [29](ch2.xhtml#p29), [30](ch2.xhtml#p30), [32](ch2.xhtml#p32), [35](ch2.xhtml#p35), [123](ch6.xhtml#p123), [126](ch6.xhtml#p126), [166](ch8.xhtml#p166)

## Y

- 酵母提取物, [63](ch3.xhtml#table3_2), [102](ch5.xhtml#table5_1), [110](ch5.xhtml#p110), [111](ch5.xhtml#p111), [168](ch8.xhtml#p168), [169](ch8.xhtml#table8_1), [170](ch8.xhtml#table8_2), [172](ch8.xhtml#p172), [173](ch8.xhtml#table8_3), [196](ch9.xhtml#p196), [196](ch9.xhtml#p196), [184](ch8.xhtml#p184), [186](ch8.xhtml#p186), [187](ch8.xhtml#table8_5), [188](ch8.xhtml#p188)
    - 𝑆-type 子种群, [206](ch9.xhtml#p206)
    - 𝑆-type, [203](ch9.xhtml#p203)
