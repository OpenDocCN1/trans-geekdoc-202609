

# 用于智能故障诊断的无监督深度迁移学习 ■ 131

![](img/f29bba55de4872c43f26af4667e705f2_141_0.png)

![](img/f29bba55de4872c43f26af4667e705f2_141_1.png)

图 7.14 与瓶颈层相关的四种情况对比。

负迁移。基于 UDTL 的智能故障诊断（IFD）主要有四种场景，但使用两个数据集的所有实验都是关于不同工作工况之间的迁移。为了说明这些场景不适用于生成正迁移，我们使用 PU 数据集设计了另一个迁移任务，考虑了不同数据生成方法之间的迁移。每个任务包含三个健康状态，详细信息列于表 7.6 中。总共有两种迁移学习场景。

迁移结果如图 7.15 所示。我们观察到每种方法与时间域或频域输入都存在负迁移，这种现象表明该构建的任务可能不适用于迁移学习任务。实际上，也有一些发表的论文设计了迁移学习任务，解决将齿轮样本迁移到轴承样本（这可能不是可靠的迁移任务）或将实验数据迁移到真实数据（如果两台机器的结构不同，也可能不是可靠的迁移任务）。因此，首先弄该任务是否适用于迁移学习以及哪些领域具有共享特征是非常重要的。

# 表 7.6 带有人工损伤的轴承信息

| 任务 | 制造方法 | 损伤位置 | 损伤程度 | 轴承代码 | 标签 |
|---|---|---|---|---|---|
| 0 | 电刻机 | 外圈 | 1 | KA05 | 0 |
| | 电刻机 | 外圈 | 2 | KA03 | 1 |
| | 电刻机 | 内圈 | 1 | KI03 | 2 |
| 1 | 电火花加工与钻孔 | 外圈 | 1 | KA01 和 KA07 | 0 |
| | 钻孔 | 外圈 | 2 | KA08 | 1 |
| | 电火花加工 | 内圈 | 1 | KI01 | 2 |

# 132 ■ 深度神经网络驱动的机械系统智能故障诊断

![](img/f29bba55de4872c43f26af4667e705f2_142_0.png)

图 7.15 这些方法对应基准的准确率偏差。(F) 表示频域输入，(T) 表示时间域输入。

物理先验。对于基于 UDTL 的 IFD，许多学者仅引入了其他领域已存在的方法来执行故障诊断，而较少关注数据背后的先验知识（缺乏对物理系统中特殊现象或规则的使用）。因此，我们建议学者可以从迁移学习领域的核心思想中学习（不仅仅是使用现有方法），并将物理系统的先验知识引入到提出的方法中，以在工业应用中构建更具针对性、更合适且具有更高识别率的诊断模型。

其他方面。尽管可以收集到不同工况的大量数据，但某些工况下的故障数据仍然稀缺。由于大多数机器在正常状态下运行，类别平衡问题在实际应用中自然存在。因此，结合迁移学习方法的不平衡学习或少样本学习（Wu 等人 2020）可能是让构建算法更好地落地的重要方向。

联邦迁移学习（FTL）（Liu et al. 2020）为特定行业提供了一种更安全、可靠的方法。同时，基于迁移学习的特性，FTL 参与者可以拥有自己的特征空间，而不需要所有参与者拥有或使用相同的特征数据，这使得 FTL 适用于更多应用场景。FTL 已用于 IFD（Zhang and Li 2021），并需深入研究。

不确定性量化在评估 DL 模型构建、优化和决策过程的安全性方面起着关键作用。贝叶斯网络（Gal and Gahramani 2016）和集成学习技术（Lakshminarayanan, Pritzel, and Blundell 2017）是广泛使用的不确定性方法，它们的有效性已在自动驾驶汽车等不同应用中得到验证。因此，不确定性可以作为辅助项进一步纠正迁移学习过程中的某些不恰属性。例如，在语义分割训练期间显式地估计预测（Zheng and Yang 2021）。

# 结论

