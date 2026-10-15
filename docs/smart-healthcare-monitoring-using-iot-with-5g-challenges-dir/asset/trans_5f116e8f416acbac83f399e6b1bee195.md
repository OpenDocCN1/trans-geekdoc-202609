
## 表 7.2
预训练深度学习 ResNet 算法用于 CT 扫描图像 COVID-19 检测的评估方法总结 [5]

| 作者 | Wu et al. [60] | Li et al. [61] | Yousefadeh et al. [62] | Jin et al. [63] | Xu et al. [64] | Jin et al. [65] |
|---|---|---|---|---|---|---|
| 技术 | ResNet50 | ResNet50 | DenseNet, ResNet, Xception, Efficient Net | ResNet152 | ResNet18 | DPN-92, Inception-V3, ResNet50, Attention ResNet50 with 3D U-NET++ |
| 数据来源 | 中国医科大学和北京佑安医院 | 多家医院 | 来自医院的实时数据 | 中国三家不同医院、LIDC-IDRI、ILD-HUG | 浙江大学、温州医院、温岭医院 | 中国五家不同医院 |
| 样本数量（图像） | 总计-495 COVID-19-368 肺炎-127 | 总计-4536 COVID-19-1296 CAP-1735 非肺炎-1325 | 总计-2124 COVID-19-706 非COVID-19-1418 | 总计-1881 COVID-19-496 非COVID-19-1385 | 总计-618 COVID-19-219 甲型流感病毒性肺炎-224 与感染无关-175 | 总计-1391 COVID-19-850 非COVID-19-541 |
| 数据划分 | 训练-80% 验证-10% 测试-10% | 训练-90% 测试-10% | 训练-80% 验证-20% | 随机划分 | 训练+验证-85.4% 测试-14.6% | 随机划分 |
| 性能评估（%） | 准确率-76 敏感性-81.1 特异性-61.5 AUC-81.9 | 敏感性-90 特异性-96 AUC-96 | 准确率-96.4 敏感性-92.4 特异性-98.3 AUC-98.9 F1分数-95.3 Kappa-91.7 | 准确率-94.98 敏感性-94.06 特异性-95.47 精确率-91.53 AUC-97.91 F1分数-92.78 NPV-96.86 Youden指数-89.53 | 准确率-86.7 敏感性-81.5 精确率-80.8 F1分数-81.1 | 敏感性-97.04 特异性-92.2 AUC-99.1 |

用于识别 COVID-19 的流程。因此，我们也可以将基于图像的评估作为辅助措施。鉴于这些局限性和障碍，我们可以建议适当形成和标记数据库，以便研究人员能够充分评估 ResNet 或其他方法。否则，我们可以研究可在小规模数据库上运行的算法。本综述的另一个局限性是缺乏结果的图片对比，无法直观了解检测过程。此外，本综述还简要介绍了 ResNet 以外的算法。

## 表 7.3
自定义深度学习算法评估方法总结，用于 X 射线图像 COVID-19 检测 [5]

| 作者 | Wang et al. [66] | Khan et al. [67] | Rahimzadeh and Attar [68] | Alqudah et al. [69] | Farooq and Hafeez [70] | Afshar et al. [71] |
|---|---|---|---|---|---|---|
| 技术 | COVID-Net (CNN) | CoroNet (CNN) | Concatenated CNN | CNN, SVM, RF | COVID-ResNet (CNN) | COVID-CAPS (Capsule Network) |
| 数据来源 | COVID-19 X 射线图像数据库、RSNA 肺炎检测挑战数据集 | COVID-19 X 射线图像数据库、Kaggle 胸部 X 射线存储库 | COVID-19 X 射线图像数据库、RSNA 肺炎检测挑战数据集 | COVID-19 X 射线图像数据库、 | COVIDx 数据集 | COVIDx 数据集 |
| 样本数量（图像） | 13,800 | 总计-1251 COVID-19-284 正常-310 肺炎_bac-330 肺炎_vir-327 | 总计-15085 COVID-19-180 肺炎-6054 正常-8851 | 总计-71 COVID-19-48 非COVID-23 | 13,800 | 13,800 |
| 数据划分 | 训练-90% 测试-10% | 训练-80% 验证-20% | 5折交叉验证 | 训练-70% 测试-30% | 训练-90% 测试-10% | 训练-90% 测试-10% |
| 性能评估（%） | 准确率-92.4 敏感性-80 精确率-88.9 | 准确率-89.5 敏感性-100 精确率-97 F1分数-98 | 准确率-99.50 敏感性-80.53 特异性-99.56 精确率-35.27 | 准确率-95.2 敏感性-93.3 特异性-100 精确率-100 | 准确率-96.23 敏感性-100 精确率-100 F1分数-100 | 准确率-95.7 敏感性-90 精确率-95.8 AUC-97 |

