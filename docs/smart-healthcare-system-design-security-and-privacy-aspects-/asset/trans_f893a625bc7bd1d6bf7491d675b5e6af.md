

### 13.2.2 AI 赋能的图像处理与诊断

本研究的目标是详细探讨启用 AI 的医学影像在对抗 COVID-19 战役中的地位，这将具有鼓励意义 [13]。这些基于 AI 的医学影像技术有望在未来为研究人员和放射科医生提供指导 [14]。在诊断和预后方面，图像分割、边缘检测以及增强技术发挥着重要作用。在 COVID-19 病例中，胸部 X 光和 CT 图像常用于高风险患者，以判断早期的 COVID-19 肺炎。COVID-19 是一种极具危险性的空气传播病毒，可感染其附近的所有正常患者。然而，基于 X 光和 CT 图像的诊断提供了一种无接触且自动化的检测工作流程，因为许多现代 X 光和 CT 设备都配备了相关功能。此外，在所有医院中，X 光和 CT 成像设备均可用，这极大地提升了便携性、可扩展性和可负担性等问题 [15]。研究还考察了 COVID-19 与其他肺炎及健康受试者的区分。Ucar 等人 [15] 使用了一种结合贝叶斯优化加法的 SqueezeNet 结构来诊断 COVID-19。该实验包含完整的 5,949 张后前位胸部 X 光片，涵盖 2,839 个患者病例，并将 COVID 胸部 X 光数据集与 Kaggle 胸部 X 光肺炎数据集相结合 [16]。实验结果表明，深度 Bayes-SqueezeNet 将单一 COVID-19 识别（在普通、肺炎和 COVID 病例中）的检测准确率提高至 98.3%，而在其他类别中则达到 100%。研究人员在这篇论文中强调了人们对深度学习结果的感知，并鼓励采用更多基于 AI 的决策过程。Chowdhury 等人解释了不同深度学习模型在胸部 X 光数据集上的复合结构。它利用 sgd-SqueezeNet 以 98.3% 的精度对 COVID-19 进行分类 [17]。

Ghoshal 等人正在引入一种贝叶斯卷积神经网络（BCNN）来预测 COVID-19。该研究从在线 COVID-19 数据集中收集了 70 名阳性患者的肺部 X 光片，以及从 Kaggle 胸部 X 光图像（肺炎）数据集中收集的非 COVID 患者图像。这将 VGG16 模型的检测精度提高到了 92.9%。Zhang 等人提出了一种基于 ResNet 的模型，用于从 X 光片中感知 COVID-19。它不仅在 COVID-19 分类方面表现出色，还执行异常检测。为了优化用于分类的 COVID-19 评分，使用了异常检测。为了实验目的，使用了 70 张 COVID 和 1,008 张非 COVID 患者的 X 光片。该模型实现了 96.0% 的精度，AUC 为 0.952。Li 和 Zhu 提出了一种基于 DenseNet 的 COVID-Xpert 架构，用于胸部 X 光图像的分类。他们使用迁移学习，获得了 88.9% 的总体准确率。Wang 和 Wong 使用了一种专为从 X 光片诊断 COVID-19 而定制的特殊 CNN 模型。虽然使用了机器驱动的设计，但旨在增强模型架构。该方法实现了 92.3% 的总体分类准确率。Afshar 等人提出了一种基于胶囊网络并使用四类数据集的深度学习模型。在 COVID-19 的分类中，他们的模型实现了 95.7% 的总体准确率 [18]。

这些实验主要基于 70 名 COVID-19 患者的公开图像，这不足以评估技术的效率和鲁棒性。Ozkaya 等人使用深度融合和排序特征在早期阶段从 CT 图像中检测 COVID-19。从 150 张 CT 图像生成了两个子集（16 × 16 & 32 × 32）。共有 3,000 张被标记为 COVID-19 的图像块。随后，在迁移学习中使用的模型对处理后的数据进行了分类。实验结果表明，其精度达到了 98.27%。Tang 等人为 COVID-19 的治疗计划模型提出了独特的基于随机森林（RF）的严重程度评估。首先使用深度 VB-Net，将肺部图像划分为解剖学亚区（例如肺叶和肺段）。然后，从每个解剖学亚区的感染体积和比率计算出的定量特征用于训练 RF 模型。结果表明，分类准确率为 87.5% [19]。

## 13.3 乐观的治疗与治愈方法

许多实验室和信息中心此前已指定，他们正在参与 AI 个体工作并构建高效的基础设施，以寻找 COVID-19 的治疗方法和疫苗。科学家和医生正在合作，通过重新组合现有药物来确定针对 COVID-19 的创新药物 [11]。AI 流程和工具帮助他们加速了这一发现过程。Beck 等人及 Stebbing 等人报告称，现有药物如阿扎那韦和 Baricitinib（用于对抗类风湿关节炎和骨髓纤维化）可能成为应对 COVID-19 的潜在行为方案。Dong 等人总结了一份可能的用于应对 COVID-19 的药物列表。该论文讨论了通过气雾吸入使用 IFN-α 药物 10 天的方法。然后，它介绍了通过口服洛哃沙韦/利托那韦和 Arbidol 使用 10 天的方法。此外，它还解释了通过静脉注射利巴韦林药物使用 10 天的方法 [20]。

