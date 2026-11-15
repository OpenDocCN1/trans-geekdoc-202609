

![](img/5fa4874adaccc5ede04575a2e9e5662a_64_0.png)

图 3.10 基于输出迁移的知识蒸馏示意图 [27]。

负标签所携带的信息会被相对放大，因此模型训练会更加关注负标签。该改进函数称为 softmax-T 函数，形式为

$$q_i = \frac{\exp(z_i/T)}{\sum_j \exp(z_j/T)}.$$ (3.2)

基于预训练的教师模型 Net-T 和待训练的学生模型 Net-S，蒸馏过程如图 3.10 所示。

- 首先，将训练数据集同时以高温 \( T = t \) 输入到 Net-T 和 Net-S 中，Net-T 和 Net-S 的 softmax-T 函数输出构成交叉熵，作为损失函数的第一部分 \( \mathcal{L}_{\text{soft}} \)。
- 然后，将 Net-S 在常温 \( T = 1 \) 下的 softmax 函数输出作为损失函数的第二部分 \( \mathcal{L}_{\text{hard}} \)。
- 总损失函数 \( \mathcal{L} \) 由 \( \mathcal{L}_{\text{soft}} \) 和 \( \mathcal{L}_{\text{hard}} \) 组成，并以 \( \mathcal{L} \) 作为 Net-S 的损失函数来训练 Net-S。

Hinton 通过实验指出，知识蒸馏使学生模型能够获取教师模型的知识，从而提升小模型的效果。Hinton 等人提出的这一方法对后续知识蒸馏研究产生了深远影响，并且还提出了一些输出迁移的改进形式。例如，Ying Zhang 等人 [37] 提出了一种互助学习模型，使 Net-S 在训练过程中能够相互学习和指导。经典的蒸馏算法是一条单向通道，将知识从 Net-T 传递到 Net-S，而互助学习使

![](img/5fa4874adaccc5ede04575a2e9e5662a_65_0.png)

图 3.11 基于特征迁移的知识蒸馏示意图。

每个 Net-S 的损失函数由传统监督学习损失和模仿损失组成，并要求 Net-S 的预测概率保持一致。

基于输出迁移的知识蒸馏方法难以控制学生模型对中间细节特征的学习，并会导致训练不稳定。一种更直观的方法是对 Net-T 模型和 Net-S 模型的中间特征施加约束，以确保 Net-S 模型能够尽可能准确地继承 Net-T 的所有知识。这种蒸馏称为特征迁移。特征迁移并非直接将 softmax 的输出作为目标蒸馏到小模型，而是强调 Net-S 学习 Net-T 网络结构的中间层，即在中间特征层和输出端同时进行知识蒸馏，如图 3.11 所示。

输出迁移已考虑到 Net-S 的参数数量少于 Net-T，但对于层数更多且每层神经元更少的 Net-S（这种结构称为窄深网络），Hinton 的方法仍需扩展。因此，Romero 等人 [28] 提出了一种训练窄深网络的方法。通过引入 Net-T 隐藏层输出变量 Hints 来指导 Net-S 的学习过程，Net-S 的隐藏层可以学习 Net-T 隐藏层的预测输出。在这种蒸馏模式下的 Net-S 称为 FitNet。

整个训练过程分为两个阶段，如图 3.12 所示。Net-T 模型中间层的权重表示为 \( \mathbf{W}_H \)，表示指导，而 Net-S 模型中间层

![](img/5fa4874adaccc5ede04575a2e9e5662a_66_0.png)

图 3.12 FitNet 知识蒸馏示意图 [28]。

的权重表示为 \( \mathbf{W}_G \)，表示被指导。第一阶段是匹配中间层 \( \mathbf{W}_H \) 和 \( \mathbf{W}_G \) 的特征。由于两个特征的输出尺寸不同，使用映射函数 \( \mathbf{W}_r \) 实现尺寸匹配，然后通过最小化 \( \mathbf{W}_H \) 和 \( \mathbf{W}_G \) 之间的差异来实现中间层特征的知识蒸馏。在此阶段，FitNet 前 \( g \) 层的参数在 Net-T 前 \( h \) 层参数的指导下进行训练。第二阶段与上述输出迁移相同，通过训练得到 Net-S 所有层的参数 \( \mathbf{W}_S \) 和 \( \mathbf{W}_G \)。

实验结果表明，特征迁移方法能够提供更多的教师模型知识，并比输出迁移方法更好地提升学生模型的泛化能力。此外，FitNet 作为一种模型压缩算法，在速度和精度之间取得了出色的平衡，在参数减少 36 倍的条件下，模型性能仅下降 1.3%。然而，值得注意的是，基于提示的隐藏层特征映射实际上是一种正则化表示，因此设置的 \( \mathbf{W}_G \) 层数越深，FitNet 越容易受到过度正则化的影响。其他关于特征迁移的研究也从隐藏层入手，例如，将卷积神经网络隐藏层输出的特征图传递到 Net-S，并计算并降低 Net-T 和 Net-S 中特征图的差异 [40]。

