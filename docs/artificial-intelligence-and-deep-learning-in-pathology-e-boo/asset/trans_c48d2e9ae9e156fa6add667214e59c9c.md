

![](img/ec668102bd6cbe5645156f246a7c2e8b_137_0.png)

## 图7.3

（A）通常，新的图像模态可能难以解读。然而，深度神经网络可用于将这些图像转换为类似H&E的图像，以便更好地解读。（B）定量相位成像是一种难以解读的成像模态，但与H&E图像相比，它具有其他优势，例如更低的光毒性和便携性。训练了一个GAN将QPI图像转换为数字H&E染色图像。（C）测试了全卷积神经网络和基于像素的VGG分类，用于将多光子显微镜图像转换为H&E染色图像。（D）共聚焦激光内窥显微镜可以对组织进行体内实时分析，但图像难以解读。该研究没有使用GAN等传统图像翻译算法，而是使用神经风格迁移对CLE图像进行数字染色。GAN，生成对抗网络；QPI，定量相位成像；CLE，共聚焦激光内窥显微镜。

（A）经许可改编自Rivenson Y, Liu T., Wei Z., Zhang Y., de Haan K, and Ozcan A, PhaseStain: the digital staining of label-free quantitative phase microscopy images using deep learning, Light: Science & Applications 2019;8(1):1–11. https://doi.org/10.1038/s41377-019-0129-y （B）经许可改编自Rivenson Y, Liu T, Wei Z, Zhang Y, de Haan K, and Ozcan A, PhaseStain: the digital staining of label-free quantitative phase microscopy images using deep learning, Light: Science & Applications 2019;8(1):1–11. https://doi.org/10.1038/s41377-019-0129-y （C）经许可改编自Borhani N, Bower AJ, Boppart SA, and Psaltis D, Digital staining through the application of deep neural networks to multi-modal multi-photon microscopy, Biomedical Optics Express 2019;10(3):1339–1350. https://doi.org/10.1364/BOE.10.001339; （D）经许可改编自Izadyyazdanabadi M, et al., Fluorescence image histology pattern transformation using image style transfer, Frontiers in Oncology 2019;9. https://doi.org/10.3389/fonc.2019.00519

针对皮肤组织的H&E染色、肾脏组织的Jones染色和肝脏组织的Masson三色染色进行了训练。然后，将这些模型应用于训练集中未出现的类似图像。他们利用自定义的全局共配准方法和弹性图像配准进行局部特征配准。生成器采用了U-net架构，输入是转换为YCbCr颜色空间的H&E图像。凭借快速的推理时间，并且无需染色，这项技术有潜力降低人力和时间成本。虽然

在某些情况下，染色过程可能导致不可逆的修改或损伤；这通常被认为是不利的，因为它会妨碍对组织的进一步分析。然而，在体外受精（IVF）中精子细胞选择的特殊情况下尤其如此，因为染色具有潜在的细胞毒性。干涉相位显微镜（IPM）目前用于精子评估，因为它与现有的医用显微镜兼容，这些显微镜经过改装，增加了一个波前传感器，以实现全息显微成像。这种组合无需染色即可提供细胞的定量拓扑图。然而，细胞形态学评估最有效的方法是对细胞器进行化学染色。因此，研究人员开发了一种名为“HoloStain”的方法，利用DCGANs[39]将从数字全息图中提取的定量相位图像和相位梯度图像转换为虚拟染色的明场图像。对于每个细胞，使用四张图像的集合来训练模型：无染色定量相位图像、两张无染色相位梯度图像以及目标染色的明场图像。HoloStain的一个优点是，失焦的细胞可以被虚拟染色并重新聚焦。这是可能的，因为可以对全息图进行数字重建，从而使失焦细胞重新对焦。为了证明该算法的实用性，一位胚胎学家使用来自明场图像（未染色）、无染色定量相位图像、一张无染色梯度图像以及HoloStain图像的数据对精子细胞进行了分类。与其他三种方法相比，HoloStain方法的F1分数最高。

虽然大多数研究采用GAN，但也可以使用图像风格迁移算法作为替代方法，正如IzadyYazdanabadi等人[10]所证明的那样。具体来说，作者试图将共聚焦激光内窥显微镜（CLE）图像转换为H&E图像。CLE是一种实时的体内术中成像技术，在手术过程中辅助神经外科医生方面具有很大潜力。作者开发了一种转换工具，可以去除常见的CLE伪影、添加组织学模式，并避免去除关键特征或向图像添加不真实的特征（图7.3D）。不幸的是，由于精确共定位的问题和组织的内在运动，难以获得空间配准的H&E-CLE图像对。因此，作者采用了一种使用预训练VGG19架构以及内容和风格损失的图像风格迁移算法。风格迁移的一个优点是它只需要一张所需风格（H&E）的图像。五位神经外科医生独立评估，认为风格化后的CLE图像比原始CLE图像具有显著更高的诊断质量。

这些方法的潜力相当高，在实施方面也相当成熟，目前已有多个团队正在进行临床试验。从这些方法获得的图像质量远远超过了当前实时病理学的金标准——冷冻切片，而冷冻切片会产生伪影，使评估变得困难。通过将图像从荧光配色方案转换为病理学家一看就熟悉的配色方案，采用的可能性大大增加。这些成像方式有潜力在不久的将来成为实时病理学的新金标准；因此，精确的颜色映射引起了广泛关注。

## *计算机模拟标记*

深度学习推动了从其他图像模态中提取信息以重建明场染色图像的方法的发展。然而，能否从无染色的明场图像中重建出突出显示荧光标记细胞结构的分子染色图像呢（图7.4A）？近期研究表明这类转换确实是可能的。受参考文献[40]的启发，我们将此类工作称为计算机模拟标记。

Rana等人[41]证明了如何使用条件生成对抗网络（cGANs）对未染色的石蜡包埋全切片图像（WSIs）进行计算染色。他们同时训练了染色和脱色模型，使用传统的GAN和L1损失函数，并额外利用基于皮尔逊相关系数的正则化项来防止平铺噪声。这些模型可用于肿瘤诊断等进一步的后续任务。

Rivenson等人[42]则利用DAPI激发/发射滤光片组激发未染色组织切片产生的自发荧光，以重建

![](img/ec668102bd6cbe5645156f246a7c2e8b_140_0.png)

## 图7.4
（A）新研究已证明，可以使用深度学习将未染色图像转换为数字染色图像。（B）一种基于GAN的模型被成功应用于将未染色自发荧光图像转换为H&E虚拟染色图像。（C）训练了一个多任务模型，用于将未标记的透射光图像转换为荧光标记图像。GAN，生成对抗网络。

*（A）经许可改编自Rana A, Yauney G, Lowe A, and Shah P, Computational histological staining and destaining of prostate core biopsy RGB images with generative adversarial neural networks, 2018年第17届IEEE国际机器学习与应用会议（ICMLA），奥兰多，佛罗里达州，2018年，第828–834页。 https://doi.org/10.1109/ICMLA.2018.00133 （B）经许可改编自Rivenson Y, 等, Virtual histological staining of unlabelled tissue-autofluorescence images via deep learning, Nature Biomedical Engineering 2019;3(6):466–477. https://doi.org/10.1038/s41551-019-0362-y; （C）经许可改编自Christiansen EM, 等, In silico labeling: predicting fluorescent labels in unlabeled images, Cell 2018;173(3):792–803. https://doi.org/10.1016/j.cell.2018.03.040.*

