

- 分类。在 _2020 IEEE 第 4 届图像处理、应用与系统国际会议 (IPAS)_, 第 174–179 页。IEEE, 2020.

- 25. Jeremy Kawahara, Sara Daneshvar, Giuseppe Argenziano, and Ghassan Hamarneh. 七点检查表与使用多任务多模态神经网络的皮肤病变分类。_IEEE 生物医学与健康信息学杂志_, 23(2):538–546, 2018.

- 26. Seema Kolkur and DR Kalbande. 基于纹理的皮肤病检测特征提取综述。在 _2016 商业、工业与政府 ICT 国际会议 (ICTBIG)_, 第 1–6 页。IEEE, 2016.

- 27. Hongfeng Li, Yini Pan, Jie Zhao, and Li Zhang. 基于深度学习的皮肤病诊断：综述。_arXiv 预印本 arXiv:2011.05627_, 2020.

- 28. Andrew L Maas, Awni Y Hannun, Andrew Y Ng. 整流器非线性改进神经网络声学模型。在 _ICML 论文集_, 第 30 卷, 第 3 页。Citeseer, 2013.

- 29. T Mendonça, PM Ferreira, J Marques, ARS Marçal, and J Rozeira. 用于研究和基准测试的皮肤镜图像数据库。_PH2 IEEE EMBC 论文集中的演示_, 2013.

- 30. Andrew Ng. 数据科学家应该了解的深度学知识。https://www.slideshare.net/ExtractConf, 2015.

- 31. Fabian Pedregosa, Gaël Varoquaux, Alexandre Gramfort, Vincent Michel, Bertrand Thirion, Olivier Grisel, et al. Scikit-learn：_Python_ 中的机器学习。_机器学习研究杂志_, 12:2825–2830, 2011.

- 32. Adrian Rosebrock. _使用 Python 进行计算机视觉深度学习：实践者套装_. PyImageSearch, 2017.

- 33. Xiaolei Shen, Jiachi Zhang, Chenjun Yan, and Hong Zhou. 基于卷积神经网络的面部寻常痤疮自动诊断方法。_科学报告_, 8(1):1–10, 2018.

- 34. Karen Simonyan and Andrew Zisserman. 用于大规模图像识别的非常深层卷积网络。_arXiv 预印本 arXiv:1409.1556_, 2014.

- 35. Nitish Srivastava, Geoffrey Hinton, Alex Krizhevsky, Ilya Sutskever, and Ruslan Salakhutdinov. Dropout：防止神经网络过拟合的简单方法。_机器学习研究杂志_, 15(1):1929–1958, 2014.

- 36. Xiaoxiao Sun, Jufeng Yang, Ming Sun, and Kai Wang. 临床皮肤病图像自动视觉分类基准。在 _欧洲计算机视觉会议_, 第 206–222 页。Springer, 2016.

- 37. Talicia Tarver. 2012 年癌症事实与数据。American Cancer Society (ACS) Atlanta, GA: American Cancer Society, 2012. 66 页, pdf.

- 38. Philipp Tschandl, Cliff Rosendahl, and Harald Kittler. HAM10000 数据集：常见色素性皮肤病变的多源皮肤镜图像大型集合。科学数据, 5(1):1–9, 2018.

- 39. Xiaoping Wu, Ni Wen, Jie Liang, Yu-Kun Lai, Dongyu She, Ming-Ming Cheng, and Jufeng Yang. 通过标签分布学习进行痤疮图像联合分级与计数。在 IEEE/CVF 国际计算机视觉会议论文集, 第 10642–10651 页, 2019.

- 40. Xin Yi, Ekta Walia, and Paul Babyn. 利用 Wasserstein 距离辅助的分类生成对抗网络的非监督与半监督学习用于皮肤镜图像分类。arXiv 预印本 arXiv:1804.03700, 2018.

- 41. Zhen Yu, Xudong Jiang, Feng Zhou, Jing Qin, Dong Ni, Siping Chen, Baiying Lei, and Tianfu Wang. 通过聚合深度卷积特征识别皮肤镜图像中的黑色素瘤。IEEE 生物医学工程学报, 66(4):1006–1016, 2018.

## 基于 COVIDx 数据集的 COVID-19 诊断深度学习方法：初步调查

Esraa Hassan