## 7.6 结论
COVID-19 仍在传播，并在世界各地以不断演化的新毒株留下痕迹。随着时间的推移，目前虽然大多数国家已配备疫苗，但仍无法治愈病毒的进展及其影响。病毒的影响更为危险，因为无症状患者不会表现出任何症状，却在不知情的情况下传播病毒。因此，人工智能系统至少用于检测和隔离患者至关重要。各种人工智能和物联网设备已提供了有希望的

## 表 7.4
自定义深度学习算法评估方法总结，用于 CT 扫描图像 COVID-19 检测 [5]

| 作者 | He et al. [72] | Zheng et al. [73] | Singh et al. [74] | Farid et al. [75] |
|---|---|---|---|---|
| 技术 | CRNet | DeCoVNet | MODE-CNN | CNN |
| 数据来源 | 意大利医学与介入放射学会 COVID-19 数据库 COvid-CT | 联合医院同济医学院华中科技大学 | Covid-19 患者胸部 CT 图像 | Kaggle 基准数据集 |
| 样本数量（图像） | 总计-746 COVID-19-349 非COVID-397 | 630 | 总计-150 COVID-19-75 非COVID-75 | 总计-102 COVID-19-51 SARS-51 |
| 数据划分 | 训练-60% 验证-15% 测试-25% | 训练-80% 测试-20% | 训练和测试数据集的各种比例 | 10折交叉验证 |
| 性能评估（%） | 准确率-95.2 敏感性-93.3 特异性-100 精确率-100 | 准确率-95.2 敏感性-93.3 特异性-100 精确率-100 | 准确率-95.2 敏感性-93.3 特异性-100 精确率-100 | 准确率-95.2 敏感性-93.3 特异性-100 精确率-100 |

解决方案用于 COVID-19，但通过除 RT-PCR 之外的流程检测患者仍在研究中。使用 X 射线和 CT 扫描图像的检测过程仍被视为 RT-PCR 检测的额外措施。本章回顾了人工智能在深度学习算法领域的应用，重点关注用于 COVID-19 分析的快速探索方法 ResNet。ResNet 的稳健性提供了有希望的结果，但仍有改进空间。本章综述提供了基于用于方法分类的分类法的讨论。方法主要分为预训练模型，其中已训练的与类似疾病类型的模型在添加 COVID-19 数据后进行再训练。第二种方法是自定义深度学习方法，从头开始训练系统。综述还提供了对可公开用于评估的数据库的见解，预计对该领域的研究人员将有很大帮助。本研究中的局限性也已概述，涉及非统一有效数据库以及由于缺乏实时 COVID-19 数据而造成的危害，而实时 COVID-19 数据是深度学习方法高度需要的。评估的金标准不可用也被报告。进一步还讨论了可能的解决方案和结果。虽然用于 COVID-19 的医学图像深度学习算法可被视为识别的额外措施，但最近它们也可能为传统的 RT-PCR 筛查提供高效且更快的解决方案。如果不是，至少通过人工智能的早期检测，它们可能有助于减少病毒的传播。

