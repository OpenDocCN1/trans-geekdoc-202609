
| GXNOR-Net [27] | R | {-1,1} | 未报告 | | {-1,1} | R |

| TOT-Net [29] | R | {-1,1} | R | | 带 $\alpha$ 的 {-1,1} | R |

R 代表实值，$K$ 和 $\alpha$ 分别代表激活缩放因子和权重缩放因子。

## 二进制神经网络 109

## 表 5.3 提及方法的分类率

| 方法 | MNIST (LeNet-5) | CIFAR10 NIN | SVHN (VGG-7) | CIFAR100 AlexNet | Image+ ResNet-18 |

| :--- | :--- | :--- | :--- | :--- | :--- |

| 全精度 [13] | 99.48 | 92.88 89.67 | 97.68 | 64.32 | 57.2/80.2 | 69.3/89.2 |

| BinaryCount [19] | 90.05 | 91.73 NA | 97.85 | NA | 35.5/61 | NA |

| BWN [13] | 99.38 | 92.58 NA | 97.46 | NA | 56.8/79.4 | 60.8/83 |

| TWN [30] | 33.38 | 92.56 NA | NA | NA | 54.5/76.8 | 65.3/86.2 |

| BNN [20] | 98.60 | 88.85 NA | 97.47 | NA | 27.9/50.42 | NA |

| XNOR-Net [13] | 99.21 | 90.02 85.74 | 96.96 | 54.10 | 44.2/69.2 | 51.2/73.2 |

| TNN [26] | 99.33 | 87.89* NA | NA | 51.6 | NA | NA |

| TBN [28] | 99.38 | 90.85 NA | 97.27 | NA | 49.7/74.2 | 55.6/79.0 |

| GXNOR-Net [27] | 99.32 | 92.50 NA | 97.37 | 61.61, NA | 42.9/96.8 (20epoch) | NA |

+ 分别表示 top-1 和 top-5 准确率。

*TNN 使用了 [31] 提供的类 VGG架构。

## 5.3 BNN 优化技术

上一节引入了 BNN 和 TNN。这些方法主要关注的问题是减少计算和内存存储需求，使其适用于功耗和资源受限的设备。然而，准确率损失（在大数据集上）是这种方法的一个主要挑战。因此，许多工作尝试解决这一问题并减少准确率损失。在此，我们引入了该领域的两项主要创新。

[14] 中提出的方法是针对减少大型数据集 BNN 准确率损失的最受关注且有前景的方法之一。作者证明由于 BNN 固有属性，常用的训练方法并不适用于它们。相反，他们建议在保持高压缩率和高准确率的同时训练 BNN。

- **学习率**。通常，全精度 CNN 的学习率初始化为 0.01，这对于 BNN 是是不适当的。实际上，BNN 的许多权重经常变化，其符号变化比全精度 CNN 大几个数量级。他们探索并发现，对于较低的几率（如 0.0001），BNN 的符号相比其他 BNN 显著提高了准确率，特别是对于 ImageNet 数据集。

- **缩放因子**。如 5.2 节所述，XNOR-Net 在权重和激活上部署了缩放因子，以增强 BNN 的准确率。由于缩放因子计算是复杂的，[14] 提出了一种在没有缩放因子的情况下二值化权重和激活的方法。实际上，他们用 PRE 层替换 ReLU 层来消除缩放因子可能带来的准确率损失。因此，卷积层只能通过 XNOR-Post 执行。

- **正则化**。CNN 部署了正则化以获得模型泛化能力并防止过拟合。全精度 CNN 经常使用 L2 正则化来驱动权重趋零。在 BNN 中，将权重驱动至 +1 或 -1 以实现最小二值化误差是理想的。在 [16] 中，提出了一种适用于 BNN 的方法，使权重更接近 +1 和 -1。

- **多二值化**。BNN 仅考虑将 {-1,1} 值编码为 1 位值（0 和 1）。

## 112 深度学习硬件架构

