

假阳性（FP）：当模型将负样本预测为正样本时。在肺分割的情况下，当模型将属于非肺区域的图像像素分类为肺像素时。

假阴性（FN）：当模型将正样本分类为负样本时。在肺分割的情况下，当模型将属于肺区域的图像像素分类为背景像素时。

以下是医学图像中肺分割常用指标的摘要。

### 准确率（Accuracy）
准确率是评估深度学习模型的关键指标，能提供其预测能力的洞察。它衡量模型准确预测数与总预测数之比，确定被正确分类为肺或非肺的图像像素百分比。该计算通过以下公式实现：

Accuracy = \frac{TP + TN}{TP + TN + FP + FN}

### Jaccard 指数（Jaccard Index）
也称为重叠度量，它是实测掩膜与分割图像之间的相似度度量。它也称为 IoU。使用以下公式计算：

Jaccard Index = \frac{TP}{TP + FP + FN}

其值在 0 到 1 之间，其中 0 表示预测图像与实测图像之间没有重叠或相似性，1 表示完全重叠，即分割图像与实测图像完全相同。Jaccard 指数值越高，分割结果的相似性和准确性越好。Jaccard 指数被认为是平衡的，因为它同时考虑了假阳性和假阴性。它会对模型缺失或包含实测中不存在的区域进行惩罚。

### Dice 系数（Dice coefficient）
DSC 度量两个集合之间的相似性，通常用于图像分割和自然语言处理等任务。该指标量化预测分割与实测之间的重叠程度。同样，DSC 越高表示分割准确性越好。它也称为“Sørensen Dice 系数”，计算如下：

DC = \frac{2 \times TP}{2 \times TP + FP + FN}

### 精确率（Precision）
精确率是衡量模型正预测准确性的指标。它计算为模型分类为正样本的 TP 预测数与模型分类为正样本的总实例数之比，无论这些预测是否正确。在肺分割中，它是被正确分类的像素数除以被分类为肺像素的总数。当假阳性预测代价高昂时，精确率是一项重要的评估指标。例如，如果模型错误地将健康组织分类为癌变组织。高精确率意味着错误识别正值的错误被最小化。精确率提供了模型正预测准确性的度量。计算如下：

Precision = \frac{TP}{TP + FP}

### 召回率（Recall）
也称为灵敏度，它是模型正确捕获和识别 TP 的能力的度量。在肺分割中，它是从图像中正确分类肺像素的概率。当假阴性比假阳性更关键时，它是一个有用的指标。使用以下公式计算：

Recall = \frac{TP}{TP + FN}

### 特异度（Specificity）
与灵敏度或召回率相反，特异度是模型正确识别 TN 的能力的度量。在肺分割中，它是正确分类背景（或非肺）像素的概率。当假阳性代价高昂或关注负预测的准确性时，它是一个有用的指标。该指标使用以下公式推导：

Specificity = \frac{TN}{TN + FN}

特异度告诉我们模型做出正确负预测的准确性。特异度值越高，模型正确识别 TN 的效果越好，最小化假阳性的发生。值越低意味着模型错误地将负实例预测为正，导致假阳性。

### F1 分数（F1-score）
F1 分数是一项关键的评估指标，通过同时考虑精确率和召回率，对模型性能提供平衡评估。通过计算精确率和召回率的调和平均数，F1 分数在单个值中对这两项指标提供对称表示。最大值为 1 表示完美的精确率和召回率，最小值为 0 表示精确率或召回率为零，F1 分数是模型准确性的可靠指标，计算如下：

F1 Score = \frac{2 \times Precision \times Recall}{Precision + Recall}

### Hausdorff 距离（Hausdorff distance）
度量预测和实测分割边界上任意两点之间的最大距离。Hausdorff 距离越低，分割之间的对齐越好。

肺分割或任何医学图像分割任务的评估指标选择取决于多种因素，包括分割的具体目标、数据集特征以及评估指标所期望的具体特性。

## 7.7 结论

这项研究描绘了基于深度学习技术（特别是在 LFS 中）的变革性作用的更广阔图景，标志着从传统计算机视觉算法的重要转变。评估中强调优先考虑鲁棒性和泛化能力，以降低针对低变异性或标注不充分的数据过拟合的风险。该综述强调了标准化数据集的迫切需求，以有效评估用于分割和疾病分类的各种模型。在提出未来研究方向方面，该研究建议探索多模态成像并整合临床数据，以提高肺分割的精度。在医学图像分析（特别是 CXR 图像）的深度学习模型不断进步的背景下，该研究认识到由于器官重叠和各种解剖结构的存在，肺分割面临着持续的挑战。所提架构所反映的持续研究工作旨在提高分割的准确性和鲁棒性。重要的是，所讨论的分割框架有望适应 CT 等其他医学成像模态，从而将其适用性扩展到 CXR 图像之外。这种多功能性使深度学习成为医学成像领域多种诊断和监测任务的关键技术。

