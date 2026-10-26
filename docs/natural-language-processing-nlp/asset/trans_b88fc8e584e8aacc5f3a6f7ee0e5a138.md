

## 附录B

## 数值优化

无约束数值优化涉及求解如下形式的问题：

$$\min_{x \in \mathbb{R}^D} f(x),$$ [B.1]

其中 $x \in \mathbb{R}^D$ 是由 $D$ 个实数组成的向量。

微分是数值优化的基础。假设在某个 $x^*$ 处，$f$ 的每个偏导数都等于0：形式化地，$\left.\frac{\partial f}{\partial x_i}\right|_{x^*} = 0$。则称 $x^*$ 为 $f$ 的**临界点**。如果 $f$ 是**凸**函数（定义见§2.4），则当且仅当 $x^*$ 是 $f$ 的临界点时，$f(x^*)$ 的值等于 $f$ 的全局最小值。

例如，考虑图B.1a所示的凸函数 $f(x) = (x-2)^2+3$。其导数为 $\frac{\partial f}{\partial x} = 2x-4$。令导数等于零并求解 $x$，可得唯一最小值点 $x^* = 2$。现在考虑多元凸函数 $f(x) = \frac{1}{2}\|x - [2,1]^\top\|^2$，其中 $\|x\|^2$ 是欧几里得范数的平方。偏导数

![](img/ba66a8f6f22adeb28512d560b999a231_502_0.png)

![](img/ba66a8f6f22adeb28512d560b999a231_502_1.png)

(a) 函数 $f(x) = (x - 2)^2 + 3$

(b) 函数 $f(x) = |x| - 2\cos(x)$

图B.1：两个具有唯一全局最小值的函数

Abadi, M., A. Agarwal, P. Barham, E. Brevdo, Z. Chen, C. Citro, G. S. Corrado, A. Davis, J. Dean, M. Devin, S. Ghemawat, I. J. Goodfellow, A. Harp, G. Irving, M. Isard, Y. Jia, R. Józefowicz, L. Kaiser, M. Kudlur, J. Levenberg, D. Mané, R. Monga, S. Moore, D. G. Murray, C. Olah, M. Schuster, J. Shlens, B. Steiner, I. Sutskever, K. Talwar, P. A. Tucker, V. Vanhoucke, V. Vasudevan, F. B. Viégas, O. Vinyals, P. Warden, M. Wattenberg, M. Wicke, Y. Yu, and X. Zheng (2016). TensorFlow：异构分布式系统上的大规模机器学习。CoRR abs/1603.04467.

Abend, O. and A. Rappoport (2017). 语义表示的最新水平。参见 acl (2017)。

Abney, S., R. E. Schapire, and Y. Singer (1999). 将提升方法应用于标注和PP附着。参见 emn (1999)，第132–134页。

Abney, S. P. (1987). 英语名词短语的句子层面表现。博士论文，麻省理工学院。

Abney, S. P. and M. Johnson (1991). 解析策略的内存需求与局部歧义。*《心理语言学研究杂志》* 20(3), 233–250.

Adafre, S. F. and M. De Rijke (2006). 在维基百科中跨语言查找相似句子。载于《关于新文本维基、博客和其他动态文本源的研讨会论文集》。

Ahn, D. (2006). 事件抽取的阶段。载于《时间与事件标注和推理研讨会论文集》，第1–8页。计算语言学协会。

Aho, A. V., M. S. Lam, R. Sethi, and J. D. Ullman (2006). *《编译器：原理、技术与工具》*（第2版）。艾迪生-韦斯利出版公司。

Aikhenvald, A. Y. (2004). *《示证性》*。牛津大学出版社。

Carletta, J. (1996). 评估分类任务的一致性：kappa统计量。*《计算语言学》* 22(2), 249–254.

Carletta, J. (2007). 释放杀手级语料库：创建多维度AMI会议语料库的经验。*《语言资源与评测》* 41(2), 181–190.

Carlson, L. and D. Marcu (2001). 话语标注参考手册。技术报告 ISI-TR-545，信息科学研究所。

Carlson, L., M. E. Okurowski, and D. Marcu (2002). RST篇章树库。宾夕法尼亚大学语言数据联盟。

