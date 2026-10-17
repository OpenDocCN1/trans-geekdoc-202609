
# 步态识别研究

## 概述

一般来说，步态识别指的是行人识别（Sarkar et al., 2005; Shiraga et al., 2016），它利用从行人轮廓图中提取的特征来识别人员（Lam et al., 2011; Murase & Sakai, 1996; Wang et al., 2004）。近年来，随着深度学习的发展，例如 `Mask Region-Based Convolutional Neural Network (Mask-RCNN)`，将步态识别应用于实际复杂场景成为可能（He et al., 2017; Lee & Grimson, 2002）。

不同于直接将步态轮廓作为输入送入深度神经网络，Shiraga 采用 `Gait Energy Images (GEI)` 作为输入特征（Tao & Maybank, 2007）。`GEI` 是一种步态模型，包含一序列混合步态轮廓中的静态和动态信息。模型中每个像素的能量是通过计算一个步态周期内轮廓像素的平均强度获得的。

`LBP` 基于灰度图像像素的值。`HOG` 主要利用像素的梯度大小和方向（Dalal & Triggs, 2005）。因此，经过第一轮操作后，仍然存在具有灰度强度变化的图像。为了从灰度图像中获取丰富且有用的纹理信息和边缘形状信息，可以生成分层 `LBP` 和 `HOG`（见图 2）。

如图 2 所示，所有图像都包含用于后续处理的有用信息。图 2(b) 清楚地表达了强烈的纹理信息和轮廓信息。图 2(e) 明显指示了人体步态的边缘信息。图 2(c) 和图 2(f) 比图 2(b) 和图 2(e) 较弱，但仍有可利用的有用信息。因此，分层结构显然能提供更多信息。

提取步态特征的传统步态识别算法相对简单（Niyogi & Adelson, 1994）。此外，由于遮挡、光照和其他干扰因素的影响，步态识别率通常很低。因此，信息融合理论广泛应用于步态识别。Han 结合 Platts 分析与椭圆傅里叶描述子来匹配人体轮廓以进行步态识别（Han, 2010）。该方法结合了人体的时空运动特征、统计和物理参数来分析步态轮廓形状。然而，它忽略了内部特征。Derlatka 提出了一种基于人体不同步态数据的生物特征系统，结合了动态信息（地面反作用力）和静态信息（如躯干和臀部宽度、大腿长度和身高）（Derlatka & Bogdan, 2015）。该方法需要繁琐的特征提取过程和复杂的信息输入，导致计算过程复杂，无法满足实时需求。本章的组合方法不仅能描述局部纹理信息，还能描述边缘轮廓信息，计算非常简单快捷。

### 图 1. 步态识别通用步骤流程图

![Figure978-1-7998-2701-6.ch011.f01](img/ch011.f01.png)

### 图 2. 分层 LBP 和 HOG 特征

![Figure978-1-7998-2701-6.ch011.f02](img/ch011.f02.png)

前两层的 `LBP` 和 `HOG` 特征包含相对清晰的纹理特征和轮廓边缘。随着提取层数的增加，图像中可用的信息减少。第三层的信息明显模糊。因此，本章将由三层表示的 `LBP` 和 `HOG` 特征图像进行划分，每层均包含有用信息。如果综合不同层的信息，提取的信息将更加完整和有效。因此，本章采用特征融合方法，即分层 `LBP` 和基于分层 `LBP` 的分层特征融合。该方法首先对 `GEI` 图提取三次 `LBP` 特征，以获得每层的 `LBP` 直方图和每层的 `LBP` 图像，然后在每层的 `LBP` 图像上提取相应的 `HOG` 特征。基于 `LBP` 图像的 `HOG` 特征图像，将每层的 `LBP` 特征直方图和基于 `LBP` 图像的 `HOG` 特征直方图顺序连接，得到每层的融合特征直方图，最后将三层的特征直方图顺序级联，形成最终的融合特征。

