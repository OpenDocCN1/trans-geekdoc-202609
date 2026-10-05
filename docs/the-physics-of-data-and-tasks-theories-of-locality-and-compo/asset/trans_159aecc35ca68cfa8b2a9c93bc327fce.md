

[Wu+22] Yixin Wu, Ning Yu, Zheng Li, Michael Backes, and Yang Zhang. “针对文本到图像生成模型的成员推理攻击。” In: arXiv preprint arXiv:2210.00968 (2022).

[Xia+16] Jianxiao Xiao, Krista Ehinger, James Hayes, Antonio Torralba, and Aude Liu. “Sun数据库：探索大规模场景类别集合。” In: 国际计算机视觉杂志 (2016).

[Xia22] Lechao Liao. “特征空间重构：神经网络中空间与频率的原理。” In: 学习理论会议. PMLR, 2022, pp. 4888–4944.

[XP22] Lechao Liao and Jeffrey Pennington. “深度学习中的协同与对称性：数据、模型与推理算法之间的相互作用。” In: 第39届国际机器学习会议论文。Vol. 162. 2022, pp. 24347–24369.

[Xie+21] Jiahao Xie, Xia Zhan, Ziwei Liu, Wei Soon Ong, and Chen Change Loy. “来自场景图像的无监督物体级表示。” In: 神经信息处理系统进展 33 (2021), pp. 28864–28876.

[YO86] Victor Yahord and Steven A Orsag. “湍流的重正化群分析。I. 基础。” In: 科学计算杂志 1.1 (1986), pp. 3–51.

[YH20] Greg Yang and Edward J Hu. “无限宽度神经网络中的特征学习。” In: arXiv preprint arXiv:2011.14522 (2020).

[Yoo+23] TaeH Yoon, Joo Young Choi, Sehyun Kwon, and Ernest K Ryu. “扩散概率模型在未能实现记忆化时何能具有泛化能力。” In: ICML 2023 概率推理与生成模型建模工作坊。2023.

[Yua+23] Hui Yuan, Kaixuan Huang, Zhengchu Ni, Minshu Chen, and Mengdi Wang. “奖励引导的条件扩散与可证明的分布改进。” In: arXiv preprint arXiv:2307.07053 (2023).

[Yuc+22] Gizem Yuce, Guillermo Ortiz-Jimenez, Beril Besinar, and Pascal Fross. “隐式神经表示的结构化字典视角。” In: IEEE 计算机视觉与模式识别会议。2022.

[Zen+20] Luca Zancato, Alessandro Achille, Avinash Ravichandran, Rahul Bhotika, and Stefano Soatto. “无需训练预测训练时间。” In: 神经信息处理系统进展。2020.

[ZF14] Matthew D. Zeiler and Rob Fergus. “卷积网络的视化与理解。” In: 计算机视觉–ECCV 2014. 计算机科学讲义。2014, pp. 818–833.

[Zha+17] Chiyuan Zhang, Samy Bengio, Moritz Hardt, Benjamin Recht, and Oriol Ylin. “理解深度学习需要重新思考。” In: 第55届国际表示学习会议 (2017).

[Zha+23] Huijie Zhang, Jinfan Zhou, Yifu Lu, Minze Guo, Peng Wang, Lylie Shen, and Qing Qu. “扩散模型中可复现性与泛化性的出现。” In: arXiv preprint arXiv:2310.05264 (2023).

[ZM20] Xiao Zhang and Michael Maire. “基于分层聚类的自监督表示学习。” In: 神经信息处理系统进展 33 (2020), pp. 16579–16590.

[ZXS18] H. H. Zhou, Y. Xiong, and V. Singh. “基于块构建贝叶斯神经网络：关于结构、可解释性和不确定性。” In: arXiv preprint, arXiv:1806.03563 (2018).

[ZM+07] Song-Chun Zhu, David Mumford, 等. “图像的随机语法。” In: 计算机图形与视觉基础与趋势 2.4 (2007), pp 259–362.

