

识别异常序列？与您在(a)中提出的无监督解决方案相比，监督方法的优缺点是什么？

7.15. 强化学习（RL）和多臂老虎机（MAB）都广为人知，用于建模智能体与外部环境之间的交互，以实现最大奖励。有趣的是，MAB常被称为单状态RL问题。你能解释为什么，并比较这两个问题的区别吗？

## 7.10 参考文献注释

Fisher score的详细介绍可参见Duda, Stork, 和 Hart [DHS01]。Gu, Li, 和 Han 提出了用于联合特征选择的广义Fisher score [GLH12]。已开发许多特征选择的替代优度量度，例如He, Cai, 和 Niyogi 的Laplacian score [HCN05]，以及Nie et al. 的trace ratio [NXJ+08]。Kohavi 和 Sommerfield [KS95] 引入了特征选择的包装器方法。Tibshirani [Tib96] 开发了用于回归任务特征选择的LASSO。Ravikumar, Wainwright, 和 Lafferty [RWL10] 将L1正则化应用于逻辑回归分类器的特征选择。LASSO存在许多扩展和推广，例如Meier, Van, 和 Sara 的group LASSO [MVDGB08]，Tibshirani et al. 的fused LASSO [TSR+05]，以及Friedman, Hastie, 和 Tibshirani 的graphical LASSO [FHT08]。有关特征选择的全面综述，参见Chandrashekar 和 Sahin [CS14]，以及Li et al. [LCW+17]。

有关贝叶斯信念网络的介绍，参见Darwiche [Dar10] 和 Heckerman [Hec96]。有关概率网络的详尽介绍，参见Pearl [Pea88] 和 Koller 和 Friedman [KF09]。Cooper 和 Herskovits [CH92]；Buntine [Bun94]；以及Heckerman, Geiger, 和 Chickering [HGC95] 提出了从训练数据和给定可观测变量学习信念网络结构的解决方案。Russell 和 Norvig [RN95] 以及 Jensen [Jen96] 中可以找到信念网络推理算法。Russell, Binder, Koller, 和 Kanazawa [RBKK95] 给出了用于训练贝叶斯信念网络的梯度下降法（如第7.2.2节所述）。图7.4中的示例改编自Russell et al. [RBKK95]。

学习带有隐藏变量的信念网络的替代策略包括应用Dempster, Laird, 和 Rubin的 [DLR77] EM（期望最大化）算法（Lauritzen [Lau95]）以及基于最小描述长度原理的方法（Lam [Lam98]）。Cooper [Coo90] 表明，无约束信念网络中推理的一般问题是NP-hard的。信念网络的局限性，例如其巨大的计算复杂性（Laskey 和 Mahoney [LM97]），促使了对层次化和可组合贝叶斯模型的探索（Pfeffer, Koller, Milch, 和 Takusagawa [PKMT99] 以及 Xiang, Olesen, 和 Jensen [XOJ00]）。这些遵循面向对象的知识表示方法。Fishelson 和 Geiger [FG02] 提出了一种用于遗传连锁分析的贝叶斯网络。

支持向量机（SVM）起源于Vapnik 和 Chervonenkis 关于统计学习理论的早期工作 [VC71]。关于SVM的第一篇论文由Boser, Guyon, 和 Vapnik [BGV92] 提出。更详细的内容可见Vapnik 的书籍 [Vap95,Vap98]。良好的入门资料包括Burges 的SVM教程 [Bur98]，以及Haykin [Hay08]、Kecman [Kec01] 和 Cristianini 与 Shawe-Taylor [CST00] 的教科书覆盖。有关求解优化问题的方法，参见Fletcher [Fle87] 和 Nocedal 与 Wright [NW99]。这些参考文献提供了文本中提到的“花哨的数学技巧”的更多细节，例如将问题转换为拉格朗日公式，随后使用Karush-Kuhn-Tucker (KKT) 条件求解。Shalev-Shwartz, Singer, Srebro, 和 Cotter 开发了一种名为Pegasos 的基于次梯度的求解器，以扩展SVM 的计算规模 [SSSC11]。存在许多SVM 变体，例如Bradley 和 Mangasarian 的L1 SVM [BM98b]、Cai, Nie, Huang, 和 Ding 的L2,1 SVM [CNHD11] 以及Nie, Wang, 和 Huang 的Lp SVM [NWH17]。有关核方法的全面介绍，参见Hofmann, Schölkopf, 和 Smola [HSS08]。

