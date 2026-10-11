

# U-Net

U-Net `[21]` 主要用于语义分割。该网络启发了用于各种其他图像处理任务的多个网络，如生物医学图像分割、稠密体积分割和图像到图像转换。该模型由收缩/编码路径（左侧）和扩展/解码路径（右侧）组成，如 [图 9.35](#c09.xhtml#fig9_35) 所示。

收缩路径遵循卷积网络的典型架构。它由两个 `3x3` 卷积（无填充卷积）的重复应用组成，每个卷积后跟一个 ReLU 激活函数和一个步长为 2 的 `2x2` 最大池化操作，用于下采样。在每个下采样步骤中，特征通道的数量翻倍。

扩展路径中的每一步都包含特征图的上采样，随后是一个将特征通道数量减半的 `2x2` 卷积，与收缩路径中相应裁剪的特征图进行拼接（图中的虚线框），以及两个 `3x3` 卷积，每个卷积后跟一个 ReLU。裁剪（图中的虚线框）是必要的，因为每次卷积都会导致边界像素的丢失。在最后一层，使用 `1x1` 卷积将每个 64 分量的特征向量映射到所需的类别数量。请参阅下图（来源 `[21]`）：

![](images/Image46358.jpg)

**图 9.35：** *U-Net 架构，蓝色框代表多通道特征图，框顶部标注通道数，左侧标注空间维度，白色框代表复制的特征图*

## 能量函数

能量函数通过最终特征图上的逐像素 soft-max 与交叉熵损失函数相结合来计算。Soft-max 定义如下：

![](images/2415.jpg)

其中 ![](images/2416.jpg) 是近似最大值函数，![](images/2417.jpg) 表示像素位置 ![](images/2418.jpg) 处特征通道 `k` 的激活值，其中 ![](images/2419.jpg)。对于具有最大激活值 ![](images/2421.jpg) 的 `k`，![](images/2420.jpg)；对于所有其他 `k`，![](images/2422.jpg)。然后交叉熵使用以下公式惩罚每个位置处 ![](images/2423.jpg) 的偏差：

![](images/2424.jpg)

其中 ![](images/2425.jpg) 是每个像素的真实标签，![](images/2426.jpg) 是引入的权重图，用于在训练中赋予某些像素更高的重要性。

# 总结

在本章中，我们讨论了使用卷积应用滤波器处理图像的算法，以及各类滤波器及其示例。接下来，我们讨论了同时使用 DNN 和卷积操作的架构，称为 CNN，这帮助我们根据给定任务自动学习滤波器。我们详细讨论了 CNN 的发展历程及一些模型，以及一些应用。在下一章 [第 10 章 序列学习模型](#c10.xhtml) 中，我们将学习如何从序列数据中学习。

# 延伸阅读

图像处理研究的当前趋势最终已演变为对各种 CNN 架构的调查和实验。本章提到的模型不足以了解 CNN 模型的全貌，但能为理解其他模型提供基础。要了解 CNN 模型的全貌，可以阅读像 `[24]` 和 `[25]` 这样的综述论文。仅举一例，论文 `[25]` 绘制了流行 CNN 模型的图表，包含可学习参数和一次推理所需的操作，如 [图 9.36](#c09.xhtml#fig9_36) 所示：

![](images/Image46365.jpg)

**图 9.36：** *报告 Top-1 准确率与计算复杂度的气泡图，气泡大小代表模型的可训练参数量（来源：[25]）*

# 重点回顾

*   图像维度较大，因此分类等任务无法直接应用。在执行任务前，需要从图像中提取特征。
*   最初，通过使用滤波器从图像中提取特征。这些滤波器根据所需任务手工开发。为所需任务识别滤波器的工作非常困难。
*   CNN 模型根据给定任务学习滤波器。这些模型在图像任务上取得了成功。

# 参考文献

1.  *Digital Image Processing*，第 4 版，作者 *Rafael C Gonzalez, Richard E Woods*。
2.  *Deep Learning*，作者 *Ian Goodfellow, Yoshua Bengio, Aaron Courville*。
3.  Y. Lecun, L. Bottou, Y. Bengio and P. Haffner, "Gradient-based learning applied to document recognition," in *Proceedings of the IEEE*, Nov. 1998。通俗称为 *LeNet*。
4.  Krizhevsky, Alex and Sutskever, Ilya and Hinton, Geoffrey E, "ImageNet Classification with Deep Convolutional Neural Networks" in *Proceedings of the NIPS 2012*, vol. 25。通俗称为 *AlexNet*。
5.  C. Szegedy et al., "Going deeper with convolutions," *IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, 2015。通俗称为 *Inception V1* 或 *GoogLeNet*。
6.  S. Liu and W. Deng, "Very deep convolutional neural network based image classification using small training sample size," *3rd IAPR Asian Conference on Pattern Recognition (ACPR)*, 2015。通俗称为 *VGGNet*。
7.  He, K., Zhang, X., Ren, S. and Sun, J., 2016. Deep residual learning for image recognition. In *Proceedings of the IEEE conference on computer vision and pattern recognition*。通俗称为 *ResNet*。
8.  Chollet, F., 2017. Xception: Deep learning with depthwise separable convolutions. In *Proceedings of the IEEE conference on computer vision and pattern recognition*。通俗称为 *Xception* 模型。
9.  Hebb 学习规则规定了两个单元之间连接权重应按其激活值的乘积成比例增加或减少的程度。该规则建立在 Hebb 1949 年的学习规则之上，该规则指出，如果两个神经元同时放电，它们之间的连接可能会加强。
10. Szegedy, C., Vanhoucke, V., Ioffe, S., Shlens, J. and Wojna, Z., 2016. Rethinking the inception architecture for computer vision. In *Proceedings of the IEEE conference on computer vision and pattern recognition*。通俗称为 *Inception V3*。
11. Andrew, G. and Menglong, Z., 2017. Efficient convolutional neural networks for mobile vision applications。通俗称为 *MobileNets*。
12. Q. Li, W. Cai, X. Wang, Y. Zhou, D. D. Feng and M. Chen, "Medical image classification with convolutional neural network," *2014 13th International Conference on Control Automation Robotics & Vision (ICARCV)*, 2014。
13. Jiang, Y., Chen, L., Zhang, H. and Xiao, X., 2019. Breast cancer histopathological image classification using convolutional neural networks with small SE-ResNet module. *PloS one*, 14(3), p.e0214587。
14. Iandola, F., Moskewicz, M., Karayev, S., Girshick, R., Darrell, T. and Keutzer, K., 2014. Densenet: Implementing efficient convnet descriptor pyramids。通俗称为 *DenseNet*。
15. Redmon, J., Divvala, S., Girshick, R. and Farhadi, A., 2016. You only look once: Unified, real-time object detection. In *Proceedings of the IEEE conference on computer vision and pattern recognition*。通俗称为 *YOLO*。
16. Girshick, R., Donahue, J., Darrell, T. and Malik, J., 2014. Rich feature hierarchies for accurate object detection and semantic segmentation. In *Proceedings of the IEEE conference on computer vision and pattern recognition*。
17. Girshick, R., 2015. Fast r-cnn. In *Proceedings of the IEEE international conference on computer vision*。
18. Ren, S., He, K., Girshick, R. and Sun, J., 2015. Faster r-cnn: Towards real-time object detection with region proposal networks. *Advances in neural information processing systems*。
19. He, K., Gkioxari, G., Dollár, P. and Girshick, R., 2017. Mask r-cnn. In *Proceedings of the IEEE international conference on computer vision*。