Carpenter, B. (1997). *《类型逻辑语义学》*。马萨诸塞州剑桥：麻省理工学院出版社。

Carreras, X., M. Collins, and T. Koo (2008). 基于标注、动态规划和感知机的高效、特征丰富的解析。载于*《自然语言学习会议（CoNLL）论文集》*，第9–16页。

Carreras, X. and L. Márquez (2005). CoNLL-2005共享任务简介：语义角色标注。载于*《第九届计算自然语言学习会议论文集》*，第152–164页。计算语言学协会。

Carroll, L. (1865). *《爱丽丝梦游仙境》*。伦敦：麦克米伦出版社。

Carroll, L. (1917). *《镜中世界：爱丽丝镜中奇遇记》*。芝加哥：兰德-麦克纳利出版社。

Chambers, N. and D. Jurafsky (2008). 联合整合隐式约束改进时间排序。参见 emn (2008)，第698–706页。

Chang, K.-W., A. Krishnamurthy, A. Agarwal, H. Daumé III, and J. Langford (2015). 学习比你的老师更好地搜索。参见 icm (2015)。

Chang, M.-W., L. Ratinov, and D. Roth (2007). 用约束驱动学习指导半监督。参见 acl (2007)，第280–287页。

Chang, M.-W., L.-A. Ratinov, N. Rizzolo, and D. Roth (2008). 带约束的学习与推理。载于*《美国人工智能协会全国会议（AAAI）论文集》*，第1513–1518页。

Chapman, W. W., W. Bridewell, P. Hanbury, G. F. Cooper, and B. G. Buchanan (2001). 一种识别出院摘要中否定发现和疾病的简单算法。*《生物医学信息学杂志》* 34(5), 301–310.

Charniak, E. (1997). 自然语言解析的统计技术。*《AI杂志》* 18(4), 33–43.

Collobert, R., K. Kavukcuoglu, and C. Farabet (2011). Torch7：类似Matlab的机器学习环境。技术报告 EPFL-CONF-192376，EPFL。

Collobert, R. and J. Weston (2008). 自然语言处理的统一架构：基于多任务学习的深度神经网络。参见 icm (2008)，第160–167页。

Collobert, R., J. Weston, L. Bottou, M. Karlen, K. Kavukcuoglu, and P. Kuksa (2011). 自然语言处理（几乎）从零开始。*《机器学习研究杂志》* 12, 2493–2537.

Colton, S., J. Goodwin, and T. Veale (2012). 全脸诗歌生成。载于《国际计算创意会议论文集》，第95–102页。

Conneau, A., D. Kiela, H. Schwenk, L. Barrault, and A. Bordes (2017). 从自然语言推理数据监督学习通用句子表示。参见 emn (2017)，第681–691页。

Cormen, T. H., C. E. Leiserson, R. L. Rivest, and C. Stein (2009). *《算法导论》*（第3版）。麻省理工学院出版社。

Cotterell, R., H. Schütze, and J. Eisner (2016). 词嵌入的形态平滑与外推。参见 acl (2016)，第1651–1660页。

Coviello, L., Y. Sohn, A. D. Kramer, C. Marlow, M. Franceschetti, N. A. Christakis, and J. H. Fowler (2014). 在大规模社交网络中检测情绪传染。*《PLoS ONE》* 9(3), e90315.

Covington, M. A. (2001). 依存句法分析的基础算法。载于《第39届ACM东南会议论文集》，第95–102页。

Crammer, K., O. Dekel, J. Keshet, S. Shalev-Shwartz, and Y. Singer (2006年12月). 在线被动-主动算法。*《机器学习研究杂志》* 7, 551–585.

Crammer, K. and Y. Singer (2001). Pranking与排序。载于《神经信息处理系统会议（NIPS）》，第641–647页。

Crammer, K. and Y. Singer (2003). 针对多类问题的超保守在线算法。*《机器学习研究杂志》* 3, 951–991.

Creutz, M. and K. Lagus (2007). 用于语素切分和形态学习的无监督模型。*《ACM语音与语言处理汇刊（TSLP）》* 4(1), 3.

Cross, J. and L. Huang (2016). 基于跨度、使用结构标签系统和可证明最优动态预言机的成分句法分析。参见 emn (2016)，第1–11页。

