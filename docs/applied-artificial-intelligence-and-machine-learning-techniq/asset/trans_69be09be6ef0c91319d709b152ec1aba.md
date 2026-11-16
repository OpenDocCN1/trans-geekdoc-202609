

![](img/a454246e6e2ea26f4583534f7cbdd134_98_0.png)

![](img/a454246e6e2ea26f4583534f7cbdd134_98_1.png)

(a) 不含 CBAM 的 CNN

(b) 含 CBAM 的 CNN

图 6.5 提议 CNN 模型的混淆矩阵。

![](img/a454246e6e2ea26f4583534f7cbdd134_98_2.png)

(a) 不含 CBAM 的 CNN

![](img/a454246e6e2ea26f4583534f7cbdd134_98_3.png)

(b) 含 CBAM 的 CNN

图 6.6 基于 ROC-AUC 曲线的性能度量。

表 6.4 性能比较

| 模型名称 | 参数 | 深度 | 准确率 (%) |
|---|---|---|---|
| VGG16 [16] | 138.4M | 16 | 96.23 |
| VGG19 [16] | 143.7M | 19 | 96.51 |
| InceptionV3 [17] | 23.9M | 189 | 97.20 |
| ResNet50 [18] | 25.6M | 107 | 97.43 |
| DenseNet121 [19] | 8.1M | 242 | 96.07 |
| MobileNetV2 [20] | 3.5M | 105 | 94.50 |
| 提议模型 | 0.0565M | 13 | 98.34 |

在 ROC-AUC 曲线方面。图 6.6 显示了提议模型的 ROC-AUC 曲线，该图表明提议模型以高性能准确率对图像进行分类。

为更好地展示提议模型的特征提取能力，实现了一些最先进的深度学习（DL）模型以供比较。比较中考虑的深度学习不同变体包括 VGG16、VGG19、InceptionV3、ResNet50、DenseNet、EfficientNetB0 和 MobileNetV2。性能比较如表 6.4 所示。从表 6.4 可以看出，与参数更少的最先进的深度学习架构相比，提议模型具有更高的性能准确率。

### 6.5 结论

本研究表明，将注意力模块纳入基于深度学习的模型，有助于提高从医学影像数据中检测结肠癌的效果。注意力模块的集成使模型能够根据图像中特征的显著性动态调整其关注点，从而优先处理潜在病变区域，同时抑制无关的背景噪声。本章中，我们提出了一种在肺癌和结肠癌识别中带有 CBAM 的轻量级深度学习模型。带有 CBAM 的提议 CNN 模型的性能与不含自注意力模型的 CNN 架构以及多种最先进的深度学习架构进行了比较。结果表明，带有注意力的 CNN 具有更好的图像识别能力，准确率达到 98.34%。此外，提议模型在参数方面与多个深度学习模型进行了比较，结果表明提议模型使用的参数较少且模型深度更低。

### 参考文献