## 参考文献

Abdani, S.R., Zulkifley, M.A., Shahrimin, M.I., 和 Zulkifley, N.H. (2022). 计算机辅助翼状胬肉筛查系统：综述. Diagnostics (巴塞尔, 瑞士) 12 (3): 639. https://doi.org/10.3390/diagnostics12030639.

Agrawal, T. 和 Choudhary, P. (2023). 胸部 X 线摄影中的分割与分类：系统综述. The Visual Computer 39 (3): 875–913. https://doi.org/10.1007/s00371-021-02352-7.

Ait Skourt, B., El Hassani, A., 和 Majda, A. (2018). 基于深度神经网络的肺 CT 图像分割. Procedia Computer Science 127: 109–113. https://doi.org/10.1016/j.procs.2018.01.104.

Akila Agnes, S., Arun Solomon, A., 和 Karthick, K. (2024). 用于 CT 扫描中肺结节精确分割的 Wavelet U-Net++：改善肺癌早期检测与诊断. Biomedical Signal Processing and Control 105: 105509. https://doi.org/10.1016/j.bspc.2023.105509.

Annangi, P., Thiruvenkadam, S., Raja, A., Xu, H., Sun, X., 和 Mao, L. (2010). 一种基于先验形状和低级特征的 X 射线肺分割区域主动轮廓方法. 2010 IEEE 生物医学成像国际研讨会：从纳米到宏观. https://doi.org/10.1109/isbi.2010.5490130.

Armato, S., McLennan, G., McNitt-Gray, M. 等 (2010). WE-B-201B-02: 肺影像数据库联盟 (LIDC) 和图像数据库资源倡议 (IDRI)：用于肺结节分析的 CT 扫描已完成公共数据库. Medical Physics 37 (6Part6): 3416–3417. https://doi.org/10.1118/1.3469350.

Armato, S.G., Giger, M.L., 和 Mac Mahon, H. (1998). 数字化后前位胸部 X 线片中肺的自动分割. Academic Radiology 5 (4): 245–255. https://doi.org/10.1016/s1076-6332(98)80223-7.

Arvind, S., Tembhurne, J.V., Diwan, T., 和 Sahare, P. (2023). 用于胸部 X 射线肺语义分割的改进轻量级基于深度 CNN 的 U-Net. Results in Engineering 17: 100929. https://doi.org/10.1016/j.rineng.2023.100929.

Beyer, T., Bidaud, L., Dickson, J. 等 (2020). 我们将读取什么扫描：临床肿瘤学中的成像仪器趋势. Cancer Imaging 20 (1): https://doi.org/10.1186/s40644-020-00312-3.

Bodenreider, O. (2004). 统一医学语言系统 (UMLS)：整合生物医学术语. Nucleic Acids Research 32 (数据库期刊): D267–D270. https://doi.org/10.1093/nar/gkh061.

Boudoukhani, N., Elberrichi, Z., Ouladjdi, L., 和 Dif, N. (2023). 用于胸部 X 射线精确肺分割的新型注意力门控剩余深度卷积网络. Evolving Systems. https://doi.org/10.1007/s12530-023-09516-x.

Brown, M.S., Wilson, L.S., Doust, B.D. 等 (1998). 基于知识的胸部 X 射线图像中肺边界分割与分析方法. Computerized Medical Imaging and Graphics 22 (6): 463–477. https://doi.org/10.1016/s0895-6111(98)00051-2.

Bustos, A., Pertusa, A., Salinas, J-M., 和 de la Iglesia-Vayá, M. (2020). PadChest：带有多标签注释报告的大型胸部 X 射线图像数据集. Medical Image Analysis 66: 101797. https://doi.org/10.1016/j.media.2020.101797.

癌症成像档案：用于肺癌诊断的大规模 CT 和 PET/CT 数据集 (lung-pet-ct-DX). (无日期). 从 https://wiki.cancerimagingarchive.net/pages/viewpage.action?pageid=70224216 检索.

Candemir, S., Jaeger, S., Palaniappan, K. 等 (2014). 使用带有非刚性配准的解剖图谱进行胸部 X 线片中的肺分割. IEEE 医学成像交易 33 (2): 577–590. https://doi.org/10.1109/tmi.2013.2290491.

Candemir, S., Palaniappan, K., 和 Akgul, Y. S. (2013, April). 图像分割图割的多类正则化参数学习. 2013 IEEE

