
| Baby | 1900 | 104 | 8,424/63,144 |
| Magazine | 1970 | 117 | 11,552/63,144 |
| Software | 1915 | 129 | 5,788/63,144 |
| Sports | 2000 | 94 | 9,816/63,144 |
| IMDN | 2000 | 269 | 25,195/63,144 |
| MR | 2000 | 21 | 7,315/63,144 |

结果如图 10.4 所示。可以观察到，测试损失与合成数据集情况一致。尽管 `BiG-FL` 的测试曲线在收敛早期阶段有一些波动，但最终实现了最低损失。原因可能是 LL 学习模型之间的竞争，这影响了 UL 问题中的嵌入搜索进程，一旦图结构被学习，`BiG-FL` 将展现出稳定的收敛行为。该示例验证了在多任务联邦学习问题中利用词嵌入间相似性的重要性，以及 `BiG-FL` 求解此类问题的优越性。

![图 10.4 真实数据实验结果（测试损失）。](img/gr008.jpg)

**图 10.4 真实数据实验结果（测试损失）。**

## 10.6 小结

在本章中，我们介绍了 `GFL` 框架的三大主要类别，包括去中心化联邦学习、多中心联邦学习和双层优化增强联邦学习。每种 FL 模型主要适用于不同的实际 FL 场景，其中 `DFL` 专为以去中心化方式在图上收集的数据样本设计，多中心 FL 用于聚类数据结构，而 `BiG-FL` 在整合通用拓扑信息并适应本地学习任务方面表现优越。鉴于这些 `GFL` 模型的独特特性，我们进一步研究了基于梯度的高效算法，以联邦学习的方式求解相应的优化问题。结论是，面向图结构的 FL 系统在学习效率和泛化性能方面均可改进经典的 `FedAvg` FL。

## 参考文献