根据目标不同，步态识别可分为两类。一类任务是验证：根据相似度指数或给定阈值判断给定样本和验证样本，以识别给定对象；即给定测试样本，研究问题是如何在给定数据集中找到具有相同身份的样本（Johansson, 1973）。

步态数据集包括训练数据集和测试集。训练集用于训练并生成分类模型；测试集用于评估分类模型的泛化性能。训练集和测试集保持互斥关系；即测试样本不应出现在训练集中（Zheng et al., 2011）。通常，我们使用训练数据集训练模型，并基于测试集评估步态识别方法的优劣。从实际角度来看，识别率是衡量步态识别算法性能的指标。一般来说，识别率越高，算法性能越好。此外，累积识别率和 `ROC` 曲线常用于评估性能（Yu et al., 2006; Yu et al., 2009）。

## 方法论

本章采用结合 `HOG`（Viola et al., 2005）和 `LBP`（Han & Bhanu, 2005; Jeevan et al., 2013）的特征。从 `GEI` 提取 `m` 次特征可获得 `m` 级 `LBP` 特征图像（Derlatka & Bogdan, 2015; Yan et al., 2015）。将每级 `LBP` 特征与 `HOG` 特征融合，可获得最终的融合特征。将所有特征顺序连接在一起（Wang et al., 2003）即可得到该 `GEI` 的最终特征，如图 2 所示。

### 深度神经网络架构

本章的深度神经网络由一个卷积受限玻尔兹曼机和一个全连接层网络组成（Begg, Palaniswami & Owen, 2005）。不同于卷积神经网络的监督学习方法（Tao & Maybank, 2007; Yu, et al. 2006），卷积受限玻尔兹曼机是一种无监督学习模型，它通过比较散度算法来学习网络参数，并完成输入图像的特征提取以用于识别和分类（Chen, et al. 2009; Lee, et al. 2009）。本章提出的网络使用 GEI+LBP+HOG 特征作为输入，并分别用 3×3 和 7×7 卷积核对其进行卷积，以获得不同尺度下的异步特征（Xu, et al. 2011）。同时，在卷积受限玻尔兹曼机之后获得步态特征，利用全连接网络将两个不同卷积核获得的特征融合，最终在全连接网络末端利用该特征进行分类识别，如图 3 所示。

### 图 3. 网络结构

![Figure978-1-7998-2701-6.ch011.f03](img/ch011.f03.png)

首先，使用卷积受限玻尔兹曼机（CRBM）进行特征提取；提取的步态特征通过全连接网络进行训练，最后使用 softmax 函数对特征进行分类以获得预测结果；然后将预测结果与真实结果进行比较，计算交叉熵损失。同时，使用反向传播算法优化网络参数。

在卷积受限玻尔兹曼模型训练中设置了两个不同尺寸的卷积核，分别为 3×3 和 7×7 矩阵；每种尺寸各有 32 个卷积核。通过此操作，将发现核尺寸对性能的影响。

## 实验结果

实验旨在研究所提算法的有效性。在实验中，训练数据的行走姿态与测试数据的行走姿态相同，该组实验（训练集-测试集）记为 (nm-nm)、(bg-bg)、(cl-cl)。在跨状态实验中，训练数据集的行走姿态与测试数据集不同，实验（训练集-测试集）包括 (nm-bg) 和 (nm-cl)。数据集中的四个视频序列用于 (nm-nm) 的训练，其余数据用于测试。在 (bg-bg) 和 (cl-cl) 中，一半数据用作训练集，一半用作测试集。在跨状态实验 (nm-bg) 和 (nm-cl) 中，nm 中的四个视频序列作为训练集，bg 和 cl 中的所有数据作为测试集。表 2 展示了我们的实验策略。

