

![](img/a2afc74fc22d678e24674964f5d46bc8_8_0.png)

![](img/a2afc74fc22d678e24674964f5d46bc8_8_1.png)

不带 TPUPoint-Optimizer 的 TPUv2 和 TPUv3。图 [16] 显示了带有和不带 TPUPoint-Optimizer 的朴素实现对 TPUv2 和 TPUv3 的 MXU 利用率。TPUPoint-Optimizer 增加了 TPUv2 和 TPUv3 朴素实现的 TPU 空闲时间（图 [15]）并提高了 TPUv2 的 MXU 利用率（图 [16]）。因此，TPUPoint-Optimizer 能够通过更高效地使用 Cloud TPU 带来性能提升，其中 TPUv2 表现出对矩阵运算依赖的显著变化。当我们将 TPUPoint-Optimizer 应用于原先执行时间不足二十分钟的朴素工作负载（BERT 和 DCGAN）时，这些工作负载的速度与原始性能相比没有显著变化。相比之下，当我们将 TPUPoint-Optimizer 应用于原先耗时超过二十分钟的朴素工作负载（QANet 和 RetinaNet）时，我们确实看到了速度的改善——这并不令人意外，因为执行时间较长的工作负载相对于执行时间较短的工作负载，涉及更大、更复杂的数据集和更深层的实现。由于 TPUv3 仅仅是包含 TPUv2 两倍数量的 MXU 和 HBM，我们没有观察到 TPUPoint-Optimizer 对 TPUv3 带来性能提升。事实上，由于我们分析/优化工具的开销，我们观察到平均性能损失低于 10%。尽管如此，这些结果表明，与完整程序执行相关的开销相比，TPUPoint-Optimizer 相关的开销相对微不足道。

## VIII. 相关工作

针对架构模拟而非全系统分析（SimPoint [19], [21], [22] 的关键概念）以及将相似程序行为聚类为程序阶段（如 HyGCN [33] 所做）启发了 TPUPoint 的开发。TPUPoint 还整合了 TurboSMARTS [34] 的检查点和重启功能，以节省架构模拟时间并降低云计算成本。

TPUPoint 和 ParaDnn [35] 均提供工具和系统方法论来分析 Cloud TPU 性能。TPUPoint 在自动且隐式地重写性能不佳的代码的同时，向程序员提供直接反馈。相比之下，ParaDnn 侧重于架构视角下的系统性测试和优化洞察，因此与 TPUPoint 互补。

除了使用 Cloud TPU，数据中心还经常依赖异构硬件组件来加速 ML 工作负载 [36]–[53]。然而，硬件解决方案通常不易于分发。由于 TPUPoint 在编程语言/应用程序级别工作以观察和优化性能，TPUPoint 具有可移植性；只需更改 TPUPoint 用于检索统计信息的低级库函数调用，即可使 TPUPoint 的分析和优化在多种平台上可用。

一些基准套件也试图标准化 ML 工作负载管理：$\mu$ Suite [54]、BigDataBench [55]、AI Benchmark [56]、EEMBC MLMark Benchmark [57]、[58]、Fathom [59]、AI Matrix [60]、DeepBench [61]、DAWNBench [62] 和 MLPerf [63]，以及混合精度基准 [64]、[65]。在对 Cloud TPU 进行基准测试时，由于 Cloud TPU 平台的前端编程语言支持有限，我们只能测试每个基准套件的一个子集。话虽如此，许多基准依赖相同的模型和数据集，仅不同框架和实现。我们已尽力覆盖 ML 工作负载的全谱。

此前已有若干关于 ML 摘要的论文，例如 EcoRNN [66]、SeqPoints [67] 和 TBD [68]。这些工作并未尝试像 TPUPoint 那样对同一范围的基准进行分析/优化，其中计算可能与输入无关或在不同迭代中具有异构性。EcoRNN 和 TBD 分别针对 LSTM RNN 和 DNN 采用基于采样和迭代的方法，而 SeqPoint 则考虑输入变化如何影响基于序列的神经网络（SQNN）。为了对如此广泛的 ML 工作负载提供洞察，TPUPoint 致力于实现高覆盖率和低开销，无论 ML 工作负载如何。

