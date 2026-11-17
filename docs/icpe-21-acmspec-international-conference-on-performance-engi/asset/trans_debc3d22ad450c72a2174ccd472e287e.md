

### 表 4：估算误差比较。

| 处理器 | 最大误差 | 平均误差 | 标准差 |
|---|---|---|---|
| ARM946 测试 [15] | 29.75% | 9.05% | 8.90% |
| 8051 测试 | 0.61% | 0.42% | 0.12% |
| ATmega328/P 测试 | 6.03% | 2.24% | 1.48% |
| LEON3 测试 | 0.29% | 0.07% | 0.06% |
| ARM946 验证 [15] | N.A. | N.A. | N.A. |
| 8051 验证 | 2.58% | 1.19% | 0.69% |
| ATmega328/P 验证 | 65.39% | 12.58% | 17.79% |
| LEON3 验证 | 73.74% | 52.02% | 21.36% |

足以预测 CISC 微控制器的时序行为。同时，将此方法用于更复杂的处理器会引入可通过更先进的 ML 技术降低的估算误差。未来工作将研究 (1) 通过引入能够不仅表征输入数据类型，还能表征输入特定值的指标和特征来增加特征总数的可能性 (2) 模型预测参数优化（即，树集群和回归树的最小叶子大小和学习者数量，SVM 的核函数等）；(3) 过拟合问题（例如，LEON3 场景）及使用交叉验证来解决这些问题，(4) 分析多种不同于本工作所考虑的回归模型的可能性，同时也考虑将神经网络作为一种具体且有用的 ML 算法替代方案，(5) 使用所提方法表征给定处理器上 SW 监控系统的影响 [31]，(6) 将此方法应用于其他领域（即，网络物理系统、SW Computer 性能等）的可能性 [32]。

## 致谢

本工作部分得到 ECSEL RIA 2017-783162 FitOptivis 和 ECSEL-JU 2018-826610 COMP4DRONES 项目的支持。

## 参考文献

