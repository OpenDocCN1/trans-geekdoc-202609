

使用 SIPaKMeD 数据集进行了训练和评估。研究结果表明，两种配置都表现出强大且可比拟的性能，总体平均精度（mAP）值分别为 89% 和 88%。这些一致的结果强调了两种模型在提供高效分割和分类功能方面的可靠性。因此，这些模型有可能显著减轻医疗专业人员的工作量，并提高宫颈细胞图像分析的诊断准确性。

未来工作涵盖多个方向，旨在改进宫颈细胞分割并扩展其应用。主干结构的创新以及多类实例分割的调整，是增强模型适应性和提高对各类宫颈细胞描绘准确性的主要目标。该方法的通用性超出了宫颈细胞分割的范畴，有望应用于各种生物医学成像学科。努力构建大规模宫颈癌细胞数据库，将优化模型训练并提升整体性能。将算法集成到医疗设备中用于大规模宫颈筛查，并为阴道镜检查开发人工智能算法，可显著增强诊断能力并简化宫颈癌筛查流程。这些共同努力旨在提升宫颈癌筛查方法的精确性、可及性和实用性，促进医疗效果的改善。

## REFERENCES

- Agustiansyah, P., Nurmaini, S., Nuranna, L., Irfannuddin, I., Sanif, R., Legiran, L., Rachmatullah, M. N., Florina, G. O., Sapitri, A. I., & Darmawahyuni, A. (2022). 利用实例分割技术改进自动癌前病变筛查准确性. Sensors, 22(15).
- Chen, J., & Zhang, B. (2021). 基于掩码区域卷积神经网络的重叠宫颈细胞分割. Computational and Mathematical Methods in Medicine, 2021.
- Cohen, P. A., Jhingran, A., Oaknin, A., & Denny, L. (2019). 宫颈癌. Lancet (London, England), 393 (10167), 169–182.
- Dongyao Jia, A., Zhengyi Li, B., & Chuanwang Zhang, C. (2020). 基于强特征 CNN-SVM 网络的宫颈癌细胞检测. Neurocomputing, 411, 112-127.
- Girshick, R. (2015). Fast R-CNN. IEEE 国际计算机视觉会议论文集, 1440–1448.
- He, K., Gkioxari, G., Dollár, P., & Girshick, R. (2017a). Mask R-CNN. IEEE 国际计算机视觉会议论文集, 2961–2969.
- He, K., Gkioxari, G., Dollár, P., & Girshick, R. (2017b). Mask R-CNN. IEEE 国际计算机视觉会议论文集, 2961–2969.
- He, K., Zhang, X., Ren, S., & Sun, J. (2015). 图像识别的深度残差学习.
- Hsieh, Y.-C., Chin, C.-L., Wei, C.-S., Chen, I.-M., Yeh, P.-Y., & Tseng, R.-J. (2020). 结合 VGG16、Mask R-CNN 和 Inception V3 识别乳腺微钙化簇的良性与恶性. 2020 模糊理论及其应用国际会议 (IFUZZY), 1–4.
- Lin, T.-Y., Dollár, P., Girshick, R., He, K., Hariharan, B., & Belongie, S. (2016). 目标检测的特征金字塔网络.
- Nayar, R., & Wilbur, D. C. (2017). 宫颈细胞学报告的贝塞斯达系统：历史视角. Acta Cytologica, 61(4–5), 359–372.
- Plissiti, M. E., Dimitrakopoulos, P., Sfikas, G., Nikou, C., Krikoni, O., & Charchanti, A. (2018). Spikmed：巴氏涂片图像中正常和病理宫颈细胞的特征与图像分类新数据集. 图像处理国际会议论文集，ICIP, 3144–3148.
- Ren, S., He, K., Girshick, R., & Sun, J. (2015). Faster R-CNN：面向带区域建议网络的实时目标检测. 神经信息处理系统进展, 28.
- Sagar, C. V., Bhardwaj, H., & Bhan, A. (2023). 基于巴氏涂片的宫颈癌检测深度学习分割方法. In B. K. Murthy, B. V. R. Reddy, N. Hasteer, & J.-P. Van Belle (Eds.), Decision Intelligence (pp. 309–317). Springer Nature Singapore.
- Sarwar, A., Sheikh, A. A., Manhas, J., & Sharma, V. (2020). 宫颈细胞分割用于自动宫颈癌筛查：综述. Artificial Intelligence Review, 53(4), 2341–2379.
- Xie, S., Girshick, R., Dollár, P., Tu, Z., & He, K. (2016). 深度神经网络的聚合剩余变换.

## 用于轻量级神经网络的空洞卷积模型

Sachin Gupta
Department of CSE, Maharaja Agrasen Institute of Technology, India