由于 ML 工作负载在云服务中占据主导地位，优化资源利用率的方法已受到广泛关注。一些方法使用性能估算算法 [69]–[73] 或训练模型 [74]–[76] 来选择最优参数。此类方法倾向于拥有停滞的选择器，尽管其开销较低，但在适应新工作负载方面能力有限。TPUPoint 不仅仅关注特定工作负载，而是提供一个更通用的框架，适用于更广泛的 ML 任务范围。

## IX. 结论

本文介绍了 TPUPoint，这是一个用于收集、分析和优化 TPU 加速 ML 工作负载性能的工具链。使用事后分析工具 TPUPoint-Analyzer，我们确定大多数 TPU 加速 ML 工作负载未充分利用宝贵的 TPU 资源。此外，由于工作负载行为随模型和数据集而异，手动优化工作负载不可行。幸运的是，工作负载内部的行为通常具有重复性，为动态优化打开了大门。利用从 TPUPoint-Analyzer 获得的观察结果，我们设计了 TPUPoint-Optimizer 以检测主要应用阶段并在运行代码中动态调整参数。结果表明，在无需程序员干预的情况下，相对于默认参数实现了 1.12× 的加速比。

## 致谢

作者们要感谢匿名审稿人提供的有益意见。我们要感谢 TensorFlow Research Cloud (TFRC) 为我们提供 Cloud TPU 的访问权限和支持。我们还要感谢 Christopher Fraser 出色的文本编辑工作。该工作由国家科学基金会 (NSF) 奖项 CNS-2007124 资助。

## 参考文献

