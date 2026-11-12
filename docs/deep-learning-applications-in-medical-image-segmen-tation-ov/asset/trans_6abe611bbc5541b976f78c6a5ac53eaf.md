
表 2.3 基于深度学习的肝脏分割模型摘要。

| 参考文献 | 模态 | 模型 | 数据集 | 性能 |
| :--- | :--- | :--- | :--- | :--- |
| (Stollenga et al. 2015) | CT | FCN | 3DIRCAD (Soler et al. 2010) | DSC – 95.7% |
| (Christ et al. 2017) | CT, MR | Cascaded FCN | 3DIRCAD (Soler et al. 2010) | DSC – 94.3% |
| (Li et al. 2018b) | CT | H-Dense U-Net | LiTS (Bilic et al. 2023), 3DIRCAD (Soler et al. 2010) | DSC – 96.5%, 98.2% |
| (Seo et al. 2020) | CT | U-Net modified (mUNet) | LiTS (Bilic et al. 2023), 3DIRCAD (Soler et al. 2010) | DSC – 96.0%, 98.51% |
| (Liu et al. 2019) | CT | Cascaded UNet | LiTS (Bilic et al. 2023) | DSC – 97.16% |
| (Zhou et al. 2018) | CT | U-Net – Nested | LiTS (Bilic et al. 2023) | IoU – 82.9% |
| (Dou et al. 2017) | CT | CNN-3D | Sliver07 | VOE 5.4 |
| (Tran et al. 2021) | CT | U^n–Net | LiTS (Bilic et al. 2023), 3DIRCADb (Soler et al. 2010) | DSC – 96.38%, 96.45% |
| (Wang et al. 2021) | CT | SAR-UNet | LiTS (Bilic et al. 2023) | DSC – 95.71% |
| (Fan et al. 2021) | CT | MSN-Net | MICCAI2017 LiTS (Bilic et al. 2023) | DSC – 94.24%, IoU – 90.75% |

在胸部 X 射线中对肺部进行分割面临的问题是，由于严重肺部疾病导致的极端肺形状转移和模糊肺区域，自动肺部分割模型可能被错误构建。刘等人（2022）使用预训练的 efficientnet-b4 编码器，以及解码器中的残差块和 LeakyReLU 激活函数，增强了 U-Net 网络的性能。通过避免梯度反向传播中乘法效应带来的梯度不稳定性，该网络能够高效提取肺野特征。与其他方法的实验比较表明，该方法不仅在从 CXR 图像中分割肺部方面更准确，而且标准差更低、更稳健。帕尔等人（2022）引入了 Attention UW-Net，它通过一个新颖的中间层连接编码器和解码器层。最终编码器层经过上采样生成中间层，该中间层包含多个全连接卷积层。这些层通过跳跃连接与相应的上采样和下采样块建立连接。一个下采样层被用来将中间层额外链接到解码器管道。UW-Net 不仅超越了 U-Net 及其衍生模型，还超越了近年来开发的其他传统自动和半自动分割/标注模型。由于所有类型（大、中、小病变）的分割掩码预测准确率具有统一性，该模型非常适合器官的自动标注。表 2.4 汇总了各种基于深度学习的肺部分割模型。

表 2.4 基于深度学习的肺部分割模型摘要。

| 参考文献 | 模态 | 模型 | 数据集 | 性能 |
| :--- | :--- | :--- | :--- | :--- |
| (Stirenko et al. 2018) | X-ray | CNN | SH | Acc – 70% |
| (Gaal et al. 2020) | X-ray | Attention U-Net | JSRT (Shiraishi et al. 2000) | DSC – 97.5% |
| (Hofmanninger et al. 2020) | CT | U-Net, ResU-net | LTRC (Goksel and Foncubierta-Rodriguez 2017), Anatomy3 (Yang et al. 2018b) | DSC – 94%, 92% |
| (Pawar and Talbar 2021) | CT | GAN | ILD (Depeursinge et al. 2012) | DSC – 96% |
| (Ait Skourt et al. 2018) | CT | U-Net | LIDC (Armato et al. 2011) | DSC – 95.02% |
| (Wu and Lin 2020) | CT | Dilated – FCN | LIDC/IDRI (Armato et al. 2011) | DSC – 97.02% |
| (Yahyatabar et al. 2020) | X-ray | Dense-Unet | JSRT (Shiraishi et al. 2000), Montgomery | DSC – 97.6%, 97.9% |
| (Liu et al. 2022) | X-ray | Improved UNet | JSRT (Shiraishi et al. 2000), Montgomery | DSC – 97.9%, 97.7% |
| (Pal et al. 2022) | X-ray | Attention-UWNet | NIH Chest X-ray (Wang et al. 2017) | F1 – 83.8% |

### 2.3.1.5 肾脏