[Zhu+20] Fuzhen Zhuang, Zhiyuan Qi, Key Duan, Dongbo Xi, Yongchun Zhu, Hengshu Zhu, Hui Xiong, and Qing He. “迁移学习的综述。” In: IEEE 学报 (2020).

[mc16] TorchVision 维护者与贡献者。TorchVision: PyTorch 的计算机视觉库。https://github.com/pytorch/vision. 2016.

# 术语表

激活函数 (ACTIVATION FUNCTION) 应用于神经网络神经元输出的非线性函数，例如 ReLU ($\sigma(u)$ = max(0,u))。它允许网络学习数据中复杂的非线性模式。

算术（任务）(ARITHMETIC (TASK)) 参见 *算术。*

反向传播 (BACKPROPAGATION) 一用于训练神经网络的算法，通过高效计算损失函数对权重的梯度来实现。它通过跨网络层递归应用链式法则工作。

贝叶斯 (BAYES) 指一种统计方法或预测器，能够在给定问题和数据分布下达到最低错误率。在论文背景下，它通常代表理论上的最优性能，作为与其他方法比较的基准。

信念传播 (BELIEF PROPAGATION (BP)) 一种用于对图模型执行推理的消息传递算法。在此处，它用于精确计算随机分层模型 (RHM) 的贝叶斯最优去噪过程，揭示了潜变量在扩散过程中的演化。

组合性 (COMPOSITIONALITY) 一项原则，认为复杂数据或特征是由更简单、可重用的部分构建的，或者通常以分层的方式。例如，图像由物体组成，物体由部分、纹理和边缘组成。本文认为组合性是数据中的一种关键结构，深度学习模型利用该结构来实现有效的泛化。

卷积神经网络 (CONVOLUTIONAL NEURAL NETWORK (CNN)) 一类主要为结构化数据（如图像）设计的深度网络。CNN 使用卷积滤波器捕捉局部模式并通过权重共享实现平移不变性。

维度灾难 (CURSE OF DIMENSIONALITY) 一种现象，随着数据维度（特征）的增加，达到特定置信度所需的数据量指数级增长。这使得在没有强底层结构的情况下，从高维数据中学习是不可行的。

深度学习 (DEEP LEARNING) 基于多层架构的人工神经网络的机器学习子领域。这些模型学习数据的分层表示，能够处理图像识别自然语言处理等复杂任务。

扩散模型 (DIFFUSION MODELS) 一类受非平衡统计物理启发的生成模型，通过反转去噪过程来创建数据。它们从纯噪声开始，随着时间迭代去噪，以从学习到的分布中生成样本。

特征学习 (FEATURE LEARNING) 神经网络中的一种学习模式，模型参数（权重）在训练期间发生显著变化。这允许网络使其内部表示（特征）适应训练数据的结构，与之相对的是“惰性”或内核模式，其中特征保持基本不变。

全连接神经网络 (FULLY CONNECTED NEURAL NETWORK (FCN)) 一种基础神经网络架构，给定层中的每个神经元与之前和之后层的所有神经元都连接。FCN 是通用函数近似器，但没有内置局部性等先验。

泛化 (GENERALIZATION) 模型在有限数据集上训练后，在未见新数据上准确执行的能力。良好的泛化意味着模型学习了数据分布的底层模式，而不仅仅是记忆训练示例。

泛化误差 (GENERALIZATION ERROR) 衡量训练模型的预测结果与来自同一分布的未见数据真实结果之间的匹配程度。从形式上讲，它是损失函数在整个数据分布上的期望值。

内核 (KERNEL) 在机器学习中是指一种衡量数据对之间相似性的函数。内核允许在高维特征空间中操作，而无需显式计算数据在空间中的坐标。

内核方法 (KERNEL METHODS) 一类学习算法，例如支持向量机或核岭回归，使用内核函数来学习预测器。在无限宽度限制下，某些神经网络等同于内核方法。

核岭回归 (KERNEL RIDGE REGRESSION) 一种回归算法，通过通过最小化训练数据上的平方误差和函数在再生内核希尔伯特空间 (RKHS) 中的范数来学习函数。