表 1 展示了已建立的步态识别数据库。目前，这些数据库缺乏普适性和广泛的适用性。目前最大的步态数据库是英国南安普顿大学创建的 Soton Big Gait Database，以及中国科学院自动化研究所（CASIA）创建的多视角步态数据库（CASIA-B）和红外步态数据库（CASIA-C）。此外，CASIA-C 数据库是目前唯一公开可用的大规模红外步态数据库。USMT 步态数据库是目前为数不多的可用 3D 步态库之一。

### 表 1. 现有的步态识别数据库

![Figure978-1-7998-2701-6.ch011.g01](img/ch011.g01.png)

### 图 4. 最终融合特征

![Figure978-1-7998-2701-6.ch011.f04](img/ch011.f04.png)

### 图 5. LBP 和 HOG 特征提取组合流程图

![Figure978-1-7998-2701-6.ch011.f05](img/ch011.f05.png)

计算得到的步态能量图被输入神经网络进行训练，卷积受限玻尔兹曼机的重构误差如图 6 所示。

### 图 6. 重构误差

![Figure978-1-7998-2701-6.ch011.f06](img/ch011.f06.png)

在图 6 中，初始重构误差较大，因为参数是随机初始化的。经过几轮带参数更新的迭代后，误差迅速下降并逐渐趋于一个固定值或在一个小范围内波动。

全连接层网络的训练基于交叉熵损失函数，通过迭代更新网络参数以获得优化的网络模型。训练过程中，训练误差曲线如图 7 所示。迭代后，训练误差逐渐减小并趋于稳定，这表明模型已收敛。

### 图 7. 训练误差曲线

![Figure978-1-7998-2701-6.ch011.f07](img/ch011.f07.png)

该方法的验证也在自拍视频上进行了测试，我们对数据集进行标记用于训练和测试。图 8 展示了实验研究结果。

### 图 8. 正确结果显示在单个框中，错误结果显示在多个框中

![Figure978-1-7998-2701-6.ch011.f08](img/ch011.f08.png)

在本实验中，对比了算法在三个步态数据集上、在 2×4、4×4、4×8、8×8、8×16、16×16、16×32 个分块下的识别率。获得了最佳分块，结果如图 9 所示。

在图 9 中，最佳分块为 8×8。过大或过小的分块都会影响识别率，因为过大的分块无法提取准确合适的局部特征；而过小的分块对图像配准和人体运动敏感，提取的全局和局部特征不准确。

### 图 9. 分块大小对准确率的影响

![Figure978-1-7998-2701-6.ch011.f09](img/ch011.f09.png)

本章在评估算法性能时，采用“留一交叉验证法”获得正确分类率（CCR）的无偏估计；即每次实验保留一个样本序列作为测试样本，其余样本序列作为 ANN 的训练样本（Rida, et al. 2016），根据与训练样本的相似度进行分类（Han, 2010）。为了对比本章融合特征的优势，对比了 Original-GEI（Han & Bhanu, 2005）、GEI+LBP+PCA（Sivapalan, et al. 2013）、Bayes+HMM（Chen, et al. 2009）和 Integrated-HOG（Viola, et al. 2005）的识别率。结果如表 2 所示。

### 表 2. 不同特征提取方法的 CCR

![Figure978-1-7998-2701-6.ch011.g02](img/ch011.g02.png)

此外，累积匹配分数（CMS）也被应用于评估。CMS 定义为测试度量实际类别在其前序秩值（例如 Rank = 10）处的累积概率。CCR 是 Rank 等于 1 时的累积识别率。五种方法的 CMS 分别如表 3 所示。

### 表 3. 跨状态测试结果

![Figure978-1-7998-2701-6.ch011.g03](img/ch011.g03.png)