有关SVM 在回归中的应用，参见Schölkopf, Bartlett, Smola, 和 Williamson [SBSW98] 以及Drucker et al. [DBK+97]。大数据SVM 方法包括Platt 的序列最小优化算法 [Pla98]、Osuna, Freund, 和 Girosi 的分解方法 [OFG97] 以及由Yu, Yang, 和 Han 开发的CB-SVM（一种用于大数据集的基于微聚类的SVM 算法）[YYH03]。Chang 和 Lin 在 http://www.csie.ntu.edu.tw/~cjlin/libsvm/ 提供了一个支持向量机软件库，支持多类分类。

存在几个基于规则的分类器示例。这些包括AQ15（Hong, Mozetic, 和 Michalski [HMM86]）、CN2（Clark 和 Niblett [CN89]）、ITRULE（Smyth 和 Goodman [SG92]）、RISE（Domingos [Dom94]）、IREP（Furnkranz 和 Widmer [FW94]）、RIPPER（Cohen [Coh95]）、FOIL（Quinlan 和 Cameron-Jones [Qui90,QCJ93]）以及Swap-1（Weiss 和 Indurkhya [WI98]）。有关从决策树中提取规则，参见Quinlan [Qui87,Qui93]。Major 和 Mangano [MM95] 中可以找到识别给定规则集中最有趣规则的规则细化策略。

已提出许多将频繁模式挖掘适应分类任务的算法。关联分类的早期研究包括Liu, Hsu, 和 Ma 提出的CBA 算法 [LHM98]。Dong 和 Li [DL99] 以及Li, Dong, 和 Ramamohanarao [LDR00] 提出了一种使用新兴模式（不同数据集之间支持度显著变化的项集）的分类器。Li, Han, 和 Pei [LHP01] 提出了CMAR。Yin 和 Han [YH03] 提出了CPAR。Cong, Tan, Tung, 和 Xu 描述了RCBT，一种用于以高精度对高维基因表达数据进行分类的挖掘top-k 覆盖规则组的方法 [CTTX05]。

Wang 和 Karypis [WK05] 提出了HARMONY（用于以实例为中心分类的最高置信度分类规则挖掘），它借助修剪策略直接挖掘最终分类规则集。Lent, Swami, 和 Widom [LSW97] 提出了ARCS 系统，用于挖掘多维关联规则。它结合了关联规则挖掘、聚类和图像处理的思想，并将其应用于分类。Meretakis 和 Wüthrich [MW99] 提出通过挖掘长项集来构建朴素贝叶斯分类器。Veloso, Meira, 和 Zaki [VMZ06] 提出了一种基于惰性（非急切）学习方法的关联规则基础分类方法，其中计算按需执行。

Cheng, Yan, Han, 和 Hsu [CYHH07] 以及Cheng, Yan, Han, 和 Yu [CYHY08] 开展了基于歧视性频繁模式分类的研究。前者工作确立了频繁模式歧视能力的理论上界（基于信息增益 [Qui86] 或Fisher score [DHS01]），可用于设置最小支持度的策略。后者工作描述了DDPMine 算法，这是一种直接挖掘用于分类的歧视性频繁模式的方法，因为它避免生成完整的频繁模式集。Kim et al. 提出了NDPMine 算法，通过考虑重复特征来执行频繁和歧视性模式基础分类 [KKW+10]。Shang, Tong, Peng, 和 Han 提出了一个名为DPClass 的简洁有效的基于歧视性模式的分类框架 [SPTH16]。