Priya Goyal
Department of Computer Science and Engineering, Manipal University Jaipur, India

Bhuman Vyas
Credit Acceptance, Canton, USA

Mohammad Shabaz
Model Institute of Engineering and Technology, Jammu, J&K, India

Suchitra Bala
ICT & Cognitive Systems, Sri Krishna Arts And Science College, India

Aws Zuhair Sameen
College of Medical Techniques, Al-Farahidi University, Baghdad, Iraq

### 摘要

轻量卷积神经网络正在被进一步研究，以便更好地将深度卷积神经网络部署到边缘设备，减少深度神经网络中的模型参数数量，并降低网络复杂度。为了实现轻量化目标，对剩余网络结构执行全卷积。为了增强轻量化效果，将其与逐点卷积相结合，构建了一种改进的空洞卷积轻量化方法。增强的空洞卷积与传统卷积相耦合，以减轻准确率的衰减，并提出了一种轻量化融合空洞卷积。根据数据，改进的空洞卷积轻量化方法提供了最显著的轻量化收益。此外，轻量化融合空洞卷积方法减少了模型参数数量，并提供了最佳的速度-准确率权衡。

## 1 引言

近年来，卷积神经网络有两个发展趋势。一方面，它朝着大规模和深层级方向发展；另一方面，它朝着轻量化和高速度方向发展。随着移动互联网的快速增长，人们对移动边缘设备的需求越来越高，对轻量化卷积神经网络的需求也越来越多。在边缘设备上更流畅地运行深度学习算法已成为一项挑战。边缘设备存储空间小且缺乏计算资源，为卷积神经网络的轻量化方法提供了广阔的研究与开发平台。空洞卷积首次由（Zhu et al. 2020）系统研究。基础空洞卷积轻量化方法直接将空洞卷积应用于网络结构设计，具有出色的轻量化效果和略高的准确率损失；改进的空洞卷积轻量化方法将逐点卷积与空洞卷积相结合。

## 2 相关工作

为了实现轻量化神经网络，模型设计的优化通常通过使用小卷积核替代大卷积核、分解卷积以及处理卷积通道来实现（Yu et al. 2019）。现代深度神经网络通常在网络设计中使用小卷积核替代大卷积核（Zhang et al. 2018）。Squeeze Net 是最早公开的轻量化结构设计网络。一方面，使用 1 × 1 小卷积核替代 3 × 3。因此，该内核可将卷积操作参数量减少八倍，并减少大部分卷积操作（Zhang, Zhang and Wang 2019）。Shuffle Net 使用分组卷积的思想，并将不同组的特征信息进行重排，使分组后的卷积特征信息被打乱和混合，从而能够更好地传播（Risso et al. 2021）。上述模型优化方法通过重新设计模型的宏观结构和微观结构，实现了一种新的高效骨干网络，并从结构层面完成了神经网络的轻量化设计（Guo et al. 2021）。

## 3 基于空洞卷积的神经网络轻量化方法

### 3.1 空洞卷积结构

空洞卷积是一种具有独特结构的卷积，引入了空洞的概念。通过在传统图像卷积中添加空洞，实现了扩大卷积感受野的目的。例如，设 H_i 为第 i 层的特征图，G_i 为第 i 层的卷积层。那么，特征图 H_i 中的点，b 是卷积层 G_i 中的点，

```
(H_i * G_i)(q) = \sum_{b+c=q} H_i(b)G_i(c)  \quad (1)
```

空洞卷积的计算公式如公式 (2) 所示，其中 m 为扩张率，空洞数比普通卷积多 1。当扩张率 m 为 1 时，空洞卷积变为普通卷积。

```
(H_i * G_i)(q) = \sum_{b+mc=q} H_i(b)G_i(c)  \quad (2)
```

从空洞卷积和普通卷积的计算公式可以看出，空洞卷积操作具有等间隔采样的特征，扩张率决定其采样程度。扩张率越大，空洞卷积的采样范围越广，单位范围内的点越少。感受野的计算公式为公式 (3)——第 i 层卷积的步幅。

```
sf_l = sf_{l-1} + (\eta_l - 1) * \prod_{i=1}^{l-1} t_i  \quad (3)
```

空洞卷积在不减小特征图尺寸的情况下扩大了感受野。因此，第 l 层空洞卷积的核心大小 em_l 的计算公式如公式 (4) 所示，其中 m_l 表示第 l 层原始普通卷积的核心大小。

```
em_l = m_l + (m_l - 1) * (n - 1)  \quad (4)
```

将公式 (4) 代入公式 (3)，第 l 层大小为 em_l 的空洞卷积核对标准卷积扩张的感受野