使用 CASIA-B 数据集的卷积核识别率优于 `3×3` 卷积核的识别结果，特征融合基于 `3×3` 和 `7×7` 卷积核。后续识别准确率优于或等于单一卷积核的识别准确率。同时，本章将所提方法与其他现有方法 GPPE、GEI、STIPs 及基于 CNN 的方法进行了比较。在表 3 中，所提方法在同一状态实验（nm-nm）和（cl-cl）中略低于现有基于深度学习的方法，因为后者使用了更深的网络。在跨状态实验中，该方法表现更好，表明本章方法在鲁棒性方面更优。此外，跨状态的准确率低于其他现有方法，因为传统方法可通过针对性设计特征进行识别，而深度学习需要更多步态姿态进行训练以增强网络的泛化能力。然而，仅有一种步态状态会导致网络泛化能力较差；因此，跨状态的实验结果不优于现有方法。

## 结论

本章构建了用于人体步态识别的深度神经网络 `CRBM+FC`。基于 LBP 和 HOG 融合，提出了一种从 GEI 到输出的端到端深度学习步态识别方法。本文还提出了一种基于步态能量图的步态识别算法。该方法采用分层思想克服了步态能量图的缺陷，不仅捕捉人体图像的局部信息，还提取其轮廓和形状信息。这些信息的融合基于 CASIA 步态数据集。本章的识别算法实现了较高的识别率。文中提出了一种由卷积受限玻尔兹曼机和全连接神经网络组成的特征学习网络。该网络首先利用不同卷积核的特征受限玻尔兹曼机从步态图像中提取特征；由于卷积受限玻尔兹曼机是无监督的，它们能够广泛且丰富地学习。尽管学习到了丰富的步态特征信息，但必然存在冗余和不太有用的信息。因此，本文使用有监督的全连接层网络对这些特征进行深度学习。

在单一场景中，步态的检测和提取相对简单。然而，在复杂的实际场景中，背景和多个个体等因素的复杂性使得难以准确获取步态。不准确的步态信息直接影响最终的识别效率和准确性（Sivapalan 等，2013）。

## 参考文献

Ahonen, T., Hadid, A., & Pietikainen, M. (2006). Face description with local binary patterns: Application to face recognition. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 28(12), 2037–2041. doi:10.1109/TPAMI.2006.244

Begg, R. K., Palaniswami, M., & Owen, B. (2005). Support vector machines for automated gait classification. *IEEE Transactions on Biomedical Engineering*, 52(5), 828–838. doi:10.1109/TBME.2005.845241

Boykov, Y. Y., & Jolly, M. P. (2001). Interactive graph cuts for optimal boundary & region segmentation of objects in ND images. *Proceedings IEEE International Conference on Computer Vision*. (Vol. 1, pp. 105-112). Academic Press.

BulatA.TzimiropoulosG. (2016). Human pose estimation via convolutional part heatmap regression. *Proceedings European Conference on Computer Vision* (pp. 717-732). Springer. 10.1007/978-3-319-46478-7\_44

CaoZ.SimonT.WeiS. E.SheikhY. (2017). Realtime multi-person 2D pose estimation using part affinity fields. *Proceedings IEEE Conference on Computer Vision and Pattern Recognition* (pp. 7291-7299). 10.1109/CVPR.2017.143

Chen, C., Liang, J., Zhao, H., Hu, H., & Tian, J. (2009). Frame difference energy image for gait recognition with incomplete silhouettes. *Pattern Recognition Letters*, 30(11), 977–984. doi:10.1016/j.patrec.2009.04.012

Cunado, D., Nixon, M. S., & Carter, J. N. (1997). Using gait as a biometric, via phase-weighted magnitude spectra. *Proceedings International Conference on Audio-and Video-Based Biometric Person Authentication* (pp. 93-102). Berlin, Germany: Springer. 10.1007/BFb0015984

Dalal, N., & Triggs, B. (2005). Histograms of oriented gradients for human detection. *Proceedings International Conference on Computer Vision & Pattern Recognition*, 1, 886–893. IEEE.

DerlatkaM.BogdanM. (2015). Fusion of static and dynamic parameters at decision level in human gait recognition. *Proceedings International Conference on Pattern Recognition and Machine Intelligence* (pp. 515-524). Springer. 10.1007/978-3-319-19941-2\_49
