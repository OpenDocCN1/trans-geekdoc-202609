
采用剪枝或 TP（阈值处理）会在分类的平均延迟和分类准确率之间产生权衡。剪枝策略减少了参数，TP 减少了平均 FLOP 数量。然而，根据结果（图 9.21 和 9.22），资源的增加并不总是能转化为更高的准确率。结合了剪枝和阈值化的混合策略表现出相同的行为，即更多的参数和 FLOPs 并不总是有助于提高分类准确率。因此，要在达到目标准确率的同时使用最少的资源（在此例中为执行时间）寻找最优策略，需要对阈值和剪枝参数进行彻底的探索和调整。

图 9.26 捕捉了 ICNN 在通过 5k 种阈值化和剪枝策略组合牺牲准确率以缩短运行时间时的设计空间。

![](img/e6e752b99eb1621488c89445a57e2a86_252_0.png)

图 9.26 在 K80 GPU 上，batch size 为 1 针对 50k 幅验证图像的迭代 AlexNet 的准确率与每幅图像平均运行时间的对比图。菱形标记了原始 AlexNet。图顶部的策略标记了在准确率和执行时间方面效率最高的策略。

## 228 深度学习的硬件架构

图中，每个点代表阈值化策略和剪枝策略的唯一组合。对于实时应用，等待整个批次（batch）处理会显著增加延迟 [39]，因此选择了 batch size 为 1 以针对实时流式应用。

如图所示，与独立的剪枝策略相比，独立的 TP 产生了更好的运行时间/准确率权衡。然而，它们在混合策略中的结合可能会导致最优解。图 9.26 中混合策略的几个优化点在相同准确率下显示出运行时间比独立的 TP 更短。例如，图 9.26 突出了一个独立的 TP 和一个通过将相同 TP 与剪枝结合得出的混合策略。图 9.26 显示，该混合策略在仅损失 1% 准确率的情况下，将分类时间缩短了 38%。

### 9.11.3.2 截止日期驱动

图 9.27 显示了在 K80 GPU 上，batch size 为 1 针对 50k 幅验证图像的迭代 AlexNet 在不同时间预算下（任何给定截止日的迭代相同）的 DD 策略总体率。与剪枝和/或 TP 不同，所有图像都会经过时间预算函数。需要注意的是，较高的时间预算只有在足够执行下次迭代时才会增加准确率，这在图中观察到了阶梯状的行为。

与阈值化和剪枝策略不同，DD 策略在给定时间预算下只执行一次的 FC 层。然而，剪枝和/或 TP 需要完成所有迭代的 FC 层以得出关于提前终止和类别标签的结论。结果，对于更高的准确率（即在混合/阈值/剪枝策略中使用高 $D_{ci}$ 和低 $S_{th}$ 值），DD 策略允许根据可用时间预算调整每幅图像的运行时间。

![](img/e6e752b99eb1621488c89445a57e2a86_253_0.png)

图 9.27 在 K80 GPU 上，batch size 为 1 针对 50k 幅验证图像的迭代 AlexNet 的 DD 总体准确率。菱形标记了原始 AlexNet。只有当时间预算足够执行下次迭代时，较高的时间预算才会增加准确率，因为 DD 策略跳过了前几次迭代的 FC 层。例如，在 1.7 ms 时间预算下，DD 策略的 top-5 准确率为 79%。

## 9 结论

在本章中，引入了一种用于处理 CNN 的迭代架构 (`ICNN`)。作为一个案例研究，`ICNN` 用于将大型 AlexNet 分为一系列较小的网络 (`uCNN`)，每个网络处理输入的一个样本，提供了提前终止的能力（当达到实时系统的截止日期或低功率系统的准确率时）或进入下次迭代的能力（如果未达到实时系统的截止日期或低功率系统的准确率）。为了探索这些权衡，引入了动态截止驱动策略和两种混合策略。我们的仿真结果显示，通过智能选择剪枝和 TP，`ICNN` 在 50K 幅验证图像上减少了超过 25%、80% 和 38% 的平均 FLOP 和参数数量，且准确率损失忽略不计。数量的减少直接转化为能量节省。此外，实时系统可以通过将 `ICNN` 的执行时间减少多达 2 倍来利用其动态结构。

## 参考文献

- [1] J. Deng, W. Dong, R. Socher, L.-J. Li, and L. Fei-Fei, “ImageNet: A large-scale hierarchical database,” in Computer Vision and Pattern Recognition, CVPR, 2009, pp. 248–255.

- [2] A. Miller, “The geometrical learning of binary neural networks,” Communications of the ACM, 38, no. 11, pp. 39–41, 1995.

- [3] A. Krizhevsky, I. Sutever, and E. Hinton, “ImageNet classification with deep convolutional networks,” in Advances in Neural Information Processing Systems, Curran Associates. 2012, pp. 1097–1110.