肾脏分割是分析图像和开发复杂手术程序中的关键步骤。针对 CT 扫描中的肾脏分割，已提出多种深度神经网络（DNN）。科托等人（2019）训练了一组全卷积网络，并在测试期间结合其预测结果进行分割。该算法实现了高度准确的分割结果，尤其是在勾勒肾皮质方面。虽然提供的参考分割的精度似乎对数值性能设定了适度的上限，但所提出的解决方案在 CT 图像中提供了可靠且准确的肾皮质自动分割。杨等人（2018a）将基于 3D FCN 的架构与金字塔池化相结合，以增强特征提取。张等人（2019）提出了一种基于 3D FCN 的两阶段框架，用于分割肾脏和肿瘤。为了减轻类别不平衡和计算开销，第一步是在早期阶段定位肾脏并移除多余背景。然后在第二阶段，对裁剪补片中的肾脏和肿瘤进行仔细分割。该建议技术的综合 Dice 系数为 90.24%，使团队在 MICCAI 2019 肾肿瘤分割（KiTS）挑战赛中位列 105 支参赛队伍的第四名。赵等人（2020）提出了一种多尺度监督 U-Net，用于从 CT 图像中分割肾脏和肾肿瘤。作者利用 KiTS19 数据集，设计了一种架构，通过集成深度监督与指数损失来提高 3D U-Net 的性能。表 2.5 汇总了各种基于深度学习的肾脏分割模型。

表 2.5 基于深度学习的肾脏分割模型摘要。

| 参考文献 | 模态 | 模型 | 数据集 | 性能 |
| :--- | :--- | :--- | :--- | :--- |
| (Couteaux et al. 2019) | CT | Ensemble UNet | COCO (Lin et al. 2014) | DSC – 86.7% |
| (Wang et al. 2019b) | CT | Modified U-Net | KiTS (Heller et al. 2019) | DSC – 95.4% |
| (Yang et al. 2018a) | CT | FCN with PPM | Private | DSC – 93.1% |
| (Zhang et al. 2019) | CT | 3D-FCN | KiTS (Heller et al. 2019) | DSC – 90.24% |
| (Zhao et al. 2020) | CT | Multi-scale supervised 3D U-Net | KiTS (Heller et al. 2019) | DSC – 96.9% |

### 2.3.1.6 心脏

心脏是我们身体的重要器官。然而，许多人也因诸多心脏问题而生命受到威胁。为了解决心脏医疗领域的实际问题，必须实现心脏区域的自动分割。根据多项研究（Wang and Smedby 2018; Payer et al. 2018），完整的心脏已使用基于深度学习的神经网络进行了分割。陈等人（Tran 2016）使用全卷积神经网络架构对心脏 MRI 进行了像素分类。短轴心脏 MRI 前所未有地实现了所提 FCN 架构所能提供的如此复杂的语义分割。韩等人（2020）开发了一种级联体积 FCN。该方法采用串联的一对 V-Net。第一个网络定位心脏，第二个网络将心脏和大血管结构划分为更小的部分。为了帮助从 MR 图像中进行心脏分割，作者将 V-Net 重建为 3D V-Net。叶等人（2019）提供了一种新型深度监督 3D U-NET，通过使用多深度融合提取上下文信息来改进原始网络。作者采用了焦点损失，并将其应用扩展到图像分割领域的多类别挑战中。最后，他们将焦点损失与 Dice 损失耦合，形成了新的混合损失函数。混合损失可用于解决类别不平衡的问题。沈等人（2019）开发了一种统一架构，同时利用深度学习和传统水平集方法进行冠状动脉计算机血管造影（CTA）分割。利用 3D FCN 学习冠状动脉的 3D 语义特征，这为经典水平集提供了良好的起点。徐等人（2020）提出了一种新型 GAN，称为渐进序列因果 GAN（PSCGAN）。

这标志着在动态 MR 成像中开创性地开发了一种无造影剂缺血性心脏病（IHD）技术，能够同时生成类似晚期钆增强（LGE）的图像，并准确分割与诊断相关的组织。为了实现这一目标，PSCGAN 具有三个非常有用的特性：

- 1) 一种用于图像合成与分割训练的迭代框架，采用分而治之策略，包含三个阶段（即先验生成、条件合成和增强分割）。
- 2) 设计了一种序列因果学习网络（SCLN），具有多尺度双流路径和多注意力加权单元。该架构在从动态 MR 图像中提取空间和时序连接的同时，能有效识别特定于任务的依赖关系。它还融合了 GAN 架构，利用对抗训练使整个过程中更容易理解动态 MR 图像中感兴趣的隐空间依赖关系。
- 3) 为自主学习开发的两种损失概念：为了减轻合成过程中的噪声，作者采用了利用稀疏正则化的合成正则化损失项；在分割中，作者采用了利用每种组织像素数量的辅助损失项，以补偿判别。