Zhu [Zhu05] 提出了关于半监督分类的全面综述。有关更多参考文献，参见由Chapelle, Schlölkopf, 和 Zien 编辑的书籍 [ClZ06]。Bennett 和 Demiriz [BD+99] 开发了名为S3SVM 的半监督SVM。有关主动学习的综述，参见Settles [Set10]。Tong 和 Chang 开发了一种基于版本空间概念的主动SVM 方法 [TC01]。He 和 Carbonell 开发了一种基于最近邻的主动学习方法，用于发现新类。Pan 和 Yang 提出了关于迁移学习的综述 [PY10]。Dai, Yang, Xue, 和 Yu [DYXY07] 给出了用于迁移学习的TrAdaBoost 提升算法。有关迁移学习中的负迁移效应，参见Rosenstein, Marx, Kaelbling, 和 Dietterich [RMKD05]。Ge et al. [GGN+14] 开发了一种基于Rademacher 分布的有效方法，以减轻多源迁移学习中的负迁移。

Go, Bhayani, 和 Huang 开发了一种使用远程监督的情感分类方法。Zubiaga 和 Ji 提出使用网页目录作为Twitter 分类的远程监督。或者，Magdy, Sajjad, El-Ganainy, 和 Sebastiani 将YouTube 标签作为Twitter 分类的远程监督。Ratner et al. [RBE+17] 开发了Snorkel，这是一个允许用户依赖标记函数而非手动标记来训练机器学习算法的系统。Palatucci, Pomerleau, Hinton, 和 Mitchell [PPHM09] 开发了一种基于语义输出代码的零样本学习方法。Romera-Paredes 和 Torr [RPT15] 提出了一种基于两层线性网络的简单而有效的零样本学习方法。Wang, Zheng, Yu, 和 Miao [WZYM19] 提出了关于零样本学习的全面综述。有关零样本学习的评估，参见Xian, Schiele, 和 Akata [XSA17]。

Wang, Fan, Yu, 和 Han [WFYH03] 开发了一种用于对漂移概念的流数据进行分类的集成方法。Hulten, Spencer, 和 Domingos 开发了一种基于决策树的替代方法，用于流数据分类。Aggarwal, Han, Wang, 和 Yu 提出了一种按需分类方法，动态选择时间窗口以训练流数据分类器。Masud et al. [MGK+08] 开发了一种用于对数据流进行分类的半监督方法。Aggarwal [Agg07] 的书籍对各种流数据挖掘任务进行了广泛覆盖。Keogh 和 Pazzani [KP00] 开发了一种可扩展的方法来计算时间扭曲距离。Lodhi et al. [LSST+02] 中可以找到字符串核在文本分类中的应用。有关序列数据分类的综述，参见Xing, Pei, 和 Keogh [XPK10] 以及Dietterich [Die02]。Tong, Faloutsos, 和 Pan [TFP06] 开发了一种快速带重启的随机游走方法，用于计算图上节点邻近性。Henderson et al. [HGL+11] 提出以递归方式生成图结构特征。存在许多图相似性或核方法，例如Vishwanathan, Schraudolph, Kondor, 和 Borgwardt 的随机游走图核 [VSKB10] 以及Shervashidze et al. 的Weisfeiler-Lehman 图核 [SSVL+11]。有关不同图相似性度量的比较，参见Koutra et al. [KSV+16]。

Hastie 和 Tibshirani [HT98]、Tax 和 Duin [TD02] 以及Allwein, Schapire, 和 Singer [ASS00] 描述了多类分类工作。Dietterich 和 Bakiri [DB95] 提出使用纠错码进行多类分类。Weinberger 和 Saul [WS09] 为最近邻分类引入了距离度量学习。Xing, Jordan, Russell, 和 Ng [XJRN02] 在聚类背景下研究了距离度量学习。Movshovitz-Attias et al. [MATL+17] 提出使用基于代理的损失来加速距离度量学习的收敛。有关距离度量学习的综述，参见Yang 和 Jin [YJ06] 以及Wang 和 Sun [WS15]。Ribeiro, Singh, 和 Guestrin [RSG16] 提出了LIME 来解释分类器。已开发许多替代解释技术，例如[LL17] 的Shapley 值、Koh 和 Liang 的影响函数 [KL17] 以及Van Looveren 和 Klaise 的反事实解释 [VLK19]。为了全面介绍