- [4] K. Simonyan and A. Zisserman, “Very deep convolutional networks for large-scale image recognition,” arXiv:1409.1556, 2014.

- [5] C. Szegedy, W. Liu, Y. Jia, et al., “Going deeper with convolutions,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2015, pp. 1–9.

- [6] K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2016, pp. 770–778.

- [7] M. D. Zeiler and R. Fergus, “Visualizing and understanding convolutional networks,” in European Conference on Computer Vision, Springer. 2014, pp. 818–833.

- [8] M. Liu, J. Shi, Z. Li, J. Zhu, and S. Liu, “Better analysis of deep convolutional networks,” IEEE Transactions on Visualization and Computer Graphics, vol. 23, no. 1, pp. 91–100.

- [9] Y. LeCun, B. Boser, S. Denker, et al., “Backpropagation applied to handwritten zip code recognition,” Neural Computation, vol. 1, no. 4, pp. 541–551.

- [10] Y-H. Chen, T. Krishna, J.S. Emer, and V. Se, “An energy-efficient reconfigurable accelerator for deep convolutional networks,” IEEE Journal of Solid-State Circuits, vol. 52, no. 1, pp. 127–138, 2017.

- [11] C. Zhang, P. Li, G. Sun, Y. Guan, B. Xiao, and J. Cong, “Optimizing FPGA-based accelerator design for convolutional neural networks,” in Proceedings of the 2015 ACM/SIGDA International Symposium on Field-Programmable Arrays, ACM, 2015, pp. 160–170.

- [12] M. Jaderberg, A. Vedaldi, and A. Zisserman, “Speeding up convolutional networks with low rank expansions,” arXiv:1405.3866, 2014.

- [13] V. Lebedev, Y. Ganin, M. Rakhuba, I. Oseled, and Y. Lempitsky, “Speeding-up convolutional networks using fine-tuned CP-decomposition,” arXiv:1412.6553, 2014.

- [14] B. Liu, M. Wang, H. Foroszcz, M. Tappen, and M. Pensky, “Sparse convolutional networks,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2015, pp. 806–814.

- [15] M. Rastegari, V. Ordone, J. Redmon, and A. Faradi, “XNOR-Net: ImageNet classification using binary convolutional networks,” in ECCV, Springer, 2016, pp. 525–542.

- [16] S. Yu, J. Li, P.-Y. Chen, et al., “Binary neural networks with 16 Mb RAM macro for classification and online training,” (IEDEM), 2016 IEEE International. IEEE, 2016, pp. 16–2.

# 迭代卷积神经网络

[20] J. Wu, C. Leng, Y. Wang, Q. Hu, and J. Cheng, “用于移动设备的量化卷积神经网络”，发表于 IEEE 视觉与模式识别会议集，2016，pp. 4820–4828。

[21] S. Zhou, Y. Wu, Z. Ni, X. Zhou, H. Wen, and Y. Zou, “DoReFa-Train: 具有位宽梯度的低比特卷积神经网络”，arXiv preprint arXiv:1606.06160, 2016.

[22] M. Courbaux, Y. Bengio, and J-P. David, “深度学习的低精度算术”，CORR, abs/1412.7024, vol. 4, 2014.

[23] S. Gupta, A. Agrawal, and P. Narayanan, “有限数值精度的深度学习”，发表于 ICML, 2015，pp. 1737–1746.

[24] D. D. Lin, S. Talati, and V. S. Annapureddy, “深度卷积神经网络的点量化”，发表于 ICML, 2016，pp. 2849–2858.

[25] H. Tamm, S. Hashemi, R. I. Hasheri, and S. Red, “用于能量-精度权衡的运行时配置神经网络”，发表于 IEEE 硬件/软件协同设计与系统论文国际会议 (CODES+)，2016，pp. 1–10.

[26] P. Panda, A. Sengupta, and K. Roy, “用于能量高效和增强模式识别的条件深度学习”，发表于欧洲设计、自动化与测试会议，2016. IEEE，pp. 475–480.

[27] S. Teerpartiyanan, B. Macandel, and K. Hung, “BranchNet: 通过从深度神经网络早期退出的神经网络”，发表于模式识别 (ICPR) 2016 第3届国际会议。IEEE, 2016，pp. 2464–2469.

[28] L. Deng. “用于机器学习研究的手写数字图像 MNIST 数据库 [网络精华]”，IEEE 信号处理杂志，vol. 29, no. 6, pp. 141–142, 2012.

[29] K. Neshatpur, F. Behnia, H. Homayoun, and A. Sasan, “CNN: 一种迭代的卷积神经网络实现，以实现能量和计算感知的动态近似”，发表于设计、自动化与测试会议，2018。