本章根据不同任务构建了一个分类法，并对基于 UDTL 的 IFD 进行了简单回顾。收集了两个公共数据集，从多个角度对基于 UDTL 的方法进行了对比分析。基于这项系统研究，不同方法的结果表明，联合分布假设和对抗训练是提高准确性的两种有效技术。同时，不同的输入类型往往定义了提高准确性的关键。基于 UDTL 的 IFD 的稳定性和鲁棒性需要重视。总之，在开发新模型之前考虑到这些结果可能会有用。

# 参考文献

- Borgward, Karsten, Arthur Gretton, Hans-Peter Kriegel, Bernhard Schölkopf, and Alex Smola. 2016. "Integrating Data by Kernel Mean Discrepancy." *Bioinformatics* 22(14): e49–e57. https://doi.org/10.1093/bioinformatics/242.
- Cao, Xincheng, Bingqian Chen, and Nianyan Zeng. 2022. "Deep Adaptation Model With Multi-Task Networks for Planetary Gear Diagnosis." *Neurocomputing* 49: 173–190. https://doi.org/10.1016/j.neucom.2020.064.
- Cheng, Bingtong, Guijun Ma, and Ye Yuan. 2020. "Wasserstein Based Deep Transfer Learning for Intelligent Fault Diagnosis With Unlabeled Data." *Neurocomputing* 39:35–45. https://doi.org/10.1016/j.neucom.2020.940.
- Gan, Yarin, Evgeniya Ustinaova, Hana Pascal, Germain Hugo, Francois Laviolette, Mario March, and Victor Lempitsky. 2016. "Domain-Adversarial Training of Neural Networks." *The Journal of Machine Learning Research* 17(1): 2096–2130. https://jmlr.org/papers/v17-239.html.
- Glorot, Xavier, Antoine Bordes, and Yoshua Bengio. 2011. "Domain Adaptation for Large-Scale." Proceedings of the 28th.
- Gretton, Arthur, Dino Stuart, 2012. "Integrating Data by Kernel Mean Discrepancy." *Bioinformatics* 22(14): e49–e57. https://doi.org/10.1093/bioinformatics/242.
- Han, Te, Chao Liu, Wenquang Yang, and Dongxiang Jiang. 2019. "Revisiting batch normalization for practical domain adaptation." arXiv preprint:1603.0479.
- Han, Te, Chao Liu, Wenquang Yang, and Dongxiang Jiang. 2020. "Simple and Scalable Predictive Estimation Using Ensembles." *Advances in Information Systems* 30.
- Lakshminarayanan, Ali, Alexander Pritzel, and Charlesundell. 2017. "Simple and Scalable Predictive Estimation Using Ensembles." *Advances in Information Systems* 30.
- Lessmeier, Christian, 2016. "Condition Monitoring of Bearing Damage Using Current Signals: A Benchmark." PHM European Conference.
- Li, Qiqing, Baoqi, Lei Deng, Yanling Wu, and Yi Wang. 2020. "Deep Balanced Domain Adaptation for Fault Diagnosis of Planetary Gearboxes Limited Labeled." *Measurement* 156: 10750.
- Li, Wei, Qian Dian, and Jian-Qiao Sun. 2019. "Multi-Layer Domain Adaptation for Rolling Fault Diagnosis." *Signal Processing* 157:180–197.
- Li, Yagao, Nian Yang, Shijing Jia, and Xiaodi Hu. 2016. "Revisiting batch normalization for practical domain adaptation." arXiv preprint:1603.0479.
- Li, Yibin, Yan Sun, and Qqiang Li, and Meikang Qu. 2020. "Intelligent Fault Diagnosis by Fusing Domain Adversarial Training and Maximum Mean Discrepancy via Ensemble Learning." *IEEE Transactions on Industrial Informatics* 17 (4): 2833–2841.
- Long, Mingheng, Yue Cao, Jianmin Wang, and Michael Jordan. 2015. "Learning Transferable Features with Deep Adaptation Networks." International Conference on Machine Learning.
- Long, Mingheng, Jianmin Wang, Guiguang Ding, Jiaguant Sun, and Philip S Y. 2013. "Transfer feature learning with joint distribution adaptation." Proceedings of the IEEE conference on computer vision.