- [1] Y. Deng, F. Bao, Y. Kong, Z. Ren, 和 Q. Dai, "面向金融信号表示和交易的深度直接强化学习," IEEE Transactions on Neural Networks and Learning Systems, 第 28 卷, 第 3 期, 第 653–664 页, 2017.
- [2] X. Ding, Y. Zhang, T. Liu, 和 J. Duan, "面向事件驱动股票预测的深度学习," 收录于 IJCAI'15. AAAI Press, 2015, 第 23272333 页.
- [3] A. Grover 和 J. Leskovec, "Node2vec: 面向网络的可扩展特征学习," 收录于第 22 届 ACM SIGKDD 知识发现与数据挖掘国际会议论文集, ser. KDD '16. New York, NY, USA: 计算机协会, 2016, 第 855–864 页. [在线]。可用: https://doi.org/10.1145/2939672.2939754
- [4] T. N. Kipf 和 M. Welling, "基于图卷积网络的半监督分类," arXiv, 2017.
- [5] X. Liu, H. Yang, Z. Liu, L. Song, H. Li, 和 Y. Chen, "DPatch: 针对对象探测器的对抗性攻击," arXiv, 2019.
- [6] W. Liu, D. Anguelov, D. Erhan, C. Szegedy, S. Reed, C.-Y. Fu, 和 A. C. Berg, "SSD: 单发多框探测器," 收录于计算机视觉 – ECCV 2016, B. Leibe, J. Matas, N. Sebe, 和 M. Welling, 编. Cham: Springer International Publishing, 2016, 第 21–37 页.
- [7] B. Perozzi, R. Al-Rfou, 和 S. Skiena, "DeepWalk: 社交表示的在线学习," 收录于第 20 届 ACM SIGKDD 知识发现与数据挖掘国际会议论文集, ser. KDD '14. New York, NY, USA: 计算机协会, 2014, 第 701–710 页. [在线]。可用: https://doi.org/10.1145/2623330.2623732
- [8] S. Ren, K. He, R. Girshick, 和 J. Sun, "更快 R-CNN: 面向带有区域提议网络的实时对象检测," 收录于神经信息处理系统进展 28, C. Cortes, N. D. Lawrence, D. D. Lee, M. Sugiyama, 和 R. Garnett, 编. Curran Associates, Inc., 2015, 第 91–99 页. [在线]。可用: http://papers.nips.cc/paper/5638-faster-r-cnn-towards-real-time-object-detection-with-region-proposal-networks.pdf
- [9] L. Song, F. Chen, S. R. Young, C. D. Schuman, G. Perdue, 和 T. E. Potok, "基于结合能量和时间数据的中微子-原子核相互作用事件顶点重建的深度学习," 收录于 ICASSP 2019 - 2019 年 IEEE 音频、语音和信号处理国际会议 (ICASSP), 2019, 第 3882–3886 页.
- [10] R. Miotto, F. Wang, S. Wang, X. Jiang, 和 J. T. Dudley, "面向医疗保健的深度学习: 回顾、机遇与挑战," Bioinformatics 简报, 第 19 卷, 第 6 期, 第 1236–1246 页, 05 2017. [在线]。可用: https://doi.org/10.1093/bib/bbx044
- [11] N. P. Jouppi, C. Young, N. Patil, D. Patterson, G. Agrawal, R. Bajwa, S. Bates, S. Bhatia, N. Boden, A. Borchers, R. Boyle, P. l Cantin, C. Chao, C. Clark, J. Coriell, M. Daley, M. Dau, J. Dean, B. Gelb, T. V. Ghaemmaghami, J. Gottipati, W. Gulland, R. Hagmann, C. R. Ho, D. Hogberg, J. Hu, R. Hundt, D. Hurt, J. Ibarz, A. Jaffey, A. Jaworski, A. Kaplan, H. Khaitan, D. Killebrew, A. Koch, N. Kumar, S. Lacy, J. Laudon, J. Law, D. Le, C. Leary, Z. Liu, K. Lucke, A. Lundin, G. MacKean, A. Maggiore, M. Mahony, K. Miller, R. Nagarajan, R. Narayanaswami, R. Ni, K. Nix, T. Norrie, M. Omernick, N. Penukonda, A. Phelps, J. Ross, M. Ross, A. Salek, E. Samadiani, C. Severn, G. Sizikov, M. Snelham, J. Souter, D. Steinberg, A. Swing, M. Tan, G. Thorson, B. Tian, H. Toma, E. Tuttle, V. Vasudevan, R. Walter, W. Wang, E. Wilcox, 和 D. H. Yoon, "张量处理单元的数据中心性能分析," 收录于第 44 届计算机体系结构国际研讨会论文集, ser. ISCA '17. New York, NY, USA: 计算机协会, 2017, 第 1–12 页. [在线]。可用: https://doi.org/10.1145/3079856.3080246
- [12] (2020) TensorFlow 研究云. [在线]。可用: https://www.tensorflow.org/tfrc
- [13] Google Cloud. (2020) Cloud TPU 系统架构. [在线]。可用: https://cloud.google.com/tpu/docs/system-architecture
- [14] TensorFlow. [在线]。可用: https://github.com/tensorflow/tensorflow
- [15] S. Lloyd, "PCM 中的最小平方量化," IEEE 信息论汇刊, 第 28 卷, 第 2 期, 第 129–137 页, 1982.
- [16] J. Macqueen, "多元观测的分类与分析方法," 多元观测, 第 17 页, 1967.
- [17] M. Ester, H.-P. Kriegel, J. Sander, 和 X. Xu, "在大型空间数据库中发现带噪声聚类的基于密度的算法," 收录于 KDD, 1996, 第 226–231 页. [在线]。可用: http://www.aaai.org/Library/KDD/1996/kdd96-037.php
- [18] E. Schubert, J. Sander, M. Ester, H. P. Kriegel, 和 X. Xu, "DBSCAN 再回顾, 再回顾: 为什么以及如何仍然应该使用 DBSCAN," ACM 事务数据库系统, 第 42 卷, 第 3 期, Jul. 2017. [在线]。可用: https://doi.org/10.1145/3068335
- [19] T. Sherwood, E. Perelman, G. Hamerly, 和 B. Calder, "自动表征大规模程序行为," 收录于第 10 届编程语言与操作系统架构支持国际会议论文集, ser. ASPLOS X. New York, NY, USA: 计算机协会, 2002, 第 4557 页. [在线]。可用: https://doi.org/10.1145/605397.605403
- [20] S. Wold, K. Esbensen, 和 P. Geladi, "主成分分析," 化学计量学与智能实验室系统, 第 2 卷, 第 1 期, 第 37–52 页, 1987, 地质学家与地球化学家多元统计研讨会论文集. [在线]。可用: http://www.sciencedirect.com/science/article/pii/0169743987800849
- [21] G. Hamerly, P. Elmeleegy, 和 B. Calder, "SimPoint 的多项式与 k-means 聚类比较," 收录于 2006 年 IEEE 系统与软件性能分析国际研讨会, 2006, 第 131–142 页.
- [22] E. Perelman, M. Polito, J. Bouguet, J. Sampson, B. Calder, 和 C. Dulong, "共享内存架构上并行应用程序中的阶段检测," 收录于第 20 届 IEEE 国际并行分布处理研讨会论文集, 2006, 第 10 页.
- [23] D. Pelleg 和 A. Moore, "X-means: 通过高效估计聚类数扩展 K-means," 收录于第 17 届机器学习国际会议论文集, 2000, 第 727734 页.
- [24] R. L. Thorndike, "谁属于这个家族?" Psychometrika, 第 18 卷, 第 4 期, 第 267–276 页, Dec 1953. [在线]。可用: https://doi.org/10.1007/BF02289263
- [25] Google Cloud. (2020) Compute Engine 文档机器类型. [在线]。可用: https://cloud.google.com/compute/docs/machine-types
- [26] TensorFlow. (2019) TensorFlow TPU 模型. [在线]。可用: https://github.com/tensorflow/tpu
- [27] I. Turc, M.-W. Chang, K. Lee, 和 K. Toutanova, "博览群书的学生学得更好: 关于预训练紧凑模型的重要性," arXiv, 2019.
- [28] A. Radford, L. Metz, 和 S. Chintala, "基于深度卷积生成对抗网络的无监督表示学习," arXiv, 2016.
- [29] A. W. Yu, D. Dohan, M.-T. Luong, R. Zhao, K. Chen, M. Norouzi, 和 Q. V. Le, "QANet: 结合本地卷积与全局自注意力的阅读理解," arXiv, 2018.
- [30] T.-Y. Lin, P. Goyal, R. Girshick, K. He, 和 P. Dollar, "面向密集对象检测的焦点损失," 收录于 IEEE 国际计算机视觉会议 (ICCV), Oct 2017.
- [31] K. He, X. Zhang, S. Ren, 和 J. Sun, "面向图像识别的深度残差学习," CoRR, vol. abs/1512.03385, 2015. [在线]。可用: http://arxiv.org/abs/1512.03385
- [32] TensorFlow. (2020) XLA: 面向机器学习的优化编译器. [在线]。可用: https://www.tensorflow.org/xla
- [33] M. Yan, L. Deng, X. Hu, L. Liang, Y. Feng, X. Ye, Z. Zhang, D. Fan, 和 Y. Xie, "FGYCNN: 具有混合架构的 GCN 加速器," 收录于 2020 年 IEEE 高性能计算机体系结构国际研讨会 (HPCA), 2020, 第 15–29 页.
- [34] T. F. Wenisoh, R. E. Wunderlich, B. Falsafi, 和 J. C. Hoe, "TurboSMARTS: 几分钟内的准确微架构模拟采样," 收录于 2005 年 ACM SIGMETRICS 计算机系统测量与建模国际会议论文集, ser. SIGMETRICS '05. New York, NY, USA: 计算机协会, 2005, 第 408409 页. [在线]。可用: https://doi.org/10.1145/1064212.1064278
- [35] Y. Wang, G.-Y. Wei, 和 D. Brooks, "深度学习硬件和软件平台分析的系统方法论," 收录于机器学习与系统论文集, I. Dhillon, D. Papailiopoulos, 和 V. Sze, 编, vol. 2, 2020, 第 30–43 页. [在线]。可用: https://proceedings.mlsys.org/paper/2020/file/2c0ad46de7f9759aa2a0c99fb67f10-Paper.pdf
- [36] J. Powers, K. Ovtcharov, M. Papamichael, T. Massengill, M. Liu, D. Lo, S. Alkalay, M. Haselman, L. Adams, M. Ghandi, S. Heil, P. Patel, A. Sapek, G. Weisz, L. Woods, S. Lanka, S. Reinhardt, A. M. Caulfield, E. S. Chung, 和 D. Burger, "面向实时 AI 的可配置云规模 DNN 处理器," 收录于 2018 年 ACM/IEEE 第 45 届计算机体系结构年际国际研讨会 (ISCA), 2018, pp.

