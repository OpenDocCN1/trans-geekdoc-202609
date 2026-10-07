

# 迭代卷积神经网络 227

少于 5。在第二种情况下，继续下一次迭代不会提高顶部准确率（top-accuracy），ICNN 将终止，此时达到置信度阈值。

这种提前终止的影响是双重的：一方面，它识别出那些永远无法达到高分类置信度的图像，对这些图像进行更多迭代处理是浪费资源，在不提高准确率的情况下增加了计算。

另一方面，它过早地终止了在后续迭代中可能达到高置信度的图像处理，对准确率产生了负面影响。因此，选择 $D_{ci}$ 和 $S_{it}$ 的最佳组合是一个优化问题。

图 9.25 显示，当每次迭代的 $S_{it}$ 值选取为略高于下次迭代的 $D_{ci}$ 时，FLOP 和参数数量的减少对准确率的影响最小（参见 T4-P5 混合策略）。

此外，图 9.24 中提到的激进剪枝和阈值化对参数和 FLOP 数量的反向影响在图 9.25 中也被观察到（见两图中的红色条形）。

## 9.11.3 运行时间与总体准确率

### 9.11.3.1 剪枝和/或阈值化

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

在本章中，引入了一种用于处理 CNN 的迭代架构 (ICNN)。作为一个案例研究，ICNN 用于将大型 AlexNet 分为一系列较小的网络 (uCNN)，每个网络处理输入的一个样本，提供了提前终止的能力（当达到实时系统的截止日期或低功率系统的准确率时）或进入下次迭代的能力（如果未达到实时系统的截止日期或低功率系统的准确率）。为了探索这些权衡，引入了动态截止驱动策略和两种混合策略。我们的仿真结果显示，通过智能选择剪枝和 TP，ICNN 在 50K 幅验证图像上减少了超过 25%、80% 和 38% 的平均 FLOP 和参数数量，且准确率损失忽略不计。数量的减少直接转化为能量节省。此外，实时系统可以通过将 ICNN 的执行时间减少多达 2 倍来利用其动态结构。

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