[30] K. Neshatpur, F. Behnia, H. Homayoun, and A. Sasan, “通过多阶段卷积神经网络中的上下文感知利用能量-精度权衡”，发表于 IPSED, 2019.

[31] C. S. Burrus, R. A. Gopinath, and H. Guo, 《小波与小波变换：导论》，1997。

[32] D. Neekhav and V. Denim, “使用反卷积优化方法对深度神经网络神经元最大化图像可视化”，Procedia Computer Science, vol. 119, pp. 174–181, 2017.

[33] M. D. Zeiler, G. W. Taylor, and R. Fergus, “用于中高级特征学习的自适应反卷积网络”，发表于 2011 IEEE 国际计算机视觉会议 (ICCV)。IEEE, 2011，pp. 2018–2025.

[34] W. Shi, J. Caballero, T. Weiss, 等, “反卷积层等于卷积层吗？”，arXiv preprint:1609.07009, 2016.

[35] J. Long, E. Shelhammer, and T. Darrell, “用于分割的全卷积网络”，发表于 IEEE 视觉与模式识别会议集，2015，pp. 3431–3440。

## 232 深度学习的硬件架构

- [36] A. Dosovitskiy, P. Fischer, E. Ilg, 等, “FlowNet: 使用卷积神经网络学习光流”，发表于 IEEE 国际计算机视觉会议集，2015，pp. 2758–2766.

- [37] A. Radford, L. Metz, and S. Chintala, “基于深度生成对抗网络的无监督表示学习”，arXiv preprint arXiv:1511.06434, 2015.

- [38] S. Anwar, K. Hwang, and W. Sung, “深度卷积神经网络的结构化剪枝”，计算系统系统工程技术期刊，vol. 13, no. 3, pp: 32–38, 2017. [在线].可用：http://doi.acm.org/10.1145/3005348

- [39] S. Han, H. Mao, and W. J. Daly. “深度压缩：使用训练过的量化和霍曼编码压缩深度神经网络”，arXiv preprint arXiv:1510.00149, 2015.

- [40] S. Han, X. Liu, H. Mao, 等, “EIE: 压缩深度神经网络上的高效推理引擎”，发表于第43届国际计算机体系体系会议。IEEE Press, 2016，pp. 243–254.

- [41] Y. Jia, E. Shelham, J. Donahue, 等, “Caffe: 用于快速特征嵌入的卷积架构”，发表于第22 届 ACM 国际多媒体会议。ACM, 2014，pp. 675–678.

- [42] S. Mallat, 《信号处理的小波之旅》。Burlington, MA: Academic Press, 1999.

- [43] H. Chu and Symas Corporation, “闪电内存映射数据库管理器 (LMDB)”,2011。http://104.237.133.194/doc/.

- [44] Pywavelets, https://pywavelets.org/stable/

- [45] S. Zha, Luisier, Srivastava, “Exploit,”arXiv:1503.0441, 2015.

生物医学（特别是心电图 ECG）信号处理面临的挑战。第10.3节介绍了所提的NeuRAM3混合信号神经形态平台，第10.4节介绍了在所提平台上的ECG应用映射。第10.5节讨论了实验结果，并在第10.6节中给出了结论。

## 10.2 相关工作

### 10.2.1 混合信号神经形态架构 – 简述

神经系统是一类特殊的分布式信息处理系统，其处理信息的方式与基于冯·诺依曼架构的现代计算机技术截然不同。神经生物系统利用数以亿计的缓慢、非均匀、有噪声且精度有限的元件（神经元和突触），尽管如此在语音处理、符号推理、运动控制和多感整合等许多任务中仍然优于计算机。近年来，人们对探索超越冯·诺依曼架构的替代计算技术产生了越来越兴趣。神经形态工程是一个活跃的研究领域，该领域在开发用于实际应用的人工系统的同时，应用生物系统的计算原理，利用硅互补金属氧化半导体（CMOS）技术或其他材料和基底的已知物理特性。在此背景下，已经提出了许多神经处理元件的模拟与数字实现的多种混合信号组合。这主要是因为计算部分的模拟特性符合低功耗需求，并与神经生物学对应物保持一致。

近期一些项目致力于开发用于大规模神经硬件仿真器的硬件平台。其目标是以最低的功耗模拟尽可能数量的神经元和突触。这种方法通过模拟尽可能数量的神经元和突触来实现。最近，脉冲神经网络架构（SNN）项目已实现了一种基于18nm的平台，能够以最低的功耗预算模拟大量数量的神经元和突触。这种脉冲神经元（LIF）在实时范围内模拟了大脑的部分。该系统包含可编程的脉冲神经元，在实时范围内实现了128个神经元核心。每个核心具有100KB的本地存储器，用于存储突触权重。这种能够模拟神经生物神经元的系统，其功耗与低功耗需求相符。