## 13.4 挑战与未来研究问题

针对 COVID-19 的研究工作仍处于早期阶段且仍在进行中。不同的图像处理技术，如分割、边缘检测、诊断、分类和形态变化，有效地监测了 COVID-19 AI 赋能随访研究的进展。下文讨论了一些开放性的挑战和未来研究问题。医学影像、AI、NLP、肿瘤学及组合技术的综合使用，可能会促进 COVID-19 的测量过程。基于自然语言处理（NLP）的 AI 有助于处理人类无法处理的海量数据。AI 可以帮助我们通过统计分析追踪 SARS-CoV-2 病毒的传播、模式、趋势和行为变化，并形成症状聚类，从而引导新的治疗或药物发现路径 [12]。可以构建基于 AI 和 NLP 的聊天机器人系统，通过阅读数据库中成千上万篇学术文章，对其进行排序并生成响应片段和摘要，以回答患者查询。即使是深度学习也可以帮助我们快速搜索数据库以满足智力需求。我们可以关注区分那些症状轻微、在 X 光或 CT 图像上可能无法准确可视化的患者，而不是仅仅关注肺炎症状患者。实施机器学习（ML）技术以增强低显著性数据，避免对 COVID-19 实例产生有偏见和错误的预测。使用不同的 ML 技术（如回归），即使是不足的时序数据也可以进行改进和分析。基于深度学习的 CNN 模型（ResNet、DenseNet 等）更适用于管理医学图像数据的不平衡数据集，并减少长时间的训练。动态规划方法可以有效管理基因组或蛋白质组序列的大型数据集，并辅以监督式深度学习方法的帮助。我们可以使用深度学习模型结合 NLP 工具来处理低质量、多维且高度非结构化的区域卫星图像和社交媒体数据。

## 13.5 结论

本研究解释了 AI 驱动的方法和 AI 赋能的影像解释如何预测、诊断和分类 COVID-19 及药物开发。详细讨论了智能 AI 工具、深度学习策略和 AI 赋能的影像设备。这些主要集中于展示 AI 赋能的医学影像在 COVID-19（即 X 光和 CT）中的效率。值得指出的是，当临床表现和实验室检查结果与这些 AI 赋能方法结合时，可以更有效地揭示和分析 COVID-19。此外，针对胸部 X 光和 CT 图像增强的基于 AI 的图像处理技术可以在近期构建，以更准确和快速地诊断高风险 COVID-19 肺炎。因此，qRT-PCR 和抗原检测方法可以得到很好的支持。实时定量聚合酶链反应（qRT-PCR）技术用于检测上呼吸道和下呼吸道样本中的 SARS-CoV-2 核酸。在从口腔或鼻腔采取的拭子中，qRT-PCR 可以检测到少至一个病毒颗粒。可以构建有效的 ML 算法，基于社交网络数据进行情感分析。人工智能可以帮助更快地预测不同药物的影响。然而，在本报告中，除了一些潜在的 COVID-19 疗法和治愈方法外，还讨论了一些引人入胜的 AI 驱动的药物发现方法。

## 参考文献

- 1. Ucar, F. and Korkmaz, D., COVlDagnosis-Net: Deep Bayes-SqueezeNet based Diagnostic of the Coronavirus Disease 2019 (COVID-19) from X-Ray Images. Med. Hypotheses, 140, 109761, 2020.
- 2. Ibrahim, I.M., Abdelmalek, D.H., Elshatka, M.E., Elfiky, A.A., COVID-19 spike-host cell receptor GRP78 binding site prediction. J. Infect., 80, 554–562, 2020.
- 3. Kassani, S.H., Kassani, P.H., Wesolowski, M.J., Schneider, K.A.R., Automatic Detection of Coronavirus Disease (COVID-19) in X-ray and CT Images: A Machine Learning-Based Approach. arXiv preprint arXiv:2004.10641, 1, 1–10, 2020.
- 4. Kumar, R., Arora, R., Bansal, V., Sahayasheela, V.J., Buckhash, H., Imran, J., Raman, B., Accurate Prediction of COVID-19 using Chest X-Ray Images through Deep Feature Learning model with SMOTE and Machine Learning Classifiers. medRxiv, 1, 1–10, 2020.
- 5. Salman, F.M., Abu-Naser, S.S., Alajrami, E., Abu-Nasser, B.S., Alashqar, B.A., Covic-19 detection using artificial intelligence, in: AUI Repository, 2020.
- 6. Horry, M.J., Paul, M., Ulhaq, A., Pradhan, B., Saha, M., Shukla, N., X-Ray Image based COVID-19 Detection using Pre-trained Deep Learning Models. EngrXiv, 1, 1–13, 2020. https://doi.org/10.31224/osf.io/wx89s.
- 7. Bastugan, M., Ozkaya, U., Ozturk, S., Coronavirus (COVID-19) classification using ct images by machine learning methods. arXiv preprint arXiv:2003.09424, 2020.
- 8. Wang, L. and Wong, A., COVID-Net: A tailored deep convolutional neural network design for detection of COVID-19 cases from chest radiography images. arXiv preprint arXiv:2003.09871, 2020.