- [1] Shafi, L., Iqbal, P., Khaliq, R.: 印度癌症负担：发病率统计分析. Indian Journal of Public Health **67**(4), 582–587 (2023)
- [2] Pacal, I., Karaboga, D., Basturk, A., Akay, B., Nalbantoglu, U.: 结肠癌中深度学习的综合综述. Computers in Biology and Medicine **126**, 104003 (2020)
- [3] Karthikeyan, A., Jothilakshmi, S., Suthir, S.: 基于卷积神经网络 (CNN) 和排名算法的结直肠癌检测. Measurement: Sensors 31, 100976 (2024)
- [4] Giger, M.L., Doi, K., MacMahon, H.: 数字放射摄影中的图像特征分析和计算机辅助诊断。3. 外周肺野结节自动检测. Medical Physics 15(2), 158–166 (1988)
- [5] Rathore, S., Hussain, M., Khan, A.: 基于新颖几何特征和一些传统特征混合的结肠癌自动检测. Computers in Biology and Medicine 65, 279–296 (2015)
- [6] Masud, M., Sikder, N., Nahid, A.-A., Bairagi, A.K., AlZain, M.A.: 基于深度学习分类框架的机器学习肺癌和结肠癌诊断方法. Sensors 21(3), 748 (2021)
- [7] Zhang, J., Xia, Y., Xie, Y., Fulham, M., Feng, D.D.: 通过联合使用深度和手工制作的视觉特征对生物医学文献中的医学图像进行分类. IEEE Journal of Biomedical and Health Informatics 22(5), 1521–1530 (2017)
- [8] Hamida, A.B., Devanne, M., Weber, J., Truntzer, C., Derang'ere, V., Ghiringhelli, F., Forestier, G., Wemmert, C.: 结肠癌病理图像分析的深度学习. Computers in Biology and Medicine 136, 104730 (2021)
- [9] Talakder, M.A., Islam, M.M., Uddin, M.A., Akhter, A., Hasan, K.F., Moni, M.A.: 基于深度特征提取和集成学习的机器学习肺癌和结肠癌检测. Expert Systems with Applications 205, 117695 (2022)
- [10] Chhillar, I., Singh, A.: 基于特征工程的机器学习技术，用于从病理图像中检测和分类肺癌和结肠癌. Medical & Biological Engineering & Computing 62(3), 913–924 (2024)
- [11] Sakr, A.S., Soliman, N.F., Al-Gaashani, M.S., Plawiak, P., Ateya, A.A., Hammad, M.: 一种高效的结肠癌检测深度学习方法. Applied Sciences 12(17), 8450 (2022)
- [12] Sharkas, M., Attallah, O.: Color-CADX: 通过三重卷积神经网络和离散余弦变换对结直肠癌进行分类的深度学习方法. Scientific Reports 14(1), 6914 (2024)
- [13] Seth, A., Kaushik, V.D.: 使用改进级联卷积神经网络自动检测肺癌和结肠癌. Multimedia Tools and Applications 83, 1–22 (2024)
- [14] Woo, S., Park, J., Lee, J.-Y., Kweon, I.S.: CBAM: 卷积块注意力模块. In: Proceedings of the European Conference on Computer Vision (ECCV), pp. 3–19 (2018)
- [15] Borkowski, A.A., Bui, M.M., Thomas, L.B., Wilson, C.P., DeLand, L.A., Mastorides, S.M.: 肺癌和结肠癌病理图像数据集 (LC25000). arXiv 预印本 arXiv:1912.12142 (2019)
- [16] Karen, S.: 用于大规模图像识别的非常深层卷积网络. arXiv 预印本 arXiv:1409.1556 (2014)
- [17] Szegedy, C., Vanhoucke, V., Ioffe, S., Shlens, J., Wojna, Z.: 重新思考计算机视觉的 Inception 架构. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 2818–2826 (2016)
- [18] He, K., Zhang, X., Ren, S., Sun, J.: 图像识别的深度残差学习. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 770–778 (2016)
- [19] Huang, G., Liu, Z., Van Der Maaten, L., Weinberger, K.Q.: 密集连接卷积网络. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 4700–4708 (2017)
- [20] Sandler, M., Howard, A., Zhu, M., Zhmoginov, A., Chen, L.-C.: Mobilenetv2: 倒置残差和线性瓶颈. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 4510–4520 (2018)

## 7 基于声学的帕金森病诊断：使用迁移学习结合 VGG16 与轻量级梯度提升机 (LGBM) 分类器

Shibina V 和 Thasleema T M

### 7.1 引言

帕金森病（PD）是一种随时间推移而进展的慢性神经功能障碍，主要影响运动控制。该疾病源于黑质中产生多巴胺的神经元逐渐被破坏，黑质是大脑中对运动协调至关重要的区域。患者通常会出现震颤、运动迟缓、肌肉僵硬、言语障碍和平衡问题等症状。除了这些运动症状外，睡眠问题、认知下降和情绪障碍等非运动问题也很普遍 [1, 2]。说话困难经常是帕金森病的早期迹象之一。研究表明，90% 的 PD 患者不同程度存在声带功能障碍。PD 会损害肌肉功能和自主运动，对发声系统产生显著影响 [3]。言语障碍可能包括声道体积和舌头灵活性降低、音调范围和说话强度减少、语音质量差以及不及时停顿。因此，通过语音线索预测帕金森病（尤其是在早期阶段）是合理且至关重要的课题 [4]。近期研究已探索利用自动语音分析来诊断帕金森病。深度学习（DL）和机器学习（ML）方法已应用于语音分析，以识别和监测 PD [5]。

PD 症状因人而异。研究人员已开发出多种影像和信号检测来检测 PD。PD 的检查包括扩散张量成像（DaTscan）和磁共振成像（MRI）[6]。尽管生物标志物、基因和神经影像学有所进步，但医学检测