- [1] Yuriy Zcachia Lun, Alessandro D’Innocenzo, Francesco Smarra, Ivano Malavolta, and Maria Domenica Di Benedetto. 网络物理系统安全现状：一种自动控制视角。系统与软件期刊, 149:174 – 216, 2019.
- [2] P. Derler, E. A. Lee, and A. Sangiovanni-Vincentelli. 网络物理系统建模。IEEE 学报, 100(1):13–28, 2012.
- [3] Francesco Smarra, Giovanni Domenico Di Giralomo, Vittorio De Juliis, Achin Jain, Rahul Mangharam, and Alessandro D’Innocenzo. 基于回归树和随机森林的 MPC 数据驱动切换建模。非线性分析：混合系统, 36:100882, 2020.
- [4] A. Loja, L. Rubo, J. M. Ruano, T. Di Mascio, L. Pomante, E. Ferrari, I. G. Vega, F. K. Gürkaynak, M. L. Esnaola, V. Orani, and J. Abella. ECSEL 分形项目：基于唯一的开放-安全-可靠-低功耗硬件平台的认知分形和安全边缘。在第 23 届欧微数字系统设计会议 (DSD) 上, 页 393–400, 2020.
- [5] C. Brandolese, W. Fornaciari, F. Salice, and D. Sciuto. C 程序源级执行时间估算。在第九届硬件/软件协同设计国际研讨会 (CODES ’01) 论文集中, 页 98–103, 纽约, NY, 美国, 2001. ACM.
- [6] Peter Altenbernd, Jan Gustafsson, Björn Lisper, and Friedhelm Stappert. 通过自动生成的时序模型进行早期执行时间估算。实时系统, 52(6):731–760, 2016 年 11 月.
- [7] Philipp Axer, Rolf Ernst, Heiko Falk, Alain Girault, Daniel Grund, Nan Guan, Bengt Jonsson, Peter Marwedel, Jan Reineke, Cristina Rochange, Maurice Sebastian, Reinhard Von Hanxleden, Reinhard Wilhelm, and Wang Yi. 构建可预测时序的嵌入式系统。ACM 嵌入式计算系统期刊, 13(4), 2014 年 3 月.
- [8] D. J. Lilja. 计算机性能测量：从业者指南。剑桥大学出版社, 美国, 2000.
- [9] V. Muttillo, G. Valente, L. Pomante, F. Stoico, F. D’Antonio, and F. Salice. Ce4cs: 一种用于 HW/SW 技术的现成统一语句级性能指标。在 2018 年 ACM/SPEC 国际会议附录中, 纽约, NY, 美国, 2018. ACM.
- [10] G. Valente, T. Di Mascio, G. D’Andrea, and L. Pomante. 实时系统中动态部分重构的盈利性。IEEE 嵌入式系统通信, 页 1–1, 2020.
- [11] David J. Lilja. 计算机性能测量：从业者指南。SIAM 评论, 43:383–384, 2001 年 1 月.
- [12] S. Malik, M. Martonosi, and Y. S. Li. 嵌入式软件静态时序分析。第 34 届设计自动化会议论文集, 页 147–152, 1997.
- [13] Jwahar R. Banni, Wido Kruijtzer, Luciano Lavagno, Edwin Harcourt, and Mihai T. Lazarescu. 系统级设计工具中的软件性能估算策略。在第八届硬件/软件协同设计国际研讨会 (CODES 2000, CODES ’00) 论文集中, 页 82–86, 纽约, NY, 美国, 2000. 计算机协会.
- [14] Nikolica Frid, Danko Ivosevic, and Vlado Sruk. 基本运算：一种用于源级时序估算的新概念。自动学, 60(1):91–104, 2019.
- [15] Marico Oyama, Flavio Wagner, Marius Bonacini, Wander Cesarí, and Ahmed Jerraya. MPSoC 设计中的软件性能估算。在亚洲和南太平洋设计自动化会议上, 卷 0, 页 38–43, 2007 年 1 月.
- [16] B. Ozisikyilmaz, G. Memik, and A. Choudhary. 用于预测计算机系统设计方案性能的机器学习模型。在第 37 届并行处理国际会议上, 页 495–502, 2008.
- [17] Ling Huang, Jinzh Jia, Bin Yu, Byung-Gon Chun, Petros Maniatis, and Mayur Naik. 使用稀疏多项式回归预测计算机程序执行时间。在第 23 届神经信息处理系统国际会议 - 第 1 卷论文集中, 页 883–891. Curran Associates Inc., 2010.
- [18] Monika and O. P. Sangwan. 使用机器学习技术预测软件工作量估算。在第 7 届云计算、数据科学工程国际会议 - Confluence 上, 页 92–98, 2017.
- [19] Frama-C 软件分析器, 2020 (访问日期: 15.03.2020). https://frama-c.com/.
- [20] CC4CS/ML 开源 Git 仓库, 2020 (访问日期: 15.03.2020). https://github.com/vnzstc/cc4cs.
- [21] I. Lettere, G. Della Penna, and P. Caiariello. HTTP 僵尸网络流量检测的特征选择策略。在 2019 年 IEEE 欧洲安全与隐私研讨会 (EuroS PW) 上, 页 202–210, 2019.
- [22] L. Breiman, J. H. Friedman, R. A. Olshen, and C. J. Stone. 分类与回归树。Wadsworth and Brooks, Monterey, CA, 1984.
- [23] Trevor Hastie, Robert Tibshirani, and Jerome Friedman. 统计学习方法。斯普링거统计学系列. Springer New York Inc., New York, NY, USA, 2001.
- [24] 回归学习者 App, 2020 (访问日期: 15.03.2020). https://it.mathworks.com/help/stats/regression-learner-app.html.
- [25] P. Giammatteo, F. V. Firdigigli, L. Pomante, T. Di Mascio, and F. Caruso. 边缘计算的年龄性别分类器。在第 8 届地中海嵌入式计算会议 (MECO) 上, 页 1–4, 2019.
- [26] Trevor Hastie, Robert Tibshirani, and Jerome Friedman. 统计学习方法。斯普링거统计学系列. Springer New York Inc., New York, NY, USA, 2001.
- [27] Dalton 项目: 8051 微控制器, 加州大学, 2020 (访问日期: 15.03.2020). http://www.ann.ece.utk.edu/8051/.
- [28] Martin Becker, Ravindra Metta, Rentala Venkatesh, and Samarjit Chakraborty. 面向分析友好型处理器的最坏情况执行时间可扩展且精确的估算与调试。软件技术转移国际期刊, 2018 年 2 月.
- [29] Vittorio Muttillo, Paolo Giammatteo, Vincenzo Stoico, and Luigi Pomante. 嵌入式处理器能量表征的早期语句级指标。微处理器与微系统, 77:103200, 2020.
- [30] Donatella Sciuto, Fabio Salice, Luigi Pomante, and William Fornaciari. 异构多处理器嵌入式系统设计空间探索的指标。在第十届硬件/软件协同设计国际研讨会 (CODES ’02) 论文集中, 页 56–60, 纽约, NY, 美国, 2002. ACM.
- [31] G. Valente, T. Di Mascio, L. Pomante, and V. Stoico. 可监控嵌入式系统 HW/SW 协同设计的 ESL 方法：“面向可监控性设计”项目 - 进行中的工作。在 2020 年硬件/软件协同设计与系统综合国际会议 (CODES+ISSS) 上, 页 40–42, 2020.
- [32] S. J. Pan and Q. Yang. 迁移学习综述。IEEE 知识与数据工程事务, 22(10):1345–1359, 2010.