YodaNN [34] 作为最早的架构原型之一，为二值权重（BWTs）提供了一种灵活、高能效且性能可扩展的加速器设计。在该加速器中，权重和激活分别为二进制和 12 位数。通过实现基于锁存的标准单元内存（latch-based standard cell memory），与 SRAM 相比提供了更高的能效和电压可扩展性，他们获得了每瓦特 61.2 万亿次操作能效。

在 [35] 中，提出了一种用于九层二值卷积神经网络（BCNN）的优化 FPGA 加速器。由于输入图像是定点型的，第一层的处理元素也是定点型的。该设计使用查找表（LUTs）代替 DSP8 切片来实现位运算，并使用位计数（bitcount）来累加 LUT 的输出。所提出的基于 FPGA 的架构在小批量尺寸下比 Titan X GPU 快 8 倍，效率高 75 倍。在大批量尺寸下，该架构实现了接近 Titan X GPU 的吞吐量和 9.5 倍的能效。

[17] 的作者为 BNN 提出了一种全可综合的超高效硬件加速器——XNOR 神经引擎（XNE）。它以 IP 核的形式设计，可以集成到微控制器中用于低功耗嵌入式设备。

注意，在所有 BNN 中，BN 层都部署在卷积层和全连接层之后。随后执行符号函数（sign function）。然而，硬件加速器通常将符号函数和归一化结合在一起以实现简单实现。

对于传统的 CNN，有一些用于自动 FPGA 实现的方法和工具。一个广为人知的例子是 DNNWe [36]，它能够基于 CNN 的 Caffe 模型生成用于 FPGA 的可综合代码和调度器软件代码。对于 BNN 也有类似的工具。第一个用于 BNN（无论是 CNN 或 MLP）的框架称为 FINN [37]，它通过部署一种灵活的异构流式架构来生成快速且灵活的 BNN FPGA 加速器。在 FINN 框架中，权重和激活均为二进制形式。ReNet [38] 引入了一种基于 FINN 的新框架，通过对激活值进行多级残差二值化克服了 BNN 的精度损失。二值化层数根据给定的精度阈值确定。ReNet 的探索表明，2 层和 3 层的二值化通常足以获得合理的精度。

## 5.5 结论

由于 CNN 在嵌入式和手持设备中的部署日益增加，具有二值化和三值化权重及激活值的神经网络模型近年来引起了广泛关注。这些方法用简单的位运算取代了大量的计算密集型 MAC 操作。此外，由于参数位宽较低，内存存储/带宽需求也被显著降低。在本章中，我们对适用于低功耗和资源受限嵌入式系统的先进 BNN 和 TNN 进行了综述。我们进一步回顾了一些旨在解决低精度神经网络主要挑战（即精度损失）的近期工作。随着目前的进展，BNN 和 TNN 正成为实现未来低功耗嵌入式系统的有前景的选择。

## 参考文献

- [1] K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 770–778, 2016.

- [2] A. Krizhevsky, I. Sutskever, and G. E. Hinton, “ImageNet classification with deep convolutional neural networks,” Advances in Neural Information Processing Systems, pp. 1097–1105, 2012.

- [3] R. Girshick, J. Donahue, T. Darrell, and J. Malik, “Rich feature hierarchies for accurate object detection and semantic segmentation,” in Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 580–587, 2014.

- [4] V. Sze, Y. H. Chen, T. J. Yang, and J. S. Emer, “Efficient processing of deep neural networks: a tutorial and survey,” Proceedings of the IEEE, vol. 105, no. 12, pp. 2295–2329, 2017.

- [5] S. Han, J. Pool, J. Tran, and W. J. Daly, “Dangling weights and connections for efficient neural networks,” Advances in Neural Information Processing Systems, pp. 1135–1143, 2015.

- [6] Y-H. Chen, J. Emer, and V. Sze, “Eyeriss: a spatial architecture for energy-efficient dataflow for convolutional neural networks,” ACM SIGARCH Computer Architecture News, Vol. 44, no. 3, pp. 367–379, 2016.

- [7] P. Gysel, J. Pimentel, M. Motamedi, and S. Ghiasi, “Ristretto: A framework for empirical study of resource-efficient inference in convolutional neural networks,” IEEE Transactions on Neural Networks and Learning Systems, vol. 29, pp. 1–6, 2018.