*   [\[1\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0300) Yoshua Bengio, Réjean Ducharme, Pascal Vincent, A neural probabilistic language model, *Advances in Neural Information Processing Systems* 2000;13.
*   [\[2\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0060) Tsung-Hui Chang, Mingyi Hong, Hoi-To Wai, Xinwei Zhang, Songtao Lu, Distributed learning in the nonconvex world: from batch data to streaming and beyond, *IEEE Signal Processing Magazine* 2020;37(3):26–38.
*   [\[3\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0175) Xiaodong Cui, Songtao Lu, Brian Kingsbury, Federated acoustic modeling for automatic speech recognition, *Proceedings of IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*. 2021:6748–6752.
*   [\[4\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0180) Alireza Fallah, Aryan Mokhtari, Asuman Ozdaglar, Personalized federated learning with theoretical guarantees: a model-agnostic meta-learning approach, *Proceedings of Advances in Neural Information Processing Systems (NeurIPS)*. 2020.
*   \[5\] Saeed Ghadimi, Mengdi Wang, Approximation methods for bilevel programming, [arXiv:1802.02246](http://www.arxiv.org/abs/1802.02246); 2018.
*   [\[6\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0040) Avishek Ghosh, Jichan Chung, Dong Yin, Kannan Ramchandran, An efficient framework for clustered federated learning, *Proceedings of Advances in Neural Information Processing Systems (NeurIPS)*. 2020:19586–19597.
*   \[7\] Will Hamilton, Zhitao Ying, Jure Leskovec, Inductive representation learning on large graphs, *Proceedings of Advances in Neural Information Processing Systems (NeurIPS)*. 2017.
*   [\[8\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0205) Thomas N. Kipf, Max Welling, Semi-supervised classification with graph convolutional networks, [arXiv:1609.02907](http://www.arxiv.org/abs/1609.02907); 2016.
*   [\[9\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0285) Pengfei Liu, Xipeng Qiu, Xuanjing Huang, Adversarial multi-task learning for text classification, [arXiv:1704.05742](http://www.arxiv.org/abs/1704.05742); 2017.
*   [\[10\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0050) Rui Liu, Han Yu, Federated graph neural networks: overview, techniques and challenges, [arXiv:2202.07256](http://www.arxiv.org/abs/2202.07256); 2022.
*   [\[11\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0065) Wei Liu, Li Chen, Wenyi Zhang, Decentralized federated learning: balancing communication and computing costs, *IEEE Transactions on Signal and Information Processing over Networks* 2022;8:131–143.
*   [\[12\]](#Chp010_181-197_B9780443190377000181.xhtml#cs0010_2) Songtao Lu, Xiaodong Cui, Mark S. Squillante, Brian Kingsbury, Lior Horesh, Decentralized bilevel optimization for personalized client learning, *Proceedings of IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*. 2022:5543–5547.
*   [\[13\]](#Chp010_181-197_B9780443190377000181.xhtml#cs0010_2) Songtao Lu, Jason D. Lee, Meisam Razaviyayn, Mingyi Hong, Linearized ADMM converges to second-order stationary points for non-convex problems, *IEEE Transactions on Signal Processing* 2021;69:4859–4874.
*   \[14\] Songtao Lu, Chai Wah Wu, Decentralized stochastic non-convex optimization over weakly connected time-varying digraphs, *Proceedings of IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)*. 2020:5770–5774.
*   [\[15\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0185) Songtao Lu, Siliang Zeng, Xiaodong Cui, Mark S. Squillante, Lior Horesh, Brian Kingsbury, Jia Liu, Mingyi Hong, A stochastic linearized augmented Lagrangian method for decentralized bilevel optimization, *Proceedings of Advances in Neural Information Processing Systems (NeurIPS)*. 2022.
*   \[16\] Songtao Lu, Xinwei Zhang, Haoran Sun, Mingyi Hong, GNSD: A gradient-tracking based nonconvex stochastic algorithm for decentralized optimization, *Proceedings of IEEE Data Science Workshop (DSW)*. 2019:315–321.
*   \[17\] Songtao Lu, Yawen Zhang, Yunlong Wang, Decentralized federated learning for electronic health records, *Proceedings of the 54th Annual Conference on Information Sciences and Systems (CISS)*. 2020.
*   \[18\] Brendan McMahan, Eider Moore, Daniel Ramage, Seth Hampson, Blaise Aguera y Arcas, Communication-efficient learning of deep networks from decentralized data, *Proceedings of International Conference on Artificial Intelligence and Statistics (AISTATS)*. 2017:1273–1282.
*   [\[19\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0295) Jeffrey Pennington, Richard Socher, Christopher D. Manning, GloVe: global vectors for word representation, *Proceedings of Empirical Methods in Natural Language Processing (EMNLP)*. 2014:1532–1543.
*   [\[20\]](#Chp010_181-197_B9780443190377000181.xhtml#cs0015_2) Haoran Sun, Songtao Lu, Mingyi Hong, Improving the sample and communication complexity for decentralized non-convex optimization: joint gradient estimation and tracking, *Proceedings of International Conference on Machine Learning*. 2020:9217–9228.
*   [\[21\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0085) Hanlin Tang, Xiangru Lian, Ming Yan, Ce Zhang, Ji Liu, D²: decentralized training over decentralized data, *Proceedings of International Conference on Machine Learning (ICML)*. 2018:4848–4856.
*   [\[22\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0275) Minjie Wang, Da Zheng, Zihao Ye, Quan Gan, Mufei Li, Xiang Song, Jinjing Zhou, Chao Ma, Lingfan Yu, Yu Gai, Tianjun Xiao, Tong He, George Karypis, Jinyang Li, Zheng Zhang, Deep graph library: a graph-centric, highly-performant package for graph neural networks, [arXiv:1909.01315](http://www.arxiv.org/abs/1909.01315); 2019.
*   [\[23\]](#Chp010_181-197_B9780443190377000181.xhtml#cf0070) Lin Xiao, Stephen Boyd, Sanjay Lall, A scheme for robust distributed sensor fusion based on average consensus, *Proceedings of the Fourth International Symposium on Information Processing in Sensor Networks*. 2005:63–70.
*   \[24\] Ming Xie, Guodong Long, Tao Shen, Tianyi Zhou, Xianzhi Wang, Jing Jiang, Multi-center federated learning, [arXiv:2005.01026](http://www.arxiv.org/abs/2005.01026); 2020.
*   \[25\] Pengwei Xing, Songtao Lu, Lingfei Wu, Han Yu, BiG-Fed: Bilevel optimization enhanced graph-aided federated learning, *IEEE Transactions on Big Data* 2022.

# 第 11 章：纵向异步联邦学习：算法与理论保证

Tianyi Chen^(a)；Xiao Jin^(a)；Yuejiao Sun^(b)；Wotao Yin^(c) ^a 伦斯勒理工学院，特洛伊，纽约，美国

^b 加州大学洛杉矶分校，洛杉矶，加利福尼亚，美国

^c 阿里巴巴集团，贝尔维尤，华盛顿，美国

## 摘要

联邦学习（FL）支持利用多客户端数据进行模型训练，适用于因隐私顾虑和协调挑战而无法使用传统机器学习方法的场景。具体而言，横向联邦学习处理共享相同特征集的多客户端数据，而纵向联邦学习处理同一组主体的数据，但不同客户端持有其不同的特征。本章将纵向联邦学习建模为一个优化问题，并开发了一种*简单且实用*的联邦学习方法。该新方法允许每个客户端运行随机梯度算法，而无需与其他客户端协调，因此适用于间歇性甚至不可控的客户端。理论上，我们分别给出了强凸、非凸甚至非光滑目标函数下该方法的收敛速率。实证上，我们将该方法应用于各种图像和医疗数据集上的联邦逻辑回归和深度学习。

### 关键词

纵向联邦学习；异步分布式优化；差分隐私

## 致谢

本工作得到美国国家科学基金会 CAREER 奖项 2047177 的支持，以及伦斯勒-IBM 人工智能研究合作（[`airc.rpi.edu`](http://airc.rpi.edu)），该合作是 IBM AI Horizons Network（[`ibm.biz/AIHorizons`](http://ibm.biz/AIHorizons)）的一部分。

## 11.1 引言