## 参考文献

- [1] A. Krizhevsky, I. Sutskever, G.E. Hinton, 基于深度卷积神经网络的ImageNet图像分类, 《计算机协会通讯》 60 (2012) 84–90.
- [2] H. Yang, S. Gui, Y. Zhu, J. Liu, 基于稀疏-量化联合学习的自动神经网络压缩：一种约束优化方法, 载于: IEEE计算机视觉与模式识别会议论文集, 2020.
- [3] Y. Guo, H. Yuan, J. Tan, Z. Wang, S. Yang, J. Liu, GDP: 通过可微分极化门实现的稳定神经网络剪枝, 载于: 国际计算机视觉会议, 2021.
- [4] X. Ding, G. Ding, X. Zhou, Y. Guo, J. Han, J. Liu, 用于剪枝非常深神经网络的全局稀疏动量SGD, 神经信息处理系统 (2019).
- [5] J. Shen, H. Wang, S. Gui, J. Tan, Z. Wang, J. Liu, UMEC: 面向高效推荐系统的统一模型与嵌入式压缩, 载于: 国际学习表征会议, 2021.
- [6] H. Yang, Y. Zhu, J. Liu, ECC: 基于双线性回归模型的平台无关能量约束深度神经网络压缩, 载于: IEEE计算机视觉与模式识别会议论文集, 2019, pp. 11206–11215.
- [7] H. Wang, S. Gui, H. Yang, H. Yang, J. Liu, Z. Wang, GAN 瘦身：基于统一优化框架的全方位GAN压缩, 载于: 欧洲计算机视觉会议, Springer, Cham, 2020, pp. 54–73.
- [8] S. Gui, H. Wang, H. Yang, C. Yu, Z. Wang, J. Liu, 兼具对抗鲁棒性的模型压缩：统一优化框架, 神经信息处理系统进展 (2019) 1285–1296.
- [9] M. Denil, B. Shakibi, L. Dinh, M. Ranzato, N.D. Freitas, 深度学习中的参数预测, 载于: 国际神经信息处理系统会议论文集, 2013.
- [10] K. He, X. Zhang, S. Ren, J. Sun, 面向图像识别的深度残差学习, 载于: IEEE计算机视觉与模式识别会议论文集, 2016.
- [11] F.N. Iandola, M. Moskewicz, K. Ashraf, S. Han, W. Dally, K. Keutzer, SqueezeNet: 参数减少50倍且模型大小小于1MB的AlexNet级精度, arXiv: 1602.07360 [abs].
- [12] A.G. Howard, M. Zhu, B. Chen, D. Kalenichenko, W. Wang, T. Weyand, M. Andreetto, H. Adam, MobileNets: 面向移动视觉应用的高效卷积神经网络, arXiv:1704.04861 [abs].
- [13] C. Szegedy, W. Liu, Y. Jia, P. Sermanet, S.E. Reed, D. Anguelov, D. Erhan, V. Vanhoucke, A. Rabinovich, 卷积网络更深, 载于: IEEE计算机视觉与模式识别会议论文集, 2015.
- [14] K. Simonyan, A. Zisserman, 面向大规模图像识别的非常深层卷积网络, arXiv:1409.1556 [abs].
- [15] M. Sandler, A.G. Howard, M. Zhu, A. Zhmoginov, L.-C. Chen, MobileNetV2: 倒残差与线性瓶颈, 载于: IEEE计算机视觉与模式识别会议论文集, 2018.
- [16] X. Zhang, X. Zhou, M. Lin, J. Sun, ShuffleNet: 面向移动设备的极高效卷积神经网络, 载于: IEEE计算机视觉与模式识别会议论文集, 2018.
- [17] M. Tan, Q. Le, EfficientNet: 重新思考卷积神经网络的模型缩放, 载于: 国际机器学习会议论文集, 2019.
- [18] Q.V. Tan, Mingxing and Le, EfficientNetV2: 更小的模型和更快的训练, arXiv: 2104.00298 [abs].
- [19] D. Singh, V. Kumar, M. Kaur, 基于密连卷积网络的COVID-19筛查模型, 应用智能 (2021) 1–8.
- [20] B. Zoph, V. Vasudevan, J. Shlens, Q.V. Le, 面向可扩展图像识别的可迁移架构学习, 载于: IEEE计算机视觉与模式识别会议论文集, 2018.

