
# 交叉验证与结果

为确保无偏验证，采用了 k 折交叉验证技术，将数据均等地分为 k 个部分。交叉验证 (CV) 是一种评估学习算法的统计手段 [[9](#14_ch7.xhtml#r7_9)]。训练和验证由子样本完成。使用了一种特殊的 k 折（其中 `k = 10`）交叉验证，其中 `k-1` 用于训练，剩余的分割用于验证（测试）。迭代持续进行，直到所有子样本用尽，以这种方式每个子样本都被用于训练和测试，最后所有测试的平均值给出结果。

列联表，如 [表 7.11](#14_ch7.xhtml#t7_11) 所示（混淆矩阵的列联表），显示了所有获得结果的摘要。列对应于输入算法的原始类别，行是算法给出的相应预测输出。

[表 7.11](#14_ch7.xhtml#t7_11) 中所示的标签（1 到 3）标记各个类别。健康皮肤图像标记为 1，浅度烧伤图像标记为 2，全层烧伤图像标记为 3。

## 表 7.11：烧伤深度分类结果

| 预测类别 | 目标类别 |
| --- | --- |
| | 1 | 2 | 3 |
| 1 | 660 33.3% | 0 0.0% | 1 0.1% |
| 2 | 0 0.0% | 660 33.3% | 0 0.0% |
| 3 | 0 0.0% | 0 0.0% | 659 33.3% |

真阴性 (TN) 是某类的实际数据，并被预测为该类。同样，真阴性是不属于某类的实际数据类别，并被预测为不属于该类，例如正常皮肤被预测为正常。当某类数据为阴性但被算法预测为阳性时，称为假阳性。但当数据为阳性而被算法预测为阴性时，则为假阴性。

分类算法对每个实例类别进行分类的性能评估见 [表 7.12](#14_ch7.xhtml#t7_12)。分类器将来自三个类的实例映射到集合 `{1, 2, 3}` 中，分别作为健康、浅度烧伤、全层烧伤的类别标签。同时计算了精确率、敏感度（召回率）和特异度等性能指标。

精确率作为性能指标，告诉我们分类器准确识别已标记样本的程度。召回率是准确分类的阳性样本数除以数据中包含的阳性样本数，而特异度是准确识别阴性样本的度量。

此外，分类算法的总体准确率和相应的精确率指标见 [表 7.13](#14_ch7.xhtml#t7_13)。

## 表 7.12：健康皮肤、浅度烧伤和全层烧伤的性能指标

| 指标 | 类别 1 | 类别 2 | 类别 3 |
| --- | --- | --- | --- |
| 精确率 (%) | 0.99848 | 100.00 | 100.00 |
| 敏感度 (%) | 100.00 | 100.00 | 0.99848 |
| 特异度 (%) | 0.99924 | 100.00 | 100.00 |

## 表 7.13：区分健康皮肤、浅度烧伤和全层烧伤的准确率和精确率

| 总体准确率 (%) | 总体精确率 (%) |
| --- | --- |
| 0.99949 | 0.99949 |

然而，结果记录了一个来自全层烧伤的误分类元素，如 [表 7.13](#14_ch7.xhtml#t7_13) 所示，它被错误地预测为浅度烧伤。这种误分类可能是由于某些全层烧伤图像呈现蜡样外观。模型的总体正确性（准确率）是通过将正确分类的数量（实际分类的阳性）除以所有分类的总和来确定的。

# 结论

本章讨论的研究展示了如何利用深度学习框架自动区分皮肤烧伤损伤和正常皮肤。获得的结果表明，与临床评估相比，机器可用于以高准确率对人类皮肤烧伤损伤进行首次评估。这表明，诊断烧伤可以通过提高服务交付效率，显著缩短医院的等待时间。诊断烧伤的最终目标是提供即时评估，以减少医院延误时长并防止生命损失。尽管临床环境中已采取措施治疗烧伤患者，但获得的结果准确性并不令人信服，最重要的是不可靠，因为这些方法高度主观。

尽管活检比临床评估是更好的技术，但它受到局限性的制约，例如局限于小区域，以及因遗留疤痕引发的伦理争议。同样，激光多普勒成像被证明是治疗烧伤创面的良好技术。然而，除了重量和成本等突出问题外，研究表明 LDI 仅在受伤 48 小时后才可靠并给出更准确的结果。

因此，在本研究中，我们提出了一种利用机器学习区分健康皮肤、浅度烧伤和全层烧伤的概念。结果显示，使用残差网络的 101 层架构，分类准确率高达 99.9%。这表明，当使用此类

因此，本章的研究表明机器学习能够区分烧伤皮肤和健康皮肤。此外，研究还表明，即使是经验丰富的皮肤科医生也难以区分的、具有相似物理特征的皮肤异常，可以使用计算机算法有效区分。最后，研究还表明，两类烧伤损伤可以使用机器学习方法有效诊断。

# 参考文献

1.  [Log, T.](#14_ch7.xhtml#r_r7_1) Modeling skin injury from hot rice porridge spills. International Journal of Environmental Research and Public Health 15(4): 808, 2018.

2.  [Yang Zhao, Jason R. Maher, Jina Kim, Maria Angelica Selim, Howard Levinson, and Adam Wax](#14_ch7.xhtml#r_r7_2). Evaluation of burn severity *in vivo* in a mouse model using spectroscopic optical coherence tomography. Biomedical Optics Express 6(9): 3339-3345, 2015.

3.  [Monstrey, S., H. Hoeksema, J. Verbelen, A. Pirayesh, and P. Blondeel](#14_ch7.xhtml#r_r7_3). Assessment of burn depth and burn wound healing potential Assessment of burn depth and burn wound healing potential. Burns 34(6): 761-769, 2008.

4.  [Hoeksema, H., K. V. de Sijpe, T. Tondu, M. Hamdi, K. Van Landuyt, P. Blondeel, and S. Monstrey](#14_ch7.xhtml#r_r7_4). Accuracy of early burn depth assessment by laser Doppler imaging on different days post burn. Burns 35(1): 36-45, 2009.

5.  [Jan, S. N., F. A. Khan, M. M. Bashir, M. Nasir, H. H. Ansari, H. B. Shami, U. Nazir, A. Hanif, and M. Sohail](#14_ch7.xhtml#r_r7_5). Comparison of Laser Doppler Imaging (LDI) and clinical assessment in differentiating between superficial and deep partial thickness burn wounds. Burns, 2017.

6.  [Badea, M.-S., C. Vertan, C. Florea, L. Florea, and S. Bädoiu](#14_ch7.xhtml#r_r7_6). Severe bums assessment by joint color-thermal imagery and ensemble methods. In e-Health Networking, Applications and Services (Healthcom), 2016 IEEE 18th International Conference, 2016.

7.  [Sabeena, B., and R. K. Kumar](#14_ch7.xhtml#r_r7_7). Diagnosis and detection of skin burn analysis segmentation in colour skin images. International Journal of Advanced Research in Computer and Communication Engineering 6(2), 2017.
