

# 第15章：联邦学习中的数据估值

受机器学习应用中评估数据价值的兴趣日益增长的驱动，本章概述了协作机器学习中的数据估值方法，重点关注联邦学习。数据估值为协作学习场景中的数据集提供了一种可解释的贡献归因方法。然而，必须注意现有方法的局限性以及未来研究的开放问题。

首先，当前的垂直数据估值方法并未针对 `FL` 的迭代学习过程量身定制。我们是应该对最终模型进行特征估值，还是像水平数据估值那样考虑按轮次估值，这尚有争议。其次，基于学习的估值仅应用于 `HFL`。探讨基于学习的估值在 `VFL` 上的适用性将很有趣。第三，通信带宽、算力、客户端的诚实度和可用性等属性是客户端对 `FL` 贡献的额外维度，这些有可能构成一个更完整的客户端估值框架。开放问题清单当然并不详尽，我们邀请感兴趣的读者对这一具有实际意义的新兴领域开展进一步研究。

总之，我们讨论了将传统数据估值方法扩展到联邦设置中的情况，并描述了专门为 `FL` 开发的水平和垂直数据估值方法。本章为一套多功能工具箱提供了指南，使 `FL` 从业者能够在各种场景中应用数据估值。

## 参考文献

*   [[1]](#Chp015_281-296_B9780443190377000247.xhtml#cf0255) Gavin Brown, Adam Pocock, Ming-Jie Zhao, Mikel Luján, Conditional likelihood maximisation: a unifying framework for information theoretic feature selection, *Journal of Machine Learning Research* 2012;13(1):27–66.
*   [[2]](#Chp015_281-296_B9780443190377000247.xhtml#cf0315) Wei-Sheng Chin, Bo-Wen Yuan, Meng-Yuan Yang, Yong Zhuang, Yu-Chin Juan, Chih-Jen Lin, LIBMF: a library for parallel matrix factorization in shared-memory systems, *Journal of Machine Learning Research* 2016;17(86):1–5.
*   [[3]](#Chp015_281-296_B9780443190377000247.xhtml#cf0170) R. Dennis Cook, Detection of influential observation in linear regression, *Technometrics* 1977;19(1):15–18.
*   [[4]](#Chp015_281-296_B9780443190377000247.xhtml#cs0020_1) Soumi Das, Manasvi Sagarkar, Suparna Bhattacharya, Sourangshu Bhattacharya, CheckSel: Efficient and accurate data-valuation through online checkpoint selection, 2022.
*   [[5]](#Chp015_281-296_B9780443190377000247.xhtml#cf0195) P. Dubey, On the uniqueness of the Shapley value, *International Journal of Game Theory* 1975;4(3):131–139.
*   [6] Zhenan Fan, Huang Fang, Zirui Zhou, Jian Pei, Michael P. Friedlander, Changxin Liu, Yong Zhang, Improving fairness for data valuation in horizontal federated learning, *Proc. ICDE*. 2022:2440–2453.
*   [7] Amirata Ghorbani, James Zou, Data Shapley: equitable valuation of data for machine learning, *Proc. ICML*. 2019:2242–2251.
*   [8] Xiao Han, Leye Wang, Junjie Wu, Data valuation for vertical federated learning: an information-theoretic approach, [arXiv:2112.08364](http://www.arxiv.org/abs/2112.08364); 2021.
*   [[9]](#Chp015_281-296_B9780443190377000247.xhtml#cs0025_1) Andreas Krause, Carlos Guestrin, Nonmyopic active learning of Gaussian processes: an exploration-exploitation approach, *Proc. ICML*. 2007:449–456.
*   [[10]](#Chp015_281-296_B9780443190377000247.xhtml#cs0025_2) John K. Kruschke, Bayesian approaches to associative learning: from passive to active learning, *Learning & Behavior* 2008;36(3):210–226.
*   [[11]](#Chp015_281-296_B9780443190377000247.xhtml#cf0285) Yongchan Kwon, James Zou, Beta Shapley: a unified and noise-reduced data valuation framework for machine learning, *Proc. AISTATS*. 2022.
*   [[12]](#Chp015_281-296_B9780443190377000247.xhtml#cf0230) Scott M. Lundberg, Su-In Lee, A unified approach to interpreting model predictions, *Proc. NeurIPS*. 2017:4768–4777.
*   [[13]](#Chp015_281-296_B9780443190377000247.xhtml#cf0105) Vassil Panayotov, Guoguo Chen, Daniel Povey, Sanjeev Khudanpur, LibriSpeech: an ASR corpus based on public domain audio books, *Proc. ICASSP*. 2015:5206–5210.
*   [[14]](#Chp015_281-296_B9780443190377000247.xhtml#cf0340) Zhuan Shi, Lan Zhang, Zhenyu Yao, Lingjuan Lyu, Cen Chen, Li Wang, Junhao Wang, Xiang-Yang Li, FedFAIM: a model performance-based fair incentive mechanism for federated learning, *IEEE Transactions on Big Data* 2022:1–13.
*   [[15]](#Chp015_281-296_B9780443190377000247.xhtml#cf0165) Rachael Hwee Ling Sim, Yehong Zhang, Mun Choon Chan, Bryan Kian Hsiang Low, Collaborative machine learning with incentive-aware model rewards, *Proc. ICML*. 2020:8927–8936.
*   [16] Tianshu Song, Yongxin Tong, Shuyue Wei, Profit allocation for federated learning, *Proc. IEEE Big Data*. 2019:2577–2586.
*   [[17]](#Chp015_281-296_B9780443190377000247.xhtml#cf0155) Sebastian Shenghong Tay, Xinyi Xu, Chuan Sheng Foo, Bryan Kian Hsiang Low, Incentivizing collaboration in machine learning via synthetic data rewards, *Proc. AAAI*. 2022.
*   [[18]](#Chp015_281-296_B9780443190377000247.xhtml#cf0245) Guan Wang, Charlie Xiaoqian Dang, Ziye Zhou, Measure contribution of participants in federated learning, *Proc. IEEE Big Data*. 2019:2597–2604.
*   [[19]](#Chp015_281-296_B9780443190377000247.xhtml#cf0185) Jiacheng Wang, Ruoxi Jia, Data Banzhaf: a data valuation framework with maximal robustness to learning stochasticity, *Proc. AISTATS*. 2023.
*   [20] Tianhao Wang, Johannes Rausch, Ce Zhang, Ruoxi Jia, Dawn Song, A principled approach to data valuation for federated learning, *Federated Learning*. Springer; 2020:153–167.
*   [21] Zhaoxuan Wu, Yao Shu, Bryan Kian Hsiang Low, DAVINZ: data valuation using deep neural networks at initialization, *Proc. ICML*. 2022.
*   [[22]](#Chp015_281-296_B9780443190377000247.xhtml#cf0320) Xinyi Xu, Lingjuan Lyu, Xingjun Ma, Chenglin Miao, Chuan Sheng Foo, Bryan Kian Hsiang Low, Gradient driven rewards to guarantee fairness in collaborative machine learning, *Proc. NeurIPS*. 2021:16104–16117.
*   [23] Xinyi Xu, Zhaoxuan Wu, Chuan Sheng Foo, Bryan Kian Hsiang Low, Validation free and replication robust volume-based data valuation, *Proc. NeurIPS*. 2021:10837–10848.
*   [[24]](#Chp015_281-296_B9780443190377000247.xhtml#cf0190) Tom Yan, Ariel D. Procaccia, If you like Shapley then you'll love the core, *Proc. AAAI*. 2021:5751–5759.
*   [25] Jinsung Yoon, Sercan O. Arik, Tomas Pfister, Data valuation using reinforcement learning, *Proc. ICML*. 2020:10842–10851.
*   [26] Jie Zhao, Xinghua Zhu, Jianzong Wang, Jing Xiao, Efficient client contribution evaluation for horizontal federated learning, *Proc. ICASSP*. 2021:3060–3064.

# 第3部分：应用与伦理考量

## 大纲

*   [第16章 联邦学习中的激励机制](#Chp016_299-309_B9780443190377000260.xhtml)
*   [第17章 量子联邦机器学习导论](#Chp017_311-328_B9780443190377000272.xhtml)
*   [第18章 面向量子联邦学习的联邦量子自然梯度下降](#Chp018_329-341_B9780443190377000284.xhtml)
*   [第19章 面向联邦学习的移动计算框架](#Chp019_343-352_B9780443190377000296.xhtml)
*   [第20章 面向隐私保护语音识别的联邦学习](#Chp020_353-368_B9780443190377000302.xhtml)
*   [第21章 与联邦学习相关的伦理考量与法律问题](#Chp021_369-391_B9780443190377000326.xhtml)

# 第16章：联邦学习中的激励机制