- [8] Y. Ma, N. Suda, Y. Cao, J-S. Seo, and S. Vrudula, “Scalable and modular-RTL compilation of convolutional neural networks to FPGA,” in 2016 26th International Conference on Field Programmable Logic (FPL), pp. 1–8, 2016.

- [9] T. Yang, G. Chen, and V. Sze, “Designing energy-efficient convolutional neural networks,” in 2017 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), pp. 6071–6079.

- [10] A. Howard, M. Zhu, B. Chen, “MobileNets: Efficient convolutional neural networks,” ArXiv:1704.4095, 2017.

- [11] C. Jin, H. Sun, and S. Kimura, “Regularization of networks using DeepConnect,” in 23rd Asia Pacific Design Automation Conference (Asia-DAC), pp. 190–195, 2018.

- [12] A. Zhou, A. Yao, and Y. Guo, “Incremental quantization for low-precision neural networks,” ArXiv:1702.0304, 2017.

- [13] H. Alemdar, V. Leroy, and F. Prost, “Ternary neural networks for resource-efficient applications,” in 2017 International Joint Conference on Neural Networks (IJCNN), pp. 2547–2554.

- [14] M. Rastegar, G. Pasandi, and M. David, “BinaryNet,” ArXiv:1807.0511, 2018.

- [15] X. Lin, G. Hua, and L. Wang, “Towards binary neural networks,” in Advances in Neural Information Processing Systems, pp. 345–357, 2017.

- [16] F. Conti, P. D., and S. Member, “How to train a binary neural network with high accuracy?” in AAAI Conference on Artificial Intelligence, pp. 2625–2631, 2017.

- [17] A. Bahou, G. Karunat, and L. Benini, “XNORBIN: a hardware accelerator for low-precision neural networks,” ArXiv:1807.0310, 2018.

- [18] A. Bahou, G. Karunat, and L. Benini, “XNORBIN: 95 TOP/s accelerator for binary networks,” in 2018 IEEE Symposium on Low-Power and High-Speed Chips (CHIPS), pp. 1–3.

- [19] M. Courbariaux and J. David, “BinaryConnect: training deep neural networks with binary weights during propagation,” Advances in Neural Information Processing Systems, pp. 3123–3131, 2015.

- [20] I. Hubara, “Binarized neural networks,” Advances in Neural Information Processing Systems, pp. 4107–4115, 2016.

- [21] Z. Lin, R. Misesev, and M. Courbariaux, “Neural networks with few multiplications,” in International Conference on Learning, pp. 1–9, 2017.

- [22] N. Srivastava, G. Hinton, A. Krizhevsky, I. Sutskever, and R. Salakhdut, “Dropout: a simple way to prevent neural networks from overfitting,” The Journal of Machine Learning Research, vol. 15, no. 1, 1929–1958, 2014.

- [23] L. Wan, M. Zeiler, S. Zhang, Y. LeCun, and R. Fergus, “Regularization of networks using DeepConnect,” in 30th International Conference on Machine Learning, no. 1, pp. 109–111, 2013.

- [25] D. P. Kingma and J. Ba, “Adam: a method for stochastic optimization.” ArXiv Preprint:1412.6980, 2014.

# 二值化神经网络 115

[27] L. Deng, P. Jiao, J. Pei, Z. Wu, and G. Li, “GXNOR-Net: training deep networks with ternary weights and activations under full-precision memory under a unified discretization framework.” Neural Networks, vol. 100, no. 4, pp. 49–58, 2018.

[28] D. Wan, F. Shen, L. Liu, et al., “TBN: convolutional neural network with ternary inputs and binary weights.” In Proceedings of the European Conference on Computer Vision (ECCV), pp. 315–332, 2018.

[29] N. Nazari, M. Moni, M. Salehi, M. Daneshtalab, and M. Sjödin. “TOT-Net: an endeavor toward optimizing ternary neural networks.” In 2019 Euroicro Conference on Digital System Design (DSD), IEEE, 2019.

[30] B. Liu, “Ternary weights.” ArXiv Preprint:1605.04711, 2016.
