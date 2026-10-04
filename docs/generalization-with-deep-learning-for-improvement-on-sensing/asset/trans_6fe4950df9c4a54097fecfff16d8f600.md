

[47](#chap8.xhtml#fs47).C. Li, *et al*., “光学遥感图像显著目标检测的双流金字塔嵌套网络,” *IEEE Trans. Geosci. Remote Sens*., vol. 57, pp.9156–9166, 2019.

[48](#chap8.xhtml#fs48).A. Krizhevsky, I. Sutskever, and G. Hinton, “使用深度卷积神经网络的ImageNet分类,” *Neural Inform. Process. Syst*., vol. 25, 2012.

[49](#chap8.xhtml#fs49).C. Szegedy *et al*., “重新思考计算机视觉的Inception架构,” *IEEE CVPR*, 2015.

[50](#chap8.xhtml#fs50).C. Szegedy *et al*., “Inception-v4、Inception-ResNet以及残差连接对学习的影响,” in *AAAI Conference on Artificial Intelligence*, 2016.

[51](#chap8.xhtml#fs51).S. Ioffe and C. Szegedy, “批归一化：通过减少内部协变量偏移加速深度网络训练,” *CoRR*, vol. 1511, pp. 448–456, 2015.

[52](#chap8.xhtml#fs52).D. Kingma and J. Ba, “Adam：一种随机优化方法,” *CoRR*, vol. 1412, 2014.

[53](#chap8.xhtml#fs53).A. G. Howard *et al*., “MobileNets：用于移动视觉应用的高效卷积神经网络,” *CoRR*, vol. 1704, 2017.

[54](#chap8.xhtml#fs54).L. Smith and N. Topin, “深度卷积神经网络设计模式,” *CoRR*, 2016.

[55](#chap8.xhtml#fs55).C. Szegedy *et al*., “通过卷积更深地学习,” in *IEEE Conf. Computer Vision and Pattern Recognition*, pp. 1–9, 2015.

[56](#chap8.xhtml#fs56).K. He *et al*., “图像识别的深度残差学习,” in *IEEE Conference on Computer Vision and Pattern Recognition*, pp. 770–778, 2016.

[57](#chap8.xhtml#fs57).J. Long, E. Shelhamer, and T. Darrell, “语义分割的全卷积网络,” in *Proc. IEEE Conf. Computer Vision and Pattern Recognition(CVPR)*, Boston, MA, USA, pp. 3431–3440, 2015.

[58](#chap8.xhtml#fs58).K. He *et al*., “Mask R-CNN,” in *Proc. Int. Conf. Computer Vision (ICCV)*, Venice, Italy, pp. 2980–2988, 2017.

[59](#chap8.xhtml#fs59).R. Achanta *et al*., “与最先进超像素方法的SLIC超像素比较,” *IEEE Trans. Pattern Anal. Mach. Intell*., vol. 34, no. 11, pp. 2274–2282, 2012.

[60](#chap8.xhtml#fs60).J. W. Rouse *et al*., “利用ERTS监测大平原的植被系统,” in *3rd Earth Resource Technology Satellite*, vol. 1, pp. 48–62, 1974.

[61](#chap8.xhtml#fs61).A. R. Huete, “一种土壤调节植被指数（SAVI）,” *Remote Sens. Environ*., 25, pp. 295–309, 1988.

[62](#chap8.xhtml#fs62).P. Qin and J. Chen, “基于ASTER影像的NDVI与SAVI在植被空间信息提取中的比较：以广州花都区为例,” *Trop. Geograp*., vol. 28, no. 5, 2008.

[63](#chap8.xhtml#fs63).Kovács and T. Szirányi, “用于航空图像中方位敏感城市区域检测的改进Harris特征点集,” *IEEE Geosci Remote Sens Lett*., vol. 10, pp. 796–800, 2013.

[64](#chap8.xhtml#fs64).Q. Liu *et al*., “基于贝叶斯显著性模型的建筑区检测,” *Int. J. Wavelets Multiresolut. Inf. Process*., vol. 15, pp. 1–16, 2017.

[65](#chap8.xhtml#fs65).L. Yang, J. Yuan, and D. Lunga, “利用航空图像的卷积神经网络实现国家尺度建筑检测,” in *IEEE Int. Geoscience and Remote Sensing Symp*., 2017, pp. 870–873.

[66](#chap8.xhtml#fs66).D. A. Clevert, T. Unterthiner, and S. Hochreiter, “指数线性单元（ELUs）实现快速而精确的深度网络学习,” *Comput. Sci*., vol. 1511, 2015.

© 2021 World Scientific Publishing Company

[https://doi.org/10.1142/9789811218842_0009](https://doi.org/10.1142/9789811218842_0009)

## Chapter 9

## 遥感图像识别中基于流形的图卷积网络最新进展

Sichao Fu and Weifeng Liu[*](#chap9.xhtml#fn1)

*中国石油大学（华东）控制科学与工程学院，青岛，中国*[*](#chap9.xhtml#fnr1)

[liuwf@upc.edu.cn](mailto:liuwf@upc.edu.cn)

### Abstract

**摘要**

由于遥感图像包含的信息多样且空间结构复杂，图表示学习（GRL）因其能够学习更具代表性的数据特征而受到广泛关注。作为最具代表性的工作之一，图神经网络（GNNs）能够充分利用具有任意结构的数据的高阶相关信息，在仅有少量标记数据的情况下提高其学习性能。近年来，出现了越来越多的GNN模型，包括基于空间域的GNN和基于谱域的GNN，并在许多领域取得了优异的性能。更典型的模型图卷积网络（GCNs）首先将卷积神经网络（CNNs）在欧几里得空间上的卷积操作推广到图上。GCN通过谱图拉普拉斯卷积的一阶近似融合原始特征信息和节点之间复杂且高阶的数据相关关系，以学习更丰富的数据特征。然而，如何更好地保留和获取图结构数据的局部性和相似性关系一直是一个具有挑战性的任务。在本章中，我们总结了现有GNN的许多应用。在GCN与流形假设结合的框架下，提出了许多GCN变体，以在探索和利用数据流形的局部几何结构时精确获取图结构数据的空间结构信息。特别地，我们详细介绍了其理论分析以及GCN变体的一些应用，如二阶GCN、超图p-拉普拉斯GCN和流形正则化动态GCN。

**关键词：**图表示学习，图神经网络，谱域，空间域，图卷积网络

### 1. Introduction

**1. 引言**

随着卫星遥感技术和传感器技术的快速发展，具有不同分辨率的大量遥感图像可以轻松获得。遥感图像已成为相关部门和机构监测地面信息的主要方法之一。同时，所获取的数据在规模和复杂性方面都大幅增加。如何从这些海量高维数据中提取最有价值的信息，是机器学习和计算机视觉领域许多研究人员面临的最常见挑战之一[[1](#chap9.xhtml#fsr1), [2](#chap9.xhtml#fsr2)]。

近年来，许多流行的工作，如卷积神经网络（CNNs）[[3](#chap9.xhtml#fsr3)]、主成分分析网络（PCANet）[[4](#chap9.xhtml#fsr4)]、典型相关分析网络（CCANet）[[5](#chap9.xhtml#fsr5)]和自动编码器[[6](#chap9.xhtml#fsr6)]，已被提出并广泛应用于许多任务，从自然语言处理[[7](#chap9.xhtml#fsr7)]和图像[[8](#chap9.xhtml#fsr8)]到音频[[9](#chap9.xhtml#fsr9)]和视频[[10](#chap9.xhtml#fsr10)]。这些现有方法可以高效处理定义在欧几里得空间或规则网格上的数据。将这些模型应用于具有任意空间结构的图，如遥感图像，仍然是一个具有挑战性的任务。对于定义在非欧几里得域上的图结构数据，图的每个节点具有不同数量的邻居节点。此外，随着空间位置的变化，其高阶数据相关信息也会发生变化。因此，如何有效地、高效地分析和解释遥感图像的内容至关重要。