## 参考文献
- [1]. WHO COVID-19 情况报告。 [在线]. 可用：2021年3月 https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports, (2021).
- [2]. Cascella M, Rajnik M, Cuomo A, Dulebohn SC 和 Di Napoli R. 冠状病毒（covid-19）的特征、评估和治疗。 Statpearls [互联网]. StatPearls Publishing, 2020.
- [3]. Forni, D., Cagliani, R., Clerici, M. 和 Sironi, M. 人类冠状病毒基因组的分子进化。 Trends in Microbiology, 25 (1), 35–48, (2017).
- [4]. Harapan, H., Itoh, N., Yufika, A., Winardi, W., Keam, S., Te, H., Megawati, D., Hayati, Z., Wanger, A.L. 和 Mudatsir, M. 冠状病毒病 2019（COVID-19）：文献综述。 Journal of Infection and Public Health, 13 (5), 667–673 doi: 10.1016/j.jiph.2020.03.01, 2020.
- [5]. Islam, M. M., Karray, F., Alhajj, R. 和 Zeng, J. 关于新型冠状病毒（covid-19）诊断的深度学习技术的综述。 IEEE Access, 9, 30551–30572, (2021).
- [6]. J. P. Kanne, “2019新型冠状病毒（2019-nCoV）感染的胸部CT表现——来自中国武汉：放射科医生的关键点。” Radiology, 295 (1), 16–17, (Apr. 2020).
- [7]. J. P. Kanne, “2019新型冠状病毒（2019-nCoV）感染的胸部CT表现——来自中国武汉：放射科医生的关键点。” Radiology, 295 (1), 16–17, (Apr. 2020).
- [8]. Tayarani-N, M. H. 人工智能在抗击 Covid-19 中的应用：文献综述。 Chaos, Solitons & Fractals, 110338, 1–60 (2020).
- [9]. Mishra, A. K., Das, S. K., Roy, P. 和 Bandyopadhyay, S. 基于胸部 CT 图像识别 COVID19：一种基于深度卷积神经网络的方法。 Journal of Healthcare Engineering, 2020, 1–7 (2020).
- [10]. H. Kim, H. Hong, S. H. Yoon, 冠状病毒病 2019 CT 与逆转录聚合酶链反应诊断性能：荟萃分析。 Radiology, 296 (3), E145–E155 (Sep. 2020).
- [11]. Z. Ye, Y. Zhang, Y. Wang, Z. Huang 和 B. Song, 新型冠状病毒病 2019（COVID-19）的胸部 CT 表现：图示综述。 European Radiology, 30, (8), 4381–4389 (Aug. 2020).
- [12]. X. Mei, H. C. Lee, K. Diao, M. Huang, B. Lin, C. Liu 和 Z. Xie, 人工智能支持的 COVID19 患者快速诊断。 Nature Medicine, 26 (8),1224–1228 (Aug. 2020).
- [13]. L. Huang, R. Han, T. Ai, P. Yu, H. Kang, Q. Tao 和 L. Xia, COVID-19 序列定量胸部 CT 评估：一种深度学习方法。 Radiology: Cardiothoracic Imaging, 2 (2), Art. no. e200075 (Apr. 2020).
- [14]. H. Panwar, P. K. Gupta, M. K. Siddiqui, R. Morales-Menendez 和 V. Singh, 使用 nCOVnet 通过深度学习快速检测 X 射线中的 COVID-19 应用。 Chaos, Solitons & Fractals, 138, Art. no. 109944, (Sep. 2020).
- [15]. K. El Asnaoui 和 Y. Chawki, 使用 X 射线图像和深度学习自动检测冠状病毒病。 Journal of Biomolecular Structure and Dynamics, 7, 1–12 doi: 10.1080/07391102.2020.1767212, (May 2020).
- [16]. Y. Oh, S. Park 和 J. C. Ye, 使用有限训练数据集在 CXR 上深度学习 COVID-19 特征。 IEEE Transactions on Medical Imaging, 39 (8), 2688–2700 (Aug. 2020).
- [17]. R. M. Pereira, D. Bertolini, L. O. Teixeira, C. N. Silla 和 Y. M. G. Costa, 在平坦和分层分类场景中在胸部 X 射线图像中识别 COVID-19。 Computer Methods and Programs in Biomedicine, 194, Art. no. 105532 (Oct 2020).