卡夫尔谢赫大学人工智能学院机器学习与信息检索系，埃及卡夫尔谢赫

Mahmoud Y. Shams, Noha A. Hikak, 和 Samir Elmougy

曼苏拉大学计算机与信息学院信息技术系，埃及曼苏拉

### 内容

- 6.1 引言 108
- 6.2 数据集描述 109
- 6.3 COVIDx 数据集 109
- 6.4 COVIDx-CT 数据集 109
- 6.5 相关工作 110
- 6.6 结论 117

COVID-19 是一种严重且普遍流行的疾病，因为它直接影响肺部，使全世界许多人的生命处于危险之中。胸部 X 光 (CXR) 图像和计算机断层扫描 (CT) 被部分用于对感染该病毒的患者进行可靠的筛查分析。从不同医学图像中识别 COVID-19 非常具有挑战性，因为这需要更长时间，还需要对易受人为错误影响的批次进行准确可视化。因此，人工智能 (AI) 技术不断被用于实现高性能。深度学习 (DL) 架构已超越了 AI 方法中流行的经典机器学习 (ML)。此外，DL 自动充当提取器、选择器和特征分类器。本章全面回顾了 DL 方法在 COVID-19 识别和肺部分割中的应用。此外，我们还重点研究了 X 光图像和 CT 用于特征提取和分类。此外，还介绍了使用 DL 方法基于 COVIDX 数据集对录入图像进行分类的文章综述。该数据集最近常用于分类感染患者或正常患者。最后，我们强调了在检测基于 DL 的 COVID-19 方法过程中遇到的困难。还介绍了诊断记录图像的挑战，并提出了解决这些挑战的建议。

### 6.1 引言

2019 年 12 月，COVID-19 病毒在中国武汉被发现，随即在全球迅速传播 [1]。该病毒进入肺细胞并扩散至呼吸系统，在那里复制并杀死细胞 [2, 3]。该病毒极其危险，可能导致免疫系统较弱的人死亡 [4]。全世界的传染病专家和临床医生一直在尝试寻找该疾病的治疗方法 [5]。COVID-19 是世界上许多国家的首要死亡原因，因此在其早期阶段进行检测至关重要。然而，使用聚合酶链反应 (PCR) 检测进行检测耗时，这对 COVID-19 患者来说是一种风险。因此，首先和最重要的是，使用医学影像应用来识别 COVID-19，然后使用 PCR 检测来协助临床医生做出最终决定。用于诊断 COVID-19 的两种医学影像程序是 X 光和 CT 扫描。X 光模态是诊断 COVID-19 的初始方法。它具有费用低廉且对人体健康辐射危害风险低的优点 [6]。基于 X 光的 COVID-19 检测是一个困难的过程。放射科医生必须密切关注这些图像中含有水和脓液的白色斑点，因为这些斑点非常冗长且棘手。诊断 COVID-19 的初始技术是使用 X 光，它具有费用低廉且被认为是低人体健康辐射风险的优点。然而，使用 X 光进行 COVID-19 检测是一项艰巨的任务。因为这些图像中含有水和脓液的白色斑点异常冗长且棘手，放射科医生必须特别关注它们。由于 X 光具有较高的误差率，CT 扫描可以用于更精确的检测。尽管如此，CT 扫描比 X 光图像昂贵得多 [7]。在 CT 扫描记录时，会提供每个被怀疑感染 COVID-19 的患者的多个切片。要基于 CT 扫描图像诊断 COVID-19，医生和放射科医生必须处理大量图像。图 (14.3) [8] 展示了基于深度学习 (DL) 的最近方法的分类法，用于监督学习和非监督学习。在监督学习中，卷积神经网络 (CNN) 和循环神经网络 (RNN) 被优先用于实现医学图像的实时精确诊断和分类。另一方面，基于自动编码器 (AE)、深度置信神经网络 (DBNN) 以及 CNN 和 AE 组合的非监督深度学习方法被用于应用医学图像的聚类和诊断。在特殊情况下，这些方法可用于从 MRI 扫描中诊断和扫描脑肿瘤，以及在许多任务（包括医学图像分析）中实现人类精度水平的多种 AI 数据处理应用。在第 [7] 章中，介绍了使用 DL 模型诊断冠状病毒的摘要 [7, 9]。节

